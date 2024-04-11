---
product: campaign
title: Configurare l’app mobile in Adobe Campaign
description: Scopri come iniziare con la configurazione dell’app mobile
feature: Push
role: User, Developer
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 5%

---

# Introduzione alla configurazione dell’app



Puoi trovare in questa sezione un esempio di configurazione basato su un’azienda che vende pacchetti vacanza online. La sua app mobile (Neotrips) è disponibile per i suoi clienti in due versioni: Neotrips per Android e Neotrips per iOS.

Per inviare notifiche push in Adobe Campaign, devi:

* Creare un **[!UICONTROL Mobile application]** servizio informazioni sui tipi per l’app mobile Neotrips. Fai riferimento a [questa sezione per iOS](configuring-the-mobile-application.md#configuring-ios-service). e [questa sezione per Android](configuring-the-mobile-application-android.md#configuring-android-service).
* Aggiungi le versioni iOS e Android dell’applicazione a questo servizio.
* Creare una consegna per [iOS](create-notifications-ios.md) e [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Vai a **[!UICONTROL Subscriptions]** scheda del servizio per visualizzare l’elenco degli abbonati al servizio, ovvero tutte le persone che hanno installato l’applicazione sul proprio cellulare e hanno accettato di ricevere notifiche.

## Installare il pacchetto {#installing-package-ios}

[!BADGE On-premise e ibrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"}

![](assets/do-not-localize/how-to-video.png) [Scopri come installare il pacchetto per app mobile nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

In qualità di cliente ibrido/in hosting, contatta [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team per accedere al canale di notifica push in Campaign.

In qualità di cliente on-premise, devi installare un pacchetto integrato.

>[!CAUTION]
>
>Ulteriori informazioni sui pacchetti incorporati, sulle best practice e sui consigli di Campaign in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

I passaggi di installazione sono i seguenti:

1. Accedi alla procedura guidata di importazione del pacchetto da **[!UICONTROL Tools > Advanced > Import package]** nella console client di Adobe Campaign.

   ![](assets/package_ios.png)

1. Seleziona **[!UICONTROL Install a standard package]**.

1. Nell&#39;elenco visualizzato selezionare **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Clic **[!UICONTROL Next]**, quindi **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto.

   Una volta installati i pacchetti, la barra di avanzamento viene visualizzata **100%** e puoi visualizzare il seguente messaggio nei registri di installazione: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la finestra di installazione.

Al termine di questo passaggio, puoi configurare le app Android e iOS.
Consulta queste sezioni:

* [Passaggi di configurazione per iOS](configuring-the-mobile-application.md)

* [Passaggi di configurazione per Android](configuring-the-mobile-application-android.md)
