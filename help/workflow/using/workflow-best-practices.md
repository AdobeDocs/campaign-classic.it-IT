---
product: campaign
title: Best practice per i flussi di lavoro
description: Scopri le best practice per i flussi di lavoro di Campaign
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 11%

---

# Best practice per i flussi di lavoro{#workflow-best-practices}



## Esecuzione e prestazioni {#execution-and-performance}

Di seguito sono elencate le linee guida generali sull’ottimizzazione delle prestazioni di Campaign, incluse le best practice da applicare ai flussi di lavoro.

Le linee guida per la risoluzione dei problemi relativi all&#39;esecuzione dei flussi di lavoro sono disponibili anche nella [Guida alla produzione di Campaign Classic v7](../../production/using/workflow-execution.md).

### Registri {#logs}

Il metodo JavaScript **[!UICONTROL logInfo()]** rappresenta una soluzione ottimale per il debug di un flusso di lavoro. È utile ma deve essere utilizzato con attenzione, in particolare per le attività che vengono eseguite di frequente: può sovraccaricare i registri e aumentare in modo significativo le dimensioni della tabella dei registri. Ma potrebbero essere necessari più di **[!UICONTROL logInfo()]**.

Sono disponibili due soluzioni aggiuntive:

* **Mantieni il risultato delle popolazioni provvisorie tra due esecuzioni**

  Questa opzione mantiene le tabelle temporanee tra due esecuzioni di un flusso di lavoro. È disponibile nella scheda **[!UICONTROL General]** delle proprietà del flusso di lavoro e può essere utilizzato a scopo di sviluppo e test per monitorare i dati e verificare i risultati. Puoi utilizzare questa opzione negli ambienti di sviluppo ma mai negli ambienti di produzione. Mantenere tabelle temporanee potrebbe comportare un aumento significativo delle dimensioni del database e, in ultima analisi, il raggiungimento del limite consentito. Inoltre, rallenterà il backup.

  Vengono mantenute solo le tabelle di lavoro dell’ultima esecuzione del flusso di lavoro. Le tabelle di lavoro delle esecuzioni precedenti vengono eliminate dal flusso di lavoro **[!UICONTROL cleanup]**, eseguito su base giornaliera.

  >[!CAUTION]
  >
  >Questa opzione non deve mai essere selezionata in un flusso di lavoro di produzione. Viene utilizzata per analizzare i risultati ed è progettata solo a scopo di test e quindi deve essere utilizzata solo in ambienti di sviluppo o di staging.

* **Registra le query SQL nel giornale di registrazione**

  Disponibile nella scheda **[!UICONTROL Execution]** delle proprietà del flusso di lavoro, questa opzione registra tutte le query SQL generate dallo strumento dalle diverse attività. È un buon modo per vedere cosa viene effettivamente eseguito dalla piattaforma. Tuttavia, questa opzione deve essere utilizzata solo temporaneamente durante lo sviluppo e non deve essere attivata durante la produzione.

Elimina i registri quando non sono più necessari. La cronologia del flusso di lavoro non viene eliminata automaticamente: tutti i messaggi vengono conservati per impostazione predefinita. La cronologia può essere eliminata tramite il menu **[!UICONTROL File > Actions]** o facendo clic sul pulsante Azioni nella barra degli strumenti sopra l&#39;elenco. Selezionare Rimuovi cronologia.
Per informazioni su come eliminare i registri, consulta questa [documentazione](starting-a-workflow.md).

### Pianificazione del flusso di lavoro {#workflow-planning}

* Prova a mantenere un livello stabile di attività durante il giorno ed evita picchi per evitare il sovraccarico dell’istanza. A tal fine, distribuisci gli orari di inizio del flusso di lavoro in modo uniforme nell’arco della giornata.
* Pianifica il caricamento dei dati durante la notte per ridurre il conflitto tra risorse.
* I flussi di lavoro lunghi possono potenzialmente avere un impatto sulle risorse del server e del database. Dividi i flussi di lavoro più lunghi per ridurre i tempi di elaborazione.
* Per ridurre i tempi di esecuzione complessivi, sostituisci le attività che richiedono tempo con attività semplificate e più veloci.
* Evita di eseguire più di 20 flussi di lavoro simultaneamente. Quando vengono eseguiti troppi flussi di lavoro contemporaneamente, il sistema può esaurire le risorse e diventare instabile. Per ulteriori informazioni sul motivo per cui il flusso di lavoro potrebbe non essere avviato, consulta questo [articolo](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).


