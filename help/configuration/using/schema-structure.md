---
solution: Campaign Classic
product: campaign
title: Struttura dello schema
description: Struttura dello schema
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: a469d275fdd768fbd098a0027b5096872dbf6d89
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 1%

---


# Struttura dello schema{#schema-structure}

La struttura di base di un `<srcschema>` è la seguente:

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

Il documento XML di uno schema dati deve contenere gli attributi **`<srcschema>`** root con gli attributi **name** e **namespace** per compilare il nome dello schema e il relativo spazio dei nomi.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

È possibile utilizzare il contenuto XML seguente per illustrare la struttura di uno schema dati:

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Con lo schema dati corrispondente:

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

Nel nostro esempio, l&#39;elemento principale è rappresentato dalla seguente riga:

```
<element name="recipient">
```

Gli elementi **`<attribute>`** e **`<element>`** che seguono l&#39;elemento principale consentono di definire le posizioni e i nomi degli elementi di dati nella struttura XML.

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

* Ogni **`<element>`** e **`<attribute>`** deve essere identificato per nome tramite l&#39;attributo **name**.

   >[!IMPORTANT]
   >
   >Il nome dell&#39;elemento deve essere conciso, preferibilmente in inglese, e includere solo caratteri autorizzati in conformità alle regole di denominazione XML.

* Solo gli elementi **`<element>`** possono contenere elementi **`<attribute>`** e **`<element>`** nella struttura XML.
* Un elemento **`<attribute>`** deve avere un nome univoco all&#39;interno di un elemento **`<element>`**.
* È consigliabile utilizzare **`<elements>`** nelle stringhe di dati su più righe.

## Tipi di dati {#data-types}

Il tipo di dati viene immesso tramite l&#39;attributo **type** negli elementi **`<attribute>`** e **`<element>`**.

Un elenco dettagliato è disponibile nella descrizione dell&#39;elemento [`<attribute>` ](../../configuration/using/schema/attribute.md) e dell&#39; [`<element>` element](../../configuration/using/schema/element.md).

Se questo attributo non è popolato, **string** è il tipo di dati predefinito, a meno che l&#39;elemento non contenga elementi secondari. In caso contrario, viene utilizzato solo per strutturare gli elementi gerarchicamente (**`<location>`** nel nostro esempio).

I seguenti tipi di dati sono supportati negli schemi:

* **stringa**: stringa di caratteri. Esempi: un nome, una città, ecc.

   La dimensione può essere specificata tramite l&#39;attributo **length** (facoltativo, valore predefinito &quot;255&quot;).

* **booleano**: Campo booleano. Esempio di possibili valori: true/false, 0/1, yes/no, ecc.
* **byte**,  **short**,  **long**: numeri interi (1 byte, 2 byte, 4 byte). Esempi: un&#39;età, un numero di conto, un numero di punti, ecc.
* **double**: numero a virgola mobile a doppia precisione. Esempi: un prezzo, un tasso, ecc.
* **date**,  **datetime**: date e date + ore. Esempi: una data di nascita, una data di acquisto, ecc.
* **datetimenotz**: data + ora senza i dati del fuso orario.
* **timespan**: durate. Esempio: anzianità.
* **nota**: campi di testo lunghi (righe multiple). Esempi: una descrizione, un commento, ecc.
* **uuid**: Campi &quot;uniqueidentifier&quot; per supportare un GUID (supportati solo in Microsoft SQL Server).

   >[!NOTE]
   >
   >Per contenere un campo **uuid** in motori diversi da Microsoft SQL Server, è necessario aggiungere e completare la funzione &quot;newuid()&quot; con il relativo valore predefinito.

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

### Mappatura dei tipi  dati Adobe Campaign/DBMS {#mapping-the-types-of-adobe-campaign-dbms-data}

