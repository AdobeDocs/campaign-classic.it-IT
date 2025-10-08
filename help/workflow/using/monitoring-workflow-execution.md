---
product: campaign
title: Monitorare l’esecuzione di un flusso di lavoro
description: Monitorare l’esecuzione di un flusso di lavoro
feature: Workflows
hide: true
hidefromtoc: true
exl-id: d589180b-8e1d-4149-9b16-3f541018a41f
source-git-commit: 221e2ccdaadf793212fcacdf5e13823f1505f4dc
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 2%

---

# Monitorare l’esecuzione di un flusso di lavoro {#monitoring-workflow-execution}



Questa sezione contiene informazioni su come monitorare l’esecuzione dei flussi di lavoro.

Un caso d&#39;uso su come creare un flusso di lavoro che consenta di monitorare lo stato di un set di flussi di lavoro &quot;in pausa&quot;, &quot;interrotti&quot; o &quot;con errori&quot; è disponibile anche in [questa sezione](supervising-workflows.md#supervising-workflows).

Inoltre, gli amministratori dell&#39;istanza possono utilizzare **Audit trail** per controllare le attività e le ultime modifiche apportate ai flussi di lavoro, lo stato dei flussi di lavoro. Per ulteriori informazioni, consulta [Guida alla produzione di Campaign Classic v7](../../production/using/audit-trail.md).

Ulteriori metodi di monitoraggio dei diversi processi di Campaign sono descritti nella [Guida alla produzione di Campaign Classic v7](../../production/using/monitoring-guidelines.md).

## Visualizzazione dell&#39;avanzamento {#displaying-progress}

Puoi monitorare l’esecuzione visualizzando l’avanzamento utilizzando l’icona appropriata sulla barra degli strumenti.

L&#39;icona **[!UICONTROL Display progress information]** consente di visualizzare lo stato e il risultato dell&#39;attività nella schermata di esecuzione.

![](assets/s_user_segmentation_toolbar_progr.png)

Quando questa opzione è selezionata, le attività eseguite vengono visualizzate in blu, le attività in sospeso lampeggiano, gli avvisi vengono visualizzati in arancione e gli errori in rosso. Questa opzione visualizza anche il risultato delle attività nella relativa transizione in uscita, seguito dall’etichetta del risultato definita nelle proprietà dell’attività e dalla durata del processo, se superiore a un secondo

![](assets/s_user_segmentation_results.png)

## Visualizzazione dei registri {#displaying-logs}

Il registro contiene la cronologia o l’audit trail del flusso di lavoro. Registra tutte le azioni dell’utente, tutte le operazioni eseguite e gli errori riscontrati. Puoi eseguire le seguenti azioni:

* Selezionare la scheda **[!UICONTROL Tracking]** nel dettaglio. Questo elenco contiene tutti i messaggi del flusso di lavoro.

  ![](assets/new-workflow-display-log-tab.png)

* Filtra i messaggi di registro per attività. A tale scopo, fare clic su **[!UICONTROL Display the tasks and the log]** sulla barra degli strumenti sopra il diagramma per visualizzare le schede **[!UICONTROL Log]** e **[!UICONTROL Tasks]** sotto il diagramma. Seleziona un’attività per visualizzare tutti i messaggi correlati. Questo elenco contiene tutti i messaggi quando non è selezionata alcuna attività.

  ![](assets/new-workflow-display-log-activity.png)

  >[!NOTE]
  >
  >Fare clic sullo sfondo del diagramma per deselezionare tutti gli elementi.

* Visualizza solo i messaggi collegati a una determinata attività. A tale scopo, selezionare la scheda **[!UICONTROL Tasks]**, quindi selezionare un&#39;attività nel diagramma per limitare l&#39;elenco. Fare doppio clic su un&#39;attività per visualizzare le informazioni; l&#39;ultima scheda della finestra contiene il registro.

  ![](assets/new-workflow-display-tasks-activity.png)

  Il pulsante **[!UICONTROL Details...]** consente di visualizzare tutte le informazioni aggiuntive sull&#39;esecuzione dell&#39;attività. Ad esempio, puoi visualizzare l’operatore di convalida e, se applicabile, il commento inserito durante l’approvazione, come nell’esempio seguente:

  ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>Il registro non viene eliminato al riavvio di un flusso di lavoro. Tutti i messaggi vengono conservati. Se desideri eliminare i messaggi di un’esecuzione precedente, devi eliminare la cronologia.

