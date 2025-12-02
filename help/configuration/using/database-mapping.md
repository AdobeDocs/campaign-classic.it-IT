---
product: campaign
title: Mappatura del database
description: Mappatura del database
feature: Configuration, Instance Settings
role: Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 3%

---

# Mappatura del database{#database-mapping}

Il mapping SQL dello schema di esempio descritto [in questa pagina](schema-structure.md) genera il seguente documento XML:

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

Elemento radice dello schema modificato in **`<srcschema>`** in **`<schema>`**.

Questo altro tipo di documento viene generato automaticamente dallo schema di origine e viene semplicemente indicato come schema.

I nomi SQL vengono determinati automaticamente in base al nome e al tipo dell&#39;elemento.

Le regole di denominazione SQL sono le seguenti:

* **tabella**: concatenazione dello spazio dei nomi e del nome dello schema

  Nel nostro esempio, il nome della tabella viene immesso tramite l&#39;elemento principale dello schema nell&#39;attributo **sqltable**:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **campo**: nome dell&#39;elemento preceduto da un prefisso definito in base al tipo: &#39;i&#39; per numero intero, &#39;d&#39; per doppio, &#39;s&#39; per stringa, &#39;ts&#39; per date e così via.

  Il nome del campo viene immesso tramite l&#39;attributo **sqlname** per ogni tipo di **`<attribute>`** e **`<element>`**:

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

Per impostazione predefinita, qualsiasi elemento digitato **`<attribute>`** e **`<element>`** è mappato su un campo SQL della tabella dello schema di dati. È tuttavia possibile fare riferimento a questo campo in formato XML anziché in formato SQL, il che significa che i dati vengono memorizzati in un campo Memo (&quot;mData&quot;) della tabella contenente i valori di tutti i campi XML. La memorizzazione di questi dati è un documento XML che osserva la struttura dello schema.

Per compilare un campo in XML, è necessario aggiungere l&#39;attributo **xml** con il valore &quot;true&quot; all&#39;elemento interessato.

**Esempio**: di seguito sono riportati due esempi di utilizzo di campi XML.

* Campo commento su più righe:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Descrizione dei dati in formato HTML:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  Il tipo &quot;html&quot; consente di memorizzare il contenuto HTML in un tag CDATA e di visualizzare uno speciale HTML edit check nell’interfaccia client di Adobe Campaign.

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
* Un indice può essere univoco (per evitare duplicati) in tutti i campi se l&#39;attributo **unique** contiene il valore &quot;true&quot;
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

## Ulteriori informazioni

Per ulteriori informazioni, consulta i seguenti collegamenti:

* [Introduzione agli schemi](about-schema-reference.md)
* [Struttura dello schema](schema-structure.md)
* [Gestione delle chiavi](database-keys.md)
* [Gestione collegamenti](database-links.md)
* [Modello dati di Campaign](about-data-model.md)