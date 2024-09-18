---
product: campaign
title: Comprendere la struttura dello schema in Adobe Campaign
description: Struttura dello schema
feature: Custom Resources
role: Data Engineer, Developer
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '1511'
ht-degree: 1%

---

# Comprendere la struttura dello schema {#schema-structure}

La struttura di base di uno schema è descritta di seguito.

## Schemi di dati  {#data-schema}

Per un `<srcschema>`, la struttura è la seguente:

```sql
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

Il documento XML di uno schema dati deve contenere l&#39;elemento principale **`<srcschema>`** con gli attributi **name** e **namespace** per popolare il nome dello schema e il relativo spazio dei nomi.

```sql
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Per illustrare la struttura di uno schema di dati, utilizziamo i seguenti contenuti XML:

```sql
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Con lo schema di dati corrispondente:

```sql
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

Il punto di ingresso dello schema è il suo elemento principale. È facile da identificare perché ha lo stesso nome dello schema e dovrebbe essere l’elemento secondario dell’elemento principale. La descrizione del contenuto inizia con questo elemento.

Nel nostro esempio, l’elemento principale è rappresentato dalla seguente riga:

```
<element name="recipient">
```

Gli elementi **`<attribute>`** e **`<element>`** che seguono l&#39;elemento principale vengono utilizzati per definire le posizioni e i nomi degli elementi dati nella struttura XML.

Nello schema di esempio, questi sono:

