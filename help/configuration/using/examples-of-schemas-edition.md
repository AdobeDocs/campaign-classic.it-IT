---
product: campaign
title: Esempi di modifica degli schemi
description: Esempi di modifica degli schemi
exl-id: b7ee70e0-89c6-4cd3-8116-2f073d4a2f2f
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 2%

---


# Esempi di modifica degli schemi{#examples-of-schemas-edition}

![](../../assets/v7-only.svg)

## Estendere una tabella {#extending-a-table}

Per estendere **nms:recipient** tabella dei destinatari dello schema, applicare la procedura seguente:

1. Crea lo schema dell&#39;estensione (**cus:extension**) utilizzando i dati seguenti:

   ```
   <srcSchema mappingType="sql" name="extension" namespace="cus" xtkschema="xtk:srcSchema" extendedSchema="nms:recipient">  
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>  
   
     <element name="extension">    
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>      
   
       <attribute label="Loyalty code" name="fidelity" type="long"/>    
       <element name="location">      
         <attribute name="area" label="Purchasing zone" type="string" length="50" enum="area"/>    
       </element>  </element>  
   </srcSchema>
   ```

   In questo esempio, un campo indicizzato (**fedeltà**) viene aggiunta e la **posizione** elemento (già presente nel **nms:recipient** schema) è completato da un campo enumerato (**area**).

   >[!IMPORTANT]
   >
   >Ricorda di aggiungere **ExtendedSchema** per fare riferimento allo schema dell&#39;estensione.

1. Controlla che lo schema esteso sia il **nms:recipient** schema e la presenza di dati aggiuntivi:

   ```
   <schema dependingSchemas="cus:extension" mappingType="sql" name="recipient" namespace="nms" xtkschema="xtk:schema">
     ...
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>
     ...
     <element autopk="true" name="recipient" sqltable="NmsRecipient"> 
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>
   
       ...
       <attribute belongsTo="cus:extension" label="Loyalty code" name="fidelity" sqlname="iFidelity" type="long"/>
       <element name="location">
         ...
         <attribute enum="area" label="Purchasing zone" length="50" name="area" sqlname="sArea" type="string"/>
       </element>
       ...
     </element>
   </schema>
   ```

   Lo script SQL generato dalla procedura guidata di aggiornamento del database è il seguente:

   ```
   ALTER TABLE NmsRecipient ADD iFidelity INTEGER;
   UPDATE NmsRecipient SET iFidelity = 0;
   ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET NOT NULL;ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET Default 0;
   ALTER TABLE NmsRecipient ADD sArea VARCHAR(50); 
   CREATE INDEX NmsRecipient_area ON NmsRecipient(sArea);
   ```

## Tabella raccolta collegata {#linked-collection-table}

Questa sezione descrive come creare una tabella dell’ordine collegata alla tabella dei destinatari con cardinalità 1-N.

Schema origine tabella ordine:

```
<srcSchema label="Order" name="order" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="order">    
    <compute-string expr="@number" + '(' + ToString(@date) + ')'/>    
    
    <attribute label="Number" length="128" name="number" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" type="datetime" default="GetDate()"/>    
    <attribute desc="order total" label="Total" name="total" type="double"/>    
    <element label="Recipient" name="recipient" revDesc="Orders associated with this recipient" revIntegrity="own" revLabel="Orders" target="nms:recipient" type="link"/>  
  </element>
</srcSchema>
```

Il tipo di tabella è **autopk** per creare una chiave primaria generata automaticamente che deve essere utilizzata dal join del collegamento alla tabella dei destinatari.

Schema generato:

```
<schema label="Order" mappingType="sql" name="order" namespace="cus" xtkschema="xtk:schema">  
  <element autopk="true" label="Order" name="order" sqltable="CusOrder">    
    <compute-string expr="ToString(@date) + ' - ' + @number"/>    

    <dbindex name="id" unique="true">      
      <keyfield xpath="@id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>    

    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iOrderId" type="long"/>    
    <attribute label="Number" length="128" name="number" sqlname="sNumber" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" sqlname="tsDate" type="datetime"/>    
    <attribute desc="order total" label="Total" name="total" sqlname="Total" type="double"/>    
    <element label="Recipient" name="recipient" revLink="order" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>  
   </element>
</schema>
```

