---
product: campaign
title: Informazioni sulle attività di controllo del flusso
description: Informazioni sulle attività di controllo del flusso
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 7%

---

# Informazioni sulle attività di controllo del flusso{#about-flow-control-activities}

![](../../assets/common.svg)

Le seguenti attività sono attività del database: Il loro compito principale è quello di coordinare le altre attività.

* **Inizio e Fine**: ti consente di visualizzare i punti iniziale e finale di un flusso di lavoro. Fare riferimento a [Start ed end](start-and-end.md).
* **Fork**: consente di attivare tutte le transizioni in uscita. Consulta la sezione [Fork](fork.md) .
* **Appuntamento**: consente di attendere il completamento di più attività avviate contemporaneamente prima di procedere. Consulta la sezione [Fork](fork.md) .
* **Scheduler**: ti consente di definire una pianificazione dell’esecuzione di un flusso di lavoro. Fare riferimento a [Scheduler](scheduler.md).
* **Test**: abilita una transizione basata su un risultato del test. Fare riferimento a [Test](test.md).
* **Attendi**: abilita la transizione in uscita dopo un determinato limite di tempo. Fare riferimento a [Wait](wait.md) .
* **Vincolo** di tempo: consente di sospendere un&#39;attività per un determinato periodo di tempo. Fare riferimento a [Vincolo di tempo](time-constraint.md).
* **Flusso di lavoro** secondario: ti consente di eseguire un altro flusso di lavoro. Fare riferimento a [Flusso di lavoro secondario](sub-workflow.md).
* **Salti**: consente di implementare transizioni senza collegamenti. Fare riferimento a [Jump (punto iniziale e punto finale)](jump--start-point-and-end-point-.md).
* **Segnale** esterno: consente di abilitare la transizione in uscita dopo aver ricevuto un segnale esterno. Consulta la sezione [External signal](external-signal.md).
* **Approvazione**: consente di inviare un’e-mail a un operatore o a un gruppo di operatori e di attendere che l’approvazione continui con l’esecuzione. Consulta la sezione [Approvazione](approval.md) .
* **Avviso**: consente di inviare un avviso a un operatore o a un gruppo di operatori. Consulta la sezione [Avviso](alert.md) .
* **Attività**: consente di configurare l’esecuzione delle attività. Consulta la sezione [Attività](task.md) .
