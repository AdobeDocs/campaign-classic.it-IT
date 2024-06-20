---
product: campaign
title: Integrare l’SDK di Campaign
description: Scopri come integrare l’SDK di Campaign nella tua app mobile
feature: Mobile SDK Integration, Push
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# Integrare l’SDK Campaign con la tua app {#integrating-campaign-sdk-into-the-mobile-application}

>[!CAUTION]
>
>L’Adobe consiglia vivamente di utilizzare l’SDK di Adobe Experience Platform Mobile configurando l’estensione Adobe Campaign nell’interfaccia utente di Data Collection. L’SDK di Adobe Experience Platform Mobile aiuta ad alimentare soluzioni e servizi di Experience Cloud di Adobe nelle app mobili. La configurazione degli SDK viene gestita tramite l’interfaccia utente di Data Collection per una configurazione flessibile e integrazioni estensibili basate su regole. [Ulteriori informazioni sono disponibili nella documentazione di Adobe Developer](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.

Per ottenere l’SDK di Campaign (precedentemente noto come SDK Neolane), contatta [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

Per ulteriori informazioni sulle diverse versioni supportate di Android e iOS, consulta [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#MobileSDK).

Di seguito sono riportati i passaggi di integrazione per l’SDK di Campaign.

+++**Caricamento dell’SDK di Campaign**

* **In Android**: il **neolane_sdk-release.aar** Il file deve essere collegato al progetto.

  Le seguenti autorizzazioni concedono l’accesso al server Adobe Campaign:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  La seguente autorizzazione ti consente di recuperare l’ID univoco di un dispositivo mobile:

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  Dalla versione 1.0.24 dell’SDK, questa autorizzazione viene utilizzata solo per le versioni precedenti ad Android 6.0.

  A partire dalla versione 1.0.26 dell’SDK, questa autorizzazione non viene più utilizzata.

* **In iOS**: il **libNeolaneSDK.a** e **Neolane_SDK.h** I file devono essere collegati al progetto. Dalla versione 1.0.24 dell’SDK, l’opzione **ENABLE_BITCODE** è attivato.

  >[!NOTE]
  >
  >Per la versione 1.0.25 dell’SDK, le quattro architetture sono disponibili nel **Neolane_SDK.h** file.

+++

+++**Dichiarazione delle impostazioni di integrazione**

Per integrare l’SDK di Campaign nell’app mobile, l’amministratore funzionale deve fornire le seguenti informazioni allo sviluppatore:

* **Una chiave di integrazione**: per abilitare la piattaforma Adobe Campaign per identificare l’app mobile.

  >[!NOTE]
  >
  >Questa chiave di integrazione viene immessa nella console Adobe Campaign, nel **[!UICONTROL Information]** scheda del servizio dedicata all’app mobile. Fai riferimento a [Configurazione di un’app mobile in Adobe Campaign](configuring-the-mobile-application.md).

* **Un URL di tracciamento**: corrisponde all’indirizzo del server di tracciamento di Adobe Campaign.
* **Un URL di marketing**: per abilitare la raccolta di abbonamenti.

* **In Android**:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **In iOS**:

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

+++

+++**Funzione di registrazione**

La funzione di registrazione consente di:

* invia l’ID notifica o l’ID push (deviceToken per iOS e registrationID per Android) ad Adobe Campaign.
* recupera la chiave di riconciliazione o userKey (ad esempio e-mail o numero di account)

* **In Android**:

  ```
  void registerInNeolane(String registrationId, String userKey, Context context)
  {
   try{
    Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
   } catch (NeolaneException e){
    //...
   } catch (IOException e){
    //...
   }
  }
  ```

  Se utilizzi FCM (Firebase Cloud Messaging), ti consigliamo di utilizzare il **registerDevice** quando si chiama il **onTokenRefresh** per notificare ad Adobe Campaign la modifica nel token del dispositivo mobile dell’utente.

  ```
  public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
    @Override
    public void onTokenRefresh() {
      String registrationToken = FirebaseInstanceId.getInstance().getToken();
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      ...
      ...
      // Neolane Registration
      neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
      public void onComplete(String e, Object state) { ... }
      public void onNeolaneException(NeolaneException e, Object state) { ... }
      public void onIOException(IOException e, Object state) { ... }
      });
      ...
      ...
    }
  }
  ```

* **In iOS**:

  ```
  // Callback called on successful registration to the APNs
  - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
  {
      // Pass the token to Adobe Campaign
      Neolane_SDK *nl = [Neolane_SDK getInstance];
      [nl registerDevice:tokenString:self.userKey:dic];
  }
  ```

+++

+++**Funzione di tracciamento**

* **In Android**:

  Le funzioni di tracciamento consentono di tenere traccia delle attivazioni delle notifiche (aperture) e delle visualizzazioni delle notifiche (schermata).

  Per tenere traccia della visualizzazione delle notifiche (eseguita chiamando il **notificationReceive** dell’SDK), segui l’implementazione riportata di seguito. Se utilizzi FCM (Firebase Cloud Messaging), ti consigliamo di utilizzare il **notificationReceive** funzione quando **onMessageReceived** viene richiamata dal sistema Android.

  ```
  package com.android.YourApplication;
  
  import android.content.Context;
  import android.content.SharedPreferences;
  import android.os.Bundle;
  import android.util.Log;
  
  import com.google.firebase.messaging.FirebaseMessagingService;
  import com.google.firebase.messaging.RemoteMessage;
  
  import java.util.Iterator;
  import java.util.Map;
  import java.util.Map.Entry;
  
  public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
    private static final String TAG = "MyFirebaseMsgService";
  
    @Override
    public void onMessageReceived(RemoteMessage message) {
      Log.d(TAG, "Receive message from: " + message.getFrom());
      Map<String,String> payloadData = message.getData();
      final Bundle extras = new Bundle();
      final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
      while(iter.hasNext())
      {
        final Entry<String, String>  entry =iter.next();
        extras.putString(entry.getKey(), entry.getValue());
      }
  
      SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      String mesg = payloadData.get("_msg");
      String title = payloadData.get("title");
      String url = payloadData.get("url");
      String messageId = payloadData.get("_mId");
      String deliveryId = payloadData.get("_dId");
      YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
    }
  }
  ```

  ```
  public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
      if( message == null ) message = "No Content";
      if( title == null )   title = "No title";
      if( url == null )     url = "https://www.tripadvisor.fr";
      int iconId = R.drawable.notif_neotrip;
  
    // notify Neolane that a notification just arrived
    SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
    Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
    Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
    Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
    NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
    nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
      public void onNeolaneException(NeolaneException arg0, Object arg1) {}
      public void onIOException(IOException arg0, Object arg1) {}
      public void onComplete(String arg0, Object arg1){}
    });
    if (yourApplication.isActivityVisible())
      {
        Log.i("INFO", "The application has the focus" );
        ...
      }
      else
      {
        // notification creation :
        NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
        Notification notification;
  
        // Activity to start :
        Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
        notifIntent.putExtra("notificationText", message);
        notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
        notifIntent.putExtra("_dId", deliveryId);
        notifIntent.putExtra("_mId", messageId);
        notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
        PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
  
        notification = new Notification.Builder(context)
                .setContentTitle(title)
                .setContentText(message)
                .setSmallIcon(iconId)
                .setContentIntent(contentIntent)
                .build();
  
        // launch the notification :
        notification.flags |= Notification.FLAG_AUTO_CANCEL;
        notificationManager.notify(Integer.valueOf(messageId), notification);
      }
  }
  ```

  Esempio di implementazione per il tracciamento di una notifica aperta (eseguita chiamando il **notificationOpening** dell&#39;SDK). Il **NotificationActivity** la classe corrisponde a quella utilizzata per creare **notifIntent** nell&#39;esempio precedente.

  ```
  public class NotificationActivity extends Activity {
  public void onCreate(Bundle savedBundle) {
    [...]
    Bundle extra = getIntent().getExtras();
    if (extra != null) {
      // reinit the acc sdk
      SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
      Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
      Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
      // Get the messageId and the deliveryId to do the tracking
      String deliveryId = extra.getString("_dId");
      String messageId = extra.getString("_mId");
      if (deliveryId != null && messageId != null) {
        try {
          Neolane.getInstance().notifyOpening(Integer.valueOf(messageId), Integer.valueOf(deliveryId));
        } catch (NeolaneException e) {
          // ...
        } catch (IOException e) {
          // ...
        }
      }
    }
   }
  }
  ```

* **In iOS**:

  La funzione di tracciamento ti consente di tenere traccia di quando le notifiche vengono attivate (si apre).

  ```
  (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
  {
  if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
  *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
  ...  
  completionHandler(UIBackgroundFetchResultNoData);
  }
  ```

  >[!NOTE]
  >
  >Dalla versione 7.0, una volta **`application:didReceiveRemoteNotification:fetchCompletionHandler`** è implementata, il sistema operativo chiama solo questa funzione. Il **`application:didReceiveRemoteNotification`** La funzione non viene quindi chiamata.

+++

+++**Tracciamento delle notifiche silenziose**

iOS consente di inviare notifiche invisibili all’utente, una notifica o dati che verranno inviati direttamente a un’app mobile senza visualizzarli. Adobe Campaign consente di tracciarli.

Per tenere traccia della notifica invisibile all’utente, segui l’esempio seguente:

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

+++

+++**Delegato RegisterDeviceStatus**

>[!NOTE]
>
>Tieni presente che questo è esclusivo per iOS.

In iOS, il protocollo delegato ti consente di ottenere il risultato del **registerDevice** e può essere utilizzato per sapere se si è verificato un errore durante la registrazione.

Il **registerDeviceStatus** prototipo:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Stato** consente di sapere se la registrazione è riuscita o se si è verificato un errore.

**ErrorReason** fornisce ulteriori informazioni sugli errori che si sono verificati. Per ulteriori informazioni sugli errori disponibili e sulle relative descrizioni, consulta la tabella seguente.

<table> 
 <thead>
  <tr>
   <th> Stato<br /> </th>
   <th> Descrizione<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Registrazione riuscita<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> Il nome host del server di marketing ACC è vuoto o non impostato.<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> La chiave di integrazione è vuota o non impostata.<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> Problema di connessione con ACC<br /> </td>
   <td> Ulteriori informazioni (nella lingua corrente del sistema operativo)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> L’UUID (chiave di integrazione) fornito è sconosciuto.<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> Errore imprevisto restituito al server ACC.<br /> </td>
   <td> Messaggio di errore restituito ad ACC.<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** protocollo e **registerDeviceStatus** la definizione del delegato è la seguente:

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

Per implementare **registerDeviceStatus** delegato, segui questi passaggi:

1. Implementare **setDelegate** durante l’inizializzazione dell’SDK.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings
   
    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];
   
    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. Aggiungere il protocollo in **@interface** della tua classe.

   ```
   //  AppDelegate.h
   
   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"
   
   @class LandingPageViewController;
   
   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. Implementare il delegato in **AppDelegate**.

   ```
   //  AppDelegate.m
   
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);
   
       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);
   
       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

+++

+++**Variabili**

Le variabili ti consentono di definire il comportamento dell’app mobile dopo aver ricevuto una notifica. Queste variabili devono essere definite nel codice dell’app mobile e nella console Adobe Campaign, nel **[!UICONTROL Variables]** nell’app mobile dedicata (consulta [Configurazione di un’app mobile in Adobe Campaign](configuring-the-mobile-application.md)). Di seguito è riportato un esempio di codice che consente a un’app mobile di raccogliere tutte le variabili aggiunte in una notifica. Nel nostro esempio, utilizziamo la variabile &quot;VAR&quot;.

* **In Android**:

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **In iOS**:

  ```
  - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
  {
      ....
      if( launchOptions )
      {
          // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
          NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
          if( localLaunchOptions )
          {
           ...
           [localLaunchOptions objectForKey:@"VAR"];
          ...
          }
     }
  }
  
  // Callback called when the application is already launched (whether the application is running foreground or background)
  - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  {
      if( launchOptions )
      {
       ...
          [launchOptions objectForKey:@"VAR"];
      }
  }
  ```

>[!CAUTION]
>
>L’Adobe consiglia di scegliere nomi di variabili brevi, perché la dimensione della notifica è limitata a 4 kB per iOS e Android.

+++

+++**Estensione del servizio di notifica**

**Per iOS**

Il supporto deve essere scaricato a livello di estensione del servizio di notifica.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

+++

+++**Estensione contenuto notifica**

**Per iOS**

A questo livello, devi:

* Associa l’estensione di contenuto alla categoria inviata da Adobe Campaign:

  Se desideri che nell’app mobile venga visualizzata un’immagine, puoi impostare il valore della categoria su &quot;image&quot; in Adobe Campaign e creare un’estensione di notifica con il **UNNotificationExtensionCategory** parametro impostato su &quot;image&quot;. Quando la notifica push viene ricevuta sul dispositivo, l’estensione viene chiamata in base al valore di categoria definito.

* Definire il layout delle notifiche

  È necessario definire un layout con i widget pertinenti. Per un’immagine, il widget è denominato **UimageView**.

* Visualizzare i file multimediali

  È necessario aggiungere il codice per alimentare i dati multimediali al widget. Di seguito è riportato un esempio di codice per un’immagine:

  ```
  #import "NotificationViewController.h"
  #import <UserNotifications/UserNotifications.h>
  #import <UserNotificationsUI/UserNotificationsUI.h>
  
  @interface NotificationViewController () <UNNotificationContentExtension>
  
  @property (strong, nonatomic) IBOutlet UIImageView *imageView;
  @property (strong, nonatomic) IBOutlet UILabel *notifContent;
  @property (strong, nonatomic) IBOutlet UILabel *label;
  
  @end
  
  @implementation NotificationViewController
  
  - (void)viewDidLoad {
      [super viewDidLoad];
      // Do any required interface initialization here.
  }
  
  - (void)didReceiveNotification:(UNNotification *)notification {
      self.label.text = notification.request.content.title;
      self.notifContent.text = notification.request.content.body;
      UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
      if ([attachment.URL startAccessingSecurityScopedResource])
      {
        NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
        self.imageView.image =[UIImage imageWithData: imageData];
        [attachment.URL stopAccessingSecurityScopedResource];
      }
  }
  @end
  ```

+++
