---
product: campaign
title: Coordinare gli aggiornamenti dei dati
description: Coordinare gli aggiornamenti dei dati
feature: Workflows, Data Management
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# Coordinare gli aggiornamenti dei dati{#coordinating-data-updates}



Questo caso d’uso descrive la creazione di un flusso di lavoro che consente di gestire gli aggiornamenti concomitanti quando si utilizzano diverse esecuzioni di un flusso di lavoro.

Lo scopo è verificare che il processo di aggiornamento sia terminato prima di eseguire un&#39;altra operazione di aggiornamento. A questo scopo, verrà impostata una variabile di istanza e verrà eseguito un test del flusso di lavoro se l’istanza è in esecuzione per decidere se continuare l’esecuzione del flusso di lavoro ed eseguire l’aggiornamento.

![](assets/uc_dataupdate_wkf.png)

Questo flusso di lavoro è costituito da:

* a **Scheduler** che esegue il flusso di lavoro su una frequenza specifica.
* a **Test** attività che controlla se il flusso di lavoro è già in esecuzione.
* **Query** e **Aggiorna dati** attività nel caso in cui il flusso di lavoro non sia già in esecuzione, seguite da **Fine** attività che reinizializza la variabile dell’istanza del flusso di lavoro su false.
* Un **Fine** se il flusso di lavoro è già in esecuzione.

Per creare il flusso di lavoro, effettua le seguenti operazioni:

1. Aggiungi un **Scheduler** e configurarne la frequenza in base alle tue esigenze.
1. Aggiungi un **Test** per verificare se il flusso di lavoro è già in esecuzione, quindi configuralo come segue.

   >[!NOTE]
   >
   >&quot;isRunning&quot; è il nome della variabile di istanza scelto per questo esempio. Questa non è una variabile incorporata.

   ![](assets/uc_dataupdate_test.png)

1. Aggiungi un **Fine** attività al **No** fork. In questo modo, non viene eseguito nulla se il flusso di lavoro è già in esecuzione.
1. Aggiungi le attività desiderate al **Sì** fork. Nel nostro caso, **Query** e **Aggiorna dati** attività.
1. Apri la prima attività, quindi aggiungi **instance.vars.isRunning = true** comando in **[!UICONTROL Advanced]** scheda. In questo modo, la variabile di istanza viene impostata come in esecuzione.

   ![](assets/uc_dataupdate_query.png)

1. Aggiungi un **Fine** attività alla fine del **[!UICONTROL Yes]** fork, quindi aggiungi **instance.vars.isRunning = false** comando in **[!UICONTROL Advanced]** scheda.

   In questo modo, non verrà eseguita alcuna azione durante l’esecuzione del flusso di lavoro.

   ![](assets/uc_dataupdate_end.png)

**Argomenti correlati:**

* [Impedire esecuzioni simultanee multiple](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Attività Update Data](update-data.md)
