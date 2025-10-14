---
product: campaign
title: Best practice per l’importazione e l’esportazione
description: Scopri le best practice da seguire per importare o esportare dati
feature: Data Management
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 2%

---

# Best practice per l’importazione e l’esportazione {#import-export-best-practices}



Prestare attenzione e seguire le poche e semplici regole descritte di seguito aiuterà a garantire la coerenza dei dati all’interno del database e a evitare errori comuni durante l’aggiornamento del database o le esportazioni di dati.

## Utilizzo dei modelli di flusso di lavoro {#using-import-templates}

La maggior parte dei flussi di lavoro destinati all&#39;importazione di dati deve contenere le attività seguenti: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

L’utilizzo dei modelli di flusso di lavoro rende molto utile preparare importazioni simili e garantire la coerenza dei dati all’interno del database.

In molti progetti, le importazioni vengono create senza l&#39;attività **[!UICONTROL Deduplication]** perché i file utilizzati nel progetto non contengono duplicati. I duplicati vengono talvolta visualizzati quando si importano file diversi. La deduplicazione è quindi difficile. Pertanto, un passaggio di deduplicazione è una buona precauzione in tutti i flussi di lavoro di importazione.

Non partire dal presupposto che i dati in arrivo siano coerenti e corretti o che il reparto IT o il supervisore Adobe Campaign se ne occuperanno. Durante il progetto, tieni presente la pulizia dei dati. Deduplicare, riconciliare e mantenere la coerenza durante l&#39;importazione dei dati.

Un esempio di modello di flusso di lavoro generico progettato per l&#39;importazione di dati è disponibile nella sezione [Esempio: modello di flusso di lavoro per l&#39;importazione di dati](../../platform/using/creating-import-export-templates.md).

## Usa formati di file flat {#using-flat-file-formats}

Il formato più efficiente per le importazioni è costituito dai file flat. I file Flat possono essere importati in modalità collettiva a livello di database.

Ad esempio:

* Separatore: tabulazione o punto e virgola
* Prima riga con intestazioni
* Nessun delimitatore di stringa
* Formato data: `YYYY/MM/DD HH:mm:SS`

Esempio di file da importare:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Usa compressione {#using-compression}

Se possibile, utilizzate file compressi per le importazioni e le esportazioni. GZIP è supportato per impostazione predefinita. È possibile aggiungere la pre-elaborazione durante l&#39;importazione di file o la post-elaborazione durante l&#39;estrazione dei dati, rispettivamente, nelle attività del flusso di lavoro **[!UICONTROL Load file]** e **[!UICONTROL Extract file]**.

**Argomenti correlati:**

* [Attività caricamento dati (file)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html?lang=it){target="_blank"}
* [Attività di estrazione dati (file)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=it){target="_blank"}.

## Importa in modalità Delta {#importing-in-delta-mode}

Le importazioni regolari devono essere effettuate in modalità delta. Significa che ad Adobe Campaign vengono inviati solo dati nuovi o modificati, invece che l’intera tabella ogni volta.

Le importazioni complete devono essere utilizzate solo per il carico iniziale.

## Mantieni coerenza {#maintaining-consistency}

Per mantenere la coerenza dei dati nel database di Adobe Campaign, segui i principi riportati di seguito:

* Se i dati importati corrispondono a una tabella di riferimento in Adobe Campaign, devono essere riconciliati con tale tabella nel flusso di lavoro. I record che non corrispondono devono essere rifiutati.
* Verificare che i dati importati siano sempre **&quot;normalizzati&quot;** (e-mail, numero di telefono, indirizzo di direct mailing) e che questa normalizzazione sia affidabile e che non cambi nel corso degli anni. In caso contrario, è probabile che alcuni duplicati vengano visualizzati nel database e, poiché Adobe Campaign non fornisce strumenti per effettuare una corrispondenza &quot;fuzzy&quot;, sarà molto difficile gestirli e rimuoverli.
* I dati transazionali devono avere una chiave di riconciliazione ed essere riconciliati con i dati esistenti al fine di evitare la creazione di duplicati.
* **Importa i file correlati nell&#39;ordine**. Se l’importazione è composta da più file che dipendono l’uno dall’altro, il flusso di lavoro deve assicurarsi che i file vengano importati nell’ordine corretto. Quando un file ha esito negativo, gli altri file non vengono importati.
* **Deduplicare**, riconciliare e mantenere la coerenza durante l&#39;importazione dei dati.
