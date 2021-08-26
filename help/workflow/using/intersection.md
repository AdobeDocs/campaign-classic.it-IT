---
product: campaign
title: Intersezione
description: Intersezione
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Intersezione{#intersection}

![](../../assets/common.svg)

Un’attività di tipo **Intersection** crea un target dall’intersezione delle destinazioni ricevute.

Un’intersezione consente di estrarre solo la popolazione comune a tutti i risultati delle attività in entrata. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono pertanto essere completate prima che sia possibile eseguire l’intersezione. Per configurare questa attività, devi immettere un’etichetta per essa e le opzioni relative al risultato.

![](assets/s_user_segmentation_inter.png)

Per ulteriori informazioni sulla configurazione e l&#39;utilizzo dell&#39;attività di intersezione, consulta [Estrazione di dati di giunzione (Intersezione)](targeting-data.md#extracting-joint-data--intersection-).

Se desideri elaborare la popolazione rimanente, seleziona l’opzione **[!UICONTROL Generate complement]** . Il complemento conterrà l&#39;unione dei risultati di tutte le attività in entrata meno l&#39;intersezione. All’attività verrà quindi aggiunta una transizione in uscita aggiuntiva, come segue:

![](assets/s_user_segmentation_inter_compl.png)

## Esempio di intersezione {#intersection-example}

Nell’esempio seguente, lo scopo dell’intersezione è quello di calcolare i destinatari comuni a tre semplici query per creare un elenco.

1. Dopo tre semplici query, inserisci un&#39;attività di tipo **[!UICONTROL Intersection]**.

   In questo esempio; le query riguardano rispettivamente gli uomini, i beneficiari che vivono a Parigi e i beneficiari di età compresa tra i 18 e i 30 anni.

1. Configura l&#39;intersezione. A questo scopo, seleziona il metodo di riconciliazione **[!UICONTROL Keys only]** in quanto le popolazioni risultanti dalle query contengono dati coerenti.
1. Se hai inserito dati aggiuntivi per le query, puoi scegliere di mantenere solo quelli condivisi dai destinatari selezionando la casella corrispondente.
1. Se desideri utilizzare il resto dei dati (per quanto riguarda le query ma non la loro intersezione), seleziona la casella **[!UICONTROL Generate complement]**.
1. Aggiungi un’attività di aggiornamento elenco dopo il risultato dell’intersezione. È inoltre possibile aggiungere un aggiornamento dell’elenco al complemento, se lo si desidera.
1. Esegui il flusso di lavoro. In questo caso, due destinatari si applicano a tutte e tre le query inserite contemporaneamente. Il complemento è composto da cinque destinatari che si applicano solo a una o due delle tre query.

   Il risultato dell’intersezione viene inviato al primo aggiornamento dell’elenco. Se hai scelto di utilizzare il complemento, questo viene inviato anche al secondo aggiornamento dell’elenco.

   ![](assets/intersection_example.png)

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall&#39;intersezione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione,  **[!UICONTROL schema]** è lo schema del gruppo (in genere  **[!UICONTROL nms:recipient]**) ed  **[!UICONTROL recCount]** è il numero di elementi nella tabella.
