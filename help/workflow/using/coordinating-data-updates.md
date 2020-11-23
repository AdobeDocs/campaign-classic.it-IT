---
solution: Campaign Classic
product: campaign
title: Coordinamento degli aggiornamenti dati
description: Coordinamento degli aggiornamenti dati
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---


# Coordinamento degli aggiornamenti dati{#coordinating-data-updates}

Questo caso d’uso descrive in dettaglio la creazione di un flusso di lavoro che consente di gestire gli aggiornamenti dei contenuti quando si utilizzano più esecuzioni di un flusso di lavoro.

L&#39;obiettivo è verificare che il processo di aggiornamento sia terminato prima di eseguire un&#39;altra operazione di aggiornamento. A questo scopo, imposteremo una variabile di istanza e lasceremo che il flusso di lavoro verifichi se l&#39;istanza è in esecuzione per decidere se continuare o meno l&#39;esecuzione del flusso di lavoro ed eseguire l&#39;aggiornamento.

![](assets/uc_dataupdate_wkf.png)

Questo flusso di lavoro è composto da:

* un&#39;attività **Scheduler** che esegue il flusso di lavoro su una frequenza specifica.
* un&#39;attività **Test** che verifica se il flusso di lavoro è già in esecuzione.
* **Attività di query** e **aggiornamento dati** nel caso in cui il flusso di lavoro non sia già in esecuzione, seguite da un&#39;attività **End** che reinizializza la variabile di istanza del flusso di lavoro su false.
* Un&#39;attività **End** se il flusso di lavoro è già in esecuzione.

Per generare il flusso di lavoro, effettuate le seguenti operazioni:

1. Aggiungi un&#39;attività **Scheduler** , quindi configurane la frequenza in base alle tue esigenze.
1. Aggiungete un&#39;attività **Test** per verificare se il flusso di lavoro è già in esecuzione, quindi configuratela come di seguito.

   >[!NOTE]
   >
   >&quot;isRunning&quot; è il nome della variabile di istanza scelto per questo esempio. Questa non è una variabile incorporata.

   ![](assets/uc_dataupdate_test.png)

1. Aggiungete un&#39;attività **End** al **fork No** . In questo modo, se il flusso di lavoro è già in esecuzione non verrà eseguito nulla.
1. Aggiungete le attività desiderate al modulo **Sì** . Nel nostro caso, le attività **Query** e **Aggiorna dati** .
1. Aprite la prima attività, quindi aggiungete il comando **instance.vars.isRunning = true** nella **[!UICONTROL Advanced]** scheda. In questo modo, la variabile di istanza viene impostata come in esecuzione.

   ![](assets/uc_dataupdate_query.png)

1. Aggiungete un&#39;attività **End** alla fine del **[!UICONTROL Yes]** fork, quindi aggiungete il comando **instance.vars.isRunning = false** nella **[!UICONTROL Advanced]** scheda.

   In questo modo, non verrà eseguita alcuna azione finché il flusso di lavoro sarà in esecuzione.

   ![](assets/uc_dataupdate_end.png)

**Argomenti correlati:**

* [Prevenzione simultanea di più esecuzioni](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Aggiorna attività dati](../../workflow/using/update-data.md)

