---
product: campaign
title: Problemi dei registri di tracciamento
description: Problemi dei registri di tracciamento
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 24%

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
