---
product: campaign
title: Ciclo di vita di un flusso di lavoro
description: Ulteriori informazioni sul ciclo di vita di un flusso di lavoro
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Ciclo di vita di un flusso di lavoro {#workflow-life-cycle}

Il ciclo del flusso di lavoro prevede tre passaggi principali.

* **In corso di modifica**

   Questa è la fase di progettazione iniziale: Quando viene creato un nuovo flusso di lavoro, il relativo stato è &quot;In corso di modifica&quot;. Il flusso di lavoro non è ancora gestito dal server e può essere modificato senza rischi.

* **Avviato**

   Una volta completata la fase di progettazione iniziale, è possibile avviare il flusso di lavoro. In questa fase, l’istanza viene gestita dal server e le singole attività vengono eseguite. Il flusso di lavoro può ancora essere modificato con alcune precauzioni.

* **Completato**

   Un flusso di lavoro è &quot;Completato&quot; quando non sono più presenti attività in corso o quando un operatore ha esplicitamente interrotto l’istanza.

Ad esempio, le attività **Start** e **Consegna** sono evidenziate mentre l&#39;attività **Approvazione** lampeggia nel flusso di lavoro seguente.

![](assets/new-workflow-6.png)

Ciò significa che le prime due attività sono state eseguite correttamente e che l’approvazione è in corso, ovvero è stata creata ma non ancora completata.

I caratteri **574 -Ok** visualizzati sopra la transizione dopo l’attività **Consegna** indicano che la preparazione della consegna ha eseguito il targeting di 574 destinatari e che l’operazione è stata completata correttamente. Queste informazioni, che vengono aggiunte alle transizioni quando vengono eseguite, vengono calcolate dalle attività che elaborano i dati.

Il flusso di lavoro viene avviato ed è in attesa che un operatore appartenente al gruppo specificato nell&#39;attività **Approvazione** prenda una decisione. Vengono notificati gli operatori appartenenti al gruppo e che dispongono di un indirizzo e-mail o di un numero di telefono cellulare.

La gestione degli operatori è descritta in questa sezione [sezione](../../platform/using/access-management.md).

Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta [questa sezione](../../workflow/using/monitoring-workflow-execution.md).
