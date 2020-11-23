---
solution: Campaign Classic
product: campaign
title: Raccolta di dati da analizzare
description: Raccolta di dati da analizzare
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 3%

---


# Raccolta di dati da analizzare{#collecting-data-to-analyze}

I dati da utilizzare per creare il rapporto possono essere selezionati direttamente nella pagina del rapporto (per ulteriori informazioni, fare riferimento a [Utilizzo del contesto](../../reporting/using/using-the-context.md)) o raccolti tramite una o più query.

Questa attività offre tre metodi diversi:

1. Creazione di una query utilizzando i dati nel database.
1. Elaborazione dei dati contenuti in un elenco.
1. Utilizzo dei dati contenuti in un cubo esistente.

La scelta del metodo dipende dal tipo di calcolo, dal volume dei dati e dalla loro durata, ecc. Tutti questi parametri devono essere esaminati attentamente per evitare il sovraccarico del database Adobe Campaign  e per ottimizzare la generazione e la manipolazione dei rapporti creati. Per ulteriori informazioni, consulta [questa pagina](../../reporting/using/best-practices.md#optimizing-report-creation).

In tutti i casi, i dati vengono raccolti tramite un&#39;attività di **[!UICONTROL Query]** tipo.

![](assets/reporting_query_edit.png)

Questa modalità di selezione dei dati è pertinente quando i dati nel rapporto devono essere raccolti o generati utilizzando i dati presenti nel database. In alcuni casi, potete anche selezionare i dati direttamente dagli elementi utilizzati nel rapporto. Ad esempio, quando si inserisce un grafico, è possibile selezionare direttamente i dati di origine. Per ulteriori informazioni, vedere [Uso del contesto](../../reporting/using/using-the-context.md).

## Utilizzo dei dati di uno schema {#using-the-data-from-a-schema}

Per utilizzare i dati collegati a uno schema di database, selezionare l&#39;opzione appropriata nell&#39;editor di query e configurare la query da applicare.

L&#39;esempio seguente consente di raccogliere il numero di destinatari per ciascun paese, tra i profili presenti nel database. Possono quindi essere visualizzati in un rapporto sotto forma di tabella.

![](assets/reporting_query_from_schema.png)

## Utilizzo di un elenco importato {#using-an-imported-list}

Per creare un rapporto, puoi utilizzare i dati di un elenco di dati importati.

A questo scopo, selezionate l’ **[!UICONTROL Use an imported list]** opzione nella casella di query e selezionate l’elenco interessato.

![](assets/reporting_query_from_list.png)

Fate clic sul **[!UICONTROL Edit query...]** collegamento per definire i dati da raccogliere tra gli elementi di questo elenco per la creazione del rapporto.

## Utilizzo di un cubo {#using-a-cube}

È possibile selezionare un cubo per la definizione della query.

![](assets/reporting_query_from_cube.png)

I cubi consentono di ampliare le capacità di esplorazione e analisi del database, semplificando la configurazione di report e tabelle per gli utenti finali: è sufficiente selezionare un cubo esistente completamente configurato e utilizzarne calcoli, misure e statistiche. For more on creating cubes, refer to [this section](../../reporting/using/about-cubes.md).

Fate clic sul **[!UICONTROL Edit query...]** collegamento e selezionate gli indicatori da visualizzare o utilizzare nel rapporto.

![](assets/reporting_query_from_cube_edit_query.png)

## Opzioni di filtro nelle query {#filtering-options-in-the-queries}

Per evitare di eseguire query sull&#39;intero database, i dati devono essere filtrati.

### Filtro semplificato {#simplified-filter}

Puoi selezionare l&#39; **[!UICONTROL Filter automatically with the context]** opzione per rendere il rapporto accessibile tramite un nodo specifico della struttura, ad esempio un elenco, un destinatario o una consegna.

L’ **[!UICONTROL Filter with the folder]** opzione consente di specificare una cartella e di tenerne conto solo del relativo contenuto. Questo consente di filtrare i dati del rapporto in modo da mostrare solo i dati di una delle cartelle della struttura, come illustrato di seguito:

![](assets/reporting_control_folder.png)

### Limitazione della quantità di dati raccolti {#limiting-the-amount-of-data-collected}

Configurare il numero di record da estrarre tramite la query utilizzando le opzioni di limitazione dei risultati:

* **[!UICONTROL Limit to first record]** per estrarre un risultato,
* **[!UICONTROL Size]** per estrarre un determinato numero di record.

