---
solution: Campaign Classic
product: campaign
title: Metodi SOAP in JavaScript
description: Metodi SOAP in JavaScript
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---


# Metodi SOAP in JavaScript{#soap-methods-in-javascript}

Questo è il JavaScript eseguito sul server Adobe Campaign .

## Metodi statici {#static-methods}

È possibile accedere ai metodi SOAP statici richiamando un metodo sull&#39;oggetto che rappresenta lo schema. Gli schemi sono proprietà degli oggetti &#39;namespace&#39;. Questi spazi dei nomi sono variabili globali, pertanto, ad esempio, le variabili xtk o nms rappresentano gli spazi dei nomi corrispondenti

L’esempio seguente richiama il metodo PostEvent statico dello schema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Metodi non statici {#non-static-methods}

Per utilizzare metodi SOAP non statici, è necessario innanzitutto recuperare un&#39;entità utilizzando i metodi &quot;get&quot; o &quot;create&quot; negli schemi corrispondenti.

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

* Query sulla tabella dei destinatari con un&#39;operazione &quot;get&quot;:

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

* Query sulla tabella dei destinatari con un&#39;operazione &quot;select&quot;:

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

* Scrittura dei dati nella tabella del destinatario:

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```

