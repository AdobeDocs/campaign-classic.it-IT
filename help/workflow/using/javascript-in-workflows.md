---
product: campaign
title: Esempi di codice JavaScript nei flussi di lavoro
description: Questi esempi mostrano come utilizzare il codice JavaScript in un flusso di lavoro
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 3%

---

# Esempi di codice JavaScript nei flussi di lavoro{#javascript-in-workflows}



Questi esempi mostrano come utilizzare il codice JavaScript in un flusso di lavoro:

* [Scrivi nel database](#write-example)
* [Eseguire una query sul database](#read-example)
* [Attivare un flusso di lavoro utilizzando un metodo SOAP statico](#trigger-example)
* [Interagire con il database utilizzando un metodo SOAP non statico](#interact-example)

[Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) informazioni sui metodi SOAP statici e non statici.

In questi esempi viene utilizzata l&#39;estensione ECMAScript for XML (E4X). Con questa estensione, puoi combinare le chiamate JavaScript e le primitive XML nello stesso script.

Per provare questi esempi, segui questi passaggi:

1. Crea un flusso di lavoro e aggiungi queste attività al flusso di lavoro:
   1. Avvia attività
   1. Attività codice JavaScript
   1. Attività Fine

   [Ulteriori informazioni](building-a-workflow.md) informazioni sulla creazione di flussi di lavoro.

1. Aggiungi il codice JavaScript a un’attività. [Ulteriori informazioni](advanced-parameters.md).
1. Salva il flusso di lavoro.
1. Prova gli esempi:
   1. Avvia il flusso di lavoro. [Ulteriori informazioni](starting-a-workflow.md).
   1. Apri il diario. [Ulteriori informazioni](monitoring-workflow-execution.md#displaying-logs).

## Esempio 1: scrivere nel database{#write-example}

Per scrivere nel database, è possibile utilizzare il `Write` metodo su `xtk:session` schema:

1. Comporre una richiesta di scrittura in XML.

1. Scrivi il record:

   1. Chiama il `Write` metodo su `xtk:session` schema.

      >[!IMPORTANT]
      > Se utilizzi Adobe Campaign v8, ti consigliamo di utilizzare il meccanismo di staging con **Acquisizione** e **Aggiornamento/eliminazione dati** API per `Write` in una tabella di Snowflake. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

   1. Passa il codice XML come argomento per la richiesta di scrittura.

### Passaggio 1: comporre una richiesta di scrittura

È possibile aggiungere, aggiornare ed eliminare record.

#### Inserire un record

Perché il `insert` è l&#39;operazione predefinita, non è necessario specificarla.

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

Utilizza il `_update` operazione. [Ulteriori informazioni](../../configuration/using/data-oriented-apis.md).

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

Utilizza il `DeleteCollection` metodo. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Specifica queste informazioni:

* Schema della tabella da modificare
* Il `where` clausola necessaria per identificare il record da aggiornare, sotto forma di un elemento XML

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

Chiama il file non statico `Write` metodo su `xtk:session` schema:

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

Per eseguire una query sul database, è possibile utilizzare la proprietà non statica `xtk:queryDef` metodo di istanza:

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

Specifica queste informazioni:

* Schema della tabella da leggere
* L&#39;operazione
* Le colonne da restituire, in un `select` clausola
* Le condizioni, in un `where` clausola
* I criteri di filtraggio, in un `orderBy` clausola

Puoi utilizzare le seguenti operazioni:

| Operazione | Risultato |
| --- | --- |
| `select` | Zero o più elementi vengono restituiti come raccolta. |
| `getIfExists` | Viene restituito un elemento. Se non esiste alcun elemento di corrispondenza, viene restituito un elemento vuoto. |
| `get` | Viene restituito un elemento. Se non esiste alcun elemento di corrispondenza, viene restituito un errore. |
| `count` | Il numero di record corrispondenti viene restituito sotto forma di un elemento con un `count` attributo. |

Scrivi il `select`, `where`, e `orderBy` clausole come elementi XML:

* `select` clausola

  Specificare le colonne da restituire. Ad esempio, per selezionare il nome e il cognome della persona, scrivere il codice seguente:

  ```xml
  <select>
      <node expr="@firstName"/>
      <node expr="@lastName"/>
  </select>
  ```

  Con il `nms:recipient` schema, gli elementi vengono restituiti nel seguente formato:

  ```xml
  <recipient firstName="Bo" lastName="Didley"/>
  ```

* `where` clausola

  Per specificare le condizioni, utilizza una `where` clausola. Ad esempio, per selezionare i record che si trovano nel **Formazione** cartella, puoi scrivere questo codice:

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

* `orderBy` clausola

  Per ordinare il set di risultati, specificare `orderBy` come elemento XML con `sortDesc` attributo. Ad esempio, per ordinare i cognomi in ordine crescente, è possibile scrivere il codice seguente:

  ```xml
  <orderBy>
      <node expr="@lastName> sortDesc="false"/>
  </orderBy>
  ```

### Passaggio 2: creare un oggetto query

Per creare un’entità dal codice XML, utilizza `create(`*`content`*`)` metodo:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Aggiungi il prefisso `create(`*`content`*`)` con lo schema dell’entità da creare.

Il *`content`* l&#39;argomento è un argomento stringa ed è facoltativo. Questo argomento contiene il codice XML che descrive l&#39;entità.

### Passaggio 3: eseguire la query

Segui questi passaggi:

1. Chiama il `ExecuteQuery` metodo su `queryDef` entità:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Elabora i risultati:
   1. Eseguire iterazioni sui risultati del `select` mediante un costrutto di loop.
   1. Testare i risultati utilizzando `getIfExists` operazione.
   1. Contare i risultati, utilizzando `count` operazione.

#### Risultati di una `select` operazione

Tutte le corrispondenze vengono restituite come una raccolta:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Per scorrere i risultati, utilizzare `for each` loop:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

Il ciclo include una variabile di destinatario locale. Per ogni destinatario restituito nella raccolta di destinatari, viene stampata l’e-mail del destinatario. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) informazioni su `logInfo` funzione.

#### Risultati di una `getIfExists` operazione

Ogni corrispondenza viene restituita come elemento:

```xml
<recipient id="52,378,079">
```

Se non viene trovata alcuna corrispondenza, viene restituito un elemento vuoto:

```xml
<recipient/>
```

È possibile fare riferimento al nodo della chiave primaria, ad esempio `@id` attributo:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Risultato di un `get` operazione

Viene restituita una corrispondenza come elemento:

```xml
<recipient id="52,378,079">
```

Se non viene trovata alcuna corrispondenza, viene restituito un errore.

>[!TIP]
>
>Se sai che esiste una corrispondenza, utilizza `get` operazione. In caso contrario, utilizza `getIfExists` operazione. Se utilizzi questa best practice, gli errori rivelano problemi imprevisti. Se si utilizza `get` , non utilizzare il `try…catch` dichiarazione. Il problema viene gestito dal processo di gestione degli errori del flusso di lavoro.

#### Risultato di un `count` operazione

Un elemento con `count` viene restituito l&#39;attributo:

```xml
<recipient count="200">
```

Per utilizzare il risultato, fare riferimento a `@count` attributo:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Per `select` , aggiungi questo codice a un&#39;attività di codice JavaScript nel flusso di lavoro:

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

Perché il `select` è l&#39;operazione predefinita, non è necessario specificarla.

Questo video illustra come leggere dal database:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Attivare un flusso di lavoro {#trigger-example}

Puoi attivare i flussi di lavoro a livello di programmazione, ad esempio nei flussi di lavoro tecnici o per elaborare le informazioni immesse da un utente in una pagina di un’applicazione web.

L’attivazione dei flussi di lavoro avviene tramite l’utilizzo di eventi. Puoi utilizzare queste funzioni per gli eventi:

* Per pubblicare un evento, puoi utilizzare l’ `PostEvent` metodo. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Per ricevere un evento, puoi utilizzare **[!UICONTROL External signal]** attività. [Ulteriori informazioni](external-signal.md).

Puoi attivare i flussi di lavoro in diversi modi:

* Puoi attivare un flusso di lavoro in linea, ovvero dallo script principale di una **[!UICONTROL JavaScript code]** attività.
* Puoi attivare un flusso di lavoro al completamento di un altro:
   * Aggiungere uno script di inizializzazione al **[!UICONTROL End]** attività del flusso di lavoro iniziale.
   * Aggiungi il **[!UICONTROL External signal]** attività all’inizio del flusso di lavoro di target.

     Al completamento del flusso di lavoro iniziale, viene registrato un evento. La transizione in uscita viene attivata e le variabili dell’evento vengono compilate. Quindi, l’evento viene ricevuto dal flusso di lavoro di destinazione.

     >[!TIP]
     >
     >Come best practice, quando aggiungi uno script a un’attività, racchiudi il nome dell’attività in trattini doppi, ad esempio: `-- end --`. [Ulteriori informazioni](workflow-best-practices.md) informazioni sulle best practice per i flussi di lavoro.

Sintassi del `PostEvent` metodo:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In questo esempio, al completamento del flusso di lavoro, viene passato un breve testo a **segnale** attività del **wkfExampleReceiver** workflow:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Perché l&#39;ultimo parametro è impostato su `false`, il **wkfExampleReceiver** Il flusso di lavoro viene attivato ogni volta che viene completato il flusso di lavoro iniziale.

Quando attivi i flussi di lavoro, tieni presente i seguenti principi:

* Il `PostEvent` viene eseguito in modo asincrono. Il comando viene inserito nella coda del server. Il metodo restituisce dopo la registrazione dell’evento.
* È necessario avviare il flusso di lavoro di destinazione. In caso contrario, viene scritto un errore nel file di registro.
* Se il flusso di lavoro di destinazione è sospeso, il `PostEvent` viene inserito nella coda fino alla ripresa del flusso di lavoro.
* L’attività attivata non richiede che sia in corso un’attività.

Questo video illustra come utilizzare i metodi API statici:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Questo video mostra come attivare i flussi di lavoro:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagire con il database {#interact-example}

Questi esempi mostrano come eseguire queste azioni:

* Utilizza il `get` e `create` metodi sugli schemi per utilizzare metodi SOAP non statici
* Creare metodi che eseguono query SQL
* Utilizza il `write` metodo per inserire, aggiornare ed eliminare record

Segui questi passaggi:

1. Definisci la query:

   * Recuperare un&#39;entità utilizzando `create` nello schema corrispondente, ad esempio il metodo `xtk:workflow` schema. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Utilizza il `queryDef` per eseguire una query SQL.

1. Eseguire la query utilizzando `ExecuteQuery` metodo. [Ulteriori informazioni](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Utilizza il `for each` per recuperare i risultati.

### Sintassi del `queryDef` metodo con un `select` clausola

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

#### Esempio 1: selezionare i record e scrivere nel giornale di registrazione

I nomi interni dei flussi di lavoro che si trovano in **wfExamples** cartella selezionata. I risultati vengono ordinati in base al nome interno, in ordine crescente, e scritti nel giornale di registrazione.

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

Vengono selezionati il nome, il cognome, l’e-mail e l’ID di tutti i destinatari di nome Chris Smith. I risultati vengono ordinati per e-mail, in ordine crescente e scritti nel giornale di registrazione. A `delete` per eliminare i record selezionati viene utilizzata l&#39;operazione.

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

In questo esempio viene utilizzato un metodo non statico. L’anno e-mail e l’anno di nascita di tutti i destinatari le cui informazioni sono memorizzate in **1234** e il cui nome di dominio e-mail inizia con &quot;adobe&quot; vengono selezionati. I risultati sono ordinati in ordine decrescente per data di nascita. L&#39;e-mail dei destinatari viene scritta nel giornale di registrazione.

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

È possibile inserire, aggiornare ed eliminare record. È possibile utilizzare `Write` su qualsiasi schema in Adobe Campaign. Poiché questo metodo è statico, non è necessario creare un oggetto. Puoi utilizzare le seguenti operazioni:

* Il `update` operazione
* Il `insertOrUpdate` con il `_key` per identificare il record da aggiornare

  Se non si specifica **Destinatari** cartella, se esiste una corrispondenza, il record viene aggiornato in qualsiasi sottocartella. In caso contrario, il record viene creato nella radice **Destinatari** cartella.

* Il `delete` operazione

>[!IMPORTANT]
> Se utilizzi Adobe Campaign v8, ti consigliamo di utilizzare il meccanismo di staging con **Acquisizione** e **Aggiornamento/eliminazione dati** API per `Write` in una tabella di Snowflake. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

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
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Scrittura](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [funzione logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)
