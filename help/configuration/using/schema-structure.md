---
product: campaign
title: Struttura dello schema
description: Struttura dello schema
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 1%

---

# Struttura dello schema{#schema-structure}

![](../../assets/v7-only.svg)

La struttura di base di un `<srcschema>` è il seguente:

```
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

Il documento XML di uno schema dati deve contenere **`<srcschema>`** elemento principale con **name** e **namespace** attributi per popolare il nome dello schema e il relativo spazio dei nomi.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Utilizza il seguente contenuto XML per illustrare la struttura di uno schema di dati:

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Con lo schema di dati corrispondente:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## Descrizione {#description}

Il punto di ingresso dello schema è il suo elemento principale. È facile da identificare perché ha lo stesso nome dello schema e dovrebbe essere l&#39;elemento secondario dell&#39;elemento principale. La descrizione del contenuto inizia con questo elemento.

Nel nostro esempio, l’elemento principale è rappresentato dalla seguente riga:

```
<element name="recipient">
```

Gli elementi **`<attribute>`** e **`<element>`** che seguono l&#39;elemento principale ti consentono di definire le posizioni e i nomi degli elementi dati nella struttura XML.

Nel nostro schema di esempio, questi sono:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Devono essere rispettate le seguenti regole:

* Ogni **`<element>`** e **`<attribute>`** deve essere identificato per nome tramite il **name** attributo.

   >[!IMPORTANT]
   >
   >Il nome dell’elemento deve essere conciso, preferibilmente in inglese, e includere solo caratteri autorizzati in conformità alle regole di denominazione XML.

* Solo **`<element>`** gli elementi possono contenere **`<attribute>`** e **`<element>`** elementi nella struttura XML.
* Un **`<attribute>`** deve avere un nome univoco all&#39;interno di un **`<element>`**.
* L&#39;uso di **`<elements>`** in stringhe di dati su più righe è consigliato.

## Tipi di dati {#data-types}

Il tipo di dati viene immesso tramite il **type** nella **`<attribute>`** e **`<element>`** elementi.

È disponibile un elenco dettagliato nella descrizione del [`<attribute>` elemento](../../configuration/using/schema/attribute.md) e [`<element>` elemento](../../configuration/using/schema/element.md)).

Quando questo attributo non è popolato, **string** è il tipo di dati predefinito, a meno che l’elemento non contenga elementi secondari. Se lo fa, viene utilizzato solo per strutturare gli elementi gerarchicamente (**`<location>`** nel nostro esempio).

I seguenti tipi di dati sono supportati negli schemi:

* **string**: stringa di caratteri. Esempi: un nome, una città, ecc.

   Le dimensioni possono essere specificate tramite il **length** (facoltativo, valore predefinito &quot;255&quot;).

* **booleano**: Campo booleano. Esempio di possibili valori: true/false, 0/1, yes/no, ecc.
* **byte**, **short**, **long**: numeri interi (1 byte, 2 byte, 4 byte). Esempi: un’età, un numero di conto, un numero di punti, ecc.
* **double**: numero a virgola mobile a doppia precisione. Esempi: un prezzo, un tasso, ecc.
* **date**, **datetime**: date e date + ore. Esempi: una data di nascita, una data di acquisto, ecc.
* **datetimenotz**: data + ora senza dati sul fuso orario.
* **timespan**: durate. Esempio: anzianità.
* **promemoria**: campi di testo lunghi (righe multiple). Esempi: una descrizione, un commento, ecc.
* **uuid**: Campi &quot;uniqueidentifier&quot; per supportare un GUID (supportato solo in Microsoft SQL Server).

   >[!NOTE]
   >
   >Per contenere un **uuid** in motori diversi da Microsoft SQL Server, è necessario aggiungere e completare la funzione &quot;newuuuid()&quot; con il relativo valore predefinito.

Di seguito è riportato lo schema di esempio con i tipi immessi:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### Mappatura dei tipi di dati Adobe Campaign/DBMS {#mapping-the-types-of-adobe-campaign-dbms-data}

La tabella seguente elenca le mappature per i tipi di dati generati da Adobe Campaign per i diversi sistemi di gestione del database.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong> Oracle</strong><br /> </td> 
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>SQL MS</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Stringa<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 se unicode)<br /> </td> 
   <td> VARCHAR (CARATTERE VARCHAR IMPOSTA UNICODE SE Unicode)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR se unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINO<br /> </td> 
   <td> NUMERO(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINO<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINO<br /> </td> 
   <td> NUMERO(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINO<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Breve<br /> </td> 
   <td> SMALLINO<br /> </td> 
   <td> NUMERO(5)<br /> </td> 
   <td> SMALLINO<br /> </td> 
   <td> SMALLINO<br /> </td> 
   <td> SMALLINO<br /> </td> 
  </tr> 
  <tr> 
   <td> Doppio<br /> </td> 
   <td> DOPPIA PRECISIONE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOPPIO<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Lunga<br /> </td> 
   <td> INTERO<br /> </td> 
   <td> NUMERO(10)<br /> </td> 
   <td> INTERO<br /> </td> 
   <td> INTERO<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGLIETTO<br /> </td> 
   <td> NUMERO(20)<br /> </td> 
   <td> NUMERIC(20)<br /> </td> 
   <td> BIGLIETTO<br /> </td> 
   <td> BIGLIETTO<br /> </td> 
  </tr> 
  <tr> 
   <td> Data<br /> </td> 
   <td> DATA<br /> </td> 
   <td> DATA<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> DATA<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Time<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> TIME<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATA<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATA<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Intervallo temporale<br /> </td> 
   <td> DOPPIA PRECISIONE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOPPIO<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Per memoria<br /> </td> 
   <td> TESTO<br /> </td> 
   <td> CLOB (NCLOB se Unicode)<br /> </td> 
   <td> CLOB (CLOB CHARACTER SET UNICODE, se Unicode)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TESTO (NTEXT se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMMAGINE<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Properties {#properties}

La **`<elements>`** e **`<attributes>`** gli elementi dello schema dati possono essere arricchiti con varie proprietà. È possibile compilare un’etichetta per descrivere l’elemento corrente.

### Etichette e descrizioni {#labels-and-descriptions}

* La **etichetta** consente di inserire una breve descrizione.

   >[!NOTE]
   >
   >L’etichetta è associata alla lingua corrente dell’istanza.

   **Esempio**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   L’etichetta è visibile dal modulo di input della console client di Adobe Campaign:

   ![](assets/d_ncs_integration_schema_label.png)

* La **desc** consente di inserire una descrizione lunga.

   La descrizione può essere visualizzata dal modulo di input nella barra di stato della finestra principale della console client di Adobe Campaign.

   >[!NOTE]
   >
   >La descrizione è associata alla lingua corrente dell’istanza.

   **Esempio**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Valori predefiniti {#default-values}

La **default** consente di definire un&#39;espressione che restituisce un valore predefinito alla creazione del contenuto.

Il valore deve essere un&#39;espressione conforme al linguaggio XPath. Per ulteriori informazioni, consulta [Riferimento con XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Esempio**:

* Data corrente: **default=&quot;GetDate()&quot;**
* Contatore: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   In questo esempio, il valore predefinito viene costruito utilizzando la concatenazione di una stringa e chiamando il **CounterValue** funzione con un nome contatore gratuito. Il numero restituito viene incrementato di uno a ogni inserimento.

   >[!NOTE]
   >
   >Nella console del client Adobe Campaign, la **[!UICONTROL Administration>Counters]** viene utilizzato per gestire i contatori.

Per collegare un valore predefinito a un campo, puoi utilizzare la funzione `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : consente di precompilare il campo con un valore predefinito durante la creazione di entità. Il valore non sarà un valore SQL predefinito.

