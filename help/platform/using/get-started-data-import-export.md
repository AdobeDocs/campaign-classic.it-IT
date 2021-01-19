---
solution: Campaign Classic
product: campaign
title: Introduzione all'importazione e all'esportazione dei dati
description: Ulteriori informazioni sull'importazione e l'esportazione di dati in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 6%

---


# Introduzione all&#39;importazione e all&#39;esportazione di dati {#get-started-data-import-export}

Adobe Campaign Classic offre funzionalità di gestione dei dati che consentono di importare ed esportare i dati. Queste operazioni possono essere eseguite tramite flussi di lavoro o importazioni ed esportazioni generiche.

>[!IMPORTANT]
>
>Ricorda i limiti di archiviazione SFTP, archiviazione del database e profilo attivo come previsto dal tuo contratto Adobe Campaign  durante l&#39;utilizzo di questa funzionalità.

## Flussi di lavoro {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**I** flussi di lavoro sono un modo utile per automatizzare i processi di importazione. Sia che importi dati da un file locale o da un SFTP, questi consentono di standardizzare le procedure di gestione dei dati.

Con i flussi di lavoro, le operazioni di importazione ed esportazione possono essere ripetute automaticamente secondo una pianificazione, ad esempio per automatizzare lo scambio di dati tra diversi sistemi informativi.

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/import-export-workflows.md).

## Importazioni ed esportazioni generiche {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Inoltre, Campaign Classic fornisce **importazioni ed esportazioni generiche** che consentono di creare processi occasionali di importazione o esportazione.

Le importazioni e le esportazioni sono configurate in modelli dedicati, che potete configurare e utilizzare per avviare e monitorare i processi di importazione ed esportazione.

Per ulteriori informazioni sulle importazioni e le esportazioni generiche, consultare [questa sezione](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Le importazioni e le esportazioni generiche devono essere utilizzate solo per operazioni occasionali. Per garantire la coerenza dei dati e migliorare l&#39;efficienza, si consiglia di eseguire le operazioni di importazione ed esportazione tramite flussi di lavoro.

## Cifratura dei dati e compressione {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic consente di importare file compressi o crittografati ed esportare file compressi o crittografati.

Queste operazioni vengono eseguite all&#39;interno dei flussi di lavoro, applicando le fasi di pre-elaborazione ai dati che si desidera sfruttare.

Per ulteriori informazioni, consulta queste sezioni:

* [Decrittografare o decomprimere un file](../../platform/using/unzip-decrypt.md)
* [Zipping o cifratura di un file](../../platform/using/zip-encrypt.md)

## Procedure ottimali e risoluzione dei problemi {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Durante le operazioni di importazione ed esportazione, è necessario seguire diverse procedure [best practice](../../platform/using/import-export-best-practices.md) per garantire la coerenza dei dati all&#39;interno del database ed evitare errori comuni durante l&#39;aggiornamento o l&#39;esportazione.

Inoltre, raccomandazioni e problemi comuni relativi all&#39;utilizzo dei server SFTP sono disponibili in [questa sezione](../../platform/using/sftp-server-usage.md).
