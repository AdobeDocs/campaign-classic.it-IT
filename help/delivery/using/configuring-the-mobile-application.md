---
solution: Campaign Classic
product: campaign
title: Configurazione dell’applicazione mobile iOS in  Adobe Campaign
description: Scopri come configurare l’applicazione mobile per iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 7%

---


# Passaggi di configurazione per iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Una volta installato il pacchetto, potete definire le impostazioni dell&#39;app iOS in Adobe Campaign Classic.

>[!NOTE]
>
>Per informazioni su come configurare l&#39;app per Android e come creare una consegna per Android, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application-android.md).

## Configurazione dell&#39;account esterno iOS {#configuring-external-account-ios}

Per iOS, il connettore iOS HTTP/2 invia notifiche agli APN HTTP/2.

Per configurare questo connettore, procedere come segue:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Select the **[!UICONTROL iOS routing]** external account.
1. Nella **[!UICONTROL Connector]** scheda, compila il **[!UICONTROL Access URL of the connector]** campo con il seguente URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

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
>In caso contrario, fare riferimento a [questa pagina](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

1. Vai al **[!UICONTROL Profiles and Targets > Services and subscriptions]** nodo e fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. Vai al **[!UICONTROL Type]** campo e seleziona **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Il mapping di **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** destinazione predefinito è collegato alla tabella dei destinatari. Se desiderate utilizzare un mapping di destinazione diverso, dovete creare un nuovo mapping di destinazione e immetterlo nel **[!UICONTROL Target mapping]** campo del servizio. Per ulteriori informazioni sulla creazione della mappatura di destinazione, consulta la guida [alla](../../configuration/using/about-custom-recipient-table.md)configurazione.

   ![](assets/nmac_ios.png)

1. Quindi fate clic sul **[!UICONTROL Add]** pulsante per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Creare le applicazioni di sviluppo e produzione iOS. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app).

## Creazione di un’applicazione mobile iOS {#creating-ios-app}

Dopo aver creato il servizio, è ora necessario creare l&#39;applicazione iOS:

1. Dal servizio appena creato, fate clic sul **[!UICONTROL Add]** pulsante per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Viene visualizzata la finestra seguente. Seleziona **[!UICONTROL Create an iOS application]** e inizia inserendo il **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Come opzione, puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]** se necessario. Sono completamente personalizzabili e una parte del payload di messaggi inviato al dispositivo mobile.
Nell&#39;esempio seguente, aggiungiamo **mediaURl** e **mediaExt** per creare una notifica push potenziata e quindi fornisce all&#39;applicazione l&#39;immagine da visualizzare all&#39;interno della notifica.

   ![](assets/nmac_ios_3.png)

1. La **[!UICONTROL Subscription parameters]** scheda consente di definire la mappatura con un&#39;estensione dello **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema.

   >[!NOTE]
   >
   >Accertatevi di non utilizzare lo stesso certificato per la versione di sviluppo (sandbox) e per la versione di produzione dell&#39;applicazione.

1. La **[!UICONTROL Sounds]** scheda consente di specificare un suono da riprodurre. Fare clic **[!UICONTROL Add]** e compilare il **[!UICONTROL Internal name]** campo che deve contenere il nome del file incorporato nell&#39;applicazione o il nome dell&#39;audio di sistema.

1. Fare clic **[!UICONTROL Next]** per avviare la configurazione dell&#39;applicazione di sviluppo.

1. Assicurati che lo stesso **[!UICONTROL Integration key]** sia definito in  Adobe Campaign e nel codice dell’applicazione tramite l’SDK. Per ulteriori informazioni, consulta: [Integrazione di Campaign SDK nell&#39;applicazione](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)mobile. Questa chiave di integrazione, specifica per ogni applicazione, consente di collegare l’applicazione mobile alla piattaforma Adobe Campaign .

   >[!NOTE]
   >
   > L’ **[!UICONTROL Integration key]** impostazione è completamente personalizzabile con il valore stringa, ma deve corrispondere esattamente a quella specificata nell’SDK.

1. Seleziona una delle icone predefinite dal **[!UICONTROL Application icon]** campo per personalizzare l’applicazione mobile nel servizio.

1. Seleziona **[!UICONTROL Authentication mode]**. Puoi sempre modificare la modalità di autenticazione in un secondo momento nella **[!UICONTROL Certificate]** scheda dell’applicazione mobile.
   * **[!UICONTROL Certificate-based authentication]**: Fate clic **[!UICONTROL Enter the certificate...]** quindi sulla chiave p12 e immettete la password fornita dallo sviluppatore di applicazioni mobili.
   * **[!UICONTROL Token-based authentication]**: Compilate le impostazioni di connessione **[!UICONTROL Key ID]**, **[!UICONTROL Team ID]** quindi **[!UICONTROL Bundle ID]** selezionate il certificato p8 facendo clic su **[!UICONTROL Enter the private key]**. For more on **[!UICONTROL Token-based authentication]**, refer to [Apple documentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   >  Adobe consiglia di utilizzare **[!UICONTROL Token-based authentication]** per la configurazione iOS in quanto questa modalità di autenticazione è più sicura e non è associata alla scadenza del certificato.

   ![](assets/nmac_ios_4.png)

1. Potete fare clic **[!UICONTROL Test the connection]** per verificare che abbia esito positivo.

1. Fare clic **[!UICONTROL Next]** per avviare la configurazione dell&#39;applicazione di produzione e seguire gli stessi passaggi descritti in precedenza.

   ![](assets/nmac_ios_5.png)

1. Fai clic su **[!UICONTROL Finish]**.

L&#39;applicazione iOS è ora pronta per essere utilizzata in Campaign Classic.

## Creazione di una notifica iOS RTF {#creating-ios-delivery}

Con iOS 10 o versione successiva, è possibile generare notifiche avanzate.  Adobe Campaign può inviare notifiche utilizzando variabili che consentiranno al dispositivo di visualizzare una notifica RTF.

È ora necessario creare una nuova consegna e collegarla all’applicazione mobile creata.

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleziona **[!UICONTROL Deliver on iOS (ios)]** nell’ **[!UICONTROL Delivery template]** elenco a discesa. Aggiungi un **[!UICONTROL Label]** biglietto alla consegna.

1. Fare clic **[!UICONTROL To]** per definire la popolazione di destinazione. Per impostazione predefinita, viene applicata la mappatura della **[!UICONTROL Subscriber application]** destinazione. Fate clic **[!UICONTROL Add]** per selezionare il servizio creato in precedenza.

   ![](assets/nmac_ios_9.png)

1. Nella **[!UICONTROL Target type]** finestra, selezionare **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** e fare clic su **[!UICONTROL Next]**.

1. Nell&#39; **[!UICONTROL Service]** elenco a discesa, selezionate il servizio creato in precedenza e quindi l&#39;applicazione di destinazione e fate clic su **[!UICONTROL Finish]**.
Le **[!UICONTROL Application variables]** vengono aggiunte automaticamente in base a quanto è stato aggiunto durante i passaggi di configurazione.

   ![](assets/nmac_ios_6.png)

1. Modificate la notifica RTF.

   ![](assets/nmac_ios_7.png)

1. Selezionate la **[!UICONTROL Mutable content]** casella nella finestra di notifica di modifica per consentire all’applicazione mobile di scaricare il contenuto multimediale.

1. Fai clic su **[!UICONTROL Save]** e invia la consegna.

L&#39;immagine e la pagina Web devono essere visualizzate nella notifica push quando vengono ricevute sui dispositivi iOS mobili degli abbonati.

![](assets/nmac_ios_8.png)
