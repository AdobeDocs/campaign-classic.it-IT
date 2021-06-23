---
product: campaign
title: Configurazione dell’app mobile iOS in Adobe Campaign
description: Scopri come configurare la tua app mobile per iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 5%

---

# Passaggi di configurazione per iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Una volta installato il pacchetto, puoi definire le impostazioni dell’app iOS in Adobe Campaign Classic.

>[!NOTE]
>
>Per scoprire come configurare l’app per Android e come creare una consegna per Android, consulta questa [sezione](configuring-the-mobile-application-android.md).

I passaggi chiave sono i seguenti:

1. [Configurare l’account esterno iOS](#configuring-external-account-ios)
1. [Configurare il servizio iOS](#configuring-ios-service)
1. [Integrare l’app mobile iOS in Campaign](#creating-ios-app)

Potrai quindi [creare una notifica push per i dispositivi iOS](create-notifications-ios.md).


## Configurare un account esterno iOS {#configuring-external-account-ios}

Per iOS, il connettore iOS HTTP/2 invia notifiche al servizio APN HTTP/2.

Per configurare questo connettore, effettua le seguenti operazioni:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleziona l’account esterno **[!UICONTROL iOS routing]**.
1. Nella scheda **[!UICONTROL Connector]** , compila il campo **[!UICONTROL Access URL of the connector]** con il seguente URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Fai clic su **[!UICONTROL Save]**.

Il connettore iOS è ora configurato. Puoi iniziare a creare il servizio.

## Configurazione del servizio iOS {#configuring-ios-service}

>[!CAUTION]
>
>L’applicazione deve essere stata configurata per le azioni push PRIMA di qualsiasi integrazione con Adobe Campaign SDK.
>
>In caso contrario, fare riferimento a [questa pagina](https://developer.apple.com/documentation/usernotifications).

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

1. Crea le tue applicazioni di sviluppo e produzione iOS. Per ulteriori informazioni, consulta questa [sezione](configuring-the-mobile-application.md#creating-ios-app).

## Creare un’app mobile iOS {#creating-ios-app}

Dopo aver creato il servizio, crea l’applicazione iOS in Campaign. Segui i passaggi seguenti:

1. Dal servizio appena creato, fai clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Viene visualizzata la finestra seguente. Seleziona **[!UICONTROL Create an iOS application]** e inizia immettendo il **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Puoi anche arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]** se necessario. Sono completamente personalizzabili e una parte del payload del messaggio inviato al dispositivo mobile.
Nell’esempio seguente, aggiungiamo **mediaURl** e **mediaExt** per creare una notifica push potenziata e quindi fornisce all’applicazione l’immagine da visualizzare all’interno della notifica.

   ![](assets/nmac_ios_3.png)

1. La scheda **[!UICONTROL Subscription parameters]** ti consente di definire la mappatura con un’estensione dello schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Assicurati di non utilizzare lo stesso certificato per la versione di sviluppo (sandbox) e la versione di produzione dell&#39;applicazione.

1. La scheda **[!UICONTROL Sounds]** consente di specificare un suono da riprodurre. Fare clic su **[!UICONTROL Add]** e compilare il campo **[!UICONTROL Internal name]** che deve contenere il nome del file incorporato nell&#39;applicazione o il nome dell&#39;audio di sistema.

1. Fai clic su **[!UICONTROL Next]** per iniziare a configurare l&#39;applicazione di sviluppo.

1. Assicurati che lo stesso **[!UICONTROL Integration key]** sia definito in Adobe Campaign e nel codice dell&#39;applicazione tramite l&#39;SDK. Per ulteriori informazioni, consulta: [Integrazione dell’SDK Campaign nell’app mobile](integrating-campaign-sdk-into-the-mobile-application.md). Questa chiave di integrazione, specifica per ogni applicazione, consente di collegare l’app mobile alla piattaforma Adobe Campaign.

   >[!NOTE]
   >
   > Il **[!UICONTROL Integration key]** è completamente personalizzabile con il valore stringa, ma deve essere esattamente lo stesso specificato nell&#39;SDK.

1. Seleziona una delle icone predefinite dal campo **[!UICONTROL Application icon]** per personalizzare l’app mobile nel servizio.

1. Seleziona **[!UICONTROL Authentication mode]**. Puoi sempre modificare la modalità di autenticazione in un secondo momento nella scheda **[!UICONTROL Certificate]** della tua app mobile.
   * **[!UICONTROL Certificate-based authentication]**: Fai clic su  **[!UICONTROL Enter the certificate...]**  quindi seleziona la chiave p12 e immetti la password fornita dallo sviluppatore di applicazioni mobili.
   * **[!UICONTROL Token-based authentication]**: Inserisci le impostazioni di connessione  **[!UICONTROL Key ID]**,  **[!UICONTROL Team ID]** quindi  **[!UICONTROL Bundle ID]** seleziona il certificato p8 facendo clic su  **[!UICONTROL Enter the private key]**. Per ulteriori informazioni su **[!UICONTROL Token-based authentication]**, consulta la [documentazione Apple](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe consiglia di utilizzare **[!UICONTROL Token-based authentication]** per la configurazione iOS, poiché questa modalità di autenticazione è più protetta e non è associata alla scadenza del certificato.

   ![](assets/nmac_ios_4.png)

1. Puoi fare clic su **[!UICONTROL Test the connection]** per verificare che sia stato eseguito correttamente.

1. Fai clic su **[!UICONTROL Next]** per iniziare a configurare l&#39;applicazione di produzione e segui gli stessi passaggi descritti in precedenza.

   ![](assets/nmac_ios_5.png)

1. Fai clic su **[!UICONTROL Finish]**.

L’applicazione iOS è ora pronta per essere utilizzata in Campaign Classic.
