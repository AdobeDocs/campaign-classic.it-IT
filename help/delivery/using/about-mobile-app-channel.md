---
product: campaign
title: Guida introduttiva al canale app mobile
description: Introduzione al canale app mobile in Adobe Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# Guida introduttiva al canale app mobile{#about-mobile-app-channel}

Con Adobe Campaign, crea consegne di notifiche push per inviare messaggi personalizzati agli utenti della tua app mobile.

Le notifiche push consentono di coinvolgere gli utenti su iOS e Android in tempo reale. Che tu invii aggiornamenti, annunci o promozioni, puoi controllare contenuti, tempistiche e targeting. Scopri come impostare e utilizzare il canale push, gestire gli abbonamenti, integrarsi con APN e FCM e personalizzare i messaggi nella [documentazione di Adobe Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

Nell’ambito dell’iniziativa di promozione di Campaign v8, è stata riorganizzata la documentazione di Campaign Classic. Le funzioni comuni sono ora disponibili solo nel set di documentazione di Campaign v8.

>[!BEGINTABS]

>[!TAB Documentazione del canale push]

Per ulteriori informazioni sul canale di notifica push, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=it){target=_blank}.

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=it){target=_blank}


>[!TAB Creazione consegna push]

Scopri i passaggi chiave relativi alla creazione di consegne push nella documentazione di Campaign v8:

* [Creare una notifica push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=it#push-create){target="_blank"}: scopri i diversi passaggi necessari per creare una consegna push.
* [Inviare e monitorare la notifica push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=it#push-test){target="_blank"}: scopri come convalidare, inviare e tenere traccia delle consegne.
* [Progetta una consegna push potenziata da Android](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html?lang=it){target="_blank"}: scopri come creare e configurare notifiche push potenziate per dispositivi Android.
* [Progetta una distribuzione push potenziata da iOS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html?lang=it){target="_blank"}: scopri come progettare e configurare notifiche push potenziate per dispositivi iOS in Adobe Campaign v8.


>[!TAB Parametri push]

Per informazioni sui parametri push nella documentazione di Campaign v8, consulta queste pagine:

* [Prerequisiti per la configurazione](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=it#before-starting){target="_blank"}: scopri come impostare le autorizzazioni e configurare l&#39;app.
* [Configurare la proprietà launch](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=it#launch-property){target="_blank"}: scopri come impostare una proprietà di tag mobile in Raccolta dati di Adobe Experience Platform per abilitare le notifiche push.
* [Configura i servizi push per dispositivi mobili](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=it#push-service){target="_blank"}: configura i servizi push di iOS e Android in Adobe per abilitare le notifiche push mirate per gli utenti delle app mobili.
* [Configura l&#39;estensione nella proprietà mobile](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=it#configure-extension){target="_blank"}: integra l&#39;estensione Campaign nella proprietà mobile per abilitare le notifiche push e gestire in modo efficace le interazioni utente.

>[!ENDTABS]


Le seguenti informazioni sono specifiche per Campaign Classic.

+++ **Installazione del pacchetto**

![](assets/do-not-localize/how-to-video.png) [Scopri come installare il pacchetto per app mobile nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=it#sending-messages)

In qualità di cliente ibrido/in hosting, contatta il team [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per accedere al canale di notifica push in Campaign.

In qualità di cliente on-premise, devi installare un pacchetto integrato.

>[!CAUTION]
>
>Ulteriori informazioni sui pacchetti incorporati, sulle best practice e sui consigli di Campaign in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

I passaggi di installazione sono i seguenti:

1. Accedere all&#39;Assistente all&#39;importazione del pacchetto da **[!UICONTROL Tools > Advanced > Import package]** nella console client di Adobe Campaign.

   ![](assets/package_ios.png)

1. Seleziona **[!UICONTROL Install a standard package]**.

1. Nell&#39;elenco visualizzato, selezionare **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Fare clic su **[!UICONTROL Next]**, quindi su **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto.

   Una volta installati i pacchetti, la barra di avanzamento mostra **100%** ed è possibile visualizzare il seguente messaggio nei registri di installazione: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la finestra di installazione.

Al termine di questo passaggio, puoi configurare le app Android e iOS. Consulta la [documentazione](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=it){target="_blank"} di Campaign v8.

+++

+++ **Risoluzione dei problemi**

Se il dispositivo mobile è connesso a Wi-Fi e non si ricevono notifiche, verificare che le porte FCM/APN non siano bloccate dal firewall.

**Android**: il dispositivo mobile si connette ai server FCM sulle porte da 5228 a 5230. Devi quindi configurare il firewall in modo che autorizzi la connessione con FCM. Le porte da aprire sono: 5228 (le più utilizzate), 5229 e 5230.

**iOS**:

Connettore HTTP/2: è necessario consentire la comunicazione da e verso i seguenti server:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>Per ulteriori informazioni sui due connettori, consulta la [documentazione](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=it){target="_blank"} di Campaign v8.

+++