Lo script SQL per la creazione della tabella è il seguente:

```
CREATE TABLE CusOrder(dTotal DOUBLE PRECISION NOT NULL Default 0, iOrderId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, sNumber VARCHAR(128), tsDate TIMESTAMP Default NULL);
CREATE UNIQUE INDEX CusOrder_id ON CusOrder(iOrderId);
CREATE INDEX CusOrder_recipientId ON CusOrder(iRecipientId);  
INSERT INTO CusOrder (iOrderId) VALUES (0); 
```

>[!NOTE]
>
>Il comando SQL INSERT INTO alla fine dello script consente di inserire un record di identificazione impostato su 0 per simulare i join esterni.

## Tabella delle estensioni {#extension-table}

Una tabella di estensione consente di estendere il contenuto di una tabella esistente in una tabella collegata di cardinalità 1-1.

Lo scopo di una tabella di estensione è quello di evitare limitazioni al numero di campi supportati in una tabella o di ottimizzare lo spazio occupato dai dati, che viene utilizzato su richiesta.

Creazione dello schema della tabella di estensione (**cus:feature**):

```
<srcSchema mappingType="sql" name="feature" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="feature">    
    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
  </element>
</srcSchema>
```

Creazione di uno schema di estensione nella tabella dei destinatari per aggiungere il collegamento della cardinalità 1-1:

```
<srcSchema extendedSchema="nms:recipient" label="Recipient" mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="recipient">    
    <element desc="Features" integrity="own" label="Features" name="feature" revCardinality="single" revLink="recipient" target="cus:feature" type="link"/> 
  </element>
</srcSchema>
```

>[!NOTE]
>
>La definizione del collegamento tra la tabella dei destinatari e la tabella delle estensioni deve essere compilata dallo schema contenente la chiave esterna.

Lo script SQL per la creazione della tabella di estensione è il seguente:

```
CREATE TABLE CusFeature(  iChildren NUMERIC(3) NOT NULL Default 0, iFeatureId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusFeature_id ON CusFeature(iFeatureId);  
INSERT INTO CusFeature (iFeatureId) VALUES (0); 
```

Lo script di aggiornamento SQL della tabella dei destinatari è il seguente:

```
ALTER TABLE NmsRecipient ADD iFeatureId INTEGER;
UPDATE NmsRecipient SET iFeatureId = 0;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET NOT NULL;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET Default 0;
CREATE INDEX NmsRecipient_featureId ON NmsRecipient(iFeatureId);
```

## Tabella di overflow {#overflow-table}

Una tabella di overflow è una tabella di estensione (cardinalità 1-1), ma la dichiarazione del collegamento alla tabella da estendere è compilata nello schema della tabella di overflow.

La tabella di overflow contiene la chiave esterna della tabella da estendere. La tabella da estendere non è pertanto modificata. La relazione tra le due tabelle è il valore della chiave primaria della tabella da estendere.

Creazione dello schema della tabella di overflow (**cus:overflow**):

```
<srcSchema label="Overflow" name="overflow" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="overflow">    
    <key internal="true" name="id">      
      <keyfield xlink="recipient"/>    
    </key>    

    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
    <element label="Customer" name="recipient" revCardinality="single" revIntegrity="own" revExternalJoin="true" target="nms:recipient" type="link"/>  
  </element>  
</srcSchema>
```

>[!NOTE]
>
>La chiave primaria della tabella di overflow è il collegamento alla tabella da estendere ( schema &quot;nms:recipient&quot; nel nostro esempio).

Lo script SQL per la creazione della tabella è il seguente:

```
CREATE TABLE CusOverflow(iChildren NUMERIC(3) NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusOverflow2_id ON CusOverflow2(iRecipientId);  
```

## Tabella di relazione {#relationship-table}

Una tabella di relazione consente di collegare due tabelle con cardinalità N-N. Questa tabella contiene solo le chiavi esterne delle tabelle da collegare.

Esempio di tabella di relazione tra gruppi (**nms:group**) e i destinatari (**nms:recipient**).

Schema di origine della tabella delle relazioni:

