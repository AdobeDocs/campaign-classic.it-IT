---
product: campaign
title: Consegne cross-channel
description: Ulteriori informazioni sulle consegne cross-channel
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 7%

---

# Consegne cross-channel{#cross-channel-deliveries}

Le consegne cross-channel sono disponibili nella scheda **[!UICONTROL Deliveries]** delle attività del flusso di lavoro della campagna.

Consentono di creare una consegna specifica per un particolare canale. Puoi specificare il modello su cui basare la consegna e il relativo contenuto, esattamente come con una procedura guidata di consegna classica.

I vari canali disponibili sono:

* [E-mail](../../delivery/using/about-email-channel.md)
* [Direct mailing](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [per Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

Puoi specificare un target per la consegna a monte del flusso di lavoro utilizzando le diverse attività di targeting.

Ad esempio, in questo caso creeremo un flusso di lavoro per inviare un’e-mail o un SMS per gli abbonati alle notifiche push e quindi una notifica push una settimana dopo. Per eseguire questa operazione:

1. Creare una campagna.
1. Nella scheda **[!UICONTROL Targeting and workflows]** della campagna, aggiungi un **[!UICONTROL Query]** al flusso di lavoro.
1. Configura la query. Ad esempio, in questo caso selezioni i destinatari abbonati alle notifiche push come dimensione di destinazione.

   >[!NOTE]
   >
   >Per le notifiche push, ricorda di utilizzare la dimensione di destinazione **applicazioni utente con sottoscrizione**.

   ![](assets/cross_channel_delivery_1.png)

1. Aggiungi le condizioni del filtro alla query. In questo caso, selezioneremo i destinatari che hanno un numero mobile o un indirizzo e-mail.

   ![](assets/cross_channel_delivery_2.png)

1. Aggiungi un’attività **[!UICONTROL Split]** al flusso di lavoro per dividere i destinatari con un numero di cellulare e quelli con un indirizzo e-mail.
1. Nella scheda **[!UICONTROL Delivery]** , seleziona una consegna per ciascuna delle tue destinazioni.

   Crea la consegna come con una procedura guidata di consegna classica facendo doppio clic sull’attività di consegna nel flusso di lavoro. Per ulteriori informazioni, consulta questa [pagina](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Aggiungi e configura un’attività **[!UICONTROL Wait]** in modo che i destinatari non ricevano troppe consegne alla volta.
1. Aggiungi un’attività **[!UICONTROL Split]** per dividere gli abbonati a un’app mobile iOS o Android.

   Selezionare un servizio per ciascuno dei sistemi operativi. Per ulteriori informazioni sulla creazione di un servizio, consulta questa [pagina](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Seleziona e configura una consegna di app mobili per ciascuno dei sistemi operativi.

   ![](assets/cross_channel_delivery_5.png)
