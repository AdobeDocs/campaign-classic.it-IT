---
title: Informazioni sui flussi di lavoro
description: Automatizza i processi con flussi di lavoro, gestisci dati e audience, invia messaggi e molto altro.
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 546c8f14006e333bb81aa52a008e9f1dfa79f03b
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 16%

---


# Introduzione ai flussi di lavoro{#gs-workflows}

## Informazioni sui flussi di lavoro{#about-workflows}

 Adobe Campaign include un modulo di flusso di lavoro che consente di orchestrare l&#39;intera gamma di processi e attività tra i diversi moduli del server applicazioni. Questo ambiente grafico completo ti consente di progettare processi inclusi segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc. Il motore del flusso di lavoro esegue e traccia tali processi.

Ad esempio, puoi utilizzare un flusso di lavoro per scaricare un file da un server, decomprimerlo e quindi importare i record contenuti all’interno nel database di Adobe Campaign.

Un flusso di lavoro può inoltre coinvolgere uno o più operatori da avvisare o che possono effettuare scelte e approvare processi. In questo modo, è possibile creare un’azione di consegna, assegnare un’attività a uno o più operatori per lavorare sul contenuto, specificare dei target e approvare le prove prima di avviare la consegna.

I flussi di lavoro si verificano in vari contesti e fasi del processo di gestione delle campagne.

 Adobe Campaign utilizza i flussi di lavoro per:

* Eseguire campagne di targeting. For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* Creare campagne: per ogni campagna, la **[!UICONTROL Workflow]** scheda consente di creare la destinazione e creare le consegne. For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* Eseguire processi tecnici: pulizia, raccolta delle informazioni di tracciamento o calcoli provvisori. For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

Un flusso di lavoro può significare sia una definizione del processo (il modello del flusso di lavoro, che è una rappresentazione di ciò che dovrebbe accadere) che un&#39;istanza di questo processo (un&#39;istanza del flusso di lavoro, che è una rappresentazione di ciò che sta effettivamente accadendo).

Il modello di flusso di lavoro descrive le varie attività da eseguire e come vengono collegate tra loro. I modelli di attività sono denominati attività e sono rappresentati da icone. Sono collegati tra loro da transizioni.

![](assets/example1.png)

Ogni flusso di lavoro contiene:

* **[!UICONTROL Activities]**

   Un&#39;attività descrive un modello di attività. Le varie attività disponibili sono rappresentate nel diagramma da icone. Ogni tipo ha proprietà comuni e proprietà specifiche. Ad esempio, mentre tutte le attività hanno un nome e un&#39;etichetta, solo l&#39; **[!UICONTROL Approval]** attività dispone di un&#39;assegnazione.

   In un diagramma di flusso di lavoro, una determinata attività può produrre più attività, in particolare in presenza di un ciclo o di azioni ricorrenti (periodiche).

   Tutte le attività del flusso di lavoro sono elencate in [questa sezione](../../workflow/using/about-activities.md), compresi casi di utilizzo ed esempi.

* **[!UICONTROL Transitions]**

   Le transizioni consentono di collegare le attività e definirne la sequenza. Una transizione collega un&#39;attività di origine a un&#39;attività di destinazione. Esistono diversi tipi di transizioni, che dipendono dall&#39;attività di origine. Alcune transizioni presentano parametri aggiuntivi, ad esempio una durata, una condizione o un filtro.

   Una transizione che non è collegata a un&#39;attività di destinazione è di colore arancione e l&#39;indicatore freccia è visualizzato come rombo.

   >[!NOTE]
   >
   >È comunque possibile eseguire un flusso di lavoro contenente transizioni non interrotte: viene generato un messaggio di avviso e il flusso di lavoro viene messo in pausa una volta raggiunta la transizione, ma non viene generato un errore. È quindi possibile avviare un flusso di lavoro senza completarlo e aggiungerlo man mano che si prosegue.

   Per ulteriori informazioni sulla creazione di un flusso di lavoro, consulta [questa sezione](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Worktables]**

   La tabella di lavoro contiene tutte le informazioni riportate dalla transizione. Ogni flusso di lavoro utilizza diverse tabelle di lavoro. I dati trasmessi in queste tabelle possono essere accelerati e utilizzati per tutto il ciclo di vita del flusso di lavoro, purché non vengano eliminati. In effetti, le tabelle non necessarie vengono eliminate ogni volta che il flusso di lavoro viene passivato, ed eventualmente durante l&#39;esecuzione dei flussi di lavoro più grandi per evitare di sovraccaricare il server.

   Ulteriori informazioni sui dati e sulle tabelle del flusso di lavoro in [questa sezione](../../workflow/using/how-to-use-workflow-data.md).

## Principi chiave e procedure ottimali{#principles-workflows}

Per informazioni e procedure ottimali per automatizzare i processi con i flussi di lavoro, consultare queste sezioni:

* Ulteriori informazioni sulle attività del flusso di lavoro in [questa pagina](../../workflow/using/how-to-use-workflow-data.md).
* Scopri come creare un flusso di lavoro in [questa sezione](../../workflow/using/building-a-workflow.md).
* Scopri come utilizzare i flussi di lavoro per importare dati in Campaign in [questa sezione](../../workflow/using/importing-data.md).
* Le best practice relative ai flussi di lavoro sono illustrate in [questa pagina](../../workflow/using/workflow-best-practices.md).
* In [questa sezione](../../workflow/using/starting-a-workflow.md)troverai le istruzioni sull’esecuzione del flusso di lavoro.
* Scopri come monitorare i flussi di lavoro in [questa pagina](../../workflow/using/monitoring-workflow-execution.md).
* Scopri come concedere l’accesso agli utenti per l’utilizzo dei flussi di lavoro in [questa pagina](../../workflow/using/managing-rights.md).
