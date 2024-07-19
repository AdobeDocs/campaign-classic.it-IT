---
product: campaign
title: Creare un elenco di riepilogo
description: Creare un elenco di riepilogo
feature: Workflows, Data Management
exl-id: 39cec42a-c7ac-41b1-8f61-799b559ce002
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 1%

---

# Creare un elenco di riepilogo{#creating-a-summary-list}



Questo caso d’uso descrive la creazione di un flusso di lavoro che, dopo aver raccolto i file e seguito diversi arricchimenti, ti consente di creare un elenco di riepilogo. L&#39;esempio si basa su un elenco di contatti che hanno effettuato acquisti in un negozio.

![](assets/uc2_enrich_overview.png)

Viene utilizzata la seguente struttura di dati:

![](assets/uc2_enrich_data.png)

Il suo obiettivo è:

* Per utilizzare le varie opzioni dell’attività di arricchimento
* Per aggiornare i dati nel database dopo una riconciliazione
* Creare una &quot;visualizzazione&quot; globale dei dati arricchiti

Per creare un elenco di riepilogo, è necessario seguire questi passaggi:

1. Raccolta e caricamento di un file &quot;Purchases&quot; nella tabella di lavoro del flusso di lavoro
1. Arricchimento dei dati importati creando un collegamento a una tabella di riferimento
1. Aggiornamento della tabella &quot;Acquisti&quot; con i dati arricchiti
1. Arricchimento dei dati &quot;Contatti&quot; con un calcolo aggregato dalla tabella &quot;Acquisti&quot;
1. Creazione di un elenco di riepilogo

## Passaggio 1: caricare il file e riconciliare i dati importati {#step-1--loading-the-file-and-reconciling-the-imported-data}

I dati da caricare sono dati relativi all’&quot;acquisto&quot; con il seguente formato:

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

