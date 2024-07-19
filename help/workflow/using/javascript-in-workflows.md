---
product: campaign
title: Esempi di codice JavaScript nei flussi di lavoro
description: Questi esempi mostrano come utilizzare il codice JavaScript in un flusso di lavoro
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1695'
ht-degree: 3%

---

# Esempi di codice JavaScript nei flussi di lavoro{#javascript-in-workflows}



Questi esempi mostrano come utilizzare il codice JavaScript in un flusso di lavoro:

* [Scrivi nel database](#write-example)
* [Eseguire una query sul database](#read-example)
* [Attivare un flusso di lavoro utilizzando un metodo SOAP statico](#trigger-example)
* [Interagire con il database utilizzando un metodo SOAP non statico](#interact-example)

[Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) sui metodi SOAP statici e non statici.

In questi esempi viene utilizzata l&#39;estensione ECMAScript for XML (E4X). Con questa estensione, puoi combinare le chiamate JavaScript e le primitive XML nello stesso script.

Per provare questi esempi, segui questi passaggi:

1. Crea un flusso di lavoro e aggiungi queste attività al flusso di lavoro:
   1. Avvia attività
   1. Attività codice JavaScript
   1. Attività Fine

   [Ulteriori informazioni](building-a-workflow.md) sulla creazione dei flussi di lavoro.

1. Aggiungi il codice JavaScript a un’attività. [Ulteriori informazioni](advanced-parameters.md).
1. Salva il flusso di lavoro.
1. Prova gli esempi:
   1. Avvia il flusso di lavoro. [Ulteriori informazioni](starting-a-workflow.md).
   1. Apri il diario. [Ulteriori informazioni](monitoring-workflow-execution.md#displaying-logs).

## Esempio 1: scrivere nel database{#write-example}

Per scrivere nel database, è possibile utilizzare il metodo statico `Write` nello schema `xtk:session`:

1. Comporre una richiesta di scrittura in XML.

1. Scrivi il record:

   1. Chiama il metodo `Write` nello schema `xtk:session`.

      >[!IMPORTANT]
      > Se utilizzi Adobe Campaign v8, ti consigliamo di utilizzare il meccanismo di gestione temporanea con le API **Ingestion** e **Data update/delete** per il metodo `Write` in una tabella di Snowflake. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

   1. Passa il codice XML come argomento per la richiesta di scrittura.

### Passaggio 1: comporre una richiesta di scrittura

È possibile aggiungere, aggiornare ed eliminare record.

#### Inserire un record

Poiché l&#39;operazione `insert` è l&#39;operazione predefinita, non è necessario specificarla.

Specificare queste informazioni come attributi XML:

* Schema della tabella da modificare
* Campi della tabella da compilare

Esempio:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Aggiornare un record

Utilizzare l&#39;operazione `_update`. [Ulteriori informazioni](../../configuration/using/data-oriented-apis.md).

Specificare queste informazioni come attributi XML:

* Schema della tabella da modificare
* Campi della tabella da aggiornare
* Argomento chiave necessario per identificare il record da aggiornare

Esempio:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Eliminare un record

Utilizzare il metodo `DeleteCollection`. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Specifica queste informazioni:

* Schema della tabella da modificare
* Clausola `where` necessaria per identificare il record da aggiornare, sotto forma di un elemento XML

Esempio:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Passaggio 2: scrivere il record

Chiama il metodo `Write` non statico nello schema `xtk:session`:

```javascript
xtk.session.Write(myXML)
```

Nessun valore restituito per questo metodo.

Aggiungi il codice completo a un’attività di codice JavaScript nel flusso di lavoro:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

Questo video mostra come scrivere nel database:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Esempio 2: eseguire una query sul database{#read-example}

Per eseguire una query sul database, è possibile utilizzare il metodo di istanza `xtk:queryDef` non statico:

1. Componi una query in XML.
1. Creare un oggetto query.
1. Esegui la query.

### Passaggio 1: comporre una query

Specificare il codice XML per un&#39;entità `queryDef`.

Sintassi:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Specifica queste informazioni:

* Schema della tabella da leggere
* L&#39;operazione
* Colonne da restituire, in una clausola `select`
* Condizioni in una clausola `where`
* Criteri di filtro in una clausola `orderBy`

Puoi utilizzare le seguenti operazioni:

| Operazione | Risultato |
| --- | --- |
| `select` | Zero o più elementi vengono restituiti come raccolta. |
| `getIfExists` | Viene restituito un elemento. Se non esiste alcun elemento di corrispondenza, viene restituito un elemento vuoto. |
| `get` | Viene restituito un elemento. Se non esiste alcun elemento di corrispondenza, viene restituito un errore. |
| `count` | Il numero di record corrispondenti viene restituito sotto forma di un elemento con un attributo `count`. |

Scrivere le clausole `select`, `where` e `orderBy` come elementi XML:

* clausola `select`

  Specificare le colonne da restituire. Ad esempio, per selezionare il nome e il cognome della persona, scrivere il codice seguente:

  ```xml
  <select>
      <node expr="@firstName"/>
      <node expr="@lastName"/>
  </select>
  ```

  Con lo schema `nms:recipient`, gli elementi vengono restituiti in questo modulo:

  ```xml
  <recipient firstName="Bo" lastName="Didley"/>
  ```

* clausola `where`

  Per specificare le condizioni, utilizzare una clausola `where`. Ad esempio, per selezionare i record che si trovano nella cartella **Training**, è possibile scrivere il codice seguente:

  ```xml
  <where>
      <condition expr="[folder/@label]='Training'"/>
  </where>
  ```

  Quando combini più espressioni, utilizza l’operatore booleano nella prima espressione. Ad esempio, per selezionare tutte le persone denominate Isabel Garcia, puoi scrivere questo codice:

  ```xml
  <condition boolOperator="AND" expr="@firstName='Isabel'"/>
  <condition expr="@lastName='Garcia'"/>
  ```

* clausola `orderBy`

  Per ordinare il set di risultati, specificare la clausola `orderBy` come elemento XML con attributo `sortDesc`. Ad esempio, per ordinare i cognomi in ordine crescente, è possibile scrivere il codice seguente:

  ```xml
  <orderBy>
      <node expr="@lastName> sortDesc="false"/>
  </orderBy>
  ```

### Passaggio 2: creare un oggetto query

Per creare un&#39;entità dal codice XML, utilizzare il metodo `create(`*`content`*`)`:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Aggiungi al metodo `create(`*`content`*`)` il prefisso dello schema dell&#39;entità da creare.

L&#39;argomento *`content`* è un argomento stringa ed è facoltativo. Questo argomento contiene il codice XML che descrive l&#39;entità.

### Passaggio 3: eseguire la query

Segui questi passaggi:

1. Chiama il metodo `ExecuteQuery` sull&#39;entità `queryDef`:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Elabora i risultati:
   1. Eseguire un&#39;iterazione sui risultati dell&#39;operazione `select` utilizzando un costrutto loop.
   1. Verificare i risultati utilizzando l&#39;operazione `getIfExists`.
   1. Contare i risultati utilizzando l&#39;operazione `count`.

#### Risultati di un&#39;operazione `select`

Tutte le corrispondenze vengono restituite come una raccolta:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Per scorrere i risultati, utilizzare il ciclo `for each`:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

Il ciclo include una variabile di destinatario locale. Per ogni destinatario restituito nella raccolta di destinatari, viene stampata l’e-mail del destinatario. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) sulla funzione `logInfo`.

#### Risultati di un&#39;operazione `getIfExists`

Ogni corrispondenza viene restituita come elemento:

```xml
<recipient id="52,378,079">
```

Se non viene trovata alcuna corrispondenza, viene restituito un elemento vuoto:

```xml
<recipient/>
```

È possibile fare riferimento al nodo della chiave primaria, ad esempio l&#39;attributo `@id`:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Risultato di un&#39;operazione `get`

Viene restituita una corrispondenza come elemento:

```xml
<recipient id="52,378,079">
```

Se non viene trovata alcuna corrispondenza, viene restituito un errore.

>[!TIP]
>
>Se si sa che esiste una corrispondenza, utilizzare l&#39;operazione `get`. In caso contrario, utilizzare l&#39;operazione `getIfExists`. Se utilizzi questa best practice, gli errori rivelano problemi imprevisti. Se si utilizza l&#39;operazione `get`, non utilizzare l&#39;istruzione `try…catch`. Il problema viene gestito dal processo di gestione degli errori del flusso di lavoro.

#### Risultato di un&#39;operazione `count`

Viene restituito un elemento con l&#39;attributo `count`:

```xml
<recipient count="200">
```

Per utilizzare il risultato, fare riferimento all&#39;attributo `@count`:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Per l&#39;operazione `select`, aggiungere questo codice a un&#39;attività codice JavaScript nel flusso di lavoro:

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

Poiché l&#39;operazione `select` è l&#39;operazione predefinita, non è necessario specificarla.

Questo video illustra come leggere dal database:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Attivare un flusso di lavoro {#trigger-example}

Puoi attivare i flussi di lavoro a livello di programmazione, ad esempio nei flussi di lavoro tecnici o per elaborare le informazioni immesse da un utente in una pagina di un’applicazione web.

L’attivazione dei flussi di lavoro avviene tramite l’utilizzo di eventi. Puoi utilizzare queste funzioni per gli eventi:

* Per pubblicare un evento, è possibile utilizzare il metodo statico `PostEvent`. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Per ricevere un evento, è possibile utilizzare l&#39;attività **[!UICONTROL External signal]**. [Ulteriori informazioni](external-signal.md).

Puoi attivare i flussi di lavoro in diversi modi:

* È possibile attivare un workflow in linea, ovvero dallo script principale di un&#39;attività **[!UICONTROL JavaScript code]**.
* Puoi attivare un flusso di lavoro al completamento di un altro:
   * Aggiungere uno script di inizializzazione all&#39;attività **[!UICONTROL End]** del flusso di lavoro iniziale.
   * Aggiungi l&#39;attività **[!UICONTROL External signal]** all&#39;inizio del flusso di lavoro di destinazione.

     Al completamento del flusso di lavoro iniziale, viene registrato un evento. La transizione in uscita viene attivata e le variabili dell’evento vengono compilate. Quindi, l’evento viene ricevuto dal flusso di lavoro di destinazione.

     >[!TIP]
     >
     >Come procedura ottimale, quando si aggiunge uno script a un&#39;attività, racchiudere il nome dell&#39;attività in trattini doppi, ad esempio `-- end --`. [Ulteriori informazioni](workflow-best-practices.md) sulle best practice per i flussi di lavoro.

Sintassi del metodo `PostEvent`:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In questo esempio, al completamento del flusso di lavoro, viene passato un breve testo all&#39;attività **signal** del flusso di lavoro **wkfExampleReceiver**:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Poiché l&#39;ultimo parametro è impostato su `false`, il flusso di lavoro **wkfExampleReceiver** viene attivato ogni volta che il flusso di lavoro iniziale viene completato.

Quando attivi i flussi di lavoro, tieni presente i seguenti principi:

* Il comando `PostEvent` viene eseguito in modo asincrono. Il comando viene inserito nella coda del server. Il metodo restituisce dopo la registrazione dell’evento.
* È necessario avviare il flusso di lavoro di destinazione. In caso contrario, viene scritto un errore nel file di registro.
* Se il flusso di lavoro di destinazione è sospeso, il comando `PostEvent` viene accodato fino alla ripresa del flusso di lavoro.
* L’attività attivata non richiede che sia in corso un’attività.

Questo video illustra come utilizzare i metodi API statici:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Questo video mostra come attivare i flussi di lavoro:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagire con il database {#interact-example}

Questi esempi mostrano come eseguire queste azioni:

* Utilizzare i metodi `get` e `create` negli schemi per utilizzare metodi SOAP non statici
* Creare metodi che eseguono query SQL
* Utilizzare il metodo `write` per inserire, aggiornare ed eliminare record

Segui questi passaggi:

1. Definisci la query:

   * Recuperare un&#39;entità utilizzando il metodo `create` nello schema corrispondente, ad esempio lo schema `xtk:workflow`. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Utilizzare il metodo `queryDef` per eseguire una query SQL.

1. Eseguire la query utilizzando il metodo `ExecuteQuery`. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Utilizzare il ciclo `for each` per recuperare i risultati.

### Sintassi del metodo `queryDef` con una clausola `select`

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### metodo `Create`

#### Esempio 1: selezionare i record e scrivere nel giornale di registrazione

I nomi interni dei flussi di lavoro che si trovano nella cartella **wfExamples** sono selezionati. I risultati vengono ordinati in base al nome interno, in ordine crescente, e scritti nel giornale di registrazione.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Esempio 2: eliminare record

Vengono selezionati il nome, il cognome, l’e-mail e l’ID di tutti i destinatari di nome Chris Smith. I risultati vengono ordinati per e-mail, in ordine crescente e scritti nel giornale di registrazione. È stata utilizzata un&#39;operazione `delete` per eliminare i record selezionati.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Esempio 3: selezionare i record e scrivere nel giornale di registrazione

In questo esempio viene utilizzato un metodo non statico. Vengono selezionati l&#39;anno e-mail e l&#39;anno di nascita di tutti i destinatari le cui informazioni sono memorizzate nella cartella **1234** e il cui nome di dominio e-mail inizia con &quot;adobe&quot;. I risultati sono ordinati in ordine decrescente per data di nascita. L&#39;e-mail dei destinatari viene scritta nel giornale di registrazione.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### metodo `Write`

È possibile inserire, aggiornare ed eliminare record. È possibile utilizzare il metodo `Write` su qualsiasi schema in Adobe Campaign. Poiché questo metodo è statico, non è necessario creare un oggetto. Puoi utilizzare le seguenti operazioni:

* Operazione `update`
* Operazione `insertOrUpdate`, con l&#39;argomento `_key` per identificare il record da aggiornare

  Se non si specifica la cartella **Destinatari**, se esiste una corrispondenza, il record verrà aggiornato in una sottocartella. In caso contrario, il record viene creato nella cartella principale **Destinatari**.

* Operazione `delete`

>[!IMPORTANT]
> Se utilizzi Adobe Campaign v8, ti consigliamo di utilizzare il meccanismo di gestione temporanea con le API **Ingestion** e **Data update/delete** per il metodo `Write` in una tabella di Snowflake. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

#### Esempio 1: inserire o aggiornare un record

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Esempio 2: eliminare record

Questo esempio combina un metodo statico e un metodo non statico.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

Questo video mostra come utilizzare i metodi API non statici:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

Questo video mostra un esempio di utilizzo di un metodo API non statico in un flusso di lavoro:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Argomenti correlati

* [API orientate ai dati](../../configuration/using/data-oriented-apis.md)
* [Script e modelli JavaScript](javascript-scripts-and-templates.md)
* [Metodi SOAP in JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### Documentazione API

* [Esempi di chiamate SOAP](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Metodi:
   * [Crea](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [EliminaRaccolta](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Scrittura](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [funzione logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)
