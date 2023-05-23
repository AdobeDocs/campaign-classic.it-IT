---
product: campaign
title: Backup
description: Backup
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# Backup{#backup}

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o di sistema) su una macchina.

I dati vengono memorizzati in due posizioni separate:

* i file fisici vengono memorizzati nelle directory di Adobe Campaign,
* altri dati vengono memorizzati nel database.

La maggior parte dei dati si trova nel database. Ciò rappresenta il 99% delle informazioni di cui eseguire il backup.

## File fisici {#physical-files}

I file sono suddivisi in diverse categorie:

* File di configurazione, archiviati in **nl6/conf**, consente di riconfigurare Adobe Campaign molto rapidamente.

* File di reindirizzamento, archiviati in  **nl6/var/`<instance-name>`/redir**, si trovano sui server di tracciamento (spesso denominati &quot;frontali&quot;) e includono tutti i reindirizzamenti precedenti delle campagne. Vengono ancora utilizzati nelle campagne precedenti.

* File di registro, archiviati in **nl6/var/`<instance-name>`/log**, può essere utilizzato per tracciare i problemi.

Le directory di cui eseguire il backup sono pertanto le seguenti:

* nl6/conf

* nl6/var/`<instance-name>`/redir (per ogni istanza)

* nl6/var/`<instance-name>`/log (facoltativo)

* nl6/var/`<instance-name>`/relay (facoltativo)


## Database {#database}

>[!IMPORTANT]
>
>È fondamentale eseguire il backup del database.


Il database contiene tutte le informazioni visualizzate nella console rich client di Adobe Campaign, nonché tutti i dati line-of-business.

La società di hosting, e in particolare i relativi amministratori di database, sono responsabili di questa operazione.
