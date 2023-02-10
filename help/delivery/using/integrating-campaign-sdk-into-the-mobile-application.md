---
product: campaign
title: Integrare Campaign SDK
description: Scopri come integrare l’SDK Campaign nella tua app mobile
feature: Mobile SDK Integration, Push
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 0ae52b00f69298e001596583fe166771faddead2
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---

# Integrare Campaign SDK con la tua app {#integrating-campaign-sdk-into-the-mobile-application}

![](../../assets/common.svg)

Gli SDK di Campaign per iOS e Android sono uno dei componenti del modulo Canale app mobile.

>[!NOTE]
>
>Per ottenere l’SDK di Campaign (noto in precedenza come SDK di Neolane), contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

L’obiettivo dell’SDK è quello di facilitare l’integrazione di un’app mobile nella piattaforma Adobe Campaign.

Per ulteriori informazioni sulle diverse versioni di Android e iOS supportate, consulta la [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#MobileSDK).

>[!NOTE]
>
>Puoi anche utilizzare l’SDK per dispositivi mobili Adobe Experience Platform configurando l’estensione Adobe Campaign in Adobe Launch. [Ulteriori informazioni nella documentazione di Adobe Experience Platform](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.
>
>Scopri come configurare e installare l’SDK di Adobe Experience Platform Mobile [in questo video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/configure-push-using-aep-mobile-sdk.html?lang=en){target="_blank"}.

## Caricamento dell’SDK di Campaign {#loading-campaign-sdk}

* **In Android**: la **neolane_sdk-release.aar** deve essere collegato al progetto.

   La seguente autorizzazione consente l’accesso al server Adobe Campaign:

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
   ```

   La seguente autorizzazione consente di recuperare l&#39;ID univoco di un telefono:

   ```
   <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   ```

   Dalla versione 1.0.24 dell&#39;SDK, questa autorizzazione è utilizzata solo per le versioni precedenti a Android 6.0.

   Dalla versione 1.0.26 dell&#39;SDK, questa autorizzazione non viene più utilizzata.

* **In iOS**: la **libNeolaneSDK.a** e **Neolane_SDK.h** i file devono essere collegati al progetto. Dalla versione 1.0.24 dell’SDK, l’opzione **ENABLE_BITCODE** è attivato.

   >[!NOTE]
   >
   >Per la versione 1.0.25 dell’SDK, le quattro architetture sono disponibili nella sezione **Neolane_SDK.h** file.

## Dichiarazione delle impostazioni di integrazione {#declaring-integration-settings}

Per integrare l’SDK di Campaign nell’app mobile, l’amministratore funzionale deve fornire allo sviluppatore le seguenti informazioni:

* **Una chiave di integrazione**: per abilitare la piattaforma Adobe Campaign per identificare l’app mobile.

   >[!NOTE]
   >
   >Questa chiave di integrazione viene immessa nella console Adobe Campaign, nella **[!UICONTROL Information]** scheda di servizio dedicata all’app mobile. Fai riferimento a [Configurazione di un’app mobile in Adobe Campaign](configuring-the-mobile-application.md).

* **Un URL di tracciamento**: che corrisponde all’indirizzo del server di tracciamento di Adobe Campaign.
* **Un URL di marketing**: per abilitare la raccolta degli abbonamenti.

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

## Funzione di registrazione {#registration-function}

La funzione di registrazione consente di:

* invia l&#39;ID di notifica o l&#39;ID push (deviceToken per iOS e registrationID per Android) ad Adobe Campaign.
* recuperare la chiave di riconciliazione o userKey (ad esempio il numero di e-mail o account)

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

   Se utilizzi FCM (Firebase Cloud Messaging), ti consigliamo di utilizzare il **registerDevice** quando si chiama **onTokenRefresh** per notificare ad Adobe Campaign la modifica del token del dispositivo mobile dell’utente.

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

## Funzione di tracciamento {#tracking-function}

* **In Android**:

   Le funzioni di tracciamento ti consentono di tenere traccia delle attivazioni di notifica (aperture) e delle visualizzazioni di notifica (schermata).

   Per tenere traccia della visualizzazione della notifica (mediante una chiamata al **notifyReceive** (funzione dell&#39;SDK), segui l&#39;implementazione seguente. Se utilizzi FCM (Firebase Cloud Messaging), ti consigliamo di utilizzare il **notifyReceive** quando **onMessageReceived** La funzione viene chiamata dal sistema Android.

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

   Ecco un esempio di implementazione per tenere traccia di una notifica aperta (eseguita chiamando il **notifyOpening** funzione dell&#39;SDK). La **NotificationActivity** corrisponde a quello utilizzato per creare il **notificaIntent** nell&#39;esempio precedente.

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

   La funzione di tracciamento ti consente di tenere traccia di quando vengono attivate le notifiche (si apre).

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
   >Dalla versione 7.0, una volta **applicazione:didReceiveRemoteNotification:fetchCompletionHandler** viene implementata, il sistema operativo chiama solo questa funzione. La **applicazione:didReceiveRemoteNotification** La funzione non viene pertanto chiamata.

## Tracciamento delle notifiche silenziose {#silent-notification-tracking}

iOS ti consente di inviare notifiche silenziose, notifiche o dati che verranno inviati direttamente a un’app mobile senza visualizzarli. Adobe Campaign ti consente di seguirli.

Per tenere traccia della notifica silenziosa, segui l’esempio seguente:

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

### Delegato RegisterDeviceStatus {#registerdevicestatus-delegate}

>[!NOTE]
>
>Tieni presente che questo è esclusivo per iOS.

In iOS, il protocollo delegato ti consente di ottenere il risultato della **registerDevice** chiama e può essere utilizzato per sapere se si è verificato un errore durante la registrazione.

La **registerDeviceStatus** prototipo:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Stato** consente di sapere se una registrazione è riuscita o se si è verificato un errore.

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
   <td> Il nome host del server di marketing ACC è vuoto o non è impostato.<br /> </td>
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
   <td> L'UUID fornito (chiave di integrazione) è sconosciuto.<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> Errore imprevisto restituito al server ACC.<br /> </td>
   <td> Il messaggio di errore è stato restituito ad ACC.<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** protocollo e **registerDeviceStatus** la definizione di delegato è la seguente:

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

Implementazione **registerDeviceStatus** delegare, segui questi passaggi:

1. Implementare **setDelegate** durante l&#39;inizializzazione dell&#39;SDK.

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

1. Aggiungi il protocollo nel **@interface** della tua classe.

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

1. Implementa il delegato nel **AppDelegate**.

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

## Variabili {#variables}

Le variabili ti consentono di definire il comportamento dell’app mobile dopo aver ricevuto una notifica. Queste variabili devono essere definite nel codice dell’app mobile e nella console Adobe Campaign, nella **[!UICONTROL Variables]** scheda nel servizio dedicato per le applicazioni mobili (vedi [Configurazione di un’app mobile in Adobe Campaign](configuring-the-mobile-application.md)). Ecco un esempio di codice che consente a un’app mobile di raccogliere tutte le variabili aggiunte in una notifica. Nel nostro esempio, utilizziamo la variabile &quot;VAR&quot;.

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
>Adobe consiglia di scegliere nomi di variabili brevi perché le dimensioni di notifica sono limitate a 4kB per iOS e Android.

## Estensione del servizio di notifica {#notification-service-extension}

**Per iOS**

I file multimediali devono essere scaricati a livello di estensione del servizio di notifica.

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

## Estensione contenuto notifica {#notification-content-extension}

**Per iOS**

A questo livello, è necessario:

* Associa l’estensione del contenuto alla categoria inviata da Adobe Campaign:

   Se desideri che l’app mobile visualizzi un’immagine, puoi impostare il valore della categoria su &quot;image&quot; in Adobe Campaign e nella tua app mobile, crea un’estensione di notifica con il **UNNotificationExtensionCategory** impostato su &quot;image&quot;. Quando la notifica push viene ricevuta sul dispositivo, l&#39;estensione viene chiamata in base al valore di categoria definito.

* Definire il layout delle notifiche

   È necessario definire un layout con i widget pertinenti. Per un&#39;immagine, il widget viene denominato **UIImageView**.

* Visualizzare i supporti

   Devi aggiungere del codice per inviare i dati multimediali al widget. Ecco un esempio di codice per un&#39;immagine:

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
