---
solution: Campaign Classic
product: campaign
title: Proprietà del flusso di lavoro
description: Ulteriori informazioni sulle proprietà del flusso di lavoro Campaign
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# Proprietà del flusso di lavoro{#workflow-properties}

## Scheda Esecuzione {#execution-tab}

La scheda **[!UICONTROL Execution]** della finestra **[!UICONTROL Properties]** di un flusso di lavoro è suddivisa in 3 sezioni:

![](assets/wf_execution_tab.png)

### Scheduler {#scheduler}

Questa sezione viene visualizzata solo nei flussi di lavoro delle campagne.

* **[!UICONTROL Priority]**

   Il motore del flusso di lavoro elabora i flussi di lavoro da eseguire in base al criterio di priorità definito in questo campo. Ad esempio, tutti i flussi di lavoro con priorità **[!UICONTROL Average]** verranno eseguiti prima di quelli con priorità **[!UICONTROL Low]**.

* **[!UICONTROL Schedule execution for a time of low activity]**

   Questa opzione posticipa l&#39;inizio del flusso di lavoro a un periodo meno occupato. Alcuni flussi di lavoro possono essere costosi in termini di risorse per il motore del database. È consigliabile pianificare l&#39;esecuzione per un periodo di bassa attività (ad esempio di notte). I periodi di attività ridotti sono definiti nel **[!UICONTROL Processes on campaigns]** flusso di lavoro tecnico.

### Esecuzione {#execution}

* **[!UICONTROL Default affinity]**

   Se l&#39;installazione include diversi server di workflow, utilizzare questo campo per scegliere il computer su cui verrà eseguito il flusso di lavoro. Se il valore definito in questo campo non esiste su alcun server, il flusso di lavoro rimarrà in sospeso.

   Fare riferimento a questa sezione [](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL History in days]**

   Nelle tabelle di lavoro del database viene mantenuta una cronologia delle esecuzioni (attività, eventi, log). Qui puoi definire il numero di giorni da archiviare per il flusso di lavoro: il processo di pulizia eliminerà gli archivi più vecchi una volta al giorno. Se il valore in questo campo è zero, l&#39;archivio non verrà mai eliminato.

* **[!UICONTROL Log SQL queries in the journal]**

   Questa funzionalità è riservata agli utenti avanzati. Riguarda flussi di lavoro che contengono attività di targeting (query, unione, intersezione, ecc.). Quando questa opzione è selezionata, le query SQL inviate al database durante l&#39;esecuzione del flusso di lavoro vengono visualizzate in  Adobe Campaign: questo significa che puoi analizzarli per ottimizzare le query o diagnosticare i problemi.

   Le query vengono visualizzate in una scheda **[!UICONTROL SQL logs]** aggiunta al flusso di lavoro (ad eccezione dei flussi di lavoro delle campagne) e all&#39;attività **[!UICONTROL Properties]** quando l&#39;opzione è abilitata. La scheda **[!UICONTROL Audit]** include anche le query SQL.

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   Questa opzione può essere utilizzata solo per il debug e non mai in produzione. Quando è attivato, il flusso di lavoro ha la priorità e tutti gli altri flussi di lavoro vengono interrotti fino al termine.

### Gestione errori {#error-management}

* **[!UICONTROL Troubleshooting]**

   Questo campo consente di definire le azioni da eseguire in caso di errori in un&#39;attività del flusso di lavoro. Sono disponibili due opzioni:

   * **[!UICONTROL Stop the process]**: il flusso di lavoro viene automaticamente messo in pausa. lo stato del flusso di lavoro cambia in **[!UICONTROL Failed]**. Una volta risolto il problema, riavviate il flusso di lavoro utilizzando i pulsanti **[!UICONTROL Start]** o **[!UICONTROL Restart]**.
   * **[!UICONTROL Ignore]**: lo stato dell’attività che ha attivato l’errore cambia in  **[!UICONTROL Failed]**, ma il flusso di lavoro mantiene lo  **[!UICONTROL Started]** stato. Questa configurazione è pertinente per le attività ricorrenti: se il ramo include un pianificatore, verrà avviato normalmente al successivo avvio del flusso di lavoro.

* **[!UICONTROL Consecutive errors]**

   Questo campo diventa disponibile quando il valore **[!UICONTROL Ignore]** è selezionato nel campo **[!UICONTROL In case of errors]**. È possibile specificare il numero di errori che possono essere ignorati prima dell&#39;arresto del processo. Una volta raggiunto questo numero, lo stato del flusso di lavoro cambia in **[!UICONTROL Failed]**. Se il valore di questo campo è 0, il flusso di lavoro non verrà mai interrotto indipendentemente dal numero di errori.

* **[!UICONTROL Template]**

   Questo campo consente di selezionare il modello di notifica da inviare ai supervisori del flusso di lavoro quando il suo stato cambia in **[!UICONTROL Failed]**.

   Gli operatori interessati riceveranno una notifica via e-mail, se il loro profilo contiene un indirizzo e-mail. Per definire i supervisori del flusso di lavoro, andate al campo **[!UICONTROL Supervisor(s)]** delle proprietà (**[!UICONTROL General]** scheda).

   ![](assets/wf-properties_select-supervisors.png)

   Il modello **[!UICONTROL Notification to a workflow supervisor]** predefinito include un collegamento per accedere alla console Adobe Campaign  tramite Web, in modo che il destinatario possa lavorare sul problema una volta effettuato l&#39;accesso.

   Per creare un modello personalizzato, passate a **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**.

