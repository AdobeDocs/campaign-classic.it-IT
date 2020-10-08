---
title: Union
seo-title: Union
description: Union
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 2%

---


# Union{#union}

Un&#39;unione raggruppa il risultato di diverse attività in entrata in un unico obiettivo. La destinazione viene creata con tutti i risultati ricevuti: tutte le attività precedenti devono pertanto essere portate a termine affinché l&#39;Unione possa essere esercitata.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione e l&#39;utilizzo dell&#39;attività dell&#39;Unione, fare riferimento a [Combinare più obiettivi (Unione)](../../workflow/using/targeting-data.md#combining-several-targets--union-).

## Esempio di unione {#union-example}

Nell&#39;esempio seguente, i risultati di due query sono stati combinati per aggiornare l&#39;elenco. Le due query vengono indirizzate ai destinatari. I risultati si basano pertanto sulla stessa tabella.

1. Inserire un&#39;attività **[!UICONTROL Union]** -type subito dopo le due query e prima di un&#39;attività di tipo update dell&#39;elenco, quindi aprirla.
1. È possibile immettere un&#39;etichetta.
1. Selezionare il metodo di **[!UICONTROL Keys only]** riconciliazione perché, in questo esempio, la popolazione risultante dalle query contiene dati coerenti.
1. Se avete aggiunto dati aggiuntivi per le query, potete decidere di conservare solo i dati condivisi.
1. If you wish to limit the size of the final population, check the **[!UICONTROL Limit size of generated population]** box.

   Specificate questo numero finale immettendo il numero massimo di destinatari e selezionando la query di cui la popolazione avrà priorità.

1. Approvare l&#39;attività dell&#39;unione, quindi configurare l&#39;attività di aggiornamento dell&#39;elenco (vedere Aggiornamento [](../../workflow/using/list-update.md)elenco).
1. Avvia il flusso di lavoro. Il numero di risultati viene visualizzato e l&#39;elenco definito nell&#39;attività di aggiornamento dell&#39;elenco viene creato o aggiornato. Questo elenco contiene l&#39;insieme di destinatari per entrambe le query o, se del caso, il numero definito nel passaggio precedente.

   ![](assets/union_example.png)

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall&#39;unione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:destinatario) ed **[!UICONTROL recCount]** è il numero di elementi nella tabella.