Il registro mostra l’elenco cronologico dei messaggi di esecuzione relativi alle attività del flusso di lavoro di targeting.

* Registro di una campagna di targeting

  Dopo aver eseguito una campagna di targeting, fare clic sulla scheda **[!UICONTROL Tracking]** per visualizzare la traccia di esecuzione.

  ![](assets/s_user_segmentation_journal.png)

  Vengono visualizzati tutti i messaggi della campagna: campagne eseguite, avvisi o errori.

* Registro di un’attività

  Puoi anche visualizzare il registro di esecuzione e i dettagli di ogni attività. Esistono due modi per farlo:

   1. Selezionare l&#39;attività di destinazione e fare clic sull&#39;icona **[!UICONTROL Display the tasks and the log]**.

      ![](assets/s_user_segmentation_show_logs.png)

      La sezione inferiore del diagramma mostra due schede: Registro e Attività.

      Le attività selezionate nel diagramma fungono da filtri nell&#39;elenco dei registri e delle attività.

      ![](assets/s_user_segmentation_logs.png)

   1. Fare clic con il pulsante destro del mouse sull&#39;attività di destinazione e selezionare **[!UICONTROL Display logs]**.

      ![](assets/s_user_segmentation_logs_menu.png)

      Il registro viene visualizzato in una finestra separata.

## Rimozione dei registri {#purging-the-logs}

La cronologia del flusso di lavoro non viene eliminata automaticamente: tutti i messaggi vengono conservati per impostazione predefinita. La cronologia può essere eliminata tramite il menu **[!UICONTROL File > Actions]** o facendo clic sul pulsante **[!UICONTROL Actions]** nella barra degli strumenti sopra l&#39;elenco. Seleziona **[!UICONTROL Purge history]**. Le opzioni disponibili nel menu **[!UICONTROL Actions]** sono descritte in dettaglio nella sezione [Actions toolbar](starting-a-workflow.md).

![](assets/purge_historique.png)

## Tabelle di lavoro e schema flusso di lavoro {#worktables-and-workflow-schema}

Il flusso di lavoro trasmette tabelle di lavoro che possono essere manipolate tramite determinate attività. Adobe Campaign consente di modificare, rinominare e arricchire le colonne delle tabelle di lavoro del flusso di lavoro tramite attività di gestione dati, ad esempio per allinearle alla nomenclatura in base alle esigenze del cliente, per raccogliere informazioni aggiuntive sul co-beneficiario di un contratto, ecc.

È inoltre possibile creare collegamenti tra varie dimensioni di lavoro e definire modifiche alle dimensioni. Ad esempio, per ogni contratto registrato nella banca dati, indicare nelle informazioni supplementari il titolare principale e utilizzare i dati dei cotitolari.

Le tabelle di lavoro del flusso di lavoro vengono eliminate automaticamente quando il flusso di lavoro viene passivo. Se si desidera conservare una tabella di lavoro, salvarla in un elenco tramite l&#39;attività **[!UICONTROL List update]** (fare riferimento a [Aggiornamento elenco](list-update.md)).

## Gestione degli errori {#managing-errors}

Quando si verifica un errore, il flusso di lavoro viene messo in pausa e l’attività in esecuzione quando si verifica l’errore lampeggia in rosso. Nella panoramica del flusso di lavoro, nella scheda **[!UICONTROL Monitoring]** - collegamento **[!UICONTROL Workflows]**, è possibile visualizzare solo i flussi di lavoro con errori, come illustrato di seguito.

![](assets/wf-global-view_filter_only_errors.png)

In Adobe Campaign Explorer, l&#39;elenco dei flussi di lavoro visualizza una colonna **[!UICONTROL Failed]** per impostazione predefinita.

![](assets/wf-explorer_errors_col.png)

