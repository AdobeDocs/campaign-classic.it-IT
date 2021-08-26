---
product: campaign
title: Best practice per l’importazione e l’esportazione
description: Ulteriori informazioni sulle best practice da seguire per l’importazione o l’esportazione di dati.
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 2%

---

# Best practice per l’importazione e l’esportazione {#import-export-best-practices}

![](../../assets/common.svg)

La cautela e il rispetto delle poche semplici regole descritte di seguito aiuteranno molto a garantire la coerenza dei dati all&#39;interno del database e ad evitare errori comuni durante l&#39;aggiornamento del database o le esportazioni di dati.

## Utilizzo dei modelli di flusso di lavoro {#using-import-templates}

La maggior parte dei flussi di lavoro destinati all’importazione di dati deve contenere le seguenti attività: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

L’utilizzo di modelli di flusso di lavoro rende molto comodo preparare importazioni simili e garantire la coerenza dei dati all’interno del database.

In molti progetti, le importazioni vengono generate senza **[!UICONTROL Deduplication]** attività perché i file utilizzati nel progetto non contengono duplicati. Talvolta i duplicati vengono visualizzati dall’importazione di file diversi. La deduplicazione è quindi difficile. Pertanto, un passaggio di deduplicazione è una buona precauzione in tutti i flussi di lavoro di importazione.

Non basarsi sul presupposto che i dati in arrivo siano coerenti e corretti o che il reparto IT o il supervisore di Adobe Campaign se ne occuperà. Durante il progetto, tenere a mente la pulizia dei dati. Deduplica, riconcilia e mantieni la coerenza quando importi i dati.

Un esempio di modello di flusso di lavoro generico progettato per l’importazione di dati è disponibile nell’ [Esempio: Modello di flusso di lavoro per importare la sezione dati](../../platform/using/creating-import-export-templates.md) .

## Utilizzare formati di file flat {#using-flat-file-formats}

Il formato più efficiente per le importazioni è quello dei file piatti. I file Flat possono essere importati in modalità collettiva a livello di database.

Ad esempio:

* Separatore: tabulazione o punto e virgola
* Prima riga con intestazioni
* Nessun delimitatore di stringa
* Formato data: AAAA/MM/GG HH:mm:SS

Esempio di file da importare:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Usa compressione {#using-compression}

Se possibile, utilizza i file compressi per le importazioni e le esportazioni. GZIP è supportato per impostazione predefinita. Puoi aggiungere la pre-elaborazione durante l’importazione di file o la post-elaborazione durante l’estrazione dei dati, rispettivamente nelle attività del flusso di lavoro **[!UICONTROL Load file]** e **[!UICONTROL Extract file]** .

**Argomenti correlati:**

* [Attività di caricamento dei dati (file)](../../workflow/using/data-loading--file-.md)
* [Attività di estrazione dati (file)](../../workflow/using/extraction--file-.md)

## Importazione in modalità Delta {#importing-in-delta-mode}

Le importazioni regolari devono essere effettuate in modalità delta. Significa che solo i dati nuovi o modificati vengono inviati ad Adobe Campaign, invece che l’intera tabella ogni volta.

Le importazioni complete devono essere utilizzate solo per il carico iniziale.

## Gestisci coerenza {#maintaining-consistency}

Per mantenere la coerenza dei dati nel database Adobe Campaign, segui i principi seguenti:

* Se i dati importati corrispondono a una tabella di riferimento in Adobe Campaign, è necessario riconciliarla con tale tabella nel flusso di lavoro. I record che non corrispondono devono essere rifiutati.
* Assicurati che i dati importati siano sempre **&quot;normalizzati&quot;** (e-mail, numero di telefono, indirizzo direct mail) e che questa normalizzazione sia affidabile e non cambierà nel corso degli anni. In caso contrario, è probabile che alcuni duplicati vengano visualizzati nel database e, poiché Adobe Campaign non fornisce strumenti per eseguire la corrispondenza &quot;sfocata&quot;, sarà molto difficile gestirli e rimuoverli.
* Per evitare la creazione di duplicati, i dati transazionali devono avere una chiave di riconciliazione e devono essere riconciliati con i dati esistenti.
* **Importa i file correlati in ordine**. Se l’importazione è composta da più file che dipendono l’uno dall’altro, il flusso di lavoro deve assicurarsi che i file siano importati nell’ordine corretto. Quando un file non riesce, gli altri file non vengono importati.
* **Deduplica**, riconcilia e mantieni la coerenza quando importi i dati.
