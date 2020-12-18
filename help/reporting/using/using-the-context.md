---
solution: Campaign Classic
product: campaign
title: Utilizzo del contesto
description: Utilizzo del contesto
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 2%

---


# Utilizzo del contesto{#using-the-context}

Se si desidera rappresentare i dati sotto forma di **[!UICONTROL tables]** o **[!UICONTROL charts]**, è possibile prelevarli da due origini: una nuova query (fare riferimento a [Definizione di un filtro diretto sui dati](#defining-a-direct-filter-on-data)) o al contesto del rapporto (fare riferimento a [Utilizzo dei dati contestuali](#using-context-data)).

## Definizione di un filtro diretto sui dati {#defining-a-direct-filter-on-data}

### Filtrare dati {#filtering-data}

L&#39;utilizzo di un&#39;attività di tipo **[!UICONTROL Query]** non è obbligatorio quando si crea un report. I dati possono essere filtrati direttamente nelle tabelle e nei grafici che compongono il rapporto.

Questo consente di selezionare i dati da visualizzare nel report direttamente tramite l&#39;attività **[!UICONTROL Page]** del report.

A tal fine, fare clic sul collegamento **[!UICONTROL Filter data...]** nella scheda **[!UICONTROL Data]**: questo collegamento consente di accedere all&#39;editor delle espressioni per definire una query sui dati da analizzare.

![](assets/reporting_filter_data_from_page.png)

### Esempio: utilizzare un filtro in un grafico {#example--use-a-filter-in-a-chart}

Nell&#39;esempio seguente, il grafico mostrerà solo i profili dei destinatari residenti in Francia e che hanno effettuato un acquisto durante l&#39;anno.

Per definire questo filtro, posizionate una pagina nel grafico e modificatelo. Fare clic sul collegamento **[!UICONTROL Filter data]** e creare il filtro corrispondente ai dati da visualizzare. Per ulteriori informazioni sulla creazione di query in  Adobe Campaign, consultare [questa sezione](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Qui si desidera visualizzare la suddivisione per città dei destinatari selezionati.

![](assets/reporting_graph_with_2vars.png)

Il rendering sarà simile al seguente:

![](assets/reporting_graph_with_2vars_preview.png)

### Esempio: utilizzare un filtro in una tabella pivot{#example--use-a-filter-in-a-pivot-table}

In questo esempio, il filtro consente di visualizzare nella tabella pivot solo i clienti non parigini, senza prima utilizzare un&#39;altra query.

Effettuate le seguenti operazioni:

1. Inserite una pagina nel grafico e modificatela.
1. Creare una tabella pivot.
1. Fare clic sulla scheda **[!UICONTROL Data]** e selezionare il cubo da utilizzare.
1. Fare clic sul collegamento **[!UICONTROL Filter data...]** e definire la seguente query per rimuovere  Adobe dall&#39;elenco delle società.

   ![](assets/s_ncs_advuser_report_display_03.png)

Nel rapporto verranno visualizzati solo i destinatari che soddisfano i criteri di filtro.

![](assets/s_ncs_advuser_report_display_04.png)

## Utilizzo dei dati contestuali {#using-context-data}

Per rappresentare i dati sotto forma di **[!UICONTROL table]** o **[!UICONTROL chart]**, i dati possono provenire dal contesto del rapporto.

Nella pagina contenente la tabella o il grafico, la scheda **[!UICONTROL Data]** consente di selezionare l&#39;origine dati.

![](assets/s_ncs_advuser_report_datasource_3.png)

* L&#39;opzione **[!UICONTROL New query]** consente di creare una query per la raccolta dei dati. Per ulteriori informazioni, vedere [Definizione di un filtro diretto per i dati](#defining-a-direct-filter-on-data).
* L&#39;opzione **[!UICONTROL Context data]** consente di utilizzare i dati di input: il contesto del rapporto coincide con le informazioni contenute nella transizione in entrata della pagina che contiene il grafico o la tabella. Questo contesto può, ad esempio, contenere i dati raccolti tramite un&#39;attività **[!UICONTROL Query]** collocata prima dell&#39;attività **[!UICONTROL Page]** e per la quale è necessario specificare la tabella e i campi interessati dal rapporto.

Ad esempio, in una casella di query, generare la seguente query per i destinatari:

![](assets/s_ncs_advuser_report_datasource_2.png)

Quindi indicate l&#39;origine dei dati nel rapporto, in questo caso: **[!UICONTROL Data from the context]**.

La posizione dei dati viene ricavata automaticamente. Se necessario, è possibile forzare il percorso dei dati.

![](assets/s_ncs_advuser_report_datasource_4.png)

Quando si selezionano i dati che saranno interessati dalle statistiche, i campi disponibili coincidono con i dati specificati nella query.

![](assets/s_ncs_advuser_report_datasource_1.png)

