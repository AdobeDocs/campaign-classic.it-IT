---
solution: Campaign Classic
product: campaign
title: Configurazione dell’applicazione mobile iOS in  Adobe Campaign
description: Scopri come configurare l’applicazione mobile per iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: a1bd8dc2b5946b74cb880eff934e3b35cadfb2d2
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 8%

---


# Passaggi di configurazione per iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Una volta installato il pacchetto, potete definire le impostazioni dell&#39;app iOS in Adobe Campaign Classic.

>[!NOTE]
>
>Per informazioni su come configurare l&#39;app per Android e su come creare una consegna per Android, consultate questa [sezione](../../delivery/using/configuring-the-mobile-application-android.md).

## Configurazione dell&#39;account esterno iOS {#configuring-external-account-ios}

Per iOS, il connettore iOS HTTP/2 invia notifiche agli APN HTTP/2.

Per configurare questo connettore, procedere come segue:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Selezionare l&#39;account esterno **[!UICONTROL iOS routing]**.
1. Nella scheda **[!UICONTROL Connector]**, compilare il campo **[!UICONTROL Access URL of the connector]** con il seguente URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   >[!NOTE]
   >
   > A partire dalla release Campaign 20.3, il connettore legacy binario per iOS è diventato obsoleto. Se utilizzi questo connettore, devi adattare di conseguenza l’implementazione. [Ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/migrate-to-apns-http2.html)

   ![](assets/nmac_connectors.png)

1. Fai clic su **[!UICONTROL Save]**.

Il connettore iOS è ora configurato. Potete iniziare a creare il servizio.

## Configurazione del servizio iOS {#configuring-ios-service}

>[!CAUTION]
>
>L&#39;applicazione deve essere stata configurata per le azioni push PRIMA di qualsiasi integrazione  Adobe Campaign SDK.
>
>In caso contrario, fare riferimento a [questa pagina](https://developer.apple.com/documentation/usernotifications).

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

1. Creare le applicazioni di sviluppo e produzione iOS. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app).

## Creazione di un&#39;applicazione mobile iOS {#creating-ios-app}

Dopo aver creato il servizio, è ora necessario creare l&#39;applicazione iOS:

1. Dal servizio appena creato, fate clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Viene visualizzata la finestra seguente. Selezionare **[!UICONTROL Create an iOS application]** e iniziare immettendo la **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Come opzione, puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]**, se necessario. Sono completamente personalizzabili e una parte del payload di messaggi inviato al dispositivo mobile.
Nell&#39;esempio seguente, per creare una notifica push potenziata vengono aggiunti **mediaURl** e **mediaExt**, quindi viene fornita all&#39;applicazione l&#39;immagine da visualizzare all&#39;interno della notifica.

   ![](assets/nmac_ios_3.png)

1. La scheda **[!UICONTROL Subscription parameters]** consente di definire la mappatura con un&#39;estensione dello schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Accertatevi di non utilizzare lo stesso certificato per la versione di sviluppo (sandbox) e per la versione di produzione dell&#39;applicazione.

1. La scheda **[!UICONTROL Sounds]** consente di specificare un suono da riprodurre. Fare clic su **[!UICONTROL Add]** e compilare il campo **[!UICONTROL Internal name]** che deve contenere il nome del file incorporato nell&#39;applicazione o il nome dell&#39;audio del sistema.

1. Fare clic su **[!UICONTROL Next]** per avviare la configurazione dell&#39;applicazione di sviluppo.

1. Assicurati che lo stesso **[!UICONTROL Integration key]** sia definito in  Adobe Campaign e nel codice dell&#39;applicazione tramite l&#39;SDK. Per ulteriori informazioni, consulta: [Integrazione di Campaign SDK nell&#39;applicazione mobile](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). Questa chiave di integrazione, specifica per ogni applicazione, consente di collegare l’applicazione mobile alla piattaforma Adobe Campaign .

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** è completamente personalizzabile con valore stringa, ma deve corrispondere esattamente a quello specificato nell&#39;SDK.

