---
product: campaign
title: Informazioni sulla modifica degli schemi
description: Guida introduttiva all’edizione dello schema
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 7%

---

# Informazioni sulla modifica degli schemi{#about-schema-edition}

Adobe Campaign utilizza gli schemi di dati per:

* Definire il modo in cui gli oggetti dati all’interno dell’applicazione sono legati alle tabelle del database sottostanti.
* Definire i collegamenti tra i diversi oggetti dati all’interno dell’applicazione Campaign.
* Definire e descrivere i singoli campi inclusi in ciascun oggetto.

Per una migliore comprensione delle tabelle integrate di Campaign e della loro interazione, consulta [questa sezione](https://helpx.adobe.com/it/campaign/kb/acc-datamodel.html).

## Estensione o creazione di schemi {#extending-or-creating-schemas}

Per aggiungere un campo o un indice o un altro elemento a uno degli schemi di dati principali in Campaign, ad esempio la tabella dei destinatari (nms:recipient), devi estendere tale schema. Per ulteriori informazioni, consulta la sezione [Estensione di uno schema](../../configuration/using/extending-a-schema.md) .

Per aggiungere un tipo completamente nuovo di dati che non esistono preconfigurati in Adobe Campaign (ad esempio, una tabella di contratti), puoi creare direttamente uno schema personalizzato. Per ulteriori informazioni, consulta la sezione [Schemi di dati](../../configuration/using/data-schemas.md) .

![](assets/schemaextension_getting_started_1.png)

Dopo aver esteso o creato uno schema in cui lavorare, la procedura consigliata è quella di definirne gli elementi di contenuto XML nello stesso ordine in cui compaiono di seguito.

## Enumerazioni {#enumerations}

Le enumerazioni sono definite per prime, prima dell&#39;elemento principale dello schema. Consentono di visualizzare i valori in un elenco al fine di limitare le scelte disponibili per un dato campo.

Esempio:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Quando definisci i campi, puoi quindi utilizzare questa enumerazione nel modo seguente:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>È inoltre possibile utilizzare enumerazioni gestite dall’utente (in genere in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) per specificare i valori di un dato campo. Si tratta di enumerazioni globali efficaci e di una scelta migliore se l’enumerazione può essere utilizzata al di fuori dello schema specifico in cui si sta lavorando.

Per ulteriori informazioni sulle enumerazioni, consulta le sezioni [Enumerazioni](../../configuration/using/schema-structure.md#enumerations) e [`<enumeration>` element](../../configuration/using/schema/enumeration.md) .

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

L&#39;attributo **xpath** punta al campo nello schema che desideri indicizzare.

>[!IMPORTANT]
>
>È importante ricordare che i miglioramenti delle prestazioni di lettura della query SQL forniti dagli indici hanno anche un risultato sulle prestazioni durante la scrittura di record. Gli indici devono pertanto essere utilizzati con cautela.

Per ulteriori informazioni sugli indici, consulta la sezione [Campi indicizzati](../../configuration/using/database-mapping.md#indexed-fields) .

## Chiavi {#keys}

Ogni tabella deve avere almeno una chiave e spesso viene stabilita automaticamente nell&#39;elemento principale dello schema utilizzando l&#39;attributo **@autopk=true** impostato su &quot;true&quot;.

La chiave primaria può essere definita anche utilizzando l&#39;attributo **internal** .

Esempio:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

In questo esempio, invece di lasciare che l&#39;attributo **@autopk** crei una chiave primaria predefinita denominata &quot;id&quot;, stiamo specificando la nostra chiave primaria &quot;familyId&quot;.

>[!IMPORTANT]
>
>Durante la creazione di un nuovo schema o durante un&#39;estensione dello schema, è necessario mantenere lo stesso valore di sequenza della chiave primaria (@pkSequence) per l&#39;intero schema.

Per ulteriori informazioni sulle chiavi, consulta la sezione [Gestione delle chiavi](../../configuration/using/database-mapping.md#management-of-keys) .

## Attributi (campi) {#attributes--fields-}

Gli attributi ti consentono di definire i campi che compongono l’oggetto dati. Puoi usare il pulsante **[!UICONTROL Insert]** nella barra degli strumenti dell’edizione dello schema per rilasciare modelli di attributi vuoti nel file XML in cui si trova il cursore. Per ulteriori informazioni, consulta la sezione [Schemi di dati](../../configuration/using/data-schemas.md) .

![](assets/schemaextension_getting_started_2.png)

L’elenco completo degli attributi è disponibile nella sezione [`<attribute>` element](../../configuration/using/schema/attribute.md) . Di seguito sono riportati alcuni degli attributi più comunemente utilizzati:

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
* **@required**
* **@ref**
* **@xml**
* **@type**

   Per visualizzare una tabella in cui sono elencate le mappature dei tipi di dati generati da Adobe Campaign per i diversi sistemi di gestione del database, consulta la sezione [Mappatura dei tipi di dati Adobe Campaign/DBMS](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) .

Per ulteriori informazioni su ciascun attributo, consulta la sezione [Descrizione attributo](../../configuration/using/schema/attribute.md) .

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

Esempio di campo XML memorizzato anche in un campo SQL e con un attributo **@dataPolicy**.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Sebbene la maggior parte degli attributi siano collegati in base a una cardinalità 1-1 a un campo fisico del database, ciò non avviene per i campi XML o i campi calcolati.\
>Un campo XML viene memorizzato in un campo Memo (&quot;mData&quot;) della tabella.\
>Un campo calcolato viene tuttavia creato dinamicamente ogni volta che viene avviata una query, quindi esiste solo nel livello applicativo.

## Collegamenti {#links}

I collegamenti sono alcuni degli ultimi elementi nell’elemento principale dello schema. Definiscono il modo in cui tutti i diversi schemi nella tua istanza si relazionano tra loro.

I collegamenti sono dichiarati nello schema che contiene la **chiave esterna** della tabella a cui è collegata.

Ci sono tre tipi di cardinalità: 1-1, 1-N e N-N. È il tipo 1-N utilizzato per impostazione predefinita.

### Esempi {#examples-1}

Esempio di collegamento 1-N tra la tabella dei destinatari (schema predefinito) e una tabella delle transazioni personalizzate:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Esempio di collegamento 1-1 tra uno schema personalizzato &quot;Car&quot; (nello spazio dei nomi &quot;cus&quot;) e la tabella dei destinatari:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Esempio di join esterno tra la tabella dei destinatari e una tabella di indirizzi basata sull’indirizzo e-mail e non su una chiave primaria:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Qui &quot;xpath-dst&quot; corrisponde alla chiave primaria nello schema di destinazione e &quot;xpath-src&quot; corrisponde alla chiave esterna nello schema di origine.

## Audit trail {#audit-trail}

Un elemento utile da includere nella parte inferiore dello schema è un elemento di tracciamento (Audit trail).

Utilizza l’esempio seguente per includere i campi relativi alla data di creazione, all’utente che ha creato i dati, alla data e all’autore dell’ultima modifica per tutti i dati nella tabella:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Aggiornamento della struttura del database {#updating-the-database-structure}

Una volta completate e salvate le modifiche, tutte le modifiche che possono influire sulla struttura SQL devono essere applicate al database. A questo scopo, utilizzare la procedura guidata di aggiornamento del database.

![](assets/schemaextension_getting_started_3.png)

Per ulteriori informazioni, consulta la sezione [Aggiornamento della struttura del database](../../configuration/using/updating-the-database-structure.md).

>[!NOTE]
>
>Quando le modifiche non influiscono sulla struttura del database, è sufficiente rigenerare gli schemi. A questo scopo, seleziona gli schemi da aggiornare, fai clic con il pulsante destro del mouse e scegli **[!UICONTROL Actions > Regenerate selected schemas...]** . Per ulteriori informazioni, consulta la sezione [Rigenerazione degli schemi](../../configuration/using/regenerating-schemas.md) .