### Esegui nel motore, opzione {#execute-in-the-engine-option}

Nella finestra **[!UICONTROL Workflow properties]**, non selezionare mai l&#39;opzione **[!UICONTROL Execute in the engine]**. Quando questa opzione è abilitata, il flusso di lavoro ha la priorità e tutti gli altri flussi di lavoro vengono interrotti dal motore del flusso di lavoro fino al completamento di questo.

![](assets/wf-execute-in-engine.png)

## Proprietà del flusso di lavoro {#workflow-properties}

### Cartelle del flusso di lavoro {#workflow-folders}

Adobe consiglia di creare i flussi di lavoro in una cartella dedicata.

Se il flusso di lavoro influisce sull&#39;intera piattaforma (ad esempio sui processi di pulizia), è possibile aggiungere una sottocartella nella cartella incorporata **[!UICONTROL Technical Workflows]**.

### Denominazione flusso di lavoro {#workflow-naming}

Poiché ciò ne semplifica la ricerca e la risoluzione dei problemi se non stanno ottenendo le prestazioni previste, Adobe consiglia di assegnare ai flussi di lavoro nomi ed etichette corretti: compila il campo di descrizione del flusso di lavoro per riepilogare il processo da eseguire in modo tale che l’operatore possa comprenderlo facilmente.

Se il flusso di lavoro fa parte di un processo che coinvolge più flussi di lavoro, puoi essere esplicito quando inserisci un’etichetta; l’utilizzo dei numeri è un ottimo modo per ordinare i flussi di lavoro (per Etichetta).

Ad esempio:

* 001 - Importazione - Destinatari importazione
* 002 - Importazione - Vendite all’importazione
* 003 - Importazione - Dettagli delle vendite all’importazione
* 010 - Esportazione - Registri di consegna delle esportazioni
* 011 - Esportazione - Registri di tracciamento delle esportazioni

### Gravità del flusso di lavoro {#workflow-severity}

È possibile configurare la gravità di un flusso di lavoro nelle proprietà del flusso di lavoro nella scheda **[!UICONTROL Execution]**:

* Normale
* Produzione
* Critico

L’indicazione di queste informazioni durante la creazione di un flusso di lavoro consente di comprendere la gravità del processo configurato.

Questa opzione non ha alcun impatto funzionale sui flussi di lavoro diversi da quelli delle campagne.

I flussi di lavoro delle campagne (flussi di lavoro creati come parte di una campagna/operazione) con una gravità più elevata vengono eseguiti in priorità nel caso in cui la campagna abbia molti processi che dovrebbero essere eseguiti contemporaneamente. Per impostazione predefinita, solo 10 processi possono essere eseguiti contemporaneamente in una campagna, in base all’opzione NmsOperation_LimitConcurrency. Ad esempio, se una campagna contiene 25 flussi di lavoro, quelli con una gravità maggiore verranno eseguiti nel primo pool di 10 processi.

### Monitoraggio del flusso di lavoro {#workflow-monitoring}

Tutti i flussi di lavoro pianificati in esecuzione negli ambienti di produzione devono essere monitorati per ricevere un avviso in caso di errore.

Nelle proprietà del flusso di lavoro, selezionare un gruppo Supervisore, il **[!UICONTROL Workflow supervisors]** predefinito o un gruppo personalizzato. Assicurati che almeno un operatore appartenga a questo gruppo, con un messaggio e-mail configurato.

