---
solution: Campaign Standard
product: campaign
title: Best practice di importazione ed esportazione
description: Ulteriori informazioni sulle procedure ottimali da seguire per l'importazione o l'esportazione dei dati.
audience: automating
content-type: reference
topic-tags: workflow-general-operation
translation-type: tm+mt
source-git-commit: a2a99135bdd74d87c04262b53e074b6aa05e7915
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# Best practice di importazione ed esportazione {#import-export-best-practices}

Essere cauti e seguire le poche semplici regole descritte di seguito aiuterà molto a garantire la coerenza dei dati all&#39;interno del database e ad evitare errori comuni durante l&#39;aggiornamento del database o le esportazioni di dati.

## Utilizzo dei modelli di workflow {#using-import-templates}

La maggior parte dei flussi di lavoro finalizzati all&#39;importazione di dati deve contenere le seguenti attività: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

L&#39;utilizzo di modelli di workflow semplifica notevolmente la preparazione di importazioni simili e la coerenza dei dati all&#39;interno del database.

In molti progetti, le importazioni vengono create senza l&#39;attività **[!UICONTROL Deduplication]** perché i file utilizzati nel progetto non hanno duplicati. Talvolta i duplicati vengono visualizzati durante l’importazione di file diversi. La deduplicazione è quindi difficile. Pertanto, un passaggio di deduplicazione è una buona precauzione in tutti i flussi di lavoro di importazione.

Non devi basarsi sul presupposto che i dati in arrivo siano coerenti e corretti, o che il reparto IT o  supervisore Adobe Campaign se ne occuperà. Durante il progetto, tenere presente la pulizia dei dati. Deduplicare, riconciliare e mantenere la coerenza quando si importano i dati.

Un esempio di modello di flusso di lavoro generico progettato per l&#39;importazione di dati è disponibile nell&#39; [Esempio: Modello di flusso di lavoro per importare i dati](../../platform/using/creating-import-export-templates.md).

## Uso dei formati di file semplici {#using-flat-file-formats}

Il formato più efficiente per le importazioni è rappresentato dai file semplici. I file flat possono essere importati in modalità collettiva a livello di database.

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

## Utilizzo della compressione {#using-compression}

Quando possibile, usate file ZIP per le importazioni e le esportazioni. GZIP è supportato per impostazione predefinita. Durante l&#39;estrazione dei dati è possibile aggiungere la pre-elaborazione durante l&#39;importazione di file o la post-elaborazione, rispettivamente nelle attività dei flussi di lavoro **[!UICONTROL Load file]** e **[!UICONTROL Extract file]**.

**Argomenti correlati:**

* [Attività di caricamento dei dati (file)](../../workflow/using/data-loading--file-.md)
* [Attività di estrazione dei dati (file)](../../workflow/using/extraction--file-.md)

## Importazione in modalità Delta {#importing-in-delta-mode}

Le importazioni regolari devono essere effettuate in modalità delta. Ciò significa che solo i dati nuovi o modificati vengono inviati a  Adobe Campaign, invece che l&#39;intera tabella ogni volta.

Le importazioni complete devono essere utilizzate solo per il carico iniziale.

## Mantenimento della coerenza {#maintaining-consistency}

Per mantenere la coerenza dei dati nel database Adobe Campaign , attenersi ai principi seguenti:

* Se i dati importati corrispondono a una tabella di riferimento in  Adobe Campaign, è necessario riconciliarla con tale tabella nel flusso di lavoro. I record che non corrispondono devono essere rifiutati.
* Assicurarsi che i dati importati siano sempre **&quot;normalizzati&quot;** (indirizzo e-mail, numero di telefono, indirizzo di posta diretta) e che la normalizzazione sia affidabile e non cambi nel corso degli anni. In caso contrario, è probabile che nel database vengano visualizzati dei duplicati, e poiché  Adobe Campaign non fornisce strumenti per effettuare la corrispondenza &quot;fuzzy&quot;, sarà molto difficile gestirli e rimuoverli.
* I dati transazionali devono avere una chiave di riconciliazione e devono essere riconciliati con i dati esistenti al fine di evitare la creazione di duplicati.
* **Importa i file correlati in ordine**. Se l’importazione è composta da più file che dipendono l’uno dall’altro, il flusso di lavoro deve verificare che i file vengano importati nell’ordine corretto. Quando un file ha esito negativo, gli altri file non vengono importati.
* **Deduplicare**, riconciliare e mantenere la coerenza quando si importano i dati.
