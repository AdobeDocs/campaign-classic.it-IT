---
solution: Campaign Classic
product: campaign
title: Importazione ed esportazione di dati tramite flussi di lavoro
description: Scopri come importare ed esportare dati utilizzando i flussi di lavoro in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---


# Importazione ed esportazione di dati tramite flussi di lavoro {#import-export-workflows}

## Raccolta di dati {#collecting-data-workflows}

I flussi di lavoro possono essere un modo utile per automatizzare alcuni dei processi di importazione. Sia che importi dati da un file locale o da un SFTP, puoi utilizzare i flussi di lavoro per standardizzare le procedure di gestione dei dati.

### Utilizzo dei dati di un elenco: Elenco di lettura {#using-data-from-a-list--read-list}

I dati inviati in un flusso di lavoro possono provenire da elenchi in cui i dati sono stati preparati e strutturati in anticipo.

Questo elenco potrebbe essere stato creato direttamente in  Adobe Campaign o importato dall&#39;opzione **[!UICONTROL Import a list]**. Per ulteriori informazioni su questa opzione, fare riferimento a [page](../../platform/using/about-generic-imports-exports.md).

Per ulteriori informazioni sull&#39;utilizzo dell&#39;attività dell&#39;elenco di lettura in un flusso di lavoro, vedere [questa pagina](../../workflow/using/read-list.md).

### Caricamento di dati da un file {#loading-data-from-a-file}

I dati elaborati in un flusso di lavoro possono essere estratti da un file strutturato in modo che possano essere importati in  Adobe Campaign.

Una descrizione dell&#39;attività di caricamento dei dati è disponibile nella sezione [Caricamento dei dati (file)](../../workflow/using/data-loading--file-.md).

Esempio di file strutturato da importare:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Una volta raccolti i dati, puoi usarli nei tuoi flussi di lavoro, ad esempio per arricchire la consegna o aggiornare il database. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/how-to-use-workflow-data.md).

## Esportazione di dati {#exporting-data-via-a-workflow}

I flussi di lavoro possono essere un modo utile per automatizzare alcuni dei processi di esportazione o per esportare insiemi precisi di dati dopo aver utilizzato alcune delle attività di gestione dei dati disponibili per trasformare i dati.

Le operazioni di esportazione vengono eseguite utilizzando un **[!UICONTROL Data extraction (file) activity]**. Per ulteriori informazioni su come configurare e utilizzare l&#39;attività, fare riferimento a [questa pagina](../../workflow/using/extraction--file-.md).
