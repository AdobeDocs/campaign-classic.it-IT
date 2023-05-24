---
product: campaign
title: Raccogliere dati da analizzare
description: Raccogliere dati da analizzare
badge: label="v7" type="Informative" tooltip="Si applica solo a Campaign Classic v7"
feature: Reporting
exl-id: cf621374-88f9-4def-8bea-87e0ea69ecd3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 3%

---

# Raccogliere dati da analizzare{#collecting-data-to-analyze}



I dati da utilizzare per la creazione del rapporto possono essere selezionati direttamente nella pagina del rapporto (per ulteriori informazioni, consulta [Utilizzo del contesto](../../reporting/using/using-the-context.md)) o raccolti tramite una o più query.

Questa attività offre tre metodi diversi:

1. Creazione di una query utilizzando i dati nel database.
1. Elaborazione dei dati contenuti in un elenco.
1. Utilizzo dei dati contenuti in un cubo esistente.

La scelta del metodo dipende dal tipo di calcolo, dal volume dei dati e dalla loro durata, ecc. Tutti questi parametri devono essere esaminati attentamente per evitare un sovraccarico del database di Adobe Campaign e per ottimizzare la generazione e la manipolazione dei rapporti creati. Per ulteriori informazioni, consulta [questa pagina](../../reporting/using/best-practices.md#optimizing-report-creation).

In tutti i casi, i dati vengono raccolti tramite un **[!UICONTROL Query]** attività di tipo.

![](assets/reporting_query_edit.png)

Questa modalità di selezione dei dati è pertinente quando i dati nel rapporto devono essere raccolti o generati utilizzando i dati presenti nel database. In alcuni casi, puoi anche selezionare i dati direttamente dagli elementi utilizzati nel rapporto. Ad esempio, quando si inserisce un grafico, è possibile selezionare direttamente i dati di origine. Per ulteriori informazioni, consulta [Utilizzo del contesto](../../reporting/using/using-the-context.md).

## Utilizzare i dati di uno schema {#using-the-data-from-a-schema}

Per utilizzare i dati collegati a uno schema di database, seleziona l’opzione appropriata nell’editor delle query e configura la query da applicare.

L’esempio seguente ti consente di raccogliere il numero di destinatari per ogni paese, tra i profili nel database. Possono quindi essere visualizzati in un rapporto sotto forma di tabella.

![](assets/reporting_query_from_schema.png)

## Utilizza un elenco importato {#using-an-imported-list}

Per creare un rapporto, puoi utilizzare i dati di un elenco di dati importati.

A questo scopo, seleziona la **[!UICONTROL Use an imported list]** nella casella query e selezionare l&#39;elenco corrispondente.

![](assets/reporting_query_from_list.png)

Fai clic su **[!UICONTROL Edit query...]** per definire i dati da raccogliere tra gli elementi di questo elenco per la creazione del rapporto.

## Usa un cubo {#using-a-cube}

È possibile selezionare un cubo per definire la query.

![](assets/reporting_query_from_cube.png)

I cubi consentono di estendere le capacità di esplorazione e analisi del database e di semplificare la configurazione di report e tabelle per gli utenti finali: è sufficiente selezionare un cubo esistente completamente configurato e utilizzarne calcoli, misure e statistiche. Per ulteriori informazioni sulla creazione di cubi, consulta [questa sezione](../../reporting/using/ac-cubes.md).

Fai clic su **[!UICONTROL Edit query...]** e selezionare gli indicatori che si desidera visualizzare o utilizzare nel rapporto.

![](assets/reporting_query_from_cube_edit_query.png)

## Opzioni di filtro nelle query {#filtering-options-in-the-queries}

Per evitare di eseguire query sull’intero database, i dati devono essere filtrati.

### Filtro semplificato {#simplified-filter}

È possibile selezionare **[!UICONTROL Filter automatically with the context]** per rendere il rapporto accessibile tramite un nodo specifico della struttura, ad esempio un elenco, un destinatario o una consegna.

Il **[!UICONTROL Filter with the folder]** consente di specificare una cartella e di tenerne conto solo il contenuto. Questo consente di filtrare i dati del rapporto in modo da visualizzare solo i dati di una delle cartelle della struttura, come illustrato di seguito:

![](assets/reporting_control_folder.png)

### Limita la quantità di dati raccolti {#limiting-the-amount-of-data-collected}

Configura il numero di record da estrarre tramite la query utilizzando le opzioni di limitazione dei risultati:

* **[!UICONTROL Limit to first record]** per estrarre un risultato,
* **[!UICONTROL Size]** per estrarre un numero di record impostato.
