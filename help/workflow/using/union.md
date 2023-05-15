---
product: campaign
title: Unione
description: Ulteriori informazioni sull’attività del flusso di lavoro dell’Unione
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Unione{#union}



Un’unione raggruppa il risultato di diverse attività in entrata in un unico target. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono pertanto essere portate a termine affinché l&#39;unione sia eseguita.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione e l’utilizzo dell’attività di unione, consulta [Combinazione di più obiettivi (Unione)](targeting-data.md#combining-several-targets--union-).

## Esempio di unione {#union-example}

Nell’esempio seguente, i risultati di due query sono stati combinati per aggiornare l’elenco. Le due query hanno come target i destinatari. I risultati sono quindi basati sulla stessa tabella.

1. Inserisci un **[!UICONTROL Union]** -digita l’attività subito dopo le due query e prima di un’attività di tipo di aggiornamento dell’elenco, quindi aprila.
1. È possibile inserire un’etichetta.
1. Seleziona la **[!UICONTROL Keys only]** metodo di riconciliazione poiché, in questo esempio, la popolazione risultante dalle query contiene dati coerenti.
1. Se hai aggiunto dati aggiuntivi per le query, puoi decidere di conservare solo i dati condivisi.
1. Se desideri limitare la dimensione della popolazione finale, controlla la **[!UICONTROL Limit size of generated population]** scatola.

   Specifica questo numero finale immettendo il numero massimo di destinatari e selezionando la query la cui popolazione avrà priorità.

1. Approva l’attività di unione e configura l’attività di aggiornamento dell’elenco (vedi [Aggiornamento elenco](list-update.md)).
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

Questo insieme di tre valori identifica il target risultante dall&#39;unione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.
