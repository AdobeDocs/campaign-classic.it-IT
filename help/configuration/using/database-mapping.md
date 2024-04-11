---
product: campaign
title: Mappatura del database
description: Mappatura del database
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 3%

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

## Ulteriori informazioni

Per ulteriori informazioni, consulta i seguenti collegamenti:

* [Introduzione agli schemi](about-schema-reference.md)
* [Struttura dello schema](schema-structure.md)
* [Gestione delle chiavi](database-keys.md)
* [Gestione collegamenti](database-links.md)
* [Modello dati di Campaign](about-data-model.md)