---
product: campaign
title: Introduzione alla messaggistica transazionale
description: Ulteriori informazioni sul principio operativo della messaggistica transazionale di Adobe Campaign Classic e sui passaggi chiave
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 8%
---
# Introduzione alla messaggistica transazionale {#about-transactional-messaging}



## Panoramica {#overview}

**La messaggistica transazionale** (Centro messaggi) è un modulo di Campaign progettato per gestire le notifiche di attivazione personalizzate generate da eventi inviati da un sistema di informazioni esterno.

Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8. Per ulteriori informazioni sui messaggi transazionali, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}.

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

Questa sezione descrive l’architettura della messaggistica transazionale e la configurazione delle istanze di controllo ed esecuzione, specifiche per le distribuzioni on-premise e ibride.

>[!IMPORTANT]
>
>La messaggistica transazionale richiede una licenza specifica. Controlla il contratto di licenza.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Principio operativo della messaggistica transazionale {#transactional-messaging-operating-principle}

Il modulo di messaggistica transazionale di Adobe Campaign si integra in un sistema di informazioni che restituisce eventi da trasformare in messaggi transazionali personalizzati. Questi messaggi possono essere inviati singolarmente o in batch tramite e-mail, SMS o notifiche push.

Questa funzionalità si basa su un&#39;architettura specifica, in cui l&#39;**istanza di esecuzione** è separata dall&#39;**istanza di controllo**. Questa distribuzione garantisce una maggiore disponibilità e una migliore gestione del carico. Per ulteriori informazioni, consulta [Architettura dei messaggi transazionali](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Per creare nuovi utenti per le istanze di esecuzione del Centro messaggi ospitate su Adobe Cloud, devi contattare [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Gli utenti del Centro messaggi sono operatori specifici che richiedono autorizzazioni dedicate per accedere alle cartelle **[!UICONTROL Real time events (nmsRtEvent)]**.

>[!NOTE]
>
>Adobe Campaign dà priorità all’elaborazione dei messaggi transazionali rispetto a qualsiasi altra consegna.

## Passaggi chiave {#key-steps}

Di seguito sono riepilogati i passaggi principali per la creazione e la gestione di messaggi transazionali personalizzati in Adobe Campaign.

### Passaggi da eseguire sull’istanza di controllo

Nell&#39;**istanza di controllo** è necessario eseguire le azioni seguenti:

1. [Crea un tipo di evento](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"} (documentazione di Campaign v8).
1. [Crea e progetta il modello di messaggio](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentazione di Campaign v8). Collega un evento al messaggio durante questo passaggio.
1. [Verifica il messaggio](../../message-center/using/testing-message-templates.md).
1. [Pubblica il modello di messaggio](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentazione di Campaign v8).

>[!NOTE]
>
>Tutti i passaggi precedenti vengono eseguiti sull&#39;**istanza di controllo**. La pubblicazione del modello nell&#39;istanza di controllo lo pubblicherà anche in tutte le **istanze di esecuzione**. Per ulteriori informazioni sulle istanze di messaggistica transazionale, consulta [Architettura della messaggistica transazionale](../../message-center/using/transactional-messaging-architecture.md).

### Elaborazione degli eventi nell’istanza di esecuzione

Dopo aver progettato e pubblicato il modello di messaggio transazionale, se viene attivato un evento corrispondente, i passaggi principali seguenti vengono eseguiti sull&#39;**istanza di esecuzione**:

1. Quando l&#39;evento viene generato dal sistema di informazioni esterno, i dati rilevanti vengono inviati a Campaign tramite i metodi **PushEvent** e **PushEvents**. Consulta [Raccolta eventi](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"} (documentazione di Campaign v8).
1. L’evento è collegato al modello di messaggio appropriato. Consulta [Instradamento verso un modello](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"} (documentazione di Campaign v8).
1. Una volta completata la fase di arricchimento, la consegna viene inviata. Consulta [Esecuzione della consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentazione di Campaign v8). Ogni destinatario riceve un messaggio personalizzato.

## Argomenti correlati {#related-topics}

* [Introduzione ai canali di comunicazione](../../delivery/using/communication-channels.md)
* [Passaggi chiave per la creazione della consegna](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=it){target="_blank"}
* [Architettura della messaggistica transazionale](../../message-center/using/transactional-messaging-architecture.md)
* [Accedere ai rapporti sulla messaggistica transazionale](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentazione di Campaign v8)
