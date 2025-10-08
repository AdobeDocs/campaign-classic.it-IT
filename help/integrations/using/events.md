---
product: campaign
title: Configurazione degli eventi
description: Scopri come configurare gli eventi per l’implementazione personalizzata
feature: Triggers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 1%

---

# Configurazione di eventi per l’implementazione personalizzata {#events}



Parti di questa configurazione sono sviluppi personalizzati e richiedono quanto segue:

* Conoscenza operativa dell’analisi JSON, XML e Javascript in Adobe Campaign.
* Conoscenza operativa delle API QueryDef e Writer.
* Nozioni di lavoro di crittografia e autenticazione mediante chiavi private.

Poiché la modifica del codice JavaScript richiede competenze tecniche, non tentare senza aver compreso il codice.

## Elaborazione di eventi in JavaScript {#events-javascript}

### File JavaScript {#file-js}

La pipeline utilizza una funzione JavaScript per elaborare ogni messaggio. Questa funzione è definita dall’utente.

È configurato nell&#39;opzione **[!UICONTROL NmsPipeline_Config]** nell&#39;attributo &quot;JSConnector&quot;. Questo JavaScript viene chiamato ogni volta che viene ricevuto un evento. Viene eseguito dal processo [!DNL pipelined].

Il file JavaScript di esempio è cus:triggers.js.

### Funzione JavaScript {#function-js}

Il codice JavaScript [!DNL pipelined] deve iniziare con una funzione specifica.

Questa funzione viene chiamata una volta per ogni evento:

```
function processPipelineMessage(xmlTrigger) {}
```

Deve restituire come

```
<undefined/>
```

Riavviare [!DNL pipelined] dopo aver modificato JavaScript.

### Attiva formato dati {#trigger-format}

I dati [!DNL trigger] vengono passati alla funzione JS in formato XML.

* L&#39;attributo **[!UICONTROL @triggerId]** contiene il nome di [!DNL trigger].
* L&#39;elemento **arricchimenti** in formato JSON contiene i dati generati da Adobe Analytics ed è associato al trigger.
* **[!UICONTROL @offset]** è il &quot;puntatore&quot; al messaggio. Indica l’ordine del messaggio all’interno della coda.
* **[!UICONTROL @partition]** è un contenitore di messaggi all&#39;interno della coda. L&#39;offset è relativo a una partizione. <br>Nella coda sono presenti circa 15 partizioni.

Esempio:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Arricchimento del formato dei dati {#enrichment-format}

>[!NOTE]
>
>Si tratta di un esempio specifico da varie implementazioni possibili.

Il contenuto è definito in formato JSON in Adobe Analytics per ogni trigger.
Ad esempio, in un trigger LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** può contenere l&#39;ID acquirente in formato stringa utilizzato per eseguire la riconciliazione con i destinatari di Adobe Campaign. <br>È necessario riconciliarlo per trovare l&#39;ID acquirente, che è la chiave primaria.

* **[!UICONTROL timeGMT]** può contenere l&#39;ora del trigger sul lato Adobe Analytics in formato epoca UTC (secondi dal 01/01/1970 UTC).

Esempio:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### Ordine di elaborazione degli eventi{#order-events}

Gli eventi vengono elaborati uno alla volta, in ordine di offset. Ogni thread di [!DNL pipelined] elabora una partizione diversa.

L&#39;offset dell&#39;ultimo evento recuperato viene memorizzato nel database. Pertanto, se il processo viene interrotto, viene riavviato dall’ultimo messaggio. Questi dati sono archiviati nello schema predefinito xtk:pipelineOffset.

Questo puntatore è specifico per ogni istanza e per ogni consumer. Pertanto, quando molte istanze accedono alla stessa pipeline con consumer diversi, ognuna riceve tutti i messaggi e nello stesso ordine.

Il parametro **consumer** dell&#39;opzione pipeline identifica l&#39;istanza chiamante.

Attualmente, non è possibile avere code diverse per ambienti separati, ad esempio &quot;staging&quot; o &quot;dev&quot;.

### Registrazione e gestione degli errori {#logging-error-handling}

I registri come logInfo() vengono indirizzati al registro [!DNL pipelined]. Errori quali logError() vengono scritti nel registro [!DNL pipelined] e causano l&#39;inserimento dell&#39;evento in una coda di nuovi tentativi. In questo caso, controlla il registro pipeline.
I messaggi in errore vengono ritentati più volte nel periodo impostato nelle opzioni [!DNL pipelined].

A scopo di debug e monitoraggio, i dati a trigger completi vengono scritti nella tabella dei trigger nel campo &quot;data&quot; in formato XML. In alternativa, un logInfo() contenente i dati del trigger ha lo stesso scopo.

### Analisi dei dati {#data-parsing}

Questo esempio di codice JavaScript analizza l’eVar01 negli arricchimenti.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

Presta attenzione durante l’analisi per evitare errori.
Poiché questo codice viene utilizzato per tutti i trigger, la maggior parte dei dati non è richiesta. Pertanto, può essere lasciato vuoto quando non presente.

### Memorizzazione del trigger {#storing-triggers-js}

>[!NOTE]
>
>Si tratta di un esempio specifico da varie implementazioni possibili.

Questo codice JS di esempio salva il trigger nel database.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>;
 }
