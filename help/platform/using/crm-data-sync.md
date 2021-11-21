---
product: campaign
title: Sincronizzazione dei dati dei connettori di gestione delle relazioni con i clienti
description: Gestione dei dati tra Campaign e il tuo CRM
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1528'
ht-degree: 0%

---

# Sincronizzazione dei dati tra Campaign e CRM {#data-synchronization}

![](../../assets/common.svg)

La sincronizzazione dei dati tra Adobe Campaign e il CRM viene eseguita tramite un’attività di flusso di lavoro dedicata: [Connettore CRM](../../workflow/using/crm-connector.md).

Ad esempio, per importare i dati di Microsoft Dynamics in Adobe Campaign, crea il seguente tipo di flusso di lavoro:

![](assets/crm_connectors_msdynamics_07.png)

Questo flusso di lavoro importa i contatti tramite Microsoft Dynamics, li sincronizza con i dati esistenti di Adobe Campaign, elimina i contatti duplicati e aggiorna il database Adobe Campaign.

La **[!UICONTROL CRM Connector]** l’attività deve essere configurata per sincronizzare i dati.

![](assets/crm_connectors_msdynamics_08.png)

Con questa attività puoi:

* Importa dal CRM - [Ulteriori informazioni](#importing-from-the-crm)
* Esportazione in CRM - [Ulteriori informazioni](#exporting-to-the-crm)
* Importa oggetti eliminati nel CRM - [Ulteriori informazioni](#importing-objects-deleted-in-the-crm)
* Elimina gli oggetti nel CRM - [Ulteriori informazioni](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Seleziona l&#39;account esterno che corrisponde al CRM con cui desideri configurare la sincronizzazione, quindi seleziona l&#39;oggetto da sincronizzare: account, opportunità, lead, contatti, ecc.

![](assets/crm_task_select_obj.png)

La configurazione di questa attività dipende dal processo da eseguire. Di seguito sono descritte diverse configurazioni.

## Importazione da CRM {#importing-from-the-crm}

Per importare dati tramite il CRM in Adobe Campaign, devi creare il seguente tipo di flusso di lavoro:

![](assets/crm_wf_import.png)

Per un’attività di importazione, la variabile **[!UICONTROL CRM Connector]** i passaggi di configurazione dell’attività sono:

1. Seleziona un **[!UICONTROL Import from the CRM]** funzionamento.
1. Vai a **[!UICONTROL Remote object]** elenco a discesa e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in Adobe Campaign durante la configurazione del connettore.
1. Vai a **[!UICONTROL Remote fields]** e immettere i campi da importare.

   Per aggiungere un campo, fai clic sul pulsante **[!UICONTROL Add]** nella barra degli strumenti, quindi fai clic sul pulsante **[!UICONTROL Edit expression]** icona.

   ![](assets/crm_task_import_add_field.png)

   Se necessario, modifica il formato dei dati tramite l’elenco a discesa della **[!UICONTROL Conversion]** colonne. I possibili tipi di conversione sono descritti in [Formato dati](#data-format).

   >[!IMPORTANT]
   >
   >L&#39;identificatore del record nel CRM è obbligatorio per il collegamento di oggetti in CRM e in Adobe Campaign. Viene aggiunto automaticamente quando la casella viene approvata.
   >
   >Anche l’ultima data di modifica sul lato CRM è obbligatoria per le importazioni di dati incrementali.

1. Puoi anche filtrare i dati da importare in base alle tue esigenze. A questo scopo, fai clic sul pulsante **[!UICONTROL Edit the filter...]** link.

   Nell’esempio seguente, Adobe Campaign importa solo i contatti per i quali è stata registrata una certa attività dal 1° novembre 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >Le limitazioni collegate alle modalità di filtraggio dei dati sono descritte in [Filtrare i dati](#filtering-data).

1. La **[!UICONTROL Use automatic index...]** consente di gestire automaticamente la sincronizzazione incrementale degli oggetti tra CRM e Adobe Campaign, a seconda della data e dell’ultima modifica.

   Per ulteriori informazioni, consulta [Gestione delle variabili](#variable-management).

### Gestire le variabili {#variable-management}

Abilita la **[!UICONTROL Automatic index]** per raccogliere solo gli oggetti modificati dall’ultima importazione.

![](assets/crm_task_import_option.png)

Per impostazione predefinita, la data dell&#39;ultima sincronizzazione viene memorizzata in un&#39;opzione specificata nella finestra di configurazione: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Questa nota si applica solo al generico **[!UICONTROL CRM Connector]** attività. Per altre attività CRM, il processo è automatico.
>
>Questa opzione deve essere creata e compilata manualmente in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Deve essere un’opzione di testo e il suo valore deve corrispondere al seguente formato: **aaaa/MM/gg hh:mm:ss**.
> 
>È necessario aggiornare manualmente questa opzione per qualsiasi ulteriore importazione.

Puoi specificare il campo CRM remoto da prendere in considerazione per identificare le modifiche più recenti.

Per impostazione predefinita, vengono utilizzati i campi seguenti (nell’ordine specificato):

* Per Microsoft Dynamics: **modifiedon**,
* Per Salesforce.com: **LastModifiedDate**, **SystemModestamp**.

Attivazione della **[!UICONTROL Automatic index]** L’opzione genera tre variabili che possono essere utilizzate nel flusso di lavoro di sincronizzazione tramite un **[!UICONTROL JavaScript code]** digitare activity. Queste attività sono:

* **vars.crmOptionName**: rappresenta il nome dell’opzione che contiene l’ultima data di importazione.
* **vars.crmStartImport**: rappresenta la data di inizio (inclusa) dell&#39;ultimo recupero dati.
* **vars.crmEndDate**: rappresenta la data di fine (esclusa) dell’ultimo recupero dati.

   >[!NOTE]
   >
   >Queste date vengono visualizzate nel seguente formato: **aaaa/MM/gg hh:mm:ss**.

### Filtrare i dati {#filtering-data}

Per garantire un funzionamento efficiente con le varie CRM, è necessario creare i filtri utilizzando le seguenti regole:

* Ogni livello di filtro può utilizzare un solo tipo di operatore.
* Operatore AND NOT non supportato.
* I confronti possono riguardare solo valori nulli (&quot;è vuoto&quot;/&quot;non è vuoto&quot;) o numeri. Ciò significa che il valore (colonna a destra) è valutato e il risultato di tale valutazione deve essere un numero. I confronti tra tipi JOIN non sono pertanto supportati.
* Il valore contenuto nella colonna di destra viene valutato in JavaScript.
* I confronti JOIN non sono supportati.
* L’espressione nella colonna a sinistra deve essere un campo. Non può essere una combinazione di più espressioni, un numero, ecc.

Ad esempio, le seguenti condizioni di filtro NON saranno valide per un&#39;importazione CRM, perché l&#39;operatore OR è posizionato allo stesso livello degli operatori AND:

* L’operatore OR viene posizionato allo stesso livello degli operatori AND
* I confronti vengono eseguiti sulle stringhe di testo

![](assets/crm_import_wrong_filter.png)

### Ordina per {#order-by}

In Microsoft Dynamics e Salesforce.com, puoi ordinare i campi remoti da importare in ordine crescente o decrescente.

A questo scopo, fai clic sul pulsante **[!UICONTROL Order by]** collega e aggiungi le colonne all’elenco.

L’ordine delle colonne nell’elenco è l’ordinamento:

![](assets/crm_import_order.png)

### Identificazione del record {#record-identification}

Invece di importare gli elementi inclusi (e possibilmente filtrati) nel CRM, puoi utilizzare una popolazione calcolata in precedenza nel flusso di lavoro.

A questo scopo, seleziona la **[!UICONTROL Use the population calculated upstream]** e specifica il campo contenente l&#39;identificatore remoto.

Quindi seleziona i campi della popolazione in entrata che desideri importare, come illustrato di seguito:

![](assets/crm_wf_import_calculated_population.png)

## Esportazione in CRM in corso {#exporting-to-the-crm}

L&#39;esportazione di dati Adobe Campaign in CRM ti consente di copiare l&#39;intero contenuto in un database CRM.

Per esportare i dati verso il CRM, devi creare il seguente tipo di flusso di lavoro:

![](assets/crm_export_diagram.png)

Per un’esportazione, applica la seguente configurazione al **[!UICONTROL CRM Connector]** attività:

1. Seleziona un **[!UICONTROL Export to CRM]** funzionamento.
1. Vai a **[!UICONTROL Remote object]** elenco a discesa e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in Adobe Campaign durante la configurazione del connettore.

   >[!IMPORTANT]
   >
   >La funzione di esportazione del **[!UICONTROL CRM Connector]** l&#39;attività può inserire o aggiornare campi sul lato CRM. Per abilitare gli aggiornamenti dei campi nel CRM, devi specificare la chiave primaria della tabella remota. Se la chiave è mancante, i dati verranno inseriti (anziché essere aggiornati).

1. In **[!UICONTROL Mapping]** specifica i campi da esportare e la relativa mappatura nel CRM.

   ![](assets/crm_export_config.png)

   Per aggiungere un campo, fai clic sul pulsante **[!UICONTROL Add]** nella barra degli strumenti, quindi fai clic sul pulsante **[!UICONTROL Edit expression]** icona.

   >[!NOTE]
   >
   >Per un dato campo, se non è definita alcuna corrispondenza sul lato CRM, i valori non possono essere aggiornati: sono inseriti direttamente nel CRM.

   Se necessario, modifica il formato dei dati tramite l’elenco a discesa della **[!UICONTROL Conversion]** colonne. I possibili tipi di conversione sono descritti in [Formato dati](#data-format).

   >[!NOTE]
   >
   >L’elenco dei record da esportare e il risultato dell’esportazione vengono salvati in un file temporaneo che rimane accessibile finché il flusso di lavoro non viene completato o riavviato. Questo consente di riavviare il processo in caso di errori senza correre il rischio di esportare più volte lo stesso record o di perdere dati.

## Configurazioni aggiuntive {#additional-configurations}

### Formato dati {#data-format}

Puoi convertire al volo il formato dei dati quando li importi in o dal CRM.

A questo scopo, seleziona la conversione da applicare nella colonna corrispondente.

![](assets/crm_task_import.png)

La **[!UICONTROL Default]** applica la conversione automatica dei dati, che nella maggior parte dei casi equivale a una copia/incolla dei dati. Tuttavia, viene applicata la gestione del fuso orario.

Altre possibili conversioni sono:

* **[!UICONTROL Date only]**: in questa modalità vengono eliminati i campi tipo data + ora .
* **[!UICONTROL Without time offset]**: questa modalità annulla la gestione del fuso orario applicata nella modalità predefinita.
* **[!UICONTROL Copy/Paste]**: questa modalità utilizza dati non elaborati come le stringhe (nessuna conversione).

### Elaborazione errore {#error-processing}

Nel quadro delle importazioni o delle esportazioni di dati, puoi applicare un processo specifico a errori e rifiuti. A questo scopo, seleziona la **[!UICONTROL Process rejects]** e **[!UICONTROL Process errors]** nelle opzioni **[!UICONTROL Behavior]** scheda .

![](assets/crm_export_options.png)

Queste opzioni posizionano le transizioni di output corrispondenti.

![](assets/crm_export_transitions.png)

Quindi inserisci le attività pertinenti ai processi che desideri applicare.

Per elaborare gli errori, ad esempio, è possibile aggiungere una casella di attesa e pianificare nuovi tentativi.

I rifiuti vengono raccolti con il loro codice di errore e il relativo messaggio, il che significa che puoi impostare il tracciamento dei rifiuti per ottimizzare il processo di sincronizzazione.

>[!NOTE]
>
>Anche quando il **[!UICONTROL Process rejects]** l’opzione non è abilitata, viene generato un avviso per ogni colonna rifiutata con un codice di errore e un messaggio.

La **[!UICONTROL Reject]** la transizione di output consente di accedere allo schema di output contenente le colonne specifiche relative ai messaggi di errore e ai codici. Per Salesforce.com, questa colonna è **errorSymbol** (simbolo di errore diverso dal codice di errore), **errorMessage** (descrizione del contesto dell’errore).

## Importa oggetti eliminati nel CRM {#importing-objects-deleted-in-the-crm}

Per abilitare l’impostazione di un ampio processo di sincronizzazione dei dati, puoi importare in Adobe Campaign gli oggetti eliminati nel CRM.

A questo scopo, esegui i seguenti passaggi:

1. Seleziona un **[!UICONTROL Import objects deleted in the CRM]** funzionamento.
1. Vai a **[!UICONTROL Remote object]** elenco a discesa e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in Adobe Campaign durante la configurazione del connettore.
1. Specifica il periodo di eliminazione di cui tenere conto nel **[!UICONTROL Start date]** e **[!UICONTROL End date]** campi. Queste date saranno incluse nel periodo.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >Il periodo di eliminazione degli elementi deve coincidere con le limitazioni specifiche del CRM. Ciò significa che per Salesforce.com, ad esempio, gli elementi cancellati più di 30 giorni fa non possono essere recuperati.

## Eliminare gli oggetti nel CRM {#deleting-objects-in-the-crm}

Per eliminare gli oggetti dal lato CRM, è necessario specificare la chiave primaria degli elementi remoti da eliminare.

![](assets/crm_delete_in_crm.png)

La **[!UICONTROL Behavior]** consente di abilitare l’elaborazione dei rifiuti. Questa opzione genera una seconda transizione di output per **[!UICONTROL CRM connector]** attività. Per ulteriori informazioni, consulta [Elaborazione errore](#error-processing).

>[!NOTE]
>
>Anche quando il **[!UICONTROL Process rejects]** è disabilitata, viene generato un avviso per ogni colonna rifiutata.
