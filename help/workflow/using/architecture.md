---
title: Architettura
description: I flussi di lavoro sono gestiti da un modulo specifico, che può essere avviato su più server per condividere il carico di elaborazione.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Architettura {#architecture}

I flussi di lavoro vengono gestiti da un modulo specifico. Questo modulo può essere avviato su più server per condividere il carico di elaborazione.

![](assets/architecture.png)

* Il processo &#39;Workflow Instance Runner&#39; (runwf) esegue tutte le attività di una determinata istanza del flusso di lavoro. Quando non ci sono attività da eseguire per il momento, diventa &quot;passivo&quot;, cioè salva il suo stato nel database, quindi si arresta.
* Il modulo &#39;Workflow Server&#39; (wfserver) controlla le istanze correnti del flusso di lavoro. In presenza di un&#39;attività da eseguire, questo modulo crea un processo per attivare (o riattivare) l&#39;istanza corrispondente.

Quando un operatore esegue un&#39;azione su un flusso di lavoro (avvio, arresto, pausa, ecc.), l&#39;azione non viene eseguita direttamente dal modulo &#39;nlserver&#39;, ma viene invece inserita in una coda per essere elaborata dal modulo del flusso di lavoro.
