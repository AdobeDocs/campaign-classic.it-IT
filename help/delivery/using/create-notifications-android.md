---
product: campaign
title: Creare una notifica push per dispositivi Android
description: Scopri come creare notifiche push per Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 1%

---

# Creare notifiche per Android{#create-notificaations-android}

Utilizza Adobe Campaign per inviare notifiche push sui dispositivi Android. I concetti globali sulla creazione della consegna sono descritti in [questa sezione](steps-about-delivery-creation-steps.md).

Inizia creando una nuova consegna.

![](assets/nmac_delivery_1.png)

Con Firebase Cloud Messaging, puoi scegliere tra due tipi di messaggi:

* **[!UICONTROL Data message]**, gestito dall’app client.
   <br>I messaggi vengono inviati direttamente all’app mobile, che genererà e visualizzerà la notifica android sul dispositivo. I messaggi di dati contengono solo le variabili di applicazione personalizzate.

* **[!UICONTROL Notification message]**, gestito automaticamente dall&#39;SDK FCM.
   <br> FCM visualizza automaticamente il messaggio sui dispositivi degli utenti per conto dell’app client. I messaggi di notifica contengono un set predefinito di parametri e opzioni, ma possono ancora essere ulteriormente personalizzati con variabili di applicazione personalizzate.

Per ulteriori informazioni sui tipi di messaggi Firebase Cloud Messaging, consulta la [documentazione FCM](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

## Creare un messaggio dati {#creating-data-message}

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

## Creare un messaggio di notifica {#creating-notification-message}

>[!NOTE]
>
>Ulteriori opzioni per il messaggio di notifica sono disponibili solo con la configurazione dell’API HTTP v1. Per ulteriori informazioni, consulta questa [sezione](configuring-the-mobile-application-android.md#android-service-httpv1).

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