`<sqldefault>` : consente di ottenere un valore aggiunto durante la creazione di un campo. Questo valore viene visualizzato come risultato SQL. Durante un aggiornamento dello schema, questo valore incide solo sui nuovi record.

### Enumerazioni {#enumerations}

#### Enumerazione gratuita {#free-enumeration}

La **userEnum** consente di definire un&#39;enumerazione gratuita per memorizzare e visualizzare i valori immessi tramite questo campo. La sintassi è la seguente:

**userEnum=&quot;nome dell&#39;enumerazione&quot;**

Il nome assegnato all&#39;enumerazione può essere scelto liberamente e condiviso con altri campi.

Questi valori vengono visualizzati in un elenco a discesa del modulo di input:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Nella console del client Adobe Campaign, la **[!UICONTROL Administration > Enumerations]** viene utilizzato per gestire le enumerazioni.

#### Imposta enumerazione {#set-enumeration}

La **enum** consente di definire un&#39;enumerazione fissa utilizzata quando l&#39;elenco dei valori possibili è noto in anticipo.

La **enum** l’attributo si riferisce alla definizione di una classe di enumerazione compilata nello schema al di fuori dell’elemento principale.

Le enumerazioni consentono all’utente di selezionare un valore da un elenco a discesa invece di immettere il valore in un campo di input regolare:

![](assets/d_ncs_integration_schema_enum.png)

Esempio di dichiarazione di enumerazione nello schema dati:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Un’enumerazione viene dichiarata al di fuori dell’elemento principale tramite il **`<enumeration>`** elemento.

