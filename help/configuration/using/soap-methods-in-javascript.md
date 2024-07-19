---
product: campaign
title: Metodi SOAP in JavaScript
feature: Configuration, Instance Settings
description: Metodi SOAP in JavaScript
role: Data Engineer, Developer
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# Metodi SOAP in JavaScript{#soap-methods-in-javascript}

Si tratta del JavaScript eseguito sul server Adobe Campaign.

## Metodi statici {#static-methods}

I metodi SOAP statici sono accessibili richiamando un metodo sull’oggetto che rappresenta lo schema. Gli schemi sono proprietà degli oggetti &#39;namespace&#39;. Questi spazi dei nomi sono variabili globali, pertanto, ad esempio, le variabili xtk o nms rappresentano gli spazi dei nomi corrispondenti

Nell&#39;esempio seguente viene richiamato il metodo PostEvent statico dello schema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Metodi non statici {#non-static-methods}

Per utilizzare metodi SOAP non statici, è necessario innanzitutto recuperare un’entità utilizzando i metodi &quot;get&quot; o &quot;create&quot; negli schemi corrispondenti.

Nell&#39;esempio seguente viene richiamato il metodo ExecuteQuery dello schema &quot;xtk:queryDef&quot;:

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## Esempi {#examples}

* Eseguire una query sulla tabella dei destinatari con un’operazione &quot;get&quot;:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* Eseguire una query sulla tabella dei destinatari con un&#39;operazione di selezione:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* Scrittura dei dati nella tabella dei destinatari:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
