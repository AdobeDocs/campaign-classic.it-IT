---
product: campaign
title: Unione
description: Ulteriori informazioni sull’attività del flusso di lavoro dell’Unione
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Unione{#union}

![](../../assets/common.svg)

Un’unione raggruppa il risultato di diverse attività in entrata in un unico target. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono pertanto essere portate a termine affinché l&#39;unione sia eseguita.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione e l’utilizzo dell’attività di unione, consulta [Combinazione di più destinazioni (Union)](targeting-data.md#combining-several-targets--union-).

## Esempio di unione {#union-example}

Nell’esempio seguente, i risultati di due query sono stati combinati per aggiornare l’elenco. Le due query hanno come target i destinatari. I risultati sono quindi basati sulla stessa tabella.

1. Inserisci un&#39;attività di tipo **[!UICONTROL Union]** subito dopo le due query e prima di un&#39;attività di tipo update dell&#39;elenco, quindi aprila.
1. È possibile inserire un’etichetta.
1. Seleziona il metodo di riconciliazione **[!UICONTROL Keys only]** poiché, in questo esempio, la popolazione risultante dalle query contiene dati coerenti.
1. Se hai aggiunto dati aggiuntivi per le query, puoi decidere di conservare solo i dati condivisi.
1. Se desideri limitare le dimensioni della popolazione finale, seleziona la casella **[!UICONTROL Limit size of generated population]** .

   Specifica questo numero finale immettendo il numero massimo di destinatari e selezionando la query la cui popolazione avrà priorità.

1. Approva l&#39;attività di unione e configura l&#39;attività di aggiornamento elenco (consulta [Aggiornamento elenco](list-update.md)).
1. Avviare il flusso di lavoro. Viene visualizzato il numero di risultati e viene creato o aggiornato l’elenco definito nell’attività di aggiornamento elenco. Questo elenco contiene l’insieme di destinatari per entrambe le query o, se applicabile, il numero definito nel passaggio precedente.

   ![](assets/union_example.png)

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall&#39;unione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione,  **[!UICONTROL schema]** è lo schema del gruppo (in genere nms:recipient) ed  **[!UICONTROL recCount]** è il numero di elementi della tabella.