Quando un flusso di lavoro è in errore, gli operatori appartenenti al gruppo di supervisione del flusso di lavoro ricevono una notifica via e-mail, purché il loro indirizzo e-mail sia elencato nel profilo. Questo gruppo è selezionato nel campo **[!UICONTROL Supervisor(s)]** delle proprietà del flusso di lavoro.

![](assets/wf-properties_select-supervisors.png)

Il contenuto della notifica è configurato nel modello predefinito **[!UICONTROL Workflow manager notification]**: questo modello è selezionato nella scheda **[!UICONTROL Execution]** delle proprietà del flusso di lavoro. La notifica mostra il nome del flusso di lavoro di errore e dell’attività interessata.

Esempio di notifica:

![](assets/wf-notification_error-msg.png)

Il collegamento ti consente di accedere alla console Adobe Campaign in modalità Web e di lavorare sul flusso di lavoro degli errori dopo aver effettuato l’accesso.

![](assets/wf-notification_error-console.png)

Puoi configurare il flusso di lavoro in modo che non vada in pausa e continui l’esecuzione in caso di errori. A tale scopo, modificare il flusso di lavoro **[!UICONTROL Properties]** e, nella sezione **[!UICONTROL Error management]**, selezionare l&#39;opzione **[!UICONTROL Ignore]** nel campo **[!UICONTROL In case of error]**. È quindi possibile specificare il numero di errori consecutivi che possono essere ignorati prima della messa in pausa del processo.

In questo caso, l’attività di errore viene interrotta. Questa modalità è particolarmente adatta per i flussi di lavoro progettati per ritentare la campagna in un secondo momento (azioni periodiche).

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>Puoi applicare questa configurazione singolarmente per ogni attività. A tale scopo, modificare le proprietà dell&#39;attività e selezionare la modalità di gestione degli errori nella scheda **[!UICONTROL Advanced]**.

Per ulteriori informazioni sulla risoluzione dei problemi di esecuzione dei flussi di lavoro, consulta la [Guida alla produzione di Campaign Classic v7](../../production/using/workflow-execution.md).

## Errori di elaborazione {#processing-errors}

Per quanto riguarda le attività, l&#39;opzione **[!UICONTROL Process errors]** visualizza una transizione specifica che verrà abilitata se viene generato un errore. In questo caso, il flusso di lavoro non entra in modalità di errore e l’esecuzione continua.

Gli errori presi in considerazione sono errori del file system (file non spostabile, directory non accessibile, ecc.).

Questa opzione non elabora gli errori relativi alla configurazione dell’attività, ovvero valori non validi. Gli errori relativi a una configurazione errata non abiliteranno questa transizione (la directory non esiste, ecc.).

Se un workflow viene messo in pausa (manualmente o automaticamente dopo un errore), il pulsante **[!UICONTROL Start]** riavvia l&#39;esecuzione del workflow nel punto in cui è stato interrotto. L’attività errata (o l’attività in pausa) verrà rieseguita. Le attività precedenti non vengono rieseguite.

Per eseguire nuovamente tutte le attività del flusso di lavoro, utilizzare il pulsante **[!UICONTROL Restart]**.

Se modifichi attività già eseguite, le modifiche non vengono prese in considerazione al riavvio dell’esecuzione del flusso di lavoro.

Se modifichi le attività non eseguite, queste vengono prese in considerazione al riavvio dell’esecuzione del flusso di lavoro.

Se modifichi le attività in pausa, le modifiche non possono essere prese in considerazione correttamente al riavvio del flusso di lavoro.

Se possibile, si consiglia di riavviare completamente il flusso di lavoro dopo aver eseguito le modifiche.

## Supervisione istanza {#instance-supervision}

La pagina **[!UICONTROL Instance supervision]** consente di visualizzare l&#39;attività del server Adobe Campaign e l&#39;elenco dei flussi di lavoro e delle consegne con errori.

Per accedere a questa pagina, passare alla scheda **[!UICONTROL Monitoring]** e fare clic sul collegamento **[!UICONTROL General view]**.

![](assets/wf-monitoring_from-homepage.png)

Per visualizzare tutti i workflow, fare clic sul collegamento **[!UICONTROL Workflows]**. Utilizza l’elenco a discesa per visualizzare i flussi di lavoro nella piattaforma in base al loro stato.

