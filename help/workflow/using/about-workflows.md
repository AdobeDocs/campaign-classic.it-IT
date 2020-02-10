---
title: Informazioni sui flussi di lavoro
seo-title: Informazioni sui flussi di lavoro
description: Informazioni sui flussi di lavoro
seo-description: null
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
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Informazioni sui flussi di lavoro{#about-workflows}

Adobe Campaign include un modulo di flusso di lavoro che consente di orchestrare l&#39;intera gamma di processi e attività tra i diversi moduli del server applicazione. Questo ambiente grafico completo vi consente di progettare processi che includono segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc. Il motore del flusso di lavoro esegue e tiene traccia di questi processi.

Puoi utilizzare un flusso di lavoro, ad esempio, per scaricare un file da un server, decomprimerlo e importare i record contenuti nel database di Adobe Campaign.

Un flusso di lavoro può coinvolgere anche uno o più operatori ai quali inviare una notifica o che possono effettuare scelte e approvare processi. In questo modo, è possibile creare un&#39;azione di consegna, assegnare un&#39;attività a uno o più operatori per lavorare sul contenuto, specificare le destinazioni e approvare le prove prima di iniziare la consegna.

I flussi di lavoro si verificano in vari contesti e fasi del processo di gestione delle campagne.

Adobe Campaign utilizza i flussi di lavoro per:

* Eseguire campagne di targeting. Per ulteriori informazioni, consulta i passaggi [di](../../workflow/using/building-a-workflow.md#implementation-steps-)implementazione.
* Creare campagne: per ogni campagna, la **[!UICONTROL Workflow]** scheda consente di creare la destinazione e creare le consegne. Per ulteriori informazioni, consulta Flussi di lavoro [](../../workflow/using/building-a-workflow.md#campaign-workflows)Campaign.
* Eseguire processi tecnici: pulizia, raccolta delle informazioni di tracciamento o calcoli provvisori. Per ulteriori informazioni, consulta Flussi di lavoro [](../../workflow/using/building-a-workflow.md#technical-workflows)tecnici.

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
   >È comunque possibile eseguire un flusso di lavoro contenente transizioni non interrotte: viene generato un messaggio di avviso e il flusso di lavoro viene messo in pausa una volta raggiunta la transizione, ma non viene generato un errore. È quindi possibile avviare un flusso di lavoro senza completarlo e aggiungerlo man mano che si procede.

   Per ulteriori informazioni sulla creazione di un flusso di lavoro, consulta [questa sezione](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Worktables]**

   La tabella di lavoro contiene tutte le informazioni riportate dalla transizione. Ogni flusso di lavoro utilizza diverse tabelle di lavoro. I dati trasmessi in queste tabelle possono essere accelerati e utilizzati per tutto il ciclo di vita del flusso di lavoro, purché non vengano eliminati. In effetti, le tabelle non necessarie vengono eliminate ogni volta che il flusso di lavoro viene passivato, ed eventualmente durante l&#39;esecuzione dei flussi di lavoro più grandi per evitare di sovraccaricare il server.

   Ulteriori informazioni sui dati e sulle tabelle del flusso di lavoro in [questa sezione](../../workflow/using/how-to-use-workflow-data.md).

