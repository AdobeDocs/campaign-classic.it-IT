---
title: Configurazione del canale delle app mobili
seo-title: Configurazione del canale delle app mobili
description: Configurazione del canale delle app mobili
seo-description: null
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---


# Integrazione dell’SDK Campaign nell’app mobile {#integrating-campaign-sdk-into-the-mobile-application}

Gli SDK delle campagne per iOS e Android sono uno dei componenti del modulo Canale app mobile.

>[!NOTE]
>
>Per ottenere l&#39;SDK di Campaign (precedentemente noto come Neolane SDK), contatta &#39;Assistenza clienti del Adobe.

L’obiettivo dell’SDK è quello di facilitare l’integrazione di un’applicazione mobile nella piattaforma Adobe Campaign .

Per ulteriori informazioni sulle diverse versioni di Android e iOS supportate, fare riferimento alla matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#MobileSDK) compatibilità.

## Caricamento dell&#39;SDK della campagna {#loading-campaign-sdk}

* **In Android**: il file **neolane_sdk-release.aar** deve essere collegato al progetto.

   La seguente autorizzazione consente di accedere al server Adobe Campaign :

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
   ```

   La seguente autorizzazione consente di recuperare l&#39;ID univoco di un telefono:

   ```
   <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   ```

   Dalla versione 1.0.24 dell’SDK, questa autorizzazione è utilizzata solo per le versioni precedenti alla 6.0 di Android.

   Dalla versione 1.0.26 dell’SDK, questa autorizzazione non è più utilizzata.

* **In iOS**: i file **libNeolaneSDK.a** e **Neolane_SDK.h** devono essere collegati al progetto. Dalla versione 1.0.24 dell’SDK, l’opzione **ENABLE_BITCODE** è attivata.

   >[!NOTE]
   >
   >Per la versione 1.0.25 dell’SDK, le quattro architetture sono disponibili nel file **Neolane_SDK.h** .

## Dichiarazione delle impostazioni di integrazione {#declaring-integration-settings}

Per integrare Campaign SDK nell&#39;applicazione mobile, l&#39;amministratore funzionale deve fornire allo sviluppatore le seguenti informazioni:

* **Una chiave** di integrazione: per abilitare la piattaforma Adobe Campaign  per identificare l&#39;applicazione mobile.

   >[!NOTE]
   >
   >Questa chiave di integrazione viene immessa nella console  Adobe Campaign, nella **[!UICONTROL Information]** scheda del servizio dedicata all’applicazione mobile. Consultare [Configurazione di un’applicazione mobile in  Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

* **Un URL** di tracciamento: che corrisponde all&#39;indirizzo del server di tracciamento Adobe Campaign .
* **Un URL** di marketing: per abilitare la raccolta di sottoscrizioni.

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

* inviate l&#39;ID notifica o l&#39;ID push (deviceToken per iOS e registrationID per Android) a  Adobe Campaign.
* recuperare la chiave di riconciliazione o userKey (ad esempio, e-mail o numero account)

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

   Se utilizzi FCM (Firebase Cloud Messaging), ti consigliamo di utilizzare la funzione **registerDevice** quando chiami la funzione **onTokenRefresh** per notificare  Adobe Campaign la modifica apportata al token del dispositivo mobile dell&#39;utente.

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
   // Callback called on successful registration to the APNS
   - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
   {
       // Pass the token to Adobe Campaign
       Neolane_SDK *nl = [Neolane_SDK getInstance];
       [nl registerDevice:tokenString:self.userKey:dic];
   }
   ```

## Funzione di tracciamento {#tracking-function}

* **In Android**:

   Le funzioni di tracciamento consentono di tenere traccia delle attivazioni delle notifiche (aperture) e delle visualizzazioni delle notifiche (screenshot).

   Per tenere traccia della visualizzazione delle notifiche (richiamando la funzione **notificationReceive** dell’SDK), segui l’implementazione riportata di seguito. Se utilizzate FCM (Firebase Cloud Messaging), consigliamo di utilizzare la funzione **notificationReceive** quando la funzione **onMessageReceived** viene chiamata dal sistema Android.

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

   Di seguito è riportato un esempio di implementazione per il tracciamento di una notifica aperta (eseguita chiamando la funzione **notificationOpening** dell’SDK). La classe **NotificationActivity** corrisponde a quella utilizzata per creare l&#39;oggetto **NotificationIntent** nell&#39;esempio precedente.

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

   La funzione di tracciamento consente di tenere traccia di quando vengono attivate le notifiche (si apre).

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
   >Dalla versione 7.0, una volta implementata la funzione **application:didReceiveRemoteNotification:fetchCompletionHandler** , il sistema operativo chiama solo questa funzione. La funzione **application:didReceiveRemoteNotification** non viene pertanto chiamata.

