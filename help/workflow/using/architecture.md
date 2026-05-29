---
product: campaign
title: Architettura
description: I flussi di lavoro sono gestiti da un modulo specifico, che può essere avviato su più server per condividere il carico di elaborazione
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 116
ht-degree: 1%

---

# Architettura {#architecture}



I flussi di lavoro vengono gestiti da un modulo specifico. Questo modulo può essere avviato su più server per condividere il carico di elaborazione.

![](assets/architecture.png)

* Il processo &#39;Workflow Instance Runner&#39; (runwf) esegue tutte le attività di una determinata istanza del flusso di lavoro. Quando non ci sono attività da eseguire per il momento, diventa &quot;passivo&quot;, cioè salva il suo stato nel database, quindi si arresta.
* Il modulo &#39;Workflow Server&#39; (wfserver) monitora le istanze di flusso di lavoro correnti. Quando è presente un task da eseguire, questo modulo crea un processo per attivare (o riattivare) l’istanza corrispondente.
