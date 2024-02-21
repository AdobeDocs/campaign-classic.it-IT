---
product: campaign
title: Importazione ed esportazione di dati tramite flussi di lavoro
description: Scopri come importare ed esportare dati utilizzando i flussi di lavoro in Campaign
feature: Data Management, Workflows
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 3%

---

# Importare ed esportare dati tramite flussi di lavoro {#import-export-workflows}



## Raccolta dei dati {#collecting-data-workflows}

I flussi di lavoro possono essere utili per automatizzare alcuni dei processi di importazione. Che tu importi dati da un file locale o da un SFTP, puoi utilizzare i flussi di lavoro per standardizzare le procedure di gestione dei dati.

### Utilizza dati da un elenco: Leggi elenco {#using-data-from-a-list--read-list}

I dati inviati in un flusso di lavoro possono provenire da elenchi in cui i dati sono stati preparati e strutturati in precedenza.

Questo elenco potrebbe essere stato creato direttamente in Adobe Campaign o importato da **[!UICONTROL Import a list]** opzione. Per ulteriori informazioni su questa opzione, consulta questa [pagina](../../platform/using/about-generic-imports-exports.md).

Per ulteriori informazioni sull’utilizzo dell’attività di lettura elenco in un flusso di lavoro, consulta [questa pagina](../../workflow/using/read-list.md).

### Caricare dati da un file {#loading-data-from-a-file}

I dati elaborati in un flusso di lavoro possono essere estratti da un file strutturato in modo che possa essere importato in Adobe Campaign.

Una descrizione dell’attività di caricamento dei dati si trova nella sezione [Caricamento dati (file)](../../workflow/using/data-loading-file.md) sezione.

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

I flussi di lavoro possono essere utili per automatizzare alcuni dei processi di esportazione o per esportare set di dati precisi dopo aver utilizzato alcune delle attività di gestione dati disponibili per trasformare i dati.

Le operazioni di esportazione vengono eseguite utilizzando **[!UICONTROL Data extraction (file) activity]**. Per ulteriori informazioni su come configurare e utilizzare l’attività, consulta [questa pagina](../../workflow/using/extraction-file.md).
