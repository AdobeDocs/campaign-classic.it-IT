---
title: Utilizzo del contesto
seo-title: Utilizzo del contesto
description: Utilizzo del contesto
seo-description: null
page-status-flag: never-activated
uuid: ac8c7068-d640-4934-b7f5-bc91b98eab4c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 72fe6df0-0271-48f9-bd6d-bb1ff25fbdf3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---


# Utilizzo del contesto{#using-the-context}

Quando si desidera rappresentare i dati sotto forma di **[!UICONTROL tables]** o **[!UICONTROL charts]**, è possibile prelevarli da due origini: una nuova query (fare riferimento a [Definizione di un filtro diretto sui dati](#defining-a-direct-filter-on-data)) o il contesto del rapporto (fare riferimento a [Utilizzo dei dati](#using-context-data)contestuali).

## Definizione di un filtro diretto sui dati {#defining-a-direct-filter-on-data}

### Filtrare dati {#filtering-data}

L&#39;utilizzo di un&#39;attività di **[!UICONTROL Query]** tipo non è obbligatorio quando si crea un rapporto. I dati possono essere filtrati direttamente nelle tabelle e nei grafici che compongono il rapporto.

Questo consente di selezionare i dati da visualizzare nel rapporto direttamente tramite l&#39; **[!UICONTROL Page]** attività del rapporto.

A questo scopo, fate clic sul **[!UICONTROL Filter data...]** collegamento nella **[!UICONTROL Data]** scheda: questo collegamento consente di accedere all&#39;editor delle espressioni per definire una query sui dati da analizzare.

![](assets/reporting_filter_data_from_page.png)

### Esempio: utilizzare un filtro in un grafico {#example--use-a-filter-in-a-chart}

Nell&#39;esempio seguente, il grafico mostrerà solo i profili dei destinatari residenti in Francia e che hanno effettuato un acquisto durante l&#39;anno.

Per definire questo filtro, posizionate una pagina nel grafico e modificatelo. Fare clic sul **[!UICONTROL Filter data]** collegamento e creare il filtro corrispondente ai dati da visualizzare. Per ulteriori informazioni sulla creazione di query in  Adobe Campaign, consultare [questa sezione](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Qui si desidera visualizzare la suddivisione per città dei destinatari selezionati.

![](assets/reporting_graph_with_2vars.png)

Il rendering sarà simile al seguente:

![](assets/reporting_graph_with_2vars_preview.png)

### Esempio: utilizzare un filtro in una tabella pivot {#example--use-a-filter-in-a-pivot-table}

In questo esempio, il filtro consente di visualizzare nella tabella pivot solo i clienti non parigini, senza prima utilizzare un&#39;altra query.

Effettuate le seguenti operazioni:

1. Inserite una pagina nel grafico e modificatela.
1. Creare una tabella pivot.
1. Passare alla **[!UICONTROL Data]** scheda e selezionare il cubo da utilizzare.
1. Fate clic sul **[!UICONTROL Filter data...]** collegamento e definite la seguente query per rimuovere  Adobe dall’elenco delle società.

   ![](assets/s_ncs_advuser_report_display_03.png)

Nel rapporto verranno visualizzati solo i destinatari che soddisfano i criteri di filtro.

![](assets/s_ncs_advuser_report_display_04.png)

## Utilizzo dei dati contestuali {#using-context-data}

Per rappresentare i dati sotto forma di un **[!UICONTROL table]** o di un **[!UICONTROL chart]**, i dati possono provenire dal contesto del rapporto.

Nella pagina contenente la tabella o il grafico, la **[!UICONTROL Data]** scheda consente di selezionare l&#39;origine dati.

![](assets/s_ncs_advuser_report_datasource_3.png)

* L&#39; **[!UICONTROL New query]** opzione consente di creare una query per la raccolta dei dati. Per ulteriori informazioni, vedere [Definizione di un filtro diretto per i dati](#defining-a-direct-filter-on-data).
* L&#39; **[!UICONTROL Context data]** opzione consente di utilizzare i dati di input: il contesto del rapporto coincide con le informazioni contenute nella transizione in entrata della pagina che contiene il grafico o la tabella. Questo contesto può, ad esempio, contenere dati raccolti tramite un&#39; **[!UICONTROL Query]** attività posta prima dell&#39; **[!UICONTROL Page]** attività e per la quale è necessario specificare la tabella e i campi interessati dal rapporto.

Ad esempio, in una casella di query, generare la seguente query per i destinatari:

![](assets/s_ncs_advuser_report_datasource_2.png)

Quindi indicate l&#39;origine dei dati nel rapporto, in questo caso: **[!UICONTROL Data from the context]**.

La posizione dei dati viene ricavata automaticamente. Se necessario, è possibile forzare il percorso dei dati.

![](assets/s_ncs_advuser_report_datasource_4.png)

Quando si selezionano i dati che saranno interessati dalle statistiche, i campi disponibili coincidono con i dati specificati nella query.

![](assets/s_ncs_advuser_report_datasource_1.png)

