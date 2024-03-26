---
product: campaign
title: Gestione delle chiavi negli schemi di dati
description: Gestione delle chiavi negli schemi di dati
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 46dcd80d5adc31a66b47c6d75e7914b0a686326b
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 3%

---

# Gestione delle chiavi negli schemi {#management-of-keys}

Ogni tabella associata a uno schema di dati deve avere almeno una chiave per identificare un record in una tabella.

Una chiave viene dichiarata dall’elemento principale dello schema di dati.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Una chiave è nota come &quot;chiave primaria&quot; quando è la prima dello schema a essere compilata, o se contiene `internal` attributo impostato su &quot;true&quot;.

Le seguenti regole si applicano alle chiavi:

* Una chiave può fare riferimento a uno o più campi della tabella
* Un indice univoco viene dichiarato in modo implicito per ogni definizione di chiave. La creazione di un indice sulla chiave può essere impedita impostando `noDbIndex` su &quot;true&quot;.

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

## Tasto incrementale automatico {#auto-incremental-key}

La chiave primaria della maggior parte delle tabelle di Adobe Campaign è un numero intero a 32 bit generato automaticamente dal motore di database. Il calcolo del valore chiave dipende da una sequenza (per impostazione predefinita, il **XtkNewId** funzione SQL) che genera un numero univoco nell&#39;intero database. Il contenuto della chiave viene immesso automaticamente all’inserimento del record.

Il vantaggio di una chiave incrementale è che fornisce una chiave tecnica non modificabile per i join tra tabelle. Inoltre, questa chiave non occupa molta memoria perché utilizza un numero intero a doppio byte.

È possibile specificare nello schema di origine il nome della sequenza da utilizzare con **pkSequence** attributo. Se questo attributo non è specificato nello schema di origine, **XtkNewId** verrà utilizzata la sequenza predefinita. L&#39;applicazione utilizza sequenze dedicate per **nms:broadLog** e **nms:trackingLog** schemi (**NmsBroadLogId** e **NmsTrackingLogId** rispettivamente) perché queste sono le tabelle che contengono il maggior numero di record.

ACC 18.10, **XtkNewId** non è più il valore predefinito per la sequenza negli schemi predefiniti. Ora puoi creare uno schema o estendere uno schema esistente con una sequenza dedicata.

>[!IMPORTANT]
>
>Quando crei un nuovo schema o durante un’estensione dello schema, devi mantenere lo stesso valore di sequenza di chiave primaria (@pkSequence) per l’intero schema.

Una sequenza a cui si fa riferimento in uno schema di Adobe Campaign (**NmsTrackingLogId** ad esempio) deve essere associata a una funzione SQL che restituisce il numero di ID nei parametri, separati da virgole. Questa funzione deve essere chiamata **GetNew** XXX **Id**, dove **XXX** è il nome della sequenza (**GetNewNmsTrackingLogIds** ad esempio). Visualizza **postgres-nms.sql**, **mssql-nms.sql** o **oracle-nms.sql** file forniti con l&#39;applicazione in **datakit/nms/eng/sql/** per recuperare l&#39;esempio di creazione di una sequenza &#39;NmsTrackingLogId&#39; per ciascun motore di database.

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


## Ulteriori informazioni

Per ulteriori informazioni, consulta i seguenti collegamenti:

* [Introduzione agli schemi](about-schema-reference.md)
* [Struttura dello schema](schema-structure.md)
* [Mappatura del database](database-mapping.md)
* [Gestione collegamenti](database-links.md)
* [Modello dati di Campaign](about-data-model.md)
