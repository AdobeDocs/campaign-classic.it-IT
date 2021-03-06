---
product: campaign
title: Casi d’uso
description: Casi di utilizzo del reporting
feature: Reporting
exl-id: e326e32e-7bb0-46ff-9ba5-94ccd1169af2
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 0%

---

# Casi d’uso{#use-cases}

![](../../assets/common.svg)

## Analisi di una popolazione {#analyzing-a-population}

L’esempio seguente consente di esplorare la popolazione di destinazione di un set di newsletter utilizzando la procedura guidata di analisi descrittiva.

Le fasi di implementazione sono descritte in dettaglio di seguito, mentre un elenco completo delle opzioni e delle descrizioni è disponibile nelle altre sezioni di questo capitolo.

### Identificazione della popolazione da analizzare {#identifying-the-population-to-analyze}

In questo esempio, vogliamo esplorare la popolazione target delle consegne incluse nella **Newsletter** cartella.

A questo scopo, seleziona le consegne interessate, quindi fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Action > Explore the target...]**.

![](assets/reporting_quick_start_1.png)

### Selezione di un tipo di analisi {#selecting-a-type-of-analysis}

Nel primo passaggio dell’assistente, puoi selezionare il modello di analisi descrittiva da utilizzare. Per impostazione predefinita, Adobe Campaign offre due modelli: **[!UICONTROL Qualitative distribution]** e **[!UICONTROL Quantitative distribution]**. Per ulteriori informazioni, consulta la sezione [Configurazione del modello di distribuzione qualitativa](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-qualitative-distribution-template) sezione . Le varie rappresentazioni sono presentate nel [Informazioni sull’analisi descrittiva](../../reporting/using/about-descriptive-analysis.md) sezione .

Per questo esempio, seleziona la **[!UICONTROL Qualitative distribution]** e scegliere una visualizzazione con un grafico e una tabella (matrice). Assegna un nome al rapporto (&quot;Analisi descrittiva&quot;) e fai clic su **[!UICONTROL Next]**.

![](assets/reporting_descriptive_quickstart_step_1.png)

### Selezione delle variabili da visualizzare {#selecting-the-variables-to-display}

Il passaggio successivo ti consente di selezionare i dati da visualizzare nella tabella.

Fai clic sul pulsante **[!UICONTROL Add...]** per selezionare la variabile contenente i dati da visualizzare. Qui vogliamo visualizzare le città dei destinatari della consegna su una riga:

![](assets/reporting_descriptive_quickstart_step_2.png)

Nelle colonne viene visualizzato il numero di acquisti per azienda. In questo esempio, gli importi sono aggregati nella variabile **Acquisti web** campo .

In questo caso, vogliamo definire il binding dei risultati per chiarirne la visualizzazione. A questo scopo, seleziona la **[!UICONTROL Manual]** opzione di binding e impostare le classi di calcolo per i segmenti da visualizzare:

![](assets/reporting_descriptive_quickstart_step_2a.png)

Quindi, fai clic su **[!UICONTROL Ok]** per approvare la configurazione.

Una volta definite le linee e le colonne, è possibile modificarle, spostarle o eliminarle utilizzando la barra degli strumenti.

![](assets/reporting_descriptive_quickstart_step_2b.png)

### Definizione del formato di visualizzazione {#defining-the-display-format}

Il passaggio successivo della procedura guidata consente di selezionare il tipo di grafico che si desidera generare.

In questo caso, scegli l’istogramma.

![](assets/reporting_descriptive_quickstart_step_3.png)

