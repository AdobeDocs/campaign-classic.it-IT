---
solution: Campaign Classic
product: campaign
title: Procedure consigliate per i flussi di lavoro
description: Best practice per i flussi di lavoro delle campagne
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 5%

---


# Best practice per i flussi di lavoro{#workflow-best-practices}

## Esecuzione e prestazioni {#execution-and-performance}

Di seguito sono elencate le linee guida generali sull&#39;ottimizzazione delle prestazioni di Campaign, comprese le best practice da applicare ai flussi di lavoro.

Le linee guida per la risoluzione dei problemi relativi all&#39;esecuzione dei flussi di lavoro sono disponibili anche in [questa sezione](../../production/using/workflow-execution.md).

### Registri {#logs}

Il metodo JavaScript **[!UICONTROL logInfo()]** è una soluzione ideale per il debug di un flusso di lavoro. È utile, ma deve essere utilizzato con attenzione, soprattutto per le attività che vengono eseguite frequentemente: può sovraccaricare i registri e aumentare notevolmente la dimensione della tabella di registro. Ma potrebbe essere necessario anche più di **[!UICONTROL logInfo()]**.

Sono disponibili due soluzioni aggiuntive per:

* **Mantenere il risultato di popolazioni provvisorie tra due esecuzioni**

   Questa opzione consente di mantenere tabelle temporanee tra due esecuzioni di un flusso di lavoro. È disponibile nella scheda **[!UICONTROL General]** delle proprietà del flusso di lavoro e può essere utilizzata per lo sviluppo e lo scopo del test per monitorare i dati e verificare i risultati. Questa opzione può essere utilizzata in ambienti di sviluppo, ma non in ambienti di produzione. Mantenere tabelle temporanee potrebbe comportare un aumento significativo delle dimensioni del database e, in ultima istanza, il raggiungimento del limite di dimensioni. Inoltre, rallenterà il backup.

   Vengono mantenute solo le tabelle di lavoro dell&#39;ultima esecuzione del flusso di lavoro. Le tabelle di lavoro delle precedenti esecuzioni vengono eliminate dal flusso di lavoro **[!UICONTROL cleanup]**, che viene eseguito su base giornaliera.

   >[!CAUTION]
   >
   >Questa opzione non deve mai essere selezionata in un flusso di lavoro di produzione. Questa opzione è utilizzata per analizzare i risultati ed è progettata solo a scopo di test e pertanto deve essere utilizzata solo in ambienti di sviluppo o di pre-produzione.

* **Registra query SQL nel giornale di registrazione**

   Disponibile nella scheda **[!UICONTROL Execution]** delle proprietà del flusso di lavoro, questa opzione registra tutte le query SQL generate dallo strumento dalle diverse attività. È un buon modo per vedere cosa viene effettivamente eseguito dalla piattaforma. Tuttavia, questa opzione deve essere utilizzata solo temporaneamente durante lo sviluppo e non deve essere attivata in fase di produzione.

Rimuovere i registri quando non sono più necessari. La cronologia del flusso di lavoro non viene eliminata automaticamente: tutti i messaggi vengono conservati per impostazione predefinita. La cronologia può essere eliminata dal menu **[!UICONTROL File > Actions]** o facendo clic sul pulsante Azioni nella barra degli strumenti sopra l&#39;elenco. Selezionare Elimina cronologia.
Per informazioni su come eliminare i registri, consultare la [documentazione](../../workflow/using/starting-a-workflow.md).

### Pianificazione del flusso di lavoro {#workflow-planning}

