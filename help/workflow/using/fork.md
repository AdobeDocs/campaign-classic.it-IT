---
product: campaign
title: Fork
description: Ulteriori informazioni sull’attività del flusso di lavoro Fork
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---

# Fork{#fork}



È possibile utilizzare **[!UICONTROL Fork]** attività per creare più transizioni in uscita ed eseguire diverse attività in modo indipendente all’interno dello stesso flusso di lavoro.

>[!IMPORTANT]
>
>Le transizioni in uscita aggiunte dopo un **[!UICONTROL Fork]** l&#39;attività non viene eseguita contemporaneamente. Questo comportamento può influire sulle prestazioni del flusso di lavoro. Utilizza il **[!UICONTROL Fork]** se devi eseguire diverse attività in modo indipendente. Facoltativamente, puoi unire le attività in uscita prima della parte successiva del flusso di lavoro.

Per configurare un **[!UICONTROL Fork]** e le attività correlate, eseguire la procedura seguente:

1. Apri **[!UICONTROL Fork]** e definiscono il nome e l’etichetta delle transizioni in uscita.

   ![](assets/s_user_segmentation_fork.png)

1. Apri ogni transizione in uscita e configurala.
1. Facoltativamente, per unire le transizioni in uscita, aggiungi un’attività AND-join. [Ulteriori informazioni](and-join.md).

   La parte successiva del flusso di lavoro viene eseguita solo al completamento delle transizioni in uscita unite.

## Esempio: segmentazione

In questo esempio, e-mail diverse vengono inviate a gruppi di popolazione diversi. A **[!UICONTROL Fork]** L’attività viene utilizzata dopo una query per eseguire due azioni in parallelo:

* Salvare il risultato della query
* Segmentare il risultato per inviare più consegne

  ![L’attività fork segue l’intersezione di due query e precede un’attività di aggiornamento elenco e un’attività divisa.](assets/wkf_fork_example.png)

Il flusso di lavoro comprende le seguenti attività:

1. **[!UICONTROL Query]** attività

   Due gruppi di popolazione sono selezionati: le donne e i parigini.

1. **[!UICONTROL Intersection]** attività

   Viene selezionata l’intersezione dei risultati della query, ovvero donne parigine.

1. **[!UICONTROL Fork]** attività

   La popolazione calcolata viene salvata e, in parallelo, segmentata in due gruppi:

   1. Donne parigine di età compresa tra 18 e 40 anni
   1. Parigine over 40

1. **[!UICONTROL Delivery]** attività

   A ciascun gruppo di popolazione viene inviata un’e-mail diversa.

## Caso d’uso: inviare un’e-mail di compleanno

Un’e-mail ricorrente viene inviata a un elenco di destinatari per il compleanno. A **[!UICONTROL Fork]** L’attività viene utilizzata per includere i destinatari nati il 29 febbraio in un anno bisestile. [Ulteriori informazioni](sending-a-birthday-email.md) informazioni su questo caso d’uso.

![L’attività di fork segue un’attività di test e precede due attività di query.](assets/birthday-workflow_usecase_1.png)

## Caso di utilizzo: automatizzare i contenuti con un flusso di lavoro

La creazione e la distribuzione di un blocco di contenuto sono automatizzate. A **[!UICONTROL Fork]** L’attività viene utilizzata per calcolare il target e, in parallelo, per creare il contenuto. [Ulteriori informazioni](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) informazioni su questo caso d’uso.

![L’attività fork segue un’attività di consegna e precede un’attività query e un’attività di gestione dei contenuti, entrambe unite tramite un’attività AND-join.](../../delivery/using/assets/d_ncs_content_workflow10.png)

Puoi quindi configurare ciascuna transizione in uscita, quindi unirla utilizzando un’ [Unione AND](and-join.md) attività, se necessario. In questo modo, il resto del flusso di lavoro verrà eseguito una sola volta **[!UICONTROL Fork]** le transizioni in uscita dell’attività sono terminate.

## Argomenti correlati

* [Attività AND-join](and-join.md)
* [Caso d’uso: e-mail di compleanno](sending-a-birthday-email.md)
* [Caso di utilizzo: creazione e distribuzione di contenuti](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)