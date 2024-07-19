---
product: campaign
title: Utilizzare il contesto nei rapporti
description: Scopri come utilizzare il contesto nei rapporti
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Reporting, Monitoring
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Utilizzare il contesto nei rapporti{#using-the-context}



Quando si desidera rappresentare dati in formato **[!UICONTROL tables]** o **[!UICONTROL charts]**, è possibile ricavarli da due origini: una nuova query (fare riferimento a [Definire un filtro diretto sui dati](#defining-a-direct-filter-on-data)) o il contesto del report (fare riferimento a [Utilizzare dati contestuali](#using-context-data)).

## Definire un filtro diretto per i dati {#defining-a-direct-filter-on-data}

### Filtrare i dati {#filtering-data}

L&#39;utilizzo di un&#39;attività di tipo **[!UICONTROL Query]** non è obbligatorio durante la creazione di un report. I dati possono essere filtrati direttamente nelle tabelle e nei grafici che compongono il rapporto.

Questo consente di selezionare i dati da visualizzare nel report direttamente tramite l&#39;attività **[!UICONTROL Page]** del report.

A tale scopo, fare clic sul collegamento **[!UICONTROL Filter data...]** nella scheda **[!UICONTROL Data]**: questo collegamento consente di accedere all&#39;editor espressioni per definire una query sui dati da analizzare.

![](assets/reporting_filter_data_from_page.png)

### Esempio: utilizzare un filtro in un grafico {#example--use-a-filter-in-a-chart}

Nell’esempio seguente, vogliamo che il grafico mostri solo i profili dei destinatari che vivono in Francia e che hanno effettuato un acquisto durante l’anno.

Per definire questo filtro, inserisci una pagina nel grafico e modificala. Fare clic sul collegamento **[!UICONTROL Filter data]** e creare il filtro corrispondente ai dati che si desidera visualizzare. Per ulteriori informazioni sulla creazione di query in Adobe Campaign, consulta [questa sezione](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

In questo caso, vogliamo visualizzare il raggruppamento per città dei destinatari selezionati.

![](assets/reporting_graph_with_2vars.png)

Il rendering sarà simile al seguente:

![](assets/reporting_graph_with_2vars_preview.png)

### Esempio: utilizzare un filtro in una tabella pivot {#example--use-a-filter-in-a-pivot-table}

In questo esempio, il filtro consente di visualizzare solo i clienti non parigini nella tabella pivot, senza utilizzare prima un’altra query.

Applica i seguenti passaggi:

1. Posizionare una pagina nel grafico e modificarla.
1. Creare una tabella pivot.
1. Passare alla scheda **[!UICONTROL Data]** e selezionare il cubo da utilizzare.
1. Fare clic sul collegamento **[!UICONTROL Filter data...]** e definire la query seguente per rimuovere l&#39;Adobe dall&#39;elenco delle società.

   ![](assets/s_ncs_advuser_report_display_03.png)

Solo i destinatari che soddisfano i criteri di filtro verranno visualizzati nel rapporto.

![](assets/s_ncs_advuser_report_display_04.png)

## Utilizzare i dati contestuali {#using-context-data}

Per rappresentare i dati sotto forma di **[!UICONTROL table]** o **[!UICONTROL chart]**, i dati possono provenire dal contesto del report.

Nella pagina che contiene la tabella o il grafico, la scheda **[!UICONTROL Data]** consente di selezionare l&#39;origine dati.

![](assets/s_ncs_advuser_report_datasource_3.png)

* L&#39;opzione **[!UICONTROL New query]** consente di creare una query per la raccolta dei dati. Per ulteriori informazioni, consulta [Definire un filtro diretto per i dati](#defining-a-direct-filter-on-data).
* L&#39;opzione **[!UICONTROL Context data]** consente di utilizzare i dati di input: il contesto del report coincide con le informazioni contenute nella transizione in entrata della pagina che contiene il grafico o la tabella. Questo contesto può, ad esempio, contenere dati raccolti tramite un&#39;attività **[!UICONTROL Query]** inserita prima dell&#39;attività **[!UICONTROL Page]** e per la quale è necessario specificare la tabella e i campi interessati dal report.

Ad esempio, in una casella di query, genera la seguente query per i destinatari:

![](assets/s_ncs_advuser_report_datasource_2.png)

Indicare quindi l&#39;origine dei dati nel report, in questo caso: **[!UICONTROL Data from the context]**.

La posizione dei dati viene dedotta automaticamente. Se necessario, puoi forzare il percorso dati.

![](assets/s_ncs_advuser_report_datasource_4.png)

Quando selezioni i dati che saranno interessati dalle statistiche, i campi disponibili coincidono con i dati specificati nella query.

![](assets/s_ncs_advuser_report_datasource_1.png)
