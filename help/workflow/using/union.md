---
product: campaign
title: Unione
description: Ulteriori informazioni sull’attività del flusso di lavoro dell’Unione
feature: Workflows, Targeting Activity
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Unione{#union}



Un’unione raggruppa il risultato di diverse attività in entrata in un unico target. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono quindi essere completate affinché l&#39;unione possa essere eseguita.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione e sull’utilizzo dell’attività di unione, consulta [Combinazione di più obiettivi (Unione)](targeting-data.md#combining-several-targets--union-).

## Esempio di unione {#union-example}

Nell’esempio seguente, i risultati di due query sono stati combinati per aggiornare l’elenco. Le due query eseguono il targeting dei destinatari. I risultati si basano quindi sulla stessa tabella.

1. Inserisci un **[!UICONTROL Union]** Attività di tipo -type subito dopo le due query e prima di un&#39;attività di tipo update dell&#39;elenco, quindi aprirla.
1. È possibile immettere un&#39;etichetta.
1. Seleziona la **[!UICONTROL Keys only]** metodo di riconciliazione in quanto, in questo esempio, la popolazione risultante dalle query contiene dati coerenti.
1. Se hai aggiunto dati aggiuntivi per le query, puoi decidere di mantenere solo i dati condivisi.
1. Se desideri limitare la dimensione della popolazione finale, controlla **[!UICONTROL Limit size of generated population]** casella.

   Specifica questo numero finale immettendo il numero massimo di destinatari e selezionando la query la cui popolazione avrà la priorità.

1. Approva l’attività unione, quindi configura l’attività di aggiornamento elenco (consulta [Aggiornamento elenco](list-update.md)).
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

Questo insieme di tre valori identifica il target risultante dall&#39;unione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificativi target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.
