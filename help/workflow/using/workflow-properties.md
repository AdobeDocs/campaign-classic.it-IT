---
product: campaign
title: Proprietà del flusso di lavoro
description: Ulteriori informazioni sulle proprietà del flusso di lavoro di Campaign
feature: Workflows
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---

# Proprietà del flusso di lavoro{#workflow-properties}

![](../../assets/v7-only.svg)

## Scheda Esecuzione {#execution-tab}

La **[!UICONTROL Execution]** della scheda **[!UICONTROL Properties]** la finestra di un flusso di lavoro è suddivisa in 3 sezioni:

![](assets/wf_execution_tab.png)

### Attività Scheduler {#scheduler}

Questa sezione viene visualizzata solo nei flussi di lavoro delle campagne.

* **[!UICONTROL Priority]**

   Il motore del flusso di lavoro elabora i flussi di lavoro da eseguire in base al criterio di priorità definito in questo campo. Ad esempio, tutti i flussi di lavoro con un **[!UICONTROL Average]** la priorità verrà eseguita prima di quelle con un **[!UICONTROL Low]** priorità.

* **[!UICONTROL Schedule execution for a time of low activity]**

   Questa opzione posticipa l’inizio del flusso di lavoro a un periodo meno occupato. Alcuni flussi di lavoro possono essere costosi in termini di risorse per il motore di database. Consigliamo di pianificare l’esecuzione per un periodo di bassa attività (ad esempio di notte). I periodi di attività ridotti sono definiti nella variabile **[!UICONTROL Processes on campaigns]** flusso di lavoro tecnico.

### Execution {#execution}

* **[!UICONTROL Default affinity]**

   Se l’installazione include diversi server del flusso di lavoro, utilizza questo campo per scegliere il computer su cui verrà eseguito il flusso di lavoro. Se il valore definito in questo campo non esiste su alcun server, il flusso di lavoro rimarrà in sospeso.

   Fai riferimento a questo [Guida all’installazione di Campaign Classic v7](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL History in days]**

   Le tabelle di lavoro del database conservano una cronologia delle esecuzioni (attività, eventi, log). Qui puoi definire il numero di giorni da archiviare per questo flusso di lavoro: il processo di pulizia eliminerà gli archivi più vecchi una volta al giorno. Se il valore in questo campo è zero, l’archivio non verrà mai eliminato.

* **[!UICONTROL Log SQL queries in the journal]**

   Questa funzionalità è riservata agli utenti avanzati. Riguarda flussi di lavoro che contengono attività di targeting (query, unione, intersezione, ecc.). Quando questa opzione è selezionata, le query SQL inviate al database durante l’esecuzione del flusso di lavoro vengono visualizzate in Adobe Campaign: questo significa che puoi analizzarli per ottimizzare le query o diagnosticare i problemi.

   Le query vengono visualizzate in un **[!UICONTROL SQL logs]** , che viene aggiunta al flusso di lavoro (ad eccezione dei flussi di lavoro della campagna) e al **[!UICONTROL Properties]** quando l’opzione è abilitata. La **[!UICONTROL Audit]** La scheda include anche le query SQL.

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   Questa opzione può essere utilizzata solo per il debug e non mai in produzione. Quando è abilitato, il flusso di lavoro ha la priorità e tutti gli altri flussi di lavoro vengono interrotti fino al termine di questo.

### Gestione degli errori {#error-management}

* **[!UICONTROL Troubleshooting]**

   Questo campo ti consente di definire le azioni da eseguire in caso di errori in un’attività del flusso di lavoro. Sono disponibili due opzioni possibili:

   * **[!UICONTROL Stop the process]**: il flusso di lavoro viene messo in pausa automaticamente. lo stato del flusso di lavoro cambia in **[!UICONTROL Failed]**. Una volta risolto il problema, riavvia il flusso di lavoro utilizzando **[!UICONTROL Start]** o **[!UICONTROL Restart]** pulsanti.
   * **[!UICONTROL Ignore]**: lo stato dell’attività che ha attivato l’errore cambia in **[!UICONTROL Failed]**, ma il flusso di lavoro mantiene **[!UICONTROL Started]** stato. Questa configurazione è pertinente per le attività ricorrenti: se il ramo include una pianificazione, si avvia normalmente alla successiva esecuzione del flusso di lavoro.

* **[!UICONTROL Consecutive errors]**

   Questo campo diventa disponibile quando la **[!UICONTROL Ignore]** è selezionato nella **[!UICONTROL In case of errors]** campo . È possibile specificare il numero di errori che possono essere ignorati prima dell&#39;arresto del processo. Una volta raggiunto questo numero, lo stato del flusso di lavoro cambia in **[!UICONTROL Failed]**. Se il valore di questo campo è 0, il flusso di lavoro non verrà mai interrotto indipendentemente dal numero di errori.

* **[!UICONTROL Template]**

   Questo campo ti consente di selezionare il modello di notifica da inviare alle autorità di vigilanza del flusso di lavoro quando il suo stato cambia in **[!UICONTROL Failed]**.

   Gli operatori interessati riceveranno una notifica tramite e-mail, se il loro profilo contiene un indirizzo e-mail. Per definire i supervisori del flusso di lavoro, vai alla pagina **[!UICONTROL Supervisor(s)]** campo delle proprietà (**[!UICONTROL General]** ).

   ![](assets/wf-properties_select-supervisors.png)

   La **[!UICONTROL Notification to a workflow supervisor]** il modello predefinito include un collegamento per accedere alla console Adobe Campaign tramite il Web in modo che il destinatario possa risolvere il problema una volta effettuato l’accesso.

   Per creare un modello personalizzato, passa a **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**.
