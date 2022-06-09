---
product: campaign
title: Intersezione
description: Intersezione
feature: Workflows, Targeting Activity
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: 389e5a87ea195024707c3c58e63899ad7949f025
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 1%

---

# Intersezione{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="Attività di intersezione"
>abstract="Un’attività di tipo Intersezione crea un target dall’intersezione delle destinazioni ricevute. Un’intersezione consente di estrarre solo la popolazione comune a tutti i risultati delle attività in entrata."
>additional-url="https://video.tv.adobe.com/v/329373" text="Guarda il video dimostrativo"


![](../../assets/common.svg)

Un **Intersection** L’attività -type crea un target dall’intersezione dei target ricevuti.

Un’intersezione consente di estrarre solo la popolazione comune a tutti i risultati delle attività in entrata. Il target viene creato con tutti i risultati ricevuti: tutte le attività precedenti devono pertanto essere completate prima che sia possibile eseguire l’intersezione. Per configurare questa attività, devi immettere un’etichetta per essa e le opzioni relative al risultato.

![](assets/s_user_segmentation_inter.png)

Per ulteriori informazioni sulla configurazione e l’utilizzo dell’attività di intersezione, consulta [Estrazione di dati comuni (intersezione)](targeting-data.md#extracting-joint-data--intersection-).

Controlla la **[!UICONTROL Generate complement]** se desideri elaborare la popolazione rimanente. Il complemento conterrà l&#39;unione dei risultati di tutte le attività in entrata meno l&#39;intersezione. All’attività verrà quindi aggiunta una transizione in uscita aggiuntiva, come segue:

![](assets/s_user_segmentation_inter_compl.png)

## Esempio di intersezione {#intersection-example}

Nell’esempio seguente, lo scopo dell’intersezione è quello di calcolare i destinatari comuni a tre semplici query per creare un elenco.

1. Dopo tre semplici query, inserisci un **[!UICONTROL Intersection]** attività di tipo -type.

   In questo esempio; le query riguardano rispettivamente gli uomini, i beneficiari che vivono a Parigi e i beneficiari di età compresa tra i 18 e i 30 anni.

1. Configura l&#39;intersezione. A questo scopo, seleziona la **[!UICONTROL Keys only]** metodo di riconciliazione in quanto le popolazioni risultanti dalle query contengono dati coerenti.
1. Se hai inserito dati aggiuntivi per le query, puoi scegliere di mantenere solo quelli condivisi dai destinatari selezionando la casella corrispondente.
1. Se desideri utilizzare il resto dei dati (per quanto riguarda le query ma non la loro intersezione), controlla il **[!UICONTROL Generate complement]** scatola.
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

Questo insieme di tre valori identifica il target risultante dall&#39;intersezione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori target, **[!UICONTROL schema]** è lo schema del gruppo (in genere **[!UICONTROL nms:recipient]**) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.
