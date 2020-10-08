---
title: Informazioni su Adobe Experience Manager
seo-title: Informazioni su Adobe Experience Manager
description: Informazioni su Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 1%

---


# Informazioni su Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] è un&#39;integrazione tra  Adobe Campaign e  Adobe Analytics mediante la pipeline. La pipeline recupera le azioni o gli attivatori degli utenti dal sito Web. Un abbandono del carrello è un esempio di trigger. Gli attivatori vengono elaborati in  Adobe Campaign per inviare e-mail in tempo quasi reale.

[!DNL Triggers] eseguire azioni di marketing entro un breve intervallo di tempo a seguito dell&#39;azione di un utente. Il tempo di risposta tipico è inferiore a un&#39;ora.

Consente integrazioni più agili, poiché la configurazione è minima e non coinvolge una terza parte.
Supporta inoltre volumi elevati di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l&#39;integrazione può elaborare un milione di attivatori all&#39;ora.

## [!DNL Triggers] architettura {#triggers-architecture}

### Cos&#39;è Pipeline? {#pipeline-explanation}

>[!CAUTION]
>
>Solo  soluzioni Adobe Cloud possono produrre e utilizzare eventi dai servizi pipeline  Adobe. I sistemi esterni  Adobe non possono.

Pipeline è un sistema di messaggistica ospitato nel Experience Cloud  che utilizza [Apache Kafka](http://kafka.apache.org/). È un modo per trasmettere facilmente i dati tra le soluzioni. Inoltre, Pipeline è una coda di messaggi anziché un database. I produttori spingono gli eventi in preparazione e i consumatori ascoltano il flusso e fanno ciò che vogliono con l&#39;evento. Gli eventi vengono conservati per alcuni giorni, ma non più. Lo scopo è quello di ascoltare 24 ore su 24, 7 giorni su 7 e di elaborare gli eventi immediatamente.

![](assets/triggers_1.png)

### Come funziona Pipeline? {#how-pipeline-work}

Il [!DNL pipelined] processo è sempre in esecuzione sul server di marketing Adobe Campaign . Si collega alla pipeline, recupera gli eventi e li elabora immediatamente.

![](assets/triggers_2.png)

Il [!DNL pipelined] processo accede al Experience Cloud  utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l&#39;autenticazione al momento del recupero degli eventi. [!DNL Triggers] vengono recuperati da un servizio Web REST utilizzando una semplice richiesta di GET. La risposta è in formato JSON. I parametri della richiesta includono il nome dell&#39;attivatore e un puntatore che indica l&#39;ultimo messaggio recuperato. Il [!DNL pipelined] processo lo gestisce automaticamente.

## Utilizzo dell&#39;integrazione di Adobe Experience Cloud Triggers con Adobe Campaign Classic

Di seguito sono riportate alcune [!DNL Triggers] best practice:

* I [!DNL Trigger] dati devono essere memorizzati nel momento in cui sono inclusi in Campaign. Non deve essere elaborato direttamente in quanto creerebbe latenza.
* La marca temporale deve essere controllata dal messaggio e non dalla base dati.
* Utilizzare TriggerTimestamp e Trigger ID per rimuovere i duplicati.

>[!CAUTION]
>
>L&#39;esempio seguente non è fornito out-of-box. Questo è un esempio specifico tratto da diverse possibili implementazioni.

Gli eventi della pipeline vengono scaricati automaticamente. Questi eventi possono essere monitorati utilizzando un modulo.

![](assets/triggers_3.png)

Il nodo Evento pipeline non è integrato e deve essere aggiunto, così come il modulo correlato deve essere creato in Campaign. Queste operazioni sono riservate solo agli utenti esperti. Per ulteriori informazioni, consulta le sezioni seguenti: [Gerarchia](../../configuration/using/about-navigation-hierarchy.md) di navigazione e [modifica dei moduli](../../configuration/using/editing-forms.md).

Un flusso di lavoro di campagna periodico esegue query sugli attivatori e, se corrispondono ai criteri di marketing, avvia una consegna.

![](assets/triggers_4.png)
