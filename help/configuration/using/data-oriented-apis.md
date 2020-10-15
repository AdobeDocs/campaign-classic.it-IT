---
title: API orientate ai dati
seo-title: API orientate ai dati
description: API orientate ai dati
seo-description: null
page-status-flag: never-activated
uuid: f81356b3-8eef-4b65-9510-47c9d4b4e871
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: fba46d42-0253-425b-bbc2-6702d4140e05
translation-type: tm+mt
source-git-commit: 63b208e5607bdcddaef03292d229847c4b7366f8
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 0%

---


# API orientate ai dati{#data-oriented-apis}

Le API orientate ai dati consentono di gestire l&#39;intero modello dati.

## Panoramica del modello dati {#overview-of-the-datamodel}

 Adobe Campaign non offre un&#39;API di lettura dedicata per entità (nessuna funzione getRecipient o getDelivery, ecc.). Utilizzare i metodi di lettura e modifica dei dati QUERY e WRITER per accedere ai dati del modello.

 Adobe Campaign consente di gestire le raccolte: le query consentono di recuperare una serie di informazioni raccolte in tutta la base. A differenza dell&#39;accesso in modalità SQL,  API Adobe Campaign restituiscono una struttura XML invece delle colonne di dati.  Adobe Campaign crea quindi documenti compositi con tutti i dati raccolti.

Questa modalità operativa non offre la mappatura uno-a-uno tra gli attributi e gli elementi dei documenti XML e le colonne delle tabelle nel database.

I documenti XML sono memorizzati nei campi del tipo MEMO del database.

## Descrizione del modello {#description-of-the-model}

È necessario avere familiarità con il  modello dati Adobe Campaign per poter indirizzare i campi del database negli script.

Per una presentazione del modello dati, fare riferimento alla descrizione [del modello dati](../../configuration/using/data-model-description.md)Adobe Campaign.

