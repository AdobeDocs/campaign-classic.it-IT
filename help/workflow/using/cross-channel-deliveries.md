---
solution: Campaign Classic
product: campaign
title: Consegne cross-channel
description: Ulteriori informazioni sulle consegne tra canali
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 7%

---


# Consegne cross-channel{#cross-channel-deliveries}

Le consegne tra canali sono disponibili nella scheda **[!UICONTROL Deliveries]** delle attività del flusso di lavoro della campagna.

Consentono di creare una distribuzione specifica per un canale specifico. Potete specificare il modello su cui basare la consegna e il relativo contenuto, come con una procedura guidata di consegna classica.

I diversi canali disponibili sono:

* [E-mail](../../delivery/using/about-email-channel.md)
* [Posta diretta](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [per Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

Potete specificare una destinazione per la distribuzione a monte del flusso di lavoro utilizzando le diverse attività di targeting.

Ad esempio, qui creeremo un flusso di lavoro per inviare un&#39;e-mail o un SMS per gli utenti che dispongono di notifiche push e quindi una notifica push una settimana dopo. Per eseguire questa operazione:

1. Creare una campagna.
1. Nella scheda **[!UICONTROL Targeting and workflows]** della campagna, aggiungi un **[!UICONTROL Query]** al flusso di lavoro.
1. Configura la query. Ad esempio, in questo caso selezioniamo come dimensione di destinazione i destinatari a cui è stata sottoscritta la notifica push.

   >[!NOTE]
   >
   >Per le notifiche push, ricorda di utilizzare la dimensione di destinazione **applicazioni per utenti iscritti**.

   ![](assets/cross_channel_delivery_1.png)

1. Aggiungete le condizioni del filtro alla query. In questo caso, selezioneremo i destinatari che dispongono di un numero mobile o di un indirizzo e-mail.

   ![](assets/cross_channel_delivery_2.png)

1. Aggiungete un&#39;attività **[!UICONTROL Split]** al flusso di lavoro per dividere i destinatari con un numero mobile e quelli con un indirizzo e-mail.
1. Nella scheda **[!UICONTROL Delivery]**, selezionate una consegna per ciascuna delle destinazioni.

   Per creare la consegna nello stesso modo di una procedura guidata di distribuzione classica, fate doppio clic sull’attività di distribuzione nel flusso di lavoro. Per ulteriori informazioni, consulta questa [pagina](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Aggiungi e configura un&#39;attività **[!UICONTROL Wait]** affinché i destinatari non ricevano troppe consegne alla volta.
1. Aggiungete un&#39;attività **[!UICONTROL Split]** per dividere gli utenti iscritti a un&#39;applicazione mobile iOS o Android.

   Selezionare un servizio per ciascuno dei sistemi operativi. Per ulteriori informazioni sulla creazione del servizio, fare riferimento a questa [pagina](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Seleziona e configura la distribuzione di un&#39;applicazione mobile per ciascuno dei sistemi operativi.

   ![](assets/cross_channel_delivery_5.png)
