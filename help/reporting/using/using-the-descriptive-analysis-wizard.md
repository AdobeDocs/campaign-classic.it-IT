---
title: Utilizzo della procedura guidata di analisi descrittiva
seo-title: Utilizzo della procedura guidata di analisi descrittiva
description: Utilizzo della procedura guidata di analisi descrittiva
seo-description: null
page-status-flag: never-activated
uuid: 30554909-4b91-46ff-bd8d-fa57ab6304f9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 18ba04d9-7bab-4eea-8dbb-6c2c138c5293
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---


# Utilizzo della procedura guidata di analisi descrittiva{#using-the-descriptive-analysis-wizard}

Per creare un rapporto di analisi descrittivo, utilizzate la procedura guidata dedicata. La configurazione dipende dai dati da analizzare e dal rendering desiderato.

## Analisi dei dati nel database {#analyzing-data-in-the-database}

La procedura guidata di analisi descrittiva può essere avviata dal **[!UICONTROL Tools > Descriptive analysis]** menu: in questo caso, l&#39;analisi riguarda i destinatari per impostazione predefinita (**nms:Recipients**). Si applica a tutti i dati presenti nel database Adobe Campaign .

![](assets/reporting_descriptive_wz_launch.png)

Per analizzare una tabella diversa dai destinatari standard uno (**nms:destinatario**), fai clic sul **[!UICONTROL Advanced settings...]** collegamento nell’ultima fase della procedura guidata e seleziona la tabella che corrisponde alle impostazioni, in questo caso **focus:single**:

![](assets/reporting_descriptive_other_schema.png)

Se si desidera generare statistiche su parte dei dati, è possibile definire un filtro: a questo scopo, fate clic sul **[!UICONTROL Advanced settings...]** collegamento e definite il filtro da applicare, come illustrato di seguito:

![](assets/reporting_descriptive_wz_filter.png)

L&#39;analisi riguarderà solo i destinatari di database di età non inferiore ai 16 anni che vivono a Londra.

## Analisi di un insieme di dati {#analyzing-a-set-of-data}

Puoi usare la procedura guidata di analisi descrittiva in un contesto diverso: un elenco, una transizione di workflow, una o più consegne, una selezione di destinatari e così via.

È accessibile tramite diversi nodi della struttura di Adobe Campaign  che puntano alla tabella dei destinatari.

Aprite la procedura guidata di analisi descrittiva selezionando gli elementi e facendo clic con il pulsante destro del mouse. Vengono analizzati solo i dati selezionati.

![](assets/reporting_descriptive_from_recipients.png)

