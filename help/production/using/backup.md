---
title: Backup
seo-title: Backup
description: Backup
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---


# Backup{#backup}

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o legati al sistema) su una macchina.

I dati vengono memorizzati in due posizioni distinte:

* i file fisici sono memorizzati nelle directory Adobe Campaign ,
* altri dati sono memorizzati nel database.

La maggior parte dei dati si trova nel database. Rappresenta il 99% delle informazioni di cui eseguire il backup.

## File fisici {#physical-files}

I file sono suddivisi in diverse categorie:

* File di configurazione, che si trovano in **nl6/conf**

   Questi consentono di riconfigurare  Adobe Campaign molto rapidamente.

* File di reindirizzamento ** nl6/var/`<instancename>`/redir**

   Questi sono presenti sui server di tracciamento (spesso denominati &quot;frontali&quot;) e includono tutte le reindirizzamenti precedenti alle campagne. Vengono ancora utilizzati dalle campagne precedenti.

* File di registro: **nl6/var/`<instancename>`/log**

   Questi possono essere utilizzati per individuare i problemi.

Gli elenchi da sottoporre a backup sono pertanto:

* nl6/conf

* nl6/var/`<instanceName>`/redir (per ciascuna istanza)

* nl6/var/`<instanceName>`/log (facoltativo)

* nl6/var/`<instanceName>`/relay (facoltativo)

>[!CAUTION]
>
>È essenziale eseguire il backup del database.

## Database {#database}

Il database contiene tutte le informazioni visualizzate nella console client Adobe Campaign avanzata , nonché tutti i dati della linea di business.

La società di hosting e in particolare gli amministratori del database sono responsabili di questa operazione.
