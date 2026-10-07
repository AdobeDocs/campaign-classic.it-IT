---
product: campaign
title: Problemi dei registri di tracciamento
description: Problemi dei registri di tracciamento
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: 'https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '81'
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