Prima di iniziare a creare un flusso di lavoro, ricorda di definire i supervisori del flusso di lavoro. In caso di errori, verranno avvisati via e-mail. Per ulteriori informazioni, consulta [Gestione degli errori](monitoring-workflow-execution.md#managing-errors).

Controlla regolarmente la scheda **[!UICONTROL Monitoring]** per visualizzare lo stato generale dei flussi di lavoro attivi. Per ulteriori informazioni, consulta [Sorveglianza istanza](monitoring-workflow-execution.md#instance-supervision).

Workflow HeatMap consente agli amministratori della piattaforma Adobe Campaign di monitorare il carico sull’istanza e pianificare i flussi di lavoro di conseguenza. Per ulteriori informazioni, consulta [Monitoraggio del flusso di lavoro](heatmap.md).

## Utilizzo delle attività {#using-activities}

>[!CAUTION]
>
>Puoi copiare e incollare le attività all’interno dello stesso flusso di lavoro. Tuttavia, si sconsiglia di copiare e incollare le attività tra flussi di lavoro diversi. Alcune impostazioni associate ad attività come Consegne e Modulo di pianificazione potrebbero causare conflitti ed errori durante l’esecuzione del flusso di lavoro di destinazione. Ti consigliamo invece di **Duplicare** flussi di lavoro. Per ulteriori informazioni, vedere [Duplicazione dei flussi di lavoro](building-a-workflow.md#duplicating-workflows).

### Nome dell’attività {#name-of-the-activity}

Durante lo sviluppo del flusso di lavoro, tutte le attività avranno un nome, così come tutti gli oggetti di Adobe Campaign. Mentre il nome viene generato dallo strumento, è consigliabile rinominarlo con un nome esplicito durante la configurazione. Se lo facesse in un secondo momento, potrebbe interrompere il flusso di lavoro con le attività che utilizzano il nome di un’altra attività precedente. Sarebbe quindi difficile aggiornare i nomi in seguito.

Il nome dell&#39;attività si trova nella scheda **[!UICONTROL Advanced]**. Non lasciarli denominati **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]**, ma assegnargli nomi espliciti come **[!UICONTROL querySubscribedRecipients]**. Questo nome verrà visualizzato nel giornale di registrazione e, se applicabile, nei registri SQL e sarà utile per eseguire il debug del flusso di lavoro durante la configurazione.

### Prima e ultima attività {#first-and-last-activities}

* Avvia sempre il flusso di lavoro con un&#39;attività **[!UICONTROL Start]** o **[!UICONTROL Scheduler]**. Se necessario, è inoltre possibile utilizzare un&#39;attività **[!UICONTROL External signal]**.
* Durante la creazione del flusso di lavoro, utilizzare una sola attività **[!UICONTROL Scheduler]** per ramo. Se lo stesso ramo di un flusso di lavoro ha più pianificatori (collegati tra loro), il numero di attività da eseguire verrà moltiplicato in modo esponenziale, il che sovraccaricherebbe notevolmente il database. Questa regola si applica anche a tutte le attività con una scheda **[!UICONTROL Scheduling & History]**. Ulteriori informazioni su [Pianificazione](scheduler.md).

  ![](assets/wf-scheduler.png)

* Utilizza **[!UICONTROL End]** attività per ogni flusso di lavoro. Questo consente ad Adobe Campaign di liberare spazio temporaneo utilizzato per i calcoli all’interno dei flussi di lavoro. Per ulteriori informazioni, consulta: [Inizio e fine](start-and-end.md).

### JavaScript all&#39;interno di un&#39;attività {#javascript-within-an-activity}

È possibile aggiungere JavaScript durante l’inizializzazione di un’attività del flusso di lavoro. Questa operazione può essere eseguita nella scheda **[!UICONTROL Advanced]** dell&#39;attività.

Per semplificare l’individuazione del flusso di lavoro, si consiglia di utilizzare i doppi trattini all’inizio e alla fine dell’etichetta di attività, come segue: — La mia etichetta —.

### Segnale {#signal}

Nella maggior parte dei casi, non saprai da dove viene chiamato il segnale. Per evitare questo problema, utilizzare il campo **[!UICONTROL Comment]** nella scheda **[!UICONTROL Advanced]** dell&#39;attività del segnale per documentare l&#39;origine prevista di un segnale per questa attività.

![](assets/workflow-signal-bp.png)

## Aggiornamento del flusso di lavoro {#workflow-update}

Un flusso di lavoro di produzione non deve essere aggiornato direttamente. A meno che il processo non consista nella creazione di una campagna con flussi di lavoro basati su modelli, i processi devono prima essere testati in un ambiente di sviluppo. Dopo questa convalida, il flusso di lavoro può essere distribuito e avviato in produzione.

Eseguire tutti i test in ambienti di sviluppo o di staging, non in ambienti di produzione. In tal caso, non è possibile garantire la prestazione.

I flussi di lavoro archiviati possono essere mantenuti su piattaforme di sviluppo o di test, in una cartella Archiviata, ma l’ambiente di produzione deve rimanere il più pulito possibile. I flussi di lavoro precedenti devono essere rimossi dall’ambiente di produzione se sono inattivi.
