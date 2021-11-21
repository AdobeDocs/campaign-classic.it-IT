---
product: campaign
title: Coordinamento degli aggiornamenti dati
description: Coordinamento degli aggiornamenti dati
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# Coordinare gli aggiornamenti dei dati{#coordinating-data-updates}

![](../../assets/common.svg)

Questo caso d’uso descrive la creazione di un flusso di lavoro che consente di gestire gli aggiornamenti simultanei quando si utilizzano diverse esecuzioni di un flusso di lavoro.

L’obiettivo è quello di verificare che il processo di aggiornamento sia terminato prima di eseguire un’altra operazione di aggiornamento. A questo scopo, imposteremo una variabile di istanza e lasceremo che il flusso di lavoro verifichi se l’istanza è in esecuzione per decidere se continuare o meno l’esecuzione del flusso di lavoro ed eseguire l’aggiornamento.

![](assets/uc_dataupdate_wkf.png)

Questo flusso di lavoro è costituito da:

* a **Scheduler** che esegue il flusso di lavoro su una frequenza specifica.
* a **Test** attività che controlla se il flusso di lavoro è già in esecuzione.
* **Query** e **Update data** attività nel caso in cui il flusso di lavoro non sia già in esecuzione, seguite da un **Fine** attività che reinizializza la variabile dell’istanza del flusso di lavoro su false.
* Un **Fine** se il flusso di lavoro è già in esecuzione.

Per creare il flusso di lavoro, segui i passaggi seguenti:

1. Aggiungi un **Scheduler** , quindi configurane la frequenza in base alle tue esigenze.
1. Aggiungi un **Test** per verificare se il flusso di lavoro è già in esecuzione, configuralo come segue.

   >[!NOTE]
   >
   >&quot;isRunning&quot; è il nome della variabile di istanza scelto per questo esempio. Questa non è una variabile incorporata.

   ![](assets/uc_dataupdate_test.png)

1. Aggiungi un **Fine** attività **No** forchetta. In questo modo, non verrà eseguito nulla se il flusso di lavoro è già in esecuzione.
1. Aggiungi le attività desiderate al **Sì** forchetta. Nel nostro caso, **Query** e **Aggiorna dati** attività.
1. Apri la prima attività, quindi aggiungi la **instance.vars.isRunning = true** nel comando **[!UICONTROL Advanced]** scheda . In questo modo, la variabile di istanza viene impostata come in esecuzione.

   ![](assets/uc_dataupdate_query.png)

1. Aggiungi un **Fine** attività alla fine del **[!UICONTROL Yes]** fork, quindi aggiungere il **instance.vars.isRunning = false** nel comando **[!UICONTROL Advanced]** scheda .

   In questo modo, non verrà eseguita alcuna azione finché il flusso di lavoro è in esecuzione.

   ![](assets/uc_dataupdate_end.png)

**Argomenti correlati:**

* [Impedire esecuzioni simultanee multiple](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Aggiorna attività dati](update-data.md)
