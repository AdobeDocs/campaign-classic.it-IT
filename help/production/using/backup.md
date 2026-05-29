---
product: campaign
title: Backup
description: Backup
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
TQID: https://experienceleague.adobe.com/ZCExecNbs9DnWVoQLpvzlrH7k2eGhBNq7pEiybyQdi4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 232
ht-degree: 9%

---

# Backup{#backup}

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o di sistema) su una macchina.

I dati vengono memorizzati in due posizioni separate:

* i file fisici vengono memorizzati nelle directory di Adobe Campaign,
* altri dati vengono memorizzati nel database.

La maggior parte dei dati si trova nel database. Ciò rappresenta il 99% delle informazioni di cui eseguire il backup.

## File fisici {#physical-files}

I file sono suddivisi in diverse categorie:

* I file di configurazione, archiviati in **nl6/conf**, consentono di riconfigurare Adobe Campaign molto rapidamente.

* I file di reindirizzamento, archiviati in **nl6/var/`<instance-name>`/redir**, si trovano sui server di tracciamento (spesso denominati &quot;frontali&quot;) e includono tutti i reindirizzamenti di campagne precedenti. Vengono ancora utilizzati nelle campagne precedenti.

* I file di registro, archiviati in **nl6/var/`<instance-name>`/log**, possono essere utilizzati per tracciare i problemi.

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
