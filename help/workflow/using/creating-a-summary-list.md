---
product: campaign
title: Creare un elenco di riepilogo
description: Creare un elenco di riepilogo
feature: Workflows, Data Management
exl-id: 39cec42a-c7ac-41b1-8f61-799b559ce002
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 2%

---

# Creare un elenco di riepilogo{#creating-a-summary-list}

![](../../assets/v7-only.svg)

Questo caso d’uso descrive la creazione di un flusso di lavoro che, dopo la raccolta dei file e dopo diversi arricchimenti, consente di creare un elenco di riepilogo. L&#39;esempio si basa su un elenco di contatti che hanno effettuato acquisti in un negozio.

![](assets/uc2_enrich_overview.png)

Viene utilizzata la seguente struttura dati:

![](assets/uc2_enrich_data.png)

Il suo scopo è:

* Utilizzare le varie opzioni dell’attività di arricchimento
* Per aggiornare i dati nel database dopo una riconciliazione
* Creare una &quot;visualizzazione&quot; globale dei dati arricchiti

Per creare un elenco di riepilogo, segui questi passaggi:

1. Raccolta e caricamento di un file &quot;Purchases&quot; nella tabella di lavoro del flusso di lavoro
1. Arricchimento dei dati importati creando un collegamento a una tabella di riferimento
1. Aggiornamento della tabella &quot;Acquisti&quot; con i dati arricchiti
1. Arricchimento dei dati &quot;Contatti&quot; con un calcolo aggregato dalla tabella &quot;Acquisti&quot;
1. Creazione di un elenco di riepilogo

## Passaggio 1: Caricare il file e riconciliare i dati importati {#step-1--loading-the-file-and-reconciling-the-imported-data}

I dati da caricare sono dati relativi all’acquisto con il seguente formato:

```
Product Name;Product price;Store
Computer;2000;London 3
Tablet;600;Cambridge
Computer;2000;London 5
Computer;2000;London 8
Tablet;600;Cambridge
Phone;500;London 5
```

Questi dati sono contenuti in un file di testo &quot;Purchases.txt&quot;.