## Tracciamento delle notifiche invisibili {#silent-notification-tracking}

iOS consente di inviare notifiche silenziose, una notifica o dati che verranno inviati direttamente a un&#39;applicazione mobile senza visualizzarli.  Adobe Campaign consente di seguirli.

Per tenere traccia della notifica invisibile, seguite l&#39;esempio seguente:

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

### RegisterDeviceStatus delegate {#registerdevicestatus-delegate}

>[!NOTE]
>
>Tieni presente che questo è esclusivo per iOS.

In iOS, il protocollo delegato consente di ottenere il risultato della chiamata **registerDevice** e può essere utilizzato per sapere se si è verificato un errore durante la registrazione.

Il prototipo **registerDeviceStatus** è:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Lo stato** consente di sapere se una registrazione ha avuto esito positivo o se si è verificato un errore.

**ErrorReason** fornisce ulteriori informazioni sugli errori che si sono verificati. Per ulteriori informazioni sugli errori disponibili e le relative descrizioni, fare riferimento alla tabella seguente.

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
   <td> Registrazione completata<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedMarketingServerHostnameEmpty <br /> </td>
   <td> Il nome host del server di marketing ACC è vuoto o non è impostato.<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedIntegrationKeyEmpty <br /> </td>
   <td> La chiave di integrazione è vuota o non impostata.<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedConnectionIssue<br /> </td>
   <td> Problema di connessione con ACC<br /> </td>
   <td> Ulteriori informazioni (nella lingua corrente del sistema operativo)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedUnknownUID<br /> </td>
   <td> L'UUID fornito (chiave di integrazione) è sconosciuto.<br /> </td>
   <td> VUOTO<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedUnexpectedError<br /> </td>
   <td> Errore imprevisto restituito al server ACC.<br /> </td>
   <td> Il messaggio di errore è stato restituito ad ACC.<br /> </td>
  </tr>
 </tbody>
</table>

**Il protocollo Neolane_SDKDelegate** e la definizione **registerDeviceStatus** delegate sono le seguenti:

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

Per implementare **registerDeviceStatus** delegate, effettua le seguenti operazioni:

1. Implementa **setDelegate** durante l&#39;inizializzazione dell&#39;SDK.

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

1. Aggiungete il protocollo nell&#39; **@interface** della classe.

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

1. Implementa il delegato in **AppDelegate**.

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

Le variabili consentono di definire il comportamento dell’applicazione mobile dopo la ricezione di una notifica. Queste variabili devono essere definite nel codice dell’applicazione mobile e nella  console Adobe Campaign, nella **[!UICONTROL Variables]** scheda del servizio applicazione mobile dedicato (consultate [Configurazione di un’applicazione mobile in  Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md)). Di seguito è riportato un esempio di codice che consente a un&#39;applicazione mobile di raccogliere eventuali variabili aggiunte in una notifica. Nel nostro esempio, utilizziamo la variabile &quot;VAR&quot;.

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
> Adobe consiglia di scegliere nomi di variabili brevi perché la dimensione di notifica è limitata a 4kB per iOS e Android.

## Estensione del servizio di notifica {#notification-service-extension}

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

## Estensione contenuto notifica {#notification-content-extension}

**Per iOS**

A questo livello, è necessario:

* Associate l&#39;estensione di contenuto alla categoria inviata da  Adobe Campaign:

   Se desiderate che l’applicazione mobile visualizzi un’immagine, potete impostare il valore della categoria su &quot;image&quot; in  Adobe Campaign e nell’applicazione mobile, create un’estensione di notifica con il parametro **UNNotificationExtensionCategory** impostato su &quot;image&quot;. Quando la notifica push viene ricevuta sul dispositivo, l&#39;estensione viene chiamata in base al valore della categoria definito.

* Definire il layout di notifica

   È necessario definire un layout con i widget rilevanti. Per un’immagine, il widget è denominato **UIImageView**.

* Visualizzare i supporti

   È necessario aggiungere del codice per inviare i dati multimediali al widget. Esempio di codice per un’immagine:

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
