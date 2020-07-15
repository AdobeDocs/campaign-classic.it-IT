---
title: Configurazione dell'integrazione
seo-title: Configurazione dell'integrazione
description: Configurazione dell'integrazione
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---


# Attiva eventi {#events}

## Eventi di elaborazione in JavaScript {#events-javascript}

### File JavaScript {#file-js}

Pipeline utilizza una funzione JavaScript per elaborare ciascun messaggio. Questa funzione è definita dall&#39;utente.

È configurato nell&#39; **[!UICONTROL NmsPipeline_Config]** opzione sotto l&#39;attributo &quot;JSConnector&quot;. Questo javascript viene chiamato ogni volta che viene ricevuto un evento. È gestito dal [!DNL pipelined] processo.

Il file JS di esempio è cus:triggers.js.

### Funzione JavaScript {#function-js}

Javascript deve iniziare con una funzione specifica. [!DNL pipelined]

Questa funzione viene chiamata una volta per ogni evento:

```
function processPipelineMessage(xmlTrigger) {}
```

Deve restituire come

```
<undefined/>
```

Riavviate [!DNL pipelined] dopo la modifica del JS.

### Attiva formato dati {#trigger-format}

I [!DNL trigger] dati vengono passati alla funzione JS. È in formato XML.

* L&#39; **[!UICONTROL @triggerId]** attributo contiene il nome dell&#39; [!DNL trigger].
* L&#39;elemento **di arricchimento** in formato JSON contiene i dati generati da  Analytics ed è collegato al trigger.
* **[!UICONTROL @offset]** è il &quot;puntatore&quot; del messaggio. Indica l’ordine del messaggio all’interno della coda.
* **[!UICONTROL @partitio]**n è un contenitore di messaggi all&#39;interno della coda. L&#39;offset è relativo a una partizione. <br>Ci sono circa 15 partizioni in coda.

