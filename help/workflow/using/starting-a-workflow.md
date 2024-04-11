---
product: campaign
title: Avviare un flusso di lavoro
description: Scopri come avviare un flusso di lavoro e scoprire i flussi di lavoro, la barra degli strumenti delle azioni e il menu di scelta rapida
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 1%

---

# Avviare un flusso di lavoro {#starting-a-workflow}



Un workflow viene sempre avviato manualmente. Quando viene avviato, può tuttavia rimanere inattivo a seconda delle informazioni specificate tramite una pianificazione (vedi [Scheduler](scheduler.md)) o pianificazione delle attività.

Azioni relative all’esecuzione del flusso di lavoro di targeting (avvio, arresto, pausa, ecc.) sono **asincrono** processi: l’ordine viene registrato e diventa effettivo non appena il server è disponibile per applicarlo.

La barra degli strumenti consente di avviare e tenere traccia dell’esecuzione del flusso di lavoro.

L’elenco delle opzioni disponibili nella sezione **[!UICONTROL Actions]** e il menu di scelta rapida sono descritti di seguito.

>[!IMPORTANT]
>
>Tieni presente che, quando un operatore esegue un’azione su un flusso di lavoro (avvio, arresto, pausa, ecc.), l’azione non viene eseguita immediatamente, ma viene inserita in una coda per essere elaborata da [modulo flusso di lavoro](architecture.md).

## Barra delle azioni {#actions-toolbar}

I pulsanti della barra degli strumenti sono descritti in questo [sezione](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). Il **[!UICONTROL Actions]** consente di accedere a opzioni di esecuzione aggiuntive per intervenire su flussi di lavoro selezionati. È inoltre possibile utilizzare **[!UICONTROL File > Actions]** oppure fare clic con il pulsante destro del mouse su un flusso di lavoro e selezionare **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  Questa azione ti consente di avviare l’esecuzione di un flusso di lavoro: un flusso di lavoro che **Completato**, **In fase di modifica** o **In pausa** modifica lo stato in **Avviato**. Il motore del flusso di lavoro gestisce quindi l’esecuzione di questo flusso di lavoro. Se il flusso di lavoro è stato sospeso, viene ripreso; in caso contrario, il flusso di lavoro viene avviato dall’inizio e le attività iniziali vengono attivate.

  L’avvio è asincrono: la richiesta viene salvata ed elaborata il prima possibile da un server del flusso di lavoro.

* **[!UICONTROL Pause]**

  Questa azione imposta lo stato del flusso di lavoro su **In pausa**. Nessuna attività viene attivata finché il flusso di lavoro non viene ripreso; tuttavia, le operazioni in corso non vengono sospese.

* **[!UICONTROL Stop]**

  Questa azione interrompe un flusso di lavoro attualmente in esecuzione. Lo stato dell’istanza è impostato su **Completato**. Se possibile, le operazioni in corso vengono interrotte. Le importazioni e le query SQL vengono annullate immediatamente.

  >[!IMPORTANT]
  >
  >L’arresto di un flusso di lavoro è un processo asincrono: la richiesta viene registrata, quindi il server o i server del flusso di lavoro annullano le operazioni in corso. L&#39;arresto di un&#39;istanza del flusso di lavoro può quindi richiedere tempo, soprattutto se il flusso di lavoro è in esecuzione su più server, ognuno dei quali deve assumere il controllo per annullare le attività in corso. Per evitare problemi, attendi il completamento dell’operazione di arresto e non eseguire più richieste di arresto sullo stesso flusso di lavoro.

* **[!UICONTROL Unconditional stop]**

  Questa opzione cambia lo stato del flusso di lavoro in **[!UICONTROL Finished]**. Questa azione deve essere utilizzata solo come ultima risorsa se il normale processo di arresto non riesce dopo alcuni minuti. Utilizzare l&#39;interruzione incondizionata solo se si è certi che non vi siano processi di flusso di lavoro effettivi in corso.

  >[!CAUTION]
  >
  >Questa opzione è riservata agli utenti esperti.

* **[!UICONTROL Restart]**

  Questa azione si interrompe e riavvia il flusso di lavoro. Nella maggior parte dei casi, consente un riavvio più rapido. È inoltre utile automatizzare il riavvio quando l’arresto richiede un certo periodo di tempo, perché il comando &quot;Interrompi&quot; non è disponibile quando il flusso di lavoro viene arrestato.

  Il **[!UICONTROL Start / Pause / Stop / Restart]** Le azioni sono disponibili anche tramite le icone di esecuzione nella barra degli strumenti. Per ulteriori informazioni, consulta questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

  Questa azione ti consente di eliminare la cronologia del flusso di lavoro. Per ulteriori informazioni, consulta [Rimozione dei registri](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

  Questa opzione consente di avviare il flusso di lavoro in modalità simulazione anziché in modalità reale. Ciò significa che quando si attiva questa modalità, vengono eseguite solo le attività che non influiscono sul database o sul file system (ad esempio **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, ecc.). Attività che hanno un impatto (ad es. **[!UICONTROL Export]**, **[!UICONTROL Import]**, ecc.) così come quelli successivi (nello stesso ramo) non vengono eseguiti.

* **[!UICONTROL Execute pending tasks now]**

  Questa azione ti consente di avviare tutte le attività in sospeso il prima possibile. Per avviare un’attività specifica, fai clic con il pulsante destro del mouse sulla relativa attività e seleziona **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Save as template]**

  Questa azione consente di creare un nuovo modello di workflow basato sul workflow selezionato. È necessario specificare la cartella in cui verrà salvata (nel **[!UICONTROL Folder]** ).

  Il **[!UICONTROL Mass update of selected lines]** e **[!UICONTROL Merge selected lines]** opzioni sono opzioni di piattaforma generiche disponibili in tutti **[!UICONTROL Actions]** menu. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/updating-data.md).


