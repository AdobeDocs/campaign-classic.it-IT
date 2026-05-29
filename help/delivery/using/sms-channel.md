---
product: campaign
title: Introduzione al canale SMS
description: Introduzione al canale SMS
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
TQID: https://experienceleague.adobe.com/bk-HUOGv3u60NzOnXD0huo74lBJJuiBOaOJeGmPa2E4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 484
ht-degree: 10%

---

# Introduzione al canale SMS{#sms-channel}

Utilizza Adobe Campaign per inviare messaggi di testo ai clienti sui loro dispositivi mobili. Dall’editor SMS puoi creare, personalizzare e visualizzare in anteprima i messaggi in formato testo.

Gli SMS sono un canale diretto ed estremamente efficace per raggiungere gli utenti ovunque si trovino. Con tassi di apertura elevati e consegna quasi istantanea, SMS è ideale per avvisi urgenti, aggiornamenti transazionali e messaggi promozionali concisi. Utilizza gli SMS per integrare la tua strategia cross-channel e offrire comunicazioni efficaci e in tempo reale. Scopri come configurare e utilizzare il canale SMS in modo efficace nella [documentazione di Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=it){target=_blank}.

Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8.

>[!BEGINTABS]

>[!TAB Documentazione del canale SMS]

Per ulteriori informazioni sul canale SMS, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=it){target=_blank}.


[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=it){target=_blank}


>[!TAB Creazione consegna SMS]

Scopri i passaggi chiave relativi alla creazione di consegne SMS **nella documentazione di Campaign v8**:

* [Panoramica del canale SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=it){target="_blank"}: scopri come inviare messaggi di testo ai clienti sui loro dispositivi mobili.
* [Creare una consegna SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/create-sms.html){target="_blank"}: scopri i diversi passaggi necessari per creare una nuova consegna SMS.
* [Definisci il contenuto](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-content.html){target="_blank"}: scopri come personalizzare il contenuto dei messaggi SMS.
* [Seleziona il pubblico](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience.html){target="_blank"}: la destinazione principale viene estratta dal database di Adobe Campaign o può anche essere archiviata in un file esterno.
* [Invia bozze SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs.html): l&#39;impostazione di un ciclo di convalida della consegna è essenziale. Assicurati che il contenuto sia approvato prima di inviarlo al pubblico.
* [Invia al pubblico](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=it): quando il tuo SMS viene convalidato, ora puoi inviarlo al relativo pubblico.
* [Monitora e tieni traccia di un SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms-monitor.html?lang=it): monitora la consegna SMS per assicurarti che le campagne di marketing siano efficienti.


>[!TAB Configurazione SMS]

Per informazioni sulla configurazione degli SMS, consulta queste pagine. Queste pagine sono specifiche di Campaign v7.

* [Configurazione autonoma](sms-set-up.md): scopri come configurare il canale SMS in un&#39;istanza autonoma.
* [Configurazione mid-sourcing](sms-set-up-mid.md): scopri come inviare a un telefono cellulare con mid-server.
* [Connettore SMS](sms-protocol.md): informazioni sul protocollo e sulle impostazioni del connettore SMS.
* [Configurazione aggiuntiva](sms-send.md): informazioni sui parametri avanzati e altre configurazioni aggiuntive.
* [Risoluzione dei problemi](troubleshooting-sms.md): è stata elencata una serie di potenziali problemi e relative soluzioni.

>[!ENDTABS]



<!--
Use Adobe Campaign to send personalized SMS messages.

Before starting sending SMS:

* Make sure recipient profiles contain at least a mobile phone in their profile.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).

The key steps to send a SMS are as follows:

* [Configure the SMS channel](sms-set-up.md)
* [Create a SMS delivery](sms-create.md)
* [Define the audience](sms-create.md#selecting-the-target-population)
* [Define the SMS content](sms-create.md#defining-the-sms-content)
* [Send, monitor and track SMS](sms-send.md)
* [Troubleshoot](troubleshooting-sms.md)

In addition, you need to be familiar with SMS protocol and settings. Walk through the connection set up between Adobe Campaign and a SMPP provider in [this document](sms-protocol.md)

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Adobe Campaign also lets you submit notifications on mobile terminals, via its **Adobe Campaign Mobile App Channel (NMAC)** option. 
> 
>For more on this, refer to the [Get started with mobile app channel](about-mobile-app-channel.md) section.
-->