```sql
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Si applicano le seguenti regole:

* Ogni **`<element>`** e **`<attribute>`** deve essere identificato per nome tramite l&#39;attributo **name**.

  >[!IMPORTANT]
  >
  >Il nome dell&#39;elemento deve essere conciso, preferibilmente in inglese, e includere solo i caratteri consentiti nelle regole di denominazione XML.

* Solo gli elementi **`<element>`** possono contenere **`<attribute>`** elementi e **`<element>`** elementi nella struttura XML.
* Un elemento **`<attribute>`** deve avere un nome univoco all&#39;interno di **`<element>`**.
* Si consiglia di utilizzare **`<elements>`** nelle stringhe di dati su più righe.

## Tipi di dati {#data-types}

Il tipo di dati viene immesso tramite l&#39;attributo **type** negli elementi **`<attribute>`** e **`<element>`**.

Un elenco dettagliato è disponibile nella descrizione dell&#39;elemento [`<attribute>`](../../configuration/using/schema/attribute.md) e dell&#39;elemento [`<element>`](../../configuration/using/schema/element.md).

Quando questo attributo non viene popolato, **stringa** è il tipo di dati predefinito a meno che l&#39;elemento non contenga elementi figlio. In caso affermativo, viene utilizzato solo per strutturare gli elementi in modo gerarchico (**`<location>`** elemento nel nostro esempio).

Negli schemi sono supportati i seguenti tipi di dati:

* **stringa**: stringa di caratteri. Esempi: un nome, una città, ecc.

  La dimensione può essere specificata tramite l&#39;attributo **length** (facoltativo, valore predefinito &quot;255&quot;).

* **booleano**: campo booleano. Esempio di valori possibili: true/false, 0/1, sì/no, ecc.
* **byte**, **short**, **long**: valori interi (1 byte, 2 byte, 4 byte). Esempi: un’età, un numero di conto, un numero di punti, ecc.
* **double**: numero a virgola mobile a precisione doppia. Esempi: un prezzo, un tasso, ecc.
* **date**, **datetime**: date e date + ore. Esempi: una data di nascita, una data di acquisto, ecc.
* **datetimenotz**: data + ora senza dati relativi al fuso orario.
* **intervallo di tempo**: durate. Esempio: anzianità.
* **memo**: campi di testo lunghi (più righe). Esempi: una descrizione, un commento, ecc.
* **uuid**: campi &quot;uniqueidentifier&quot; per supportare un GUID (supportato solo in Microsoft SQL Server).

  >[!NOTE]
  >
  >Per contenere un campo **uuid** in RDBMS diverso da Microsoft SQL Server, è necessario aggiungere la funzione `the newuuid()` e completarla con il relativo valore predefinito.

Di seguito è riportato uno schema di esempio con i tipi immessi:

```sql
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
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Stringa<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMERO(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMERO(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Breve<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMERO(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Doppio<br /> </td> 
   <td> PRECISIONE DOPPIA<br /> </td> 
   <td> MOBILE<br /> </td> 
  </tr> 
  <tr> 
   <td> Lungo<br /> </td> 
   <td> INTERO<br /> </td> 
   <td> NUMERO(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMERO(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Data<br /> </td> 
   <td> DATA<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Ora<br /> </td> 
   <td> ORA<br /> </td> 
   <td> MOBILE<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> MARCA TEMPORALE<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> MARCA TEMPORALE<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Intervallo di tempo<br /> </td> 
   <td> PRECISIONE DOPPIA<br /> </td> 
   <td> MOBILE<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TESTO<br /> </td> 
   <td> CLOB (NCLOB se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Properties {#properties}

Gli elementi **`<elements>`** e **`<attributes>`** dello schema dati possono essere arricchiti con varie proprietà. Puoi popolare un’etichetta per descrivere l’elemento corrente.

### Etichette e descrizioni {#labels-and-descriptions}

* La proprietà **label** consente di immettere una breve descrizione.

  >[!NOTE]
  >
  >L’etichetta è associata alla lingua corrente dell’istanza.

  **Esempio**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  L’etichetta viene visualizzata nel modulo di input della console client di Adobe Campaign:

  ![](assets/d_ncs_integration_schema_label.png)

* La proprietà **desc** consente di immettere una descrizione lunga.

  La descrizione viene visualizzata nel modulo di input nella barra di stato della finestra principale della console client di Adobe Campaign.

  >[!NOTE]
  >
  >La descrizione è associata alla lingua corrente dell’istanza.

  **Esempio**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Valori predefiniti {#default-values}

Utilizzare la proprietà **default** per definire un&#39;espressione che restituisce un valore predefinito durante la creazione del contenuto.

Il valore deve essere un&#39;espressione compatibile con il linguaggio XPath. Per ulteriori informazioni, consulta [Riferimento con XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Esempio**:

* Data corrente: **default=&quot;GetDate()&quot;**
* Contatore: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  In questo esempio, il valore predefinito viene costruito utilizzando la concatenazione di una stringa e chiamando la funzione **CounterValue** con un nome di contatore libero. Il numero restituito viene incrementato di uno a ogni inserimento.

  >[!NOTE]
  >
  >Nella console del client Adobe Campaign, passare alla cartella **[!UICONTROL Administration > Counters]** di Esplora risorse per gestire i contatori.

Per collegare un valore predefinito a un campo, è possibile utilizzare `<default>` o `<sqldefault>`   campo.

`<default>` : consente di precompilare il campo con un valore predefinito durante la creazione di entità. Il valore non sarà un valore SQL predefinito.

`<sqldefault>` : ti consente di avere un valore aggiunto durante la creazione di un campo. Questo valore viene visualizzato come risultato SQL. Durante un aggiornamento dello schema, questo valore influisce solo sui nuovi record.

### Enumerazioni {#enumerations}

#### Enumerazione aperta {#free-enumeration}

La proprietà **userEnum** consente di definire un&#39;enumerazione aperta per archiviare e visualizzare i valori immessi tramite questo campo.

La sintassi è la seguente:

`userEnum="name of enumeration"`

Questi valori vengono visualizzati in un elenco a discesa dal modulo di input:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Nella console del client Adobe Campaign, passa alla cartella **[!UICONTROL Administration > Enumerations]** di Explorer per gestire le enumerazioni.

#### Imposta enumerazione {#set-enumeration}

La proprietà **enum** consente di definire un&#39;enumerazione fissa utilizzata quando l&#39;elenco dei valori possibili è noto in anticipo.

L&#39;attributo **enum** fa riferimento alla definizione di una classe di enumerazione popolata nello schema al di fuori dell&#39;elemento principale.

Le enumerazioni consentono di selezionare un valore da un elenco a discesa anziché immetterlo in un campo di input regolare:

![](assets/d_ncs_integration_schema_enum.png)

Esempio di dichiarazione di enumerazione nello schema dati:

```sql
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Enumerazione dichiarata all&#39;esterno dell&#39;elemento principale tramite l&#39;elemento **`<enumeration>`**.

Le proprietà di enumerazione sono le seguenti:

* **baseType**: tipo di dati associato ai valori
* **label**: descrizione dell&#39;enumerazione
* **name**: nome dell&#39;enumerazione
* **default**: valore predefinito dell&#39;enumerazione

I valori di enumerazione sono dichiarati nell&#39;elemento **`<value>`** con i seguenti attributi:

* **nome**: nome del valore archiviato internamente
* **label**: etichetta visualizzata nell&#39;interfaccia grafica

#### enumerazione del dbenum {#dbenum-enumeration}

*La proprietà **dbenum** consente di definire un&#39;enumerazione con proprietà simili a quelle della proprietà **enum**.

Tuttavia, l&#39;attributo **name** non memorizza il valore internamente, ma memorizza un codice che consente di estendere le tabelle interessate senza modificarne lo schema.

Questa enumerazione viene utilizzata per specificare la natura delle campagne, ad esempio.

![](assets/d_ncs_configuration_schema_dbenum.png)

### Esempio {#example}

Di seguito è riportato uno schema di esempio con le proprietà compilate:

```sql
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

L&#39;attributo **unbound** con valore &quot;true&quot; consente di popolare un elemento della raccolta.

**Esempio**: definizione dell&#39;elemento di raccolta **`<group>`** nello schema.

```sql
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Con la proiezione del contenuto XML:

```sql
<group label="Group1"/>
<group label="Group2"/>
```

## Riferimento a XPath {#referencing-with-xpath}

Il linguaggio XPath viene utilizzato in Adobe Campaign per fare riferimento a un elemento o attributo appartenente a uno schema di dati.

XPath è una sintassi che consente di individuare un nodo nella struttura di un documento XML.

Gli elementi sono designati dal loro nome e gli attributi sono designati dal nome preceduto dal carattere &quot;@&quot;.

**Esempio**:

* **@email**: seleziona l&#39;e-mail,
* **location/@city**: seleziona l&#39;attributo &quot;city&quot; nell&#39;elemento **`<location>`**
* **../@email**: seleziona l&#39;indirizzo e-mail dall&#39;elemento padre dell&#39;elemento corrente
* **gruppo`[1]/@label`**: seleziona l&#39;attributo &quot;label&quot; figlio del primo elemento della raccolta **`<group>`**
* **gruppo`[@label='test1']`**: seleziona l&#39;attributo &quot;label&quot; figlio dell&#39;elemento **`<group>`** e contiene il valore &quot;test1&quot;

>[!NOTE]
>
>Quando il percorso attraversa un sottoelemento, viene aggiunto un vincolo aggiuntivo. In questo caso, tra le parentesi deve essere inserita la seguente espressione:
>
>* **percorso/@city** non valido. Utilizzare **`[location/@city]`**
>* **`[@email]`** e **@email** sono equivalenti
>

È inoltre possibile definire espressioni complesse, ad esempio le seguenti operazioni aritmetiche:

* **@gender+1**: aggiunge 1 al contenuto dell&#39;attributo **gender**,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: crea una stringa raccogliendo il valore dell&#39;indirizzo e-mail aggiunto alla data di creazione tra parentesi (per il tipo di stringa, racchiudi la costante tra virgolette).

Sono state aggiunte funzioni di alto livello alle espressioni per arricchire il potenziale di questo linguaggio.

Puoi accedere all’elenco delle funzioni disponibili tramite qualsiasi editor di espressioni nella console client di Adobe Campaign:

![](assets/d_ncs_integration_schema_function.png)

**Esempio**:

* **GetDate()**: restituisce la data corrente
* **Year(@created)**: restituisce l&#39;anno della data contenuta nell&#39;attributo &quot;created&quot;
* **GetEmailDomain(@email)**: restituisce il dominio dell&#39;indirizzo e-mail

## Creazione di una stringa tramite la stringa di calcolo {#building-a-string-via-the-compute-string}

Una **stringa di calcolo** è un&#39;espressione XPath utilizzata per creare una stringa che rappresenta un record in una tabella associata allo schema. **La stringa di calcolo** viene utilizzata principalmente nell&#39;interfaccia grafica per visualizzare l&#39;etichetta di un record selezionato.

La **stringa di calcolo** è definita tramite l&#39;elemento **`<compute-string>`** nell&#39;elemento principale dello schema dati. Un attributo **expr** contiene un&#39;espressione XPath per calcolare la visualizzazione.

**Esempio**: stringa di calcolo della tabella dei destinatari.

```sql
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Risultato della stringa calcolata per un destinatario: **Fai John (john.doe@aol.com)**

>[!NOTE]
>
>Se lo schema non contiene una stringa di calcolo, per impostazione predefinita viene compilata una stringa di calcolo con i valori della chiave primaria dello schema.


## Ulteriori informazioni

Per ulteriori informazioni, consulta i seguenti collegamenti:

* [Introduzione agli schemi](about-schema-reference.md)
* [Mappatura del database](database-mapping.md)
* [Gestione collegamenti](database-links.md)
* [Gestione delle chiavi](database-keys.md)
* [Modello dati della campagna](about-data-model.md)