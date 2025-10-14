---
product: campaign
title: Problemi dei registri di tracciamento
description: Problemi dei registri di tracciamento
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 14%

---

# Problemi dei registri di tracciamento{#tracking-logs-issues}



Ci possono essere diversi motivi per cui i registri di tracciamento non vengono inoltrati. Si consiglia di controllare le seguenti informazioni:

* **Il flusso di lavoro** Rilevamento **contiene errori?**

Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=it){target="_blank"}.

![](assets/tracking_scheduled_task.png)

* **Il modulo** trackinglogd **è in esecuzione sul server?**

  Consulta [File di registro](../../production/using/log-files.md).

* **Sono state apportate modifiche?**

  Possono attivare una perdita di connessione ai server utilizzando l’alias di tracciamento.