Le possibili configurazioni delle diverse immagini sono descritte in dettaglio nella sezione [Opzioni del grafico dei report di analisi](../../reporting/using/processing-a-report.md#analysis-report-chart-options) sezione .

### Configurazione della statistica da calcolare {#configuring-the-statistic-to-calculate}

Quindi specificare i calcoli da applicare ai dati raccolti. Per impostazione predefinita, la procedura guidata di analisi descrittiva esegue un conteggio semplice dei valori.

Questa finestra consente di definire l’elenco delle statistiche da calcolare.

![](assets/reporting_descriptive_quickstart_step_4.png)

Per creare una nuova statistica, fai clic sul pulsante **[!UICONTROL Add]** pulsante . Per ulteriori informazioni, consulta [Calcolo delle statistiche](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).

### Visualizzazione e utilizzo del rapporto {#viewing-and-using-the-report}

Nell’ultimo passaggio della procedura guidata vengono visualizzati la tabella e il grafico.

È possibile memorizzare, esportare o stampare i dati utilizzando la barra degli strumenti sopra la tabella. Per ulteriori informazioni, consulta [Elaborazione di un report](../../reporting/using/processing-a-report.md).

![](assets/reporting_descriptive_quickstart_step_5.png)

## Analisi qualitativa dei dati {#qualitative-data-analysis}

### Esempio di visualizzazione di un grafico {#example-of-a-chart-display}

**Target**: genera un rapporto di analisi sulla posizione dei potenziali clienti o dei clienti.

1. Apri la procedura guidata di analisi descrittiva e seleziona **[!UICONTROL Chart]** solo.

   ![](assets/s_ncs_user_report_wizard_05a.png)

   Fai clic su **[!UICONTROL Next]** per approvare questo passaggio.

1. Quindi seleziona la **[!UICONTROL 2 variables]** e specifica che **[!UICONTROL First variable (abscissa)]** farà riferimento allo stato del destinatario (potenziale/cliente) e la seconda variabile farà riferimento al paese.
1. Seleziona **[!UICONTROL Cylinders]** come tipo.

   ![](assets/s_ncs_user_report_wizard_05.png)

1. Fai clic su **[!UICONTROL Next]** e lascia il valore predefinito **[!UICONTROL Simple count]** statistica.
1. Fai clic su **[!UICONTROL Next]** per visualizzare il rapporto.

   ![](assets/s_ncs_user_report_wizard_04.png)

   Passa il cursore sopra un bar per vedere il numero esatto di clienti o potenziali clienti per questo paese.

1. Attiva o disattiva la visualizzazione di uno dei paesi in base alla legenda.

   ![](assets/s_ncs_user_report_wizard_06png.png)

### Esempio di visualizzazione di una tabella {#example-of-a-table-display}

**Target**: analizzare i domini e-mail aziendali.

1. Apri la procedura guidata di analisi descrittiva e seleziona la **[!UICONTROL Array]** solo modalità di visualizzazione.

   ![](assets/s_ncs_user_report_wizard_03a.png)

   Fai clic sul pulsante **[!UICONTROL Next]** per approvare questo passaggio.

1. Seleziona la **[!UICONTROL Company]** come colonna e **[!UICONTROL Email domain]** come riga.
1. Mantieni la **[!UICONTROL By rows]** opzione per l&#39;orientamento delle statistiche: il calcolo statistico viene visualizzato a destra del **[!UICONTROL Email domain]** variabile.

   ![](assets/s_ncs_user_report_wizard_03b.png)

   Fai clic su **[!UICONTROL Next]** per approvare questo passaggio.

1. Quindi inserisci le statistiche da calcolare: mantieni il conteggio predefinito e crea una nuova statistica. A questo scopo, fai clic su **[!UICONTROL Add]** e seleziona **[!UICONTROL Total percentage distribution]** come operatore.

   ![](assets/s_ncs_user_report_wizard_03.png)

1. Immetti un’etichetta per la statistica in modo che non ci sia un campo vuoto quando viene visualizzato il rapporto.

   ![](assets/s_ncs_user_report_wizard_014.png)

1. Fai clic su **[!UICONTROL Next]** per visualizzare il rapporto.

   ![](assets/s_ncs_user_report_wizard_06.png)

1. Una volta generato il rapporto di analisi, puoi adattare lo schermo in base alle tue esigenze senza modificare la configurazione. Ad esempio, puoi cambiare gli assi: fare clic con il pulsante destro del mouse sui nomi di dominio e selezionare **[!UICONTROL Turn]** nel menu di scelta rapida.

   ![](assets/s_ncs_user_report_wizard_07.png)

   Nella tabella vengono visualizzate le informazioni come segue:

   ![](assets/s_ncs_user_report_wizard_07a.png)

## Analisi quantitativa dei dati {#quantitative-data-analysis}

**Target**: generare un rapporto di analisi quantitativa sull’età del destinatario

1. Apri la procedura guidata di analisi descrittiva e seleziona **[!UICONTROL Quantitative distribution]** dall’elenco a discesa.

   ![](assets/s_ncs_user_report_wizard_011a.png)

   Fai clic sul pulsante **[!UICONTROL Next]** per approvare questo passaggio.

1. Seleziona la **[!UICONTROL Age]** e immetti la relativa etichetta. Specificare se si tratta di un numero intero, quindi fare clic su **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_report_wizard_011.png)

