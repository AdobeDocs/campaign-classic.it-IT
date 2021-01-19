---
solution: Campaign Classic
product: campaign
title: Sincronizzazione dei dati dei connettori CRM
description: Gestione dei dati tra Campaign e CRM
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 0%

---


# Sincronizzazione dei dati tra Campaign e CRM {#data-synchronization}

La sincronizzazione dei dati tra  Adobe Campaign e CRM viene eseguita tramite un&#39;attività di flusso di lavoro dedicata: [Connettore CRM](../../workflow/using/crm-connector.md).

Ad esempio, per importare i dati di Microsoft Dynamics in  Adobe Campaign, creare il seguente tipo di flusso di lavoro:

![](assets/crm_connectors_msdynamics_07.png)

Questo flusso di lavoro importa i contatti tramite Microsoft Dynamics, li sincronizza con i dati Adobe Campaign  esistenti, elimina i contatti duplicati e aggiorna il database Adobe Campaign .

L&#39;attività **[!UICONTROL CRM Connector]** deve essere configurata per sincronizzare i dati.

![](assets/crm_connectors_msdynamics_08.png)

Con questa attività è possibile:

* Importa da CRM - [Ulteriori informazioni](#importing-from-the-crm)
* Esportazione in CRM - [Ulteriori informazioni](#exporting-to-the-crm)
* Importa oggetti eliminati in CRM - [Ulteriori informazioni](#importing-objects-deleted-in-the-crm)
* Eliminare gli oggetti in CRM - [Ulteriori informazioni](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Selezionare l&#39;account esterno che corrisponde al CRM con cui si desidera configurare la sincronizzazione, quindi selezionare l&#39;oggetto da sincronizzare: account, opportunità, lead, contatti ecc.

![](assets/crm_task_select_obj.png)

La configurazione di questa attività dipende dal processo da eseguire. Diverse configurazioni sono descritte di seguito.

## Importazione da CRM {#importing-from-the-crm}

Per importare dati tramite CRM in  Adobe Campaign, è necessario creare il seguente tipo di flusso di lavoro:

![](assets/crm_wf_import.png)

Per un&#39;attività di importazione, i passaggi di configurazione dell&#39;attività **[!UICONTROL CRM Connector]** sono:

1. Selezionare un&#39;operazione **[!UICONTROL Import from the CRM]**.
1. Fare clic sull&#39;elenco a discesa **[!UICONTROL Remote object]** e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in  Adobe Campaign durante la configurazione del connettore.
1. Andate alla sezione **[!UICONTROL Remote fields]** e immettete i campi da importare.

   Per aggiungere un campo, fare clic sul pulsante **[!UICONTROL Add]** nella barra degli strumenti, quindi fare clic sull&#39;icona **[!UICONTROL Edit expression]**.

   ![](assets/crm_task_import_add_field.png)

   Se necessario, modificare il formato dei dati tramite l&#39;elenco a discesa delle colonne **[!UICONTROL Conversion]**. I possibili tipi di conversione sono descritti in [Formato dati](#data-format).

   >[!IMPORTANT]
   >
   >L&#39;identificatore del record in CRM è obbligatorio per il collegamento di oggetti in CRM e in  Adobe Campaign. Viene aggiunto automaticamente all’approvazione della casella.
   >
   >Anche l&#39;ultima data di modifica sul lato CRM è obbligatoria per le importazioni di dati incrementali.

1. Puoi anche filtrare i dati da importare in base alle tue esigenze. A tale scopo, fare clic sul collegamento **[!UICONTROL Edit the filter...]**.

   Nell&#39;esempio seguente,  Adobe Campaign importa solo i contatti per i quali alcune attività sono state registrate dal 1° novembre 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >Le limitazioni collegate alle modalità di filtraggio dei dati sono descritte in [Filtro dei dati](#filtering-data).

1. L&#39;opzione **[!UICONTROL Use automatic index...]** consente di gestire automaticamente la sincronizzazione incrementale degli oggetti tra CRM e  Adobe Campaign, a seconda della data e dell&#39;ultima modifica.

   Per ulteriori informazioni, consultare [Gestione delle variabili](#variable-management).

### Gestione delle variabili {#variable-management}

L&#39;attivazione dell&#39;opzione **[!UICONTROL Automatic index]** consente di raccogliere solo gli oggetti modificati dall&#39;ultima importazione.

![](assets/crm_task_import_option.png)

Per impostazione predefinita, la data dell’ultima sincronizzazione è memorizzata in un’opzione specificata nella finestra di configurazione: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Questa nota si applica solo all&#39;attività **[!UICONTROL CRM Connector]** generica. Per altre attività CRM, il processo è automatico.
>
>Questa opzione deve essere creata manualmente e compilata in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Deve essere un&#39;opzione di testo e il suo valore deve corrispondere al seguente formato: **yyyy/MM/dd hh:mm:ss**.
> 
>È necessario aggiornare manualmente questa opzione per qualsiasi ulteriore importazione.

Puoi specificare il campo CRM remoto da prendere in considerazione per identificare le modifiche più recenti.

Per impostazione predefinita, vengono utilizzati i campi seguenti (nell&#39;ordine specificato):

* Per Microsoft Dynamics: **modificato su**,
* Per Salesforce.com: **LastModifiedDate**, **SystemModestamp**.

Attivando l&#39;opzione **[!UICONTROL Automatic index]** vengono generate tre variabili che possono essere utilizzate nel flusso di lavoro di sincronizzazione tramite un&#39;attività di tipo **[!UICONTROL JavaScript code]**. Tali attività sono:

* **vars.crmOptionName**: rappresenta il nome dell&#39;opzione che contiene l&#39;ultima data di importazione.
* **vars.crmStartImport**: rappresenta la data di inizio (inclusa) dell&#39;ultimo recupero di dati.
* **vars.crmEndDate**: rappresenta la data di fine (esclusa) dell&#39;ultimo recupero di dati.

   >[!NOTE]
   >
   >Queste date sono visualizzate nel seguente formato: **yyyy/MM/dd hh:mm:ss**.

### Filtrare dati {#filtering-data}

Per garantire un funzionamento efficiente con i diversi CRM, è necessario creare i filtri utilizzando le seguenti regole:

* Ogni livello di filtro può utilizzare un solo tipo di operatore.
* L&#39;operatore AND NOT non è supportato.
* I confronti possono riguardare solo valori null (tipo &#39;is empty&#39;/&#39;non empty&#39;) o numeri. Ciò significa che il valore (colonna a destra) è valutato e il risultato di tale valutazione deve essere un numero. I confronti tra tipi JOIN non sono pertanto supportati.
* Il valore contenuto nella colonna di destra viene valutato in JavaScript.
* I confronti JOIN non sono supportati.
* L&#39;espressione nella colonna a sinistra deve essere un campo. Non può essere una combinazione di più espressioni, un numero, ecc.

Ad esempio, le seguenti condizioni di filtraggio NON saranno valide per un&#39;importazione CRM, perché l&#39;operatore OR è collocato allo stesso livello degli operatori AND:

* L&#39;operatore OR è collocato allo stesso livello degli operatori AND
* I confronti vengono eseguiti sulle stringhe di testo

![](assets/crm_import_wrong_filter.png)

### Ordina per {#order-by}

In Microsoft Dynamics e Salesforce.com, puoi ordinare i campi remoti da importare in ordine crescente o decrescente.

A questo scopo, fare clic sul collegamento **[!UICONTROL Order by]** e aggiungere le colonne all&#39;elenco.

L&#39;ordine delle colonne nell&#39;elenco corrisponde all&#39;ordine di ordinamento:

![](assets/crm_import_order.png)

### Identificazione del record {#record-identification}

Invece di importare gli elementi inclusi (e possibilmente filtrati) in CRM, puoi utilizzare una popolazione calcolata in precedenza nel flusso di lavoro.

A questo scopo, selezionare l&#39;opzione **[!UICONTROL Use the population calculated upstream]** e specificare il campo che contiene l&#39;identificatore remoto.

Selezionate quindi i campi della popolazione in entrata che desiderate importare, come illustrato di seguito:

![](assets/crm_wf_import_calculated_population.png)

## Esportazione in CRM {#exporting-to-the-crm}

L&#39;esportazione  dati Adobe Campaign in CRM consente di copiare l&#39;intero contenuto in un database CRM.

Per esportare i dati in CRM, devi creare il seguente tipo di flusso di lavoro:

![](assets/crm_export_diagram.png)

Per un&#39;esportazione, applicate la seguente configurazione all&#39;attività **[!UICONTROL CRM Connector]**:

1. Selezionare un&#39;operazione **[!UICONTROL Export to CRM]**.
1. Fare clic sull&#39;elenco a discesa **[!UICONTROL Remote object]** e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in  Adobe Campaign durante la configurazione del connettore.

   >[!IMPORTANT]
   >
   >La funzione di esportazione dell&#39;attività **[!UICONTROL CRM Connector]** può inserire o aggiornare campi sul lato CRM. Per abilitare gli aggiornamenti di campo in CRM, devi specificare la chiave primaria della tabella remota. Se la chiave non è presente, i dati verranno inseriti (anziché essere aggiornati).

1. Nella sezione **[!UICONTROL Mapping]**, specificate i campi da esportare e la relativa mappatura nel CRM.

   ![](assets/crm_export_config.png)

   Per aggiungere un campo, fare clic sul pulsante **[!UICONTROL Add]** nella barra degli strumenti, quindi fare clic sull&#39;icona **[!UICONTROL Edit expression]**.

   >[!NOTE]
   >
   >Per un dato campo, se non è definita alcuna corrispondenza sul lato CRM, i valori non possono essere aggiornati: sono inseriti direttamente nel CRM.

   Se necessario, modificare il formato dei dati tramite l&#39;elenco a discesa delle colonne **[!UICONTROL Conversion]**. I possibili tipi di conversione sono descritti in [Formato dati](#data-format).

   >[!NOTE]
   >
   >L&#39;elenco dei record da esportare e il risultato dell&#39;esportazione vengono salvati in un file temporaneo che rimane accessibile finché il flusso di lavoro non viene completato o riavviato. Questo consente di riavviare il processo in caso di errori senza correre il rischio di esportare più volte lo stesso record o di perdere dati.

## Configurazioni aggiuntive {#additional-configurations}

### Formato dati {#data-format}

È possibile convertire il formato dei dati al momento dell&#39;importazione in o da CRM.

A questo scopo, selezionare la conversione da applicare nella colonna corrispondente.

![](assets/crm_task_import.png)

La modalità **[!UICONTROL Default]** applica la conversione automatica dei dati, che nella maggior parte dei casi corrisponde a una copia/incolla dei dati. Tuttavia, viene applicata la gestione del fuso orario.

Altre possibili conversioni sono:

* **[!UICONTROL Date only]**: in questa modalità vengono eliminati i campi Data + Ora.
* **[!UICONTROL Without time offset]**: questa modalità annulla la gestione del fuso orario applicata nella modalità predefinita.
* **[!UICONTROL Copy/Paste]**: questa modalità utilizza dati non elaborati come le stringhe (nessuna conversione).

### Errore durante l&#39;elaborazione di {#error-processing}

Nel quadro delle importazioni o delle esportazioni di dati, è possibile applicare un processo specifico a errori e rifiuti. A tal fine, selezionare le opzioni **[!UICONTROL Process rejects]** e **[!UICONTROL Process errors]** nella scheda **[!UICONTROL Behavior]**.

![](assets/crm_export_options.png)

Queste opzioni consentono di posizionare le transizioni di output corrispondenti.

![](assets/crm_export_transitions.png)

Quindi, inserite le attività pertinenti ai processi che desiderate applicare.

Per elaborare gli errori, ad esempio, potete aggiungere una casella di attesa e pianificare i tentativi.

I rifiuti vengono raccolti con il relativo codice di errore e il relativo messaggio, il che significa che è possibile impostare il tracciamento dei rifiuti per ottimizzare il processo di sincronizzazione.

>[!NOTE]
>
>Anche quando l&#39;opzione **[!UICONTROL Process rejects]** non è abilitata, viene generato un avviso per ogni colonna rifiutata con un codice di errore e un messaggio.

La transizione di output **[!UICONTROL Reject]** consente di accedere allo schema di output che contiene le colonne specifiche relative ai messaggi di errore e ai codici. Per Salesforce.com, questa colonna è **errorSymbol** (simbolo di errore, diverso dal codice di errore), **errorMessage** (descrizione del contesto di errore).

## Importazione di oggetti eliminati in CRM {#importing-objects-deleted-in-the-crm}

Per abilitare l&#39;impostazione di un ampio processo di sincronizzazione dei dati, puoi importare gli oggetti eliminati in CRM in  Adobe Campaign.

A questo scopo, eseguire i seguenti passaggi:

1. Selezionare un&#39;operazione **[!UICONTROL Import objects deleted in the CRM]**.
1. Fare clic sull&#39;elenco a discesa **[!UICONTROL Remote object]** e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in  Adobe Campaign durante la configurazione del connettore.
1. Specificare il periodo di eliminazione da prendere in considerazione nei campi **[!UICONTROL Start date]** e **[!UICONTROL End date]**. Queste date verranno incluse nel periodo.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >Il periodo di eliminazione degli elementi deve coincidere con le limitazioni specifiche del CRM. Ciò significa che per Salesforce.com, ad esempio, gli elementi eliminati oltre 30 giorni fa non possono essere recuperati.

## Eliminazione di oggetti in CRM {#deleting-objects-in-the-crm}

Per eliminare gli oggetti dal lato CRM, è necessario specificare la chiave primaria degli elementi remoti da eliminare.

![](assets/crm_delete_in_crm.png)

La scheda **[!UICONTROL Behavior]** consente di abilitare l&#39;elaborazione dei rifiuti. Questa opzione genera una seconda transizione di output per l&#39;attività **[!UICONTROL CRM connector]**. Per ulteriori informazioni, vedere [Elaborazione degli errori](#error-processing).

>[!NOTE]
>
>Anche quando l&#39;opzione **[!UICONTROL Process rejects]** è disabilitata, viene generato un avviso per ogni colonna rifiutata.