1. Aggiungi il **Raccoglitore file** e **Caricamento dati (file)** al flusso di lavoro.

   La **Raccoglitore file** activity ti consente di raccogliere e inviare file da e al server Adobe Campaign.

   La **Caricamento dati (file)** consente di arricchire la tabella di lavoro del flusso di lavoro con i dati raccolti.

   Per ulteriori informazioni su questa attività, consulta [Caricare dati da un file](../../platform/using/import-export-workflows.md#loading-data-from-a-file).

1. Configura le **Raccoglitore file** attività per la raccolta del testo (&#42;.txt) digitare i file dalla directory selezionata.

   ![](assets/uc2_enrich_collecteur.png)

   La **Raccoglitore file** L’attività ti consente di gestire l’assenza di un file nella directory di origine. Per eseguire questa operazione, controlla il **[!UICONTROL Process file nonexistence]** opzione . In questo flusso di lavoro, un **Wait** è stata aggiunta l’attività per provare un’altra raccolta di file se manca dalla directory al momento della raccolta.

1. Configura le **Caricamento dati (file)** attività che utilizza un file di esempio con lo stesso formato dei dati da importare.

   ![](assets/uc2_enrich_chargement1.png)

   Fai clic sul pulsante **[!UICONTROL Click here to change the file format...]** collegamento per rinominare le colonne utilizzando i nomi e le etichette interni della tabella &quot;Acquisti&quot;.

   ![](assets/uc2_enrich_chargement2.png)

Una volta importati i dati, l’arricchimento viene effettuato creando un collegamento a una tabella di riferimento che corrisponde allo schema &quot;Stores&quot;.

Aggiungi l’attività Enrichment e configurala come segue:

1. Seleziona il set principale composto dai dati del **Caricamento dati (file)** attività.

   ![](assets/uc2_enrich_enrich1.png)

1. Fai clic su **[!UICONTROL Add data]**, quindi seleziona la **[!UICONTROL A link]** opzione .

   ![](assets/uc2_enrich_enrich2.png)

1. Seleziona la **[!UICONTROL Define a collection]** opzione .
1. Selezionare lo schema &quot;Memorizza&quot; come destinazione.

   ![](assets/uc2_enrich_enrich3.png)

Per ulteriori informazioni sui vari tipi di collegamenti, consulta [Arricchimento e modifica dei dati](targeting-data.md#enriching-and-modifying-data).

Nella finestra seguente, è necessario creare una condizione di unione selezionando il campo di origine (nel set principale) e il campo di destinazione (appartenente allo schema &quot;Stores&quot;) per configurare la riconciliazione dei dati.

![](assets/uc2_enrich_enrich4.png)

Ora che il collegamento è stato creato, aggiungeremo una colonna alla tabella di lavoro del flusso di lavoro dallo schema &quot;Stores&quot;: il campo &quot;ZipCode Reference&quot;.

1. Apri l’attività di arricchimento.
1. Fai clic su **[!UICONTROL Edit additional data]**.
1. Aggiungi il campo &quot;ZipCode Reference&quot; al **[!UICONTROL Output columns]**.

![](assets/uc2_enrich_enrich5.png)

I dati nella tabella di lavoro del flusso di lavoro dopo tale arricchimento saranno i seguenti:

![](assets/uc2_enrich_population1.png)

## Passaggio 2: Scrivi dati arricchiti nella tabella &quot;Acquisti&quot; {#step-2--writing-enriched-data-to-the--purchases--table}

Questo passaggio descrive come scrivere i dati importati e arricchiti nella tabella &quot;Acquisti&quot;. Per fare questo, dobbiamo utilizzare un **Update data** attività.

Una riconciliazione tra i dati nella tabella di lavoro del flusso di lavoro e il **Acquisti** la dimensione di targeting deve essere eseguita prima dei dati nel **Acquisti** tabella aggiornata.

1. Fai clic sul pulsante **[!UICONTROL Reconciliation]** scheda dell’attività di arricchimento.
1. Seleziona la dimensione di targeting, lo schema &quot;Acquisti&quot; in questo caso.
1. Seleziona un&#39;espressione &quot;Source&quot; per i dati nella tabella del flusso di lavoro (in questo caso il campo &quot;storeName&quot;).
1. Selezionare un&#39;&quot;espressione di destinazione&quot; per i dati nella tabella &quot;Acquisti&quot; (in questo caso il campo &quot;nome store&quot;).
1. Seleziona l’opzione **[!UICONTROL Keep unreconciled data coming from the work table]**.

![](assets/uc2_enrich_reconciliation.png)

In **Update data** attività , è necessaria la seguente configurazione:

1. Seleziona la **[!UICONTROL Insert or update]** in **[!UICONTROL Operation type]** per evitare la creazione di nuovi record ogni volta che il file viene raccolto.
1. Seleziona la **[!UICONTROL By directly using the targeting dimension]** valore per **[!UICONTROL Record identification]** opzione .
1. Seleziona lo schema &quot;Purchases&quot; come **[!UICONTROL Document type]**.
1. Specifica l’elenco dei campi da aggiornare. La **[!UICONTROL Destination]** consente di definire i campi dello schema &quot;Purchases&quot;. La **[!UICONTROL Expression]** consente di selezionare i campi nella tabella di lavoro per eseguire una mappatura.
1. Fai clic sul pulsante **[!UICONTROL Generate an outbound transition]** opzione .

![](assets/uc2_enrich_miseajour.png)

## Passaggio 3: Arricchisci i dati di &quot;contatto&quot; {#step-3--enriching--contact--data-}

Lo schema &quot;Contatti&quot; è fisicamente collegato allo schema &quot;Acquisti&quot;. Questo significa che puoi utilizzare un’altra opzione dell’opzione &quot;Enrichment&quot;: aggiunta di dati collegati alla dimensione di filtro.

Lo scopo di questo secondo arricchimento è quello di creare un aggregato sullo schema di acquisto per calcolare la quantità totale di acquisti per ogni contatto identificato.

1. Aggiungi un **query** digitare attività che consente di recuperare tutti **Contatti** memorizzato.
1. Aggiungi un **Arricchimento** quindi seleziona il set principale risultante dalla query precedente.
1. Fai clic su Aggiungi **[!UICONTROL Data]**.
1. Fai clic sul pulsante **[!UICONTROL Data linked to the targeting dimension]** opzione .
1. Fai clic sul pulsante **[!UICONTROL Data linked to the filtering dimension]** in **[!UICONTROL Select fields to add]** finestra.
1. Seleziona la **[!UICONTROL Purchases]** nodo quindi fai clic su **[!UICONTROL Next]**.

   ![](assets/uc2_enrich_enrich9.png)

1. Modificare la **[!UICONTROL Collected data]** selezionando il campo **[!UICONTROL Aggregates]** opzione .

   ![](assets/uc2_enrich_enrich10.png)

1. Fai clic su **[!UICONTROL Next]**.
1. Aggiungi la seguente espressione per calcolare il totale dell&#39;acquisto per ogni contatto: &quot;Sum(@prodprice)&quot;.

   ![](assets/uc2_enrich_enrich6.png)

Per preparare l’elenco di riepilogo, è necessario aggiungere campi dai campi &quot;Acquisti&quot; e dal primo arricchimento: il campo &quot;ZipCode Reference&quot;.

1. Fai clic sul pulsante **[!UICONTROL Edit additional data...]** collegamento nell’attività di arricchimento.
1. Aggiungi i campi &quot;Nome store&quot; e &quot;Riferimenti acquisti/Codice postale&quot;.

   ![](assets/uc2_enrich_enrich7.png)

1. Fai clic sul pulsante **[!UICONTROL Properties]** scheda .
1. Cambia il secondo collegamento per creare una sola riga.

   ![](assets/uc2_enrich_enrich8.png)

## Passaggio 4: Creare e aggiungere a un elenco di riepilogo {#step-4--creating-and-adding-to-a-summary-list}

L’ultimo passaggio consiste nel scrivere tutti i dati arricchiti in un elenco.

1. Aggiungi un **Aggiornamento elenco** al flusso di lavoro. Questa attività deve essere collegata alla transizione in uscita della seconda attività di arricchimento.
1. Seleziona la **[!UICONTROL Create the list if necessary (Calculated name)]** opzione .
1. Selezionare un valore per il nome calcolato. L’etichetta scelta per l’elenco è la data corrente: &lt;%= formatDate(new Date(), &quot;%2D/%2M/%2Y&quot;) %>.

Una volta eseguito il flusso di lavoro, l’elenco includerà:

* un elenco dei contatti,
* una colonna &quot;Totale acquisti&quot;,
* una colonna &quot;Nome del negozio&quot;,
* una colonna &quot;Riferimento codice postale&quot; immessa per tutti gli archivi contenuti nello schema di riferimento dell&#39;archivio.

![](assets/uc2_enrich_listfinal.png)
