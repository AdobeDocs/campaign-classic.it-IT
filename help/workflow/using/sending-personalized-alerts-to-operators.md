---
title: Invio di avvisi personalizzati agli operatori
description: Scopri come inviare avvisi personalizzati agli operatori
page-status-flag: never-activated
uuid: 10dd46b9-df28-4043-91f9-c9316a7c69d3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4d72db10-29bd-4b3c-adb3-bead02890271
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---


# Invio di avvisi personalizzati agli operatori{#sending-personalized-alerts-to-operators}

In questo esempio, desideriamo inviare un avviso a un operatore che conterrà il nome dei profili che hanno aperto una newsletter ma non hanno fatto clic sul collegamento che contiene.

I campi nome e cognome dei profili sono collegati alla dimensione di **[!UICONTROL Recipients]** targeting, mentre l&#39; **[!UICONTROL Alert]** attività è collegata alla dimensione di **[!UICONTROL Operator]** targeting. Di conseguenza, non è disponibile alcun campo tra le due dimensioni di targeting per eseguire una riconciliazione, recuperare i campi nome e cognome e visualizzarli nell&#39;attività di avviso.

Il processo consiste nel creare un flusso di lavoro come segue:

1. Utilizzate un&#39; **[!UICONTROL Query]** attività per eseguire il targeting dei dati.
1. Aggiungete un&#39; **[!UICONTROL JavaScript code]** attività nel flusso di lavoro per salvare la popolazione dalla query alla variabile di istanza.
1. Utilizzate un&#39; **[!UICONTROL Test]** attività per controllare il numero di popolazione.
1. Utilizzate un&#39; **[!UICONTROL Alert]** attività per inviare un avviso a un operatore, in base al risultato dell&#39; **[!UICONTROL Test]** attività.

![](assets/uc_operator_1.png)

## Salvataggio della popolazione nella variabile di istanza {#saving-the-population-to-the-instance-variable}

Aggiungete il codice seguente nell&#39; **[!UICONTROL JavaScript code]** attività.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Accertatevi che il codice JavaScript corrisponda alle informazioni del flusso di lavoro:

* Il **[!UICONTROL queryDef schema]** tag deve corrispondere al nome della dimensione di targeting utilizzata nell&#39;attività di query.
* Il **[!UICONTROL node expr]** tag deve corrispondere al nome dei campi da recuperare.

![](assets/uc_operator_3.png)

Per recuperare queste informazioni, effettuate le seguenti operazioni:

1. Fare clic con il pulsante destro del mouse sulla transizione in uscita dall&#39; **[!UICONTROL Query]** attività, quindi selezionare **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Fare clic con il pulsante destro del mouse sull&#39;elenco, quindi selezionare **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Nell&#39;elenco vengono visualizzati la dimensione di targeting delle query e i nomi dei campi.

   ![](assets/uc_operator_6.png)

## Verifica del numero di persone {#testing-the-population-count}

Aggiungete il codice seguente nell&#39; **[!UICONTROL Test]** attività per verificare se la popolazione di destinazione contiene almeno 1 profilo.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Impostazione dell’avviso {#setting-up-the-alert}

Ora che la popolazione è stata aggiunta alla variabile di istanza con i campi desiderati, potete aggiungere queste informazioni all&#39; **[!UICONTROL Alert]** attività.

A tal fine, aggiungere nella **[!UICONTROL Source]** scheda il codice seguente:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>Il **[!UICONTROL <%= item.target.recipient.@fieldName %>]** comando consente di aggiungere uno dei campi salvati nella variabile di istanza attraverso l&#39; **[!UICONTROL JavaScript code]** attività.\
>È possibile aggiungere tutti i campi desiderati, purché siano stati inseriti nel codice JavaScript.

![](assets/uc_operator_8.png)

