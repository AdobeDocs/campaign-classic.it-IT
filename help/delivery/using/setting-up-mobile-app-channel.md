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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Configurazione del canale delle app mobili{#setting-up-mobile-app-channel}

## Introduzione {#introduction}

>[!CAUTION]
>
>L’implementazione del canale app mobile deve essere eseguita da utenti esperti. Se avete bisogno di assistenza, contattate il vostro responsabile Adobe Account o il partner di servizi Professional.

Puoi creare diverse versioni dell’applicazione mobile (iOS, Android): l&#39;opzione Canale app mobile consente di inviare notifiche ai terminali in cui è installata l&#39;applicazione.

Per utilizzare le funzionalità di Adobe Campaign Mobile App Channel, devi modificare/adattare l&#39;applicazione mobile per integrarla nella piattaforma Adobe Campaign.

Sono disponibili due SDK Campaign Classic, uno per Android e uno per iOS, per una facile integrazione dell&#39;applicazione mobile con Adobe Campaign. È necessaria una profonda conoscenza tecnica di Java e Objective-C. Una descrizione dettagliata dell&#39;SDK di Campaign si trova in [Integrazione dell&#39;SDK di Campaign nell&#39;applicazione](#integrating-campaign-sdk-into-the-mobile-application)mobile.

>[!NOTE]
>
>Le librerie fornite da Adobe Campaign sono progettate per essere utilizzate con Xcode (iOS) e Android Studio (Android).

## Connettori {#connectors}

### Connettori iOS {#ios-connectors}

Per iOS, sono disponibili due connettori:

* Il connettore binario iOS invia le notifiche sul server binario precedente APNS.
* Il connettore iOS HTTP/2 invia le notifiche all&#39;APNS HTTP/2.

Per scegliere quale connettore utilizzare, procedere come segue:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Selezionate l&#39;account esterno di routing iOS.
1. Nella **[!UICONTROL Connector]** scheda, compila il **[!UICONTROL Access URL of the connector]** campo:

   Per binario iOS: https://localhost:8080/nms/jsp/ios.jsp

   Per iOS HTTP2: http://localhost:8080/nms/jsp/iosHTTP2.jsp

   ![](assets/nmac_connectors.png)

### Connettori Android {#android-connectors}

Per Android sono disponibili due connettori:

* Connettore V1 che consente una connessione per MTA figlio.
* Connettore V2 che consente connessioni simultanee al server FCM per migliorare il throughput.

Per scegliere quale connettore utilizzare, procedere come segue:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Selezionate l’account **[!UICONTROL Android routing]** esterno.
1. Nella **[!UICONTROL Connector]** scheda, compila il **[!UICONTROL JavaScript used in the connector]** campo:

   Per Android V1: https://localhost:8080/nms/jsp/androidPushConnector.js

   Per Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   ![](assets/nmac_connectors3.png)

1. Per Android V2, nel file di configurazione di Adobe Server (serverConf.xml) è disponibile un parametro aggiuntivo:

   * **maxGCMConnectPerChild**: Limite massimo di richieste HTTP parallele a FCM avviate da ciascun server figlio (per impostazione predefinita, 8).

## Passaggi di configurazione {#configuration-steps}

### Creazione dell’applicazione {#creating-the-application}

Se non disponi di un’applicazione mobile (app), lo sviluppatore di applicazioni deve crearla e integrare l’SDK. Se l’applicazione per dispositivi mobili esiste, lo sviluppatore deve adattarla integrando l’SDK di Adobe Campaign e aggiungendo le impostazioni specifiche del servizio. Per una descrizione dell&#39;SDK, consulta [Integrazione dell&#39;SDK di Campaign nell&#39;applicazione](#integrating-campaign-sdk-into-the-mobile-application)mobile.

>[!CAUTION]
>
>L&#39;applicazione deve essere stata configurata per le azioni push PRIMA di qualsiasi integrazione con Adobe Campaign SDK.
>
>In caso contrario, fare riferimento a [questa pagina](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

### Raccolta di informazioni {#collecting-information-}

Per configurare l&#39;applicazione, devi raccogliere le specifiche tecniche che definiscono il set di parametri che consentono ad Adobe Campaign e all&#39;applicazione mobile di comunicare. Questi parametri sono:

* **la chiave** di integrazione: ogni applicazione ha una chiave univoca. Questa chiave consente di collegare il servizio Adobe Campaign e l&#39;applicazione mobile. Fare riferimento a [Informazioni](#general-information)generali.
* **le variabili**: definire il comportamento dell&#39;applicazione quando si attiva la notifica. Fare riferimento a [Informazioni](#general-information)generali.
* **le impostazioni** di iscrizione: per impostazione predefinita, Adobe Campaign recupera il campo **@userKey** che consente di riconciliare i dispositivi mobili con i destinatari nel database. Se desiderate raccogliere dati aggiuntivi (ad esempio una chiave di riconciliazione complessa), potete definire le impostazioni di iscrizione. Fate riferimento alle impostazioni [di](#subscription-settings)iscrizione.
* **i suoni** (solo iOS): se l&#39;audio selezionato non è un suono del sistema, il file audio deve essere incorporato nell&#39;applicazione mobile. Fare riferimento ai suoni [](#application-sounds)dell&#39;applicazione.
* **l’URL del server di marketing e del server** di tracciamento: l&#39;amministratore di Adobe Campaign deve fornire allo sviluppatore dell&#39;applicazione gli URL del server di marketing e gli URL del server di tracciamento. Per ulteriori informazioni, consulta: [Integrazione di Campaign SDK nell&#39;applicazione](#integrating-campaign-sdk-into-the-mobile-application)mobile.

### Creazione del servizio {#creating-the-service}

L&#39;amministratore di Adobe Campaign deve creare e configurare un servizio collegato all&#39;applicazione mobile. Per ulteriori informazioni, consulta [Configurazione dell’applicazione mobile in Adobe Campaign](#configuring-the-mobile-application-in-adobe-campaign).

### Verifica dell’applicazione {#testing-the-application}

In iOS, è necessario creare un&#39;applicazione che utilizza la modalità sandbox per test e approvazioni. Quindi, all&#39;interno dello stesso servizio Adobe Campaign, crea una nuova applicazione di tipo produzione e immetti il certificato appropriato. Per ulteriori informazioni, consulta la documentazione del servizio di notifica Apple.

Su Android, è sufficiente creare una sola applicazione. Verificate l&#39;intero processo di iscrizione e consegna dell&#39;applicazione prima di renderla pubblica.

## Percorso dati {#data-path}

Gli schemi seguenti descrivono i passaggi che consentono a un&#39;applicazione mobile di scambiare dati con Adobe Campaign. Questo processo coinvolge tre entità:

* l’applicazione mobile
* il servizio di notifica: APNS (Apple Push Notification Service) per Apple e FCM (Firebase Cloud Messaging) per Android
* Adobe Campaign

Le tre fasi principali del processo di notifica sono: registrazione dell&#39;applicazione in Adobe Campaign (raccolta di iscrizioni), consegne e tracciamento.

### Passaggio 1: Raccolta di iscrizioni {#step-1--subscription-collection}

L’applicazione mobile viene scaricata dall’utente dall’App Store o da Google Play. Questa applicazione contiene le impostazioni di connessione (certificato iOS e chiave di progetto per Android) e la chiave di integrazione. La prima volta che l&#39;applicazione viene aperta (a seconda della configurazione), all&#39;utente può essere chiesto di immettere le informazioni di registrazione (@userKey: indirizzo e-mail o numero di account, ad esempio). Allo stesso tempo, l&#39;applicazione contesta al servizio di notifica di raccogliere un ID di notifica (ID push). Tutte queste informazioni (impostazioni di connessione, chiave di integrazione, identificatore di notifica, userKey) vengono inviate ad Adobe Campaign.

![](assets/nmac_register_view.png)

### Passaggio 2: Consegna {#step-2--delivery}

Gli addetti al marketing eseguono il targeting degli abbonati alle applicazioni. Il processo di consegna invia le impostazioni di connessione al servizio di notifica (certificato iOS e chiave di progetto per Android), all&#39;ID di notifica (ID push) e al contenuto della notifica. Il servizio di notifica invia notifiche ai terminali di destinazione.

In Adobe Campaign sono disponibili le seguenti informazioni:

* Solo Android: numero di dispositivi che hanno visualizzato la notifica (impression)
* Android e iOS: numero di clic sulla notifica

![](assets/nmac_delivery_view.png)

Il server Adobe Campaign deve essere in grado di contattare il server APNS nelle seguenti porte:

* 2195 (invio) e 2186 (servizio di feedback) per connettore binario iOS
* 443 per il connettore iOS HTTP/2

Per verificare che funzioni correttamente, usate i seguenti comandi:

* Per le prove:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* In produzione:

   ```
   telnet gateway.push.apple.com
   ```

Se viene utilizzato un connettore binario iOS, MTA e il server Web devono essere in grado di contattare APNS sulla porta 2195 (invio), il server del flusso di lavoro deve essere in grado di contattare APNS sulla porta 2196 (servizio di feedback).

Se si utilizza un connettore iOS HTTP/2, MTA, server Web e server di workflow devono essere in grado di contattare APNS sulla porta 443.

## Integrazione di Campaign SDK nell&#39;applicazione mobile {#integrating-campaign-sdk-into-the-mobile-application}

Gli SDK delle campagne per iOS e Android sono uno dei componenti del modulo Canale app mobile.

>[!NOTE]
>
>Per ottenere l&#39;SDK di Campaign (precedentemente noto come Neolane SDK), contatta l&#39;Assistenza clienti Adobe.

L&#39;obiettivo dell&#39;SDK è quello di facilitare l&#39;integrazione di un&#39;applicazione mobile nella piattaforma Adobe Campaign.

Per ulteriori informazioni sulle diverse versioni di Android e iOS supportate, consultate la matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#MobileSDK) compatibilità .

### Caricamento dell&#39;SDK della campagna {#loading-campaign-sdk}

* **In Android**: il file **neolane_sdk-release.aar** deve essere collegato al progetto.

   La seguente autorizzazione consente di accedere al server Adobe Campaign:

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

### Dichiarazione delle impostazioni di integrazione {#declaring-integration-settings}

Per integrare Campaign SDK nell&#39;applicazione mobile, l&#39;amministratore funzionale deve fornire allo sviluppatore le seguenti informazioni:

* **Una chiave** di integrazione: per abilitare la piattaforma Adobe Campaign per identificare l&#39;applicazione mobile.

   >[!NOTE]
   >
   >Questa chiave di integrazione viene immessa nella console di Adobe Campaign, nella **[!UICONTROL Information]** scheda del servizio dedicata all’applicazione per dispositivi mobili. Fare riferimento a [Informazioni](#general-information)generali.

* **Un URL** di tracciamento: che corrisponde all&#39;indirizzo del server di tracciamento di Adobe Campaign.
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

### Funzione di registrazione {#registration-function}

La funzione di registrazione consente di:

* invia l&#39;ID notifica o l&#39;ID push (deviceToken per iOS e registrationID per Android) ad Adobe Campaign.
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

   Se utilizzi FCM (Firebase Cloud Messaging), ti consigliamo di utilizzare la funzione **registerDevice** quando chiami la funzione **onTokenRefresh** per notificare ad Adobe Campaign la modifica apportata al token del dispositivo mobile dell&#39;utente.

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

### Funzione di tracciamento {#tracking-function}

* **In Android**:

   Le funzioni di tracciamento consentono di tenere traccia delle attivazioni delle notifiche (aperture) e delle visualizzazioni delle notifiche (schermata).

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
    public static final String NOTIFICATION_URL_KEYNAME = "NotificationUrl";
    .....
    public void onCreate(Bundle savedBundle) {
     super.onCreate(savedBundle);
     setContentView(R.layout.notification_viewer);  
     .....  
     Bundle extra = getIntent().getExtras();  
     .....  
     //get the messageId and the deliveryId to do the tracking  
     String deliveryId = extra.getString("_dId");
     String messageId = extra.getString("_mId");
     if (deliveryId != null && messageId != null) {
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      neolaneAs.notifyOpening(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
       public void onNeolaneException(NeolaneException arg0, Object arg1) {}
       public void onIOException(IOException arg0, Object arg1) {}
       public void onComplete(String arg0, Object arg1) {}
       });
     }
    }
   }
   ```

* **In iOS**:

   La funzione di tracciamento consente di monitorare quando vengono attivate le notifiche (si apre).

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

### Tracciamento delle notifiche invisibili {#silent-notification-tracking}

iOS consente di inviare notifiche silenziose, una notifica o dati che verranno inviati direttamente a un&#39;applicazione mobile senza visualizzarli. Adobe Campaign consente di seguirli.

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

**ErrorReason** fornisce ulteriori informazioni sugli errori che si sono verificati. Per ulteriori informazioni sugli errori disponibili e le relative descrizioni, consultare la tabella seguente.

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
   <td> Messaggio di errore restituito ad ACC.<br /> </td>
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

### Variabili {#variables}

Le variabili consentono di definire il comportamento dell’applicazione mobile dopo la ricezione di una notifica. Queste variabili devono essere definite nel codice dell’applicazione mobile e nella console di Adobe Campaign, nella **[!UICONTROL Variables]** scheda del servizio applicazione mobile dedicato (consultate Informazioni [generali](#general-information)). Di seguito è riportato un esempio di codice che consente a un&#39;applicazione mobile di raccogliere eventuali variabili aggiunte in una notifica. Nel nostro esempio, utilizziamo la variabile &quot;VAR&quot;.

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
>Adobe consiglia di scegliere nomi di variabili brevi perché la dimensione di notifica è limitata a 4 kB per iOS e Android.

## Configurazione dell’applicazione mobile in Adobe Campaign {#configuring-the-mobile-application-in-adobe-campaign}

Di seguito è riportato un esempio di configurazione basato su una società che vende pacchetti per le vacanze online. La sua applicazione mobile (Neotrips) è disponibile ai suoi clienti in due versioni: Neotrips per Android e Neotrips per iOS. Per configurare l&#39;applicazione mobile in Adobe Campaign, devi:

1. Create un servizio **[!UICONTROL Mobile application]** di [](#creating-the-service-and-collecting-subscriptions) informazioni di tipo per l’applicazione mobile Neotrips.
1. Aggiungete al servizio le versioni iOS e Android dell&#39;applicazione.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Passate alla **[!UICONTROL Subscriptions]** scheda del servizio per visualizzare l’elenco degli utenti iscritti al servizio, ovvero tutti gli utenti che hanno installato l’applicazione sul proprio dispositivo mobile e hanno accettato di ricevere le notifiche.

### Creazione del servizio e raccolta delle sottoscrizioni {#creating-the-service-and-collecting-subscriptions}

1. Vai al **[!UICONTROL Profiles and Targets > Services and subscriptions]** nodo e fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definire un **[!UICONTROL Label]** e un **[!UICONTROL Internal name]**.
1. Vai al **[!UICONTROL Type]** campo e seleziona **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Il mapping di **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** destinazione predefinito è collegato alla tabella dei destinatari. Se desiderate utilizzare un mapping di destinazione diverso, dovete creare un nuovo mapping di destinazione e immetterlo nel **[!UICONTROL Target mapping]** campo del servizio. Per ulteriori informazioni sulla creazione della mappatura di destinazione, consulta la guida [alla](../../configuration/using/about-custom-recipient-table.md)configurazione.

1. Quindi fate clic sul **[!UICONTROL Add]** pulsante per definire le diverse versioni dell’applicazione mobile (iOS, Android).

   ![](assets/nmac_service_2.png)

Consultate di seguito per una presentazione dettagliata dei passaggi di configurazione per ciascuna versione.

>[!NOTE]
>
>Quando create un&#39;applicazione iOS, la procedura guidata vi invita a configurare la versione di sviluppo (sandbox) dell&#39;applicazione e la versione di produzione. Una volta create, le due versioni dell&#39;applicazione vengono aggiunte.

### Informazioni generali {#general-information}

![](assets/nmac_service_3.png)

1. Inizia inserendo il **[!UICONTROL Label]**.
1. Assicurati che lo stesso **[!UICONTROL Integration key]** sia definito in Adobe Campaign e nel codice dell&#39;applicazione (tramite l&#39;SDK). Per ulteriori informazioni, consulta: [Integrazione di Campaign SDK nell&#39;applicazione](#integrating-campaign-sdk-into-the-mobile-application)mobile. Questa chiave di integrazione, specifica per ogni applicazione, consente di collegare l&#39;applicazione mobile alla piattaforma Adobe Campaign.
1. Se l’applicazione gestisce l’icona di un’applicazione (angolo in alto a sinistra della notifica), potete aggiungerla qui in modo che l’anteprima sia più fedele allo stile effettivo della consegna. Per aggiungere un&#39;immagine al contenuto (notifica RTF), consultate la sezione Notifiche [](#rich-notifications) avanzate.

   >[!CAUTION]
   >
   >La risoluzione prevista per le immagini è di 48x48 pixel per iOS.

1. Per Android, immettete le impostazioni di connessione dell&#39;applicazione: immettete la chiave di progetto fornita dallo sviluppatore dell’applicazione mobile.
1. Immettete quindi le variabili dell’applicazione.

   ![](assets/nmac_service_4.png)

   Le variabili consentono di definire il comportamento dell&#39;applicazione dopo la ricezione di una notifica: ad esempio, potete configurare una schermata specifica per l’applicazione affinché venga visualizzata quando l’utente attiva la notifica. Queste variabili devono essere definite nel codice dell’applicazione mobile. Fai clic sul **[!UICONTROL Add]** pulsante per aggiungerli ad Adobe Campaign.

   La procedura guidata di consegna consente di definire i valori di queste variabili. Fare riferimento a [Creazione di notifiche](../../delivery/using/creating-notifications.md).

### Impostazioni iscrizione {#subscription-settings}

>[!NOTE]
>
>Questa scheda deve essere configurata solo se si desidera raccogliere dati aggiuntivi.

![](assets/nmac_service_5.png)

Per impostazione predefinita, Adobe Campaign salva una chiave nel campo **[!UICONTROL User identifier]** (@userKey) della **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabella. Questa chiave consente di collegare un&#39;iscrizione a un destinatario. Per raccogliere dati aggiuntivi (ad esempio una chiave di riconciliazione complessa), è necessario applicare la seguente configurazione:

1. Create un&#39;estensione dello **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema e definite i nuovi campi.
1. Definite la mappatura nella **[!UICONTROL Subscription parameters]** scheda.

   >[!CAUTION]
   >
   >Accertatevi che i nomi di configurazione nella **[!UICONTROL Subscription parameters]** scheda siano identici a quelli nel codice dell&#39;applicazione mobile. Fai riferimento all&#39;SDK [Integrating Campaign nella sezione dell&#39;applicazione](#integrating-campaign-sdk-into-the-mobile-application) mobile.

### Suoni applicazione {#application-sounds}

>[!NOTE]
>
>Questa scheda è disponibile solo per le versioni iOS delle applicazioni.

![](assets/nmac_service_6.png)

Se l&#39;applicazione iOS include dei suoni incorporati, utilizzate questa scheda per aggiungerli. Potrete quindi utilizzare la procedura guidata di consegna per selezionare uno dei suoni da riprodurre al ricevimento della notifica. Per ulteriori informazioni, consulta [Invio di notifiche su iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios).

>[!NOTE]
>
>I suoni di sistema possono essere definiti anche in questa schermata.

Nella **[!UICONTROL Application setting]** schermata, il **[!UICONTROL Internal name]** campo deve contenere il nome del file incorporato nell&#39;applicazione o il nome dell&#39;audio di sistema. Il valore immesso nel **[!UICONTROL Label]** campo verrà visualizzato nell&#39;elenco a **[!UICONTROL Play a sound]** discesa della procedura guidata di consegna.

### Certificato {#certificate}

>[!NOTE]
>
>Questa scheda è disponibile solo per le versioni iOS delle applicazioni.

In questa schermata, immettete le impostazioni di connessione dell’applicazione.

![](assets/nmac_service_7.png)

Fate clic sul **[!UICONTROL Enter the certificate...]** collegamento, quindi selezionate il certificato di autenticazione e immettete la password fornita dallo sviluppatore di applicazioni mobili.

>[!NOTE]
>
>Accertatevi di non utilizzare lo stesso certificato per la versione di sviluppo (sandbox) e per la versione di produzione dell&#39;applicazione.

## Notifiche potenziate {#rich-notifications}

Una notifica avanzata consente di includere altri tipi di supporti nelle notifiche, come immagini, video e così via.

### Android {#android}

Adobe Campaign consente di definire le variabili di applicazione oltre al contenuto (consultate [Invio di notifiche su Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)). Queste variabili possono essere utilizzate per fornire informazioni come l&#39;URL dell&#39;immagine per l&#39;applicazione mobile. L’applicazione per dispositivi mobili può quindi generare una notifica personalizzata.

Devi prima creare un&#39;applicazione mobile in Adobe Campaign e definire le variabili dell&#39;applicazione per tale applicazione.

1. Vai a **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Services and Subscriptions]**.
1. Fate clic **[!UICONTROL New]** per creare un servizio.
1. Nella **[!UICONTROL Edit]** scheda, seleziona **[!UICONTROL Mobile application]** come **[!UICONTROL Type]** e **[!UICONTROL Subscriber application]** (nms:appSubscriptionRcp) come **[!UICONTROL Target mapping]**.
1. In **[!UICONTROL List of mobile applications that use the service]**, aggiungete una nuova applicazione e selezionate **[!UICONTROL Create an Android application]**.
1. Clic **[!UICONTROL Next]**.
1. Nella **[!UICONTROL Information]** scheda della procedura guidata di creazione, immettere un&#39;etichetta.
1. Nel **[!UICONTROL Application variables]** campo, aggiungete i parametri che desiderate utilizzare per inviare un push potenziato:

   * title
   * sub
   * validation
   * imageURL
   * webpageURL

1. Fate clic su **[!UICONTROL Finish]** e salvate il servizio.

   ![](assets/nmac_rich_android_config.png)

Quindi devi creare un nuovo modello di consegna e collegarlo all’applicazione mobile che hai creato.

1. Vai a **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Duplica il **[!UICONTROL Deliver on Android]** modello.
1. Modificate l’etichetta e fate clic **[!UICONTROL Continue]**.
1. Fate clic sul **[!UICONTROL To]** collegamento per eseguire il targeting degli utenti iscritti all&#39;applicazione.
1. Cambia il **[!UICONTROL Target mapping]** campo in **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**.

   ![](assets/nmac_rich_android_target_mapping.png)

1. Fate clic **[!UICONTROL Add]**, selezionate **[!UICONTROL Subscribers of an Android mobile application]** e fate clic su **[!UICONTROL Next]**.
1. Immettete un&#39;etichetta, selezionate il servizio creato e l&#39;applicazione mobile creata all&#39;interno del servizio.

   ![](assets/nmac_rich_android_mobile_app.png)

1. Clic **[!UICONTROL Finish]**.

I parametri creati all’interno dell’applicazione mobile vengono visualizzati nel campo delle variabili **** applicazione.

![](assets/nmac_rich_android_template.png)

Infine, create una nuova distribuzione Android e aggiungete i valori desiderati per i parametri definiti nell&#39;applicazione mobile.

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.
1. Clic **[!UICONTROL New]**.
1. Selezionate il modello di consegna appena creato e fate clic su **[!UICONTROL Continue]**.
1. Nel **[!UICONTROL Application variables]** campo, aggiungere i valori desiderati per i diversi parametri.

   ![](assets/nmac_rich_android_delivery.png)

1. Fai clic su **[!UICONTROL Save]** e invia la consegna.

L&#39;immagine e la pagina Web devono essere visualizzate nella notifica push quando vengono ricevute sui dispositivi mobili Android degli abbonati.

### iOS {#ios}

Con iOS 10 o versione successiva, è possibile generare notifiche avanzate. Adobe Campaign può inviare notifiche utilizzando variabili che consentiranno al dispositivo di visualizzare una notifica avanzata.

>[!NOTE]
>
>Se desiderate utilizzare le notifiche avanzate, dovete utilizzare il connettore iOS HTTP/2. Fare riferimento alla sezione [Connettori](#connectors) .

In Adobe Campaign, i seguenti parametri devono essere inviati all&#39;applicazione mobile:

* Selezionate la **[!UICONTROL Mutable content]** casella nella finestra di notifica di modifica. In questo modo l&#39;applicazione mobile potrà scaricare il contenuto multimediale.
* Il **[!UICONTROL Category]** campo deve essere impostato. Il valore deve corrispondere a una delle estensioni di contenuto dell’applicazione mobile (parametro **UNNotificationExtensionCategory**).
* Nelle variabili dell’applicazione, aggiungete l’URL del file multimediale da scaricare e visualizzare nell’applicazione mobile.

   ![](assets/nmac_connectors2.png)

Per implementare notifiche avanzate nell’applicazione mobile, devi aggiungere le seguenti estensioni al progetto:

* Estensione del servizio di notifica
* Estensione contenuto notifica (una o più a seconda dell’implementazione)

**Estensione del servizio di notifica**

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

**Estensione contenuto notifica**

A questo livello, è necessario:

* Associa l&#39;estensione del contenuto alla categoria inviata da Adobe Campaign:

   Se desiderate che l’applicazione mobile visualizzi un’immagine, potete impostare il valore della categoria su &quot;image&quot; in Adobe Campaign e nell’applicazione mobile, create un’estensione di notifica con il parametro **UNNotificationExtensionCategory** impostato su &quot;image&quot;. Quando la notifica push viene ricevuta sul dispositivo, l&#39;estensione viene chiamata in base al valore della categoria definito.

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