```
<srcSchema name="rcpGrpRel" namespace="cus">
  <element name="rcpGrpRel">
    <key internal="true" name="id">      
      <keyfield xlink="rcpGroup"/>      
      <keyfield xlink="recipient"/>    
    </key>

    <element integrity="neutral" label="Recipient" name="recipient" revDesc="Groups to which this recipient belongs" revIntegrity="own" revLabel="Groups" target="nms:recipient" type="link"/>    
    <element integrity="neutral" label="Group" name="rcpGroup" revDesc="Recipients in the group" revIntegrity="own" revLabel="Recipients" revLink="rcpGrpRel" target="nms:group" type="link"/>
  </element>
</srcSchema>
```

Lo schema generato è il seguente:

```
<schema mappingType="sql" name="rcpGrpRel" namespace="cus" xtkschema="xtk:schema">  
  <element name="rcpGrpRel" sqltable="CusRcpGrpRel">    
    <compute-string expr="ToString([@rcpGroup-id]) + ',' + ToString([@recipient-id])"/>    
    <dbindex name="id" unique="true">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </key>    

    <dbindex name="rcpGroupId">      
      <keyfield xpath="@rcpGroup-id"/>    
    </dbindex>    
    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <element integrity="neutral" label="Recipient" name="recipient" revLink="rcpGrpRel" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>    

    <element integrity="neutral" label="Group" name="rcpGroup" revLink="rcpGrpRel" target="nms:group" type="link">      
      <join xpath-dst="@id" xpath-src="@rcpGroup-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Group' link ('id' field)" name="rcpGroup-id" sqlname="iRcpGroupId" type="long"/>  
  </element>
</schema>
```

Lo script SQL per la creazione della tabella è il seguente:

```
CREATE TABLE CusRcpGrpRel( iRcpGroupId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0);
CREATE UNIQUE INDEX CusRcpGrpRel_id ON CusRcpGrpRel(iRcpGroupId, iRecipientId);
CREATE INDEX CusRcpGrpRel_recipientId ON CusRcpGrpRel(iRecipientId);
```

## Caso d’uso: collegare un campo a una tabella di riferimento esistente {#uc-link}

Questo caso d’uso illustra come utilizzare una tabella di riferimento esistente come alternativa ai meccanismi di enumerazione incorporati di Adobe Campaign (enum, userEnum o dbEnum).

È inoltre possibile utilizzare una tabella di riferimento esistente come enumerazione negli schemi. Questo può essere ottenuto creando un collegamento tra una tabella e la tabella di riferimento e aggiungendo l’attributo **displayAsField=&quot;true&quot;**.

In questo esempio, la tabella di riferimento contiene un elenco di nomi e identificatori bancari:

```
<srcSchema entitySchema="xtk:srcSchema" img="cus:bank16x16.png" label="Bank" mappingType="sql" name="bank" namespace="cus"
xtkschema="xtk:srcSchema">
    <element img="cus:bank16x16.png" label="Banks" name="bank">
        <compute-string expr="@name"/>
        <key name="id">
            <keyfield xpath="@id"/>
        </key>
        <attribute label="Bank Id" name="id" type="short"/>
        <attribute label="Name" length="64" name="name" type="string"/>
     </element> 
</srcSchema>
```

In qualsiasi tabella che utilizzi questa tabella di riferimento, definisci un collegamento e aggiungi la **displayAsField=&quot;true&quot;** attributo.

```
<element displayAsField="true" label="Bank" name="bank" target="cus:bank" type="link" noDbIndex="true"/>
```

L’interfaccia utente non visualizza un collegamento, ma un campo. Quando gli utenti selezionano quel campo, possono selezionare un valore dalla tabella di riferimento o utilizzare la funzione di completamento automatico.

![](assets/schema-edition-ex.png)

* Per completare automaticamente la stringa, è necessario definire una stringa di calcolo nella tabella di riferimento.

* Aggiungi il **noDbIndex=&quot;true&quot;** nella definizione del collegamento per impedire ad Adobe Campaign di creare un indice sui valori memorizzati nella tabella sorgente del collegamento.

## Argomenti correlati

* [Utilizzo delle enumerazioni](../../platform/using/managing-enumerations.md)

* [Guida introduttiva agli schemi di Campaign](../../configuration/using/about-schema-edition.md)

* [Aggiornamento della struttura del database](../../configuration/using/updating-the-database-structure.md)
