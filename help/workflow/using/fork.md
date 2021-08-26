---
product: campaign
title: Attività Fork
description: Ulteriori informazioni sull’attività del flusso di lavoro Fork
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---

# Attività Fork{#fork}

![](../../assets/common.svg)

L’attività **[!UICONTROL Fork]** ti consente di creare più transizioni in uscita, al fine di eseguire diverse attività in modo indipendente all’interno dello stesso flusso di lavoro.

Ad esempio, puoi utilizzare l’attività dopo una query, per eseguire due azioni in parallelo:

* Salva il risultato della query in un pubblico,
* Esegui una segmentazione sul risultato per inviare più consegne.

Puoi inoltre utilizzare l’attività nel contesto dell’automazione della creazione e dell’invio dei contenuti, per avviare il calcolo di target e la creazione dei contenuti in parallelo. Un caso d&#39;uso dedicato è disponibile in [questa sezione](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Le transizioni in uscita aggiunte dopo un’attività **[!UICONTROL Fork]** **non verranno eseguite simultaneamente**. Questo comportamento può influire sulle prestazioni del flusso di lavoro. Utilizza questa attività se devi eseguire diverse attività in modo indipendente e alla fine uniscile prima di eseguire il resto del flusso di lavoro.

Per configurare l’attività **[!UICONTROL Fork]** , aprila definendo il numero e l’etichetta delle transizioni in uscita.

![](assets/s_user_segmentation_fork.png)

Puoi quindi configurare ogni transizione in uscita, quindi unirle utilizzando un&#39;attività [AND-join](and-join.md) , se necessario. In questo modo, il resto del flusso di lavoro verrà eseguito solo una volta completate le transizioni in uscita dell’attività **[!UICONTROL Fork]**.
