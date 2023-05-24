---
product: campaign
title: Problemi dei registri di tracciamento
description: Problemi dei registri di tracciamento
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

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
