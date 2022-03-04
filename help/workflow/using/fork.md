---
product: campaign
title: Attività Fork
description: Ulteriori informazioni sull’attività del flusso di lavoro Fork
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Attività Fork{#fork}

![](../../assets/common.svg)

È possibile utilizzare **[!UICONTROL Fork]** per creare più transizioni in uscita ed eseguire diverse attività in modo indipendente all’interno dello stesso flusso di lavoro.

>[!IMPORTANT]
>
>Le transizioni in uscita aggiunte dopo un **[!UICONTROL Fork]** l’attività non viene eseguita simultaneamente. Questo comportamento può influire sulle prestazioni del flusso di lavoro. Utilizza la **[!UICONTROL Fork]** se devi eseguire diverse attività in modo indipendente. Facoltativamente, puoi unire le attività in uscita prima della parte successiva del flusso di lavoro.

Per configurare un **[!UICONTROL Fork]** attività e relative attività, segui questi passaggi:

1. Apri **[!UICONTROL Fork]** e definisci il nome e l’etichetta delle transizioni in uscita.

   ![](assets/s_user_segmentation_fork.png)

1. Apri ogni transizione in uscita e configurala.
1. Facoltativamente, per unire transizioni in uscita, aggiungi un’attività AND-join . [Ulteriori informazioni](and-join.md).

   La parte successiva del flusso di lavoro viene eseguita solo al completamento delle transizioni in uscita unite.

## Esempio: segmentazione

In questo esempio, vengono inviate e-mail diverse a diversi gruppi di popolazione. A **[!UICONTROL Fork]** l’attività viene utilizzata dopo una query per eseguire due azioni in parallelo:

* Salva il risultato della query
* Segmenta il risultato per inviare più consegne

   ![L’attività Fork segue l’intersezione di due query e precede un’attività di aggiornamento elenco e un’attività divisa.](assets/wkf_fork_example.png)

Il flusso di lavoro comprende le seguenti attività:

1. **[!UICONTROL Query]** attività

   Sono selezionati due gruppi di popolazione: donne e parigini.

1. **[!UICONTROL Intersection]** attività

   Viene selezionata l&#39;intersezione dei risultati della query, ovvero donne parigine.

1. **[!UICONTROL Fork]** attività

   La popolazione calcolata viene salvata e, in parallelo, segmentata in due gruppi:

   1. Parigine di età compresa tra i 18 e i 40 anni
   1. donne parigine sopra i 40 anni

1. **[!UICONTROL Delivery]** attività

   Viene inviata un’e-mail diversa a ogni gruppo di popolazione.

## Caso di utilizzo: invia un’e-mail di compleanno

Un’e-mail ricorrente viene inviata a un elenco di destinatari al momento del loro compleanno. A **[!UICONTROL Fork]** L’attività viene utilizzata per includere i destinatari nati il 29 febbraio in un anno bisestile. [Ulteriori informazioni](sending-a-birthday-email.md) informazioni su questo caso d’uso.

![L’attività fork segue un’attività di test e precede due attività di query.](assets/birthday-workflow_usecase_1.png)

## Caso di utilizzo: automatizzare il contenuto con un flusso di lavoro

La creazione e la consegna di un blocco di contenuto è automatizzata. A **[!UICONTROL Fork]** viene utilizzata per calcolare il target e, in parallelo, per creare il contenuto. [Ulteriori informazioni](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) informazioni su questo caso d’uso.

![L’attività Fork segue un’attività di consegna e precede un’attività Query e un’attività di gestione dei contenuti, entrambe collegate tramite un’attività AND-join.](../../delivery/using/assets/d_ncs_content_workflow10.png)

Puoi quindi configurare ogni transizione in uscita e unirle utilizzando un’ [AND-join](and-join.md) , se necessario. In questo modo, il resto del flusso di lavoro viene eseguito solo una volta che il **[!UICONTROL Fork]** le transizioni in uscita dell’attività sono completate.

## Argomenti correlati

* [Attività AND-join](and-join.md)
* [Caso di utilizzo: mail di compleanno](sending-a-birthday-email.md)
* [Caso di utilizzo: creazione e distribuzione di contenuti](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)