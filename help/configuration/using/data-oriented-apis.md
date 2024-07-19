---
product: campaign
title: API orientate ai dati
description: API orientate ai dati
feature: API
role: Data Engineer, Developer
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1864'
ht-degree: 0%

---

# API orientate ai dati{#data-oriented-apis}

Le API orientate ai dati consentono di indirizzare l’intero modello dati.

## Panoramica del modello dati {#overview-of-the-datamodel}

Adobe Campaign non offre un’API di lettura dedicata per entità (nessuna funzione getRecipient o getDelivery, ecc.). Utilizzare i metodi di lettura e modifica dei dati QUERY &amp; WRITER per accedere ai dati del modello.

Adobe Campaign consente di gestire le raccolte: le query consentono di recuperare un set di informazioni raccolte in tutta la base. A differenza dell’accesso in modalità SQL, le API di Adobe Campaign restituiscono una struttura XML anziché colonne di dati. Adobe Campaign crea quindi documenti compositi con tutti i dati raccolti.

Questa modalità operativa non offre il mapping uno-a-uno tra gli attributi e gli elementi dei documenti XML e le colonne delle tabelle nel database.

I documenti XML vengono memorizzati nei campi di tipo MEMO del database.

## Descrizione del modello {#description-of-the-model}

Per poter gestire i campi del database negli script, è necessario avere familiarità con il modello dati di Adobe Campaign.

Per una presentazione del modello dati, fare riferimento alla [descrizione del modello dati Adobe Campaign](../../configuration/using/data-model-description.md).

## Query e writer {#query-and-writer}

Il seguente schema introduttivo descrive gli scambi di basso livello per la lettura (ExecuteQuery) e la scrittura (Writer) tra database e cliente (pagine web o console client di Adobe Campaign).

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

Per le colonne e le condizioni, è possibile utilizzare le query.

In questo modo è possibile isolare l&#39;istruzione SQL sottostante. Il linguaggio di query non dipende dal motore sottostante: alcune funzioni verranno nuovamente mappate, il che potrebbe generare diversi ordini SELECT SQL.