Esempio:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Formato dati di arricchimento {#enrichment-format}

>[!NOTE]
>
>Si tratta di un esempio specifico ricavato da diverse possibili implementazioni.

Il contenuto è definito in  Analytics per ogni trigger. È in formato JSON.
Ad esempio, in un trigger LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** può contenere l&#39;ID acquirente che viene utilizzato per riconciliare con i destinatari della campagna. È in formato stringa. <br>Deve essere riconciliato per trovare l&#39;ID acquirente, che è la chiave primaria.

* **[!UICONTROL timeGMT]** può contenere l&#39;ora del trigger sul lato Analytics . È in formato Epoch UTC (secondi a partire dall&#39;1/01/1970 UTC).

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

### Ordine di elaborazione degli eventi {#order-events}

Gli eventi vengono elaborati uno alla volta, in ordine di offset. Ogni thread del [!DNL pipelined] processo elabora una partizione diversa.

L&#39;offset dell&#39;ultimo evento recuperato viene memorizzato nel database. Pertanto, se il processo viene interrotto, viene riavviato dall&#39;ultimo messaggio. Questi dati vengono memorizzati nello schema integrato xtk:pipelineOffset.

Questo puntatore è specifico per ogni istanza e per ogni consumatore. Pertanto, quando molti casi accedono alla stessa pipeline con consumatori diversi, ciascuno riceve tutti i messaggi e nello stesso ordine.

Il parametro &quot;consumer&quot; dell&#39;opzione pipeline identifica l&#39;istanza chiamante.

Al momento, non è possibile avere code diverse per ambienti separati come &#39;staging&#39; o &#39;dev&#39;.

### Registrazione e gestione degli errori {#logging-error-handling}

I registri come logInfo() vengono indirizzati al [!DNL pipelined] registro. Errori come logError() vengono scritti nel [!DNL pipelined] registro e l&#39;evento viene inserito in una coda di tentativi. Controllare il registro tubato.
I messaggi di errore vengono ripetuti più volte nella durata impostata nelle [!DNL pipelined] opzioni.

A scopo di debug e monitoraggio, i dati dell&#39;attivatore completo vengono scritti nella tabella dell&#39;attivatore. Si trova nel campo &quot;data&quot; in formato XML. In alternativa, un logInfo() contenente i dati di attivazione ha lo stesso scopo.

### Analisi dei dati {#data-parsing}

Questo codice JS di esempio analizza la eVar01 negli arricchimenti.

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

Prestate attenzione nell’analisi per evitare errori.
Poiché questo codice è utilizzato per tutte le attivazioni, la maggior parte dei dati non è necessaria. Pertanto, può essere lasciato vuoto se non presente.

### Memorizzazione del trigger {#storing-triggers-js}

>[!NOTE]
>
>Si tratta di un esempio specifico ricavato da diverse possibili implementazioni.

Questo codice JS di esempio salva il trigger nel database.

```
function processPipelineMessage(xmlTrigger)
 {```
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

Le prestazioni di questo codice devono essere ottimali in quanto viene eseguito a frequenze elevate. Ci sono potenziali effetti negativi per altre attività di marketing. Soprattutto se l&#39;elaborazione di più di un milione di eventi di attivazione all&#39;ora sul server Marketing. Oppure se non è sintonizzato correttamente.

Il contesto di questo Javascript è limitato. Non tutte le funzioni dell&#39;API sono disponibili. Ad esempio, getOption() o getCurrentdate() non funzionano.

Per accelerare l&#39;elaborazione, diversi thread di questo script vengono eseguiti contemporaneamente. Il codice deve essere thread safe.

## Memorizzazione degli eventi {#store-events}

>[!NOTE]
>
>Si tratta di un esempio specifico ricavato da diverse possibili implementazioni.

### Schema evento pipeline {#pipeline-event-schema}

Gli eventi sono memorizzati in una tabella di database. Viene utilizzato dalle campagne di marketing per indirizzare i clienti e arricchire le e-mail tramite attivatori.
Anche se ogni trigger può avere una struttura dati distinta, tutti i trigger possono essere mantenuti in una singola tabella.
Il campo triggerType identifica da quale trigger provengono i dati.

Di seguito è riportato un esempio di codice dello schema per la tabella seguente:

| Attributo | Tipo | Etichetta | Descrizione |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Long | Chiave primaria | Chiave primaria interna dell&#39;attivatore. |
| data | Per memoria | Trigger Data | Il contenuto completo dei dati di attivazione in formato XML. A scopo di debug e audit. |
| triggerType | Stringa 50 | TriggerType | Nome dell&#39;attivatore. Identifica il comportamento del cliente sul sito Web. |
| shopper_id | Stringa 32 | shopper_id | Identificatore interno dell&#39;acquirente. Impostato dal flusso di lavoro di riconciliazione. Se zero, significa che il cliente è sconosciuto in Campaign. |
| shopper_key | Long | shopper_key | Identificatore esterno dell&#39;acquirente acquisito da  Analytics. |
| created | Datetime | Creato | L&#39;ora in cui è stato creato l&#39;evento in Campaign. |
| lastModified | Datetime | Ultima modifica | L’ultima volta che l’evento è stato modificato in Adobe. |
| timeGMT | Datetime | Timestamp | L’ora in cui l’evento è stato generato in  Analytics. |

### Visualizzazione degli eventi {#display-events}

Gli eventi possono essere visualizzati con un semplice modulo basato sullo schema degli eventi.

>[!NOTE]
>
>Il nodo Evento pipeline non è integrato e deve essere aggiunto, così come il modulo correlato deve essere creato in Campaign. Queste operazioni sono riservate solo agli utenti esperti. Per ulteriori informazioni, consulta le sezioni seguenti: [Gerarchia](../../configuration/using/about-navigation-hierarchy.md) di navigazione e [modifica dei moduli](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Elaborazione degli eventi {#processing-the-events}

### Flusso di lavoro di riconciliazione {#reconciliation-workflow}

Riconciliazione è il processo di corrispondenza del cliente da  Analytics al database Campaign. Ad esempio, i criteri per la corrispondenza possono essere shopper_id.

Per motivi di prestazioni, la corrispondenza deve essere eseguita in modalità batch tramite un flusso di lavoro.
La frequenza deve essere impostata su 15 minuti per ottimizzare il carico di lavoro. Di conseguenza, il ritardo tra la ricezione di un evento in  Adobe Campaign e la relativa elaborazione da parte di un flusso di lavoro di marketing è di 15 minuti.

### Opzioni per la riconciliazione di unità in JavaScript {#options-unit-reconciliation}

In teoria, è possibile eseguire la query di riconciliazione per ogni trigger in JavaScript. Ha un impatto maggiore sulle prestazioni e offre risultati più rapidi. Potrebbe essere richiesto per casi d&#39;uso specifici quando è necessaria la reattività.

Può essere difficile farlo se non è impostato alcun indice su shopper_id. Se i criteri si trovano su un server di database separato da quello di marketing, utilizza un collegamento al database con prestazioni insufficienti.

### Flusso di lavoro di eliminazione {#purge-workflow}

Gli attivatori vengono elaborati entro l&#39;ora, quindi non c&#39;è motivo di mantenerli per molto tempo. Il volume può essere di circa 1 milione di attivatori all&#39;ora. Questo spiega perché è necessario implementare un flusso di lavoro di eliminazione. L&#39;eliminazione elimina tutti i trigger con durata superiore a tre giorni ed è eseguita una volta al giorno.

### Flusso di lavoro campagna {#campaign-workflow}

Il flusso di lavoro della campagna di attivazione è spesso simile ad altre campagne ricorrenti utilizzate.
Ad esempio, può iniziare con una query sui trigger alla ricerca di eventi specifici durante l&#39;ultimo giorno. Tale destinazione viene utilizzata per inviare l’e-mail. L&#39;arricchimento o i dati possono provenire dal trigger. Può essere utilizzato in modo sicuro da Marketing poiché non richiede alcuna configurazione.
