---
title: Metodi SOAP in JavaScript
seo-title: Metodi SOAP in JavaScript
description: Metodi SOAP in JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 8fd1aabc-e51a-433d-835f-6b5a717c7aeb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 815d3eb9-ac45-441f-9a5f-0cd505fcf88a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 12%

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

