---
product: campaign
title: Informazioni sui flussi di lavoro
description: Automatizza i processi con i flussi di lavoro, gestisci dati e tipi di pubblico, invia messaggi e altro ancora
feature: Workflows, Data Management
exl-id: 024a7344-9376-4ff3-926a-003148229f9f
source-git-commit: dd6bcb16fe41b6a3f1e3f5aaf2f753b29ad4bc1d
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 59%

---

# Automatizzare con i flussi di lavoro {#gs-workflows}

Adobe Campaign include un modulo per flussi di lavoro con cui puoi migliorare l’orchestrazione dell’intera gamma di processi e attività tra i diversi moduli del server dell’applicazione. Questo ambiente grafico completo ti consente di progettare processi inclusi segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc. Il motore del flusso di lavoro esegue e traccia tali processi.

Ad esempio, puoi utilizzare un flusso di lavoro per scaricare un file da un server, decomprimerlo e quindi importare i record contenuti all’interno nel database di Adobe Campaign.

Un flusso di lavoro può inoltre coinvolgere uno o più operatori da avvisare o che possono effettuare scelte e approvare processi. In questo modo, è possibile creare un’azione di consegna, assegnare un’attività a uno o più operatori per lavorare sul contenuto, specificare dei target e approvare le prove prima di avviare la consegna.

I flussi di lavoro si verificano in vari contesti e fasi del processo di gestione delle campagne.

Per ulteriori informazioni sulla gestione dei flussi di lavoro, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=it){target=_blank}.

![](assets/do-not-localize/workflow.jpg){width="40%"}

Scopri i passaggi chiave relativi alla gestione dei flussi di lavoro:

* [Attività del flusso di lavoro](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html?lang=it){target=_blank}: un&#39;attività descrive un modello di attività. I flussi di lavoro includono attività di targeting, controllo del flusso, azione ed evento.

* [Crea un flusso di lavoro](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=it){target=_blank}: scopri come creare ed eseguire flussi di lavoro di targeting, campagne e tecnici.

* [Best practice](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=it){target=_blank}: scopri le linee guida per ottimizzare le prestazioni del flusso di lavoro di Campaign, migliorare la progettazione del flusso di lavoro e selezionare le impostazioni corrette.

* [Monitorare i flussi di lavoro](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=it){target=_blank}: scopri come monitorare l&#39;esecuzione dei flussi di lavoro per verificare che tutto funzioni correttamente.

* [Casi di utilizzo del flusso di lavoro](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/workflow-use-cases.html?lang=it){target=_blank}: scopri diversi contesti in cui è possibile utilizzare i flussi di lavoro e come implementarli tramite casi di utilizzo end-to-end.

<!--

Adobe Campaign uses workflows to:

* Carry out targeting campaigns. [Learn more](building-a-workflow.md#implementation-steps-)
* Build campaigns: for each campaign, the **[!UICONTROL Workflow]** tab lets you build the target and create the deliveries. [Learn more](building-a-workflow.md#campaign-workflows)
* Perform technical processes: cleanup, collecting tracking information or provisional calculations. [Learn more](building-a-workflow.md#technical-workflows)

A workflow can mean both a process definition (the workflow model, which is a representation of what is supposed to happen) and an instance of this process (a workflow instance, which is a representation of what is actually happening).

The workflow template describes the various tasks to be performed and how they are linked together. The task templates are called activities and are represented by icons. They are linked together by transitions.

![](assets/example1.png)

Each workflow contains:

* **[!UICONTROL Activities]**

  An activity describes a task template. The various activities available are represented on the diagram by icons. Each type has common properties and specific properties. For example, while all activities have a name and label, only the **[!UICONTROL Approval]** activity has an assignment.

  In a workflow diagram, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

  All workflow activities are listed in [this section](about-activities.md), including use cases and samples.

* **[!UICONTROL Transitions]**

  Transitions enable you to link activities and to define their sequence. A transition links a source activity to a destination activity. There are several sorts of transitions, which depend on the source activity. Some transitions have additional parameters such as a duration, a condition or a filter.

  A transition which is not linked to a destination activity is colored orange and the arrow head is shown as a diamond.

  >[!NOTE]
  >
  >A workflow containing unterminated transitions can still be executed: a warning message will be generated and the workflow will pause once it reaches the transition but it will not generate an error. It is thus possible to start a workflow without it being finished and to add to it as you go along.

  For more information about how to build a workflow, refer to [this section](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  The worktable contains all the information carried by the transition. Each workflow uses several worktables. The data conveyed in these tables can be accelerated and used throughout the workflow's life cycle, as long as it is not purged. Indeed, unneeded tables are purged each time the workflow is passivated, and possibly during the execution of the largest workflows to avoid overloading the server.

  Learn more on workflow data and tables in [this section](how-to-use-workflow-data.md).

## Key principles and best practices{#principles-workflows}

Refer to these sections to find guidance and best practices to automate processes with workflows:

* Learn more about workflow activities in [this page](how-to-use-workflow-data.md).
* Learn how to build a workflow in [this section](building-a-workflow.md).
* Discover how to use workflows to import data in Campaign in [this section](../../platform/using/import-export-workflows.md).
* Workflow best practices are detailed in [this page](workflow-best-practices.md).
* Find guidance about workflow execution in [this section](starting-a-workflow.md).
* Learn how to monitor workflows in [this page](monitoring-workflow-execution.md).
* Learn how to grant access to users to use workflows in [this page](managing-rights.md).

-->