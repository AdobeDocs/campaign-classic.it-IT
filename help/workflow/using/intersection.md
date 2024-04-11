---
product: campaign
title: Intersezione
description: Intersezione
feature: Workflows, Targeting Activity
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 12%

---

# Intersezione {#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="Attività Intersezione"
>abstract="Un’attività di tipo Intersezione crea un target dall’intersezione dei target ricevuti. L’intersezione consente di estrarre solo la popolazione comune a tutti i risultati delle attività in entrata."
>additional-url="https://video.tv.adobe.com/v/329373?captions=ita" text="Guarda il video dimostrativo"




Un **Intersezione** L&#39;attività -type crea un oggetto dall&#39;intersezione degli oggetti ricevuti.

Un’intersezione ti consente di estrarre solo la popolazione comune a tutti i risultati delle attività in entrata. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono quindi essere completate prima che l’intersezione possa essere eseguita. Per configurare questa attività, devi immettere un’etichetta e le opzioni relative al risultato.

![](assets/s_user_segmentation_inter.png)

Per ulteriori informazioni sulla configurazione e sull’utilizzo dell’attività di intersezione, consulta [Estrazione dei dati articolari (intersezione)](targeting-data.md#extracting-joint-data--intersection-).

Controlla la **[!UICONTROL Generate complement]** se desideri elaborare la popolazione rimanente. Il complemento conterrà l’unione dei risultati di tutte le attività in entrata senza l’intersezione. Verrà quindi aggiunta all’attività un’ulteriore transizione in uscita, come segue:

![](assets/s_user_segmentation_inter_compl.png)

## Esempio di intersezione {#intersection-example}

Nell’esempio seguente, lo scopo dell’intersezione è quello di calcolare i destinatari comuni a tre query semplici per creare un elenco.

1. Dopo tre query semplici, inserisci un **[!UICONTROL Intersection]** attività di tipo.

   In questo esempio, le query riguardano rispettivamente uomini, destinatari che vivono a Parigi e destinatari di età compresa tra i 18 e i 30 anni.

1. Configura l’intersezione. A questo scopo, seleziona la **[!UICONTROL Keys only]** metodo di riconciliazione, poiché le popolazioni risultanti dalle query contengono dati coerenti.
1. Se sono stati immessi dati aggiuntivi per le query, è possibile scegliere di mantenere solo quelli condivisi dai destinatari selezionando la casella pertinente.
1. Se desideri utilizzare il resto dei dati (per quanto riguarda le query, ma non la loro intersezione), controlla **[!UICONTROL Generate complement]** casella.
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

Questo insieme di tre valori identifica il target risultante dall&#39;intersezione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificativi target, **[!UICONTROL schema]** è lo schema della popolazione (in genere **[!UICONTROL nms:recipient]**) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.
