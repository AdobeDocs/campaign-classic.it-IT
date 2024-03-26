---
product: campaign
title: Problemi dei registri di tracciamento
description: Problemi dei registri di tracciamento
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 21%

---

# Problemi dei registri di tracciamento{#tracking-logs-issues}



Ci possono essere diversi motivi per cui i registri di tracciamento non vengono inoltrati. Si consiglia di controllare le seguenti informazioni:

* **L&#39;** Tracciamento **il flusso di lavoro presenta errori?**

  Fai riferimento a [Monitoraggio dei flussi di lavoro tecnici](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **è il modulo** trackinglogd **in esecuzione sul server?**

  Fai riferimento a [File di registro](../../production/using/log-files.md).

* **Sono state apportate modifiche?**

  Possono attivare una perdita di connessione ai server utilizzando l’alias di tracciamento.