Per generare la struttura, fare riferimento a questo articolo: [Come generare un modello dati o un dizionario](https://helpx.adobe.com/campaign/kb/generate-data-model.html)dati.

## Query e scrittura {#query-and-writer}

Lo schema di introduzione seguente descrive gli scambi di basso livello per la lettura (ExecuteQuery) e la scrittura (Writer) tra il database e il cliente (pagine Web o  console client Adobe Campaign).

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

Per le colonne e le condizioni, potete utilizzare Query.

Questo consente di isolare l&#39;SQL sottostante. La lingua della query non dipende dal motore sottostante: alcune funzioni verranno nuovamente mappate, che potrebbero generare diversi ordini SELECT SQL.

Per ulteriori informazioni, vedere [Esempio sul metodo &#39;ExecuteQuery&#39; dello schema &#39;xtk:queryDef&#39;](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

Il metodo **ExecuteQuery** viene presentato in [ExecuteQuery (xtk:queryDef)](#executequery--xtk-querydef-).

### Write {#write}

I comandi di scrittura consentono di scrivere documenti semplici o complessi, con voci in una o più tabelle della base.

Le API transazionali consentono di gestire le riconciliazioni tramite il comando **updateOrInsert** : un comando consente di creare o aggiornare i dati. È inoltre possibile configurare l&#39;unione delle modifiche (**unione**): questa modalità operativa consente di autorizzare aggiornamenti parziali.

La struttura XML offre una visualizzazione logica dei dati e consente di separare la struttura fisica della tabella SQL.

Il metodo Write viene presentato in [Write / WriteCollection (xtk:session)](#write---writecollection--xtk-session-).

## ExecuteQuery (xtk:queryDef) {#executequery--xtk-querydef-}

Questo metodo consente di eseguire query dai dati associati a uno schema. Richiede una stringa di autenticazione (deve essere eseguito il login) e un documento XML che descrive la query da inviare come parametri. Il parametro return è un documento XML che contiene il risultato della query nel formato dello schema a cui la query fa riferimento.

Definizione del metodo &quot;ExecuteQuery&quot; nello schema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Questo è un metodo &quot;const&quot;. I parametri di input sono inclusi in un documento XML nel formato dello schema &quot;xtk:queryDef&quot;.

### Formato del documento XML della query di input {#format-of-the-xml-document-of-the-input-query}

La struttura del documento XML della query è descritta nello schema &quot;xtk:queryDef&quot;. Questo documento descrive le clausole di una query SQL: &quot;select&quot;, &quot;where&quot;, &quot;order by&quot;, &quot;group by&quot;, &quot;have&quot;.

```
<queryDef schema="schema_key" operation="operation_type">
  <select>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </select>
  <where> 
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ... 
  </where>
  <orderBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </orderBy>
  <groupBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </groupBy>
  <having>
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ...
  </having>
</queryDef>
```

Una sottoquery ( `<subquery>` ) può essere definita in un `<condition> ` elemento. La sintassi di un `<subquery> ` elemento si basa sulla sintassi di un `<querydef>`.

Esempio di un `<subquery>  : </subquery>`

```
<condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
  <subQuery schema="xtk:operatorGroup">
     <select>
       <node expr="[@operator-id]" />
     </select>
     <where>
       <condition expr="[@group-id]=$long(../@owner-id)"/>
     </where>
   </subQuery>
</condition>  
  
```

Una query deve fare riferimento a uno schema iniziale dall&#39;attributo **schema** .

Il tipo di operazione desiderata viene immesso nell&#39;attributo **operation** e contiene uno dei seguenti valori:

* **get**: recupera un record dalla tabella e restituisce un errore se i dati non esistono,
* **getIfExists**: recupera un record dalla tabella e restituisce un documento vuoto se i dati non esistono,
* **selezionate**: crea un cursore per restituire più record e restituisce un documento vuoto in assenza di dati,
* **count**: restituisce un conteggio di dati.

La sintassi **XPath** viene utilizzata per individuare i dati in base allo schema di input. Per ulteriori informazioni sugli XPaths, fare riferimento a schemi [di](../../configuration/using/data-schemas.md)dati.

#### Esempio con l&#39;operazione &quot;get&quot; {#example-with-the--get--operation}

Recupera il cognome e il nome di un destinatario (&quot;schema nms:destinatario&quot;) con un filtro nell&#39;e-mail.

```
<queryDef schema="nms:recipient" operation="get">
  <!-- fields to retrieve -->
  <select>
    <node expr="@firstName"/>
    <node expr="@lastName"/>
  </select> 

  <!-- condition on email -->
  <where>  
    <condition expr="@email= 'john.doe@aol.com'"/>
  </where>
</queryDef>
```

#### Esempio con l&#39;operazione &quot;select&quot; {#example-with-the--select--operation}

Restituisce l’elenco dei destinatari filtrati in una cartella e nel dominio e-mail con un ordinamento decrescente in base alla data di nascita.

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <!-- builds a string with the concatenation of the last name and first name separated by a dash -->      
    <node expr="@lastName+'-'+@firstName"/>
    <!-- get year of birth date -->
    <node expr="Year(@birthDate)"/>
  </select> 

  <where>  
     <condition expr="[@folder-id] = 1234 and @domain like 'Adobe%'"/>
  </where>

  <!-- order by birth date -->
  <orderBy>
    <node expr="@birthDate" sortDesc="true"/> <!-- by default sortDesc="false" -->
  </orderBy>
</queryDef>
```

Le espressioni possono essere campi semplici o espressioni complesse come operazioni aritmetiche o la concatenazione di stringhe.

Per limitare il numero di record da restituire, aggiungere l&#39;attributo **lineCount** all&#39; `<querydef>` elemento.

Per limitare a 100 il numero di record restituiti dalla query:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

Per recuperare i 100 record successivi, eseguire di nuovo la stessa query, aggiungendo l&#39;attributo **startLine** .

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### Esempio con l&#39;operazione &#39;count&#39; {#example-with-the--count--operation}

Per contare il numero di record in una query:

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the e-mail -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>Anche in questo caso utilizziamo la condizione dell&#39;esempio precedente. Le clausole `<select>` e non vengono utilizzate. `</select>`

#### Raggruppamento dati {#data-grouping}

Per recuperare gli indirizzi e-mail a cui si fa riferimento più volte:

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- e-mail grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

La query può essere semplificata aggiungendo l’attributo **groupBy** direttamente al campo da raggruppare:

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>Non è più necessario compilare l&#39; `<groupby>` elemento.

#### Fratturazione in condizioni {#bracketing-in-conditions}

Di seguito sono riportati due esempi di bracketing sulla stessa condizione.

* La versione semplice in un&#39;unica espressione:

   ```
   <where>
     <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
   </where>
   ```

* La versione strutturata con `<condition>` gli elementi:

   ```
   <where>
     <condition bool-operator="AND">
       <condition expr="@age > 15" bool-operator="OR"/>
       <condition expr="@age <= 45"/>
     </condition>
     <condition>
       <condition expr="@city = 'Newton'" bool-operator="OR"/>
       <condition expr="@city = 'Culver City'"/>
     </condition>
   </where>
   ```

È possibile sostituire l&#39;operatore &quot;OR&quot; con l&#39;operazione &quot;IN&quot; quando più condizioni si applicano allo stesso campo:

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

Questa sintassi semplifica la query quando nella condizione vengono utilizzati più di due dati.

#### Esempi di collegamenti {#examples-on-links}

* Collegamenti 1-1 o N1: quando la tabella ha la chiave esterna (il collegamento inizia dalla tabella), i campi della tabella collegata possono essere filtrati o recuperati direttamente.

   Esempio di filtro sull’etichetta della cartella:

   ```
   <where>
     <condition expr="[folder/@label] like 'Segment%'"/>
   </where>
   ```

   Per recuperare i campi della cartella dallo schema &quot;nms:destinatario&quot;:

   ```
   <select>
     <!-- label of recipient folder -->
     <node expr="[folder/@label]"/>
     <!-- displays the string count of the folder -->
     <node expr="partition"/>
   </select>
   ```

* Collegamenti raccolta (1N): il filtraggio sui campi di una tabella di raccolta deve essere eseguito tramite l&#39;operatore **EXISTS** o **NOT EXISTS** .

   Per filtrare i destinatari che hanno effettuato la sottoscrizione al servizio di informazione &quot;Newsletter&quot;:

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   Il recupero diretto dei campi di un collegamento di raccolta dalla `<select>` clausola non è consigliato perché la query restituisce un prodotto cardinale. Viene utilizzato solo quando la tabella collegata contiene un solo record (ad esempio `<node expr="">`).

   Esempio di collegamento alla raccolta &quot;subscription&quot;:

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   È possibile recuperare un sotto-elenco contenente gli elementi di un collegamento di raccolta nella `<select>` clausola. Gli XPath dei campi di riferimento sono contestuali dall&#39;elemento collection.

   Gli elementi di filtraggio ( `<orderby>` ) e di restrizione ( `<where>` ) possono essere aggiunti all&#39;elemento raccolta.

   In questo esempio, per ciascun destinatario la query restituisce l&#39;e-mail e l&#39;elenco dei servizi di informazione a cui il destinatario ha aderito:

   ```
   <queryDef schema="nms:recipient" operation="select">
     <select>
       <node expr="@email"/>
   
       <!-- collection table (unbound type) -->
       <node expr="subscription">  
         <node expr="[service/@label]"/>    
         <!-- sub-condition on the collection table -->
         <where>  
           <condition expr="@expirationDate >= GetDate()"/>
         </where>
         <orderBy>
           <node expr="@expirationDate"/> 
         </orderBy>
       </node>
     </select> 
   </queryDef>
   ```

#### Binding dei parametri della clausola &#39;where&#39; e &#39;select&#39; {#binding-the-parameters-of-the--where--and--select--clause}

Il binding dei parametri consente al motore di impostare i valori dei parametri utilizzati nella query. Questo è molto utile, dal momento che il motore è responsabile dell&#39;evasione dei valori, e c&#39;è il vantaggio aggiuntivo di una cache per i parametri da recuperare.

Quando viene creata una query, i valori &quot;bound&quot; vengono sostituiti da un carattere (? in ODBC, `#[index]#` in postgres...) nel corpo della query SQL.

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

Per evitare di eseguire il binding di un parametro, l&#39;attributo &quot;noSqlBind&quot; deve essere popolato con il valore &quot;true&quot;.

>[!IMPORTANT]
>
>Se la query include istruzioni &quot;order-by&quot; o &quot;group-by&quot;, i motori di database non saranno in grado di &quot;eseguire il binding&quot; dei valori. È necessario inserire l&#39;attributo @noSqlBind=&quot;true&quot; nelle istruzioni &quot;select&quot; e/o &quot;where&quot; della query.

#### Suggerimento per la creazione di query: {#query-building-tip-}

Per semplificare la sintassi di una query, è possibile scrivere la query utilizzando l&#39;editor query generico nella console client Adobe Campaign  ( **[!UICONTROL Tools/ Generic query editor...]** menu). Per eseguire questa operazione:

1. Selezionare i dati da recuperare:

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. Definire la condizione del filtro:

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. Eseguire la query e premere CTRL+F4 per visualizzare il codice sorgente della query.

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### Formato documento di output {#output-document-format}

Il parametro return è un documento XML nel formato dello schema associato alla query.

Esempio di restituzione dallo schema &quot;nms:destinatario&quot; in un&#39;operazione &quot;get&quot;:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

In un&#39;operazione di selezione, il documento restituito è un&#39;enumerazione di elementi:

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

Esempio di documento restituito per l&#39;operazione di tipo &quot;count&quot;:

```
<recipient count="3"/>
```

#### Alias {#alias}

Un alias consente di modificare la posizione dei dati nel documento di output. L&#39;attributo **alias** deve specificare un XPath nel campo corrispondente.

```
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

Restituisce:

```
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

Invece di:

```
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### Esempio di messaggi SOAP {#example-of-soap-messages}

* Query:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <__sessiontoken xsi:type='xsd:string'/>
         <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <queryDef operation="get" schema="nms:recipient" xtkschema="xtk:queryDef">
             <select>
               <node expr="@email"/>
               <node expr="@lastName"/>
               <node expr="@firstName"/>
             </select>
             <where>
               <condition expr="@id = 3599"/>
             </where>
           </queryDef>
         </entity>
       </ExecuteQuery>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Risposta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
         </pdomOutput>
       </ExecuteQueryResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Write / WriteCollection (xtk:session) {#write---writecollection--xtk-session-}

Questi servizi vengono utilizzati per inserire, aggiornare o eliminare un&#39;entità (&quot;metodo Write&quot;) o un insieme di entità (&quot;metodo WriteCollection&quot;).

Le entità da aggiornare sono associate a uno schema di dati. I parametri di input sono una stringa di autenticazione (deve essere eseguito il login) e un documento XML contenente i dati da aggiornare.

Questo documento è completato da istruzioni per la configurazione delle procedure di scrittura.

La chiamata non restituisce alcun dato, tranne eventuali errori.

Definizione dei metodi &quot;Write&quot; e &quot;WriteCollection&quot; nello schema &quot;xtk:session&quot;:

```
<method name="Write" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference document"/>
  </parameters>
</method>
<method name="WriteCollection" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference collection document"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Questo è un metodo &quot;statico&quot;. I parametri di input sono inclusi in un documento XML nel formato dello schema da aggiornare.

### Panoramica {#overview}

La riconciliazione dei dati funziona in base alla definizione delle chiavi inserite nello schema associato. La procedura di scrittura cerca la prima chiave idonea in base ai dati immessi nel documento di input. L&#39;entità viene inserita o aggiornata in base alla sua esistenza nel database.

La chiave dello schema dell&#39;entità da aggiornare viene completata in base all&#39;attributo **xtkschema** .

La chiave di riconciliazione può quindi essere forzata con l&#39;attributo **_key** contenente l&#39;elenco di XPaths che compongono la chiave (separati da virgole).

È possibile forzare il tipo di operazione compilando l&#39;attributo **_operation** con i seguenti valori:

* **inserire**: forza l&#39;inserimento del record (la chiave di riconciliazione non è utilizzata),
* **insertOrUpdate**: aggiorna o inserisce il record in base alla chiave di riconciliazione (modalità predefinita),
* **update**: aggiorna il record; non fa nulla se i dati non esistono,
* **delete**: elimina i record,
* **none**: utilizzato solo per la riconciliazione dei collegamenti, senza aggiornamento o inserimento.

### Esempio con il metodo &#39;Write&#39; {#example-with-the--write--method}

Aggiornamento o inserimento di un destinatario (operazione implicita &quot;insertOrUpdate&quot;) con indirizzo e-mail, data di nascita e città:

```
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

Eliminazione di un destinatario:

```
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>Per un&#39;operazione di eliminazione, il documento di input deve contenere solo i campi che costituiscono la chiave di riconciliazione.

### Esempio con il metodo &#39;WriteCollection&#39; {#example-with-the--writecollection--method}

Aggiornamento o inserimento per diversi destinatari:

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### Esempio di collegamenti {#example-on-links}

#### Example 1 {#example-1}

Associazione della cartella a un destinatario in base al nome interno (@name).

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

Gli attributi &quot;_key&quot; e &quot;_operation&quot; possono essere inseriti in un elemento collegato. Il comportamento di questo elemento è lo stesso dell&#39;elemento principale dello schema di input.

La definizione della chiave dell&#39;entità principale (&quot;nms:Recipient&quot;) è costituita da un campo da una tabella collegata (schema elemento `<folder>` &quot;xtk:folder&quot;) e dall&#39;e-mail.

>[!NOTE]
>
>L&#39;operazione &quot;none&quot; immessa nell&#39;elemento cartella definisce una riconciliazione sulla cartella senza aggiornare o inserire.

#### Example 2 {#example-2}

Aggiornamento della società (tabella collegata nello schema &quot;cus:company&quot;) da un destinatario:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Example 3 {#example-3}

Aggiunta di un destinatario a un gruppo con la tabella di relazione del gruppo (&quot;nms:rcpGrpRel&quot;):

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>La definizione della chiave non viene immessa nell&#39; `<rcpgroup>` elemento perché una chiave implicita basata sul nome del gruppo è definita nello schema &quot;nms:group&quot;.

### Elementi della raccolta XML {#xml-collection-elements}

Per impostazione predefinita, tutti gli elementi della raccolta devono essere compilati per aggiornare gli elementi della raccolta XML. I dati del database verranno sostituiti con i dati del documento di input. Se il documento contiene solo gli elementi da aggiornare, è necessario compilare l&#39;attributo &quot;_operation&quot; su tutti gli elementi della raccolta da aggiornare per imporre l&#39;unione con i dati XML del database.

### Esempio di messaggi SOAP {#example-of-soap-messages-1}

* Query:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <Write xmlns='urn:xtk:persist' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <__sessiontoken xsi:type='xsd:string'/>
         <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient xtkschema="nms:recipient" email="rene.dupont@adobe.com" firstName="René" lastName="Dupont" _key="@email">
         </domDoc>
       </Write>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Risposta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </WriteResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

   Invio con errore:

   ```
   <?xml version='1.0'?>
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <SOAP-ENV:Fault>
         <faultcode>SOAP-ENV:Server</faultcode>
         <faultstring xsi:type="xsd:string">Error while executing the method 'Write' of service 'xtk:persist'.</faultstring>
         <detail xsi:type="xsd:string">PostgreSQL error: ERROR:  duplicate key violates unique constraint &quot;nmsrecipient_id&quot;Impossible to save document of type 'Recipients (nms:recipient)'</detail>
       </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

