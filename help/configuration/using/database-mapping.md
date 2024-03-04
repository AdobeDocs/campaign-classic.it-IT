---
product: campaign
title: Mappatura del database
description: Mappatura del database
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: bd1007ffcfa58ee60fdafa424c7827e267845679
workflow-type: tm+mt
source-wordcount: '1984'
ht-degree: 0%

---

# Mappatura del database{#database-mapping}

Mapping SQL dello schema di esempio descritto [in questa pagina](schema-structure.md) genera il seguente documento XML:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Descrizione {#description}

Elemento principale dello schema modificato in **`<srcschema>`** a **`<schema>`**.

Questo altro tipo di documento viene generato automaticamente dallo schema di origine e viene semplicemente indicato come schema.

I nomi SQL vengono determinati automaticamente in base al nome e al tipo dell&#39;elemento.

Le regole di denominazione SQL sono le seguenti:

* **tabella**: concatenazione dello spazio dei nomi e del nome dello schema

  Nel nostro esempio, il nome della tabella viene immesso tramite l’elemento principale dello schema nel **sqltable** attributo:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **campo**: nome dell’elemento preceduto da un prefisso definito secondo il tipo: &quot;i&quot; per il numero intero, &quot;d&quot; per il numero doppio, &quot;s&quot; per la stringa, &quot;ts&quot; per le date, ecc.

  Il nome del campo viene immesso tramite **sqlname** attributo per ogni tipo **`<attribute>`** e **`<element>`**:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>I nomi SQL possono essere sovraccaricati dallo schema di origine. A questo scopo, compila gli attributi &quot;sqltable&quot; o &quot;sqlname&quot; sull’elemento interessato.

Lo script SQL per creare la tabella generata dallo schema esteso è il seguente:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

I vincoli del campo SQL sono i seguenti:

* nessun valore nullo nei campi numerici e di data
* i campi numerici sono inizializzati a 0

## Campi XML {#xml-fields}

Per impostazione predefinita, qualsiasi  **`<attribute>`** e **`<element>`** L&#39;elemento tipizzato da è mappato su un campo SQL della tabella dello schema di dati. È tuttavia possibile fare riferimento a questo campo in formato XML anziché in formato SQL, il che significa che i dati vengono memorizzati in un campo Memo (&quot;mData&quot;) della tabella contenente i valori di tutti i campi XML. La memorizzazione di questi dati è un documento XML che osserva la struttura dello schema.

Per compilare un campo in XML, è necessario aggiungere **xml** con il valore &quot;true&quot; all&#39;elemento interessato.

**Esempio**: ecco due esempi di utilizzo dei campi XML.

* Campo commento su più righe:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Descrizione dei dati in formato HTML:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  Il tipo &quot;html&quot; consente di memorizzare il contenuto HTML in un tag CDATA e di visualizzare uno speciale controllo di modifica HTML nell’interfaccia client di Adobe Campaign.

Utilizzare i campi XML per aggiungere nuovi campi senza modificare la struttura fisica del database. Un altro vantaggio consiste nell&#39;utilizzo di meno risorse (dimensioni allocate ai campi SQL, limite al numero di campi per tabella, ecc.). Si noti tuttavia che non è possibile indicizzare o filtrare un campo XML.

## Campi indicizzati {#indexed-fields}

Gli indici consentono di ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione.

Un indice viene dichiarato dall’elemento principale dello schema di dati.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Gli indici rispettano le regole seguenti:

* Un indice può fare riferimento a uno o più campi nella tabella
* Un indice può essere univoco (per evitare duplicati) in tutti i campi se **univoco** contiene il valore &quot;true&quot;
* Il nome SQL dell&#39;indice è determinato dal nome SQL della tabella e dal nome dell&#39;indice

>[!NOTE]
>
>* Come standard, gli indici sono i primi elementi dichiarati dall’elemento principale dello schema.
>
>* Gli indici vengono creati automaticamente durante la mappatura delle tabelle (standard o FDA).

**Esempio**:

* Aggiunta di un indice all’indirizzo e-mail e alla città:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Aggiunta di un indice univoco al campo del nome &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Gestione delle chiavi {#management-of-keys}

Una tabella deve avere almeno una chiave per identificare un record nella tabella.

Una chiave viene dichiarata dall’elemento principale dello schema di dati.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Le seguenti regole si applicano alle chiavi:

* Una chiave può fare riferimento a uno o più campi della tabella
* Una chiave è nota come &quot;primaria&quot; (o &quot;priorità&quot;) quando è la prima dello schema a essere compilata o se contiene **interno** con il valore &quot;true&quot;
* Un indice univoco viene dichiarato in modo implicito per ogni definizione di chiave. La creazione di un indice sulla chiave può essere impedita aggiungendo il **noDbIndex** con il valore &quot;true&quot;

>[!NOTE]
>
>* Come standard, le chiavi sono gli elementi dichiarati dall’elemento principale dello schema dopo la definizione degli indici.
>
>* Le chiavi vengono create durante la mappatura della tabella (standard o FDA), Adobe Campaign trova indici univoci.

**Esempio**:

* Aggiunta di una chiave all’indirizzo e-mail e alla città:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  Lo schema generato:

  ```sql
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
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Aggiunta di una chiave primaria o interna nel campo del nome &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  Lo schema generato:

  ```sql
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
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

### Tasto incrementale automatico {#auto-incremental-key}

La chiave primaria della maggior parte delle tabelle di Adobe Campaign è un numero intero a 32 bit generato automaticamente dal motore di database. Il calcolo del valore chiave dipende da una sequenza (per impostazione predefinita, il **XtkNewId** funzione SQL) che genera un numero univoco nell&#39;intero database. Il contenuto della chiave viene immesso automaticamente all’inserimento del record.

Il vantaggio di una chiave incrementale è che fornisce una chiave tecnica non modificabile per i join tra tabelle. Inoltre, questa chiave non occupa molta memoria perché utilizza un numero intero a doppio byte.

È possibile specificare nello schema di origine il nome della sequenza da utilizzare con **pkSequence** attributo. Se questo attributo non è specificato nello schema di origine, **XtkNewId** verrà utilizzata la sequenza predefinita. L&#39;applicazione utilizza sequenze dedicate per **nms:broadLog** e **nms:trackingLog** schemi (**NmsBroadLogId** e **NmsTrackingLogId** rispettivamente) perché queste sono le tabelle che contengono il maggior numero di record.

ACC 18.10, **XtkNewId** non è più il valore predefinito per la sequenza negli schemi predefiniti. Ora puoi creare uno schema o estendere uno schema esistente con una sequenza dedicata.

>[!IMPORTANT]
>
>Quando crei un nuovo schema o durante un’estensione dello schema, devi mantenere lo stesso valore di sequenza di chiave primaria (@pkSequence) per l’intero schema.

>[!NOTE]
>
>Una sequenza a cui si fa riferimento in uno schema di Adobe Campaign (**NmsTrackingLogId** ad esempio) deve essere associata a una funzione SQL che restituisce il numero di ID nei parametri, separati da virgole. Questa funzione deve essere chiamata **GetNew** XXX **Id**, dove **XXX** è il nome della sequenza (**GetNewNmsTrackingLogIds** ad esempio). Visualizza **postgres-nms.sql**, **mssql-nms.sql** o **oracle-nms.sql** file forniti con l&#39;applicazione in **datakit/nms/eng/sql/** per recuperare l&#39;esempio di creazione di una sequenza &#39;NmsTrackingLogId&#39; per ciascun motore di database.

Per dichiarare una chiave univoca, compila il **autopk** (con valore &quot;true&quot;) sull’elemento principale dello schema di dati.

**Esempio**:

Dichiarazione di una chiave incrementale nello schema di origine:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Lo schema generato:

```sql
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
>Un record con una chiave primaria impostata su 0 viene inserito automaticamente al momento della creazione della tabella. Questo record viene utilizzato per evitare outer join che non sono validi per le tabelle dei volumi. Per impostazione predefinita, tutte le chiavi esterne sono inizializzate con il valore 0, in modo che un risultato possa sempre essere restituito sul join quando l&#39;elemento dati non viene popolato.

## Collegamenti: relazione tra tabelle {#links--relation-between-tables}

Un collegamento descrive l’associazione tra una tabella e un’altra.

I vari tipi di associazioni (note come &quot;cardinalità&quot;) sono i seguenti:

* Cardinalità 1-1: una occorrenza della tabella sorgente può avere al massimo una occorrenza corrispondente della tabella di destinazione.
* Cardinalità 1-N: una occorrenza della tabella sorgente può avere diverse occorrenze corrispondenti della tabella di destinazione, ma una occorrenza della tabella di destinazione può avere al massimo una occorrenza corrispondente della tabella sorgente.
* Cardinalità N-N: una occorrenza della tabella sorgente può avere diverse occorrenze corrispondenti della tabella di destinazione e viceversa.

Nell’interfaccia, è possibile distinguere facilmente i diversi tipi di relazioni grazie alle relative icone.

Per le relazioni di join con una tabella o un database di Campaign:

* ![](assets/join_with_campaign11.png) Cardinalità 1-1. Ad esempio, tra un destinatario e un ordine corrente. Un destinatario può essere correlato a una sola occorrenza della tabella dell&#39;ordine corrente alla volta.
* ![](assets/externaljoin11.png) : Cardinalità 1-1, join esterno. Ad esempio, tra un destinatario e il suo paese. Un destinatario può essere correlato a una sola occorrenza del paese della tabella. Il contenuto della country table non verrà salvato.
* ![](assets/join_with_campaign1n.png) : Cardinalità 1-N. Ad esempio, tra un destinatario e la tabella delle sottoscrizioni. Un destinatario può essere correlato a diverse occorrenze nella tabella delle sottoscrizioni.

Per le relazioni di join che utilizzano Federated Database Access:

* ![](assets/join_fda_11.png) : Cardinalità 1-1
* ![](assets/join_fda_1m.png) : Cardinalità 1-N

Per ulteriori informazioni sulle tabelle FDA, consulta [Accesso a un database esterno](../../installation/using/about-fda.md).

È necessario dichiarare un collegamento nello schema contenente la chiave esterna della tabella collegata tramite l’elemento principale:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

I collegamenti rispettano le seguenti regole:

* La definizione di un collegamento viene immessa su un **link**-type **`<element>`** con i seguenti attributi:

   * **nome**: nome del collegamento dalla tabella di origine,
   * **destinazione**: nome dello schema di destinazione,
   * **etichetta**: etichetta del collegamento,
   * **revLink** (facoltativo): nome del collegamento inverso dallo schema di destinazione (dedotto automaticamente per impostazione predefinita),
   * **integrità** (facoltativo): integrità referenziale dell’occorrenza della tabella sorgente rispetto all’occorrenza della tabella di destinazione. I valori possibili sono i seguenti:

      * **definire**: è possibile eliminare l’occorrenza sorgente se un’occorrenza target non vi fa più riferimento,
      * **normale**: l’eliminazione dell’occorrenza sorgente inizializza le chiavi del collegamento all’occorrenza target (modalità predefinita); questo tipo di integrità inizializza tutte le chiavi esterne,
      * **proprio**: l’eliminazione dell’occorrenza sorgente determina l’eliminazione dell’occorrenza target,
      * **owncopy**: uguale a **proprio** (in caso di eliminazione) o duplica le occorrenze (in caso di duplicazione),
      * **neutro**: non esegue alcuna operazione.

   * **revIntegrity** (facoltativo): integrità nello schema di destinazione (opzionale, &quot;normale&quot; per impostazione predefinita),
   * **revCardinality** (facoltativo): con il valore &quot;single&quot; compila la cardinalità con il tipo 1-1 (1-N per impostazione predefinita).
   * **externalJoin** (facoltativo): forza l’outer join
   * **revExternalJoin** (facoltativo): forza il join esterno sul collegamento inverso

* Un collegamento fa riferimento a uno o più campi dalla tabella di origine alla tabella di destinazione. Campi che compongono il join ( `<join>`  element) non devono essere compilati perché vengono automaticamente dedotti per impostazione predefinita utilizzando la chiave interna dello schema di destinazione.
* Un indice viene aggiunto automaticamente alla chiave esterna del collegamento nello schema esteso.
* Un collegamento è costituito da due collegamenti intermedi, in cui il primo viene dichiarato dallo schema di origine e il secondo viene creato automaticamente nello schema esteso dello schema di destinazione.
* Un join può essere un outer join se **externalJoin** con il valore &quot;true&quot; (supportato in PostgreSQL).

>[!NOTE]
>
>Come standard, i collegamenti sono gli elementi dichiarati alla fine dello schema.

### Esempio 1 {#example-1}

Relazione 1-N con la tabella dello schema &quot;cus:company&quot;:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Lo schema generato:

```sql
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

La definizione del collegamento è completata dai campi che compongono il join, ovvero la chiave primaria con il relativo XPath (&quot;@id&quot;) nello schema di destinazione e la chiave esterna con il relativo XPath (&quot;@company-id&quot;) nello schema.

La chiave esterna viene aggiunta automaticamente in un elemento che utilizza le stesse caratteristiche del campo associato nella tabella di destinazione, con la seguente convenzione di denominazione: nome dello schema di destinazione seguito dal nome del campo associato (&quot;company-id&quot; nel nostro esempio).

Schema esteso del target (&quot;cus:company&quot;):

```sql
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

È stato aggiunto un collegamento inverso alla tabella &quot;cus:recipient&quot; con i seguenti parametri:

* **nome**: dedotto automaticamente dal nome dello schema di origine (può essere forzato con l’attributo &quot;revLink&quot; nella definizione del collegamento nello schema di origine)
* **revLink**: nome del collegamento inverso
* **destinazione**: chiave dello schema collegato (schema &quot;cus:recipient&quot;)
* **non associato**: il collegamento viene dichiarato come elemento di raccolta per una cardinalità 1-N (per impostazione predefinita)
* **integrità**: &quot;define&quot; per impostazione predefinita (può essere forzato con l’attributo &quot;revIntegrity&quot; nella definizione del collegamento nello schema di origine).

### Esempio 2 {#example-2}

In questo esempio, dichiareremo un collegamento verso la tabella dello schema &quot;nms:address&quot;. Il join è un outer join e viene compilato esplicitamente con l&#39;indirizzo e-mail del destinatario e il campo &quot;@address&quot; della tabella collegata (&quot;nms:address&quot;).

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Esempio 3 {#example-3}

1-1 relazione con la tabella dello schema &quot;cus:extension&quot;:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Esempio 4 {#example-4}

Collegamento a una cartella (schema &quot;xtk:folder&quot;):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Il valore predefinito restituisce l&#39;identificatore del primo file del tipo di parametro idoneo immesso nella funzione &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

### Esempio 5 {#example-5}

In questo esempio, vogliamo creare una chiave su un collegamento (schema &quot;company&quot; to &quot;cus:company&quot;) con **xlink** e un campo della tabella (&quot;email&quot;):

```sql
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

Lo schema generato:

```sql
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

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La definizione della chiave del nome &quot;companyEmail&quot; è stata estesa con la chiave esterna del collegamento &quot;company&quot;. Questa chiave genera un indice univoco su entrambi i campi.
