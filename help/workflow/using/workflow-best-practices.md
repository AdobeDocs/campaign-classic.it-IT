---
product: campaign
title: Best practice per i flussi di lavoro
description: Scopri le best practice per i flussi di lavoro per Campaign
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 6%

---

# Best practice per i flussi di lavoro{#workflow-best-practices}

## Esecuzione e prestazioni {#execution-and-performance}

Di seguito sono elencate le linee guida generali sull’ottimizzazione delle prestazioni di Campaign, incluse le best practice da applicare ai flussi di lavoro.

Le linee guida per la risoluzione dei problemi relativi all’esecuzione dei flussi di lavoro sono disponibili anche in [questa sezione](../../production/using/workflow-execution.md).

### Registri {#logs}

Il metodo JavaScript **[!UICONTROL logInfo()]** è una soluzione eccellente per il debug di un flusso di lavoro. È utile ma deve essere utilizzato con attenzione, soprattutto per le attività che vengono spesso eseguite: può sovraccaricare i registri e aumentare significativamente le dimensioni della tabella di registro. Ma potrebbe anche essere necessario più di **[!UICONTROL logInfo()]**.

Sono disponibili due soluzioni aggiuntive per:

* **Mantenere il risultato delle popolazioni intermedie tra due esecuzioni**

   Questa opzione consente di mantenere tabelle temporanee tra due esecuzioni di un flusso di lavoro. È disponibile nella scheda **[!UICONTROL General]** delle proprietà del flusso di lavoro e può essere utilizzato a scopo di sviluppo e test per monitorare i dati e verificare i risultati. Puoi utilizzare questa opzione negli ambienti di sviluppo ma non mai negli ambienti di produzione. Mantenere tabelle temporanee potrebbe comportare un aumento significativo delle dimensioni del database e, in ultima analisi, il raggiungimento del limite di dimensione. Inoltre, rallenterà il backup.

   Vengono mantenute solo le tabelle di lavoro dell’ultima esecuzione del flusso di lavoro. Le tabelle di lavoro delle esecuzioni precedenti vengono eliminate dal flusso di lavoro **[!UICONTROL cleanup]**, che viene eseguito su base giornaliera.

   >[!CAUTION]
   >
   >Questa opzione non deve mai essere selezionata in un flusso di lavoro di produzione. Questa opzione viene utilizzata per analizzare i risultati ed è progettata solo a scopo di test e quindi deve essere utilizzata solo negli ambienti di sviluppo o di staging.

* **Registra query SQL nel giornale di registrazione**

   Disponibile nella scheda **[!UICONTROL Execution]** delle proprietà del flusso di lavoro, questa opzione registra tutte le query SQL generate dallo strumento dalle diverse attività. È un buon modo per vedere cosa viene effettivamente eseguito dalla piattaforma. Tuttavia, questa opzione deve essere utilizzata solo temporaneamente durante lo sviluppo e non deve essere attivata in produzione.

Elimina i log quando non sono più necessari. La cronologia del flusso di lavoro non viene eliminata automaticamente: tutti i messaggi vengono conservati per impostazione predefinita. La cronologia può essere eliminata dal menu **[!UICONTROL File > Actions]** o facendo clic sul pulsante Azioni nella barra degli strumenti sopra l’elenco. Selezionare Elimina cronologia.
Per informazioni su come eliminare i registri, consulta questa [documentazione](../../workflow/using/starting-a-workflow.md).

### Pianificazione del flusso di lavoro {#workflow-planning}