1. Seleziona una delle icone pronte all&#39;uso dal campo **[!UICONTROL Application icon]** per personalizzare l&#39;applicazione mobile nel servizio.

1. Seleziona **[!UICONTROL Authentication mode]**. È sempre possibile modificare la modalità di autenticazione in un secondo momento nella scheda **[!UICONTROL Certificate]** dell&#39;applicazione mobile.
   * **[!UICONTROL Certificate-based authentication]**: Fate clic  **[!UICONTROL Enter the certificate...]**  quindi sulla chiave p12 e immettete la password fornita dallo sviluppatore di applicazioni mobili.
   * **[!UICONTROL Token-based authentication]**: Compilate le impostazioni di connessione  **[!UICONTROL Key ID]** e  **[!UICONTROL Team ID]** quindi selezionate il certificato p8 facendo clic su  **[!UICONTROL Bundle ID]**   **[!UICONTROL Enter the private key]**. Per ulteriori informazioni su **[!UICONTROL Token-based authentication]**, fare riferimento alla [documentazione Apple](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   >  Adobe consiglia di utilizzare **[!UICONTROL Token-based authentication]** per la configurazione iOS in quanto questa modalità di autenticazione è più sicura e non è associata alla scadenza del certificato.

   ![](assets/nmac_ios_4.png)

1. È possibile fare clic su **[!UICONTROL Test the connection]** per verificare che sia stato eseguito correttamente.

1. Fare clic su **[!UICONTROL Next]** per avviare la configurazione dell&#39;applicazione di produzione e seguire gli stessi passaggi descritti in precedenza.

   ![](assets/nmac_ios_5.png)

1. Fai clic su **[!UICONTROL Finish]**.

L&#39;applicazione iOS è ora pronta per essere utilizzata in Campaign Classic.

## Creazione di una notifica iOS {#creating-ios-delivery}

Con iOS 10 o versione successiva, è possibile generare notifiche avanzate.  Adobe Campaign può inviare notifiche utilizzando variabili che consentiranno al dispositivo di visualizzare una notifica RTF.

È ora necessario creare una nuova consegna e collegarla all’applicazione mobile creata.

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selezionare **[!UICONTROL Deliver on iOS (ios)]** nel menu a discesa **[!UICONTROL Delivery template]**. Aggiungi un **[!UICONTROL Label]** alla consegna.

1. Fare clic su **[!UICONTROL To]** per definire la popolazione di destinazione. Per impostazione predefinita, viene applicata la mappatura di destinazione **[!UICONTROL Subscriber application]**. Fate clic su **[!UICONTROL Add]** per selezionare il servizio creato in precedenza.

   ![](assets/nmac_ios_9.png)

1. Nella finestra **[!UICONTROL Target type]**, selezionare **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** e fare clic su **[!UICONTROL Next]**.

1. Nel menu a discesa **[!UICONTROL Service]**, selezionate il servizio creato in precedenza, quindi l&#39;applicazione di destinazione e fate clic su **[!UICONTROL Finish]**.
Le **[!UICONTROL Application variables]** vengono aggiunte automaticamente a seconda di quanto è stato aggiunto durante i passaggi di configurazione.

   ![](assets/nmac_ios_6.png)

1. Modificate la notifica RTF.

   ![](assets/nmac_ios_7.png)

1. Per consentire all’applicazione mobile di scaricare contenuti multimediali, selezionate la casella **[!UICONTROL Mutable content]** nella finestra di notifica di modifica.

1. Fare clic su **[!UICONTROL Save]** e inviare la consegna.

L&#39;immagine e la pagina Web devono essere visualizzate nella notifica push quando vengono ricevute sui dispositivi iOS mobili degli abbonati.

![](assets/nmac_ios_8.png)
