---
product: campaign
title: Informazioni sui flussi di lavoro
description: Automatizza i processi con i flussi di lavoro, gestisci dati e tipi di pubblico, invia messaggi e altro ancora
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Data Management
exl-id: 51be6b90-2a7a-4757-9754-d16c540a87ff
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 38%

---

# Introduzione ai flussi di lavoro{#gs-workflows}



## Informazioni sui flussi di lavoro{#about-workflows}

Adobe Campaign include un modulo per flussi di lavoro con cui puoi migliorare l’orchestrazione dell’intera gamma di processi e attività tra i diversi moduli del server dell’applicazione. Questo ambiente grafico completo ti consente di progettare processi inclusi segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc. Il motore del flusso di lavoro esegue e traccia tali processi.

Ad esempio, puoi utilizzare un flusso di lavoro per scaricare un file da un server, decomprimerlo e quindi importare i record contenuti all’interno nel database di Adobe Campaign.

Un flusso di lavoro può inoltre coinvolgere uno o più operatori da avvisare o che possono effettuare scelte e approvare processi. In questo modo, è possibile creare un’azione di consegna, assegnare un’attività a uno o più operatori per lavorare sul contenuto, specificare dei target e approvare le prove prima di avviare la consegna.

I flussi di lavoro si verificano in vari contesti e fasi del processo di gestione delle campagne.

Adobe Campaign utilizza i flussi di lavoro per:

* Eseguire campagne di targeting. [Ulteriori informazioni](building-a-workflow.md#implementation-steps-)
* Creare campagne: per ogni campagna, il **[!UICONTROL Workflow]** Questa scheda ti consente di generare il target e creare le consegne. [Ulteriori informazioni](building-a-workflow.md#campaign-workflows)
* Eseguire processi tecnici: pulizia, raccolta di informazioni di tracciamento o calcoli provvisori. [Ulteriori informazioni](building-a-workflow.md#technical-workflows)

Un flusso di lavoro può significare sia una definizione di processo (il modello di flusso di lavoro, che è una rappresentazione di ciò che dovrebbe accadere) che un&#39;istanza di questo processo (un&#39;istanza di flusso di lavoro, che è una rappresentazione di ciò che sta effettivamente accadendo).

Il modello di flusso di lavoro descrive le varie attività da eseguire e il modo in cui vengono collegate tra loro. I modelli di attività sono denominati attività e sono rappresentati da icone. Sono collegati tra loro da transizioni.

![](assets/example1.png)

Ogni flusso di lavoro contiene:

* **[!UICONTROL Activities]**

  Un’attività descrive un modello di attività. Le varie attività disponibili sono rappresentate nel diagramma da icone. Ogni tipo ha proprietà comuni e specifiche. Ad esempio, tutte le attività hanno un nome e un’etichetta, ma solo **[!UICONTROL Approval]** l&#39;attività ha un&#39;assegnazione.

  In un diagramma di flusso di lavoro, una determinata attività può produrre più attività, in particolare quando è presente un ciclo continuo o azioni ricorrenti (periodiche).

  Tutte le attività del flusso di lavoro sono elencate in [questa sezione](about-activities.md), inclusi casi d&#39;uso e campioni.

* **[!UICONTROL Transitions]**

  Le transizioni consentono di collegare le attività e definirne la sequenza. Una transizione collega un’attività sorgente a un’attività di destinazione. Esistono diversi tipi di transizioni, che dipendono dall’attività sorgente. Alcune transizioni presentano parametri aggiuntivi, ad esempio una durata, una condizione o un filtro.

  Una transizione non collegata a un’attività di destinazione è di colore arancione e la punta della freccia è visualizzata come un rombo.

  >[!NOTE]
  >
  >È comunque possibile eseguire un flusso di lavoro contenente transizioni non terminate: verrà generato un messaggio di avviso e il flusso di lavoro verrà messo in pausa una volta raggiunta la transizione, ma non verrà generato un errore. È quindi possibile avviare un flusso di lavoro senza che sia stato completato e aggiungerlo man mano che prosegui.

  Per ulteriori informazioni su come creare un flusso di lavoro, consulta [questa sezione](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  La tabella di lavoro contiene tutte le informazioni contenute nella transizione. Ogni flusso di lavoro utilizza diverse tabelle di lavoro. I dati trasmessi in queste tabelle possono essere accelerati e utilizzati in tutto il ciclo di vita del flusso di lavoro, purché non vengano eliminati. In effetti, le tabelle non necessarie vengono eliminate ogni volta che il flusso di lavoro viene passivato e possibilmente durante l’esecuzione dei flussi di lavoro più grandi per evitare di sovraccaricare il server.

  Ulteriori informazioni sui dati e sulle tabelle del flusso di lavoro in [questa sezione](how-to-use-workflow-data.md).

## Principi chiave e best practice{#principles-workflows}

Consulta queste sezioni per trovare indicazioni e best practice per automatizzare i processi con i flussi di lavoro:

* Ulteriori informazioni sulle attività dei flussi di lavoro in [questa pagina](how-to-use-workflow-data.md).
* Scopri come creare un flusso di lavoro in [questa sezione](building-a-workflow.md).
* Scopri come utilizzare i flussi di lavoro per importare dati in Campaign in [questa sezione](../../platform/using/import-export-workflows.md).
* Le best practice per i flussi di lavoro sono descritte in dettaglio [questa pagina](workflow-best-practices.md).
* Trova informazioni sull’esecuzione dei flussi di lavoro in [questa sezione](starting-a-workflow.md).
* Scopri come monitorare i flussi di lavoro in [questa pagina](monitoring-workflow-execution.md).
* Scopri come concedere l’accesso agli utenti per utilizzare i flussi di lavoro in [questa pagina](managing-rights.md).
