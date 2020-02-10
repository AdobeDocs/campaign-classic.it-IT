---
title: Flusso di lavoro secondario
seo-title: Flusso di lavoro secondario
description: Flusso di lavoro secondario
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Flusso di lavoro secondario{#sub-workflow}

L&#39; **[!UICONTROL Sub-workflow]** attività consente di attivare l&#39;esecuzione di un altro flusso di lavoro e recuperare il risultato. Questa attività consente di utilizzare flussi di lavoro complessi utilizzando un&#39;interfaccia semplificata.

Puoi chiamare più flussi di lavoro secondari in un unico flusso di lavoro. I flussi di lavoro secondari vengono eseguiti in modo sincrono.

>[!NOTE]
>
>Affinché il flusso di lavoro secondario possa essere eseguito correttamente, è necessario avere un solo salto di tipo &quot;arrivo&quot; con il numero più basso e un solo salto di tipo &quot;inizio&quot; con il numero più alto. Ad esempio, se il tipo &quot;start&quot; consente di saltare con priorità pari a 1, 2 e 3, è consigliabile impostare un solo tipo &quot;start&quot; con priorità pari a 3.

1. Crea un flusso di lavoro da utilizzare come flusso di lavoro secondario in un altro flusso di lavoro.
1. Inserite un&#39; **[!UICONTROL Jump (end point)]** attività con priorità pari a 1 all&#39;inizio del flusso di lavoro. Se hai più salti di tipo &quot;arrivo&quot;, Adobe Campaign utilizzerà il salto &quot;arrivo&quot; con il numero più basso.

   Inserite un&#39; **[!UICONTROL Jump (start point)]** attività con priorità pari a 2 alla fine del flusso di lavoro. Se hai più salti di tipo &quot;start&quot;, Adobe Campaign utilizzerà il salto &quot;start&quot; con il numero più alto.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Se l&#39;attività del flusso di lavoro secondario fa riferimento a un flusso di lavoro con diverse **[!UICONTROL Jump]** attività, il flusso di lavoro secondario viene eseguito tra il salto del tipo di &quot;arrivo&quot; con il numero più basso e il salto del tipo &quot;inizio&quot; con il numero più alto.

1. Completa e salva questo &quot;flusso di lavoro secondario&quot;.
1. Create un flusso di lavoro &quot;principale&quot;.
1. Inserite un&#39; **[!UICONTROL Sub-workflow]** attività e apritela.
1. Dall’elenco a **[!UICONTROL Workflow template]** discesa, selezionate il flusso di lavoro da utilizzare.

   ![](assets/subworkflow_selection.png)

1. È inoltre possibile aggiungere uno script di configurazione per modificare il flusso di lavoro di riferimento.
1. Clic **[!UICONTROL Ok]**. Crea automaticamente una transizione in uscita con l&#39;etichetta dell&#39; **[!UICONTROL Jump (start point)]** attività dal flusso di lavoro selezionato.

   ![](assets/subworkflow_outbound.png)

1. Eseguire il flusso di lavoro.

Una volta eseguito, il flusso di lavoro chiamato come flusso di lavoro secondario è ancora nello **[!UICONTROL Being edited]** stato, ovvero:

* Non potete fare clic con il pulsante destro del mouse sulle transizioni per visualizzare la destinazione.
* Impossibile visualizzare il numero di popolazioni intermedie.
* I file di registro sono aggregati nel flusso di lavoro &quot;principale&quot; e sono etichettati solo come &quot;subworkflow&quot;.

Questo flusso di lavoro è solo un modello. Un nuovo flusso di lavoro secondario basato su questo modello viene creato quando chiamato dal flusso di lavoro &quot;principale&quot;.

## Parametri di input (facoltativo) {#input-parameters--optional-}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica la popolazione oggetto della query. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:destinatario) ed **[!UICONTROL recCount]** è il numero di elementi nella tabella.

* targetSchema

Questo valore è lo schema della tabella di lavoro. Questo parametro è valido per tutte le transizioni con **[!UICONTROL tableName]** e **[!UICONTROL schema]**.