1. Aggiungi le attività **Raccolta file** e **Caricamento dati (file)** al flusso di lavoro.

   L&#39;attività dell&#39;**Agente di raccolta file** consente di raccogliere e inviare file da e al server Adobe Campaign.

   L&#39;attività **Caricamento dati(file)** ti consente di arricchire la tabella di lavoro del flusso di lavoro con i dati raccolti.

   Per ulteriori informazioni su questa attività, consulta [Caricare dati da un file](../../platform/using/import-export-workflows.md#loading-data-from-a-file).

1. Configurare l&#39;attività **Raccoglitore file** per raccogliere i file di tipo testo (&#42;.txt) dalla directory selezionata.

   ![](assets/uc2_enrich_collecteur.png)

   L&#39;attività **Raccoglitore file** consente di gestire l&#39;assenza di un file nella directory di origine. Per eseguire questa operazione, selezionare l&#39;opzione **[!UICONTROL Process file nonexistence]**. In questo flusso di lavoro, è stata aggiunta un&#39;attività **Attendi** per provare un&#39;altra raccolta di file, se non è presente nella directory al momento della raccolta.

1. Configurare l&#39;attività **Caricamento dati (file)** utilizzando un file di esempio con lo stesso formato dei dati da importare.

   ![](assets/uc2_enrich_chargement1.png)

   Fare clic sul collegamento **[!UICONTROL Click here to change the file format...]** per rinominare le colonne utilizzando i nomi e le etichette interni della tabella &quot;Purchases&quot;.

   ![](assets/uc2_enrich_chargement2.png)

Una volta importati i dati, l’arricchimento viene eseguito creando un collegamento a una tabella di riferimento corrispondente allo schema &quot;Archivi&quot;.

Aggiungi l’attività Enrichment e configurala come segue:

1. Selezionare il set principale costituito dai dati dell&#39;attività **Caricamento dati (file)**.

   ![](assets/uc2_enrich_enrich1.png)

1. Fare clic su **[!UICONTROL Add data]**, quindi selezionare l&#39;opzione **[!UICONTROL A link]**.

   ![](assets/uc2_enrich_enrich2.png)

1. Selezionare l&#39;opzione **[!UICONTROL Define a collection]**.
1. Seleziona lo schema &quot;Archivi&quot; come destinazione.

   ![](assets/uc2_enrich_enrich3.png)

Per ulteriori informazioni sui vari tipi di collegamenti, vedere [Arricchimento e modifica dei dati](targeting-data.md#enriching-and-modifying-data).

Nella finestra seguente, è necessario creare una condizione di join selezionando il campo di origine (nel set principale) e il campo di destinazione (appartenente allo schema &quot;Archivi&quot;) per configurare la riconciliazione dei dati.

![](assets/uc2_enrich_enrich4.png)

Ora che il collegamento è stato creato, aggiungeremo una colonna alla tabella di lavoro del flusso di lavoro dallo schema &quot;Archivi&quot;: il campo &quot;Riferimento Codice postale&quot;.

1. Apri l’attività di arricchimento.
1. Fai clic su **[!UICONTROL Edit additional data]**.
1. Aggiungere il campo &quot;Riferimento Codice postale&quot; a **[!UICONTROL Output columns]**.

![](assets/uc2_enrich_enrich5.png)

I dati nella tabella di lavoro del flusso di lavoro dopo questo arricchimento saranno i seguenti:

![](assets/uc2_enrich_population1.png)

## Passaggio 2: scrittura di dati arricchiti nella tabella &#39;Acquisti&#39; {#step-2--writing-enriched-data-to-the--purchases--table}

Questo passaggio descrive come scrivere i dati importati e arricchiti nella tabella &quot;Purchases&quot;. A tale scopo, è necessario utilizzare un&#39;attività **Aggiorna dati**.

È necessario eseguire una riconciliazione tra i dati nella tabella di lavoro del flusso di lavoro e la dimensione di targeting **Purchases** prima di aggiornare i dati nella tabella **Purchases**.

1. Fare clic sulla scheda **[!UICONTROL Reconciliation]** dell&#39;attività di arricchimento.
1. In questo caso, seleziona la dimensione di targeting, lo schema &quot;Purchases&quot;.
1. Selezionare un&#39;&quot;espressione Source&quot; per i dati nella tabella del flusso di lavoro (in questo caso il campo &quot;storeName&quot;).
1. Selezionare un&#39;&quot;Espressione di destinazione&quot; per i dati nella tabella &quot;Acquisti&quot; (in questo caso il campo &quot;nome dello storename&quot;).
1. Seleziona l’opzione **[!UICONTROL Keep unreconciled data coming from the work table]**.

![](assets/uc2_enrich_reconciliation.png)

Nell&#39;attività **Aggiorna dati** è necessaria la seguente configurazione:

1. Selezionare l&#39;opzione **[!UICONTROL Insert or update]** nel campo **[!UICONTROL Operation type]** per evitare la creazione di nuovi record ogni volta che il file viene raccolto.
1. Selezionare il valore **[!UICONTROL By directly using the targeting dimension]** per l&#39;opzione **[!UICONTROL Record identification]**.
1. Selezionare lo schema &quot;Acquisti&quot; come **[!UICONTROL Document type]**.
1. Specifica l’elenco dei campi da aggiornare. La colonna **[!UICONTROL Destination]** consente di definire i campi dello schema &quot;Purchases&quot;. La colonna **[!UICONTROL Expression]** consente di selezionare i campi nella tabella di lavoro per eseguire una mappatura.
1. Fare clic sull&#39;opzione **[!UICONTROL Generate an outbound transition]**.

![](assets/uc2_enrich_miseajour.png)

## Passaggio 3: arricchire i dati dei contatti {#step-3--enriching--contact--data-}

Lo schema &quot;Contatti&quot; è fisicamente collegato allo schema &quot;Acquisti&quot;. Ciò significa che puoi utilizzare un’altra opzione dell’opzione &quot;Enrichment&quot;: aggiungere dati collegati alla dimensione di filtro.

Lo scopo di questo secondo arricchimento è quello di creare un aggregato sullo schema di acquisto per calcolare la quantità totale di acquisti per ciascun contatto identificato.

1. Aggiungi un&#39;attività di tipo **query** che consente di recuperare tutti i **contatti** archiviati.
1. Aggiungi un&#39;attività **Enrichment**, quindi seleziona il set principale risultante dalla query precedente.
1. Fare clic su Aggiungi **[!UICONTROL Data]**.
1. Fare clic sull&#39;opzione **[!UICONTROL Data linked to the targeting dimension]**.
1. Fare clic sull&#39;opzione **[!UICONTROL Data linked to the filtering dimension]** nella finestra **[!UICONTROL Select fields to add]**.
1. Selezionare il nodo **[!UICONTROL Purchases]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/uc2_enrich_enrich9.png)

1. Modificare il campo **[!UICONTROL Collected data]** selezionando l&#39;opzione **[!UICONTROL Aggregates]**.

   ![](assets/uc2_enrich_enrich10.png)

1. Fai clic su **[!UICONTROL Next]**.
1. Aggiungi la seguente espressione per calcolare il totale degli acquisti per ciascun contatto: &quot;Sum(@prodprice)&quot;.

   ![](assets/uc2_enrich_enrich6.png)

Per preparare l&#39;elenco di riepilogo, è necessario aggiungere campi dai campi &quot;Purchases&quot; e dal primo arricchimento: il campo &quot;ZipCode Reference&quot;.

1. Fare clic sul collegamento **[!UICONTROL Edit additional data...]** nell&#39;attività di arricchimento.
1. Aggiungi i campi &quot;Nome store&quot; e &quot;Purchases / Zip Code Reference&quot;.

   ![](assets/uc2_enrich_enrich7.png)

1. Fare clic sulla scheda **[!UICONTROL Properties]**.
1. Modifica il secondo collegamento per creare una sola riga.

   ![](assets/uc2_enrich_enrich8.png)

## Passaggio 4: creare e aggiungere a un elenco di riepilogo {#step-4--creating-and-adding-to-a-summary-list}

L’ultimo passaggio prevede la scrittura di tutti i dati arricchiti in un elenco.

1. Aggiungi un&#39;attività **Aggiornamento elenco** al flusso di lavoro. Questa attività deve essere collegata alla transizione in uscita della seconda attività di arricchimento.
1. Selezionare l&#39;opzione **[!UICONTROL Create the list if necessary (Calculated name)]**.
1. Selezionare un valore per il nome calcolato. L&#39;etichetta scelta per l&#39;elenco è la data corrente: &lt;%= formatDate(new Date(), &quot;%2D/%2M/%2Y&quot;) %>.

Una volta eseguito il flusso di lavoro, l’elenco include:

* un elenco di contatti,
* una colonna &quot;Acquisti totali&quot;,
* una colonna &quot;Nome del negozio&quot;,
* una colonna &quot;Riferimento codice postale&quot; immessa per tutti gli archivi contenuti nello schema di riferimento dello store.

![](assets/uc2_enrich_listfinal.png)