Nella tabella seguente sono elencati i mapping per i tipi di dati generati da  Adobe Campaign per i diversi sistemi di gestione del database.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong> Oracle</strong><br /> </td> 
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Stringa<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 se unicode)<br /> </td> 
   <td> VARCHAR (VARCHAR CARATTERE IMPOSTARE UNICODE se Unicode)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR se unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Short<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Double<br /> </td> 
   <td> DOPPIA PRECISIONE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Long<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> NUMERIC(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Data<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> DATE<br /> </td> 
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
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Durata<br /> </td> 
   <td> DOPPIA PRECISIONE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB se Unicode)<br /> </td> 
   <td> CLOB (CLOB CHARACTER SET UNICODE se Unicode)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT (NTEXT se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMAGE<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Properties {#properties}

Gli elementi **`<elements>`** e **`<attributes>`** dello schema di dati possono essere arricchiti con diverse proprietà. È possibile compilare un&#39;etichetta per descrivere l&#39;elemento corrente.

### Etichette e descrizioni {#labels-and-descriptions}

* La proprietà **label** consente di inserire una breve descrizione.

   >[!NOTE]
   >
   >L&#39;etichetta è associata alla lingua corrente dell&#39;istanza.

   **Esempio**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   L&#39;etichetta è visibile dal modulo di input della console client Adobe Campaign :

   ![](assets/d_ncs_integration_schema_label.png)

* La proprietà **desc** consente di inserire una descrizione lunga.

   La descrizione è visibile dal modulo di input nella barra di stato della finestra principale della console client Adobe Campaign .

   >[!NOTE]
   >
   >La descrizione è associata alla lingua corrente dell&#39;istanza.

   **Esempio**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Valori predefiniti {#default-values}

La proprietà **default** consente di definire un&#39;espressione che restituisce un valore predefinito al momento della creazione del contenuto.

Il valore deve essere un&#39;espressione conforme al linguaggio XPath. Per ulteriori informazioni, fare riferimento a [Riferimenti con XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Esempio**:

* Data corrente: **default=&quot;GetDate()&quot;**
* Contatore: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   In questo esempio, il valore predefinito è costruito utilizzando la concatenazione di una stringa e chiamando la funzione **CounterValue** con un nome contatore gratuito. Il numero restituito viene incrementato di un&#39;unità a ogni inserimento.

   >[!NOTE]
   >
   >Nella console client Adobe Campaign , il nodo **[!UICONTROL Administration>Counters]** viene utilizzato per gestire i contatori.

Per collegare un valore predefinito a un campo, è possibile utilizzare la variabile `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : consente di precompilare il campo con un valore predefinito durante la creazione di entità. Il valore non sarà un valore SQL predefinito.

`<sqldefault>` : consente di ottenere un valore aggiunto durante la creazione di un campo. Questo valore viene visualizzato come risultato SQL. Durante un aggiornamento dello schema, questo valore interesserà solo i nuovi record.

### Enumerazione {#enumerations}

#### Enumerazione gratuita {#free-enumeration}

La proprietà **userEnum** consente di definire un&#39;enumerazione gratuita per memorizzare e visualizzare i valori immessi tramite questo campo. La sintassi è la seguente:

**userEnum=&quot;nome dell&#39;enumerazione&quot;**

Il nome dato all&#39;enumerazione può essere scelto liberamente e condiviso con altri campi.

Questi valori vengono visualizzati in un elenco a discesa dal modulo di input:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Nella console client Adobe Campaign , il nodo **[!UICONTROL Administration > Enumerations]** viene utilizzato per gestire le enumerazioni.

#### Imposta enumerazione {#set-enumeration}

La proprietà **enum** consente di definire un&#39;enumerazione fissa utilizzata quando l&#39;elenco dei valori possibili è noto in anticipo.

L&#39;attributo **enum** fa riferimento alla definizione di una classe di enumerazione compilata nello schema all&#39;esterno dell&#39;elemento principale.

Le enumerazioni consentono all&#39;utente di selezionare un valore da un elenco a discesa invece di immettere il valore in un campo di immissione regolare:

![](assets/d_ncs_integration_schema_enum.png)

Esempio di una dichiarazione di enumerazione nello schema dati:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Un&#39;enumerazione viene dichiarata al di fuori dell&#39;elemento principale tramite l&#39;elemento **`<enumeration>`**.

Le proprietà di enumerazione sono le seguenti:

* **baseType**: tipo di dati associati ai valori,
* **label**: descrizione dell&#39;enumerazione,
* **name**: nome dell’enumerazione,
* **predefinito**: valore predefinito dell&#39;enumerazione.

I valori di enumerazione sono dichiarati nell&#39;elemento **`<value>`** con i seguenti attributi:

* **name**: nome del valore memorizzato internamente,
* **label**: etichetta visualizzata tramite l&#39;interfaccia grafica.

#### enumerazione dbenum {#dbenum-enumeration}

* La proprietà **dbenum** consente di definire un&#39;enumerazione le cui proprietà sono simili a quelle della proprietà **enum**.

   Tuttavia, l&#39;attributo **name** non memorizza il valore internamente, ma memorizza un codice che consente di estendere le tabelle interessate senza modificarne lo schema.

   I valori sono definiti tramite il nodo **[!UICONTROL Administration>Enumerations]**.

   Questa enumerazione viene utilizzata per specificare, ad esempio, la natura delle campagne.

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### Esempio {#example}

Di seguito è riportato lo schema di esempio con le proprietà compilate:

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

L&#39;attributo **unbound** con il valore &quot;true&quot; consente di compilare un elemento della raccolta.

**Esempio**: definizione dell&#39;elemento  **`<group>`** raccolta nello schema.

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

Il linguaggio XPath viene utilizzato in  Adobe Campaign per fare riferimento a un elemento o attributo appartenente a uno schema di dati.

XPath è una sintassi che consente di individuare un nodo nella struttura di un documento XML.

Gli elementi sono indicati dal nome e gli attributi sono designati dal nome preceduto dal carattere &quot;@&quot;.

**Esempio**:

* **@email**: seleziona l’e-mail,
* **location/@city**: seleziona l&#39;attributo &quot;city&quot; sotto l&#39; **`<location>`** elemento
* **../@email**: seleziona l&#39;indirizzo e-mail dall&#39;elemento padre dell&#39;elemento corrente
* **group`[1]/@label`**: seleziona l&#39;attributo &quot;label&quot; secondario del primo elemento della  **`<group>`** raccolta
* **group`[@label='test1']`**: seleziona l&#39;attributo &quot;label&quot; secondario dell&#39; **`<group>`** elemento e contiene il valore &quot;test1&quot;

>[!NOTE]
>
>Quando il percorso attraversa un sottoelemento, viene aggiunto un vincolo aggiuntivo. In questo caso, tra parentesi deve essere inserita la seguente espressione:
>
>* **location/@** city non valido; utilizzare  **`[location/@city]`**
>* **`[@email]`** e  **@** emailare equivalente

>



È inoltre possibile definire espressioni complesse, ad esempio le seguenti operazioni aritmetiche:

* **@gender+1**: aggiunge 1 al contenuto di  **** genderattribute,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: crea una stringa prendendo il valore dell&#39;indirizzo e-mail aggiunto alla data di creazione tra parentesi (per il tipo di stringa, inserire la costante tra virgolette).

Alle espressioni sono state aggiunte funzioni di alto livello per arricchire il potenziale di questa lingua.

È possibile accedere all&#39;elenco delle funzioni disponibili tramite qualsiasi editor di espressioni nella  console client Adobe Campaign:

![](assets/d_ncs_integration_schema_function.png)

**Esempio**:

* **GetDate()**: restituisce la data corrente
* **Year(@created)**: restituisce l&#39;anno della data contenuto nell&#39;attributo &quot;created&quot;.
* **GetEmailDomain(@email)**: restituisce il dominio dell’indirizzo e-mail.

## Creazione di una stringa tramite la stringa di calcolo {#building-a-string-via-the-compute-string}

Una **stringa di calcolo** è un&#39;espressione XPath utilizzata per creare una stringa che rappresenta un record in una tabella associata allo schema. **La** stringa di calcolo viene utilizzata principalmente nell&#39;interfaccia grafica per visualizzare l&#39;etichetta di un record selezionato.

La **stringa di calcolo** è definita tramite l&#39;elemento **`<compute-string>`** sotto l&#39;elemento principale dello schema di dati. Un attributo **expr** contiene un&#39;espressione XPath per calcolare la visualizzazione.

**Esempio**: stringa di calcolo della tabella ricevente.

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
>Se lo schema non contiene una stringa Calcola, per impostazione predefinita viene compilata una stringa Calcola con i valori della chiave primaria dello schema.

