---
product: campaign
title: Configurazione dell’app mobile Android in Adobe Campaign
description: Scopri come configurare la tua app mobile per Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 2%

---

# Passaggi di configurazione per Android

Una volta installato il pacchetto, puoi definire le impostazioni dell’app Android in Adobe Campaign Classic.

>[!NOTE]
>
>Per scoprire come configurare l’app per iOS e come creare una consegna per iOS, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application.md) .

I passaggi chiave sono i seguenti:

1. [Configurare l’account esterno Android](#configuring-external-account-android)
1. [Configurare il servizio Android](#configuring-android-service)
1. [Creare l’app mobile in Campaign](#creating-android-app)
1. [Estendi lo schema dell’app con dati aggiuntivi](#extend-subscription-schema)

Potrai quindi [creare una notifica avanzata Android](#creating-android-delivery).

## Configurazione dell&#39;account esterno Android {#configuring-external-account-android}

Per Android sono disponibili due connettori:

* Connettore V1 che consente una connessione per figlio MTA.
* Connettore V2 che consente connessioni simultanee al server FCM per migliorare il throughput.

Per scegliere il connettore da utilizzare, effettua le seguenti operazioni:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleziona l’account esterno **[!UICONTROL Android routing]**.
1. Nella scheda **[!UICONTROL Connector]** , compila il campo **[!UICONTROL JavaScript used in the connector]** :

   Per Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Puoi anche configurarlo come segue https://localhost:8080/nms/jsp/androidPushConnector.js ma ti consigliamo di utilizzare la versione 2 del connettore.

   ![](assets/nmac_connectors3.png)

1. Per Android V2, è disponibile un parametro aggiuntivo nel file di configurazione di Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Limite massimo di richieste HTTP parallele all&#39;FCM avviato da ogni server figlio (8 per impostazione predefinita).

## Configurazione del servizio Android {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Scopri come configurare un servizio Android nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Vai al nodo **[!UICONTROL Profiles and Targets > Services and subscriptions]** e fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definisci un **[!UICONTROL Label]** e un **[!UICONTROL Internal name]**.
1. Vai al campo **[!UICONTROL Type]** e seleziona **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >La mappatura di destinazione predefinita **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** è collegata alla tabella dei destinatari. Se desideri utilizzare una mappatura di destinazione diversa, devi creare una nuova mappatura di destinazione e immetterla nel campo **[!UICONTROL Target mapping]** del servizio. Per ulteriori informazioni sulla creazione della mappatura di destinazione, consulta la [Guida alla configurazione](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Quindi fai clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Crea la tua applicazione Android. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app).

## Creazione di un&#39;applicazione mobile Android {#creating-android-app}

Dopo aver creato il servizio, è ora necessario creare l&#39;applicazione Android:

1. Dal servizio appena creato, fai clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Seleziona **[!UICONTROL Create an Android application]** e immetti un **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Assicurati che lo stesso **[!UICONTROL Integration key]** sia definito in Adobe Campaign e nel codice dell&#39;applicazione tramite l&#39;SDK. Per ulteriori informazioni, consulta: [Integrazione dell’SDK Campaign nell’app mobile](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > Il **[!UICONTROL Integration key]** è completamente personalizzabile con il valore stringa, ma deve essere esattamente lo stesso specificato nell&#39;SDK.

1. Seleziona il **[!UICONTROL API version]**: HTTP v1 o HTTP (legacy). Queste configurazioni sono descritte in [questa sezione](#select-api-version)

1. Compila i campi **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** .

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Per impostazione predefinita, Adobe Campaign salva una chiave nel campo **[!UICONTROL User identifier]** (@userKey) della tabella **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** . Questa chiave consente di collegare un abbonamento a un destinatario. Per raccogliere dati aggiuntivi (ad esempio una chiave di riconciliazione complessa), devi applicare la seguente configurazione:

### Seleziona la versione API{#select-api-version}

Dopo aver creato un servizio e una nuova app mobile, devi configurare la tua app mobile in base alla versione API selezionata.

* **La** configurazione HTTP v1 è descritta in questa  [sezione](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).
* **La configurazione HTTP (legacy)** è descritta in questa  [sezione](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http).

#### Configura l&#39;API HTTP v1{#android-service-httpv1}

Per configurare la versione dell’API HTTP v1, segui i passaggi seguenti:

1. Nella finestra **[!UICONTROL Mobile application creation wizard]**, seleziona **[!UICONTROL HTTPV1]** nel menu a discesa **[!UICONTROL API version]**.

1. Fai clic su **[!UICONTROL Load project json file to extract projet details...]** per caricare direttamente il file della chiave JSON. Per ulteriori informazioni su come estrarre il file JSON, consulta questa [pagina](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Puoi anche immettere manualmente i seguenti dettagli:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Fai clic su **[!UICONTROL Test the connection]** per verificare che la configurazione sia corretta e che il server di marketing abbia accesso a FCM.

   >[!CAUTION]
   >
   >Per la distribuzione mid-sourcing, il pulsante **[!UICONTROL Test connection]** non controlla se il server MID ha accesso al server FCM.

   ![](assets/nmac_android_11.png)

1. Puoi anche arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]** se necessario. Sono completamente personalizzabili e una parte del payload del messaggio inviato al dispositivo mobile.

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Di seguito sono riportati i nomi dei payload FCM per personalizzare ulteriormente la notifica push:

| Tipo di messaggio | Elemento messaggio configurabile (nome payload FCM) | Opzioni configurabili (nome payload FCM) |
|:-:|:-:|:-:|
| messaggio dati | N/D | validate_only |
| messaggio di notifica | titolo, corpo, android_channel_id, icona, suono, tag, colore, click_action, immagine, ticker, persistente, visibilità, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### Configura l&#39;API HTTP (legacy){#android-service-http}

Per configurare la versione dell’API HTTP (legacy), segui la procedura seguente:

1. Nella finestra **[!UICONTROL Mobile application creation wizard]**, seleziona **[!UICONTROL HTTP (legacy)]** nel menu a discesa **[!UICONTROL API version]**.

1. Immetti il **[!UICONTROL Project key]** fornito dallo sviluppatore dell’app mobile.

1. Puoi anche arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]** se necessario. Sono completamente personalizzabili e una parte del payload del messaggio inviato al dispositivo mobile.

   Nell&#39;esempio seguente, aggiungiamo **title**, **imageURL** e **iconURL** per creare una notifica push potenziata e quindi fornisce all&#39;applicazione l&#39;immagine, il titolo e l&#39;icona da visualizzare all&#39;interno della notifica.

   ![](assets/nmac_android_2.png)

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Di seguito sono riportati i nomi dei payload FCM per personalizzare ulteriormente la notifica push:

| Tipo di messaggio | Elemento messaggio configurabile (nome payload FCM) | Opzioni configurabili (nome payload FCM) |
|:-:|:-:|:-:|
| messaggio dati | N/D | dryRun |
| messaggio di notifica | titolo, corpo, android_channel_id, icona, suono, tag, colore, click_action <br> | dryRun |

<br>

## Estendi lo schema appsubscriptionRcp {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Scopri come estendere lo schema appsubscriptionRcp nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

È necessario estendere **appsubscriptionRcp** per definire nuovi campi aggiuntivi per memorizzare i parametri dall’app nel database di Campaign . Questi campi verranno ad esempio utilizzati per la personalizzazione. Per eseguire questa operazione:

1. Crea un&#39;estensione dello schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** e definisci i nuovi campi. Ulteriori informazioni sull&#39;estensione dello schema in [questa pagina](../../configuration/using/about-schema-edition.md)

1. Definisci la mappatura nella scheda **[!UICONTROL Subscription parameters]** .

   >[!CAUTION]
   >
   >Assicurati che i nomi di configurazione nella scheda **[!UICONTROL Subscription parameters]** siano gli stessi nel codice dell&#39;applicazione mobile. Consulta la sezione [Integrazione dell’SDK Campaign nell’app mobile](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) .

## Creazione di una notifica potenziata Android {#creating-android-delivery}

Con Firebase Cloud Messaging, puoi scegliere tra due tipi di messaggi:

* **[!UICONTROL Data message]**, gestito dall’app client.
   <br>I messaggi vengono inviati direttamente all’app mobile, che genererà e visualizzerà la notifica android sul dispositivo. I messaggi di dati contengono solo le variabili di applicazione personalizzate.

* **[!UICONTROL Notification message]**, gestito automaticamente dall&#39;SDK FCM.
   <br> FCM visualizza automaticamente il messaggio sui dispositivi degli utenti per conto dell’app client. I messaggi di notifica contengono un set predefinito di parametri e opzioni, ma possono ancora essere ulteriormente personalizzati con variabili di applicazione personalizzate.

Per ulteriori informazioni sui tipi di messaggi Firebase Cloud Messaging, consulta la [documentazione FCM](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

### Creazione di un messaggio dati {#creating-data-message}

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleziona **[!UICONTROL Deliver on Android (android)]** nel menu a discesa **[!UICONTROL Delivery template]** . Aggiungi un **[!UICONTROL Label]** alla consegna.

1. Fai clic su **[!UICONTROL To]** per definire il gruppo di destinazione. Per impostazione predefinita, viene applicata la mappatura di destinazione **[!UICONTROL Subscriber application]**. Fai clic su **[!UICONTROL Add]** per selezionare il servizio.

   ![](assets/nmac_android_7.png)

1. Nella finestra **[!UICONTROL Target type]**, seleziona **[!UICONTROL Subscribers of an Android mobile application]** e fai clic su **[!UICONTROL Next]**.

1. Nel menu a discesa **[!UICONTROL Service]** , seleziona il servizio creato in precedenza e fai clic su **[!UICONTROL Finish]**.
I **[!UICONTROL Application variables]** vengono aggiunti automaticamente a seconda di ciò che è stato aggiunto durante i passaggi di configurazione.

   ![](assets/nmac_android_6.png)

1. Seleziona **[!UICONTROL data message]** come **[!UICONTROL Message Type]**.

1. Modifica le notifiche potenziate.

   ![](assets/nmac_android_5.png)

1. Se necessario, puoi aggiungere informazioni nel **[!UICONTROL Application variables]** configurato in precedenza. **[!UICONTROL Application variables]** deve essere configurato nel servizio Android e fa parte del payload del messaggio inviato al dispositivo mobile.

1. Fai clic su **[!UICONTROL Save]** e invia la consegna.

L’immagine e la pagina web devono essere visualizzati nella notifica push quando vengono ricevuti sui dispositivi mobili Android degli abbonati.

![](assets/nmac_android_4.png)

### Creazione di un messaggio di notifica {#creating-notification-message}

>[!NOTE]
>
>Ulteriori opzioni per il messaggio di notifica sono disponibili solo con la configurazione dell’API HTTP v1. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).

![](assets/do-not-localize/how-to-video.png) [Scopri come creare una notifica push Android nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleziona **[!UICONTROL Deliver on Android (android)]** nel menu a discesa **[!UICONTROL Delivery template]** . Aggiungi un **[!UICONTROL Label]** alla consegna.

1. Fai clic su **[!UICONTROL To]** per definire il gruppo di destinazione. Per impostazione predefinita, viene applicata la mappatura di destinazione **[!UICONTROL Subscriber application]**. Fai clic su **[!UICONTROL Add]** per selezionare il servizio.

   ![](assets/nmac_android_7.png)

1. Nella finestra **[!UICONTROL Target type]**, seleziona **[!UICONTROL Subscribers of an Android mobile application]** e fai clic su **[!UICONTROL Next]**.

1. Nel menu a discesa **[!UICONTROL Service]** , seleziona il servizio creato in precedenza e fai clic su **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Seleziona **[!UICONTROL notification message]** come **[!UICONTROL Message Type]**.

1. Aggiungi un titolo e modifica il messaggio. Personalizza la notifica push con **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Imposta l&#39;ID del canale della notifica. Prima di ricevere qualsiasi notifica con questo ID canale, l’app deve creare un canale con questo ID canale.
   * **[!UICONTROL Sound]**: Impostare l&#39;audio da riprodurre quando il dispositivo riceve la notifica.
   * **[!UICONTROL Color]**: Imposta il colore dell’icona della notifica.
   * **[!UICONTROL Icon]**: Imposta l’icona della notifica per visualizzarla sui dispositivi dei profili.
   * **[!UICONTROL Tag]**: Imposta l&#39;identificatore utilizzato per sostituire le notifiche esistenti nel riquadro delle notifiche.
   * **[!UICONTROL Click action]**: Imposta l&#39;azione associata a un clic utente sulla notifica.

   Per ulteriori informazioni su **[!UICONTROL Notification options]** e su come compilare questi campi, consulta la [documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. Se la tua applicazione è configurata con il protocollo API HTTP v1, puoi personalizzare ulteriormente la notifica push con la seguente **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Imposta il testo della notifica. Disponibile solo per i dispositivi impostati su Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Imposta l’URL dell’immagine da visualizzare nella notifica.
   * **[!UICONTROL Notification Count]**: Impostare il numero di nuove informazioni non lette da visualizzare direttamente sull&#39;icona dell&#39;applicazione.
   * **[!UICONTROL Sticky]**: Impostato su true o false. Se è impostato su false, la notifica viene automaticamente ignorata quando l&#39;utente vi fa clic. Se è impostato su true, la notifica viene comunque visualizzata anche quando l&#39;utente fa clic su di essa.
   * **[!UICONTROL Notification Priority]**: Imposta i livelli di priorità della notifica su valori predefiniti, minimi, bassi o alti. Per ulteriori informazioni, consulta la [documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Imposta i livelli di visibilità della notifica su pubblico, privato o segreto. Per ulteriori informazioni, consulta la [documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Per ulteriori informazioni su **[!UICONTROL HTTP v1 additional options]** e su come compilare questi campi, consulta la [documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. Se necessario, puoi aggiungere informazioni nel **[!UICONTROL Application variables]** configurato in precedenza. **[!UICONTROL Application variables]** deve essere configurato nel servizio Android e fa parte del payload del messaggio inviato al dispositivo mobile.

1. Fai clic su **[!UICONTROL Save]** e invia la consegna.

L’immagine e la pagina web devono essere visualizzati nella notifica push quando vengono ricevuti sui dispositivi mobili Android degli abbonati.
