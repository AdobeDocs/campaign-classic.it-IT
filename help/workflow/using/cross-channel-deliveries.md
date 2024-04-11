---
product: campaign
title: Consegne cross-channel
description: Ulteriori informazioni sulle consegne cross-channel
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 7%

---

# Consegne cross-channel{#cross-channel-deliveries}



Le consegne cross-channel sono disponibili nel **[!UICONTROL Deliveries]** scheda delle attività del flusso di lavoro della campagna.

I vari canali disponibili sono:

* [E-mail](../../delivery/using/about-email-channel.md)
* [Direct mailing](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [X (precedentemente noto come Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Seleziona il modello su cui desideri basare la consegna e definirne il contenuto.

Puoi specificare un target per la consegna a monte del flusso di lavoro utilizzando le diverse attività di targeting.

Nell’esempio seguente, creeremo un flusso di lavoro per inviare un’e-mail o un SMS per gli abbonati a notifiche push e quindi una notifica push una settimana dopo. Per eseguire questa operazione:

1. Creare una campagna.
1. In **[!UICONTROL Targeting and workflows]** della campagna, aggiungi un **[!UICONTROL Query]** al flusso di lavoro.
1. Configura la query. Ad esempio, in questo caso come dimensione di destinazione vengono selezionati i destinatari abbonati alle notifiche push.

   >[!NOTE]
   >
   >Per le notifiche push, utilizza **applicazioni in abbonamento** dimensione di destinazione.

   ![](assets/cross_channel_delivery_1.png)

1. Aggiungi le condizioni del filtro alla query. In questo caso, selezioneremo i destinatari che hanno un numero di cellulare o un indirizzo e-mail.

   ![](assets/cross_channel_delivery_2.png)

1. Aggiungi un **[!UICONTROL Split]** attività nel flusso di lavoro per dividere i destinatari che hanno un numero di cellulare e quelli che hanno un indirizzo e-mail.
1. In **[!UICONTROL Delivery]** , seleziona una consegna per ciascuna delle destinazioni.

   Crea la consegna nello stesso modo in cui crei una procedura guidata di consegna classica facendo doppio clic sull’attività di consegna nel flusso di lavoro. Per ulteriori informazioni, consulta questa [pagina](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Aggiungere e configurare un **[!UICONTROL Wait]** affinché i destinatari non ricevano troppe consegne contemporaneamente.
1. Aggiungi un **[!UICONTROL Split]** attività per suddividere gli abbonati di un’app mobile iOS o Android.

   Selezionare un servizio per ciascun sistema operativo. Per ulteriori informazioni sulla creazione di servizi, consulta questa [pagina](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Seleziona e configura la consegna di un’app mobile per ciascuno dei sistemi operativi.

   ![](assets/cross_channel_delivery_5.png)
