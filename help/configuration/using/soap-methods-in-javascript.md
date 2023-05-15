---
product: campaign
title: Metodi SOAP in JavaScript
description: Metodi SOAP in JavaScript
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# Metodi SOAP in JavaScript{#soap-methods-in-javascript}

Questo è il JavaScript eseguito sul server Adobe Campaign.

## Metodi statici {#static-methods}

È possibile accedere ai metodi SOAP statici richiamando un metodo sull&#39;oggetto che rappresenta lo schema. Gli schemi sono proprietà degli oggetti &quot;namespace&quot;. Questi namespace sono variabili globali, pertanto, ad esempio, le variabili xtk o nms rappresentano i namespace corrispondenti

L&#39;esempio seguente richiama il metodo statico PostEvent dello schema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Metodi non statici {#non-static-methods}

Per utilizzare metodi SOAP non statici, è innanzitutto necessario recuperare un’entità utilizzando i metodi &quot;get&quot; o &quot;create&quot; negli schemi corrispondenti.

L&#39;esempio seguente richiama il metodo ExecuteQuery dello schema &quot;xtk:queryDef&quot;:

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

* Esegui una query sulla tabella dei destinatari con un’operazione &quot;get&quot;:

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

* Esegui una query sulla tabella dei destinatari con un’operazione &quot;select&quot;:

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