Le proprietà di enumerazione sono le seguenti:

* **baseType**: tipo di dati associati ai valori,
* **etichetta**: descrizione dell&#39;enumerazione,
* **name**: nome dell&#39;enumerazione,
* **default**: valore predefinito dell&#39;enumerazione.

I valori di enumerazione sono dichiarati nel **`<value>`** con i seguenti attributi:

* **name**: nome del valore memorizzato internamente,
* **etichetta**: viene visualizzata tramite l’interfaccia grafica.

#### enumerazione del dbenum {#dbenum-enumeration}

* La **dbenum** consente di definire un&#39;enumerazione le cui proprietà sono simili a quelle della **enum** proprietà.

   Tuttavia, **name** l&#39;attributo non memorizza il valore internamente, ma memorizza un codice che consente di estendere le tabelle interessate senza modificarne lo schema.

   I valori vengono definiti tramite la **[!UICONTROL Administration>Enumerations]** nodo.

   Questa enumerazione viene utilizzata, ad esempio, per specificare la natura delle campagne.

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### Esempio {#example}

Ecco il nostro schema di esempio con le proprietà inserite:

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## Raccolte {#collections}

Una raccolta è un elenco di elementi con lo stesso nome e lo stesso livello gerarchico.

La **non legato** Attributo con il valore &quot;true&quot; consente di compilare un elemento di raccolta.

**Esempio**: definizione della **`<group>`** elemento di raccolta nello schema.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Con proiezione del contenuto XML:

```
<group label="Group1"/>
<group label="Group2"/>
```

## Riferimento con XPath {#referencing-with-xpath}

Il linguaggio XPath viene utilizzato in Adobe Campaign per fare riferimento a un elemento o un attributo appartenente a uno schema di dati.

XPath è una sintassi che consente di individuare un nodo nella struttura di un documento XML.

Gli elementi sono designati in base al loro nome e gli attributi sono designati in base al nome preceduto dal carattere &quot;@&quot;.

**Esempio**:

* **@email**: seleziona l’e-mail,
* **location/@city**: seleziona l&#39;attributo &quot;city&quot; sotto il **`<location>`** elemento
* **../@email**: seleziona l’indirizzo e-mail dall’elemento padre dell’elemento corrente
* **gruppo`[1]/@label`**: seleziona l’attributo &quot;label&quot; che è l’elemento figlio del primo **`<group>`** elemento di raccolta
* **gruppo`[@label='test1']`**: seleziona l&#39;attributo &quot;label&quot; che è l&#39;elemento figlio del **`<group>`** e contiene il valore &quot;test1&quot;

>[!NOTE]
>
>Viene aggiunto un vincolo aggiuntivo quando il percorso attraversa un sottoelemento. In questo caso, è necessario inserire tra parentesi la seguente espressione:
>
>* **location/@city** non è valido; utilizzare **`[location/@city]`**
>* **`[@email]`** e **@email** sono equivalenti

>


È inoltre possibile definire espressioni complesse, ad esempio le seguenti operazioni aritmetiche:

* **@gender+1**: aggiunge 1 al contenuto del **genere** attributo,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: crea una stringa prendendo il valore dell&#39;indirizzo e-mail aggiunto alla data di creazione tra parentesi (per il tipo di stringa, inserire la costante tra virgolette).

Sono state aggiunte funzioni di alto livello alle espressioni per arricchire il potenziale di questa lingua.

Puoi accedere all’elenco delle funzioni disponibili tramite qualsiasi editor di espressioni nella console client di Adobe Campaign:

![](assets/d_ncs_integration_schema_function.png)

**Esempio**:

* **GetDate()**: restituisce la data corrente
* **Year(@created)**: restituisce l&#39;anno della data contenuta nell&#39;attributo &quot;created&quot;.
* **GetEmailDomain(@email)**: restituisce il dominio dell’indirizzo e-mail.

## Creazione di una stringa tramite la stringa di calcolo {#building-a-string-via-the-compute-string}

A **Stringa di calcolo** è un&#39;espressione XPath utilizzata per creare una stringa che rappresenta un record in una tabella associata allo schema. **Stringa di calcolo** viene utilizzato principalmente nell’interfaccia grafica per visualizzare l’etichetta di un record selezionato.

La **Stringa di calcolo** è definito tramite **`<compute-string>`** elemento sotto l’elemento principale dello schema dati. Un **expr** attributo contiene un&#39;espressione XPath per calcolare la visualizzazione.

**Esempio**: stringa di calcolo della tabella dei destinatari.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Risultato della stringa calcolata per un destinatario: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Se lo schema non contiene una stringa Compute, per impostazione predefinita viene compilata una stringa Compute con i valori della chiave primaria dello schema.
