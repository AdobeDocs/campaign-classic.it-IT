---
product: campaign
title: Creazione di un grafico
description: Creazione di un grafico
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: d32b614f-82c1-4363-816c-4ebedaa5cfe9
source-git-commit: 7fa8cea04fb4e25187c48ad19330815e9b522b37
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 3%

---

# Creazione di un grafico{#creating-a-chart}

![](../../assets/common.svg)

È inoltre possibile raccogliere e visualizzare i dati del database in un grafico. Adobe Campaign fornisce una serie di rappresentazioni grafiche. La configurazione è descritta di seguito.

I grafici vengono inseriti direttamente in una pagina del rapporto tramite il menu di scelta rapida o la barra degli strumenti.

## Passaggi di creazione {#creation-steps}

Per creare un grafico in un rapporto, effettua le seguenti operazioni:

1. Modificare la pagina in cui si desidera visualizzare il grafico e selezionare il tipo di grafico sulla barra degli strumenti.

   ![](assets/s_advuser_report_page_activity_04.png)

1. Immettere un nome e una didascalia. Se necessario, è possibile modificare la posizione della didascalia utilizzando l’elenco a discesa.

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. Fai clic sul pulsante **[!UICONTROL Data]** per definire l’origine dati e la serie da calcolare.

   Le statistiche da visualizzare nel grafico possono essere calcolate in base a una query o ai dati contestuali, ovvero i dati forniti dalla transizione in entrata della pagina corrente (per ulteriori informazioni, consulta [Utilizzo dei dati contestuali](../../reporting/using/using-the-context.md#using-context-data)).

   * Fai clic sul pulsante **[!UICONTROL Filter data...]** collegamento per definire i criteri di filtro per i dati nel database.

      ![](assets/reporting_graph_add_filter.png)

   * Per utilizzare i dati contestuali, seleziona **[!UICONTROL Context data]** dal **[!UICONTROL Source]** e fai clic sul pulsante **[!UICONTROL Advanced settings...]** link. Quindi selezionare i dati che le statistiche riguarderanno.

      ![](assets/reporting_graph_from_context.png)

      Potrai quindi accedere ai dati contestuali per definire i valori da visualizzare nel grafico:

      ![](assets/reporting_graph_select-from_context.png)

## Tipi di grafico e varianti {#chart-types-and-variants}

Adobe Campaign offre diversi tipi di rappresentazioni grafiche. Sono descritte in dettaglio di seguito.

Il tipo di grafico viene selezionato quando viene inserito nella pagina.

![](assets/s_advuser_report_page_activity_04.png)

Può anche essere modificato tramite il **[!UICONTROL Chart type]** della sezione **[!UICONTROL General]** nel grafico.

![](assets/reporting_change_graph_type.png)

Le varianti dipendono dal tipo di grafico selezionato. Vengono selezionati tramite la **[!UICONTROL Variants...]** link.

### Suddivisione: grafici a torta {#breakdown--pie-charts}

Questo tipo di rappresentazione grafica consente di visualizzare una panoramica degli elementi misurati.

I grafici a torta consentono di analizzare una sola variabile.

![](assets/reporting_graph_type_sector_1.png)

La **[!UICONTROL Variants]** link ti consente di personalizzare il rendering complessivo del grafico.

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

Per questi tipi di grafici, le seguenti opzioni sono offerte nel **[!UICONTROL Variants]** finestra:

![](assets/reporting_select_graph_var.png)

Controlla la **[!UICONTROL Display caption]** per visualizzare la didascalia con il grafico e sceglierne la posizione:

![](assets/reporting_select_graph_legend.png)

Se appropriato, è possibile sovrapporre i valori.

![](assets/reporting_graph_type_histo.png)

Se necessario, è possibile invertire la sequenza di visualizzazione del valore. A questo scopo, seleziona la **[!UICONTROL Reverse stacking]** opzione .

### Conversione: imbuto {#conversion--funnel}

Questo tipo di grafico consente di tenere traccia del tasso di conversazione degli elementi misurati.

## Interazione con il grafico {#interaction-with-the-chart}

È possibile definire un&#39;azione quando l&#39;utente fa clic sul grafico. Apri **[!UICONTROL Interaction events]** e selezionare l&#39;azione da eseguire.

I possibili tipi di interazione e le relative configurazioni sono descritti in [questa sezione](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/s_ncs_advuser_report_wizard_017.png)

## Calcolo delle statistiche {#calculating-statistics}

I grafici consentono di visualizzare le statistiche sui dati raccolti.

Tali statistiche sono definite tramite **[!UICONTROL Series parameters]** della sezione **[!UICONTROL Data]** scheda .

Per creare una nuova statistica, fai clic sul pulsante **[!UICONTROL Add]** e configura la finestra appropriata. I tipi di calcolo disponibili sono descritti di seguito.

![](assets/reporting_add_statistics.png)

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).