![](assets/wf-monitoring_edit-wf.png)

Fai clic sul collegamento con errori in un flusso di lavoro per aprirlo e visualizzarne il registro.

![](assets/wf-monitoring_edit-task-wf.png)

## Impedire esecuzioni simultanee multiple {#preventing-simultaneous-multiple-executions}

Un singolo flusso di lavoro può avere più esecuzioni in esecuzione contemporaneamente. In alcuni casi è necessario evitare che ciò si verifichi.

Ad esempio, puoi fare in modo che una pianificazione attivi l’esecuzione del flusso di lavoro ogni ora, ma a volte l’esecuzione dell’intero flusso di lavoro richiede più di un’ora. Potrebbe essere necessario saltare l’esecuzione se il flusso di lavoro è già in esecuzione.

Se hai un’attività di segnale all’inizio del flusso di lavoro, potresti voler saltare il segnale se il flusso di lavoro è in esecuzione.

Il principio generale è il seguente:

![](assets/workflow-reentrancy-protection-principle.png)

La soluzione consiste nell’utilizzare una variabile di istanza. Le variabili dell’istanza sono condivise da tutte le esecuzioni parallele dei flussi di lavoro.

Di seguito è riportato un semplice flusso di lavoro di test:

![](assets/wkf_simultaneous_execution1.png)

**[!UICONTROL Scheduler]** attiva un evento ogni minuto. La seguente attività **[!UICONTROL Test]** sta per testare la variabile di istanza **isRunning** per decidere se continuare o meno l&#39;esecuzione:

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning** è un nome di variabile scelto per questo esempio. Questa non è una variabile incorporata.

L&#39;attività immediatamente successiva al **[!UICONTROL Test]** nel ramo **yes** deve impostare la variabile di istanza nel relativo **script di inizializzazione**:

```
instance.vars.isRunning = true
```

L&#39;ultima attività nel ramo **yes** deve ripristinare la variabile su false nel relativo **script di inizializzazione**:

```
instance.vars.isRunning = false
```

Tieni presente che:

* Puoi controllare il valore corrente della variabile di istanza tramite la scheda **Variabili** nel flusso di lavoro **Proprietà**.
* Le variabili dell’istanza vengono reimpostate al riavvio di un flusso di lavoro.
* In JavaScript, un valore non definito è falso in un test, consentendo di testare la variabile di istanza anche prima di averla inizializzata.
* Per monitorare le attività non elaborate a causa di questo meccanismo, aggiungi un’istruzione di registrazione allo script di inizializzazione dell’endpoint &quot;no&quot;.

  ```
  logInfo("Workflow already running, parallel execution not allowed.");
  ```

Un caso d&#39;uso è presentato in questa sezione: [Coordinamento degli aggiornamenti dei dati](coordinating-data-updates.md).

## Manutenzione del database {#database-maintenance}

I flussi di lavoro utilizzano molte tabelle di lavoro che occupano spazio e finiscono per rallentare l’intera piattaforma se non vengono mantenuti. Per ulteriori informazioni sulla manutenzione del database, consulta questa [sezione](../../production/using/tables-to-maintain.md) .

Il flusso di lavoro **Database cleanup** accessibile tramite il nodo **Amministrazione > Produzione > Flussi di lavoro tecnici** consente di eliminare i dati obsoleti per evitare una crescita esponenziale del database. Il flusso di lavoro viene attivato automaticamente senza l’intervento dell’utente. Consulta la [Guida alla produzione di Campaign Classic v7](../../production/using/database-cleanup-workflow.md).

