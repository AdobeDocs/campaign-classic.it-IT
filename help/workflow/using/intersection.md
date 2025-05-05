---
product: campaign
title: 'Intersezione '
description: 'Intersezione '
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 13%

---

# Intersezione {#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="Attività Intersezione"
>abstract="Un’attività di tipo Intersezione crea un target dall’intersezione dei target ricevuti. L’intersezione consente di estrarre solo la popolazione comune a tutti i risultati delle attività in entrata."
>additional-url="https://video.tv.adobe.com/v/341371?captions=ita" text="Guarda il video dimostrativo"




Un&#39;attività di tipo **Intersection** crea una destinazione dall&#39;intersezione delle destinazioni ricevute.

Un’intersezione ti consente di estrarre solo la popolazione comune a tutti i risultati delle attività in entrata. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono quindi essere completate prima che l’intersezione possa essere eseguita. Per configurare questa attività, devi immettere un’etichetta e le opzioni relative al risultato.

![](assets/s_user_segmentation_inter.png)

Per ulteriori informazioni sulla configurazione e l&#39;utilizzo dell&#39;attività di intersezione, fare riferimento a [Estrazione dei dati del giunto (intersezione)](targeting-data.md#extracting-joint-data--intersection-).

Selezionare l&#39;opzione **[!UICONTROL Generate complement]** se si desidera elaborare il gruppo rimanente. Il complemento conterrà l’unione dei risultati di tutte le attività in entrata senza l’intersezione. Verrà quindi aggiunta all’attività un’ulteriore transizione in uscita, come segue:

![](assets/s_user_segmentation_inter_compl.png)

## Esempio di intersezione {#intersection-example}

Nell’esempio seguente, lo scopo dell’intersezione è quello di calcolare i destinatari comuni a tre query semplici per creare un elenco.

1. Dopo tre semplici query, inserire un&#39;attività di tipo **[!UICONTROL Intersection]**.

   In questo esempio, le query riguardano rispettivamente uomini, destinatari che vivono a Parigi e destinatari di età compresa tra i 18 e i 30 anni.

1. Configura l’intersezione. A tale scopo, selezionare il metodo di riconciliazione **[!UICONTROL Keys only]** poiché le popolazioni risultanti dalle query contengono dati coerenti.
1. Se sono stati immessi dati aggiuntivi per le query, è possibile scegliere di mantenere solo quelli condivisi dai destinatari selezionando la casella pertinente.
1. Se si desidera utilizzare il resto dei dati (per quanto riguarda le query ma non la loro intersezione), selezionare la casella **[!UICONTROL Generate complement]**.
1. Aggiungi un’attività di aggiornamento elenco dopo il risultato dell’intersezione. È inoltre possibile aggiungere un aggiornamento elenco al complemento se si desidera utilizzare anche questo.
1. Esegui il flusso di lavoro. In questo caso, due destinatari si applicano a tutte e tre le query immesse contemporaneamente. Il complemento è costituito da cinque destinatari che si applicano solo a una o due delle tre query.

   Il risultato dell&#39;intersezione viene inviato al primo aggiornamento elenco. Se hai scelto di utilizzare il complemento, questo viene inviato anche al secondo aggiornamento dell’elenco.

   ![](assets/intersection_example.png)

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare una destinazione definita da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall&#39;intersezione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere **[!UICONTROL nms:recipient]**) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.
