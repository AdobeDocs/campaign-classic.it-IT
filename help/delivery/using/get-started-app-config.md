---
solution: Campaign Classic
product: campaign
title: 'Configurazione dell’app mobile in Adobe Campaign '
description: Scopri come iniziare con la configurazione dell’applicazione mobile
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 9%

---


# Introduzione alla configurazione dell’app

In questa sezione potete trovare un esempio di configurazione basato su una società che vende pacchetti per le vacanze online. La sua applicazione mobile (Neotrips) è disponibile ai suoi clienti in due versioni: Neotrips per Android e Neotrips per iOS.

Per inviare le notifiche push in  Adobe Campaign, è necessario:

* Crea un servizio di informazioni sui **[!UICONTROL Mobile application]** tipi per l’applicazione mobile Neotrips. Fate riferimento a [questa sezione per iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). e [questa sezione per Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Aggiungete al servizio le versioni iOS e Android dell&#39;applicazione.
* Create una consegna sia per iOS che per Android. [Consulta questa pagina](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Passate alla **[!UICONTROL Subscriptions]** scheda del servizio per visualizzare l’elenco degli utenti iscritti al servizio, ovvero tutti gli utenti che hanno installato l’applicazione sul proprio dispositivo mobile e hanno accettato di ricevere le notifiche.

## Installazione del pacchetto {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [Scopri come installare il pacchetto dell’app mobile in un video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

In qualità di cliente ibrido/ospitato, contatta  team di assistenza clienti di Adobe per accedere al canale di notifica push in Campaign.

In qualità di cliente locale, è necessario eseguire i seguenti passaggi di installazione:

1. Accedete alla procedura guidata di importazione dei pacchetti **[!UICONTROL Tools > Advanced > Package import...]** nella console client Adobe Campaign .

   ![](assets/package_ios.png)

1. Seleziona **[!UICONTROL Install a standard package]**.

1. Nell&#39;elenco visualizzato, selezionare **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Fate clic **[!UICONTROL Next]**, quindi **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto.

   Una volta installati i pacchetti, la barra di avanzamento mostra il **100%** ed è possibile visualizzare il seguente messaggio nei registri di installazione: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la finestra di installazione.

Al termine di questo passaggio, potete configurare le app Android e iOS.
Consultare le sezioni seguenti:

* [Passaggi di configurazione per iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Passaggi di configurazione per Android](../../delivery/using/configuring-the-mobile-application-android.md)
