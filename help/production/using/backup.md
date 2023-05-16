---
product: campaign
title: Backup
description: Backup
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Backup{#backup}

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o relativi al sistema) su una macchina.

I dati vengono memorizzati in due posizioni distinte:

* i file fisici sono memorizzati nelle directory Adobe Campaign,
* altri dati vengono memorizzati nel database.

La maggior parte dei dati si trova nel database. Ciò rappresenta il 99% delle informazioni da sottoporre a backup.

## File fisici {#physical-files}

I file sono suddivisi in diverse categorie:

* File di configurazione, memorizzati in **nl6/conf**, ti consente di riconfigurare Adobe Campaign molto rapidamente.

* File di reindirizzamento, memorizzati in  **nl6/var/`<instance-name>`/redir**, sono presenti sui server di tracciamento (spesso denominati &quot;frontali&quot;) e includono tutti i reindirizzamenti precedenti delle campagne. Vengono ancora utilizzati dalle campagne precedenti.

* File di registro, memorizzati in **nl6/var/`<instance-name>`/log**, può essere utilizzato per individuare i problemi.

Le directory da sottoporre a backup sono pertanto:

* nl6/conf

* nl6/var/`<instance-name>`/redir (per ogni istanza)

* nl6/var/`<instance-name>`/log (facoltativo)

* nl6/var/`<instance-name>`/relay (facoltativo)


## Database {#database}

>[!IMPORTANT]
>
>È fondamentale eseguire il backup del database.


Il database contiene tutte le informazioni visualizzate nella console client avanzata di Adobe Campaign, nonché tutti i dati della linea di business.

Questa operazione è affidata alla tua società di hosting e ai relativi amministratori di database in particolare.
