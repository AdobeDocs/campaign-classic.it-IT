---
product: campaign
title: Esempi di codice JavaScript nei flussi di lavoro
description: Questi esempi mostrano come utilizzare il codice JavaScript in un flusso di lavoro
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 3%

---

# Esempi di codice JavaScript nei flussi di lavoro{#javascript-in-workflows}

![](../../assets/v7-only.svg)

Gli esempi seguenti mostrano come utilizzare il codice JavaScript in un flusso di lavoro:

* [Scrivi nel database](#write-example)
* [Eseguire una query sul database](#read-example)
* [Attiva un flusso di lavoro utilizzando un metodo SOAP statico](#trigger-example)
* [Interagire con il database utilizzando un metodo SOAP non statico](#interact-example)

[Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) informazioni sui metodi SOAP statici e non statici.

In questi esempi viene utilizzata l&#39;estensione ECMAScript for XML (E4X). Con questa estensione, è possibile combinare chiamate JavaScript e primitive XML nello stesso script.

Per provare questi esempi, segui questi passaggi:

1. Crea un flusso di lavoro e aggiungi queste attività al flusso di lavoro:
   1. Avvia attività
   1. Attività codice JavaScript
   1. Attività fine

   [Ulteriori informazioni](building-a-workflow.md) informazioni sulla creazione di flussi di lavoro.

1. Aggiungi il codice JavaScript a un&#39;attività . [Ulteriori informazioni](advanced-parameters.md).
1. Salva il flusso di lavoro.
1. Prova gli esempi:
   1. Avviare il flusso di lavoro. [Ulteriori informazioni](starting-a-workflow.md).
   1. Apri il giornale di registrazione. [Ulteriori informazioni](monitoring-workflow-execution.md#displaying-logs).

## Esempio 1: scrivere nel database{#write-example}

Per scrivere nel database, è possibile utilizzare il `Write` metodo `xtk:session` schema:

1. Componi una richiesta di scrittura in XML.

1. Scrivere il record:

   1. Chiama il `Write` metodo `xtk:session` schema.

      >[!IMPORTANT]
      > Se utilizzi Adobe Campaign v8, ti consigliamo di utilizzare il meccanismo di staging con **Acquisizione** e **Aggiornamento/eliminazione dati** API per `Write` in una tabella di Snowflake. [Maggiori informazioni](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

   1. Passa il codice XML come argomento per la richiesta di scrittura.

### Passaggio 1: comporre una richiesta di scrittura

È possibile aggiungere, aggiornare ed eliminare record.

#### Inserire un record

Perché `insert` operazione predefinita. Non è necessario specificarla.

Specifica queste informazioni come attributi XML:

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

Utilizza la `_update` funzionamento. [Ulteriori informazioni](../../configuration/using/data-oriented-apis.md).

Specifica queste informazioni come attributi XML:

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

Utilizza la `DeleteCollection` metodo . [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Specifica le seguenti informazioni:

* Schema della tabella da modificare
* La `where` clausola necessaria per identificare il record da aggiornare, sotto forma di un elemento XML

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

Chiama il non statico `Write` metodo `xtk:session` schema:

```javascript
xtk.session.Write(myXML)
```

Nessun valore restituito per questo metodo.

Aggiungi il codice completo a un’attività del codice JavaScript nel flusso di lavoro:

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

Per eseguire una query sul database, è possibile utilizzare il `xtk:queryDef` metodo di istanza:

1. Componi una query in XML.
1. Creare un oggetto query.
1. Esegui la query.

### Passaggio 1: comporre una query

Specifica il codice XML per un `queryDef` entità.

Sintassi:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Specifica le seguenti informazioni:

* Schema della tabella da leggere
* L&#39;operazione
* Le colonne da restituire, in un `select` clausola
* Le condizioni, in un `where` clausola
* I criteri di filtraggio, in un `orderBy` clausola

È possibile utilizzare le seguenti operazioni:

| Operazione | Risultato |
| --- | --- |
| `select` | Zero o più elementi vengono restituiti come raccolta. |
| `getIfExists` | Viene restituito un elemento. Se non esiste alcun elemento di corrispondenza, viene restituito un elemento vuoto. |
| `get` | Viene restituito un elemento. Se non esiste alcun elemento corrispondente, viene restituito un errore. |
| `count` | Il numero di record corrispondenti viene restituito sotto forma di elemento con un `count` attributo. |

Scrivi `select`, `where`e `orderBy` clausole come elementi XML:

* `select` clausola

   Specifica le colonne da restituire. Ad esempio, per selezionare il nome e il cognome della persona, scrivere questo codice:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Con la `nms:recipient` schema, gli elementi vengono restituiti in questo modulo:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` clausola

   Per specificare le condizioni, utilizza un `where` clausola . Ad esempio, per selezionare i record che si trovano nella **Formazione** cartella, è possibile scrivere questo codice:

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   Quando combini più espressioni, utilizza l’operatore booleano nella prima espressione. Ad esempio, per selezionare tutte le persone che si chiamano Isabel Garcia, è possibile scrivere questo codice:

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` clausola

   Per ordinare il set di risultati, specificare la `orderBy` come elemento XML con `sortDesc` attributo. Ad esempio, per ordinare i cognomi in ordine crescente, è possibile scrivere questo codice:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Passaggio 2: creare un oggetto query

Per creare un&#39;entità dal codice XML, utilizza il `create(`*`content`*`)` metodo:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Prefisso il `create(`*`content`*`)` con lo schema dell&#39;entità da creare.

La *`content`* argomento è un argomento stringa ed è facoltativo. Questo argomento contiene il codice XML che descrive l&#39;entità.

### Passaggio 3: eseguire la query

Segui questi passaggi:

1. Chiama il `ExecuteQuery` metodo `queryDef` entità:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Elabora i risultati:
   1. Itera sui risultati della `select` utilizzando un costrutto di loop.
   1. Verificare i risultati utilizzando `getIfExists` funzionamento.
   1. Conta i risultati utilizzando `count` funzionamento.

#### Risultati di un `select` funzionamento

Tutte le corrispondenze vengono restituite come raccolta:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Per eseguire iterazioni sui risultati, utilizza la `for each` loop:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

Il ciclo include una variabile del destinatario locale. Per ogni destinatario restituito nella raccolta di destinatari, l’e-mail del destinatario viene stampata. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) informazioni `logInfo` funzione .

#### Risultati di un `getIfExists` funzionamento

Ogni corrispondenza viene restituita come elemento:

```xml
<recipient id="52,378,079">
```

Se non è presente alcuna corrispondenza, viene restituito un elemento vuoto:

```xml
<recipient/>
```

Puoi fare riferimento al nodo della chiave primaria, ad esempio il `@id` attributo:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Risultato di un `get` funzionamento

Viene restituita una corrispondenza come elemento:

```xml
<recipient id="52,378,079">
```

Se non esiste alcuna corrispondenza, viene restituito un errore.

>[!TIP]
>
>Se sai che esiste una corrispondenza, utilizza la variabile `get` funzionamento. In caso contrario, utilizza il `getIfExists` funzionamento. Se si utilizza questa best practice, gli errori mostrano problemi imprevisti. Se utilizzi `get` non utilizzare il `try…catch` istruzione. Il problema viene gestito dal processo di gestione degli errori del flusso di lavoro.

#### Risultato di un `count` funzionamento

Un elemento con `count` attributo restituito:

```xml
<recipient count="200">
```

Per utilizzare il risultato, fai riferimento alla `@count` attributo:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Per `select` aggiungi questo codice a un’attività di codice JavaScript nel flusso di lavoro:

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

Perché `select` operazione predefinita. Non è necessario specificarla.

Questo video mostra come leggere dal database:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Attivare un flusso di lavoro {#trigger-example}

Puoi attivare i flussi di lavoro a livello di programmazione, ad esempio, nei flussi di lavoro tecnici o per elaborare le informazioni immesse da un utente in una pagina di un’applicazione web.

L’attivazione del flusso di lavoro avviene tramite l’utilizzo di eventi. È possibile utilizzare le seguenti funzionalità per gli eventi:

* Per pubblicare un evento, è possibile utilizzare l&#39; `PostEvent` metodo . [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Per ricevere un evento, puoi utilizzare la funzione **[!UICONTROL External signal]** attività. [Ulteriori informazioni](external-signal.md).

Puoi attivare i flussi di lavoro in diversi modi:

* Puoi attivare un flusso di lavoro in linea, ovvero dallo script principale di un **[!UICONTROL JavaScript code]** attività.
* Puoi attivare un flusso di lavoro al completamento di un altro:
   * Aggiungi uno script di inizializzazione al **[!UICONTROL End]** attività del flusso di lavoro iniziale.
   * Aggiungi il **[!UICONTROL External signal]** all’inizio del flusso di lavoro di destinazione.

      Al completamento del flusso di lavoro iniziale, viene pubblicato un evento. La transizione in uscita viene attivata e le variabili dell’evento vengono popolate. Quindi, l’evento viene ricevuto dal flusso di lavoro di destinazione.

      >[!TIP]
      >
      >Come best practice, quando aggiungi uno script a un’attività, racchiudi il nome dell’attività in due trattini, ad esempio: `-- end --`. [Ulteriori informazioni](workflow-best-practices.md) sulle best practice per i flussi di lavoro.

Sintassi della `PostEvent` metodo:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In questo esempio, al completamento del flusso di lavoro, viene trasmesso un breve testo al **segnale** attività del **wkfExampleReceiver** flusso di lavoro:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Poiché l’ultimo parametro è impostato su `false`, **wkfExampleReceiver** il flusso di lavoro viene attivato ogni volta che il flusso di lavoro iniziale viene completato.

Quando attivi i flussi di lavoro, ricorda quanto segue:

* La `PostEvent` viene eseguito in modo asincrono. Il comando viene inserito nella coda del server. Il metodo restituisce dopo la registrazione dell&#39;evento.
* Il flusso di lavoro di destinazione deve essere avviato. In caso contrario, viene scritto un errore nel file di registro.
* Se il flusso di lavoro di destinazione viene sospeso, il `PostEvent` viene messo in coda fino a quando il flusso di lavoro non riprende.
* L’attività attivata non richiede che un’attività sia in corso.

Questo video mostra come utilizzare metodi API statici:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Questo video mostra come attivare i flussi di lavoro:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagire con il database {#interact-example}

Gli esempi seguenti mostrano come eseguire queste azioni:

* Utilizza la `get` e `create` metodi sugli schemi per l’utilizzo di metodi SOAP non statici
* Creare metodi che eseguono query SQL
* Utilizza la `write` metodo per inserire, aggiornare ed eliminare record

Segui questi passaggi:

1. Definisci la query:

   * Recupera un’entità utilizzando il `create` nello schema corrispondente, ad esempio, il `xtk:workflow` schema. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Utilizza la `queryDef` per emettere una query SQL.

1. Esegui la query utilizzando `ExecuteQuery` metodo . [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Utilizza la `for each` per recuperare i risultati.

### Sintassi della `queryDef` metodo con `select` clausola

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

### `Create` metodo

#### Esempio 1: selezionare record e scrivere nel giornale di registrazione

I nomi interni dei flussi di lavoro che si trovano nella **wfExample** cartella selezionata. I risultati vengono ordinati per nome interno, in ordine crescente e scritti nel giornale di registrazione.

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

#### Esempio 2: eliminare i record

Vengono selezionati il nome, il cognome, l’e-mail e l’ID di tutti i destinatari che si chiamano Chris Smith. I risultati vengono ordinati per e-mail, in ordine crescente e scritti nel giornale di registrazione. A `delete` viene utilizzata per eliminare i record selezionati.

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

#### Esempio 3: selezionare record e scrivere nel giornale di registrazione

In questo esempio viene utilizzato un metodo non statico. L&#39;e-mail e l&#39;anno di nascita di tutti i destinatari le cui informazioni sono memorizzate nel **1234** e il cui nome di dominio e-mail inizia con &quot;adobe&quot; sono selezionati. I risultati vengono ordinati in ordine decrescente in base alla data di nascita. L’e-mail dei destinatari viene scritta nel giornale di registrazione.

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

### `Write` metodo

È possibile inserire, aggiornare ed eliminare i record. È possibile utilizzare `Write` su qualsiasi schema in Adobe Campaign. Poiché questo metodo è statico, non è necessario creare un oggetto. È possibile utilizzare le seguenti operazioni:

* La `update` funzionamento
* La `insertOrUpdate` con `_key` argomento per identificare il record da aggiornare

   Se non si specifica il **Destinatari** quindi, se esiste una corrispondenza, il record viene aggiornato in qualsiasi sottocartella. In caso contrario, il record viene creato nella radice **Destinatari** cartella.

* La `delete` funzionamento

>[!IMPORTANT]
> Se utilizzi Adobe Campaign v8, ti consigliamo di utilizzare il meccanismo di staging con **Acquisizione** e **Aggiornamento/eliminazione dati** API per `Write` in una tabella di Snowflake. [Maggiori informazioni](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

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

#### Esempio 2: eliminare i record

Questo esempio combina un metodo statico con un metodo non statico.

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

Questo video mostra come utilizzare metodi API non statici:
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
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Scrittura](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [funzione logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)
