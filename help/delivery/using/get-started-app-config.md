---
product: campaign
title: 'Configurazione dell’app mobile in Adobe Campaign '
description: Scopri come iniziare con la configurazione dell’app mobile
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 615b56c5f4362b0f47ec5700be7d170c0e108f4c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 10%

---

# Introduzione alla configurazione dell’app

In questa sezione puoi trovare un esempio di configurazione basato su un’azienda che vende pacchetti vacanza online. La sua applicazione mobile (Neotrips) è disponibile ai suoi clienti in due versioni: Suggerimenti per Android e Neotrips per iOS.

Per inviare notifiche push in Adobe Campaign, devi:

* Crea un servizio di informazioni di tipo **[!UICONTROL Mobile application]** per l’app mobile Neotrips. Fai riferimento a [questa sezione per iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). e [questa sezione per Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Aggiungi al servizio le versioni iOS e Android dell&#39;applicazione.
* Crea una consegna per [iOS](create-notifications-ios.md) e [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Vai alla scheda **[!UICONTROL Subscriptions]** del servizio per visualizzare l&#39;elenco degli abbonati al servizio, ovvero tutte le persone che hanno installato l&#39;applicazione sul loro cellulare e hanno accettato di ricevere notifiche.

## Installa il pacchetto {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [Scopri come installare il pacchetto dell’app mobile nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

In qualità di cliente ibrido/ospitato, contatta il team [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per accedere al canale di notifica push in Campaign.

In qualità di cliente on-premise, devi installare un pacchetto integrato.

>[!CAUTION]
>
>Ulteriori informazioni sui pacchetti incorporati, sulle best practice e sui consigli di Campaign in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

I passaggi di installazione sono:

1. Accedi alla procedura guidata di importazione del pacchetto da **[!UICONTROL Tools > Advanced > Package import...]** nella console client di Adobe Campaign.

   ![](assets/package_ios.png)

1. Seleziona **[!UICONTROL Install a standard package]**.

1. Nell&#39;elenco visualizzato, selezionare **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Fai clic su **[!UICONTROL Next]**, quindi **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto.

   Una volta installati i pacchetti, la barra di avanzamento mostra **100%** e puoi visualizzare il seguente messaggio nei log di installazione: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la finestra di installazione.

Al termine di questo passaggio, puoi configurare le app Android e iOS.
Fai riferimento a queste sezioni:

* [Passaggi di configurazione per iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Passaggi di configurazione per Android](../../delivery/using/configuring-the-mobile-application-android.md)
