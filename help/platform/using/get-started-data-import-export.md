---
product: campaign
title: Introduzione all’importazione e l’esportazione dei dati
description: Ulteriori informazioni sull’importazione e l’esportazione di dati in Campaign
feature: Data Management, Encryption
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 10%

---

# Introduzione all’importazione e l’esportazione dei dati {#get-started-data-import-export}



Adobe Campaign Classic fornisce funzionalità di gestione dei dati che consentono di importare ed esportare dati. Queste operazioni possono essere eseguite utilizzando flussi di lavoro o importazioni ed esportazioni generiche.

>[!IMPORTANT]
>
>Tieni presente i limiti di archiviazione SFTP, archiviazione del database e profilo attivo in base al tuo contratto Adobe Campaign durante l’utilizzo di questa funzionalità.

## Flussi di lavoro {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**I flussi di lavoro** sono utili per automatizzare i processi di importazione. Che importi dati da un file locale o da un SFTP, ti consentono di standardizzare le procedure di gestione dei dati.

Con i flussi di lavoro, le operazioni di importazione ed esportazione possono essere ripetute automaticamente in base a una pianificazione, ad esempio per automatizzare lo scambio di dati tra diversi sistemi di informazione.

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/import-export-workflows.md).

## Importazioni ed esportazioni generiche {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Inoltre, Campaign Classic fornisce **importazioni ed esportazioni generiche** che consentono di creare processi di importazione o esportazione occasionali.

Le importazioni e le esportazioni vengono configurate in modelli dedicati, che è possibile configurare e utilizzare per avviare e monitorare i processi di importazione ed esportazione.

Per ulteriori informazioni sulle importazioni ed esportazioni generiche, consulta [questa sezione](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Le importazioni e le esportazioni generiche dovrebbero essere utilizzate solo per operazioni occasionali. Per garantire la coerenza dei dati e migliorare l’efficienza, si consiglia di eseguire le operazioni di importazione ed esportazione utilizzando i flussi di lavoro.

## Crittografia e compressione dei dati {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic consente di importare file compressi o crittografati ed esportare file compressi o crittografati.

Queste operazioni vengono eseguite all’interno dei flussi di lavoro, applicando fasi di pre-elaborazione ai dati che desideri sfruttare.

Per ulteriori informazioni, consulta queste sezioni:

* [Decomprimere o decrittografare un file](../../platform/using/unzip-decrypt.md)
* [Comprimere o crittografare un file](../../platform/using/zip-encrypt.md)

## Best practice e risoluzione dei problemi {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

È necessario seguire diverse [best practice](../../platform/using/import-export-best-practices.md) durante l&#39;esecuzione di operazioni di importazione ed esportazione per garantire la coerenza dei dati all&#39;interno del database ed evitare errori comuni durante le operazioni di aggiornamento o esportazione.

Inoltre, consigli e problemi comuni relativi all&#39;utilizzo dei server SFTP sono disponibili in [questa sezione](../../platform/using/sftp-server-usage.md).
