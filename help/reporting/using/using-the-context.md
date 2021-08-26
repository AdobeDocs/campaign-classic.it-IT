---
product: campaign
title: Utilizzo del contesto
description: Utilizzo del contesto
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 2%

---

# Utilizzo del contesto{#using-the-context}

![](../../assets/common.svg)

Per rappresentare i dati sotto forma di **[!UICONTROL tables]** o **[!UICONTROL charts]**, è possibile prelevarli da due origini: una nuova query (consulta [Definizione di un filtro diretto sui dati](#defining-a-direct-filter-on-data)) o il contesto del rapporto (consulta [Utilizzo dei dati contestuali](#using-context-data)).

## Definizione di un filtro diretto per i dati {#defining-a-direct-filter-on-data}

### Filtrare dati {#filtering-data}

L’utilizzo di un’attività di tipo **[!UICONTROL Query]** non è obbligatorio durante la creazione di un rapporto. I dati possono essere filtrati direttamente nelle tabelle e nei grafici che compongono il rapporto.

Questo consente di selezionare i dati da visualizzare nel rapporto direttamente tramite l’ **[!UICONTROL Page]** attività del rapporto.

A questo scopo, fai clic sul collegamento **[!UICONTROL Filter data...]** nella scheda **[!UICONTROL Data]** : questo collegamento ti consente di accedere all’editor espressioni per definire una query sui dati da analizzare.

![](assets/reporting_filter_data_from_page.png)

### Esempio: utilizzare un filtro in un grafico {#example--use-a-filter-in-a-chart}

Nell’esempio seguente, vogliamo che il grafico mostri solo i profili dei destinatari che vivono in Francia e che hanno effettuato un acquisto durante l’anno.

Per definire questo filtro, posizionare una pagina nel grafico e modificarlo. Fai clic sul collegamento **[!UICONTROL Filter data]** e crea il filtro corrispondente ai dati da visualizzare. Per ulteriori informazioni sulla creazione di query in Adobe Campaign, consulta [questa sezione](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

In questo caso, vogliamo visualizzare la suddivisione per città dei destinatari selezionati.

![](assets/reporting_graph_with_2vars.png)

Il rendering sarà simile al seguente:

![](assets/reporting_graph_with_2vars_preview.png)

### Esempio: utilizzare un filtro in una tabella pivot {#example--use-a-filter-in-a-pivot-table}

In questo esempio, il filtro consente di visualizzare solo i clienti non parigini nella tabella pivot, senza prima utilizzare un’altra query.

Applica i seguenti passaggi:

1. Posiziona una pagina nel grafico e modificala.
1. Creare una tabella pivot.
1. Vai alla scheda **[!UICONTROL Data]** e seleziona il cubo da utilizzare.
1. Fai clic sul collegamento **[!UICONTROL Filter data...]** e definisci la seguente query per rimuovere l’Adobe dall’elenco delle società.

   ![](assets/s_ncs_advuser_report_display_03.png)

Nel rapporto verranno visualizzati solo i destinatari che soddisfano i criteri di filtro.

![](assets/s_ncs_advuser_report_display_04.png)

## Utilizzo dei dati contestuali {#using-context-data}

Per rappresentare i dati sotto forma di **[!UICONTROL table]** o **[!UICONTROL chart]**, i dati possono provenire dal contesto del rapporto.

Nella pagina contenente la tabella o il grafico, la scheda **[!UICONTROL Data]** consente di selezionare l’origine dati.

![](assets/s_ncs_advuser_report_datasource_3.png)

* L’opzione **[!UICONTROL New query]** ti consente di creare una query per raccogliere i dati. Per ulteriori informazioni, consulta [Definizione di un filtro diretto per i dati](#defining-a-direct-filter-on-data).
* L’opzione **[!UICONTROL Context data]** ti consente di utilizzare i dati di input: il contesto del rapporto coincide con le informazioni contenute nella transizione in entrata della pagina che contiene il grafico o la tabella. Questo contesto può, ad esempio, contenere dati raccolti tramite un’attività **[!UICONTROL Query]** inserita prima dell’ attività **[!UICONTROL Page]** e per la quale è necessario specificare la tabella e i campi interessati dal rapporto.

Ad esempio, in una casella di query, genera la seguente query per i destinatari:

![](assets/s_ncs_advuser_report_datasource_2.png)

Quindi indica l’origine dei dati nel rapporto, in questo caso: **[!UICONTROL Data from the context]**.

La posizione dei dati viene dedotta automaticamente. Se necessario, puoi forzare il percorso dati.

![](assets/s_ncs_advuser_report_datasource_4.png)

Quando si selezionano i dati interessati dalle statistiche, i campi disponibili coincidono con i dati specificati nella query.

![](assets/s_ncs_advuser_report_datasource_1.png)
