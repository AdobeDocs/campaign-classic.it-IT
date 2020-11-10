---
title: Connettore di gestione delle relazioni con i clienti
description: Ulteriori informazioni sul connettore CRM e configurare la sincronizzazione dei dati
page-status-flag: never-activated
uuid: b3856a82-b1dc-4e36-a2d0-14edc5b66b3b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: af7c0d1d-10ac-427b-8d12-b97eb91b30a1
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 0%

---


# Connettore di gestione delle relazioni con i clienti{#crm-connector}

Il connettore **** CRM consente di configurare la sincronizzazione dei dati tra  Adobe Campaign e un CRM.

Per ulteriori informazioni sui connettori CRM in  Adobe Campaign, consulta questa [sezione](../../platform/using/crm-connectors.md).

Questo consente di:

* Importa da CRM (fare riferimento a [Importazione da CRM](#importing-from-the-crm)),
* Esportazione in CRM (fare riferimento a [Esportazione in CRM](#exporting-to-the-crm)),
* Importa oggetti eliminati nel CRM (fare riferimento a [Importazione di oggetti eliminati nel CRM](#importing-objects-deleted-in-the-crm)),
* Eliminare gli oggetti in CRM (fare riferimento a [Eliminazione degli oggetti in CRM](#deleting-objects-in-the-crm)).

![](assets/crm_task_select_op.png)

Selezionare l&#39;account esterno che corrisponde al CRM con cui si desidera configurare la sincronizzazione, quindi selezionare l&#39;oggetto da sincronizzare (account, opportunità, contatti, ecc.).

![](assets/crm_task_select_obj.png)

La configurazione di questa attività dipende dal processo da eseguire. Diverse configurazioni sono descritte di seguito.

## Importazione da CRM {#importing-from-the-crm}

Per importare dati tramite CRM in  Adobe Campaign, è necessario creare il seguente tipo di flusso di lavoro:

![](assets/crm_wf_import.png)

Per un&#39;attività di importazione, i passaggi di configurazione dell&#39;attività del connettore **** CRM sono:

1. Selezionare un&#39; **[!UICONTROL Import from the CRM]** operazione.
1. Fare clic sull&#39;elenco a **[!UICONTROL Remote object]** discesa e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in  Adobe Campaign durante la configurazione del connettore.
1. Passate alla **[!UICONTROL Remote fields]** sezione e inserite i campi da importare.

   Per aggiungere un campo, fare clic sul **[!UICONTROL Add]** pulsante nella barra degli strumenti, quindi fare clic sull&#39; **[!UICONTROL Edit expression]** icona.

   ![](assets/crm_task_import_add_field.png)

   Se necessario, modificare il formato dei dati tramite l&#39;elenco a discesa delle **[!UICONTROL Conversion]** colonne. I possibili tipi di conversione sono descritti in dettaglio in questa [pagina](../../platform/using/crm-connectors.md#data-format).

   >[!CAUTION]
   >
   >L&#39;identificatore del record in CRM è obbligatorio per il collegamento di oggetti in CRM e in  Adobe Campaign. Viene aggiunto automaticamente quando l&#39;attività viene approvata.
   > 
   >Anche l&#39;ultima data di modifica sul lato CRM è obbligatoria per le importazioni di dati incrementali.

1. Puoi anche filtrare i dati da importare in base alle tue esigenze. A tale scopo, fare clic sul **[!UICONTROL Edit the filter...]** collegamento.

   Nell&#39;esempio seguente,  Adobe Campaign importa solo i contatti per i quali è stata registrata una certa attività dal 31 luglio 2012.

   ![](assets/crm_task_import_filter.png)

   Le limitazioni collegate alle modalità di filtraggio dei dati sono descritte in [Filtra nella sezione dei dati](#filter-on-data) .

1. L&#39; **[!UICONTROL Use automatic index]** opzione consente di gestire automaticamente la sincronizzazione incrementale degli oggetti tra CRM e  Adobe Campaign, a seconda della data e dell&#39;ultima modifica.

   For more on this, refer to [Variable management](#variable-management).

## Gestione delle variabili {#variable-management}

Abilitando l&#39; **[!UICONTROL Automatic index]** opzione è possibile raccogliere solo gli oggetti modificati dall&#39;ultima importazione.

![](assets/crm_task_import_option.png)

Per impostazione predefinita, la data dell&#39;ultima sincronizzazione è memorizzata nell&#39;opzione specificata nella finestra di configurazione:

```
LASTIMPORT_<%=instance.internalName%>_<%=activityName%>
```

Puoi specificare il campo CRM remoto da prendere in considerazione per identificare le modifiche più recenti.

Per impostazione predefinita, vengono utilizzati i campi seguenti (nell&#39;ordine specificato):

* Per Microsoft Dynamics: **modifiedon**,
* Per Oracle On Demand: **LastUpdated**, **ModifiedDate**, **LastLoggedIn**,
* Per Salesforce.com: **LastModifiedDate**, **SystemModestamp**.

Attivando l&#39; **[!UICONTROL Automatic index]** opzione vengono generate tre variabili che possono essere utilizzate nel flusso di lavoro di sincronizzazione tramite un&#39;attività di **[!UICONTROL JavaScript code]** tipo. Tali attività sono:

* **varscriptOptionName**: rappresenta il nome dell&#39;opzione che contiene l&#39;ultima data di importazione.
* **vars.crmStartImport**: rappresenta la data di inizio (inclusa) dell&#39;ultimo recupero di dati.
* **vars.crmEndDate**: rappresenta la data di fine (esclusa) dell&#39;ultimo recupero di dati.

   Queste date sono visualizzate nel seguente formato: **aaaa/MM/gg hh:mm:ss**.

## Filtrare i dati {#filter-on-data}

Per garantire un funzionamento efficiente con i diversi CRM, è necessario creare i filtri utilizzando le seguenti regole:

* Ogni livello di filtro può utilizzare un solo tipo di operatore logico.
* L&#39;operatore EXCEPT (AND NOT) non è supportato.
* I confronti possono riguardare solo valori null (tipo &#39;is empty&#39;/&#39;non empty&#39;) o numeri. Ciò significa che una volta valutata la **[!UICONTROL Value]** colonna (colonna a destra), il risultato di questa valutazione deve essere un numero.
* I dati nella **[!UICONTROL Value]** colonna vengono valutati in JavaScript.
* I confronti JOIN non sono supportati.
* L&#39;espressione nella colonna a sinistra deve essere un campo. Non può essere una combinazione di più espressioni, un numero, ecc.

Ad esempio, la condizione di filtro illustrata di seguito NON sarà valida per un&#39;importazione CRM, perché:

* L&#39;operatore OR è collocato sullo stesso livello degli operatori AND.
* I confronti vengono eseguiti sulle stringhe di testo.

![](assets/crm_import_wrong_filter.png)

## Ordina per {#order-by}

In Microsoft Dynamics e Salesforce.com, puoi ordinare i campi remoti da importare in ordine crescente o decrescente.

A tale scopo, fare clic sul **[!UICONTROL Order by]** collegamento e aggiungere le colonne all&#39;elenco.

L&#39;ordine delle colonne nell&#39;elenco corrisponde all&#39;ordine di ordinamento:

![](assets/crm_import_order.png)

## Identificazione del record {#record-identification}

Invece di importare gli elementi inclusi (e possibilmente filtrati) in CRM, puoi utilizzare una popolazione calcolata in precedenza nel flusso di lavoro.

A questo scopo, selezionare l&#39; **[!UICONTROL Use the population calculated upstream]** opzione e specificare il campo contenente l&#39;identificatore remoto.

Selezionate quindi i campi della popolazione in entrata che desiderate importare, come illustrato di seguito:

![](assets/crm_wf_import_calculated_population.png)

## Esportazione in CRM {#exporting-to-the-crm}

L&#39;esportazione  dati Adobe Campaign in CRM consente di copiare l&#39;intero contenuto in un database CRM.

Per esportare i dati in CRM, devi creare il seguente tipo di flusso di lavoro:

![](assets/crm_export_diagram.png)

Per un&#39;esportazione, applica la seguente configurazione all&#39;attività del connettore **** CRM:

1. Selezionare un&#39; **[!UICONTROL Export to CRM]** operazione.
1. Fare clic sull&#39;elenco a **[!UICONTROL Remote object]** discesa e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in  Adobe Campaign durante la configurazione del connettore.

   >[!CAUTION]
   >
   >La funzione di esportazione dell&#39;attività Connettori **** CRM può inserire o aggiornare campi sul lato CRM. Per abilitare gli aggiornamenti di campo in CRM, devi specificare la chiave primaria della tabella remota. Se la chiave non è presente, i dati verranno inseriti (anziché essere aggiornati).

1. Nella **[!UICONTROL Mapping]** sezione, specifica i campi da esportare e la relativa mappatura in CRM.

   ![](assets/crm_export_config.png)

   Per aggiungere un campo, fare clic sul **[!UICONTROL Add]** pulsante nella barra degli strumenti, quindi fare clic sull&#39; **[!UICONTROL Edit expression]** icona.

   Per un dato campo, se non è definita alcuna corrispondenza sul lato CRM, i valori non possono essere aggiornati: sono inseriti direttamente nel CRM.

   Se necessario, modificare il formato dei dati tramite l&#39;elenco a discesa delle **[!UICONTROL Conversion]** colonne. I possibili tipi di conversione sono descritti in dettaglio in questa [sezione](../../platform/using/crm-connectors.md#data-format).

   L&#39;elenco dei record da esportare e il risultato dell&#39;esportazione vengono salvati in un file temporaneo che rimane accessibile finché il flusso di lavoro non viene completato o riavviato. Questo consente di riavviare il processo in caso di errori senza correre il rischio di esportare più volte lo stesso record o di perdere dati.

## Formato dati ed elaborazione degli errori {#data-format-and-error-processing}

È possibile convertire il formato dei dati al momento dell&#39;importazione in o da CRM.

A questo scopo, selezionare la conversione da applicare nella colonna corrispondente.

![](assets/crm_task_import.png)

La **[!UICONTROL Default]** modalità applica la conversione automatica dei dati, che nella maggior parte dei casi corrisponde a una copia/incolla dei dati. Tuttavia, viene applicata la gestione del fuso orario.

Altre possibili conversioni sono:

* **[!UICONTROL Date only]**: in questa modalità vengono eliminati i campi Data + Ora.
* **[!UICONTROL Without time offset]**: questa modalità annulla la gestione del fuso orario applicata nella modalità predefinita.
* **[!UICONTROL Copy/Paste]**: questa modalità utilizza dati non elaborati come le stringhe (nessuna conversione).

![](assets/crm_export_options.png)

Nel quadro delle importazioni o delle esportazioni di dati, è possibile applicare un processo specifico a errori e rifiuti. A questo scopo, selezionare le opzioni **[!UICONTROL Process rejects]** e **[!UICONTROL Process errors]** nella **[!UICONTROL Behavior]** scheda.

Queste opzioni consentono di posizionare le corrispondenti transizioni in uscita.

![](assets/crm_export_transitions.png)

Quindi, inserite le attività pertinenti ai processi che desiderate applicare.

Per elaborare gli errori, ad esempio, potete aggiungere un&#39;attività di attesa e pianificare i tentativi di flusso di lavoro.

I rifiuti vengono raccolti con il relativo codice di errore e il relativo messaggio, il che significa che è possibile impostare il tracciamento dei rifiuti per ottimizzare il processo di sincronizzazione.

Anche quando l&#39; **[!UICONTROL Process rejects]** opzione non è abilitata, viene generato un avviso per ogni colonna rifiutata con un codice di errore e un messaggio.

La transizione **[!UICONTROL Reject]** in uscita consente di accedere allo schema di output che contiene le colonne specifiche relative ai messaggi di errore e ai codici. Queste colonne sono:

* Per Oracle On Demand: **errorLogFilename** (nome del file di registro sul lato Oracle), **errorCode** (codice di errore), **errorSymbol** (simbolo di errore, diverso dal codice di errore), **errorMessage** (descrizione del contesto di errore).
* Per Salesforce.com: **errorSymbol** (simbolo di errore, diverso dal codice di errore), **errorMessage** (descrizione del contesto dell&#39;errore).

## Importazione di oggetti eliminati in CRM {#importing-objects-deleted-in-the-crm}

Per abilitare l&#39;impostazione di un ampio processo di sincronizzazione dei dati, puoi importare gli oggetti eliminati in CRM in  Adobe Campaign.

A questo scopo, eseguire i seguenti passaggi:

1. Selezionare un&#39; **[!UICONTROL Import objects deleted in the CRM]** operazione.
1. Fare clic sull&#39;elenco a **[!UICONTROL Remote object]** discesa e selezionare l&#39;oggetto interessato dal processo. Questo oggetto coincide con una delle tabelle create in  Adobe Campaign durante la configurazione del connettore.
1. Specificate il periodo di eliminazione da prendere in considerazione nei **[!UICONTROL Start date]** campi e nei **[!UICONTROL End date]** campi. Queste date verranno incluse nel periodo.

   ![](assets/crm_import_deleted_obj.png)

   >[!CAUTION]
   >
   >Il periodo di eliminazione degli elementi deve coincidere con le limitazioni specifiche del CRM. Ciò significa che per Salesforce.com, ad esempio, gli elementi eliminati oltre 30 giorni fa non possono essere recuperati.

## Eliminazione di oggetti in CRM {#deleting-objects-in-the-crm}

Per eliminare gli oggetti dal lato CRM, è necessario specificare la chiave primaria degli elementi remoti da eliminare.

![](assets/crm_delete_in_crm.png)

La **[!UICONTROL Behavior]** scheda consente di abilitare l&#39;elaborazione dei rifiuti. Questa opzione genera una seconda transizione di output per l&#39; **[!UICONTROL CRM connector]** attività. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/crm-connectors.md#error-processing).

Anche quando l&#39; **[!UICONTROL Process rejects]** opzione è disabilitata, viene generato un avviso per ogni colonna rifiutata.

## Esempio di configurazione di un&#39;importazione di contatti {#example-of-how-to-configure-a-contact-import}

Nell&#39;esempio seguente, l&#39;attività è configurata per importare contatti da un CRM Oracle On Demand. Prima di essere importati, i campi CRM vengono selezionati in modo che coincidano con quelli già esistenti nel database Adobe Campaign .

![](assets/crm_connectors_ood_6.png)

