---
product: campaign
title: Sincronizzazione dei dati dei connettori CRM
description: Gestire i dati tra Campaign e il CRM
feature: Microsoft CRM Integration, Salesforce Integration
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 1%

---

# Sincronizzare i dati tra Campaign e il sistema CRM {#data-synchronization}



La sincronizzazione dei dati tra Adobe Campaign e CRM viene eseguita tramite un&#39;attività del flusso di lavoro dedicata: [Connettore CRM](../../workflow/using/crm-connector.md).

Ad esempio, per importare i dati di Microsoft Dynamics in Adobe Campaign, crea il seguente tipo di flusso di lavoro:

![](assets/crm_connectors_msdynamics_07.png)

Questo flusso di lavoro importa i contatti tramite Microsoft Dynamics, li sincronizza con i dati esistenti di Adobe Campaign, li elimina e aggiorna il database di Adobe Campaign.

È necessario configurare l&#39;attività **[!UICONTROL CRM Connector]** per sincronizzare i dati.

![](assets/crm_connectors_msdynamics_08.png)

Con questa attività è possibile:

* Importa dal CRM - [Ulteriori informazioni](#importing-from-the-crm)
* Esporta in CRM - [Ulteriori informazioni](#exporting-to-the-crm)
* Importa oggetti eliminati nel CRM - [Ulteriori informazioni](#importing-objects-deleted-in-the-crm)
* Elimina oggetti nel CRM - [Ulteriori informazioni](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Seleziona l’account esterno che corrisponde al CRM con cui desideri configurare la sincronizzazione, quindi seleziona l’oggetto da sincronizzare: account, opportunità, lead, contatti, ecc.

![](assets/crm_task_select_obj.png)

La configurazione di questa attività dipende dal processo da eseguire. Di seguito sono descritte diverse configurazioni.

## Importa dal CRM {#importing-from-the-crm}

Per importare i dati tramite il sistema di gestione delle relazioni con i clienti in Adobe Campaign, devi creare il seguente tipo di flusso di lavoro:

![](assets/crm_wf_import.png)

Per un&#39;attività di importazione, i passaggi di configurazione dell&#39;attività **[!UICONTROL CRM Connector]** sono:

1. Selezionare un&#39;operazione **[!UICONTROL Import from the CRM]**.
1. Passare all&#39;elenco a discesa **[!UICONTROL Remote object]** e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in Adobe Campaign durante la configurazione del connettore.
1. Andare alla sezione **[!UICONTROL Remote fields]** e immettere i campi da importare.

   Per aggiungere un campo, fare clic sul pulsante **[!UICONTROL Add]** nella barra degli strumenti, quindi fare clic sull&#39;icona **[!UICONTROL Edit expression]**.

   ![](assets/crm_task_import_add_field.png)

   Se necessario, modificare il formato dei dati tramite l&#39;elenco a discesa delle colonne **[!UICONTROL Conversion]**. I possibili tipi di conversione sono descritti in dettaglio in [Formato dati](#data-format).

   >[!IMPORTANT]
   >
   >L’identificatore del record nel CRM è obbligatorio per il collegamento di oggetti nel CRM e in Adobe Campaign. Viene aggiunto automaticamente quando la casella viene approvata.
   >
   >L’ultima data di modifica sul lato del sistema di gestione delle relazioni con i clienti è obbligatoria anche per le importazioni di dati incrementali.

1. Puoi anche filtrare i dati da importare in base alle tue esigenze. A tale scopo, fare clic sul collegamento **[!UICONTROL Edit the filter...]**.

   Nell’esempio seguente, Adobe Campaign importa solo i contatti per i quali è stata registrata un’attività dal 1° novembre 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >Le limitazioni collegate alle modalità di filtro dei dati sono descritte in dettaglio in [Filtro dei dati](#filtering-data).

1. L&#39;opzione **[!UICONTROL Use automatic index...]** consente di gestire automaticamente la sincronizzazione incrementale degli oggetti tra il sistema di gestione delle relazioni con i clienti e Adobe Campaign, a seconda della data e dell&#39;ultima modifica.

   Per ulteriori informazioni, consulta [Gestione delle variabili](#variable-management).

### Gestisci variabili {#variable-management}

Abilitare l&#39;opzione **[!UICONTROL Automatic index]** per raccogliere solo gli oggetti modificati dall&#39;ultima importazione.

![](assets/crm_task_import_option.png)

Per impostazione predefinita, la data dell&#39;ultima sincronizzazione è memorizzata in un&#39;opzione specificata nella finestra di configurazione: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Questa nota si applica solo all&#39;attività generica **[!UICONTROL CRM Connector]**. Per altre attività CRM, il processo è automatico.
>
>Questa opzione deve essere creata e compilata manualmente in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Deve essere un&#39;opzione di testo e il relativo valore deve corrispondere al seguente formato: **`yyyy/MM/dd hh:mm:ss`**.
> 
>È necessario aggiornare manualmente questa opzione per ulteriori importazioni.

Puoi specificare il campo CRM remoto di cui tenere conto per identificare le modifiche più recenti.

Per impostazione predefinita, vengono utilizzati i campi seguenti (nell’ordine specificato):

* Per Microsoft Dynamics: **modifiedon**,
* Per Salesforce.com: **LastModifiedDate**, **SystemModstamp**.

L&#39;attivazione dell&#39;opzione **[!UICONTROL Automatic index]** genera tre variabili che possono essere utilizzate nel flusso di lavoro di sincronizzazione tramite un&#39;attività di tipo **[!UICONTROL JavaScript code]**. Queste attività sono:

* **vars.crmOptionName**: rappresenta il nome dell&#39;opzione che contiene la data dell&#39;ultima importazione.
* **vars.crmStartImport**: rappresenta la data di inizio (inclusa) dell&#39;ultimo ripristino dei dati.
* **vars.crmEndDate**: rappresenta la data di fine (esclusa) dell&#39;ultimo ripristino dei dati.

  >[!NOTE]
  >
  >Queste date sono visualizzate nel seguente formato: **`yyyy/MM/dd hh:mm:ss`**.

### Filtrare i dati {#filtering-data}

Per garantire un funzionamento efficiente con i vari CRM, i filtri devono essere creati utilizzando le seguenti regole:

* Ogni livello di filtro può utilizzare un solo tipo di operatore.
* Operatore AND NOT non supportato.
* I confronti possono riguardare solo valori nulli (tipo &quot;è vuoto&quot;/&quot;non è vuoto&quot;) o numeri. Ciò significa che il valore (colonna di destra) viene valutato e il risultato di questa valutazione deve essere un numero. I confronti tra tipi JOIN non sono pertanto supportati.
* Il valore contenuto nella colonna di destra viene valutato in JavaScript.
* I confronti JOIN non sono supportati.
* L&#39;espressione nella colonna di sinistra deve essere un campo. Non può essere una combinazione di diverse espressioni, un numero, ecc.

Ad esempio, le seguenti condizioni di filtro NON saranno valide per un’importazione CRM, perché l’operatore OR è posizionato allo stesso livello degli operatori AND:

* L&#39;operatore OR viene posizionato allo stesso livello degli operatori AND
* I confronti vengono eseguiti su stringhe di testo

![](assets/crm_import_wrong_filter.png)

### Ordina per {#order-by}

In Microsoft Dynamics e Salesforce.com è possibile ordinare i campi remoti da importare in ordine crescente o decrescente.

A tale scopo, fare clic sul collegamento **[!UICONTROL Order by]** e aggiungere le colonne all&#39;elenco.

L’ordine delle colonne nell’elenco è il seguente:

![](assets/crm_import_order.png)

### Identificazione record {#record-identification}

Invece di importare gli elementi inclusi (e possibilmente filtrati) nel CRM, puoi utilizzare una popolazione calcolata in precedenza nel flusso di lavoro.

A tale scopo, selezionare l&#39;opzione **[!UICONTROL Use the population calculated upstream]** e specificare il campo contenente l&#39;identificatore remoto.

Seleziona quindi i campi del gruppo in entrata da importare, come illustrato di seguito:

![](assets/crm_wf_import_calculated_population.png)

## Esportazione nel CRM {#exporting-to-the-crm}

L’esportazione dei dati di Adobe Campaign nel sistema di gestione delle relazioni con i clienti consente di copiare l’intero contenuto in un database di gestione delle relazioni con i clienti.

Per esportare i dati verso il CRM, devi creare il seguente tipo di flusso di lavoro:

![](assets/crm_export_diagram.png)

Per un&#39;esportazione, applicare la seguente configurazione all&#39;attività **[!UICONTROL CRM Connector]**:

1. Selezionare un&#39;operazione **[!UICONTROL Export to CRM]**.
1. Passare all&#39;elenco a discesa **[!UICONTROL Remote object]** e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in Adobe Campaign durante la configurazione del connettore.

   >[!IMPORTANT]
   >
   >La funzione di esportazione dell&#39;attività **[!UICONTROL CRM Connector]** può inserire o aggiornare campi sul lato CRM. Per abilitare gli aggiornamenti dei campi nel CRM, devi specificare la chiave primaria della tabella remota. Se la chiave non è presente, i dati verranno inseriti (anziché aggiornati).

1. Selezionare **[!UICONTROL Export in Batches]** se è necessario eseguire esportazioni più rapide.

   ![](assets/crm_export_config_2.png)

1. Nella sezione **[!UICONTROL Mapping]**, fare clic su **[!UICONTROL New]** per specificare i campi da esportare e la relativa mappatura nel CRM.

   ![](assets/crm_export_config.png)

   Per aggiungere un campo, fare clic sul pulsante **[!UICONTROL Add]** nella barra degli strumenti, quindi fare clic sull&#39;icona **[!UICONTROL Edit expression]**.

   >[!NOTE]
   >
   >Per un determinato campo, se non è definita alcuna corrispondenza sul lato CRM, i valori non possono essere aggiornati: vengono inseriti direttamente nel CRM.

   Se necessario, modificare il formato dei dati tramite l&#39;elenco a discesa delle colonne **[!UICONTROL Conversion]**. I possibili tipi di conversione sono descritti in dettaglio in [Formato dati](#data-format).

   >[!NOTE]
   >
   >L&#39;elenco dei record da esportare e il risultato dell&#39;esportazione vengono salvati in un file temporaneo che rimane accessibile fino al completamento o al riavvio del flusso di lavoro. In questo modo è possibile avviare nuovamente il processo in caso di errori, senza il rischio di esportare più volte lo stesso record o di perdere dati.

## Configurazioni aggiuntive {#additional-configurations}

### Formato dei dati {#data-format}

Puoi convertire al volo il formato dei dati quando li importi in o dal sistema CRM.

A questo scopo, seleziona la conversione da applicare nella colonna corrispondente.

![](assets/crm_task_import.png)

La modalità **[!UICONTROL Default]** applica la conversione automatica dei dati, che nella maggior parte dei casi è uguale a una copia/incolla dei dati. Tuttavia, viene applicata la gestione del fuso orario.

Altre possibili conversioni sono:

* **[!UICONTROL Date only]**: questa modalità elimina i campi di tipo Data + Ora.
* **[!UICONTROL Without time offset]**: questa modalità annulla la gestione del fuso orario applicata nella modalità predefinita.
* **[!UICONTROL Copy/Paste]**: questa modalità utilizza dati non elaborati come stringhe (nessuna conversione).

### Elaborazione degli errori {#error-processing}

Nel quadro delle importazioni o delle esportazioni di dati, puoi applicare un processo specifico agli errori e ai rifiuti. A tale scopo, selezionare le opzioni **[!UICONTROL Process rejects]** e **[!UICONTROL Process errors]** nella scheda **[!UICONTROL Behavior]**.

![](assets/crm_export_options.png)

Queste opzioni inseriscono le transizioni di output corrispondenti.

![](assets/crm_export_transitions.png)

Quindi inserisci le attività pertinenti ai processi che desideri applicare.

Per elaborare gli errori, ad esempio, puoi aggiungere una casella di attesa e pianificare nuovi tentativi.

I rifiuti vengono raccolti con il relativo codice di errore e il relativo messaggio, il che significa che puoi impostare il tracciamento dei rifiuti per ottimizzare il processo di sincronizzazione.

>[!NOTE]
>
>Anche se l&#39;opzione **[!UICONTROL Process rejects]** non è abilitata, viene generato un avviso per ogni colonna rifiutata con un codice di errore e un messaggio.

La transizione di output **[!UICONTROL Reject]** consente di accedere allo schema di output contenente le colonne specifiche relative ai messaggi di errore e ai codici. Per Salesforce.com, questa colonna è **errorSymbol** (simbolo di errore, diverso dal codice di errore), **errorMessage** (descrizione del contesto di errore).

## Importa oggetti eliminati nel CRM {#importing-objects-deleted-in-the-crm}

Per abilitare l’impostazione di un processo di sincronizzazione dati esteso, puoi importare in Adobe Campaign gli oggetti eliminati nel sistema di gestione delle relazioni con i clienti.

A questo scopo, esegui i seguenti passaggi:

1. Selezionare un&#39;operazione **[!UICONTROL Import objects deleted in the CRM]**.
1. Passare all&#39;elenco a discesa **[!UICONTROL Remote object]** e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in Adobe Campaign durante la configurazione del connettore.
1. Specificare il periodo di eliminazione da considerare nei campi **[!UICONTROL Start date]** e **[!UICONTROL End date]**. Queste date verranno incluse nel periodo.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >Il periodo di eliminazione dell’elemento deve coincidere con le limitazioni specifiche del sistema di gestione delle relazioni con i clienti. Ciò significa che per Salesforce.com, ad esempio, non è possibile recuperare gli elementi eliminati più di 30 giorni fa.

## Elimina oggetti nel CRM {#deleting-objects-in-the-crm}

Per eliminare oggetti sul lato CRM, devi specificare la chiave primaria degli elementi remoti da eliminare.

![](assets/crm_delete_in_crm.png)

La scheda **[!UICONTROL Behavior]** consente di abilitare l&#39;elaborazione dei rifiuti. Questa opzione genera una seconda transizione di output per l&#39;attività **[!UICONTROL CRM connector]**. Per ulteriori informazioni, consulta [Errore durante l&#39;elaborazione](#error-processing).

>[!NOTE]
>
>Anche quando l&#39;opzione **[!UICONTROL Process rejects]** è disabilitata, viene generato un avviso per ogni colonna rifiutata.
>
