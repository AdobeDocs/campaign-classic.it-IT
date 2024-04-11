---
product: campaign
title: Ciclo di vita di un flusso di lavoro
description: Ulteriori informazioni sul ciclo di vita di un workflow
feature: Workflows
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Ciclo di vita di un flusso di lavoro {#workflow-life-cycle}



Il ciclo del flusso di lavoro prevede tre passaggi principali.

* **In fase di modifica**

  Questa è la fase di progettazione iniziale: quando viene creato il nuovo flusso di lavoro, il suo stato è &quot;In corso di modifica&quot;. Il flusso di lavoro non è ancora gestito dal server e può essere modificato senza rischi.

* **Avviato**

  Una volta completata la fase di progettazione iniziale, è possibile avviare il flusso di lavoro. In questa fase, l’istanza viene gestita dal server e vengono eseguite le singole attività. È comunque possibile modificare il flusso di lavoro con alcune precauzioni.

* **Completato**

  Un flusso di lavoro è &quot;Completato&quot; quando non sono più presenti attività in corso o quando un operatore ha esplicitamente interrotto l’istanza.

Ad esempio, il **Inizio** e **Consegna** le attività sono descritte mentre il **Approvazione** l&#39;attività lampeggia nel flusso di lavoro seguente.

![](assets/new-workflow-6.png)

Ciò significa che le prime due attività sono state eseguite correttamente e che l’approvazione è in corso, ovvero è stata creata ma non ancora completata.

I caratteri **574 - Ok** visualizzato sopra la transizione successiva alla **Consegna** attività significa che la preparazione della consegna ha eseguito il targeting di 574 destinatari e che l’operazione è stata completata correttamente. Queste informazioni, che vengono aggiunte alle transizioni quando vengono eseguite, vengono calcolate dalle attività che elaborano i dati.

Il flusso di lavoro viene avviato ed è in attesa di un operatore appartenente al gruppo specificato in **Approvazione** per prendere una decisione. Gli operatori appartenenti al gruppo e che dispongono di un indirizzo e-mail o di un numero di telefono cellulare ricevono una notifica.

La gestione degli operatori è descritta in questo [sezione](../../platform/using/access-management.md).

Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta [questa sezione](monitoring-workflow-execution.md).
