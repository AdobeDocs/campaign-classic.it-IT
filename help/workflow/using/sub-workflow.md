---
product: campaign
title: Flusso di lavoro secondario
description: Ulteriori informazioni sull’attività del flusso di lavoro secondario
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Flusso di lavoro secondario{#sub-workflow}



Il **[!UICONTROL Sub-workflow]** L’attività ti consente di attivare l’esecuzione di un altro flusso di lavoro e di recuperare il risultato. Questa attività ti consente di utilizzare flussi di lavoro complessi utilizzando un’interfaccia semplificata.

È possibile chiamare più flussi di lavoro secondari in un unico flusso di lavoro. I workflow secondari vengono eseguiti in modo sincrono.

Nell’esempio seguente, un flusso di lavoro primario sta chiamando un flusso di lavoro secondario utilizzando i ponticelli. Per ulteriori informazioni sugli oggetti grafici di tipo Salto, consultate [questa sezione](jump-start-point-and-end-point.md).

1. Crea un flusso di lavoro da utilizzare come flusso di lavoro secondario in un altro flusso di lavoro.
1. Inserisci un **[!UICONTROL Jump (end point)]** attività con priorità 1 all’inizio del flusso di lavoro. Se disponi di più salti di tipo &quot;end point&quot;, Adobe Campaign utilizzerà il salto &quot;end point&quot; con il numero più basso.
1. Inserisci un **[!UICONTROL Jump (start point)]** con priorità 2 alla fine del flusso di lavoro. Se disponi di più salti di tipo &quot;punto iniziale&quot;, Adobe Campaign utilizzerà il salto &quot;punto iniziale&quot; con il numero più alto.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Se l’attività del flusso di lavoro secondario fa riferimento a un flusso di lavoro con più **[!UICONTROL Jump]** attività, il flusso di lavoro secondario viene eseguito tra il salto di tipo &quot;punto finale&quot; con il numero più basso e il salto di tipo &quot;punto iniziale&quot; con il numero più alto.
   >
   >Affinché il flusso di lavoro secondario possa essere eseguito correttamente, è necessario disporre di un solo salto di tipo &quot;punto finale&quot; con il numero più basso e di un solo salto di tipo &quot;punto iniziale&quot; con il numero più alto.

1. Completa e salva questo &quot;flusso di lavoro secondario&quot;.
1. Crea un flusso di lavoro principale.
1. Inserisci un **[!UICONTROL Sub-workflow]** e aprirla.
1. Seleziona il flusso di lavoro da utilizzare da **[!UICONTROL Workflow template]** elenco a discesa.

   ![](assets/subworkflow_selection.png)

1. Puoi anche aggiungere uno script di configurazione per modificare il flusso di lavoro di riferimento.
1. Fai clic su **[!UICONTROL Ok]**. Creerà automaticamente una transizione in uscita con l’etichetta del **[!UICONTROL Jump (start point)]** attività dal flusso di lavoro selezionato.

   ![](assets/subworkflow_outbound.png)

1. Esegui il flusso di lavoro.

Una volta eseguito, il flusso di lavoro chiamato come flusso di lavoro secondario rimane in **[!UICONTROL Being edited]** stato, ossia:

* Non è possibile fare clic con il pulsante destro del mouse sulle transizioni per visualizzare la destinazione.
* Impossibile visualizzare il conteggio delle popolazioni intermedie.
* I registri del flusso di lavoro secondario vengono visualizzati nel flusso di lavoro principale.

  ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>Se si verifica un errore nel flusso di lavoro secondario, il flusso di lavoro principale viene sospeso e viene creata una copia del flusso di lavoro secondario.

## Parametri di input (facoltativi) {#input-parameters--optional-}

* tableName
* schema

Ogni evento in entrata deve specificare una destinazione definita da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo set di tre valori identifica la popolazione target della query. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificativi target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

* targetSchema: questo valore è lo schema della tabella di lavoro. Questo parametro è valido per tutte le transizioni con **[!UICONTROL tableName]** e **[!UICONTROL schema]**.
