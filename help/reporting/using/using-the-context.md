---
product: campaign
title: Utilizzare il contesto nei rapporti
description: Scopri come utilizzare il contesto nei rapporti
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Utilizzare il contesto nei rapporti{#using-the-context}

![](../../assets/common.svg)

Quando desideri rappresentare i dati sotto forma di **[!UICONTROL tables]** o **[!UICONTROL charts]**, può essere prelevato da due fonti: una nuova query (fare riferimento a [Definire un filtro diretto per i dati](#defining-a-direct-filter-on-data)) o il contesto del rapporto (consulta [Utilizzare i dati contestuali](#using-context-data)).

## Definire un filtro diretto per i dati {#defining-a-direct-filter-on-data}

### Filtrare i dati {#filtering-data}

Utilizzo di un **[!UICONTROL Query]** l’attività di tipo non è obbligatoria quando si crea un rapporto. I dati possono essere filtrati direttamente nelle tabelle e nei grafici che compongono il rapporto.

Questo consente di selezionare i dati da visualizzare nel rapporto direttamente tramite il **[!UICONTROL Page]** attività del rapporto.

A questo scopo, fai clic sul pulsante **[!UICONTROL Filter data...]** nel collegamento **[!UICONTROL Data]** scheda: questo collegamento ti consente di accedere all’editor espressioni per definire una query sui dati da analizzare.

![](assets/reporting_filter_data_from_page.png)

### Esempio: utilizzare un filtro in un grafico {#example--use-a-filter-in-a-chart}

Nell’esempio seguente, vogliamo che il grafico mostri solo i profili dei destinatari che vivono in Francia e che hanno effettuato un acquisto durante l’anno.

Per definire questo filtro, posizionare una pagina nel grafico e modificarlo. Fai clic sul pulsante **[!UICONTROL Filter data]** crea e collega il filtro corrispondente ai dati da visualizzare. Per ulteriori informazioni sulla creazione di query in Adobe Campaign, consulta [questa sezione](../../platform/using/about-queries-in-campaign.md).

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
1. Vai a **[!UICONTROL Data]** e selezionare il cubo da utilizzare.
1. Fai clic sul pulsante **[!UICONTROL Filter data...]** collega e definisci la seguente query per rimuovere l’Adobe dall’elenco delle società.

   ![](assets/s_ncs_advuser_report_display_03.png)

Nel rapporto verranno visualizzati solo i destinatari che soddisfano i criteri di filtro.

![](assets/s_ncs_advuser_report_display_04.png)

## Utilizzare i dati contestuali {#using-context-data}

Per rappresentare i dati sotto forma di **[!UICONTROL table]** o **[!UICONTROL chart]**, i dati possono provenire dal contesto del rapporto.

Nella pagina contenente la tabella o il grafico, la **[!UICONTROL Data]** consente di selezionare l’origine dati.

![](assets/s_ncs_advuser_report_datasource_3.png)

* La **[!UICONTROL New query]** consente di creare una query per la raccolta dei dati. Per ulteriori informazioni, consulta [Definire un filtro diretto per i dati](#defining-a-direct-filter-on-data).
* La **[!UICONTROL Context data]** consente di utilizzare i dati di input: il contesto del rapporto coincide con le informazioni contenute nella transizione in entrata della pagina che contiene il grafico o la tabella. Questo contesto può, ad esempio, contenere dati raccolti tramite un **[!UICONTROL Query]** attività posizionata prima della **[!UICONTROL Page]** attività e per la quale devi specificare la tabella e i campi interessati dal rapporto.

Ad esempio, in una casella di query, genera la seguente query per i destinatari:

![](assets/s_ncs_advuser_report_datasource_2.png)

Quindi indica l’origine dei dati nel rapporto, in questo caso: **[!UICONTROL Data from the context]**.

La posizione dei dati viene dedotta automaticamente. Se necessario, puoi forzare il percorso dati.

![](assets/s_ncs_advuser_report_datasource_4.png)

Quando si selezionano i dati interessati dalle statistiche, i campi disponibili coincidono con i dati specificati nella query.

![](assets/s_ncs_advuser_report_datasource_1.png)
