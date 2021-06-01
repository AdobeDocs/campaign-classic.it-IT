---
product: campaign
title: Importazione ed esportazione di dati tramite flussi di lavoro
description: Scopri come importare ed esportare dati utilizzando i flussi di lavoro in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 5%

---

# Importare ed esportare dati utilizzando i flussi di lavoro {#import-export-workflows}

## Raccolta di dati {#collecting-data-workflows}

I flussi di lavoro possono essere un modo utile per automatizzare alcuni dei processi di importazione. Sia che importi dati da un file locale o da un SFTP, puoi utilizzare i flussi di lavoro per standardizzare le procedure di gestione dei dati.

### Utilizzare i dati di un elenco: Leggi l&#39;elenco {#using-data-from-a-list--read-list}

I dati inviati in un flusso di lavoro possono provenire da elenchi in cui i dati sono stati predisposti e strutturati.

Questo elenco potrebbe essere stato creato direttamente in Adobe Campaign o importato dall’opzione **[!UICONTROL Import a list]** . Per ulteriori informazioni su questa opzione, consulta questa [pagina](../../platform/using/about-generic-imports-exports.md).

Per ulteriori informazioni sull&#39;utilizzo dell&#39;attività di lettura dell&#39;elenco in un flusso di lavoro, consulta [questa pagina](../../workflow/using/read-list.md).

### Caricare dati da un file {#loading-data-from-a-file}

I dati elaborati in un flusso di lavoro possono essere estratti da un file strutturato in modo che possano essere importati in Adobe Campaign.

Una descrizione dell’attività di caricamento dei dati si trova nella sezione [Caricamento dati (file)](../../workflow/using/data-loading--file-.md) .

Esempio di file strutturato da importare:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Una volta raccolti i dati, puoi utilizzarli nei flussi di lavoro, ad esempio per arricchire una consegna o aggiornare il database. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/how-to-use-workflow-data.md).

## Esporta dati {#exporting-data-via-a-workflow}

I flussi di lavoro possono essere un modo utile per automatizzare alcuni dei processi di esportazione o per esportare set precisi di dati dopo aver utilizzato alcune delle attività di gestione dei dati disponibili per trasformare i dati.

Le operazioni di esportazione vengono eseguite utilizzando un **[!UICONTROL Data extraction (file) activity]**. Per ulteriori informazioni su come configurare e utilizzare l&#39;attività, consulta [questa pagina](../../workflow/using/extraction--file-.md).