Per ulteriori informazioni, consultare [Esempio sul metodo &#39;ExecuteQuery&#39; dello schema &#39;xtk:queryDef&#39;](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

Il metodo **ExecuteQuery** è presentato in [ExecuteQuery (xtk:queryDef)](#executequery--xtk-querydef-).

### Scrittura {#write}

I comandi di scrittura consentono di scrivere documenti semplici o complessi, con voci in una o più tabelle della base.

Le API transazionali consentono di gestire le riconciliazioni tramite il comando **updateOrInsert**: un comando consente di creare o aggiornare dati. È inoltre possibile configurare l&#39;unione modifiche (**merge**): questa modalità operativa consente di autorizzare aggiornamenti parziali.

La struttura XML offre una vista logica dei dati e consente di ignorare la struttura fisica della tabella SQL.

Il metodo Write è presentato in [Write / WriteCollection (xtk:session)](#write---writecollection--xtk-session-).

## ExecuteQuery (xtk:queryDef) {#executequery--xtk-querydef-}

Questo metodo consente di eseguire query dai dati associati a uno schema. Richiede una stringa di autenticazione (deve aver effettuato l’accesso) e un documento XML che descriva la query da inviare come parametri. Il parametro restituito è un documento XML contenente il risultato della query nel formato dello schema a cui la query fa riferimento.

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
>Si tratta di un metodo &quot;const&quot;. I parametri di input vengono inclusi in un documento XML nel formato dello schema &quot;xtk:queryDef&quot;.

### Formato del documento XML della query di input {#format-of-the-xml-document-of-the-input-query}

La struttura del documento XML della query è descritta nello schema &quot;xtk:queryDef&quot;. Questo documento descrive le clausole di una query SQL: &quot;select&quot;, &quot;where&quot;, &quot;order by&quot;, &quot;group by&quot;, &quot;HAVING&quot;.

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

È possibile definire una sottoquery ( `<subquery>` ) in un elemento `<condition> `. La sintassi per un   `<subquery> `   è basato sulla sintassi di un elemento    `<querydef>`.

Esempio di `<subquery>  : </subquery>`

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

Una query deve fare riferimento a uno schema iniziale dall&#39;attributo **schema**.

Il tipo di operazione desiderato viene immesso nell&#39;attributo **operation** e contiene uno dei valori seguenti:

* **get**: recupera un record dalla tabella e restituisce un errore se i dati non esistono,
* **getIfExists**: recupera un record dalla tabella e restituisce un documento vuoto se i dati non esistono,
* **select**: crea un cursore per restituire più record e restituisce un documento vuoto se non sono presenti dati.
* **count**: restituisce un conteggio di dati.

La sintassi **XPath** viene utilizzata per individuare i dati in base allo schema di input. Per ulteriori informazioni su XPaths, fare riferimento a [Schemi di dati](../../configuration/using/data-schemas.md).

#### Esempio con l’operazione &quot;get&quot; {#example-with-the--get--operation}

Recupera il cognome e il nome di un destinatario (schema &quot;nms:recipient&quot;) con un filtro nell’e-mail.

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

#### Esempio con l’operazione &quot;select&quot; {#example-with-the--select--operation}

Restituisce l’elenco dei destinatari filtrati su una cartella e il dominio e-mail con un ordinamento decrescente alla data di nascita.

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

Le espressioni possono essere campi semplici o espressioni complesse, ad esempio operazioni aritmetiche o concatenazione di stringhe.

Per limitare il numero di record da restituire, aggiungere l&#39;attributo **lineCount** all&#39;elemento `<querydef>`.

Per limitare a 100 il numero di record restituiti dalla query:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

Per recuperare i 100 record successivi, eseguire nuovamente la stessa query, aggiungendo l&#39;attributo **startLine**.

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### Esempio con l’operazione &quot;count&quot; {#example-with-the--count--operation}

Per contare il numero di record in una query:

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the email -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>Anche in questo caso, utilizziamo la condizione dell’esempio precedente. `<select>` e le clausole non sono utilizzate. `</select>`

#### Raggruppamento di dati {#data-grouping}

Per recuperare gli indirizzi e-mail a cui si fa riferimento più di una volta:

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- email grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

La query può essere semplificata aggiungendo l&#39;attributo **groupBy** direttamente al campo da raggruppare:

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>Non è più necessario popolare l&#39;elemento `<groupby>`.

#### Parentesi quadra in condizioni {#bracketing-in-conditions}

Di seguito sono riportati due esempi di parentesi quadre nella stessa condizione.

* La versione semplice in una singola espressione:

  ```
  <where>
    <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
  </where>
  ```

* Versione strutturata con `<condition>` elementi:

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

È possibile sostituire l’operatore &quot;OR&quot; con l’operazione &quot;IN&quot; quando più condizioni si applicano allo stesso campo:

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

Questa sintassi semplifica la query quando nella condizione vengono utilizzati più di due dati.

#### Esempi sui collegamenti {#examples-on-links}

* Collegamenti 1-1 o N1: quando la tabella ha la chiave esterna (il collegamento inizia dalla tabella), i campi della tabella collegata possono essere filtrati o recuperati direttamente.

  Esempio di filtro sull’etichetta della cartella:

  ```
  <where>
    <condition expr="[folder/@label] like 'Segment%'"/>
  </where>
  ```

  Per recuperare i campi della cartella dallo schema &quot;nms:recipient&quot;:

  ```
  <select>
    <!-- label of recipient folder -->
    <node expr="[folder/@label]"/>
    <!-- displays the string count of the folder -->
    <node expr="partition"/>
  </select>
  ```

* Collegamenti di raccolta (1N): il filtro sui campi di una tabella di raccolta deve essere eseguito tramite l&#39;operatore **EXISTS** o **NOT EXISTS**.

  Per filtrare i destinatari abbonati al servizio di informazioni &quot;Newsletter&quot;:

  ```
  <where>
    <condition expr="subscription" setOperator="EXISTS">
      <condition expr="@name = 'Newsletter'"/>
    </condition>
  </where>
  ```

  Il recupero diretto dei campi di un collegamento di raccolta dalla clausola `<select>` non è consigliato perché la query restituisce un prodotto cardinale. Viene utilizzato solo quando la tabella collegata contiene un solo record (esempio: `<node expr="">`).

  Esempio sul collegamento di raccolta &quot;subscription&quot;:

  ```
  <select>
    <node expr="subscription/@label"/>
  </select>
  ```

  È possibile recuperare un sottoelenco contenente gli elementi di un collegamento di raccolta nella clausola `<select>`. Gli XPaths dei campi a cui si fa riferimento sono contestuali rispetto all&#39;elemento di raccolta.

  È possibile aggiungere all&#39;elemento raccolta gli elementi di filtro ( `<orderby>` ) e di restrizione ( `<where>` ).

  In questo esempio, per ogni destinatario la query restituisce l’e-mail e l’elenco dei servizi di informazione a cui il destinatario si abbona:

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

#### Associazione dei parametri delle clausole &#39;where&#39; e &#39;select&#39; {#binding-the-parameters-of-the--where--and--select--clause}

L’associazione dei parametri consente al motore di impostare i valori dei parametri utilizzati nella query. Questo è molto utile, poiché il motore è responsabile dell’escape dei valori e c’è il vantaggio aggiuntivo di una cache per i parametri da recuperare.

Quando viene creata una query, i valori &quot;associati&quot; vengono sostituiti da un carattere (? in ODBC, `#[index]#` in postgres...) nel corpo della query SQL.

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

Per evitare di associare un parametro, l&#39;attributo &quot;noSqlBind&quot; deve essere compilato con il valore &quot;true&quot;.

>[!IMPORTANT]
>
>Se la query include istruzioni &quot;ordina per&quot; o &quot;raggruppa per&quot;, i motori di database non saranno in grado di &quot;associare&quot; i valori. È necessario inserire l&#39;attributo @noSqlBind=&quot;true&quot; nelle istruzioni &quot;select&quot; e/o &quot;where&quot; della query.

#### Suggerimento per creazione query: {#query-building-tip-}

Per semplificare la sintassi di una query, è possibile scrivere la query utilizzando l&#39;editor di query generico nella console del client Adobe Campaign (menu **[!UICONTROL Tools/ Generic query editor...]**). Per eseguire questa operazione:

1. Seleziona i dati da recuperare:

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. Definisci la condizione del filtro:

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. Eseguire la query e premere CTRL+F4 per visualizzare il codice sorgente della query.

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### Formato documento di output {#output-document-format}

Il parametro restituito è un documento XML nel formato dello schema associato alla query.

Esempio di ritorno dallo schema &quot;nms:recipient&quot; su un’operazione &quot;get&quot;:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

In un’operazione di &quot;selezione&quot;, il documento restituito è un’enumerazione di elementi:

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

Esempio di documento restituito per l&#39;operazione di tipo &quot;conteggio&quot;:

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

## Write/WriteCollection (xtk:session) {#write---writecollection--xtk-session-}

Questi servizi vengono utilizzati per inserire, aggiornare o eliminare un&#39;entità (metodo &quot;Write&quot;) o un insieme di entità (metodo &quot;WriteCollection&quot;).

Le entità da aggiornare sono associate a uno schema di dati. I parametri di input sono una stringa di autenticazione (deve essere effettuato l&#39;accesso) e un documento XML contenente i dati da aggiornare.

Questo documento è completato da istruzioni per la configurazione delle procedure di scrittura.

La chiamata non restituisce alcun dato, ad eccezione degli errori.

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
>Si tratta di un metodo &quot;statico&quot;. I parametri di input vengono inclusi in un documento XML nel formato dello schema da aggiornare.

### Panoramica {#overview}

La riconciliazione dei dati funziona in base alla definizione delle chiavi immesse nello schema associato. La procedura di scrittura cerca la prima chiave idonea in base ai dati immessi nel documento di input. L’entità viene inserita o aggiornata in base alla sua esistenza nel database.

La chiave dello schema dell&#39;entità da aggiornare è completata in base all&#39;attributo **xtkschema**.

È quindi possibile forzare la chiave di riconciliazione con l&#39;attributo **_key** contenente l&#39;elenco di XPaths che compongono la chiave (separati da virgole).

È possibile forzare il tipo di operazione compilando l&#39;attributo **_operation** con i valori seguenti:

* **insert**: forza l&#39;inserimento del record (la chiave di riconciliazione non viene utilizzata),
* **insertOrUpdate**: aggiorna o inserisce il record a seconda della chiave di riconciliazione (modalità predefinita),
* **update**: aggiorna il record; non esegue alcuna operazione se i dati non esistono,
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
>Per un’operazione di eliminazione, il documento di input deve contenere solo i campi che compongono la chiave di riconciliazione.

### Esempio con il metodo &#39;WriteCollection&#39; {#example-with-the--writecollection--method}

Aggiornamento o inserimento per più destinatari:

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### Esempio di collegamenti {#example-on-links}

#### Esempio 1 {#example-1}

Associazione della cartella a un destinatario in base al suo nome interno (@name).

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

Gli attributi &quot;_key&quot; e &quot;_operation&quot; possono essere immessi in un elemento collegato. Il comportamento di questo elemento è lo stesso dell’elemento principale dello schema di input.

La definizione della chiave dell&#39;entità principale (&quot;nms:recipient&quot;) è costituita da un campo di una tabella collegata (elemento `<folder>` schema &quot;xtk:folder&quot;) e dall&#39;e-mail.

>[!NOTE]
>
>L’operazione &quot;none&quot; immessa sull’elemento cartella definisce una riconciliazione sulla cartella senza aggiornamento o inserimento.

#### Esempio 2 {#example-2}

Aggiornamento della società (tabella collegata nello schema &quot;cus:company&quot;) da un destinatario:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Esempio 3 {#example-3}

Aggiunta di un destinatario a un gruppo con la tabella delle relazioni di gruppo (&quot;nms:rcpGrpRel&quot;):

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>La definizione della chiave non viene immessa nell&#39;elemento `<rcpgroup>` perché nello schema &quot;nms:group&quot; è definita una chiave implicita basata sul nome del gruppo.

### Elementi della raccolta XML {#xml-collection-elements}

Per impostazione predefinita, per aggiornare gli elementi di raccolta XML è necessario compilare tutti gli elementi di raccolta. I dati del database verranno sostituiti con i dati del documento di input. Se il documento contiene solo gli elementi da aggiornare, è necessario compilare l&#39;attributo &quot;_operation&quot; su tutti gli elementi di raccolta da aggiornare per forzare un&#39;unione con i dati XML del database.

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

  Restituisci con errore:

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
