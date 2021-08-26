---
product: campaign
title: Attività Scheduler
description: Ulteriori informazioni sull’attività del flusso di lavoro Scheduler
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# Attività Scheduler {#scheduler}

![](../../assets/common.svg)

Il **Scheduler** è un&#39;attività persistente che attiva la relativa transizione nei momenti specificati dalla relativa pianificazione.

Dovresti considerare l’attività **[!UICONTROL Scheduler]** come un inizio pianificato. Le regole di posizionamento dell’attività all’interno del grafico sono le stesse dell’attività **[!UICONTROL Start]**. Questa attività non deve avere una transizione in entrata.

## Best practice {#best-practices}

* Non pianificare l’esecuzione di un flusso di lavoro per più di 15 minuti in quanto potrebbe impedire le prestazioni complessive del sistema e creare blocchi nel database.

* Non utilizzare mai più di un’attività **[!UICONTROL Scheduler]** per ramo in un flusso di lavoro. Consulta [Utilizzo di attività](workflow-best-practices.md#using-activities).

* L’utilizzo di un’attività di pianificazione può causare l’esecuzione simultanea di diverse esecuzioni di un flusso di lavoro. Ad esempio, puoi avere una pianificazione che attiva l’esecuzione del flusso di lavoro ogni ora, ma a volte l’esecuzione dell’intero flusso di lavoro richiede più di un’ora.

   Puoi saltare l’esecuzione se il flusso di lavoro è già in esecuzione. Per ulteriori informazioni su come evitare esecuzioni simultanee di un flusso di lavoro, consulta [questa pagina](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* Tieni presente che la transizione può essere attivata diverse ore dopo se il flusso di lavoro esegue un’attività a lungo termine, ad esempio un’importazione, o se il modulo wfserver è stato arrestato per un periodo di tempo. In questo caso, potrebbe essere necessario limitare l&#39;esecuzione dell&#39;attività attivata dal programmatore a un determinato intervallo di tempo.

## Configurazione dell’attività Scheduler {#configuring-scheduler-activity}

La pianificazione definisce la pianificazione di attivazione della transizione. Per configurarlo, fai doppio clic sull’oggetto grafico, quindi fai clic su **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

Una procedura guidata consente di definire la frequenza e il periodo di validità dell’attività. I passaggi di configurazione sono i seguenti:

1. Seleziona la frequenza di attivazione e fai clic su **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Assegna tempi e giorni di attivazione. I parametri di questo passaggio dipendono dalla frequenza selezionata nel passaggio precedente. Se scegli di avviare l’attività diverse volte al giorno, le opzioni di configurazione saranno le seguenti:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Definire il periodo di validità della pianificazione o specificare quante volte verrà eseguita.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Controlla la configurazione e fai clic su **[!UICONTROL Finish]** per salvare.

   ![](assets/s_user_segmentation_scheduler5.png)
