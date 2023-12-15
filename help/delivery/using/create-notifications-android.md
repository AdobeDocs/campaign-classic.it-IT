---
product: campaign
title: Creare una notifica push per dispositivi Android
description: Scopri come creare notifiche push per Android
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 9756f05e3887bc74578bae00138c4d1317a480f8
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 12%

---

# Creare notifiche per Android{#create-notificaations-android}

Utilizza Adobe Campaign per inviare notifiche push su dispositivi Android. I concetti globali sulla creazione della consegna sono presentati in [questa sezione](steps-about-delivery-creation-steps.md).

Inizia creando una nuova consegna.

![](assets/nmac_delivery_1.png)

Con Firebase Cloud Messaging puoi scegliere tra due tipi di messaggi:

* **[!UICONTROL Data message]**, gestito dall&#39;app client.
  <br>I messaggi vengono inviati direttamente all’app mobile che genererà e visualizzerà la notifica Android al dispositivo. I messaggi di dati contengono solo variabili dell’applicazione personalizzate.

* **[!UICONTROL Notification message]**, gestito automaticamente dall’SDK FCM.
  <br> FCM visualizza automaticamente il messaggio sui dispositivi degli utenti per conto dell’app client. I messaggi di notifica contengono un set preimpostato di parametri e opzioni, ma possono ancora essere personalizzati con variabili personalizzate dell’applicazione.

Per ulteriori informazioni sui tipi di messaggi Firebase Cloud Messaging, consulta [Documentazione FCM](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"}.


## Creare un messaggio dati {#creating-data-message}

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleziona **[!UICONTROL Deliver on Android (android)]** nel **[!UICONTROL Delivery template]** a discesa. Aggiungi un **[!UICONTROL Label]** alla consegna.

1. Clic **[!UICONTROL To]** per definire la popolazione target. Per impostazione predefinita, il **[!UICONTROL Subscriber application]** viene applicata la mappatura target. Clic **[!UICONTROL Add]** per selezionare il servizio.

   ![](assets/nmac_android_7.png)

1. In **[!UICONTROL Target type]** finestra, seleziona **[!UICONTROL Subscribers of an Android mobile application]** e fai clic su **[!UICONTROL Next]**.

1. In **[!UICONTROL Service]** , seleziona il servizio creato in precedenza, quindi fai clic su **[!UICONTROL Finish]**.
Il **[!UICONTROL Application variables]** vengono aggiunte automaticamente in base a ciò che è stato aggiunto durante i passaggi di configurazione.

   ![](assets/nmac_android_6.png)

1. Seleziona **[!UICONTROL data message]** as **[!UICONTROL Message Type]**.

1. Modifica la notifica avanzata.

   ![](assets/nmac_android_5.png)

1. Puoi aggiungere informazioni nelle configurazioni precedenti **[!UICONTROL Application variables]** se necessario. **[!UICONTROL Application variables]** deve essere configurato nel servizio Android e fa parte del payload del messaggio inviato al dispositivo mobile.

1. Clic **[!UICONTROL Save]** e invia la consegna.

L’immagine e la pagina web devono essere visualizzate nella notifica push quando vengono ricevute sui dispositivi mobili Android degli abbonati.

![](assets/nmac_android_4.png)

## Creare un messaggio di notifica {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [Scopri come creare una notifica push Android in un video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html#additional-resources){target="_blank"}.

1. Vai a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Fai clic su **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleziona **[!UICONTROL Deliver on Android (android)]** nel **[!UICONTROL Delivery template]** a discesa. Aggiungi un **[!UICONTROL Label]** alla consegna.

1. Clic **[!UICONTROL To]** per definire la popolazione target. Per impostazione predefinita, il **[!UICONTROL Subscriber application]** viene applicata la mappatura target. Clic **[!UICONTROL Add]** per selezionare il servizio.

   ![](assets/nmac_android_7.png)

1. In **[!UICONTROL Target type]** finestra, seleziona **[!UICONTROL Subscribers of an Android mobile application]** e fai clic su **[!UICONTROL Next]**.

1. In **[!UICONTROL Service]** , seleziona il servizio creato in precedenza, quindi fai clic su **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Seleziona **[!UICONTROL notification message]** as **[!UICONTROL Message Type]**.

1. Aggiungi un titolo e modifica il messaggio. Personalizzare la notifica push con **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: imposta l’ID canale della notifica. L’app deve creare un canale con questo ID canale prima di ricevere qualsiasi notifica con questo ID canale.
   * **[!UICONTROL Sound]**: consente di impostare l&#39;audio da riprodurre quando il dispositivo riceve la notifica.
   * **[!UICONTROL Color]**: imposta il colore dell’icona della notifica.
   * **[!UICONTROL Icon]**: imposta l’icona della notifica da visualizzare sui dispositivi dei profili.
   * **[!UICONTROL Tag]**: imposta l’identificatore utilizzato per sostituire le notifiche esistenti nel cassetto delle notifiche.
   * **[!UICONTROL Click action]**: imposta l’azione associata a un utente che fa clic sulla notifica.

   Per ulteriori informazioni su **[!UICONTROL Notification options]** e come compilare questi campi, consulta [Documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_8.png)

1. Se l’applicazione è configurata con il protocollo API HTTP v1, puoi personalizzare ulteriormente la notifica push con quanto segue **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: imposta il testo del ticker della notifica. Disponibile solo per i dispositivi impostati su Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: imposta l’URL dell’immagine da visualizzare nella notifica.
   * **[!UICONTROL Notification Count]**: imposta il numero di nuove informazioni non lette da visualizzare direttamente sull’icona dell’applicazione.
   * **[!UICONTROL Sticky]**: impostato su true o false. Se impostato su false, la notifica viene automaticamente ignorata quando l’utente fa clic su di essa. Se impostato su true, la notifica viene comunque visualizzata anche quando l’utente fa clic su di essa.
   * **[!UICONTROL Notification Priority]**: imposta i livelli di priorità della notifica su predefinito, minimo, basso o alto. Per ulteriori informazioni, consulta la [documentazione FCM ](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: imposta i livelli di visibilità della notifica su pubblico, privato o segreto. Per ulteriori informazioni, consulta la [documentazione FCM ](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Per ulteriori informazioni su **[!UICONTROL HTTP v1 additional options]** e come compilare questi campi, consulta [Documentazione FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_9.png)

1. Puoi aggiungere informazioni nelle configurazioni precedenti **[!UICONTROL Application variables]** se necessario. **[!UICONTROL Application variables]** deve essere configurato nel servizio Android e fa parte del payload del messaggio inviato al dispositivo mobile.

1. Clic **[!UICONTROL Save]** e invia la consegna.

L’immagine e la pagina web devono essere visualizzate nella notifica push quando vengono ricevute sui dispositivi mobili Android degli abbonati.
