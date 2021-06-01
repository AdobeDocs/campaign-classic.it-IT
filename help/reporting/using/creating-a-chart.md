---
product: campaign
title: Creazione di un grafico
description: Creazione di un grafico
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: d32b614f-82c1-4363-816c-4ebedaa5cfe9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 2%

---

# Creazione di un grafico{#creating-a-chart}

È inoltre possibile raccogliere e visualizzare i dati del database in un grafico. Adobe Campaign fornisce una serie di rappresentazioni grafiche. La configurazione è descritta di seguito.

I grafici vengono inseriti direttamente in una pagina del rapporto tramite il menu di scelta rapida o la barra degli strumenti.

## Passaggi di creazione {#creation-steps}

Per creare un grafico in un rapporto, effettua le seguenti operazioni:

1. Modificare la pagina in cui si desidera visualizzare il grafico e selezionare il tipo di grafico sulla barra degli strumenti.

   ![](assets/s_advuser_report_page_activity_04.png)

1. Immettere un nome e una didascalia. Se necessario, è possibile modificare la posizione della didascalia utilizzando l’elenco a discesa.

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. Fai clic sulla scheda **[!UICONTROL Data]** per definire l’origine dati e la serie da calcolare.

   Le statistiche da visualizzare nel grafico possono essere calcolate in base a una query o ai dati contestuali, ovvero ai dati forniti dalla transizione in entrata della pagina corrente (per ulteriori informazioni, consulta [Utilizzo dei dati contestuali](../../reporting/using/using-the-context.md#using-context-data)).

   * Fai clic sul collegamento **[!UICONTROL Filter data...]** per definire i criteri di filtro per i dati nel database.

      ![](assets/reporting_graph_add_filter.png)

   * Per utilizzare i dati contestuali, seleziona questa opzione e fai clic sul collegamento **[!UICONTROL Advanced settings...]** . Quindi selezionare i dati che le statistiche riguarderanno.

      ![](assets/reporting_graph_from_context.png)

      Potrai quindi accedere ai dati contestuali per definire i valori da visualizzare nel grafico:

      ![](assets/reporting_graph_select-from_context.png)

## Tipi di grafico e varianti {#chart-types-and-variants}

Adobe Campaign offre diversi tipi di rappresentazioni grafiche. Sono descritte in dettaglio di seguito.

Il tipo di grafico viene selezionato quando viene inserito nella pagina.

![](assets/s_advuser_report_page_activity_04.png)

Può anche essere modificato tramite la sezione **[!UICONTROL Chart type]** della scheda **[!UICONTROL General]** del grafico.

![](assets/reporting_change_graph_type.png)

Le varianti dipendono dal tipo di grafico selezionato. Vengono selezionati tramite il collegamento **[!UICONTROL Variants...]** .

### Suddivisione: grafici a torta {#breakdown--pie-charts}

Questo tipo di rappresentazione grafica consente di visualizzare una panoramica degli elementi misurati.

I grafici a torta consentono di analizzare una sola variabile.

![](assets/reporting_graph_type_sector_1.png)

Il collegamento **[!UICONTROL Variants]** ti consente di personalizzare il rendering complessivo del grafico.

![](assets/reporting_graph_type_sector_2.png)

I grafici a torta consentono di immettere il valore del raggio interno nel campo appropriato.

Ad esempio:

0.00 traccia un cerchio completo.

![](assets/s_ncs_advuser_report_sector_exple1.png)

0,40 traccia un cerchio con un raggio del 40%.

![](assets/s_ncs_advuser_report_sector_exple2.png)

1.00 traccia solo l&#39;esterno del cerchio.

![](assets/s_ncs_advuser_report_sector_exple3.png)

### Evoluzione: curve e aree {#evolution--curves-and-areas}

Questo tipo di rappresentazione grafica ti permette di comprendere l’evoluzione di una o più misure nel tempo.

![](assets/reporting_graph_type_curve.png)

### Confronto: istogrammi {#comparison--histograms}

Gli istogrammi consentono di confrontare i valori di una o più variabili.

Per questi tipi di grafici, nella finestra **[!UICONTROL Variants]** sono disponibili le seguenti opzioni:

![](assets/reporting_select_graph_var.png)

Seleziona l’opzione **[!UICONTROL Display caption]** per visualizzare la didascalia con il grafico e scegli la relativa posizione:

![](assets/reporting_select_graph_legend.png)

Se appropriato, è possibile sovrapporre i valori.

![](assets/reporting_graph_type_histo.png)

Se necessario, è possibile invertire la sequenza di visualizzazione del valore. A questo scopo, seleziona l’opzione **[!UICONTROL Reverse stacking]** .

### Conversione: imbuto {#conversion--funnel}

Questo tipo di grafico consente di tenere traccia del tasso di conversazione degli elementi misurati.

### Avanzamento: misuratore {#progress--gauge}

Questo tipo di grafico consente di visualizzare l’avanzamento di un valore rispetto a un obiettivo definito. Nell’esempio seguente, il quadrante nero mostra il numero di consegne inviate correttamente (76) su un obiettivo di 100 consegne. Il misuratore è diviso in tre intervalli che corrispondono a stati specifici.

![](assets/reporting_graph_type_gauge.png)

Questi elementi vengono definiti durante la configurazione del grafico.

![](assets/reporting_graph_type_gauge1.png)

* Il campo **[!UICONTROL Value]** è rappresentato da un quadrante nero nel grafico. Rappresenta l’elemento di cui si desidera calcolare l’avanzamento. Il valore da rappresentare deve essere già stato salvato per essere utilizzato.
* Il campo **[!UICONTROL Goal]** rappresenta il valore massimo da raggiungere.
* Utilizzando il campo **[!UICONTROL Other mark]** è possibile aggiungere un secondo indicatore al grafico.
* I campi **[!UICONTROL Display range]** consentono di specificare i valori tra cui viene calcolato il rapporto.
* Il campo **[!UICONTROL Value ranges]** consente di attribuire gli stati (Nessuno, Non valido, Accettabile, Buono) a un set di valori per illustrare meglio l’avanzamento.

Nella sezione **[!UICONTROL Display settings]**, il **[!UICONTROL Change appearance...]** ti consente di configurare la modalità di visualizzazione del grafico.

![](assets/reporting_graph_type_gauge2.png)

L’opzione **[!UICONTROL Display the value below the gauge]** ti consente di visualizzare l’avanzamento del valore sotto il grafico.

Il campo **[!UICONTROL Aperture ratio]** , che deve essere compreso tra 0 e 1, consente di modificare l’apertura del rapporto in un cerchio più o meno completo. Nell’esempio precedente, il valore 0,50 corrisponde a un semicerchio.

Il campo **[!UICONTROL Width]** consente di modificare le dimensioni del grafico.

## Interazione con il grafico {#interaction-with-the-chart}

È possibile definire un&#39;azione quando l&#39;utente fa clic sul grafico. Apri la finestra **[!UICONTROL Interaction events]** e seleziona l’azione da eseguire.

I tipi di interazione possibili e le relative configurazioni sono descritti in [questa sezione](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/s_ncs_advuser_report_wizard_017.png)

## Calcolo delle statistiche {#calculating-statistics}

I grafici consentono di visualizzare le statistiche sui dati raccolti.

Queste statistiche sono definite tramite la sezione **[!UICONTROL Series parameters]** della scheda **[!UICONTROL Data]** .

Per creare una nuova statistica, fai clic sull’icona **[!UICONTROL Add]** e configura la finestra appropriata. I tipi di calcolo disponibili sono descritti di seguito.

![](assets/reporting_add_statistics.png)

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).
