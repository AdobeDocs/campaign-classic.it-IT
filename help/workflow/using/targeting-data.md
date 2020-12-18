---
solution: Campaign Classic
product: campaign
title: Dati di targeting
description: Ulteriori informazioni sul targeting dei dati in un flusso di lavoro
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1904'
ht-degree: 4%

---


# Dati di targeting{#targeting-data}

## Creazione di query {#creating-queries}

### Selezione dei dati {#selecting-data}

Un&#39;attività **[!UICONTROL Query]** consente di selezionare i dati di base per creare la popolazione di destinazione. Per ulteriori informazioni, vedere [Creazione di una query](../../workflow/using/query.md#creating-a-query).

Per eseguire query e perfezionare i dati del database è inoltre possibile utilizzare le attività seguenti: [Query incrementale](../../workflow/using/incremental-query.md), [Elenco di lettura](../../workflow/using/read-list.md).

È possibile raccogliere dati aggiuntivi da inoltrare ed elaborare per tutto il ciclo di vita del flusso di lavoro. Per ulteriori informazioni, vedere [Aggiunta di dati](../../workflow/using/query.md#adding-data) e [Modifica di dati aggiuntivi](#editing-additional-data).

### Modifica di dati aggiuntivi {#editing-additional-data}

Una volta aggiunti i dati aggiuntivi, è possibile modificarli o utilizzarli per ridefinire la destinazione definita nell&#39;attività di query.

Il collegamento **[!UICONTROL Edit additional data...]** consente di visualizzare i dati aggiunti e modificarli o aggiungerli.

![](assets/wf_add_data_edit_link.png)

Per aggiungere dati alle colonne di output definite in precedenza, selezionarle nell&#39;elenco dei campi disponibili. Per creare una nuova colonna di output, fare clic sull&#39;icona **[!UICONTROL Add]**, quindi selezionare il campo e fare clic su **[!UICONTROL Edit expression]**.

![](assets/query_add_an_output_column.png)

Definire una modalità di calcolo per il campo da aggiungere, ad esempio un aggregato.

![](assets/query_add_an_output_column_formula.png)

L&#39;opzione **[!UICONTROL Add a sub-item]** consente di allegare dati calcolati alla raccolta. Questo consente di selezionare i dati aggiuntivi dalla raccolta o definire i calcoli aggregati per gli elementi della raccolta.

![](assets/query_add_columns_subscription_sub-element.png)

I sottoelementi saranno rappresentati nella sottostruttura della raccolta a cui sono mappati.

Le raccolte sono visualizzate nella sottoscheda **[!UICONTROL Collections]**. Potete filtrare gli elementi raccolti facendo clic sull&#39;icona **[!UICONTROL Detail]** della raccolta selezionata. La procedura guidata filtro consente di selezionare i dati raccolti e specificare le condizioni di filtraggio da applicare ai dati della raccolta.

![](assets/query_add_columns_collection.png)

### Ottimizzazione della destinazione utilizzando dati aggiuntivi {#refining-the-target-using-additional-data}

I dati aggiuntivi raccolti possono consentire di perfezionare il filtraggio dei dati nel database. A tale scopo, fare clic sul collegamento **[!UICONTROL Refine the target using additional data...]**: questo consente di filtrare eccessivamente i dati aggiunti.

![](assets/wf_add_data_use_additional_data.png)

### Omogenealizzazione dei dati {#homogenizing-data}

Nelle attività di tipo **[!UICONTROL Union]** o **[!UICONTROL Intersection]**, è possibile scegliere di conservare solo i dati aggiuntivi condivisi per mantenere la coerenza dei dati. In questo caso, la tabella di lavoro dell&#39;output temporaneo di questa attività conterrà solo i dati aggiuntivi rilevati in tutti i set in entrata.

![](assets/option-common_additionnal_col_only.png)

### Riconciliazione con dati aggiuntivi {#reconciliation-with-additional-data}

Durante le fasi di riconciliazione dei dati (**[!UICONTROL Union]**, **[!UICONTROL Intersection]**, ecc. attività), è possibile selezionare le colonne da utilizzare per la riconciliazione dei dati dalle colonne aggiuntive. A questo scopo, configurate una riconciliazione su una selezione di colonne e specificate il set principale. Selezionate quindi le colonne nella colonna inferiore della finestra, come illustrato nell’esempio seguente:

![](assets/select-column-and-join.png)

### Creazione di sottoinsiemi {#creating-subsets}

L&#39;attività **[!UICONTROL Split]** consente di creare sottoinsiemi in base a criteri definiti tramite query di estrazione. Per ciascun sottoinsieme, quando si modifica una condizione di filtro sulla popolazione, si accede all&#39;attività di query standard che consente di definire le condizioni di segmentazione di destinazione.

Potete dividere una destinazione in più sottoinsiemi utilizzando solo dati aggiuntivi come condizioni di filtraggio, o in aggiunta ai dati di destinazione. È inoltre possibile utilizzare dati esterni se è stata acquistata l&#39;opzione **Federated Data Access**.

Per ulteriori informazioni, vedere [Creazione di sottoinsiemi tramite l&#39;attività Dividi](#creating-subsets-using-the-split-activity).

## Segmentazione dei dati {#segmenting-data}

### Combinazione di più obiettivi (Unione) {#combining-several-targets--union-}

L&#39;attività dell&#39;unione consente di combinare il risultato di diverse attività all&#39;interno di un&#39;unica transizione. I set non devono necessariamente essere omogenei.

![](assets/join_reconciliation_options.png)

Sono disponibili le seguenti opzioni di riconciliazione dei dati:

* **[!UICONTROL Keys only]**

   Questa opzione può essere utilizzata se le popolazioni di input sono omogenee.

* **[!UICONTROL All columns in common]**

   Questa opzione consente di riconciliare i dati in base a tutte le colonne comuni alle diverse popolazioni della destinazione.

    Adobe Campaign identifica le colonne in base al nome. È accettata una soglia di tolleranza: ad esempio, una colonna &#39;E-mail&#39; può essere riconosciuta identica a una colonna &#39;@email&#39;.

* **[!UICONTROL A selection of columns]**

   Selezionare questa opzione per definire l&#39;elenco delle colonne a cui verrà applicata la riconciliazione dei dati.

   Per iniziare, selezionate il set principale (quello contenente i dati di origine), quindi le colonne da utilizzare per il join.

   ![](assets/join_reconciliation_options_01.png)

   >[!CAUTION]
   >
   >Durante la riconciliazione dei dati, le popolazioni non vengono deduplicate.

   È possibile limitare la dimensione della popolazione a un determinato numero di record. A tal fine, fare clic sull&#39;opzione appropriata e specificare il numero di record da conservare.

   Inoltre, specificate la priorità delle popolazioni in entrata: la sezione inferiore della finestra elenca le transizioni in entrata dell&#39;attività dell&#39;unione e consente di ordinarle utilizzando le frecce blu a destra della finestra.

   I record saranno presi prima dalla popolazione della prima transizione in entrata nella lista, quindi, se il massimo non è stato raggiunto, saranno presi dalla popolazione della seconda transizione in ingresso, ecc.

   ![](assets/join_limit_nb_priority.png)

### Estrazione di dati comuni (intersezione) {#extracting-joint-data--intersection-}

![](assets/traitements.png)

L&#39;intersezione consente di recuperare solo le righe condivise dalle popolazioni di transizioni in entrata. Questa attività deve essere configurata come l&#39;attività dell&#39;unione.

Inoltre, è possibile mantenere solo una selezione di colonne, o solo le colonne condivise dalla popolazione in entrata.

L&#39;attività di intersezione è dettagliata nella sezione [Intersezione](../../workflow/using/intersection.md).

### Esclusione di una popolazione (Esclusione) {#excluding-a-population--exclusion-}

L&#39;attività di esclusione consente di escludere gli elementi di un target da una popolazione target diversa. La dimensione di targeting dell&#39;output di questa attività sarà quella del set principale.

Se necessario, è possibile manipolare le tabelle in entrata. Infatti, per escludere un target da un&#39;altra dimensione, questo obiettivo deve essere restituito alla stessa dimensione di targeting dell&#39;obiettivo principale. A questo scopo, fare clic sul pulsante **[!UICONTROL Add]** e specificare le condizioni di modifica della dimensione.

La riconciliazione dei dati viene eseguita tramite un identificatore, un asse di modifica o un join. Un esempio è disponibile in [Uso dei dati da un elenco: Read list](../../workflow/using/importing-data.md#using-data-from-a-list--read-list).

![](assets/exclusion_edit_add_rule_01.png)

### Creazione di sottoinsiemi tramite l&#39;attività Dividi {#creating-subsets-using-the-split-activity}

L&#39;attività **[!UICONTROL Split]** è un&#39;attività standard che consente di creare tutti i set necessari tramite una o più dimensioni di filtraggio, nonché di generare una transizione di output per sottoinsieme o una transizione univoca.

I dati aggiuntivi trasmessi dalla transizione in entrata possono essere utilizzati nei criteri di filtro.

Per configurarlo, è innanzitutto necessario selezionare i criteri:

1. Nel flusso di lavoro, trascinate e rilasciate un&#39;attività **[!UICONTROL Split]**.
1. Nella scheda **[!UICONTROL General]**, selezionare l&#39;opzione desiderata: **[!UICONTROL Use data from the target and additional data]**, **[!UICONTROL Use the additional data only]** o **[!UICONTROL Use external data]**.
1. Se l&#39;opzione **[!UICONTROL Use data from the target and additional data]** è selezionata, la dimensione di targeting consente di utilizzare tutti i dati trasmessi dalla transizione in entrata.

   ![](assets/split-general-tab-options.png)

   Quando si creano i sottoinsiemi, vengono utilizzati i parametri di filtro indicati sopra.

   Per definire le condizioni di filtro, scegliete l&#39;opzione **[!UICONTROL Add a filtering condition on the inbound population]** e fate clic sul collegamento **[!UICONTROL Edit...]**. Quindi specificate le condizioni di filtraggio per creare questo sottoinsieme.

   ![](assets/split-subset-config-all-data.png)

   Un esempio che mostra come utilizzare le condizioni di filtraggio nell&#39;attività **[!UICONTROL Split]** per segmentare la destinazione in popolazioni diverse è descritto in [questa sezione](../../workflow/using/cross-channel-delivery-workflow.md).

   Il campo **[!UICONTROL Label]** consente di assegnare al sottoinsieme appena creato un nome che corrisponda alla transizione in uscita.

   È inoltre possibile assegnare un codice del segmento al sottoinsieme per identificarlo e utilizzarlo per il targeting della popolazione.

   Se necessario, potete modificare le dimensioni di targeting e filtro singolarmente per ciascun sottoinsieme da creare. A questo scopo, modificate la condizione di filtraggio del sottoinsieme e verificate l&#39;opzione **[!UICONTROL Use a specific filtering dimension]**.

   ![](assets/split-subset-config-specific-filtering.png)

1. Se è selezionata l&#39;opzione **[!UICONTROL Use the additional data only]**, per il filtro dei sottoinsiemi vengono offerti solo dati aggiuntivi.

   ![](assets/split-subset-config-additional-data-only.png)

1. Se l&#39;opzione **Federated Data Access** è abilitata, **[!UICONTROL Use external data]** consente di elaborare i dati in un database esterno già configurato oppure di creare una nuova connessione a un database.

   ![](assets/split-subset-config-add_external_data.png)

   Per ulteriori informazioni, consulta questa [sezione](../../installation/using/about-fda.md).

Quindi, è necessario aggiungere nuovi sottoinsiemi:

1. Fare clic sul pulsante **[!UICONTROL Add]** e definire le condizioni di filtraggio.

   ![](assets/wf_split_add_a_tab.png)

1. Definite la dimensione di filtraggio nella scheda **[!UICONTROL General]** dell&#39;attività (vedete sopra).Si applica a tutti i sottoinsiemi per impostazione predefinita.

   ![](assets/wf_split_edit_filtering.png)

1. Se necessario, potete modificare singolarmente la dimensione di filtro per ciascun sottoinsieme. Questo consente di creare un set per tutti i possessori di carte Gold, uno per tutti i destinatari che hanno fatto clic sulla newsletter più recente e un terzo per le persone di età compresa tra i 18 e i 25 anni che hanno effettuato un acquisto in-store negli ultimi 30 giorni, utilizzando la stessa attività di divisione. A questo scopo, selezionare l&#39;opzione **[!UICONTROL Use a specific filtering dimension]** e selezionare il contesto di filtraggio dei dati.

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >Se avete acquisito l&#39;opzione **Federated Data Access**, potete creare sottoinsiemi in base alle informazioni in una base esterna. A tal fine, selezionare lo schema della tabella esterna nel campo **[!UICONTROL Targeting dimension]**. Per ulteriori informazioni, vedere [Accesso a un database esterno (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

Una volta creati i sottoinsiemi, per impostazione predefinita l&#39;attività divisa mostra tutte le transizioni di output possibili:

![](assets/wf_split_multi_outputs.png)

Potete raggruppare tutti questi sottoinsiemi in una singola transizione di output. In questo caso, il collegamento ai rispettivi sottoinsiemi sarà visibile, ad esempio, nel codice del segmento. A questo scopo, selezionare l&#39;opzione **[!UICONTROL Generate all subsets in the same table]**.

![](assets/wf_split_select_option_single_output.png)

Ad esempio, puoi inserire una singola attività di consegna e personalizzare il contenuto di consegna in base al codice del segmento di ciascun set di destinatari:

![](assets/wf_split_single_output.png)

I sottoinsiemi possono essere creati anche utilizzando l&#39;attività **[!UICONTROL Cells]**. Per ulteriori informazioni, consultare la sezione [Celle](../../workflow/using/cells.md).

### Utilizzo di dati di destinazione {#using-targeted-data}

Una volta identificati e preparati, i dati possono essere utilizzati nei seguenti contesti:

* È possibile aggiornare i dati nel database dopo la manipolazione dei dati nelle varie fasi del flusso di lavoro.

   Per ulteriori informazioni, [Aggiorna dati](../../workflow/using/update-data.md).

* Potete anche aggiornare il contenuto degli elenchi esistenti.

   Per ulteriori informazioni, fare riferimento a [Aggiornamento elenco](../../workflow/using/list-update.md).

* Puoi preparare o avviare direttamente le consegne nel flusso di lavoro.

   Per ulteriori informazioni, vedere [Consegna](../../workflow/using/delivery.md), [Controllo consegna](../../workflow/using/delivery-control.md) e [Consegna continua](../../workflow/using/continuous-delivery.md).

## Gestione dei dati {#data-management}

In  Adobe Campaign, Data Management combina una serie di attività per risolvere problemi di targeting complessi offrendo strumenti più efficienti e flessibili. Questo consente di implementare una gestione coerente di tutte le comunicazioni con un contatto utilizzando le informazioni relative ai contratti, alle sottoscrizioni, alla reattività alle consegne, ecc. La gestione dati ti consente di eseguire il tracciamento del ciclo di vita dei dati durante le operazioni di segmentazione, in particolare:

* Semplificazione e ottimizzazione dei processi di targeting, includendo dati non modellati nel data mart (creazione di nuove tabelle: estensione locale per ogni flusso di lavoro di targeting, a seconda della configurazione).
* Mantenimento e trasmissione dei calcoli di buffer, soprattutto durante le fasi di costruzione del target o per l’amministrazione del database.
* Accesso a basi esterne (facoltativo): database eterogenei presi in considerazione durante il processo di targeting.

Per implementare queste operazioni,  Adobe Campaign offre:

* Attività di raccolta dati: [Trasferimento file](../../workflow/using/file-transfer.md), [Caricamento dati (file)](../../workflow/using/data-loading--file-.md), [Caricamento dati (RDBMS)](../../workflow/using/data-loading--rdbms-.md), [Aggiornamento dati](../../workflow/using/update-data.md). Questa prima fase della raccolta dei dati prepara i dati per consentirne l&#39;elaborazione in altre attività. È necessario monitorare diversi parametri per garantire che il flusso di lavoro venga eseguito correttamente e fornire i risultati previsti. Ad esempio, quando si importano i dati, la chiave primaria (Pkey) per questi dati deve essere univoca per ciascun record.
* Il targeting delle attività è stato arricchito con le opzioni di gestione dei dati: [Query](../../workflow/using/query.md), [Unione](../../workflow/using/union.md), [Intersezione](../../workflow/using/intersection.md), [Dividi](../../workflow/using/split.md). Questo consente di configurare un&#39;unione o un&#39;intersezione tra dati provenienti da diverse dimensioni di targeting, purché sia possibile la riconciliazione dei dati.
* Attività di trasformazione dei dati: [Arricchimento](../../workflow/using/enrichment.md), [Modifica dimensione](../../workflow/using/change-dimension.md).

>[!CAUTION]
>
>Quando due flussi di lavoro sono collegati, l&#39;eliminazione di un elemento tabella di origine non comporta l&#39;eliminazione di tutti i dati ad esso collegati.
>  
>Ad esempio, l&#39;eliminazione di un destinatario tramite un flusso di lavoro non comporta l&#39;eliminazione di tutta la cronologia di consegna del destinatario. Tuttavia, eliminando un destinatario direttamente nella cartella &quot;Destinatari&quot;, tutti i dati collegati a tale destinatario verranno effettivamente eliminati.

### Arricchimento e modifica dei dati {#enriching-and-modifying-data}

Oltre alla dimensione di targeting, la dimensione di filtro consente di specificare la natura dei dati raccolti. Fare riferimento a [Dimensioni di targeting e filtro](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

I dati identificati e raccolti possono essere arricchiti, aggregati e manipolati per ottimizzare la costruzione del target. A questo scopo, oltre alle attività di manipolazione dei dati descritte nella sezione [Segmentazione dei dati](#segmenting-data), utilizza quanto segue:

* L&#39;attività **[!UICONTROL Enrichment]** consente di aggiungere momentaneamente le colonne a uno schema, nonché di aggiungere informazioni ad alcuni elementi. È descritto nella sezione [Arricchimento](../../workflow/using/enrichment.md) del repository delle attività.
* L&#39;attività **[!UICONTROL Edit schema]** consente di modificare la struttura di uno schema. È dettagliata nella sezione [Modifica schema](../../workflow/using/edit-schema.md) del repository delle attività.
* L&#39;attività **[!UICONTROL Change dimension]** consente di modificare la dimensione di targeting durante il ciclo di costruzione di destinazione. È illustrato nella sezione [Cambia dimensione](../../workflow/using/change-dimension.md).