1. Elimina **[!UICONTROL Deciles]**, **[!UICONTROL Distribution]** e **[!UICONTROL Sum]** statistiche: non sono necessarie qui.

   ![](assets/s_ncs_user_report_wizard_012.png)

1. Fai clic su **[!UICONTROL Next]** per visualizzare il rapporto.

   ![](assets/s_ncs_user_report_wizard_013.png)

## Analisi di una destinazione di transizione in un flusso di lavoro {#analyzing-a-transition-target-in-a-workflow}

**Target**: per generare rapporti sulla popolazione di un flusso di lavoro di targeting

1. Apri il flusso di lavoro di targeting desiderato.
1. Fai clic con il pulsante destro del mouse su una transizione che punta alla tabella dei destinatari.
1. Seleziona **[!UICONTROL Analyze target]** nel menu a discesa per aprire la finestra di analisi descrittiva.

   ![](assets/s_ncs_user_report_wizard_from_transision.png)

1. A questo punto, puoi selezionare la **[!UICONTROL Existing analyses and reports]** e utilizza i rapporti creati in precedenza (consulta [Riutilizzo di report e analisi esistenti](../../reporting/using/processing-a-report.md#re-using-existing-reports-and-analyses)) o crea una nuova analisi descrittiva. Per eseguire questa operazione, lascia la **[!UICONTROL New descriptive analysis from a template]** opzione selezionata per impostazione predefinita.

   Il resto della configurazione è lo stesso di tutte le analisi descrittive.

### Raccomandazioni per l’analisi di Target {#target-analyze-recommendations}

L’analisi di una popolazione in un flusso di lavoro richiede che la popolazione sia ancora presente nella transizione. Se il flusso di lavoro viene avviato, il risultato relativo alla popolazione potrebbe essere eliminato dalla transizione. Per eseguire un’analisi, puoi effettuare le seguenti operazioni:

* Stacca la transizione dalla relativa attività di destinazione e avvia il flusso di lavoro per renderla attiva. Una volta che la transizione inizia a lampeggiare, avvia la procedura guidata nel modo consueto.

   ![](assets/s_ncs_user_report_wizard_018.png)

* Modifica le proprietà del flusso di lavoro selezionando la **[!UICONTROL Keep the result of interim populations between two executions]** opzione . Questo consente di avviare un’analisi della transizione scelta, anche se il flusso di lavoro è terminato.

   ![](assets/s_ncs_user_report_wizard_020.png)

   Se la popolazione è stata eliminata dalla transizione, un messaggio di errore ti chiede di selezionare l’opzione interessata prima di avviare la procedura guidata di analisi descrittiva.

   ![](assets/s_ncs_user_report_wizard_019.png)

>[!CAUTION]
>
>La **[!UICONTROL Keep the result of interim populations between two executions]** L&#39;opzione deve essere utilizzata solo nelle fasi di sviluppo, ma mai per un ambiente di produzione.\
>Le popolazioni intermedie vengono automaticamente eliminate una volta raggiunto il termine di conservazione. Questa scadenza è specificata nelle proprietà del flusso di lavoro **[!UICONTROL Execution]** scheda .

## Analisi dei registri di tracciamento dei destinatari {#analyzing-recipient-tracking-logs}

La procedura guidata di analisi descrittiva può generare rapporti su altre tabelle di lavoro. Questo significa che puoi analizzare i registri di consegna creando un rapporto dedicato.

In questo esempio, vogliamo analizzare il tasso di reattività dei destinatari di una newsletter.

A questo scopo, esegui i seguenti passaggi:

1. Apri la procedura guidata di analisi descrittiva tramite **[!UICONTROL Tools > Descriptive analysis]** e modificare la tabella di lavoro predefinita. Seleziona **[!UICONTROL Recipient tracking log]** e aggiungi un filtro per escludere le bozze e includere le newsletter.

   ![](assets/reporting_descriptive_sample_tracking_1.png)

   Seleziona una visualizzazione della tabella e fai clic su **[!UICONTROL Next]**.

1. Nella finestra successiva, specifica che l’analisi riguarda le consegne.

   ![](assets/reporting_descriptive_sample_tracking_2.png)

   In questo caso, le etichette di consegna verranno visualizzate nella prima colonna.

1. Elimina il conteggio predefinito e crea tre statistiche per configurare le statistiche da visualizzare nella tabella.

   Qui, per ogni newsletter, la tabella mostra: il numero di aperture, il numero di clic e il tasso di reattività (in percentuale).

1. Aggiungi una statistica per il conteggio del numero di clic: definire il filtro pertinente nella **[!UICONTROL Filter]** scheda .

   ![](assets/reporting_descriptive_sample_tracking_3.png)

1. Quindi fai clic sul pulsante **[!UICONTROL General]** scheda per rinominare l’etichetta delle statistiche e l’alias:

   ![](assets/reporting_descriptive_sample_tracking_4.png)

1. Aggiungi una seconda statistica per il conteggio del numero di aperture:

   ![](assets/reporting_descriptive_sample_tracking_5.png)

1. Quindi fai clic sul pulsante **[!UICONTROL General]** per rinominare l’etichetta delle statistiche e il relativo alias:

   ![](assets/reporting_descriptive_sample_tracking_6.png)

1. Aggiungi la terza statistica e seleziona la **[!UICONTROL Calculated field]** per misurare il tasso di reattività.

   ![](assets/reporting_descriptive_sample_tracking_7.png)

   Vai a **[!UICONTROL User function]** e immettere la seguente formula:

   ```
   @clic / @open * 100
   ```

   Adatta l’etichetta delle statistiche come mostrato di seguito:

   ![](assets/reporting_descriptive_sample_tracking_8.png)

   Infine, specifica se i valori sono visualizzati come percentuale: per eseguire questa operazione, deseleziona la **[!UICONTROL Default formatting]** in **[!UICONTROL Advanced]** e seleziona **[!UICONTROL Percentage]** senza punto decimale.

   ![](assets/reporting_descriptive_sample_tracking_10.png)

1. Fai clic su **[!UICONTROL Next]** per visualizzare il rapporto.

   ![](assets/reporting_descriptive_sample_tracking_9.png)

## Analisi dei registri di esclusione della consegna {#analyzing-delivery-exclusion-logs}

Se l’analisi riguarda una consegna, puoi analizzare la popolazione esclusa. A questo scopo, seleziona le consegne da analizzare e fai clic con il pulsante destro del mouse per accedere al **[!UICONTROL Action > Explore exclusions]** menu.

![](assets/reporting_descriptive_exclusion_menu.png)

Viene visualizzata la procedura guidata di analisi descrittiva e l’analisi riguarda i registri di esclusione dei destinatari.

Ad esempio, puoi visualizzare i domini di tutti gli indirizzi esclusi e ordinarli per data di esclusione.

![](assets/reporting_descriptive_exclusion_sample.png)

Questo genererebbe il seguente tipo di rapporto:

![](assets/reporting_descriptive_exclusion_result.png)
