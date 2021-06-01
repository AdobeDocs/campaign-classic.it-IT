---
product: campaign
title: Creazione di un flusso di lavoro
description: Scopri come creare un flusso di lavoro
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 3%

---

# Creazione di un flusso di lavoro {#building-a-workflow}

Questa sezione descrive i principi chiave e le best practice per creare un flusso di lavoro in Campaign.

* Crea un flusso di lavoro, vedi [Creazione di un nuovo flusso di lavoro](#creating-a-new-workflow)
* Progettazione del diagramma del flusso di lavoro, consulta [Aggiunta e collegamento di attività](#adding-and-linking-activities)
* Accedi ai parametri e alle proprietà delle attività, consulta [Configurazione delle attività](#configuring-activities)
* Progettare i flussi di lavoro di targeting, consulta [Targeting dei flussi di lavoro](#targeting-workflows)
* Utilizzare i flussi di lavoro per eseguire una campagna, consulta [Flussi di lavoro di campagna](#campaign-workflows)
* Accedere e creare flussi di lavoro tecnici, consulta [Flussi di lavoro tecnici](#technical-workflows)
* Utilizza i modelli per creare flussi di lavoro, vedi [Modelli di flusso di lavoro](#workflow-templates)

## Creazione di un nuovo flusso di lavoro {#creating-a-new-workflow}

Accedi a una cartella di flusso di lavoro da **[!UICONTROL Explorer]**. Per impostazione predefinita, puoi utilizzare **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.

Fai clic sul pulsante **[!UICONTROL New]** situato sopra l’elenco dei flussi di lavoro.

![](assets/create_a_wf_icon.png)

In alternativa, puoi anche utilizzare il pulsante **[!UICONTROL Create]** nella panoramica del flusso di lavoro (**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]** link).

![](assets/create_a_wf.png)

Immetti un’etichetta e fai clic su **[!UICONTROL Save]**.

>[!NOTE]
>
>Quando modifichi il nome interno di un’attività del flusso di lavoro o del flusso di lavoro stesso, accertati di salvare il flusso di lavoro prima di chiuderlo in modo che il nuovo nome interno sia preso in considerazione correttamente.

## Aggiunta e collegamento di attività {#adding-and-linking-activities}

Devi ora definire le varie attività e collegarle nel diagramma. A questo punto della configurazione, è possibile visualizzare l’etichetta del diagramma e lo stato del flusso di lavoro (Modifica in corso). La sezione inferiore della finestra viene utilizzata solo per modificare il diagramma. Contiene una barra degli strumenti, una palette di attività (a sinistra) e il diagramma stesso (a destra).

![](assets/new-workflow-2.png)

>[!NOTE]
>
>Se la palette non è visualizzata, fare clic sul primo pulsante sulla barra degli strumenti per visualizzarla.

Le attività sono raggruppate per categoria all’interno delle diverse schede della palette. Le schede e le attività disponibili possono variare a seconda del tipo di flusso di lavoro (tecnico, di targeting o del flusso di lavoro della campagna).

* La prima scheda contiene attività di targeting e di manipolazione dei dati. Queste attività sono descritte in [Attività di targeting](../../workflow/using/about-targeting-activities.md).
* La seconda scheda contiene le attività di pianificazione, utilizzate principalmente per coordinare altre attività. Queste attività sono descritte in [Attività di controllo del flusso](../../workflow/using/about-flow-control-activities.md).
* La terza scheda contiene strumenti e azioni che possono essere utilizzati nel flusso di lavoro. Queste attività sono descritte in [Attività azione](../../workflow/using/about-action-activities.md).
* La quarta scheda contiene attività che dipendono da un determinato evento, ad esempio la ricezione di un’e-mail o l’arrivo di un file su un server. Queste attività sono descritte in [Attività evento](../../workflow/using/about-event-activities.md).

Per creare il diagramma

1. Aggiungi un’attività selezionandola nella palette e spostandola nel diagramma mediante un’operazione di trascinamento della selezione.

   Aggiungi un&#39;attività **Start** e quindi un&#39;attività **Delivery** sul diagramma.

   ![](assets/new-workflow-3.png)

1. Collega le attività trascinando la transizione dell&#39;attività **Start** e rilasciandola sull&#39;attività **Delivery** .

   ![](assets/new-workflow-4.png)

   Puoi collegare automaticamente un’attività a quella precedente inserendo la nuova attività alla fine della transizione.

1. Aggiungi le attività necessarie e collegale come mostrato nel diagramma seguente.

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>Puoi copiare e incollare le attività all’interno di uno stesso flusso di lavoro. Tuttavia, si sconsiglia di copiare e incollare le attività tra flussi di lavoro diversi. Alcune impostazioni collegate ad attività come Consegne e Scheduler potrebbero causare conflitti ed errori durante l’esecuzione del flusso di lavoro di destinazione. Ti consigliamo invece di eseguire flussi di lavoro **Duplica**. Per ulteriori informazioni, consulta [Duplicazione dei flussi di lavoro](#duplicating-workflows).

È possibile modificare la visualizzazione e il layout del grafico utilizzando i seguenti elementi:

* **Utilizzo della barra degli strumenti**

   La barra degli strumenti di modifica del diagramma consente di accedere alle funzioni di layout ed esecuzione del flusso di lavoro.

   ![](assets/s_user_segmentation_wizard_10.png)

   Questo consente di adattare il layout dello strumento di modifica: visualizzazione della palette e panoramica, dimensioni e allineamento degli oggetti grafici.

   ![](assets/s_user_segmentation_toolbar.png)

   Le icone relative al tracciamento e all&#39;avvio di un flusso di lavoro di targeting avanzato sono descritte in questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **Allineamento dell’oggetto**

   Per allineare le icone, selezionarle e fare clic sull&#39;icona **[!UICONTROL Align vertically]** o **[!UICONTROL Align horizontally]**.

   Utilizza il tasto **CTRL** per selezionare più attività sparse o per deselezionare una o più attività. Fai clic sullo sfondo del diagramma per deselezionare tutti gli elementi.

* **Gestione delle immagini**

   Puoi personalizzare l’immagine di sfondo del diagramma e quelle relative alle varie attività. Fai riferimento a [Gestione delle immagini delle attività](../../workflow/using/managing-activity-images.md).

## Configurazione delle attività {#configuring-activities}

Fai doppio clic su un’attività per configurarla o fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Open...]**.

>[!NOTE]
>
>Le attività del flusso di lavoro della campagna sono descritte in [questa sezione](../../workflow/using/about-activities.md).

La prima scheda contiene la configurazione di base. La scheda **[!UICONTROL Advanced]** contiene i parametri aggiuntivi, utilizzati in particolare per definire il comportamento in caso di errore, specificare la durata di esecuzione per un&#39;attività e per immettere uno script di inizializzazione.

Per una migliore comprensione delle attività e per migliorare la leggibilità del flusso di lavoro, puoi inserire commenti nelle attività: questi vengono visualizzati automaticamente quando gli operatori scorrono l’attività.

![](assets/example1-comment.png)

## Workflow di targeting {#targeting-workflows}

I flussi di lavoro di targeting consentono di creare diversi target di consegna. Puoi creare query, definire sindacati o esclusioni in base a criteri specifici, aggiungere la pianificazione, grazie alle attività del flusso di lavoro. Il risultato di questo targeting può essere trasferito automaticamente in un elenco che può fungere da target delle azioni di consegna

Oltre a queste attività, le opzioni di gestione dati ti consentono di manipolare i dati e di accedere a funzioni avanzate per soddisfare problemi di targeting complessi. Per ulteriori informazioni, consulta [Gestione dati](../../workflow/using/targeting-data.md#data-management).

Tutte queste attività si trovano nella prima scheda del flusso di lavoro.

>[!NOTE]
>
>Le attività di targeting sono descritte in [questa sezione](../../workflow/using/about-activities.md).

I flussi di lavoro di targeting possono essere creati e modificati tramite il nodo **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** della struttura di Adobe Campaign o tramite il menu **[!UICONTROL Profiles and Targets > Targeting workflows]** della home page.

![](assets/target_wf.png)

I flussi di lavoro di targeting nel quadro di una campagna vengono memorizzati con tutti i flussi di lavoro delle campagne.

### Passaggi chiave per creare un flusso di lavoro di targeting {#implementation-steps-}

I passaggi per creare un flusso di lavoro di targeting sono descritti in dettaglio in queste sezioni:

1. **** Identificare i dati nel database - Vedere  [Creazione di query](../../workflow/using/targeting-data.md#creating-queries)
1. **** Preparazione dei dati per soddisfare le esigenze di consegna - Consulta  [Arricchimento e modifica dei dati](../../workflow/using/targeting-data.md#enriching-and-modifying-data)
1. **** Dati utilizzati per eseguire aggiornamenti o all’interno di una consegna - Consulta  [Aggiornamento del database](../../workflow/using/how-to-use-workflow-data.md#updating-the-database)

I risultati di tutti gli arricchimenti e di tutte le operazioni eseguite durante il targeting sono memorizzati e accessibili nei campi di personalizzazione, in particolare per l’utilizzo durante la creazione di messaggi personalizzati. Per ulteriori informazioni, consulta [Dati di destinazione](../../workflow/using/data-life-cycle.md#target-data)

### Dimensioni di targeting e filtro {#targeting-and-filtering-dimensions}

Durante le operazioni di segmentazione dei dati, la chiave di targeting è mappata su una dimensione di filtro. La dimensione di targeting ti consente di definire la popolazione target dell’operazione: destinatari, beneficiari del contratto, operatore, abbonati, ecc. La dimensione di filtro consente di selezionare la popolazione in base a determinati criteri: titolari di contratti, abbonati a newsletter, ecc.

Ad esempio, per selezionare i clienti che hanno stipulato una polizza di assicurazione vita per più di 5 anni, seleziona la dimensione di targeting seguente: **Client** e la seguente dimensione di filtro: **Titolare del contratto**. Puoi quindi definire le condizioni di filtro all’interno dell’attività di query

Durante la fase di selezione della dimensione di targeting, nell’interfaccia sono offerte solo dimensioni di filtro compatibili.

Queste due dimensioni devono essere correlate. Pertanto, il contenuto dell’elenco **[!UICONTROL Filtering dimension]** dipende dalla dimensione di targeting specificata nel primo campo.

Ad esempio, per i destinatari (**recipient**) saranno disponibili le seguenti dimensioni di filtro:

![](assets/query_filter_target_dimensions_1.png)

Mentre per **Applicazioni web**, l&#39;elenco conterrà le seguenti dimensioni di filtro:

![](assets/query_filter_target_dimensions_2.png)

## Flussi di lavoro delle campagne {#campaign-workflows}

Per ogni campagna, puoi creare flussi di lavoro da eseguire dalla scheda **[!UICONTROL Targeting and workflows]** . Questi flussi di lavoro sono specifici per la campagna.

![](assets/wf-in-op-edit-delivery-tab.png)

Questa scheda contiene le stesse attività di tutti i flussi di lavoro. [Ulteriori informazioni](#implementation-steps-)

Oltre alle campagne di targeting, i flussi di lavoro delle campagne consentono di creare e configurare consegne interamente per tutti i canali disponibili. Una volta create nel flusso di lavoro, queste consegne sono disponibili dal dashboard della campagna. [Ulteriori informazioni](../../campaign/using/marketing-campaign-deliveries.md)

Tutti i flussi di lavoro delle campagne sono centralizzati sotto il nodo **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** .

![](assets/campaigns_wf.png)

I flussi di lavoro e gli esempi di implementazione delle campagne sono descritti in [questa pagina](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

## Flussi di lavoro tecnici {#technical-workflows}

I flussi di lavoro tecnici sono preconfigurati con Adobe Campaign. Si tratta di operazioni o processi pianificati per l&#39;esecuzione periodica sul server. Consentono di eseguire la manutenzione sul database, inoltrare le informazioni di tracciamento sulle consegne e impostare processi provvisori sulle consegne. I flussi di lavoro tecnici sono configurati tramite il nodo **[!UICONTROL Administration > Production > Technical workflows]** .

![](assets/navtree.png)

Sono disponibili modelli nativi per la creazione di flussi di lavoro tecnici. Possono essere configurati in base alle tue esigenze.

La sottocartella **[!UICONTROL Campaign process]** centralizza i flussi di lavoro necessari per l’esecuzione di processi all’interno delle campagne: notifica delle attività, gestione delle scorte, calcolo dei costi, ecc.

>[!NOTE]
>
>L&#39;elenco dei flussi di lavoro tecnici installati con ciascun modulo è disponibile in una sezione [dedicata](../../workflow/using/about-technical-workflows.md).

Puoi creare altri flussi di lavoro tecnici nel nodo **[!UICONTROL Administration > Production > Technical workflows]** della struttura ad albero. Tuttavia, questo processo è riservato agli utenti esperti.

Le attività offerte sono le stesse dei flussi di lavoro di targeting. [Ulteriori informazioni](#implementation-steps-)

## Modelli di flusso di lavoro {#workflow-templates}

I modelli di flusso di lavoro contengono la configurazione complessiva delle proprietà ed eventualmente una serie di attività concatenate all’interno di un diagramma. Questa configurazione può essere riutilizzata per creare nuovi flussi di lavoro contenenti un certo numero di elementi preconfigurati

Puoi creare nuovi modelli di flusso di lavoro basati su modelli esistenti o modificare direttamente un flusso di lavoro in un modello.

I modelli di flusso di lavoro sono memorizzati nel nodo **[!UICONTROL Resources > Templates > Workflow templates]** della struttura di Adobe Campaign.

![](assets/s_advuser_wf_template_tree.png)

Oltre alle consuete proprietà del flusso di lavoro, le proprietà del modello ti consentono di specificare il file di esecuzione per i flussi di lavoro creati in base a questo modello.

![](assets/s_advuser_wf_template_properties.png)

## Duplicazione dei flussi di lavoro {#duplicating-workflows}

Puoi duplicare diversi tipi di flussi di lavoro. Una volta eseguita la duplicazione, le modifiche del flusso di lavoro non vengono riportate nella copia del flusso di lavoro.

>[!CAUTION]
>
>La funzione Copia e incolla è disponibile nei flussi di lavoro, ma ti consigliamo di utilizzare **Duplica**. Una volta copiata un’attività, viene mantenuta l’intera configurazione. Per le attività di consegna (e-mail, SMS, notifica push..), viene copiato anche l’oggetto di consegna allegato all’attività, il che può causare un arresto anomalo.

1. Fai clic con il pulsante destro del mouse su un flusso di lavoro.
1. Fare clic su **Duplica**.

   ![](assets/duplicate-workflows.png)

1. Nella finestra del flusso di lavoro, modifica l’etichetta del flusso di lavoro.
1. Fai clic su **Salva**.

La funzione duplicata non è direttamente disponibile nella visualizzazione di una campagna.

Tuttavia, puoi creare una visualizzazione per visualizzare tutti i flussi di lavoro sull’istanza. In questa visualizzazione è possibile duplicare i flussi di lavoro utilizzando **Duplica su**.

**Innanzitutto, creiamo una visualizzazione:**

1. In **Esplora risorse**, vai alla cartella in cui devi creare la visualizzazione.
1. Fai clic con il pulsante destro del mouse e vai a **Aggiungi una nuova cartella** > **Processo**, seleziona **Flussi di lavoro**.

   ![](assets/add-new-folder-workflows.png)

Viene creata la nuova cartella **Flussi di lavoro**.

1. Fai clic con il pulsante destro del mouse e seleziona **Proprietà**.
1. In **Restrizione**, controlla **Cartella è una visualizzazione** e fai clic su **Salva**.

   ![](assets/folder-is-a-view.png)

La cartella viene ora compilata con tutti i flussi di lavoro dell’istanza.

**Duplicazione di un flusso di lavoro della campagna**

1. Seleziona un flusso di lavoro della campagna nella visualizzazione del flusso di lavoro.
1. Fai clic con il pulsante destro del mouse su **Duplica su**.
   ![](assets/duplicate-to-right-click.png)
1. Cambia l’etichetta.
1. Fai clic su **Salva**.

Puoi visualizzare il flusso di lavoro duplicato nella visualizzazione del flusso di lavoro.