* Cercate di mantenere un livello di attività stabile durante il giorno ed evitare picchi per evitare che l&#39;istanza si sovraccarichi. A tal fine, distribuite gli orari di inizio del flusso di lavoro in modo uniforme durante l&#39;intera giornata.
* Pianificare il caricamento dei dati in un giorno successivo per ridurre il contenzioso sulle risorse.
* Flussi di lavoro lunghi possono avere un impatto potenziale sulle risorse del server e del database. Suddividere i flussi di lavoro più lunghi per ridurre i tempi di elaborazione.
* Per ridurre i tempi di esecuzione complessivi, sostituisci le attività che richiedono tempo con attività semplificate e più veloci.
* Evitate di eseguire più di 20 flussi di lavoro contemporaneamente. Se vengono eseguiti contemporaneamente troppi flussi di lavoro, il sistema può esaurire le risorse e diventare instabile. Per ulteriori informazioni sul motivo per cui il flusso di lavoro potrebbe non avviarsi, fare riferimento a questo [articolo](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### Esecuzione di un flusso di lavoro {#workflow-execution}

Si consiglia di non pianificare un flusso di lavoro per eseguire più di 15 minuti, in quanto potrebbe impedire le prestazioni complessive del sistema e creare blocchi nel database.

Evitare di lasciare i flussi di lavoro in stato di pausa. Se create un flusso di lavoro temporaneo, accertatevi che sia in grado di completare correttamente e non di rimanere in uno stato **[!UICONTROL paused]**. Se viene messa in pausa, significa che è necessario mantenere le tabelle temporanee e quindi aumentare la dimensione del database. Assegnare i supervisori del flusso di lavoro in Proprietà flusso di lavoro per inviare un avviso in caso di errore di un flusso di lavoro o pausa del sistema.

Per evitare che i flussi di lavoro vengano messi in pausa:

* Controlla regolarmente i tuoi flussi di lavoro per evitare errori imprevisti.
* Semplificate al massimo i flussi di lavoro, ad esempio suddividendo flussi di lavoro di grandi dimensioni in diversi flussi di lavoro. È possibile utilizzare le attività **[!UICONTROL External signal]** per attivarne l&#39;esecuzione in base all&#39;esecuzione di altri flussi di lavoro.
* Evitare di disabilitare le attività con flussi di lavoro che consentono di lasciare i thread aperti e di generare numerose tabelle temporanee che richiedono molto spazio. Non mantenere attività negli stati **[!UICONTROL Do not enable]** o **[!UICONTROL Enable but do not execute]** dei flussi di lavoro.

Inoltre, interrompete i flussi di lavoro inutilizzati. I flussi di lavoro che mantengono in esecuzione mantengono le connessioni al database.

Utilizzate l&#39;interruzione non condizionale solo nei casi più rari. Non utilizzate questa azione su base regolare. La mancata chiusura delle connessioni generate dai flussi di lavoro al database ha un impatto sulle prestazioni.

### Esegui nell&#39;opzione del motore {#execute-in-the-engine-option}

Nella finestra **[!UICONTROL Workflow properties]**, non selezionare mai l&#39;opzione **[!UICONTROL Execute in the engine]**. Quando questa opzione è attivata, il flusso di lavoro ha la priorità e tutti gli altri flussi di lavoro vengono interrotti dal motore del flusso di lavoro fino al termine.

![](assets/wf-execute-in-engine.png)

## Proprietà del flusso di lavoro {#workflow-properties}

### Cartelle del flusso di lavoro {#workflow-folders}

 Adobe consiglia di creare i flussi di lavoro in una cartella dedicata.

Se il flusso di lavoro influisce sull’intera piattaforma (ad esempio, processi di pulizia), potete prendere in considerazione l’aggiunta di una sottocartella nella cartella **[!UICONTROL Technical Workflows]** incorporata.

### Denominazione del flusso di lavoro {#workflow-naming}

Poiché ciò ne semplifica la ricerca e la risoluzione dei problemi se non stanno ottenendo le prestazioni previste, Adobe consiglia di assegnare ai flussi di lavoro nomi ed etichette corretti: compila il campo di descrizione del flusso di lavoro per riepilogare il processo da eseguire in modo tale che l’operatore possa comprenderlo facilmente.

Se il flusso di lavoro fa parte di un processo che coinvolge più flussi di lavoro, puoi essere esplicito quando immetti un&#39;etichetta; l&#39;utilizzo di numeri è un ottimo modo per ordinare i flussi di lavoro (per Etichetta).

Ad esempio:

* 001 - Importazione - Destinatari importazione
* 002 - Importazione - Vendite all&#39;importazione
* 003 - Importazione - Dettagli vendita importazione
* 010 - Esporta - Registri di consegna delle esportazioni
* 011 - Esporta - Registri di registrazione delle esportazioni

### Gravità del flusso di lavoro {#workflow-severity}

Puoi configurare la gravità di un flusso di lavoro nelle proprietà del flusso di lavoro, nella scheda **[!UICONTROL Execution]**:

* Normale
* Produzione
* Critico

Fornire queste informazioni al momento della creazione di un flusso di lavoro vi aiuterà a comprendere la gravità del processo configurato.

Questa opzione non ha alcun impatto funzionale sui flussi di lavoro diversi dai flussi di lavoro delle campagne.

I flussi di lavoro delle campagne (flussi di lavoro creati nell’ambito di una campagna/operazione) con una gravità più elevata vengono eseguiti in priorità nel caso in cui la campagna contenga molti processi che dovrebbero essere eseguiti contemporaneamente. Per impostazione predefinita, solo 10 processi possono essere eseguiti contemporaneamente in una campagna, in base all&#39;opzione NmsOperation_LimitConcurrency. Ad esempio, se una campagna contiene 25 flussi di lavoro, i flussi di lavoro con una maggiore gravità verranno eseguiti nel primo pool di 10 processi.

### Monitoraggio del flusso di lavoro {#workflow-monitoring}

Tutti i flussi di lavoro pianificati in esecuzione in ambienti di produzione devono essere monitorati per essere avvisati in caso di errore.

Nelle proprietà del flusso di lavoro, selezionare un gruppo di supervisori, il gruppo predefinito **[!UICONTROL Workflow supervisors]** o un gruppo personalizzato. Accertatevi che almeno un operatore appartenga a questo gruppo, con un&#39;impostazione e-mail.

Prima di iniziare a creare un flusso di lavoro, occorre definire le autorità di supervisione del flusso di lavoro. In caso di errori, riceveranno una notifica tramite e-mail. Per ulteriori informazioni, vedere [Gestione degli errori](../../workflow/using/monitoring-workflow-execution.md#managing-errors).

Controllare regolarmente l&#39;universo **[!UICONTROL Monitoring]** per visualizzare lo stato complessivo dei flussi di lavoro attivi. Per ulteriori informazioni, vedere [Sorveglianza istanza](../../workflow/using/monitoring-workflow-execution.md#instance-supervision).

Workflow HeatMap consente agli amministratori  piattaforma Adobe Campaign di monitorare il carico sull&#39;istanza e pianificare i flussi di lavoro di conseguenza. Per ulteriori informazioni, vedere [Monitoraggio del flusso di lavoro](../../workflow/using/heatmap.md).

## Utilizzo delle attività {#using-activities}

>[!CAUTION]
>
>Potete copiare e incollare le attività all’interno di uno stesso flusso di lavoro. Tuttavia, non è consigliabile copiare le attività Incolla tra flussi di lavoro diversi. Alcune impostazioni associate ad attività quali Consegne e Utilità di pianificazione potrebbero causare conflitti ed errori durante l&#39;esecuzione del flusso di lavoro di destinazione. È stato invece consigliato di eseguire flussi di lavoro **Duplica**. Per ulteriori informazioni, vedere [Duplicazione dei flussi di lavoro](../../workflow/using/building-a-workflow.md#duplicating-workflows).

### Nome dell&#39;attività {#name-of-the-activity}

Durante lo sviluppo del flusso di lavoro, tutte le attività avranno un nome, così come tutti  oggetti Adobe Campaign. Mentre il nome viene generato dallo strumento, è consigliabile rinominarlo con un nome esplicito durante la configurazione. Il rischio di farlo in seguito è che interrompa il flusso di lavoro con le attività utilizzando il nome di un&#39;altra attività precedente. Sarebbe quindi difficile aggiornare i nomi successivamente.

Il nome dell&#39;attività si trova nella scheda **[!UICONTROL Advanced]**. Non lasciarle denominate **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]**, ma fornirle nomi espliciti come **[!UICONTROL querySubscribedRecipients]**. Questo nome verrà visualizzato nel giornale di registrazione, e se applicabile nei registri SQL, e questo aiuterà a eseguire il debug del flusso di lavoro durante la configurazione.

### Prima e ultima attività {#first-and-last-activities}

* Avvia sempre il flusso di lavoro con un&#39;attività **[!UICONTROL Start]** o **[!UICONTROL Scheduler]**. Se necessario, potete anche utilizzare un&#39;attività **[!UICONTROL External signal]**.
* Durante la creazione del flusso di lavoro, utilizzate una sola attività **[!UICONTROL Scheduler]** per ramo. Se lo stesso ramo di un flusso di lavoro include più pianificatori (collegati tra loro), il numero di attività da eseguire verrà moltiplicato in modo esponenziale, il che sovraccaricherebbe notevolmente il database. Questa regola si applica anche a tutte le attività con una scheda **[!UICONTROL Scheduling & History]**. Ulteriori informazioni su [Scheduling](../../workflow/using/scheduler.md).

   ![](assets/wf-scheduler.png)

* Utilizzate le attività **[!UICONTROL End]** per ogni flusso di lavoro. Questo consente  Adobe Campaign di liberare spazio temporaneo utilizzato per i calcoli all&#39;interno dei flussi di lavoro. Per ulteriori informazioni, consulta: [Inizio e fine](../../workflow/using/start-and-end.md).

### Javascript all&#39;interno di un&#39;attività {#javascript-within-an-activity}

Potrebbe essere necessario aggiungere JavaScript durante l&#39;inizializzazione di un&#39;attività del flusso di lavoro. Questo può essere fatto nella scheda **[!UICONTROL Advanced]** di un&#39;attività.

Per semplificare la ricerca del flusso di lavoro, si consiglia di utilizzare due trattini all&#39;inizio e alla fine dell&#39;etichetta dell&#39;attività, come segue: — La mia etichetta —

### Segnale {#signal}

Nella maggior parte dei casi, non si sa da dove viene chiamato il segnale. Per evitare questo problema, utilizzare il campo **[!UICONTROL Comment]** all&#39;interno della scheda **[!UICONTROL Advanced]** dell&#39;attività del segnale per documentare l&#39;origine prevista di un segnale per questa attività.

![](assets/workflow-signal-bp.png)

## Aggiornamento del flusso di lavoro {#workflow-update}

Un flusso di lavoro di produzione non deve essere aggiornato direttamente. A meno che il processo non consista nella creazione di una campagna con flussi di lavoro basati su modelli, i processi devono essere prima testati in un ambiente di sviluppo. Dopo questa convalida, il flusso di lavoro può essere distribuito e avviato in produzione.

Eseguire tutti i test in ambienti di sviluppo o di gestione temporanea, non in ambienti di produzione. In questo caso non è possibile garantire prestazioni.

I flussi di lavoro archiviati possono essere conservati su piattaforme di sviluppo o di prova, in una cartella archiviata, ma l&#39;ambiente di produzione dovrebbe essere il più pulito possibile. I vecchi flussi di lavoro devono essere rimossi dall&#39;ambiente di produzione se sono inattivi.
