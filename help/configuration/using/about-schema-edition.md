---
title: Informazioni sulla modifica degli schemi
description: Introduzione all'edizione dello schema
page-status-flag: never-activated
uuid: edb4d47d-b507-4d86-9873-ebd5f6acefc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: d5b08e4e-060c-4185-9dac-af270918e2b9
translation-type: tm+mt
source-git-commit: 30eaabba8962c518c734cc4e9ad27065cfe9d467
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 7%

---


# Informazioni sulla modifica degli schemi{#about-schema-edition}

 Adobe Campaign utilizza gli schemi dati per:

* Definire il modo in cui gli oggetti dati all’interno dell’applicazione sono legati alle tabelle del database sottostanti.
* Definire i collegamenti tra i diversi oggetti dati all’interno dell’applicazione Campaign.
* Definire e descrivere i singoli campi inclusi in ciascun oggetto.

Per una migliore comprensione delle tabelle integrate in Campaign e della loro interazione, fai riferimento al modello [dati](https://helpx.adobe.com/it/campaign/kb/acc-datamodel.html)Campaign Classic.

## Estensione o creazione di schemi {#extending-or-creating-schemas}

Per aggiungere un campo o un indice o un altro elemento a uno degli schemi di dati di base in Campaign, come la tabella dei destinatari (nms:destinatario), è necessario estendere tale schema. For more on this, refer to the [Extending a schema](../../configuration/using/extending-a-schema.md) section.

Per aggiungere un tipo completamente nuovo di dati che non esiste out-of-the-box in  Adobe Campaign (ad esempio una tabella di contratti), è possibile creare direttamente uno schema personalizzato. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_1.png)

Dopo aver esteso o creato uno schema in cui lavorare, è consigliabile definirne gli elementi di contenuto XML nello stesso ordine in cui appaiono di seguito.

## Enumerazioni {#enumerations}

Le enumerazioni sono definite per prime, prima dell&#39;elemento principale dello schema. Consentono di visualizzare i valori in un elenco al fine di limitare le scelte che l&#39;utente ha per un dato campo.

Esempio:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Quando si definiscono i campi, è quindi possibile utilizzare questa enumerazione come segue:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>È inoltre possibile utilizzare enumerazioni gestite dall&#39;utente (in genere in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) per specificare i valori per un dato campo. Si tratta di enumerazioni globali efficaci e di una scelta migliore se l&#39;enumerazione può essere utilizzata al di fuori dello schema specifico in uso.

