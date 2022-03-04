---
product: campaign
title: Configurare l’app mobile Android in Adobe Campaign
description: Scopri come configurare la tua app mobile per Android
feature: Push
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 4%

---

# Passaggi di configurazione per Android

Una volta installato il pacchetto, puoi definire le impostazioni dell’app Android in Adobe Campaign Classic.

>[!NOTE]
>
>Per scoprire come configurare l’app per iOS e come creare una consegna per iOS, consulta questo articolo [sezione](configuring-the-mobile-application.md).

I passaggi chiave sono i seguenti:

1. [Configurare l’account esterno Android](#configuring-external-account-android)
1. [Configurare il servizio Android](#configuring-android-service)
1. [Creare l’app mobile in Campaign](#creating-android-app)
1. [Estendi lo schema dell’app con dati aggiuntivi](#extend-subscription-schema)

Potrai quindi [creare una notifica potenziata Android](create-notifications-android.md).

## Configurare l’account esterno Android {#configuring-external-account-android}

Per Android sono disponibili due connettori:

* Connettore V1 che consente una connessione per figlio MTA.
* Connettore V2 che consente connessioni simultanee al server FCM per migliorare il throughput.

Per scegliere il connettore da utilizzare, effettua le seguenti operazioni:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleziona la **[!UICONTROL Android routing]** conto esterno.
1. In **[!UICONTROL Connector]** , compila **[!UICONTROL JavaScript used in the connector]** campo:

   Per Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Puoi anche configurarlo come segue https://localhost:8080/nms/jsp/androidPushConnector.js ma ti consigliamo di utilizzare la versione 2 del connettore.

   ![](assets/nmac_connectors3.png)

1. Per Android V2, è disponibile un parametro aggiuntivo nel file di configurazione di Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Limite massimo di richieste HTTP parallele all&#39;FCM avviato da ogni server figlio (8 per impostazione predefinita).

## Configurare un servizio Android {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Scopri come configurare un servizio Android nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Vai a **[!UICONTROL Profiles and Targets > Services and subscriptions]** nodo e fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definire un **[!UICONTROL Label]** e **[!UICONTROL Internal name]**.
1. Vai a **[!UICONTROL Type]** campo e seleziona **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Il valore predefinito **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** la mappatura di destinazione è collegata alla tabella dei destinatari. Se desideri utilizzare una mappatura di destinazione diversa, devi creare una nuova mappatura di destinazione e inserirla nel **[!UICONTROL Target mapping]** campo del servizio. Per ulteriori informazioni sulla creazione della mappatura di destinazione, consulta [questa sezione](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Quindi fai clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Crea la tua applicazione Android. Per ulteriori informazioni al riguardo, consulta [questa sezione](configuring-the-mobile-application-android.md#creating-android-app).

## Creare l’app mobile Android {#creating-android-app}

Dopo aver creato il servizio, è ora necessario creare l&#39;applicazione Android:

1. Dal servizio appena creato, fai clic su **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Seleziona **[!UICONTROL Create an Android application]** e immetti un **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Assicurati che le stesse **[!UICONTROL Integration key]** è definito in Adobe Campaign e nel codice dell&#39;applicazione tramite l&#39;SDK. Per ulteriori informazioni al riguardo, consulta [questa sezione](integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > La **[!UICONTROL Integration key]** è completamente personalizzabile con il valore stringa, ma deve essere esattamente uguale a quello specificato nell&#39;SDK.

1. Seleziona la **[!UICONTROL API version]**: HTTP v1 o HTTP (legacy). Queste configurazioni sono descritte in dettaglio in [questa sezione](#select-api-version)

1. Compila il **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** campi.

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Per impostazione predefinita, Adobe Campaign salva una chiave nel **[!UICONTROL User identifier]** (@userKey) campo della **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabella. Questa chiave consente di collegare un abbonamento a un destinatario. Per raccogliere dati aggiuntivi (ad esempio una chiave di riconciliazione complessa), devi applicare la seguente configurazione:

### Seleziona la versione API{#select-api-version}

Dopo aver creato un servizio e una nuova app mobile, devi configurare la tua app mobile in base alla versione API selezionata.

* **HTTP v1** la configurazione in [questa sezione](configuring-the-mobile-application-android.md#android-service-httpv1).
* **HTTP (legacy)** la configurazione in [questa sezione](configuring-the-mobile-application-android.md#android-service-http).

#### Configurare l’API HTTP v1{#android-service-httpv1}

Per configurare la versione dell’API HTTP v1, segui i passaggi seguenti:

1. Nel tuo **[!UICONTROL Mobile application creation wizard]** finestra, seleziona **[!UICONTROL HTTPV1]** in **[!UICONTROL API version]** a discesa.

1. Fai clic su **[!UICONTROL Load project json file to extract project details...]** per caricare direttamente il file della chiave JSON. Per ulteriori informazioni su come estrarre il file JSON, consulta [questa pagina](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Puoi anche immettere manualmente i seguenti dettagli:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Fai clic su **[!UICONTROL Test the connection]** per verificare che la configurazione sia corretta e che il server di marketing abbia accesso a FCM.

   >[!CAUTION]
   >
   >Per la distribuzione di mid-Sourcing, il **[!UICONTROL Test connection]** Il pulsante non controlla se il server MID ha accesso al server FCM.

   ![](assets/nmac_android_11.png)

1. Puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]** se necessario. Sono completamente personalizzabili e una parte del payload del messaggio inviato al dispositivo mobile.

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Di seguito sono riportati i nomi dei payload FCM per personalizzare ulteriormente la notifica push:

| Tipo di messaggio | Elemento messaggio configurabile (nome payload FCM) | Opzioni configurabili (nome payload FCM) |
|:-:|:-:|:-:|
| messaggio dati | N/D | validate_only |
| messaggio di notifica | titolo, corpo, android_channel_id, icona, suono, tag, colore, click_action, immagine, ticker, persistente, visibilità, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### Configurare l’API HTTP (legacy){#android-service-http}

Per configurare la versione dell’API HTTP (legacy), segui la procedura seguente:

1. Nel tuo **[!UICONTROL Mobile application creation wizard]** finestra, seleziona **[!UICONTROL HTTP (legacy)]** in **[!UICONTROL API version]** a discesa.

1. Inserisci il **[!UICONTROL Project key]** fornito dallo sviluppatore dell’app mobile.

1. Puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]** se necessario. Sono completamente personalizzabili e una parte del payload del messaggio inviato al dispositivo mobile.

   Nell’esempio seguente, aggiungiamo **title**, **imageURL** e **iconURL** per creare una notifica push potenziata e quindi fornisce all’applicazione l’immagine, il titolo e l’icona da visualizzare all’interno della notifica.

   ![](assets/nmac_android_2.png)

1. Fai clic su **[!UICONTROL Finish]**, quindi su **[!UICONTROL Save]**. L’applicazione Android è ora pronta per essere utilizzata in Campaign Classic.

Di seguito sono riportati i nomi dei payload FCM per personalizzare ulteriormente la notifica push:

| Tipo di messaggio | Elemento messaggio configurabile (nome payload FCM) | Opzioni configurabili (nome payload FCM) |
|:-:|:-:|:-:|
| messaggio dati | N/D | dryRun |
| messaggio di notifica | titolo, corpo, android_channel_id, icona, suono, tag, colore, click_action <br> | dryRun |

<br>

## Estendere lo schema appsubscriptionRcp {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Scopri come estendere lo schema appsubscriptionRcp nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

È necessario estendere il **appsubscriptionRcp** per definire nuovi campi aggiuntivi per memorizzare i parametri dall’app nel database di Campaign . Questi campi verranno ad esempio utilizzati per la personalizzazione. Per eseguire questa operazione:

1. Crea un&#39;estensione del **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** definire lo schema e i nuovi campi. Ulteriori informazioni sull’estensione dello schema in [questa pagina](../../configuration/using/about-schema-edition.md)

1. Definisci la mappatura nel **[!UICONTROL Subscription parameters]** scheda .

   >[!CAUTION]
   >
   >Assicurati che i nomi di configurazione nel **[!UICONTROL Subscription parameters]** sono uguali a quelle nel codice dell’app mobile. Fai riferimento a [questa sezione](integrating-campaign-sdk-into-the-mobile-application.md).
