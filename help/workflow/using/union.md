---
product: campaign
title: Unione
description: Ulteriori informazioni sull’attività del flusso di lavoro dell’Unione
feature: Workflows, Targeting Activity
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Unione{#union}



Un’unione raggruppa il risultato di diverse attività in entrata in un unico target. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono quindi essere completate affinché l&#39;unione possa essere eseguita.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione e sull&#39;utilizzo dell&#39;attività di unione, fare riferimento a [Combinazione di più destinazioni (Unione)](targeting-data.md#combining-several-targets--union-).

## Esempio di unione {#union-example}

Nell’esempio seguente, i risultati di due query sono stati combinati per aggiornare l’elenco. Le due query eseguono il targeting dei destinatari. I risultati si basano quindi sulla stessa tabella.

1. Inserire un&#39;attività di tipo **[!UICONTROL Union]** subito dopo le due query e prima di un&#39;attività di tipo aggiornamento dell&#39;elenco, quindi aprirla.
1. È possibile immettere un&#39;etichetta.
1. Selezionare il metodo di riconciliazione **[!UICONTROL Keys only]** poiché, in questo esempio, il gruppo risultante dalle query contiene dati coerenti.
1. Se hai aggiunto dati aggiuntivi per le query, puoi decidere di mantenere solo i dati condivisi.
1. Se si desidera limitare la dimensione della popolazione finale, selezionare la casella **[!UICONTROL Limit size of generated population]**.

   Specifica questo numero finale immettendo il numero massimo di destinatari e selezionando la query la cui popolazione avrà la priorità.

1. Approva l&#39;attività di unione, quindi configura l&#39;attività di aggiornamento elenco (vedi [Aggiornamento elenco](list-update.md)).
1. Avvia il flusso di lavoro. Viene visualizzato il numero di risultati e viene creato o aggiornato l’elenco definito nell’attività di aggiornamento elenco. Questo elenco contiene il set di destinatari per entrambe le query o, se applicabile, il numero definito al passaggio precedente.

   ![](assets/union_example.png)

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare una destinazione definita da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall&#39;unione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.
