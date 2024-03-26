---
product: campaign
title: Inviare avvisi personalizzati agli operatori
description: Scopri come inviare avvisi personalizzati agli operatori
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 4%

---

# Inviare avvisi personalizzati agli operatori{#sending-personalized-alerts-to-operators}



In questo esempio, vogliamo inviare un avviso a un operatore che conterrà il nome dei profili che hanno aperto una newsletter ma non hanno fatto clic sul collegamento in essa contenuto.

I campi Nome e Cognome dei profili sono collegati al **[!UICONTROL Recipients]** la dimensione di targeting, mentre **[!UICONTROL Alert]** l&#39;attività è collegata al **[!UICONTROL Operator]** dimensione di targeting. Di conseguenza, non è disponibile alcun campo tra le due dimensioni di targeting per eseguire una riconciliazione, recuperare i campi nome e cognome e visualizzarli nell’attività Avviso.

Il processo consiste nel creare un flusso di lavoro come indicato di seguito:

1. Utilizza un **[!UICONTROL Query]** attività per eseguire il targeting dei dati.
1. Aggiungi un **[!UICONTROL JavaScript code]** per salvare il gruppo dalla query alla variabile dell’istanza.
1. Utilizza un **[!UICONTROL Test]** attività per controllare il conteggio della popolazione.
1. Utilizza un **[!UICONTROL Alert]** per inviare un avviso a un operatore, a seconda della **[!UICONTROL Test]** risultato dell’attività.

![](assets/uc_operator_1.png)

## Salvataggio del gruppo nella variabile di istanza {#saving-the-population-to-the-instance-variable}

Aggiungi il codice seguente alla **[!UICONTROL JavaScript code]** attività.

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

* Il **[!UICONTROL queryDef schema]** il tag deve corrispondere al nome della dimensione di targeting utilizzata nell’attività di query.
* Il **[!UICONTROL node expr]** deve corrispondere al nome dei campi che desideri recuperare.

![](assets/uc_operator_3.png)

Per recuperare queste informazioni, effettua le seguenti operazioni:

1. Fare clic con il pulsante destro del mouse sulla transizione in uscita dalla **[!UICONTROL Query]** attività, quindi seleziona **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Fai clic con il pulsante destro del mouse sull’elenco, quindi seleziona **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Nell’elenco vengono visualizzati la dimensione di targeting della query e i nomi dei campi.

   ![](assets/uc_operator_6.png)

## Verifica del conteggio della popolazione {#testing-the-population-count}

Aggiungi il codice seguente alla **[!UICONTROL Test]** attività per verificare se la popolazione target contiene almeno 1 profilo.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Configurazione dell’avviso {#setting-up-the-alert}

Ora che il gruppo è stato aggiunto alla variabile dell’istanza con i campi desiderati, puoi aggiungere queste informazioni nel **[!UICONTROL Alert]** attività.

Per eseguire questa operazione, aggiungi in **[!UICONTROL Source]** seleziona il codice seguente:

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
>Il **[!UICONTROL <%= item.target.recipient.@fieldName %>]** consente di aggiungere uno dei campi salvati nella variabile di istanza tramite il comando **[!UICONTROL JavaScript code]** attività.\
>Puoi aggiungere tutti i campi desiderati, purché siano stati inseriti nel codice JavaScript.

![](assets/uc_operator_8.png)