Puoi anche creare flussi di lavoro tecnici specifici per eliminare i dati non necessari che occupano spazio. Consulta la [Guida alla produzione di Campaign Classic v7](../../production/using/application-objects.md) e questa [sezione](#purging-the-logs).

## Gestione dei flussi di lavoro in pausa {#handling-of-paused-workflows}

Per impostazione predefinita, se un flusso di lavoro viene sospeso, le relative tabelle di lavoro non vengono mai eliminate. Dalla build 8880, i flussi di lavoro che sono stati in pausa per troppo tempo vengono automaticamente interrotti e le relative tabelle di lavoro vengono eliminate. Questo comportamento viene attivato come segue:

* I flussi di lavoro sospesi da più di 7 giorni vengono visualizzati come un avviso nel dashboard di monitoraggio (e nell’API di monitoraggio) e viene inviata una notifica al gruppo di supervisori.
* Lo stesso accade ogni settimana, quando viene attivato il flusso di lavoro tecnico **[!UICONTROL cleanupPausedWorkflows]**. Per ulteriori dettagli sul flusso di lavoro, consulta [questa sezione](delivery.md).
* Dopo 4 notifiche (ovvero un mese in stato di pausa per impostazione predefinita), il flusso di lavoro viene interrotto incondizionatamente. Dopo l’interruzione, nel flusso di lavoro viene visualizzato un registro. Le tabelle vengono eliminate all&#39;esecuzione successiva del flusso di lavoro **[!UICONTROL cleanup]**

Questi periodi possono essere configurati tramite l’opzione NmsServer_PausedWorkflowPeriod.

I supervisori del flusso di lavoro ricevono una notifica. Vengono avvisati anche il creatore e l’ultimo utente che ha modificato il flusso di lavoro. Gli amministratori non ricevono le notifiche.

## Filtrare i flussi di lavoro in base al loro stato {#filtering-workflows-status}

L&#39;interfaccia di Campaign Classic ti consente di monitorare lo stato di esecuzione di tutti i flussi di lavoro nell&#39;istanza utilizzando **visualizzazioni** predefinite. Per accedere a queste visualizzazioni, apri il nodo **[!UICONTROL Administration]** / **[!UICONTROL Audit]** / **[!UICONTROL Workflows Status]**.

Sono disponibili le seguenti viste:

* **[!UICONTROL Running]**: elenca tutti i flussi di lavoro in esecuzione.
* **[!UICONTROL Paused]**: elenca tutti i flussi di lavoro in pausa.
* **[!UICONTROL Failed]**: elenca tutti i flussi di lavoro non riusciti.
* **[!UICONTROL Start Pending]**: elenca tutti i flussi di lavoro in attesa di essere avviati dal processo operationMgt. Questa visualizzazione è disponibile solo con il pacchetto **Campagne di marketing**. Ulteriori informazioni nella [Guida all&#39;installazione di Campaign Classic v7](../../installation/using/installing-campaign-standard-packages.md)).

![](assets/workflow-monitoring-views.png)

Per impostazione predefinita, queste visualizzazioni sono accessibili nella cartella **[!UICONTROL Audit]**. Tuttavia, è possibile ricrearli nella posizione desiderata nella struttura delle cartelle. In questo modo, saranno disponibili per gli utenti standard senza alcun diritto di amministrazione.

Per eseguire questa operazione:

1. Fare clic con il pulsante destro del mouse sulla cartella in cui si desidera aggiungere la visualizzazione.
1. In **[!UICONTROL Add new folder]** / **[!UICONTROL Administration]**, selezionare la visualizzazione che si desidera aggiungere.
1. Una volta aggiunta la cartella alla struttura, accertati di configurarla come vista, in modo che vengano visualizzati tutti i flussi di lavoro, indipendentemente dalla cartella di origine. Per ulteriori informazioni su come configurare le visualizzazioni, consulta [questa sezione](../../platform/using/about-adobe-campaign-classic.md).

Oltre a queste visualizzazioni, puoi impostare cartelle di filtri che ti consentano di filtrare l’elenco dei flussi di lavoro in base al loro stato di esecuzione. Per eseguire questa operazione:

1. Accedere a una cartella di tipo workflow, quindi selezionare il menu **[!UICONTROL Filters]** / **[!UICONTROL Advanced filter]**.
1. Configura il filtro in modo che il campo **[!UICONTROL @status]** del flusso di lavoro sia uguale allo stato desiderato.
1. Salva e assegna un nome al filtro. Sarà quindi disponibile direttamente dall’elenco dei filtri.

![](assets/workflow-monitoring-filter.png)

Per ulteriori informazioni sui filtri, consulta la [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.