* Per un set di **destinatari**, selezionate i destinatari da analizzare, quindi fate clic con il pulsante destro del mouse e selezionate **[!UICONTROL Actions > Explore...]**, come mostrato sopra. Se un filtro viene applicato all’elenco dei destinatari, verrà analizzato solo il relativo contenuto.

   Per selezionare tutti i destinatari nella cartella o nel filtro corrente, utilizzare la scelta rapida CTRL+A. Ciò significa che anche i destinatari non visualizzati verranno selezionati.

   Per un esempio di analisi descrittiva dei destinatari, fare riferimento a: [Analisi](../../reporting/using/use-cases.md#qualitative-data-analysis)qualitativa dei dati.

* Nel contesto di un **flusso di lavoro**, posizionate il cursore su una transizione verso la tabella dei destinatari, fate clic con il pulsante destro del mouse e selezionate **[!UICONTROL Analyze target]**. Per ulteriori informazioni, consulta l’esempio in [Analisi di una destinazione di transizione in un flusso di lavoro](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* Per **gli elenchi**, selezionare uno o più elenchi e applicare lo stesso processo utilizzato per i destinatari.
* Nel contesto di una **consegna**, selezionate le consegne di cui desiderate analizzare il target, fate clic con il pulsante destro del mouse e selezionate **[!UICONTROL Actions > Explore the target]**, come illustrato di seguito:

   ![](assets/reporting_descriptive_from_deliveries.png)

   Esempi di analisi descrittive per le consegne sono forniti qui: [Analisi di una popolazione](../../reporting/using/use-cases.md#analyzing-a-population) ed effettuate le seguenti operazioni: [Analisi dei registri](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs)di tracciamento dei destinatari.

## Configurazione del modello di distribuzione qualitativa {#configuring-the-qualitative-distribution-template}

Il **[!UICONTROL Qualitative distribution]** modello consente di creare statistiche su tutti i tipi di dati (ad esempio nome società, dominio e-mail).

Le opzioni di configurazione disponibili per un rapporto creato tramite il **[!UICONTROL Qualitative distribution]** modello sono descritte in [Visualizzazione dei dati nella tabella](#displaying-data-in-the-table). Un esempio completo è illustrato in [Analisi di una popolazione](../../reporting/using/use-cases.md#analyzing-a-population).

Quando si utilizza la procedura guidata di analisi descrittiva per analizzare i dati, le opzioni disponibili dipendono dalle impostazioni selezionate. Questi sono descritti di seguito.

### Binding dei dati {#data-binning}

Quando si selezionano le variabili da visualizzare, è possibile definire il binding dei dati, ovvero configurare i criteri di raggruppamento per i dati selezionati.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>Quando il campo interessato dal calcolo viene calcolato utilizzando un aggregato, verificare **[!UICONTROL The data is already aggregated]** di migliorare le prestazioni.

Le opzioni variano a seconda del contenuto del campo:

* **[!UICONTROL None]** : questa opzione consente di visualizzare tutti i valori disponibili per la variabile, senza associazione.

   >[!CAUTION]
   >
   >Questa opzione deve essere utilizzata con attenzione: può avere un impatto importante sul report e sulle prestazioni della macchina.

* **[!UICONTROL Auto]** : questa opzione consente di visualizzare gli n valori rappresentati più di frequente. Vengono calcolati automaticamente e ciascuna rappresenta una percentuale delle variabili rispetto al numero di raccoglitori. Per i valori numerici,  Adobe Campaign genera automaticamente n classi in cui ordinare i dati.
* **[!UICONTROL Manual]** : questa opzione funziona come l’ **[!UICONTROL Auto]** opzione, ma potete impostare manualmente questi valori. A tale scopo, fare clic sul **[!UICONTROL Add]** pulsante a destra della tabella dei valori.

   I valori possono essere inizializzati automaticamente da  Adobe Campaign prima della personalizzazione: a tal fine, immettete il numero di contenitori da generare e fate clic sul **[!UICONTROL Initialize with]** collegamento, come illustrato di seguito:

   ![](assets/reporting_descriptive_initialize.png)

   Quindi adattate i contenuti in base alle vostre esigenze:

   ![](assets/reporting_descriptive_initialize_perso.png)

   A seconda del livello di precisione desiderato, i campi contenenti le date possono essere raggruppati per ora, giorno, mese, anno e così via.

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** : consente di creare gruppi di valori in caso di valori numerici. Ad esempio, un modulo con un valore pari a 10 consente di creare un intervallo di valori che varia di dieci per dieci.

   ![](assets/reporting_descriptive_initialize_modulo.png)

   Questo esempio consente di visualizzare la suddivisione dei destinatari per gruppo di età.

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Visualizzazione dei dati nella tabella {#displaying-data-in-the-table}

Utilizzare la barra degli strumenti per personalizzare la visualizzazione delle variabili nella tabella: eliminare una colonna, visualizzare i dati in righe anziché in colonne, spostare una colonna a sinistra o a destra, visualizzare o modificare il calcolo del valore.

![](assets/s_ncs_user_report_wizard_toolbar.png)

La sezione superiore della finestra consente di selezionare le impostazioni di visualizzazione.

È possibile visualizzare o nascondere il nome delle statistiche e i totali parziali e scegliere l&#39;orientamento delle statistiche. Per ulteriori informazioni, consulta Impostazioni [di visualizzazione dei rapporti di](../../reporting/using/processing-a-report.md#analysis-report-display-settings)analisi.

### Visualizzazione dei dati nel grafico {#displaying-data-in-the-chart}

Nel primo passaggio della procedura guidata di analisi descrittiva, è possibile scegliere di visualizzare i dati solo in forma di grafico, senza che sia presente una tabella. In questo caso, la selezione della variabile deve essere eseguita durante la configurazione dell&#39;elemento grafico. È innanzitutto necessario selezionare il numero di variabili da visualizzare e selezionare i campi dal database pertinente.

![](assets/s_ncs_user_report_wizard_023.png)

Selezionare quindi il tipo di grafico desiderato.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>È possibile visualizzare le variabili contemporaneamente in un grafico e una tabella. A questo scopo, immettete le variabili nella **[!UICONTROL Table configuration]** finestra. Fare clic **[!UICONTROL Next]** e selezionare il tipo di grafico nella finestra di configurazione del grafico. Se le dimensioni secondarie sono definite nella tabella, non vengono visualizzate nel grafico.

Fare clic sul **[!UICONTROL Variants]** collegamento per modificare le proprietà del grafico.

![](assets/reporting_descriptive_graphe_options.png)

Le opzioni disponibili dipendono dal tipo di grafico selezionato. Per ulteriori informazioni, consulta [questa pagina](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### Calcolo delle statistiche {#statistics-calculation}

La procedura guidata di analisi descrittiva consente di calcolare diversi tipi di statistiche sui dati. Per impostazione predefinita, è configurato un solo conteggio semplice.

Click **[!UICONTROL Add]** to create a new statistic.

![](assets/reporting_descriptive_create_stat.png)

Sono possibili le seguenti operazioni:

* **[!UICONTROL Count]** per contare tutti i valori non-null del campo da aggregare, compresi i valori duplicati (del campo aggregato),
* **[!UICONTROL Average]** per calcolare la media dei valori in un campo numerico,
* **[!UICONTROL Minimum]** per calcolare il minimo dei valori in un campo numerico,
* **[!UICONTROL Maximum]** per calcolare il massimo dei valori in un campo numerico,
* **[!UICONTROL Sum]** per calcolare la somma dei valori in un campo numerico,
* **[!UICONTROL Standard deviation]** per calcolare la dispersione dei valori restituiti intorno alla media,
* **[!UICONTROL Row percentage distribution]** per calcolare il rapporto tra il valore di una colonna e il valore di una riga (disponibile solo per le tabelle),
* **[!UICONTROL Column percentage distribution]** per calcolare il rapporto tra il valore di una riga e il valore di una colonna (disponibile solo per le tabelle),
* **[!UICONTROL Total percentage distribution]** calcolare la distribuzione dei destinatari interessati dai valori,

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** per creare un operatore personalizzato (disponibile solo per le tabelle). Il **[!UICONTROL User function]** campo consente di inserire il calcolo da applicare ai dati.

   Esempio: Calcolo dell&#39;importo medio dell&#39;acquisto per cliente in base al paese e all&#39;origine

   ![](assets/report_compute_data_sample1.png)

   Per visualizzare le informazioni di cui sopra in una tabella, è necessario creare un campo calcolato per memorizzare l&#39;importo medio dell&#39;acquisto per cliente.

   Per eseguire questa operazione:

   1. Calcola il totale dell&#39;acquisto.

      ![](assets/report_compute_data_sample2.png)

   1. Questa statistica non verrà visualizzata nella tabella. È necessario deselezionare l&#39; **[!UICONTROL Display in the table]** opzione della **[!UICONTROL Advanced]** scheda.

      ![](assets/report_compute_data_sample3.png)

   1. Create una nuova statistica di **[!UICONTROL Calculated field]** tipo e immettete la seguente formula nel **[!UICONTROL User function]** campo: **@purchase/@count**.

      ![](assets/report_compute_data_sample4.png)

### Visualizzazione del rapporto {#displaying-the-report}

L&#39;ultimo passaggio della procedura guidata consente di visualizzare il rapporto, ovvero la tabella o il grafico così come sono stati configurati.

Quando il rapporto contiene una tabella, la cella del risultato del calcolo è colorata. Più alto è il risultato, più intenso è il colore.

![](assets/report_compute_data_sample1.png)

È possibile modificare il layout dei risultati. A tal fine, fare clic con il pulsante destro del mouse sulla variabile interessata e selezionare l&#39;input dal menu di scelta rapida.

![](assets/s_ncs_user_report_wizard_029.png)

Quando il rapporto include un grafico, le etichette della legenda consentono di filtrare le informazioni visualizzate: fare clic su un&#39;etichetta per attivare/disattivare la visualizzazione nel grafico.

![](assets/report_display_data_in_graph.png)

## Configurazione del modello di distribuzione quantitativa {#configuring-the-quantitative-distribution-template}

Per generare un’analisi descrittiva, selezionate l’opzione **Nuova analisi descrittiva da un modello** , se non è impostata per impostazione predefinita.

Modello **[!UICONTROL Quantitative distribution]** che consente di generare statistiche sui dati misurabili o conteggiabili (ad esempio, importo fattura, età dei destinatari).

La modalità di configurazione di un report di analisi creato tramite il **[!UICONTROL Quantitative distribution]** modello è dettagliata in un esempio di implementazione, l&#39;analisi [dei dati](../../reporting/using/use-cases.md#quantitative-data-analysis)quantitativi.

Le opzioni disponibili quando si utilizza la procedura guidata di analisi descrittiva per creare un rapporto quantitativo sono descritte di seguito.

Per iniziare, selezionate la variabile che i calcoli riguardano:

![](assets/s_ncs_user_report_wizard_017.png)

Per impostazione predefinita,  Adobe Campaign offre una serie di statistiche da calcolare per i dati selezionati. È possibile modificare questo elenco, aggiungerlo o eliminare le statistiche in base alle proprie esigenze.

Sono possibili le seguenti operazioni:

* **[!UICONTROL Count]** per contare tutti i valori non-null del campo da aggregare, compresi i valori duplicati (del campo aggregato),
* **[!UICONTROL Average]** per calcolare la media dei valori in un campo numerico,
* **[!UICONTROL Minimum]** per calcolare il minimo dei valori in un campo numerico,
* **[!UICONTROL Maximum]** per calcolare il massimo dei valori in un campo numerico.
* **[!UICONTROL Sum]** per calcolare la somma dei valori in un campo numerico,
* **[!UICONTROL Standard deviation]** per calcolare il modo in cui i valori restituiti vengono distribuiti intorno alla media.
* **[!UICONTROL Number of missing values]** per calcolare il numero di campi numerici senza valori definiti.
* **[!UICONTROL Decile distribution]** distribuire i valori restituiti in modo che ciascuno rappresenti 1/10 dei valori in un campo numerico.
* **[!UICONTROL Custom distribution]** per distribuire i valori restituiti in base alle soglie definite dall&#39;utente.

   Il **[!UICONTROL Detail...]** pulsante consente di modificare una statistica e, se necessario, personalizzarne il calcolo o la visualizzazione:

   ![](assets/s_ncs_user_report_wizard_030.png)

   L&#39;ultimo passaggio della procedura guidata mostra il rapporto di analisi quantitativa.

   ![](assets/reporting_descriptive_view_report.png)

   Per apportare modifiche al rapporto, fare riferimento a [Elaborazione di un rapporto](../../reporting/using/processing-a-report.md).

