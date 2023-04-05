---
product: campaign
title: Configurare l’app mobile iOS in Adobe Campaign
description: Scopri come configurare la tua app mobile per iOS
feature: Push
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 8d635722b8961b3edac9cc98f00f17b86f4ee523
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 7%

---

# Passaggi di configurazione per iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

![](../../assets/v7-only.svg)

Una volta installato il pacchetto, puoi definire le impostazioni dell’app iOS in Adobe Campaign Classic.

>[!NOTE]
>
>Per scoprire come configurare l’app per Android e come creare una consegna per Android, consulta questo articolo [sezione](configuring-the-mobile-application-android.md).

I passaggi chiave sono i seguenti:

1. [Configurare l’account esterno iOS](#configuring-external-account-ios)
1. [Configurare il servizio iOS](#configuring-ios-service)
1. [Integrare l’app mobile iOS in Campaign](#creating-ios-app)

Potrai quindi [creare una notifica push per dispositivi iOS](create-notifications-ios.md).


## Configurare l’account esterno iOS {#configuring-external-account-ios}

Per iOS, il connettore iOS HTTP/2 invia notifiche al servizio APN HTTP/2.

Per configurare questo connettore, effettua le seguenti operazioni:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleziona la **[!UICONTROL iOS routing]** conto esterno.
1. In **[!UICONTROL Connector]** , compila **[!UICONTROL Access URL of the connector]** con il seguente URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Fai clic su **[!UICONTROL Save]**.

Il connettore iOS è ora configurato. Puoi iniziare a creare il servizio.

## Configurare il servizio iOS {#configuring-ios-service}

>[!CAUTION]
>
>L’applicazione deve essere stata configurata per le azioni push PRIMA di qualsiasi integrazione con Adobe SDK.
>
>In caso contrario, si prega di fare riferimento a [questa pagina](https://developer.apple.com/documentation/usernotifications).

1. Vai a **[!UICONTROL Profiles and Targets > Services and subscriptions]** nodo e fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definire un **[!UICONTROL Label]** e **[!UICONTROL Internal name]**.
1. Vai a **[!UICONTROL Type]** campo e seleziona **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Il valore predefinito **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** la mappatura di destinazione è collegata alla tabella dei destinatari. Se desideri utilizzare una mappatura di destinazione diversa, devi creare una nuova mappatura di destinazione e inserirla nel **[!UICONTROL Target mapping]** campo del servizio. Per ulteriori informazioni sulla creazione della mappatura di destinazione, consulta [Guida alla configurazione](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Quindi fai clic sul pulsante **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Crea le tue applicazioni di sviluppo e produzione iOS. Per ulteriori informazioni, consulta questa [sezione](configuring-the-mobile-application.md#creating-ios-app).

## Creare un’app mobile iOS {#creating-ios-app}

Dopo aver creato il servizio, crea l’applicazione iOS in Campaign. Segui i passaggi seguenti:

1. Dal servizio appena creato, fai clic su **[!UICONTROL Add]** per selezionare il tipo di applicazione.

   ![](assets/nmac_service_2.png)

1. Viene visualizzata la finestra seguente. Seleziona **[!UICONTROL Create an iOS application]** e inizia inserendo il **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Puoi arricchire il contenuto di un messaggio push con alcuni **[!UICONTROL Application variables]** se necessario. Sono completamente personalizzabili e una parte del payload del messaggio inviato al dispositivo mobile.
Nell’esempio seguente, aggiungiamo **mediaURl** e **mediaExt** per creare una notifica push potenziata e quindi fornisce all’applicazione l’immagine da visualizzare all’interno della notifica.

   ![](assets/nmac_ios_3.png)

1. La **[!UICONTROL Subscription parameters]** consente di definire la mappatura con un’estensione del **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema.

   >[!NOTE]
   >
   >Assicurati di non utilizzare lo stesso certificato per la versione di sviluppo (sandbox) e la versione di produzione dell&#39;applicazione.

1. La **[!UICONTROL Sounds]** consente di specificare un suono da riprodurre. Fai clic su **[!UICONTROL Add]** e riempire **[!UICONTROL Internal name]** campo che deve contenere il nome del file incorporato nell&#39;applicazione o il nome dell&#39;audio di sistema.

1. Fai clic su **[!UICONTROL Next]** per iniziare a configurare l&#39;applicazione di sviluppo.

1. Assicurati che le stesse **[!UICONTROL Integration key]** è definito in Adobe Campaign e nel codice dell&#39;applicazione tramite l&#39;SDK. Per ulteriori informazioni, consulta [questa pagina](integrating-campaign-sdk-into-the-mobile-application.md). Questa chiave di integrazione, specifica per ogni applicazione, consente di collegare l’app mobile alla piattaforma Adobe Campaign.

   >[!NOTE]
   >
   > La **[!UICONTROL Integration key]** è completamente personalizzabile con il valore stringa, ma deve essere esattamente uguale a quello specificato nell&#39;SDK.

1. Seleziona una delle icone predefinite dal **[!UICONTROL Application icon]** per personalizzare l’app mobile nel servizio.

1. Seleziona **[!UICONTROL Authentication mode]**. Puoi sempre modificare la modalità di autenticazione in un secondo momento in **[!UICONTROL Certificate]** scheda della tua app mobile.
   * **[!UICONTROL Certificate-based authentication]**: Fai clic su **[!UICONTROL Enter the certificate...]**  quindi seleziona la tua chiave p12 e immetti la password fornita dallo sviluppatore di applicazioni mobili.
   * **[!UICONTROL Token-based authentication]**: Riempire le impostazioni di connessione **[!UICONTROL Key ID]**, **[!UICONTROL Team ID]** e **[!UICONTROL Bundle ID]** quindi seleziona il certificato p8 facendo clic su **[!UICONTROL Enter the private key]**. Per ulteriori informazioni **[!UICONTROL Token-based authentication]**, fare riferimento a [Documentazione di Apple](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe consiglia di utilizzare **[!UICONTROL Token-based authentication]** per la configurazione di iOS, poiché questa modalità di autenticazione è più protetta e non associata alla scadenza del certificato.

   ![](assets/nmac_ios_4.png)

1. Puoi fare clic su **[!UICONTROL Test the connection]** per essere sicuri che abbia successo.

1. Fai clic su **[!UICONTROL Next]** per iniziare a configurare l&#39;applicazione di produzione e seguire gli stessi passaggi descritti in precedenza.

   ![](assets/nmac_ios_5.png)

1. Fai clic su **[!UICONTROL Finish]**.

L’applicazione iOS è ora pronta per essere utilizzata in Campaign Classic.
