---
solution: Campaign Classic
product: campaign
title: Creazione di un flusso di lavoro
description: Scopri come creare un flusso di lavoro
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 3%

---


# Creazione di un flusso di lavoro {#building-a-workflow}

Questa sezione descrive i principi chiave e le procedure ottimali per creare un flusso di lavoro in Campaign.

* Creare un flusso di lavoro, vedere [Creazione di un nuovo flusso di lavoro](#creating-a-new-workflow)
* Progettare il diagramma del flusso di lavoro, vedere [Aggiunta e collegamento di attività](#adding-and-linking-activities)
* Accedere ai parametri e alle proprietà delle attività, vedere [Configurazione delle attività](#configuring-activities)
* Progettazione di flussi di lavoro di targeting, vedi Flussi di lavoro [di targeting](#targeting-workflows)
* Utilizza i flussi di lavoro per eseguire una campagna, vedi Flussi di lavoro [campagna](#campaign-workflows)
* Accesso e creazione di flussi di lavoro tecnici, consulta Flussi di lavoro [tecnici](#technical-workflows)
* Utilizzare i modelli per creare flussi di lavoro, vedere Modelli di [flusso di lavoro](#workflow-templates)

## Creating a new workflow {#creating-a-new-workflow}

Dalla cartella **[!UICONTROL Explorer]**, accedete a una cartella del flusso di lavoro. Per impostazione predefinita, è possibile utilizzare **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.

Fate clic sul **[!UICONTROL New]** pulsante situato sopra l’elenco dei flussi di lavoro.

![](assets/create_a_wf_icon.png)

Oppure, potete anche usare il **[!UICONTROL Create]** pulsante nella panoramica del flusso di lavoro (**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]** collegamento).

![](assets/create_a_wf.png)

Immettete un’etichetta e fate clic su **[!UICONTROL Save]**.

>[!NOTE]
>
>Quando modificate il nome interno di un&#39;attività del flusso di lavoro o il flusso di lavoro stesso, accertatevi di salvare il flusso di lavoro prima di chiuderlo in modo che il nuovo nome interno sia correttamente preso in considerazione.

## Aggiunta e collegamento di attività {#adding-and-linking-activities}

Devi ora definire le varie attività e collegarle nel diagramma. A questo punto della configurazione, è possibile visualizzare l’etichetta del diagramma e lo stato del flusso di lavoro (Modifica in corso). La sezione inferiore della finestra viene utilizzata solo per modificare il diagramma. Contiene una barra degli strumenti, una palette di attività (a sinistra) e il diagramma stesso (a destra).

![](assets/new-workflow-2.png)

>[!NOTE]
>
>Se la palette non è visualizzata, fare clic sul primo pulsante sulla barra degli strumenti per visualizzarla.

Le attività sono raggruppate per categoria all&#39;interno delle diverse schede della palette. Le schede e le attività disponibili possono variare a seconda del tipo di flusso di lavoro (tecnico, di targeting o del flusso di lavoro della campagna).

* La prima scheda contiene attività di targeting e manipolazione dei dati. Tali attività sono dettagliate nelle attività [di](../../workflow/using/about-targeting-activities.md)targeting.
* La seconda scheda contiene le attività di programmazione, utilizzate principalmente per coordinare altre attività. Tali attività sono descritte in dettaglio nelle attività [di controllo del](../../workflow/using/about-flow-control-activities.md)flusso.
* La terza scheda contiene gli strumenti e le azioni che è possibile utilizzare nel flusso di lavoro. Tali attività sono descritte in dettaglio nelle attività [](../../workflow/using/about-action-activities.md)d&#39;azione.
* La quarta scheda contiene le attività che dipendono da un determinato evento, ad esempio la ricezione di un&#39;e-mail o l&#39;arrivo di un file su un server. Tali attività sono dettagliate nelle attività [](../../workflow/using/about-event-activities.md)Evento.

Per creare il diagramma

1. Per aggiungere un&#39;attività, selezionatela nella palette e spostatela nel diagramma mediante un&#39;operazione di trascinamento.

   Add a **Start** activity and then a **Delivery** activity on the diagram.

   ![](assets/new-workflow-3.png)

1. Link the activities together by dragging the **Start** activity transition and dropping it on to the **Delivery** activity.

   ![](assets/new-workflow-4.png)

   Potete collegare automaticamente un&#39;attività alla precedente inserendo la nuova attività alla fine della transizione.

1. Aggiungi le attività necessarie e collegale come mostrato nel diagramma seguente.

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>Potete copiare e incollare le attività all’interno di uno stesso flusso di lavoro. Tuttavia, non è consigliabile copiare le attività Incolla tra flussi di lavoro diversi. Alcune impostazioni associate ad attività quali Consegne e Utilità di pianificazione potrebbero causare conflitti ed errori durante l&#39;esecuzione del flusso di lavoro di destinazione. È stato invece consigliato di **duplicare** i flussi di lavoro. Per ulteriori informazioni, vedere [Duplicazione dei flussi di lavoro](#duplicating-workflows).

È possibile modificare la visualizzazione e il layout del grafico utilizzando i seguenti elementi:

* **Utilizzo della barra degli strumenti**

   La barra degli strumenti di modifica del diagramma consente di accedere alle funzioni di layout ed esecuzione del flusso di lavoro.

   ![](assets/s_user_segmentation_wizard_10.png)

   Questo consente di adattare il layout dello strumento di modifica: visualizzazione della palette e panoramica, dimensioni e allineamento degli oggetti grafici.

   ![](assets/s_user_segmentation_toolbar.png)

   Le icone relative al tracciamento e all&#39;avvio di un flusso di lavoro di targeting avanzato sono descritte in dettaglio in questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **Allineamento dell&#39;oggetto**

   Per allineare le icone, selezionatele e fate clic sull’icona **[!UICONTROL Align vertically]** o **[!UICONTROL Align horizontally]** .

   Utilizzate il tasto **CTRL** per selezionare più attività sparse o per deselezionare una o più attività. Fare clic sullo sfondo del diagramma per deselezionare tutti gli elementi.

* **Gestione delle immagini**

   Potete personalizzare l&#39;immagine di sfondo del diagramma e quelle relative alle varie attività. Consultate [Gestione delle immagini](../../workflow/using/managing-activity-images.md)dell&#39;attività.

## Configurazione delle attività {#configuring-activities}

Fate doppio clic su un&#39;attività per configurarla oppure fate clic con il pulsante destro del mouse e selezionate **[!UICONTROL Open...]**.

>[!NOTE]
>
>Le attività del flusso di lavoro delle campagne sono descritte in [questa sezione](../../workflow/using/about-activities.md).

La prima scheda contiene la configurazione di base. La **[!UICONTROL Advanced]** scheda contiene i parametri aggiuntivi, utilizzati in particolare per definire il comportamento quando si verifica un errore, specificare la durata di esecuzione di un&#39;attività e immettere uno script di inizializzazione.

Per una migliore comprensione delle attività e per migliorare la leggibilità del flusso di lavoro, potete inserire commenti nelle attività: questi vengono visualizzati automaticamente quando gli operatori scorrono l&#39;attività.

![](assets/example1-comment.png)

## Flussi di lavoro di targeting {#targeting-workflows}

I flussi di lavoro di targeting consentono di creare diversi target di consegna. Potete creare query, definire unioni o esclusioni in base a criteri specifici, aggiungere la pianificazione, grazie alle attività del flusso di lavoro. Il risultato di questo targeting può essere trasferito automaticamente a un elenco che può fungere da destinazione delle azioni di consegna

Oltre a queste attività, le opzioni di gestione dei dati consentono di manipolare i dati e accedere a funzioni avanzate per risolvere problemi di targeting complessi. For more on this, refer to [Data Management](../../workflow/using/targeting-data.md#data-management).

Tutte queste attività si trovano nella prima scheda del flusso di lavoro.

>[!NOTE]
>
>Le attività di targeting sono descritte in [questa sezione](../../workflow/using/about-activities.md).

I flussi di lavoro di targeting possono essere creati e modificati tramite il **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nodo della struttura di Adobe Campaign  o tramite il **[!UICONTROL Profiles and Targets > Targeting workflows]** menu della home page.

![](assets/target_wf.png)

I flussi di lavoro di targeting nel quadro di una campagna vengono memorizzati con tutti i flussi di lavoro delle campagne.

### Passaggi chiave per creare un flusso di lavoro di targeting {#implementation-steps-}

I passaggi per creare un flusso di lavoro di targeting sono descritti in dettaglio nelle seguenti sezioni:

1. **Identificare** i dati nel database - Vedere [Creazione di query](../../workflow/using/targeting-data.md#creating-queries)
1. **Preparare** i dati per soddisfare le esigenze di distribuzione - Vedere [Arricchimento e modifica dei dati](../../workflow/using/targeting-data.md#enriching-and-modifying-data)
1. **Utilizzare** i dati per eseguire aggiornamenti o all&#39;interno di una consegna - Vedere [Aggiornamento del database](../../workflow/using/how-to-use-workflow-data.md#updating-the-database)

I risultati di tutti gli arricchimenti e tutte le operazioni eseguite durante il targeting sono memorizzati e accessibili in campi di personalizzazione, in particolare per la creazione di messaggi personalizzati. For more on this, refer to [Target data](../../workflow/using/data-life-cycle.md#target-data)

### Dimensioni di targeting e filtro {#targeting-and-filtering-dimensions}

Durante le operazioni di segmentazione dei dati, la chiave di targeting è mappata su una dimensione di filtro. La dimensione di targeting consente di definire la popolazione di destinazione dell&#39;operazione: destinatari, beneficiari del contratto, operatori, abbonati, ecc. La dimensione di filtro consente di selezionare la popolazione in base a determinati criteri: titolari di contratti, abbonati a newsletter, ecc.

Ad esempio, per selezionare i clienti che hanno sottoscritto una polizza di assicurazione vita per oltre 5 anni, selezionare la dimensione di targeting seguente: **Client** e le seguenti dimensioni filtro: **Titolare** del contratto. È quindi possibile definire le condizioni di filtraggio all&#39;interno dell&#39;attività di query

Durante la fase di selezione della dimensione di targeting, nell&#39;interfaccia sono disponibili solo dimensioni di filtraggio compatibili.

Queste due dimensioni devono essere correlate. Pertanto, il contenuto dell&#39; **[!UICONTROL Filtering dimension]** elenco dipende dalla dimensione di targeting specificata nel primo campo.

Ad esempio, per i destinatari (**destinatari**) saranno disponibili le seguenti dimensioni di filtro:

![](assets/query_filter_target_dimensions_1.png)

Per le applicazioni **** Web, l&#39;elenco conterrà le seguenti dimensioni di filtro:

![](assets/query_filter_target_dimensions_2.png)

## Flussi di lavoro campagna {#campaign-workflows}

Per ogni campagna, puoi creare flussi di lavoro da eseguire dalla **[!UICONTROL Targeting and workflows]** scheda. Questi flussi di lavoro sono specifici per la campagna.

![](assets/wf-in-op-edit-delivery-tab.png)

Questa scheda contiene le stesse attività di tutti i flussi di lavoro. [Ulteriori informazioni](#implementation-steps-)

Oltre alle campagne di targeting, i flussi di lavoro delle campagne consentono di creare e configurare le consegne per tutti i canali disponibili. Una volta creati nel flusso di lavoro, questi invii sono disponibili dal dashboard della campagna. [Ulteriori informazioni](../../campaign/using/marketing-campaign-deliveries.md)

Tutti i flussi di lavoro delle campagne sono centralizzati sotto il **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** nodo.

![](assets/campaigns_wf.png)

I flussi di lavoro delle campagne e gli esempi di implementazione sono descritti in [questa pagina](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

## Flussi di lavoro tecnici {#technical-workflows}

I flussi di lavoro tecnici vengono forniti con  Adobe Campaign. Si tratta di operazioni o processi pianificati per l&#39;esecuzione periodica sul server. Consentono di eseguire la manutenzione sul database, inoltrare le informazioni di monitoraggio sulle consegne e impostare i processi provvisori sulle consegne. I flussi di lavoro tecnici sono configurati tramite il **[!UICONTROL Administration > Production > Technical workflows]** nodo.

![](assets/navtree.png)

Sono disponibili modelli nativi per la creazione di flussi di lavoro tecnici. Possono essere configurate in base alle vostre esigenze.

La **[!UICONTROL Campaign process]** sottocartella centralizza i flussi di lavoro necessari per eseguire i processi all&#39;interno delle campagne: notifica delle attività, gestione delle scorte, calcolo dei costi, ecc.

>[!NOTE]
>
>L&#39;elenco dei flussi di lavoro tecnici installati con ciascun modulo è disponibile in una sezione [](../../workflow/using/about-technical-workflows.md)dedicata.

Puoi creare altri flussi di lavoro tecnici nel **[!UICONTROL Administration > Production > Technical workflows]** nodo della struttura ad albero. Tuttavia, questo processo è riservato agli utenti esperti.

Le attività offerte sono le stesse che per i flussi di lavoro di targeting. [Ulteriori informazioni](#implementation-steps-)

## Modelli per flussi di lavoro {#workflow-templates}

I modelli di workflow contengono la configurazione globale delle proprietà ed eventualmente una serie di attività concatenate all&#39;interno di un diagramma. Questa configurazione può essere riutilizzata per creare nuovi flussi di lavoro contenenti un certo numero di elementi preconfigurati

Potete creare nuovi modelli di flusso di lavoro basati su modelli esistenti o modificare direttamente un flusso di lavoro in un modello.

I modelli di flusso di lavoro sono memorizzati nel **[!UICONTROL Resources > Templates > Workflow templates]** nodo della struttura di Adobe Campaign .

![](assets/s_advuser_wf_template_tree.png)

Oltre alle normali proprietà del flusso di lavoro, le proprietà del modello consentono di specificare il file di esecuzione per i flussi di lavoro creati in base a questo modello.

![](assets/s_advuser_wf_template_properties.png)

## Duplicazione dei flussi di lavoro {#duplicating-workflows}

Potete duplicare diversi tipi di flussi di lavoro. Una volta eseguita la duplicazione, le modifiche del flusso di lavoro non vengono riportate nella copia del flusso di lavoro.

>[!CAUTION]
>
>Copia-incolla è disponibile nei flussi di lavoro, ma consigliamo di utilizzare **Duplica**. Una volta copiata un&#39;attività, viene mantenuta l&#39;intera configurazione. Per le attività di consegna (E-mail, SMS, Push Notification...), viene copiato anche l&#39;oggetto di consegna allegato all&#39;attività, il che può causare l&#39;arresto anomalo.

1. Fare clic con il pulsante destro del mouse su un flusso di lavoro.
1. Fate clic su **Duplica**.

   ![](assets/duplicate-workflows.png)

1. Nella finestra del flusso di lavoro, modificate l’etichetta del flusso di lavoro.
1. Fai clic su **Salva**.

La funzione duplicata non è direttamente disponibile nella visualizzazione di una campagna.

Tuttavia, potete creare una vista per visualizzare tutti i flussi di lavoro sull’istanza. In questa visualizzazione, puoi duplicare i flussi di lavoro utilizzando la funzione **Duplica**.

**Innanzitutto, creiamo una vista:**

1. In **Esplora risorse**, passate alla cartella in cui desiderate creare la visualizzazione.
1. Fare clic con il pulsante destro del mouse e passare a **Aggiungi una nuova cartella** > **Processo**, selezionare **Flussi di lavoro**.

   ![](assets/add-new-folder-workflows.png)

Viene creata la nuova cartella **Flussi** di lavoro.

1. Fare clic con il pulsante destro del mouse e selezionare **Proprietà**.
1. In **Limitazione**, seleziona **Cartella è una visualizzazione** e fai clic su **Salva**.

   ![](assets/folder-is-a-view.png)

La cartella ora viene compilata con tutti i flussi di lavoro dell&#39;istanza.

**Duplicazione di un flusso di lavoro della campagna**

1. Selezionate un flusso di lavoro della campagna nella visualizzazione del flusso di lavoro.
1. Fare clic con il pulsante destro del mouse su **Duplica**.
   ![](assets/duplicate-to-right-click.png)
1. Modificatene l’etichetta.
1. Fai clic su **Salva**.

Potete visualizzare il flusso di lavoro duplicato nella visualizzazione del flusso di lavoro.
