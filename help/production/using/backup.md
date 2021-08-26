---
product: campaign
title: Backup
description: Backup
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# Backup{#backup}

![](../../assets/v7-only.svg)

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o relativi al sistema) su una macchina.

I dati vengono memorizzati in due posizioni distinte:

* i file fisici sono memorizzati nelle directory Adobe Campaign,
* altri dati vengono memorizzati nel database.

La maggior parte dei dati si trova nel database. Ciò rappresenta il 99% delle informazioni da sottoporre a backup.

## File fisici {#physical-files}

I file sono suddivisi in diverse categorie:

* File di configurazione, che si trovano in **nl6/conf**

   Questi consentono di riconfigurare Adobe Campaign molto rapidamente.

* File di reindirizzamento ** nl6/var/`<instancename>`/redir**

   Si tratta dei server di tracciamento (spesso denominati &quot;frontali&quot;) e includono tutti i reindirizzamenti precedenti alle campagne. Vengono ancora utilizzati dalle campagne precedenti.

* File di registro: **nl6/var/`<instancename>`/log**

   Questi possono essere utilizzati per tracciare i problemi.

Le directory da sottoporre a backup sono pertanto:

* nl6/conf

* nl6/var/`<instanceName>`/redir (per ogni istanza)

* nl6/var/`<instanceName>`/log (facoltativo)

* nl6/var/`<instanceName>`/relay (facoltativo)

>[!IMPORTANT]
>
>È essenziale eseguire il backup del database.

## Database {#database}

Il database contiene tutte le informazioni visualizzate nella console client avanzata di Adobe Campaign, nonché tutti i dati della linea di business.

Questa operazione è affidata alla tua società di hosting e ai relativi amministratori di database in particolare.