```

### Vincoli {#constraints}

Le prestazioni di questo codice devono essere ottimali poiché viene eseguito ad alte frequenze e potrebbe causare potenziali effetti negativi per altre attività di marketing. Specialmente se elabora più di un milione di eventi trigger all’ora sul server Marketing o se non è regolato correttamente.

Il contesto di questo JavaScript è limitato. Non sono disponibili tutte le funzioni dell’API. Ad esempio, getOption() o getCurrentdate() non funzionano.

Per consentire un&#39;elaborazione più rapida, vengono eseguiti contemporaneamente diversi thread di questo script. Il codice deve essere thread safe.

## Memorizzazione degli eventi {#store-events}

>[!NOTE]
>
>Si tratta di un esempio specifico da varie implementazioni possibili.

### Schema evento pipeline {#pipeline-event-schema}

Gli eventi vengono memorizzati in una tabella di database. Viene utilizzato dalle campagne di marketing per eseguire il targeting dei clienti e arricchire le e-mail utilizzando i trigger.
Anche se ogni trigger può avere una struttura di dati distinta, tutti i trigger possono essere tenuti in una singola tabella.
Il campo triggerType identifica il trigger da cui hanno origine i dati.

Di seguito è riportato un codice schema di esempio per questa tabella:

| Attributo | Tipo | Etichetta | Descrizione |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Lungo | Chiave primaria | Chiave primaria interna del trigger. |
| dati | Per memoria | Dati trigger | Contenuto completo dei dati del trigger in formato XML. A scopo di debug e audit. |
| triggerType | Stringa 50 | TriggerType | Nome del trigger. Identifica il comportamento del cliente sul sito web. |
| shopper_id | Stringa 32 | shopper_id | L’identificatore interno dell’acquirente. Impostato dal flusso di lavoro di riconciliazione. Se è zero, significa che il cliente è sconosciuto in Campaign. |
| shopper_key | Lungo | shopper_key | L’identificatore esterno dell’acquirente acquisito da Analytics. |
| creato | Data e ora | Creato | L’ora in cui l’evento è stato creato in Campaign. |
| lastModified | Data e ora | Ultima modifica | L’ultima volta che l’evento è stato modificato in Adobe. |
| timeGMT | Data e ora | Marca temporale | L’ora in cui l’evento è stato generato in Analytics. |

### Visualizzazione degli eventi {#display-events}

Gli eventi possono essere visualizzati con un semplice modulo basato sullo schema degli eventi.

>[!NOTE]
>
>Il nodo Evento pipeline non è incorporato e deve essere aggiunto, così come il modulo correlato deve essere creato in Campaign. Queste operazioni sono riservate esclusivamente agli utenti esperti. Per ulteriori informazioni, consulta [Modifica dei moduli](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Elaborazione degli eventi {#processing-the-events}

### Flusso di lavoro riconciliazione {#reconciliation-workflow}

La riconciliazione è il processo di corrispondenza tra il cliente di Adobe Analytics e il database di Adobe Campaign. Ad esempio, il criterio di corrispondenza può essere shopper_id.

Per motivi di prestazioni, la corrispondenza deve essere eseguita in modalità batch da un flusso di lavoro.
La frequenza deve essere impostata su 15 minuti per ottimizzare il carico di lavoro. Di conseguenza, il ritardo tra la ricezione di un evento in Adobe Campaign e la sua elaborazione da parte di un flusso di lavoro di marketing può arrivare a 15 minuti.

### Opzioni per la riconciliazione delle unità in JavaScript {#options-unit-reconciliation}

È possibile eseguire la query di riconciliazione per ogni trigger in JavaScript. Ha un impatto maggiore sulle prestazioni e fornisce risultati più rapidi. Potrebbe essere necessario per casi d’uso specifici quando è necessaria la reattività.

Può essere difficile da implementare se non è impostato alcun indice su shopper_id. Se i criteri si trovano su un server di database separato rispetto al server di marketing, viene utilizzato un database link con prestazioni scadenti.

### Rimuovi flusso di lavoro {#purge-workflow}

Gli attivatori vengono elaborati entro un’ora. Il volume può essere di circa 1 milione di trigger all&#39;ora. Spiega perché è necessario implementare un flusso di lavoro di eliminazione. L’eliminazione viene eseguita una volta al giorno ed elimina tutti i trigger che risalgono a più di tre giorni prima.

### Flusso di lavoro della campagna {#campaign-workflow}

Il flusso di lavoro della campagna di attivazione è spesso simile ad altre campagne ricorrenti che sono state utilizzate.
Ad esempio, può iniziare con una query sui trigger che cercano eventi specifici durante l’ultimo giorno. La destinazione viene utilizzata per inviare l’e-mail. Arricchimenti o dati possono provenire dal trigger. Può essere utilizzato in modo sicuro da Marketing in quanto non richiede alcuna configurazione.
