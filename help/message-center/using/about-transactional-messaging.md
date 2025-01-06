---
product: campaign
title: Introduzione alla messaggistica transazionale
description: Ulteriori informazioni sul principio operativo della messaggistica transazionale di Adobe Campaign Classic e sui passaggi chiave
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 4%

---


# Introduzione alla messaggistica transazionale {#about-transactional-messaging}



## Panoramica {#overview}

**La messaggistica transazionale** (Centro messaggi) è un modulo di Campaign progettato per gestire le notifiche di attivazione personalizzate generate da eventi inviati da un sistema di informazioni esterno.

Un messaggio transazionale è una comunicazione singola e univoca, inviata in tempo reale da un provider, ad esempio un sito web. È particolarmente atteso, perché contiene informazioni importanti che il destinatario desidera controllare o confermare.

Le funzionalità di messaggistica transazionale sono progettate per supportare la scalabilità e fornire un servizio 24 ore su 24, 7 giorni su 7.

* **Quando scade?** Poiché questo messaggio contiene informazioni importanti, l&#39;utente si aspetta che vengano inviate in tempo reale. Di conseguenza, il ritardo tra l’attivazione dell’evento e l’arrivo del messaggio deve essere molto breve.

* **Perché è importante?** In genere, un messaggio sulle transazioni ha tassi di apertura elevati. Dovrebbe quindi essere concepita con attenzione, in quanto può avere un forte impatto sul comportamento dei clienti in quanto definisce la relazione con essi.

* **Ad esempio?** Potrebbe trattarsi di un messaggio di benvenuto dopo la creazione di un account, di una conferma della spedizione di un ordine, di una fattura, di un messaggio di conferma di una modifica della password, di una notifica dopo che un cliente ha visitato il tuo sito Web, di una comunicazione di indisponibilità del prodotto, di un estratto conto, ecc.

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

Il processo generale di messaggistica transazionale può essere descritto come segue:

![](assets/transactional-msg-overview.png)

Ad esempio, immagina di essere un’azienda con un sito web in cui i clienti possono acquistare prodotti.

Adobe Campaign consente di inviare un’e-mail di notifica ai clienti che hanno aggiunto prodotti al carrello. Quando uno di loro lascia il sito web senza procedere con gli acquisti (evento esterno che attiva un evento Campaign), riceve automaticamente un’e-mail di abbandono del carrello (consegna di messaggi transazionali).

I passaggi principali per l&#39;implementazione sono descritti di seguito in [questa sezione](#key-steps).

>[!NOTE]
>
>Adobe Campaign dà priorità all’elaborazione dei messaggi transazionali rispetto a qualsiasi altra consegna.

## Passaggi chiave {#key-steps}

Di seguito sono riepilogati i passaggi principali per la creazione e la gestione di messaggi transazionali personalizzati in Adobe Campaign.

### Passaggi da eseguire sull’istanza di controllo

Nell&#39;**istanza di controllo** è necessario eseguire le azioni seguenti:

1. [Crea un tipo di evento](../../message-center/using/creating-event-types.md).
1. [Creare e progettare il modello di messaggio](../../message-center/using/creating-the-message-template.md). Collega un evento al messaggio durante questo passaggio.
1. [Verifica il messaggio](../../message-center/using/testing-message-templates.md).
1. [Publish il modello di messaggio](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>Tutti i passaggi precedenti vengono eseguiti sull&#39;**istanza di controllo**. La pubblicazione del modello nell&#39;istanza di controllo lo pubblicherà anche in tutte le **istanze di esecuzione**. Per ulteriori informazioni sulle istanze di messaggistica transazionale, consulta [Architettura della messaggistica transazionale](../../message-center/using/transactional-messaging-architecture.md).

### Elaborazione degli eventi nell’istanza di esecuzione

Dopo aver progettato e pubblicato il modello di messaggio transazionale, se viene attivato un evento corrispondente, i passaggi principali seguenti vengono eseguiti sull&#39;**istanza di esecuzione**:

1. Quando l&#39;evento viene generato dal sistema di informazioni esterno, i dati rilevanti vengono inviati a Campaign tramite i metodi **PushEvent** e **PushEvents**. Vedi [Raccolta eventi](../../message-center/using/about-event-processing.md#event-collection).
1. L’evento è collegato al modello di messaggio appropriato. Vedi [Instradamento verso un modello](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. Una volta completata la fase di arricchimento, la consegna viene inviata. Vedi [Esecuzione della consegna](../../message-center/using/delivery-execution.md). Ogni destinatario riceve un messaggio personalizzato.

## Argomenti correlati {#related-topics}

* [Introduzione ai canali di comunicazione](../../delivery/using/communication-channels.md)
* [Passaggi chiave per la creazione della consegna](../../delivery/using/steps-about-delivery-creation-steps.md)
* [Architettura della messaggistica transazionale](../../message-center/using/transactional-messaging-architecture.md)
* [Accedere ai rapporti di messaggistica transazionale](../../message-center/using/about-transactional-messaging-reports.md)