* Cerca di mantenere un livello di attività stabile durante il giorno ed evita picchi per evitare che l&#39;istanza si sovraccarichi. A questo scopo, distribuisci gli orari di inizio del flusso di lavoro in modo uniforme durante l’intera giornata.
* Pianifica il caricamento dei dati in un giorno per ridurre il contenzioso sulle risorse.
* I flussi di lavoro lunghi possono avere un impatto potenzialmente sulle risorse del server e del database. Dividi i flussi di lavoro più lunghi per ridurre il tempo di elaborazione.
* Per ridurre i tempi di esecuzione generali, sostituisci le attività che richiedono molto tempo con attività semplificate e più veloci.
* Evita di eseguire più di 20 flussi di lavoro contemporaneamente. Quando vengono eseguiti contemporaneamente troppi flussi di lavoro, il sistema può esaurire le risorse e diventare instabile. Per ulteriori informazioni sul motivo per cui il flusso di lavoro potrebbe non essere avviato, consulta questo [articolo](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### Esecuzione di un flusso di lavoro {#workflow-execution}

È consigliabile non pianificare l’esecuzione di un flusso di lavoro per più di 15 minuti, in quanto potrebbe impedire le prestazioni complessive del sistema e creare blocchi nel database.

Evita di lasciare i flussi di lavoro in pausa. Se crei un flusso di lavoro temporaneo, assicurati che sia in grado di terminare correttamente e di non rimanere in uno stato **[!UICONTROL paused]**. Se viene messo in pausa, significa che è necessario mantenere le tabelle temporanee e quindi aumentare le dimensioni del database. Assegna le autorità di vigilanza del flusso di lavoro in Proprietà flusso di lavoro per inviare un avviso in caso di errore o interruzione di un flusso di lavoro da parte del sistema.

Per evitare che i flussi di lavoro siano in pausa:

* Controlla regolarmente i tuoi flussi di lavoro per assicurarti che non ci siano errori imprevisti.
* Semplifica i tuoi flussi di lavoro, ad esempio suddividendoli in flussi di lavoro di grandi dimensioni in diversi flussi di lavoro. Puoi utilizzare le attività **[!UICONTROL External signal]** per attivarne l’esecuzione in base all’esecuzione di altri flussi di lavoro.
* Evita di disabilitare le attività con i flussi nei flussi di lavoro lasciando i thread aperti e portando a numerose tabelle temporanee che possono occupare molto spazio. Non mantenere le attività negli stati **[!UICONTROL Do not enable]** o **[!UICONTROL Enable but do not execute]** nei flussi di lavoro.

Inoltre, interrompi i flussi di lavoro non utilizzati. I flussi di lavoro che continuano a essere in esecuzione mantengono le connessioni al database.

Utilizza l’arresto incondizionato solo nei casi più rari. Non utilizzare questa azione regolarmente. La mancata chiusura delle connessioni generate dai flussi di lavoro al database influisce sulle prestazioni.

### Esegui nell&#39;opzione del motore {#execute-in-the-engine-option}

Nella finestra **[!UICONTROL Workflow properties]** non selezionare mai l&#39;opzione **[!UICONTROL Execute in the engine]**. Quando questa opzione è abilitata, il flusso di lavoro ha la priorità e tutti gli altri flussi di lavoro vengono interrotti dal motore del flusso di lavoro fino al termine di questo.

![](assets/wf-execute-in-engine.png)

## Proprietà del flusso di lavoro {#workflow-properties}

### Cartelle del flusso di lavoro {#workflow-folders}

Adobe consiglia di creare i flussi di lavoro in una cartella dedicata.

Se il flusso di lavoro influisce sull’intera piattaforma (ad esempio, sui processi di pulizia), puoi aggiungere una sottocartella nella cartella **[!UICONTROL Technical Workflows]** incorporata.

### Denominazione del flusso di lavoro {#workflow-naming}

Poiché ciò ne semplifica la ricerca e la risoluzione dei problemi se non stanno ottenendo le prestazioni previste, Adobe consiglia di assegnare ai flussi di lavoro nomi ed etichette corretti: compila il campo di descrizione del flusso di lavoro per riepilogare il processo da eseguire in modo tale che l’operatore possa comprenderlo facilmente.

Se il flusso di lavoro fa parte di un processo che coinvolge più flussi di lavoro, puoi essere esplicito quando inserisci un’etichetta; l’utilizzo dei numeri è un ottimo modo per ordinare i flussi di lavoro (per Etichetta).

Ad esempio:

* 001 - Importazione - Destinatari importazione
* 002 - Importazione - Vendite all&#39;importazione
* 003 - Importazione - Dettagli delle vendite all&#39;importazione
* 010 - Esportazione - Registri di consegna delle esportazioni
* 011 - Esportazione - Registri di tracciamento delle esportazioni

### Gravità del flusso di lavoro {#workflow-severity}

Puoi configurare la gravità di un flusso di lavoro nelle proprietà del flusso di lavoro, nella scheda **[!UICONTROL Execution]** :

* Normale
* Produzione
* Critico

Fornire queste informazioni durante la creazione di un flusso di lavoro ti aiuterà a comprendere la gravità del processo configurato.

Questa opzione non ha alcun impatto funzionale sui flussi di lavoro diversi dai flussi di lavoro delle campagne.

I flussi di lavoro delle campagne (flussi di lavoro creati come parte di una campagna/operazione) con una gravità maggiore vengono eseguiti in priorità nel caso in cui la campagna abbia molti processi che dovrebbero essere eseguiti contemporaneamente. Per impostazione predefinita, solo 10 processi possono essere eseguiti contemporaneamente in una campagna, in base all&#39;opzione NmsOperation_LimitConcurrency. Ad esempio, se una campagna contiene 25 flussi di lavoro, i flussi di lavoro con una maggiore gravità verranno eseguiti nel primo pool di 10 processi.

### Monitoraggio del flusso di lavoro {#workflow-monitoring}

Per ricevere avvisi in caso di errore, è necessario monitorare tutti i flussi di lavoro pianificati in esecuzione su ambienti di produzione.

Nelle proprietà del flusso di lavoro, seleziona un gruppo di supervisori, il gruppo predefinito **[!UICONTROL Workflow supervisors]** o un gruppo personalizzato. Assicurati che almeno un operatore appartenga a questo gruppo, con un&#39;e-mail impostata.

Prima di iniziare a creare un flusso di lavoro, ricorda di definire i supervisori del flusso di lavoro. Saranno informati via e-mail in caso di errori. Per ulteriori informazioni, consulta [Gestione degli errori](../../workflow/using/monitoring-workflow-execution.md#managing-errors).

Controlla regolarmente la scheda **[!UICONTROL Monitoring]** per visualizzare lo stato complessivo dei flussi di lavoro attivi. Per ulteriori informazioni, consulta [Sorveglianza istanza](../../workflow/using/monitoring-workflow-execution.md#instance-supervision).

Workflow HeatMap consente agli amministratori della piattaforma Adobe Campaign di monitorare il carico sull&#39;istanza e pianificare i flussi di lavoro di conseguenza. Per ulteriori informazioni, consulta [Monitoraggio del flusso di lavoro](../../workflow/using/heatmap.md).

## Utilizzo delle attività {#using-activities}

>[!CAUTION]
>
>Puoi copiare e incollare le attività all’interno di uno stesso flusso di lavoro. Tuttavia, si sconsiglia di copiare e incollare le attività tra flussi di lavoro diversi. Alcune impostazioni collegate ad attività come Consegne e Scheduler potrebbero causare conflitti ed errori durante l’esecuzione del flusso di lavoro di destinazione. Ti consigliamo invece di eseguire flussi di lavoro **Duplica**. Per ulteriori informazioni, consulta [Duplicazione dei flussi di lavoro](../../workflow/using/building-a-workflow.md#duplicating-workflows).

### Nome dell’attività {#name-of-the-activity}

Durante lo sviluppo del flusso di lavoro, tutte le attività avranno un nome, così come tutti gli oggetti Adobe Campaign. Anche se il nome viene generato dallo strumento, al momento della configurazione è consigliabile rinominarlo con un nome esplicito. Il rischio di farlo in un secondo momento è che possa interrompere il flusso di lavoro con le attività utilizzando il nome di un’altra attività precedente. Quindi sarebbe difficile aggiornare i nomi in seguito.

Il nome dell’attività si trova nella scheda **[!UICONTROL Advanced]** . Non lasciarle denominate **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]**, ma fornirle nomi espliciti come **[!UICONTROL querySubscribedRecipients]**. Questo nome verrà visualizzato nel giornale di registrazione e, se applicabile, nei log SQL, e questo aiuterà a eseguire il debug del flusso di lavoro durante la configurazione.

### Prima e ultima attività {#first-and-last-activities}

* Avvia sempre il flusso di lavoro con un’attività **[!UICONTROL Start]** o **[!UICONTROL Scheduler]** . Se necessario, puoi anche utilizzare un’attività **[!UICONTROL External signal]** .
* Durante la creazione del flusso di lavoro, utilizza una sola attività **[!UICONTROL Scheduler]** per ramo. Se lo stesso ramo di un flusso di lavoro include più pianificatori (collegati tra loro), il numero di attività da eseguire verrà moltiplicato in modo esponenziale, il che sovraccaricherebbe notevolmente il database. Questa regola si applica anche a tutte le attività con una scheda **[!UICONTROL Scheduling & History]** . Ulteriori informazioni su [Pianificazione](../../workflow/using/scheduler.md).

   ![](assets/wf-scheduler.png)

* Utilizza le attività **[!UICONTROL End]** per ogni flusso di lavoro. Questo consente ad Adobe Campaign di liberare spazio temporaneo utilizzato per i calcoli all’interno dei flussi di lavoro. Per ulteriori informazioni, consulta: [Start ed End](../../workflow/using/start-and-end.md).

### Javascript all&#39;interno di un&#39;attività {#javascript-within-an-activity}

È possibile aggiungere JavaScript durante l’inizializzazione di un’attività del flusso di lavoro. Questo può essere fatto nella scheda **[!UICONTROL Advanced]** di un’attività.

Per semplificare lo spotting del flusso di lavoro, è consigliabile utilizzare trattini doppi all’inizio e alla fine dell’etichetta dell’attività, come segue: — La mia etichetta —

### Segnale {#signal}

Nella maggior parte dei casi, non si sa da dove viene richiamato il segnale. Per evitare questo problema, utilizza il campo **[!UICONTROL Comment]** all&#39;interno della scheda **[!UICONTROL Advanced]** dell&#39;attività del segnale per documentare l&#39;origine prevista di un segnale per questa attività.

![](assets/workflow-signal-bp.png)

## Aggiornamento del flusso di lavoro {#workflow-update}

Un flusso di lavoro di produzione non deve essere aggiornato direttamente. A meno che il processo non consista nella creazione di una campagna con flussi di lavoro basati su modelli, i processi devono prima essere testati in un ambiente di sviluppo. Dopo questa convalida, il flusso di lavoro può essere distribuito e avviato in produzione.

Esegui tutti i test negli ambienti di sviluppo o di staging, non negli ambienti di produzione. In tal caso non è possibile garantire prestazioni.

I flussi di lavoro archiviati possono essere conservati su piattaforme di sviluppo o di test, in una cartella archiviata, ma l&#39;ambiente di produzione dovrebbe rimanere il più pulito possibile. I vecchi flussi di lavoro devono essere rimossi dall’ambiente di produzione se sono inattivi.
