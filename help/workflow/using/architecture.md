---
solution: Campaign Classic
product: campaign
title: Architettura
description: I flussi di lavoro sono gestiti da un modulo specifico, che può essere avviato su più server per condividere il carico di elaborazione.
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# Architettura {#architecture}

I flussi di lavoro vengono gestiti da un modulo specifico. Questo modulo può essere avviato su più server per condividere il carico di elaborazione.

![](assets/architecture.png)

* Il processo &#39;Workflow Instance Runner&#39; (runwf) esegue tutte le attività di una determinata istanza del flusso di lavoro. Quando non ci sono attività da eseguire per il momento, diventa &quot;passivo&quot;, cioè salva il suo stato nel database, quindi si arresta.
* Il modulo &#39;Workflow Server&#39; (wfserver) controlla le istanze correnti del flusso di lavoro. In presenza di un&#39;attività da eseguire, questo modulo crea un processo per attivare (o riattivare) l&#39;istanza corrispondente.

