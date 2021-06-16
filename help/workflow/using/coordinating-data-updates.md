---
product: campaign
title: Coordinamento degli aggiornamenti dati
description: Coordinamento degli aggiornamenti dati
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# Coordinare gli aggiornamenti dei dati{#coordinating-data-updates}

Questo caso d’uso descrive la creazione di un flusso di lavoro che consente di gestire gli aggiornamenti dei concomitanti quando si utilizzano diverse esecuzioni di un flusso di lavoro.

L’obiettivo è quello di verificare che il processo di aggiornamento sia terminato prima di eseguire un’altra operazione di aggiornamento. A questo scopo, imposteremo una variabile di istanza e lasceremo che il flusso di lavoro verifichi se l’istanza è in esecuzione per decidere se continuare o meno l’esecuzione del flusso di lavoro ed eseguire l’aggiornamento.

![](assets/uc_dataupdate_wkf.png)

Questo flusso di lavoro è costituito da:

* un&#39;attività **Scheduler** che esegue il flusso di lavoro su una frequenza specifica.
* un&#39;attività **Test** che controlla se il flusso di lavoro è già in esecuzione.
* **** Query e  **aggiorna** le attività dati nel caso in cui il flusso di lavoro non sia già in esecuzione, seguite da un’attività  **** Endactivity che reinizializza la variabile dell’istanza del flusso di lavoro su false.
* Un&#39;attività **End** se il flusso di lavoro è già in esecuzione.

Per creare il flusso di lavoro, segui i passaggi seguenti:

1. Aggiungi un&#39;attività **Scheduler** , quindi configurane la frequenza in base alle tue esigenze.
1. Aggiungi un&#39;attività **Test** per verificare se il flusso di lavoro è già in esecuzione, quindi configurala come segue.

   >[!NOTE]
   >
   >&quot;isRunning&quot; è il nome della variabile di istanza scelto per questo esempio. Questa non è una variabile incorporata.

   ![](assets/uc_dataupdate_test.png)

1. Aggiungi un&#39;attività **End** al fork **No**. In questo modo, non verrà eseguito nulla se il flusso di lavoro è già in esecuzione.
1. Aggiungi le attività desiderate al fork **Sì**. Nel nostro caso, **Query** e **Aggiorna dati** attività.
1. Apri la prima attività, quindi aggiungi il comando **instance.vars.isRunning = true** nella scheda **[!UICONTROL Advanced]** . In questo modo, la variabile di istanza viene impostata come in esecuzione.

   ![](assets/uc_dataupdate_query.png)

1. Aggiungi un&#39;attività **End** alla fine del fork **[!UICONTROL Yes]**, quindi aggiungi il comando **instance.vars.isRunning = false** nella scheda **[!UICONTROL Advanced]** .

   In questo modo, non verrà eseguita alcuna azione finché il flusso di lavoro è in esecuzione.

   ![](assets/uc_dataupdate_end.png)

**Argomenti correlati:**

* [Impedire esecuzioni simultanee multiple](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Aggiorna attività dati](../../workflow/using/update-data.md)
