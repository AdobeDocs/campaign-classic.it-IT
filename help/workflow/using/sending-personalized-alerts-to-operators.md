---
product: campaign
title: Inviare avvisi personalizzati agli operatori
description: Scopri come inviare avvisi personalizzati agli operatori
feature: Workflows
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# Inviare avvisi personalizzati agli operatori{#sending-personalized-alerts-to-operators}

![](../../assets/v7-only.svg)

In questo esempio, desideri inviare un avviso a un operatore che conterrà il nome dei profili che hanno aperto una newsletter ma non ha fatto clic sul collegamento in essa contenuto.

I campi nome e cognome del profilo sono collegati al **[!UICONTROL Recipients]** la dimensione di targeting, **[!UICONTROL Alert]** l’attività è collegata al **[!UICONTROL Operator]** dimensione di targeting. Di conseguenza, non è disponibile alcun campo tra le due dimensioni di targeting per eseguire una riconciliazione e recuperare i campi nome e cognome e visualizzarli nell’attività di avviso.

Il processo consiste nel creare un flusso di lavoro come segue:

1. Utilizza un **[!UICONTROL Query]** attività per eseguire il targeting dei dati.
1. Aggiungi un **[!UICONTROL JavaScript code]** nel flusso di lavoro per salvare la popolazione dalla query alla variabile di istanza.
1. Utilizza un **[!UICONTROL Test]** per controllare il conteggio della popolazione.
1. Utilizza un **[!UICONTROL Alert]** attività per inviare un avviso a un operatore, a seconda **[!UICONTROL Test]** risultato dell&#39;attività.

![](assets/uc_operator_1.png)

## Salvataggio della popolazione nella variabile di istanza {#saving-the-population-to-the-instance-variable}

Aggiungi il codice seguente nel **[!UICONTROL JavaScript code]** attività.

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

Assicurati che il codice JavaScript corrisponda alle informazioni del flusso di lavoro:

* La **[!UICONTROL queryDef schema]** Il tag deve corrispondere al nome della dimensione di targeting utilizzata nell’attività di query.
* La **[!UICONTROL node expr]** Il tag deve corrispondere al nome dei campi da recuperare.

![](assets/uc_operator_3.png)

Per recuperare queste informazioni, segui i passaggi seguenti:

1. Fai clic con il pulsante destro del mouse sulla transizione in uscita dal **[!UICONTROL Query]** attività , quindi seleziona **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Fare clic con il pulsante destro del mouse sull’elenco, quindi selezionare **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Nell’elenco vengono visualizzati la dimensione di targeting delle query e i nomi dei campi.

   ![](assets/uc_operator_6.png)

## Verifica del conteggio della popolazione {#testing-the-population-count}

Aggiungi il codice seguente nel **[!UICONTROL Test]** attività per verificare se la popolazione target contiene almeno 1 profilo.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Impostazione dell’avviso {#setting-up-the-alert}

Ora che la popolazione è stata aggiunta alla variabile di istanza con i campi desiderati, puoi aggiungere queste informazioni nella variabile **[!UICONTROL Alert]** attività.

A questo scopo, aggiungi nella **[!UICONTROL Source]** imposta il codice seguente:

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
>La **[!UICONTROL <%= item.target.recipient.@fieldName %>]** consente di aggiungere uno dei campi salvati nella variabile di istanza tramite il comando **[!UICONTROL JavaScript code]** attività.\
>Puoi aggiungere quanti campi desideri, purché siano stati inseriti nel codice JavaScript.

![](assets/uc_operator_8.png)