Per ulteriori informazioni sulle enumerazioni, fare riferimento alle sezioni [Enumerazioni](../../configuration/using/schema-structure.md#enumerations) ed [`<enumeration>` elementi](../../configuration/using/elements-and-attributes.md#enumeration--element) .

## Indice {#index}

Gli indici sono i primi elementi dichiarati nell&#39;elemento principale dello schema.

Possono essere univoci o meno e fare riferimento a uno o più campi.

Esempi:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

L&#39;attributo **xpath** punta al campo nello schema che si desidera indicizzare.

>[!IMPORTANT]
>
>È importante tenere presente che i miglioramenti delle prestazioni di lettura della query SQL forniti dagli indici generano anche un hit di prestazioni nella scrittura dei record. È pertanto opportuno utilizzare gli indici con cautela.

Per ulteriori informazioni sugli indici, consultare la sezione [Campi](../../configuration/using/database-mapping.md#indexed-fields) indicizzati.

## Tasti {#keys}

Ogni tabella deve avere almeno una chiave e spesso viene automaticamente stabilita nell&#39;elemento principale dello schema utilizzando l&#39;attributo **@autopk=true** impostato su &quot;true&quot;.

La chiave primaria può essere definita anche utilizzando l&#39;attributo **interno** .

Esempio:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

In questo esempio, invece di consentire all&#39;attributo **@autopk** di creare una chiave primaria predefinita denominata &quot;id&quot;, stiamo specificando la chiave primaria &quot;familyId&quot;.

>[!IMPORTANT]
>
>Durante la creazione di un nuovo schema o durante un&#39;estensione dello schema, è necessario mantenere lo stesso valore di sequenza della chiave primaria (@pkSequence) per l&#39;intero schema.

Per ulteriori informazioni sulle chiavi, consulta la sezione [Gestione delle chiavi](../../configuration/using/database-mapping.md#management-of-keys) .

## Attributi (campi) {#attributes--fields-}

Gli attributi consentono di definire i campi che compongono l&#39;oggetto dati. È possibile utilizzare il **[!UICONTROL Insert]** pulsante nella barra degli strumenti dell&#39;edizione dello schema per rilasciare modelli di attributi vuoti nel codice XML in cui si trova il cursore. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_2.png)

L&#39;elenco completo degli attributi è disponibile nella sezione degli [`<attribute>` elementi](../../configuration/using/elements-and-attributes.md#attribute--element) . Di seguito sono riportati alcuni degli attributi più comunemente utilizzati:

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@requirements**
* **@ref**
* **@xml**
* **@type**

   Per visualizzare una tabella in cui sono elencati i mapping per i tipi di dati generati da  Adobe Campaign per i diversi sistemi di gestione del database, fare riferimento alla sezione [Mapping dei tipi  dati](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) Adobe Campaign/DBMS.

Per ulteriori informazioni su ciascun attributo, fare riferimento alla sezione Descrizione [](../../configuration/using/elements-and-attributes.md#attribute-description) attributo.

### Esempi {#examples}

Esempio di definizione di un valore predefinito:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Esempio di utilizzo di un attributo comune come modello per un campo contrassegnato come obbligatorio:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Esempio di campo calcolato nascosto utilizzando l&#39;attributo **@advanced** :

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Esempio di un campo XML memorizzato anche in un campo SQL con attributo **@dataPolicy** .

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Anche se la maggior parte degli attributi sono collegati in base a una cardinalità 1-1 a un campo fisico del database, ciò non vale per i campi XML o i campi calcolati.\
>Un campo XML è memorizzato in un campo Memo (&quot;mData&quot;) della tabella.\
>Un campo calcolato, tuttavia, viene creato dinamicamente ogni volta che viene avviata una query, pertanto esiste solo nel livello applicativo.

## Collegamenti {#links}

I collegamenti sono alcuni degli ultimi elementi dell&#39;elemento principale dello schema. Definiscono il modo in cui tutti i diversi schemi nell’istanza si relazionano tra loro.

I collegamenti sono dichiarati nello schema che contiene la chiave **** esterna della tabella a cui è collegata.

Esistono tre tipi di cardinalità: 1-1, 1-N e N-N. È il tipo 1-N utilizzato per impostazione predefinita.

### Esempi {#examples-1}

Un esempio di collegamento 1-N tra la tabella del destinatario (schema out-of-the-box) e una tabella di transazioni personalizzate:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Un esempio di collegamento 1-1 tra uno schema personalizzato &quot;Car&quot; (nello spazio dei nomi &quot;cus&quot;) e la tabella del destinatario:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Esempio di partecipazione esterna tra la tabella del destinatario e una tabella di indirizzi basata sull&#39;indirizzo e-mail e non su una chiave primaria:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Qui &quot;xpath-dst&quot; corrisponde alla chiave primaria nello schema di destinazione e &quot;xpath-src&quot; corrisponde alla chiave esterna nello schema di origine.

## Audit trail {#audit-trail}

Un elemento utile da includere nella parte inferiore dello schema è un elemento di tracciamento (traccia di audit).

Utilizzate l&#39;esempio seguente per includere i campi relativi alla data di creazione, all&#39;utente che ha creato i dati, alla data e all&#39;autore dell&#39;ultima modifica per tutti i dati della tabella:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Aggiornamento della struttura del database {#updating-the-database-structure}

Una volta completate e salvate le modifiche, tutte le modifiche che possono influenzare la struttura SQL devono essere applicate al database. A questo scopo, utilizzate la procedura guidata di aggiornamento del database.

![](assets/schemaextension_getting_started_3.png)

Per ulteriori informazioni, consulta la sezione [Aggiornamento della struttura del database](../../configuration/using/updating-the-database-structure.md).

>[!NOTE]
>
>Quando le modifiche non influiscono sulla struttura del database, è sufficiente rigenerare gli schemi. A questo scopo, selezionate gli schemi da aggiornare, fate clic con il pulsante destro del mouse e scegliete **[!UICONTROL Actions > Regenerate selected schemas...]** . For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

