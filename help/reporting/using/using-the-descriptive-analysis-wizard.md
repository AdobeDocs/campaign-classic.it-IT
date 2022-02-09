---
product: campaign
title: Usare la procedura guidata di analisi descrittiva
description: Usare la procedura guidata di analisi descrittiva
exl-id: 848d67c7-d1dc-4eba-bcb8-672e76d8ce87
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Usare la procedura guidata di analisi descrittiva{#using-the-descriptive-analysis-wizard}

![](../../assets/common.svg)

Per creare un rapporto di analisi descrittivo, utilizza la procedura guidata dedicata. La configurazione dipende dai dati da analizzare e dal rendering desiderato.

## Analizzare i dati nel database {#analyzing-data-in-the-database}

La procedura guidata di analisi descrittiva può essere avviata tramite la **[!UICONTROL Tools > Descriptive analysis]** menu: in questo caso, l&#39;analisi riguarda i destinatari per impostazione predefinita (**nms:recipient**). Si applica a tutti i dati del database Adobe Campaign.

![](assets/reporting_descriptive_wz_launch.png)

Per analizzare una tabella diversa dai destinatari standard un (**nms:recipient**), fai clic sul pulsante **[!UICONTROL Advanced settings...]** nell&#39;ultimo passaggio della procedura guidata e seleziona la tabella che corrisponde alle impostazioni, in questo caso **cus:individuale**:

![](assets/reporting_descriptive_other_schema.png)

Se desideri produrre statistiche su parte dei dati, puoi definire un filtro: a questo scopo, fai clic sul pulsante **[!UICONTROL Advanced settings...]** collega e definisci il filtro da applicare, come illustrato di seguito:

![](assets/reporting_descriptive_wz_filter.png)

L&#39;analisi riguarderà soltanto i destinatari di database di 16 anni e più che residenti a Londra.

## Analizzare un insieme di dati {#analyzing-a-set-of-data}

Puoi utilizzare la procedura guidata di analisi descrittiva tramite un contesto diverso: un elenco, una transizione di flusso di lavoro, una o più consegne, una selezione di destinatari, ecc.

È accessibile tramite diversi nodi della struttura di Adobe Campaign che puntano alla tabella dei destinatari.

Apri la procedura guidata di analisi descrittiva selezionando gli elementi e facendo clic con il pulsante destro del mouse. Verranno analizzati solo i dati selezionati.

![](assets/reporting_descriptive_from_recipients.png)

* Per un set di **destinatari**, seleziona i destinatari da analizzare, quindi fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Actions > Explore...]**, come illustrato in precedenza. Se un filtro viene applicato all’elenco dei destinatari, verrà analizzato solo il relativo contenuto.

   Per selezionare tutti i destinatari nella cartella o nel filtro corrente, utilizzare la scelta rapida CTRL+A. Ciò significa che verranno selezionati anche i destinatari non visualizzati.

   Per un esempio di analisi descrittiva dei destinatari, consulta: [Analisi qualitativa dei dati](../../reporting/using/use-cases.md#qualitative-data-analysis).

* Nel contesto di un **workflow**, posiziona il cursore su una transizione che punta verso la tabella dei destinatari, fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Analyze target]**. Per ulteriori informazioni, consulta l’esempio in [Analizzare una destinazione di transizione in un flusso di lavoro](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* Per **elenchi**, seleziona uno o più elenchi e applica la stessa procedura utilizzata per i destinatari.
* Nel contesto di un **consegna**, seleziona le consegne di cui desideri analizzare il target, fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Actions > Explore the target]**, come illustrato di seguito:

   ![](assets/reporting_descriptive_from_deliveries.png)

   Ecco alcuni esempi di analisi descrittive delle consegne: [Analizzare una popolazione](../../reporting/using/use-cases.md#analyzing-a-population) e qui: [Analizzare i registri di tracciamento dei destinatari](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs).

## Configurare il modello di distribuzione qualitativa {#configuring-the-qualitative-distribution-template}

La **[!UICONTROL Qualitative distribution]** template ti consente di creare statistiche su tutti i tipi di dati (ad esempio nome società, dominio e-mail).

Opzioni di configurazione disponibili per un rapporto creato tramite **[!UICONTROL Qualitative distribution]** i modelli sono descritti in [Visualizzazione dei dati nella tabella](#displaying-data-in-the-table). Un esempio completo è descritto in [Analizzare una popolazione](../../reporting/using/use-cases.md#analyzing-a-population).

Quando si utilizza la procedura guidata di analisi descrittiva per analizzare i dati, le opzioni disponibili dipendono dalle impostazioni selezionate. Questi sono descritti di seguito.

### Associazione dei dati {#data-binning}

Quando selezioni le variabili da visualizzare, puoi definire il binding dei dati, in altre parole configurare i criteri di raggruppamento per i dati selezionati.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>Quando il campo interessato dal calcolo viene calcolato utilizzando un aggregato, controllare **[!UICONTROL The data is already aggregated]** migliorare le prestazioni.

Le opzioni variano a seconda del contenuto del campo:

* **[!UICONTROL None]** : questa opzione consente di visualizzare tutti i valori disponibili per la variabile senza binding.

   >[!CAUTION]
   >
   >Questa opzione deve essere utilizzata con attenzione: può avere un impatto importante sul report e sulle prestazioni della macchina.

* **[!UICONTROL Auto]** : questa opzione ti consente di visualizzare gli n valori rappresentati più frequentemente. Vengono calcolati automaticamente e ciascuna rappresenta una percentuale delle variabili rispetto al numero di contenitori. Per i valori numerici, Adobe Campaign genera automaticamente n classi in cui ordinare i dati.
* **[!UICONTROL Manual]** : questa opzione funziona come **[!UICONTROL Auto]** ma è possibile impostare manualmente questi valori. A questo scopo, fai clic sul pulsante **[!UICONTROL Add]** a destra della tabella dei valori.

   I valori possono essere inizializzati automaticamente da Adobe Campaign prima della personalizzazione: a questo scopo, immetti il numero di bins che desideri generare e fai clic sul **[!UICONTROL Initialize with]** come mostrato di seguito:

   ![](assets/reporting_descriptive_initialize.png)

   Quindi adattate i contenuti in base alle vostre esigenze:

   ![](assets/reporting_descriptive_initialize_perso.png)

   A seconda del livello di precisione desiderato, i campi contenenti date possono essere raggruppati per ora, giorno, mese, anno, ecc.

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** : consente di creare gruppi di valori in caso di valori numerici. Ad esempio, un modulo con un valore pari a 10 consente di creare un intervallo di valori che viene modificato di dieci per dieci.

   ![](assets/reporting_descriptive_initialize_modulo.png)

   Questo esempio ti consente di visualizzare la suddivisione dei destinatari per gruppo di età.

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Visualizzazione dei dati nella tabella {#displaying-data-in-the-table}

Utilizza la barra degli strumenti per personalizzare la visualizzazione delle variabili nella tabella: eliminare una colonna, visualizzare i dati in righe anziché in colonne, spostare una colonna a sinistra o a destra, visualizzare o modificare il calcolo del valore.

![](assets/s_ncs_user_report_wizard_toolbar.png)

La sezione superiore della finestra consente di selezionare le impostazioni di visualizzazione.

È possibile visualizzare o nascondere il nome delle statistiche e dei totali parziali e scegliere l’orientamento delle statistiche. Per ulteriori informazioni, consulta [Impostazioni di visualizzazione dei rapporti di analisi](../../reporting/using/processing-a-report.md#analysis-report-display-settings).

### Visualizzazione dei dati nel grafico {#displaying-data-in-the-chart}

Nel primo passaggio della procedura guidata di analisi descrittiva, puoi scegliere di visualizzare i dati solo in forma di grafico, senza tabella. In questo caso, la selezione della variabile deve essere eseguita durante la configurazione dell&#39;immagine. È innanzitutto necessario selezionare il numero di variabili da visualizzare e selezionare i campi dal database pertinente.

![](assets/s_ncs_user_report_wizard_023.png)

Quindi selezionare il tipo di grafico desiderato.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>È possibile visualizzare le variabili in un grafico e una tabella contemporaneamente. A questo scopo, immetti le variabili nella **[!UICONTROL Table configuration]** finestra. Fai clic su **[!UICONTROL Next]** e selezionare il tipo di grafico nella finestra di configurazione del grafico. Se le dimensioni secondarie sono definite nella tabella, non vengono visualizzate nel grafico.

Fai clic sul pulsante **[!UICONTROL Variants]** per modificare le proprietà del grafico.

![](assets/reporting_descriptive_graphe_options.png)

Le opzioni disponibili dipendono dal tipo di grafico selezionato. Per ulteriori informazioni, consulta [questa pagina](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### Calcolo delle statistiche {#statistics-calculation}

La procedura guidata di analisi descrittiva consente di calcolare diversi tipi di statistiche sui dati. Per impostazione predefinita, è configurato un solo conteggio semplice.

Fai clic su **[!UICONTROL Add]** per creare una nuova statistica.

![](assets/reporting_descriptive_create_stat.png)

Sono possibili le seguenti operazioni:

* **[!UICONTROL Count]** per contare tutti i valori non nulli del campo da aggregare, compresi i valori duplicati (del campo aggregato),
* **[!UICONTROL Average]** per calcolare la media dei valori in un campo numerico,
* **[!UICONTROL Minimum]** per calcolare il minimo dei valori in un campo numerico,
* **[!UICONTROL Maximum]** per calcolare il massimo dei valori in un campo numerico,
* **[!UICONTROL Sum]** per calcolare la somma dei valori in un campo numerico,
* **[!UICONTROL Standard deviation]** per calcolare la dispersione dei valori restituiti intorno alla media,
* **[!UICONTROL Row percentage distribution]** per calcolare il rapporto tra il valore di una colonna e il valore di una riga (disponibile solo per le tabelle),
* **[!UICONTROL Column percentage distribution]** per calcolare il rapporto tra il valore di una riga e il valore di una colonna (disponibile solo per le tabelle),
* **[!UICONTROL Total percentage distribution]** calcolare la distribuzione dei destinatari interessati dai valori,

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** per creare un operatore personalizzato (disponibile solo per le tabelle). La **[!UICONTROL User function]** consente di inserire il calcolo da applicare ai dati.

   Esempio: Calcolo dell&#39;importo medio dell&#39;acquisto per cliente in base al paese e all&#39;origine

   ![](assets/report_compute_data_sample1.png)

   Per visualizzare le informazioni di cui sopra in una tabella, è necessario creare un campo calcolato per memorizzare l’importo medio dell’acquisto per cliente.

   Per eseguire questa operazione:

   1. Calcola il totale dell&#39;acquisto.

      ![](assets/report_compute_data_sample2.png)

   1. Questa statistica non verrà visualizzata nella tabella. È necessario deselezionare la **[!UICONTROL Display in the table]** opzione **[!UICONTROL Advanced]** scheda .

      ![](assets/report_compute_data_sample3.png)

   1. Crea un nuovo **[!UICONTROL Calculated field]** digitare statistic e immettere la seguente formula nel **[!UICONTROL User function]** campo: **@purchase/@count**.

      ![](assets/report_compute_data_sample4.png)

### Visualizza il rapporto {#displaying-the-report}

L’ultimo passaggio della procedura guidata consente di visualizzare il rapporto, ovvero la tabella o il grafico configurato.

Quando il report contiene una tabella, la cella del risultato del calcolo è colorata. Più alto è il risultato, più intenso è il colore.

![](assets/report_compute_data_sample1.png)

È possibile modificare il layout dei risultati. A questo scopo, fai clic con il pulsante destro del mouse sulla variabile interessata e seleziona l’input dal menu di scelta rapida.

![](assets/s_ncs_user_report_wizard_029.png)

Quando il rapporto include un grafico, le etichette della legenda consentono di filtrare le informazioni visualizzate: fai clic su un&#39;etichetta per abilitare/disabilitare la visualizzazione nel grafico.

![](assets/report_display_data_in_graph.png)

## Configurare il modello di distribuzione quantitativa {#configuring-the-quantitative-distribution-template}

Per generare autonomamente un’analisi descrittiva, seleziona la **Nuova analisi descrittiva da un modello** se non è impostata per impostazione predefinita.

La **[!UICONTROL Quantitative distribution]** modello che consente di generare statistiche sui dati misurabili o conteggiabili (ad esempio, importo della fattura, età dei destinatari).

La modalità di configurazione di un rapporto di analisi creato tramite **[!UICONTROL Quantitative distribution]** modello dettagliato in un esempio di implementazione [Analisi quantitativa dei dati](../../reporting/using/use-cases.md#quantitative-data-analysis).

Le opzioni disponibili quando si utilizza la procedura guidata di analisi descrittiva per creare un rapporto quantitativo sono descritte di seguito.

Inizia selezionando la variabile che i calcoli riguardano:

![](assets/s_ncs_user_report_wizard_017.png)

Per impostazione predefinita, Adobe Campaign offre una serie di statistiche da calcolare per i dati selezionati. È possibile modificare questo elenco, aggiungerlo o eliminare le statistiche in base alle proprie esigenze.

Sono possibili le seguenti operazioni:

* **[!UICONTROL Count]** per contare tutti i valori non nulli del campo da aggregare, compresi i valori duplicati (del campo aggregato),
* **[!UICONTROL Average]** per calcolare la media dei valori in un campo numerico,
* **[!UICONTROL Minimum]** per calcolare il minimo dei valori in un campo numerico,
* **[!UICONTROL Maximum]** per calcolare il massimo dei valori in un campo numerico.
* **[!UICONTROL Sum]** per calcolare la somma dei valori in un campo numerico,
* **[!UICONTROL Standard deviation]** per calcolare la distribuzione dei valori restituiti intorno alla media.
* **[!UICONTROL Number of missing values]** per calcolare il numero di campi numerici senza valori definiti.
* **[!UICONTROL Decile distribution]** distribuire i valori restituiti in modo che ciascuno rappresenti l&#39;1/10 dei valori in un campo numerico.
* **[!UICONTROL Custom distribution]** distribuire i valori restituiti in base alle soglie definite dall&#39;utente.

   La **[!UICONTROL Detail...]** Questo pulsante consente di modificare una statistica e, se necessario, di personalizzarne il calcolo o la visualizzazione:

   ![](assets/s_ncs_user_report_wizard_030.png)

   L’ultimo passaggio della procedura guidata mostra il rapporto di analisi quantitativa.

   ![](assets/reporting_descriptive_view_report.png)

   Per apportare modifiche al rapporto, consulta [Elaborare un rapporto](../../reporting/using/processing-a-report.md).
