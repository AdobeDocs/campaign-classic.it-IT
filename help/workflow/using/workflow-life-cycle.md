---
solution: Campaign Classic
product: campaign
title: Ciclo di vita di un flusso di lavoro
description: Ulteriori informazioni sul ciclo di vita di un flusso di lavoro
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---


# Ciclo di vita di un flusso di lavoro {#workflow-life-cycle}

Il ciclo di workflow presenta tre fasi principali.

* **In corso di modifica**

   Questa è la fase di progettazione iniziale: Quando viene creato un nuovo flusso di lavoro, il suo stato è &#39;In corso di modifica&#39;. Il flusso di lavoro non è ancora gestito dal server e può essere modificato senza rischi.

* **Avviato**

   Una volta completata la fase di progettazione iniziale, il flusso di lavoro può essere avviato. In questa fase, l&#39;istanza viene gestita dal server e le singole attività vengono eseguite. Il flusso di lavoro può comunque essere modificato con alcune precauzioni.

* **Completato**

   Un flusso di lavoro è &quot;Completato&quot; quando non sono più presenti attività in corso o quando un operatore ha esplicitamente arrestato l&#39;istanza.

Ad esempio, le attività **Start** e **Delivery** vengono evidenziate mentre l&#39;attività **Approval** lampeggia nel flusso di lavoro sottostante.

![](assets/new-workflow-6.png)

Ciò significa che le prime due attività sono state eseguite correttamente e che l&#39;approvazione è in corso, ovvero è stata creata ma non ancora completata.

I caratteri **574 -Ok** visualizzati sopra la transizione dopo l&#39;attività **Delivery** indicano che la preparazione della consegna ha interessato 574 destinatari e che l&#39;operazione è stata completata correttamente. Queste informazioni, che vengono aggiunte alle transizioni quando vengono eseguite, vengono calcolate dalle attività che elaborano i dati.

Il flusso di lavoro viene avviato e è in attesa che un operatore appartenente al gruppo specificato nell&#39;attività **Approval** prenda una decisione. Gli operatori appartenenti al gruppo e che dispongono di un indirizzo e-mail o di un numero di telefono cellulare ricevono una notifica.

La gestione dell&#39;operatore è descritta in questa sezione [](../../platform/using/access-management.md).

Per ulteriori informazioni su come monitorare i flussi di lavoro, consultare [questa sezione](../../workflow/using/monitoring-workflow-execution.md).
