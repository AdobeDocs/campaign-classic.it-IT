---
product: campaign
title: Configurare l’app mobile Android in Adobe Campaign
description: Scopri come configurare l’app mobile per Android
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 10%

---

# Passaggi di configurazione per Android

Una volta installato il pacchetto, puoi definire le impostazioni dell’app Android in Adobe Campaign Classic.

I passaggi chiave sono i seguenti:

1. [Configurare l’account esterno di Android](#configuring-external-account-android)
1. [Configurare il servizio Android](#configuring-android-service)
1. [Creare l’app mobile in Campaign](#creating-android-app)
1. [Estendere lo schema dell’app con dati aggiuntivi](#extend-subscription-schema)

Potrai quindi [creare una notifica avanzata di Android](create-notifications-android.md).

>[!IMPORTANT]
>
>Alcune importanti modifiche al servizio Android Firebase Cloud Messaging (FCM) verranno rilasciate nel 2024 e potranno influenzare la tua implementazione di Adobe Campaign. Per supportare questa modifica, potrebbe essere necessario aggiornare la configurazione dei servizi di abbonamento per i messaggi push Android. Puoi già verificare ed eseguire azioni. Per ulteriori informazioni, consulta questa [nota tecnica su Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=it){target="_blank"}.


## Configurare l’account esterno di Android {#configuring-external-account-android}

Per Android sono disponibili due connettori:

* Il connettore V1 che consente una connessione per elemento secondario MTA.
* Il connettore V2 che consente connessioni simultanee al server FCM per migliorare il throughput.

Per scegliere il connettore da utilizzare, eseguire la procedura seguente:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Selezionare l&#39;account esterno **[!UICONTROL Android routing]**.
1. Nella scheda **[!UICONTROL Connector]**, compila il campo **[!UICONTROL JavaScript used in the connector]**:

   Per Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Puoi anche configurarlo come segue https://localhost:8080/nms/jsp/androidPushConnector.js, ma ti consigliamo di utilizzare la versione 2 del connettore.

   ![](assets/nmac_connectors3.png)

1. Per Android V2, nel file di configurazione di Adobe Server (serverConf.xml) è disponibile un parametro aggiuntivo:

   * **maxGCMConnectPerChild**: limite massimo di richieste HTTP parallele a FCM avviate da ogni server secondario (8 per impostazione predefinita).

## Configurare un servizio Android {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Scopri come configurare un servizio Android nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=it#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign){target="_blank"}.

1. Passare al nodo **[!UICONTROL Profiles and Targets > Services and subscriptions]** e fare clic su **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definisci **[!UICONTROL Label]** e **[!UICONTROL Internal name]**.
1. Vai al campo **[!UICONTROL Type]** e seleziona **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Il mapping di destinazione predefinito **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** è collegato alla tabella dei destinatari. Se si desidera utilizzare una mappatura di destinazione diversa, è necessario creare una nuova mappatura di destinazione e immetterla nel campo **[!UICONTROL Target mapping]** del servizio. Per ulteriori informazioni sulla creazione di destinazione mappatura, consulta questa [sezione](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Quindi fare clic sull&#39;pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Crea la tua applicazione Android. Per ulteriori informazioni al riguardo, consulta [questa sezione](configuring-the-mobile-application-android.md#creating-android-app).

## Creare l’app mobile Android {#creating-android-app}

Dopo aver creato il servizio, ora è necessario creare l’applicazione Android:

1. Dal servizio appena creato, fare clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Selezionare **[!UICONTROL Create an Android application]** e immettere **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Assicurarsi che lo stesso **[!UICONTROL Integration key]** sia definito in Adobe Campaign e nel codice dell&#39;applicazione tramite SDK. <!--For more on this, refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** è completamente personalizzabile con valore stringa, ma deve essere esattamente lo stesso specificato in SDK.

1. Selezionare **[!UICONTROL API version]**: HTTP v1 o HTTP (legacy). Queste configurazioni sono descritte in [questa sezione](#select-api-version)

1. Compila i campi **[!UICONTROL Firebase Cloud Messaging the Android connection settings]**.

1. Fare clic su **[!UICONTROL Finish]** e quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Per impostazione predefinita, Adobe Campaign salva una chiave nel campo **[!UICONTROL User identifier]** (@userKey) della tabella **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Questa chiave consente di collegare una sottoscrizione a un destinatario. Per raccogliere dati aggiuntivi (ad esempio una chiave di riconciliazione complessa), è necessario applicare la seguente configurazione:

### Configurare la versione API{#select-api-version}

>[!IMPORTANT]
>
>Alcune importanti modifiche al servizio Android Firebase Cloud Messaging (FCM) verranno rilasciate nel 2024 e potranno influenzare la tua implementazione di Adobe Campaign. Nell&#39;ambito del continuo impegno di Google per migliorare i propri servizi, le API FCM legacy cesseranno il **20 giugno 2024**. Per ulteriori informazioni, consulta questa [nota tecnica su Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=it){target="_blank"}.

Dopo aver creato il servizio e una nuova app mobile, è necessario configurare l’app mobile. L&#39;API **HTTP (legacy)** non deve essere selezionata in quanto è stata dichiarata obsoleta da Google.

Per configurare la versione API HTTP v1, segui i passaggi seguenti:

1. Nella finestra **[!UICONTROL Mobile application creation wizard]**, seleziona **[!UICONTROL HTTPV1]** nel menu a discesa **[!UICONTROL API version]**.

1. Fai clic su **[!UICONTROL Load project json file to extract project details...]** per caricare direttamente il file di chiave JSON. Per ulteriori informazioni su come estrarre il file JSON, consulta [questa pagina](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   È inoltre possibile immettere manualmente i seguenti dettagli:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Fare clic su **[!UICONTROL Test the connection]** per verificare che la configurazione sia corretta e che il server di marketing abbia accesso a FCM.

   >[!CAUTION]
   >
   >Per la distribuzione mid-sourcing, il pulsante **[!UICONTROL Test connection]** non verifica se il server MID ha accesso al server FCM.

   ![](assets/nmac_android_11.png)

1. Se necessario, puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]**. Questi sono completamente personalizzabili e fanno parte del payload del messaggio inviato al dispositivo mobile.

1. Fare clic su **[!UICONTROL Finish]** e quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Di seguito sono riportati i nomi del payload FCM per personalizzare ulteriormente la notifica push:

| Tipo di messaggio | Elemento del messaggio configurabile (nome del payload FCM) | Opzioni configurabili (nome payload FCM) |
|:-:|:-:|:-:|
| messaggio dati | N/D | validate_only |
| messaggio di notifica | titolo, corpo, android_channel_id, icona, suono, tag, colore, click_action, immagine, ticker, fisso, visibilità, notification_priority, notification_count <br> | validate_only |

## Estendere lo schema appsubscriptionRcp {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Scopri come estendere lo schema appsubscriptionRcp nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=it#extending-the-app-subscription-schema-to-personalize-push-notifications)

È necessario estendere **appsubscriptionRcp** per definire nuovi campi aggiuntivi per archiviare i parametri dell&#39;app nel database di Campaign. Questi campi vengono utilizzati per la personalizzazione, ad esempio. Per eseguire questa operazione:

1. Creare un&#39;estensione dello schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** e definire i nuovi campi. Ulteriori informazioni sull&#39;estensione dello schema in [questa pagina](../../configuration/using/about-schema-edition.md)

1. Definire il mapping nella scheda **[!UICONTROL Subscription parameters]**.

   >[!CAUTION]
   >
   >Assicurarsi che i nomi di configurazione nella scheda **[!UICONTROL Subscription parameters]** siano gli stessi di quelli nel codice dell&#39;app mobile. <!--Refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->
