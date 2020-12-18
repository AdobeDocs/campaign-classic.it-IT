---
solution: Campaign Classic
product: campaign
title: Configurazione dell’applicazione mobile Android in  Adobe Campaign
description: Scopri come configurare l’applicazione mobile per Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 2%

---


# Passaggi di configurazione per Android

Una volta installato il pacchetto, potete definire le impostazioni dell&#39;app Android in Adobe Campaign Classic.

>[!NOTE]
>
>Per informazioni su come configurare l&#39;app per iOS e su come creare una consegna per iOS, consultate questa [sezione](../../delivery/using/configuring-the-mobile-application.md).

I passaggi chiave sono:

1. [Configurare l&#39;account esterno Android](#configuring-external-account-android)
1. [Configurare il servizio Android](#configuring-android-service)
1. [Creare l&#39;app mobile in Campaign](#creating-android-app)
1. [Estendi lo schema dell&#39;app con dati aggiuntivi](#extend-subscription-schema)

Potrete quindi [creare una notifica Android rich](#creating-android-delivery).

## Configurazione dell&#39;account esterno Android {#configuring-external-account-android}

Per Android sono disponibili due connettori:

* Connettore V1 che consente una connessione per MTA figlio.
* Connettore V2 che consente connessioni simultanee al server FCM per migliorare il throughput.

Per scegliere quale connettore utilizzare, procedere come segue:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Selezionare l&#39;account esterno **[!UICONTROL Android routing]**.
1. Nella scheda **[!UICONTROL Connector]**, compilare il campo **[!UICONTROL JavaScript used in the connector]**:

   Per Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > È inoltre possibile configurarlo come segue https://localhost:8080/nms/jsp/androidPushConnector.js, ma si consiglia di utilizzare la versione 2 del connettore.

   ![](assets/nmac_connectors3.png)

1. Per Android V2, un parametro aggiuntivo è disponibile nel file di configurazione del server di Adobe  (serverConf.xml):

   * **maxGCMConnectPerChild**: Limite massimo di richieste HTTP parallele a FCM avviate da ciascun server figlio (per impostazione predefinita, 8).

## Configurazione del servizio Android {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Scoprite come configurare un servizio Android in un video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Andate al nodo **[!UICONTROL Profiles and Targets > Services and subscriptions]** e fate clic su **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definire **[!UICONTROL Label]** e **[!UICONTROL Internal name]**.
1. Andate al campo **[!UICONTROL Type]** e selezionate **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Il mapping di destinazione predefinito **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** è collegato alla tabella dei destinatari. Se desiderate utilizzare un mapping di destinazione diverso, dovete creare un nuovo mapping di destinazione e immetterlo nel campo **[!UICONTROL Target mapping]** del servizio. Per ulteriori informazioni sulla creazione della mappatura di destinazione, fare riferimento alla [Guida alla configurazione](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Quindi fare clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Create la vostra applicazione Android. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app).

## Creazione di un&#39;applicazione mobile Android {#creating-android-app}

Dopo aver creato il servizio, è ora necessario creare l&#39;applicazione Android:

1. Dal servizio appena creato, fate clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Selezionare **[!UICONTROL Create an Android application]** e inserire un **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Assicurati che lo stesso **[!UICONTROL Integration key]** sia definito in  Adobe Campaign e nel codice dell&#39;applicazione tramite l&#39;SDK. Per ulteriori informazioni, consulta: [Integrazione di Campaign SDK nell&#39;applicazione mobile](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** è completamente personalizzabile con valore stringa, ma deve corrispondere esattamente a quello specificato nell&#39;SDK.

1. Selezionare **[!UICONTROL API version]**: HTTP v1 o HTTP (precedente). Queste configurazioni sono descritte in [questa sezione](#select-api-version)

1. Compila i campi **[!UICONTROL Firebase Cloud Messaging the Android connection settings]**.

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L&#39;applicazione Android ora è pronta per essere utilizzata in Campaign Classic.

Per impostazione predefinita,  Adobe Campaign salva una chiave nel campo **[!UICONTROL User identifier]** (@userKey) della tabella **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Questa chiave consente di collegare un&#39;iscrizione a un destinatario. Per raccogliere dati aggiuntivi (ad esempio una chiave di riconciliazione complessa), è necessario applicare la seguente configurazione:

### Selezionate la versione API{#select-api-version}

Dopo aver creato un servizio e una nuova applicazione mobile, è necessario configurare l&#39;applicazione mobile in base alla versione API scelta.

* **La** configurazione HTTP v1 [ è dettagliata in questa ](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1)sezione.
* **La** configurazione HTTP (legacy) è dettagliata in questa  [sezione](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http).

#### Configurare l&#39;API HTTP v1{#android-service-httpv1}

Per configurare la versione dell&#39;API HTTP v1, attenetevi alla seguente procedura:

1. Nella finestra **[!UICONTROL Mobile application creation wizard]**, selezionare **[!UICONTROL HTTPV1]** nel menu a discesa **[!UICONTROL API version]**.

1. Fare clic su **[!UICONTROL Load project json file to extract projet details...]** per caricare direttamente il file di chiave JSON. Per ulteriori informazioni su come estrarre il file JSON, fare riferimento a questa [pagina](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Potete anche immettere manualmente i seguenti dettagli:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Fate clic su **[!UICONTROL Test the connection]** per verificare che la configurazione sia corretta e che il server di marketing abbia accesso al MCM.

   >[!CAUTION]
   >
   >Per la distribuzione mid-Sourcing, il pulsante **[!UICONTROL Test connection]** non verificherà se il server MID ha accesso al server FCM.

   ![](assets/nmac_android_11.png)

1. Come opzione, puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]**, se necessario. Sono completamente personalizzabili e una parte del payload di messaggi inviato al dispositivo mobile.

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L&#39;applicazione Android ora è pronta per essere utilizzata in Campaign Classic.

Di seguito sono riportati i nomi dei payload FCM per personalizzare ulteriormente la notifica push:

| Tipo di messaggio | Elemento messaggio configurabile (nome payload FCM) | Opzioni configurabili (nome payload FCM) |
|:-:|:-:|:-:|
| messaggio dati | N/D | validate_only |
| messaggio di notifica | titolo, corpo, android_channel_id, icona, suono, tag, colore, click_action, immagine, ticker, persistente, visibilità, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### Configurare l&#39;API HTTP (precedente){#android-service-http}

Per configurare la versione API HTTP (precedente), attenetevi alla procedura seguente:

1. Nella finestra **[!UICONTROL Mobile application creation wizard]**, selezionare **[!UICONTROL HTTP (legacy)]** nel menu a discesa **[!UICONTROL API version]**.

1. Immettere il **[!UICONTROL Project key]** fornito dallo sviluppatore dell&#39;applicazione mobile.

1. Come opzione, puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]**, se necessario. Sono completamente personalizzabili e una parte del payload di messaggi inviato al dispositivo mobile.

   Nell&#39;esempio seguente, per creare una notifica push potenziata aggiungiamo **title**, **imageURL** e **iconURL** e quindi l&#39;applicazione dispone dell&#39;immagine, del titolo e dell&#39;icona da visualizzare all&#39;interno della notifica.

   ![](assets/nmac_android_2.png)

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L&#39;applicazione Android ora è pronta per essere utilizzata in Campaign Classic.

Di seguito sono riportati i nomi dei payload FCM per personalizzare ulteriormente la notifica push:

| Tipo di messaggio | Elemento messaggio configurabile (nome payload FCM) | Opzioni configurabili (nome payload FCM) |
|:-:|:-:|:-:|
| messaggio dati | N/D | dryRun |
| messaggio di notifica | titolo, corpo, android_channel_id, icona, suono, tag, colore, click_action <br> | dryRun |

<br>

## Estendi lo schema appsubscriptionRcp {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Scoprite come estendere lo schema appsubscriptionRcp nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

È necessario estendere **appsubscriptionRcp** per definire nuovi campi aggiuntivi per memorizzare i parametri dall&#39;app nel database di Campaign. Questi campi verranno utilizzati ad esempio per la personalizzazione. Per eseguire questa operazione:

1. Create un&#39;estensione dello schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** e definite i nuovi campi. Ulteriori informazioni sull&#39;estensione dello schema in [questa pagina](../../configuration/using/about-schema-edition.md)

1. Definire la mappatura nella scheda **[!UICONTROL Subscription parameters]**.

   >[!CAUTION]
   >
   >Accertatevi che i nomi di configurazione nella scheda **[!UICONTROL Subscription parameters]** siano identici a quelli nel codice dell&#39;applicazione mobile. Fare riferimento alla sezione [Integrazione di Campaign SDK nell&#39;applicazione mobile](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

## Creazione di una notifica Android rich {#creating-android-delivery}

Con Firebase Cloud Messaging, puoi scegliere tra due tipi di messaggi:

* **[!UICONTROL Data message]**, gestito dall&#39;app client.
   <br>I messaggi vengono inviati direttamente all&#39;applicazione mobile che genererà e visualizzerà la notifica android al dispositivo. I messaggi di dati contengono solo le variabili di applicazione personalizzate.

* **[!UICONTROL Notification message]**, gestito automaticamente da FCM SDK.
   <br> FCM visualizza automaticamente il messaggio sui dispositivi degli utenti per conto dell&#39;app client. I messaggi di notifica contengono un set predefinito di parametri e opzioni, ma possono essere ulteriormente personalizzati con variabili di applicazione personalizzate.

Per ulteriori informazioni sui tipi di messaggi di Firebase Cloud Messaging, consultare la [documentazione di FCM](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

### Creazione di un messaggio dati {#creating-data-message}

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selezionare **[!UICONTROL Deliver on Android (android)]** nel menu a discesa **[!UICONTROL Delivery template]**. Aggiungi un **[!UICONTROL Label]** alla consegna.

1. Fare clic su **[!UICONTROL To]** per definire la popolazione di destinazione. Per impostazione predefinita, viene applicata la mappatura di destinazione **[!UICONTROL Subscriber application]**. Fare clic su **[!UICONTROL Add]** per selezionare il servizio.

   ![](assets/nmac_android_7.png)

1. Nella finestra **[!UICONTROL Target type]**, selezionare **[!UICONTROL Subscribers of an Android mobile application]** e fare clic su **[!UICONTROL Next]**.

1. Nel menu a discesa **[!UICONTROL Service]**, selezionate il servizio creato in precedenza e fate clic su **[!UICONTROL Finish]**.
Le **[!UICONTROL Application variables]** vengono aggiunte automaticamente a seconda di quanto è stato aggiunto durante i passaggi di configurazione.

   ![](assets/nmac_android_6.png)

1. Selezionare **[!UICONTROL data message]** come **[!UICONTROL Message Type]**.

1. Modificate la notifica RTF.

   ![](assets/nmac_android_5.png)

1. Se necessario, puoi aggiungere informazioni nella **[!UICONTROL Application variables]** precedentemente configurata. **[!UICONTROL Application variables]** deve essere configurato nel servizio Android e fa parte del payload di messaggi inviato al dispositivo mobile.

1. Fare clic su **[!UICONTROL Save]** e inviare la consegna.

L&#39;immagine e la pagina Web devono essere visualizzate nella notifica push quando vengono ricevute sui dispositivi mobili Android degli abbonati.

![](assets/nmac_android_4.png)

### Creazione di un messaggio di notifica {#creating-notification-message}

>[!NOTE]
>
>Ulteriori opzioni per il messaggio di notifica sono disponibili solo con la configurazione dell&#39;API HTTP v1. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).

![](assets/do-not-localize/how-to-video.png) [Scoprite come creare una notifica push Android in un video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selezionare **[!UICONTROL Deliver on Android (android)]** nel menu a discesa **[!UICONTROL Delivery template]**. Aggiungi un **[!UICONTROL Label]** alla consegna.

1. Fare clic su **[!UICONTROL To]** per definire la popolazione di destinazione. Per impostazione predefinita, viene applicata la mappatura di destinazione **[!UICONTROL Subscriber application]**. Fare clic su **[!UICONTROL Add]** per selezionare il servizio.

   ![](assets/nmac_android_7.png)

1. Nella finestra **[!UICONTROL Target type]**, selezionare **[!UICONTROL Subscribers of an Android mobile application]** e fare clic su **[!UICONTROL Next]**.

1. Nel menu a discesa **[!UICONTROL Service]**, selezionate il servizio creato in precedenza e fate clic su **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Selezionare **[!UICONTROL notification message]** come **[!UICONTROL Message Type]**.

1. Aggiungi un titolo e modifica il messaggio. Personalizza la notifica push con **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Impostate l&#39;ID canale della notifica. L&#39;app deve creare un canale con questo ID canale prima di ricevere qualsiasi notifica con questo ID canale.
   * **[!UICONTROL Sound]**: Impostate l&#39;audio in modo che venga riprodotto quando il dispositivo riceve la notifica.
   * **[!UICONTROL Color]**: Impostate il colore dell&#39;icona della notifica.
   * **[!UICONTROL Icon]**: Impostate l&#39;icona della notifica per visualizzarla sui dispositivi dei profili.
   * **[!UICONTROL Tag]**: Impostate l&#39;identificatore utilizzato per sostituire le notifiche esistenti nel cassetto delle notifiche.
   * **[!UICONTROL Click action]**: Impostate l&#39;azione associata a un clic utente sulla notifica.

   Per ulteriori informazioni sulla **[!UICONTROL Notification options]** e su come compilare questi campi, fare riferimento alla [documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. Se l&#39;applicazione è configurata con il protocollo HTTP v1 API, potete personalizzare ulteriormente la notifica push con la seguente **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Impostate il testo della ticker della notifica. Disponibile solo per i dispositivi impostati su Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Impostate l’URL dell’immagine da visualizzare nella notifica.
   * **[!UICONTROL Notification Count]**: Impostate il numero di nuove informazioni non lette da visualizzare direttamente sull&#39;icona dell&#39;applicazione.
   * **[!UICONTROL Sticky]**: Impostate su true o false. Se è impostata su false, la notifica viene chiusa automaticamente quando l&#39;utente fa clic su di essa. Se è impostata su true, la notifica continua a essere visualizzata anche quando l&#39;utente fa clic su di essa.
   * **[!UICONTROL Notification Priority]**: Impostate i livelli di priorità della notifica su valori predefiniti, minimi, bassi o alti. Per ulteriori informazioni, consultare la [documentazione di FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Impostate i livelli di visibilità della notifica su pubblico, privato o segreto. Per ulteriori informazioni, consultare la [documentazione di FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Per ulteriori informazioni sulla **[!UICONTROL HTTP v1 additional options]** e su come compilare questi campi, fare riferimento alla [documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. Se necessario, puoi aggiungere informazioni nella **[!UICONTROL Application variables]** precedentemente configurata. **[!UICONTROL Application variables]** deve essere configurato nel servizio Android e fa parte del payload di messaggi inviato al dispositivo mobile.

1. Fare clic su **[!UICONTROL Save]** e inviare la consegna.

L&#39;immagine e la pagina Web devono essere visualizzate nella notifica push quando vengono ricevute sui dispositivi mobili Android degli abbonati.
