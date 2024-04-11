---
product: campaign
title: Architettura
description: I flussi di lavoro sono gestiti da un modulo specifico, che può essere avviato su più server per condividere il carico di elaborazione
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# Architettura {#architecture}



I flussi di lavoro vengono gestiti da un modulo specifico. Questo modulo può essere avviato su più server per condividere il carico di elaborazione.

![](assets/architecture.png)

* Il processo &#39;Workflow Instance Runner&#39; (runwf) esegue tutte le attività di una determinata istanza del flusso di lavoro. Quando non ci sono attività da eseguire per il momento, diventa &quot;passivo&quot;, cioè salva il suo stato nel database, quindi si arresta.
* Il modulo &#39;Workflow Server&#39; (wfserver) monitora le istanze di flusso di lavoro correnti. Quando è presente un task da eseguire, questo modulo crea un processo per attivare (o riattivare) l’istanza corrispondente.