## Best practice per l’esecuzione dei flussi di lavoro {#workflow-execution-best-practices}

**Non pianificare l&#39;esecuzione di un flusso di lavoro ogni 15 minuti** perché potrebbe ostacolare le prestazioni complessive del sistema e creare blocchi nel database.

**Evitare di lasciare i flussi di lavoro in stato di pausa**. Se crei un flusso di lavoro temporaneo, assicurati che possa terminare correttamente e non rimanere in un **[!UICONTROL paused]** stato. Se viene messo in pausa, implicherebbe la necessità di mantenere le tabelle temporanee e quindi aumentare le dimensioni del database. Assegna supervisori flusso di lavoro in Proprietà flusso di lavoro per inviare un avviso quando un flusso di lavoro non riesce o viene messo in pausa dal sistema.

Per evitare che i flussi di lavoro si trovino in stato di pausa:

* Controlla i flussi di lavoro regolarmente per assicurarti che non si verifichino errori imprevisti.
* Mantieni i flussi di lavoro il più semplici possibile, ad esempio suddividendo flussi di lavoro di grandi dimensioni in diversi flussi di lavoro. È possibile utilizzare **[!UICONTROL External signal]** Le attività attivano la loro esecuzione in base all’esecuzione di altri flussi di lavoro.
* Evita di disabilitare le attività con i flussi nei flussi di lavoro, lasciando aperti i thread e portando a molte tabelle temporanee che possono occupare molto spazio. Non mantenere le attività in **[!UICONTROL Do not enable]** o **[!UICONTROL Enable but do not execute]** nei flussi di lavoro.

**Interrompere i flussi di lavoro inutilizzati**. I flussi di lavoro in esecuzione gestiscono le connessioni al database.

**Utilizza l’interruzione incondizionata solo nei casi più rari**. Non utilizzi questa azione regolarmente. La mancata esecuzione di una chiusura pulita delle connessioni generate dai flussi di lavoro al database influisce sulle prestazioni.

**Non eseguire più richieste di arresto sullo stesso flusso di lavoro**. L’arresto di un flusso di lavoro è un processo asincrono: la richiesta viene registrata, quindi il server o i server del flusso di lavoro annullano le operazioni in corso. L&#39;arresto di un&#39;istanza del flusso di lavoro può quindi richiedere tempo, soprattutto se il flusso di lavoro è in esecuzione su più server, ognuno dei quali deve assumere il controllo per annullare le attività in corso. Per evitare problemi, attendi il completamento dell’operazione di arresto ed evita di arrestare più volte un flusso di lavoro.

## Menu di scelta rapida {#right-click-menu}

Quando sono selezionate una o più attività del flusso di lavoro, puoi fare clic con il pulsante destro del mouse per intervenire sulla selezione.

![](assets/contextual_menu.png)

Nel menu di scelta rapida sono disponibili le seguenti opzioni:

**[!UICONTROL Open]**: questa opzione ti consente di accedere alle proprietà dell’attività.

**[!UICONTROL Display logs:]** questa opzione consente di visualizzare il registro di esecuzione dell’attività per l’attività selezionata. Fai riferimento a [Visualizzazione dei registri](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** questa azione ti consente di avviare le attività in sospeso il prima possibile.

**[!UICONTROL Workflow restart from a task:]** questa opzione consente di riavviare il flusso di lavoro utilizzando i risultati precedentemente archiviati per questa attività.

**[!UICONTROL Cut/Copy/Paste/Delete:]** queste opzioni consentono di tagliare, copiare, incollare ed eliminare le attività.

**[!UICONTROL Copy as bitmap:]** questa opzione ti consente di acquisire una schermata di tutte le attività.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** queste opzioni sono disponibili anche nel **[!UICONTROL Advanced]** delle proprietà dell’attività. Sono descritte in dettaglio [Esecuzione](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** consente di salvare o annullare le modifiche apportate a un flusso di lavoro.

>[!NOTE]
>
>Puoi selezionare un gruppo di attività e applicare uno di questi comandi.

Il menu di scelta rapida è descritto anche in questo [sezione](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
