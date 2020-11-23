---
solution: Campaign Classic
product: campaign
title: Mappatura del database
description: Mappatura del database
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1974'
ht-degree: 0%

---


# Mappatura del database{#database-mapping}

La mappatura SQL dello schema di esempio fornisce il seguente documento XML:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Descrizione {#description}

L&#39;elemento principale dello schema non è più **`<srcschema>`**, ma **`<schema>`**.

Questo ci porta a un altro tipo di documento, che viene generato automaticamente dallo schema di origine, semplicemente denominato schema. Questo schema verrà utilizzato dall&#39;applicazione Adobe Campaign .

I nomi SQL vengono determinati automaticamente in base al nome e al tipo dell&#39;elemento.

Le regole di denominazione SQL sono le seguenti:

* tabella: concatenazione dello spazio dei nomi e del nome dello schema

   Nel nostro esempio, il nome della tabella viene immesso tramite l&#39;elemento principale dello schema nell&#39;attributo **sqltable** :

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* field: nome dell&#39;elemento preceduto da un prefisso definito in base al tipo (&#39;i&#39; per integer, &#39;d&#39; per double, &#39;s&#39; per stringa, &#39;ts&#39; per date, ecc.)

   Il nome del campo viene immesso tramite l&#39;attributo **sqlname** per ciascun tipo **`<attribute>`** e **`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>I nomi SQL possono essere sovraccaricati dallo schema di origine. A tal fine, popolate gli attributi &quot;sqltable&quot; o &quot;sqlname&quot; sull&#39;elemento interessato.

Lo script SQL per creare la tabella generata dallo schema esteso è il seguente:

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

I vincoli del campo SQL sono i seguenti:

* nessun valore nullo nei campi numerici e di data,
* i campi numerici sono inizializzati a 0.

## Campi XML {#xml-fields}

Per impostazione predefinita, qualsiasi elemento digitato **`<attribute>`** e **`<element>`** viene mappato su un campo SQL della tabella dello schema di dati. È tuttavia possibile fare riferimento a questo campo in XML invece che in SQL, il che significa che i dati vengono memorizzati in un campo Memo (&quot;mData&quot;) della tabella contenente i valori di tutti i campi XML. La memorizzazione di questi dati è un documento XML che osserva la struttura dello schema.

Per compilare un campo in XML, è necessario aggiungere l&#39;attributo **xml** con il valore &quot;true&quot; all&#39;elemento interessato.

**Esempio**: di seguito sono riportati due esempi di utilizzo di campi XML.

* Campo commento su più righe:

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* Descrizione dei dati in formato HTML:

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   Il tipo &quot;html&quot; consente di archiviare il contenuto HTML in un tag CDATA e di visualizzare un controllo speciale per la modifica HTML nell&#39;interfaccia client  Adobe Campaign.

L&#39;utilizzo di campi XML consente di aggiungere campi senza dover modificare la struttura fisica del database. Un altro vantaggio è rappresentato dal minor utilizzo di risorse (dimensione allocata ai campi SQL, limite al numero di campi per tabella, ecc.).

Lo svantaggio principale è che è impossibile indicizzare o filtrare un campo XML.

## Campi indicizzati {#indexed-fields}

Gli indici consentono di ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione.

Un indice è dichiarato dall&#39;elemento principale dello schema dati.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Gli indici obbediscono alle regole seguenti:

* Un indice può fare riferimento a uno o più campi della tabella.
* Un indice può essere univoco (per evitare duplicati) in tutti i campi se l&#39;attributo **univoco** contiene il valore &quot;true&quot;.
* Il nome SQL dell&#39;indice è determinato dal nome SQL della tabella e dal nome dell&#39;indice.

>[!NOTE]
>
>Come standard, gli indici sono i primi elementi dichiarati dall&#39;elemento principale dello schema.

>[!NOTE]
>
>Gli indici vengono creati automaticamente durante la mappatura della tabella (standard o FDA).

**Esempio**:

* Aggiunta di un indice all’indirizzo e-mail e alla città:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* Aggiunta di un indice univoco al campo del nome &quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="id" unique="true">
         <keyfield xpath="@id"/> 
       </dbindex>
   
       <dbindex name="email">
         <keyfield xpath="@email"/> 
       </dbindex>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## Gestione delle chiavi {#management-of-keys}

Una tabella deve avere almeno una chiave per identificare un record nella tabella.

Una chiave viene dichiarata dall&#39;elemento principale dello schema dati.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Le chiavi obbediscono alle regole seguenti:

* Una chiave può fare riferimento a uno o più campi nella tabella.
* Una chiave è nota come &#39;principale&#39; (o &#39;priorità&#39;) quando è la prima nello schema da compilare o se contiene l&#39;attributo **interno** con il valore &quot;true&quot;.
* Un indice univoco viene dichiarato implicitamente per ogni definizione di chiave. È possibile impedire la creazione di un indice sulla chiave aggiungendo l&#39;attributo **noDbIndex** con il valore &quot;true&quot;.

>[!NOTE]
>
>Come standard, le chiavi sono gli elementi dichiarati dall&#39;elemento principale dello schema dopo la definizione degli indici.

>[!NOTE]
>
>Le chiavi vengono create durante la mappatura della tabella (standard o FDA),  Adobe Campaign trova indici univoci.

**Esempio**:

* Aggiunta di una chiave all’indirizzo e-mail e alla città:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

   Schema generato:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
      <dbindex name="email" unique="true">      
        <keyfield xpath="@email"/>      
        <keyfield xpath="location/@city"/>    
      </dbindex>    
   
      <key name="email">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
      </key>    
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* Aggiunta di una chiave primaria o interna al campo del nome &quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="id" internal="true">
         <keyfield xpath="@id"/> 
       </key>
   
       <key name="email" noDbIndex="true">
         <keyfield xpath="@email"/> 
       </key>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

   Schema generato:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
       <key name="email">      
         <keyfield xpath="@email"/>    
       </key>    
   
       <dbindex name="id" unique="true">      
         <keyfield xpath="@id"/>    
       </dbindex>    
   
       <key internal="true" name="id">      
        <keyfield xpath="@id"/>    
       </key>    
   
       <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### Tasto incrementale automatico {#auto-incremental-key}

La chiave primaria della maggior parte  tabelle Adobe Campaign è un numero intero lungo 32 bit generato automaticamente dal motore del database. Il calcolo del valore chiave dipende da una sequenza (per impostazione predefinita, la funzione SQL **XtkNewId** ) che genera un numero univoco nell&#39;intero database. Il contenuto della chiave viene inserito automaticamente all&#39;inserimento del record.

Il vantaggio di una chiave incrementale è che fornisce una chiave tecnica non modificabile per i join tra le tabelle. Inoltre, questa chiave non occupa molta memoria perché utilizza un numero intero a doppio byte.

Potete specificare nello schema di origine il nome della sequenza da utilizzare con l&#39;attributo **pkSequence** . Se questo attributo non viene specificato nello schema di origine, verrà utilizzata la sequenza predefinita **XtkNewId** . L&#39;applicazione utilizza sequenze dedicate per gli schemi **nms:wideLog** e **nms:trackingLog** (rispettivamente **NmsBroadLogId** e **NmsTrackingLogId** ), in quanto queste tabelle contengono la maggior parte dei record.

Da ACC 18.10, **XtkNewId** non è più il valore predefinito per la sequenza negli schemi predefiniti. È ora possibile creare uno schema o estendere lo schema esistente con una sequenza dedicata.

>[!IMPORTANT]
>
>Durante la creazione di un nuovo schema o durante un&#39;estensione dello schema, è necessario mantenere lo stesso valore di sequenza della chiave primaria (@pkSequence) per l&#39;intero schema.

>[!NOTE]
>
>Una sequenza cui viene fatto riferimento in uno schema Adobe Campaign  (ad esempio,**NmsTrackingLogId** ) deve essere associata a una funzione SQL che restituisce il numero di ID nei parametri, separati da virgole. Questa funzione deve essere denominata ******GetNewXXXIds**, dove **XXX** è il nome della sequenza (ad esempio,**GetNewNmsTrackingLogIds** ). Visualizzare i file **postgres-nms.sql**, **mssql-nms.sql** o **oracle-nms.sql** forniti con l&#39;applicazione nella directory **datakit/nms/eng/sql/** per recuperare l&#39;esempio di creazione di una sequenza &#39;NmsTrackingLogId&#39; per ogni motore di database.

Per dichiarare una chiave univoca, compilare l&#39;attributo **autopk** (con valore &quot;true&quot;) sull&#39;elemento principale dello schema dati.

**Esempio**:

Dichiarazione di una chiave incrementale nello schema di origine:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Schema generato:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Oltre alla definizione della chiave e del relativo indice, allo schema esteso è stato aggiunto un campo numerico denominato &quot;id&quot; per contenere la chiave primaria generata automaticamente.

>[!IMPORTANT]
>
>Un record con una chiave primaria impostata su 0 viene inserito automaticamente al momento della creazione della tabella. Questo record viene utilizzato per evitare i join esterni, che non sono efficaci sulle tabelle dei volumi. Per impostazione predefinita, tutte le chiavi esterne sono inizializzate con il valore 0, in modo che sia sempre possibile restituire un risultato sul join quando l&#39;elemento dati non è popolato.

## Collegamenti: relazione tra tabelle {#links--relation-between-tables}

Un collegamento descrive l&#39;associazione tra una tabella e l&#39;altra.

I vari tipi di associazioni (note come &quot;cardinalità&quot;) sono i seguenti:

* Cardinality 1-1: one occurrence of the source table can have at most one corresponding occurrence of the target table.
* Cardinalità 1-N: una occorrenza della tabella di origine può avere diverse occorrenze corrispondenti della tabella di destinazione, ma una occorrenza della tabella di destinazione può avere al massimo una occorrenza corrispondente della tabella di origine.
* Cardinalità N-N: una occorrenza della tabella di origine può avere diverse occorrenze corrispondenti della tabella di destinazione e viceversa.

Nell&#39;interfaccia, è possibile distinguere facilmente i diversi tipi di relazioni grazie alle loro icone.

Per le relazioni di partecipazione con una tabella/database di campagna:

* ![](assets/join_with_campaign11.png) : Cardinalità 1-1. Ad esempio, tra un destinatario e un ordine corrente. Un destinatario può essere correlato a una sola occorrenza della tabella dell&#39;ordine corrente alla volta.
* ![](assets/externaljoin11.png) : Cardinalità 1-1, unione esterna. Ad esempio, tra un destinatario e il relativo paese. Un destinatario può essere correlato a una sola occorrenza del paese della tabella. Il contenuto della tabella del paese non verrà salvato.
* ![](assets/join_with_campaign1n.png) : Cardinalità 1-N. Ad esempio, tra un destinatario e la tabella delle iscrizioni. Un destinatario può essere correlato a diverse occorrenze nella tabella delle sottoscrizioni.

Per le relazioni di join mediante Federated Database Access:

* ![](assets/join_fda_11.png) : Cardinalità 1-1
* ![](assets/join_fda_1m.png) : Cardinalità 1-N

Per ulteriori informazioni sulle tabelle FDA, vedere [Accesso a un database](../../installation/using/about-fda.md)esterno.

Un collegamento deve essere dichiarato nello schema contenente la chiave esterna della tabella collegata tramite l&#39;elemento principale:

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

I collegamenti rispettano le regole seguenti:

* La definizione di collegamento viene inserita in un tipo di **collegamento****`<element>`** con i seguenti attributi:

   * **name**: nome del collegamento dalla tabella di origine,
   * **target**: nome dello schema di destinazione,
   * **label**: etichetta del collegamento,
   * **revLink** (facoltativo): nome del collegamento inverso dallo schema di destinazione (dedotto automaticamente per impostazione predefinita),
   * **integrità** (facoltativo): integrità referenziale dell&#39;occorrenza della tabella di origine all&#39;occorrenza della tabella di destinazione. I valori possibili sono i seguenti:

      * **definire**: è possibile eliminare l&#39;occorrenza di origine se non vi è più riferimento da un&#39;occorrenza di destinazione,
      * **normale**: l&#39;eliminazione dell&#39;occorrenza di origine inizializza le chiavi del collegamento all&#39;occorrenza di destinazione (modalità predefinita). Questo tipo di integrità inizializza tutte le chiavi esterne,
      * **proprie**: l&#39;eliminazione dell&#39;occorrenza di origine porta all&#39;eliminazione dell&#39;occorrenza di destinazione,
      * **owncopy**: le stesse **proprie** (in caso di cancellazione) o duplica le occorrenze (in caso di duplicazione),
      * **neutro**: non fa niente.
   * **revIntegrity** (facoltativo): integrità dello schema di destinazione (facoltativo, &quot;normale&quot; per impostazione predefinita),
   * **revCardinality** (facoltativo): con il valore &quot;single&quot; popola la cardinalità con tipo 1-1 (1-N per impostazione predefinita).
   * **externalJoin** (facoltativo): forza l&#39;unione esterna
   * **revExternalJoin** (facoltativo): forza l&#39;unione esterna sul collegamento inverso


* Un collegamento fa riferimento a uno o più campi dalla tabella di origine alla tabella di destinazione. I campi che compongono il join ( `<join>` elemento) non devono essere compilati perché vengono automaticamente dedotti per impostazione predefinita utilizzando la chiave interna dello schema di destinazione.
* Un indice viene aggiunto automaticamente alla chiave esterna del collegamento nello schema esteso.
* Un collegamento è composto da due collegamenti intermedi, in cui il primo è dichiarato dallo schema di origine e il secondo viene creato automaticamente nello schema esteso dello schema di destinazione.
* Un join può essere un join esterno se viene aggiunto l’attributo **externalJoin** , con il valore &quot;true&quot; (supportato in PostgreSQL).

>[!NOTE]
>
>Come standard, i collegamenti sono gli elementi dichiarati alla fine dello schema.

### Example 1 {#example-1}

1-N in relazione alla tabella dello schema &quot;cus:company&quot;:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Schema generato:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La definizione del collegamento è completata dai campi che compongono il join, ovvero la chiave primaria con il relativo XPath (&quot;@id&quot;) nello schema di destinazione, e la chiave esterna con il relativo XPath (&quot;@company-id&quot;) nello schema.

La chiave esterna viene aggiunta automaticamente in un elemento che utilizza le stesse caratteristiche del campo associato nella tabella di destinazione, con la seguente convenzione di denominazione: nome dello schema di destinazione seguito dal nome del campo associato (&quot;company-id&quot; nel nostro esempio).

Schema esteso della destinazione (&quot;cus:company&quot;):

```
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

È stato aggiunto un collegamento inverso alla tabella &quot;cus:Recipient&quot; con i seguenti parametri:

* **name**: dedotto automaticamente dal nome dello schema di origine (può essere forzato con l&#39;attributo &quot;revLink&quot; nella definizione del collegamento nello schema di origine)
* **revLink**: nome del collegamento inverso
* **target**: chiave dello schema collegato (schema &quot;cus:Recipient&quot;)
* **unbound**: il collegamento è dichiarato come elemento di raccolta per una cardinalità 1-N (per impostazione predefinita)
* **integrità**: &quot;define&quot; per impostazione predefinita (può essere forzato con l&#39;attributo &quot;revIntegrity&quot; nella definizione del collegamento sullo schema di origine).

### Example 2 {#example-2}

In questo esempio, dichiareremo un collegamento verso la tabella dello schema &quot;nms:address&quot;. Il join è un join esterno ed è popolato esplicitamente con l&#39;indirizzo e-mail del destinatario e il campo &quot;@address&quot; della tabella collegata (&quot;nms:address&quot;).

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Example 3 {#example-3}

1-1 relazione con la tabella dello schema &quot;cus:extension&quot;:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Example 4 {#example-4}

Collegare una cartella (&quot;schema xtk:folder&quot;):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Il valore predefinito restituisce l&#39;identificatore del primo file di tipo di parametro idoneo immesso nella funzione &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

### Example 5 {#example-5}

In questo esempio, desideriamo creare una chiave su un collegamento (&quot;società&quot; a schema &quot;cus:company&quot;) con l&#39;attributo **xlink** e un campo della tabella (&quot;email&quot;):

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Schema generato:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La definizione della chiave del nome &quot;companyEmail&quot; è stata estesa con la chiave esterna del collegamento &quot;company&quot;. Questa chiave genera un indice univoco su entrambi i campi.
