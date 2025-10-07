---
product: campaign
title: Introduzione alla personalizzazione
description: Scopri come personalizzare i messaggi e utilizzare il contenuto condizionale in Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 14%

---

# Introduzione alla personalizzazione{#about-personalization}

Il contenuto e l’aspetto dei messaggi consegnati da Adobe Campaign possono essere personalizzati in diversi modi. Tali modi possono essere combinati in base a criteri ottenuti in modo particolare dai profili dei destinatari. Per le consegne e-mail, puoi definire gli elementi e le condizioni di personalizzazione di una consegna direttamente in JavaScript dalla scheda **[!UICONTROL Source]** del messaggio. In generale, Adobe Campaign ti consente di:

* Personalizzare il formato del messaggio. Vedi [Contenuto messaggio](defining-the-email-content.md#message-content).
* Inserire campi di personalizzazione dinamici. Vedi [Campi di personalizzazione](personalization-fields.md).
* Inserire blocchi di personalizzazione predefiniti. Consulta [Blocchi di personalizzazione](personalization-blocks.md).
* Creare contenuto condizionale. Consulta la sezione [Contenuto condizionale](conditional-content.md).

>[!CAUTION]
>
>Le seguenti variabili sono variabili interne che possono essere utilizzate per la personalizzazione ma che non devono essere modificate: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposition**.


Con Adobe Campaign, personalizza le consegne per inviare messaggi che corrispondono al profilo e agli interessi di ogni destinatario.

Personalization ti aiuta a rendere i tuoi messaggi più pertinenti e coinvolgenti. Puoi utilizzare i dati dei destinatari per adattare il contenuto, aggiungere campi dinamici o visualizzare informazioni diverse in base alle condizioni. Scopri come impostare e utilizzare le funzionalità di personalizzazione nelle consegne nella [documentazione di Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=it){target=_blank}.

Nell’ambito dell’iniziativa di promozione di Campaign v8, è stata riorganizzata la documentazione di Campaign Classic. Le funzioni comuni sono ora disponibili solo nel set di documentazione di Campaign v8.

>[!BEGINTABS]

>[!TAB Documentazione sulla personalizzazione dei contenuti]

Per ulteriori informazioni sulla personalizzazione dei contenuti, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=it){target=_blank}.


[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=it){target=_blank}


>[!TAB Creazione consegna e-mail]

Scopri i passaggi chiave relativi alla creazione di consegne e-mail nella documentazione di Campaign v8:

* [Creare una consegna e-mail](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=it){target="_blank"}: scopri i diversi passaggi necessari per creare una consegna e-mail.
* [Definisci il contenuto dell&#39;e-mail](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=it){target="_blank"}: definisci ciò che l&#39;e-mail includerà: mittente, oggetto, contenuto, immagini.
* [Definisci contenuto interattivo](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=it){target="_blank"}: utilizza il formato AMP interattivo per e-mail per inviare e-mail dinamiche.
* [Invia e-mail su dispositivi mobili giapponesi](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=it){target="_blank"}: utilizza uno dei tre formati giapponesi specifici per l&#39;e-mail su dispositivi mobili.
* [Allega file a un&#39;e-mail](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=it){target="_blank"}: scopri i diversi modi in cui allegare uno o più file a un&#39;e-mail.


>[!TAB Parametri e-mail]

Per informazioni sui parametri delle e-mail nella documentazione di Campaign v8, consulta queste pagine:

* [Collegamento alla pagina mirror](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=it){target="_blank"}: configura la pagina mirror per garantire ai client la migliore esperienza di rendering.
* [Aggiungi un indirizzo Ccn](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=it){target="_blank"}: configura Adobe Campaign per conservare una copia delle e-mail inviate dalla tua piattaforma.
* [Definisci parametri e-mail aggiuntivi](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=it){target="_blank"}: ulteriori informazioni sulle opzioni e i parametri disponibili nelle proprietà di consegna.

Fai riferimento anche a questa [pagina](sending-with-enhanced-mta.md) per informazioni sull&#39;MTA avanzato.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->