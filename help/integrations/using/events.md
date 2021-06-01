---
product: campaign
title: Configurazione degli eventi
description: Scopri come configurare eventi per l’implementazione personalizzata
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 0%

---

# Configurazione di eventi per l’implementazione personalizzata {#events}

Parti di questa configurazione è uno sviluppo personalizzato e richiede quanto segue:

* Conoscenza di base dell’analisi JSON, XML e Javascript in Adobe Campaign.
* Conoscenza operativa delle API QueryDef e Writer.
* Nozioni di funzionamento di crittografia e autenticazione utilizzando chiavi private.

Poiché la modifica del codice Javascript richiede competenze tecniche, non tentare senza la comprensione appropriata.

## Eventi di elaborazione in JavaScript {#events-javascript}

### File JavaScript {#file-js}

La pipeline utilizza una funzione JavaScript per elaborare ogni messaggio. Questa funzione è definita dall&#39;utente.

È configurato nell&#39;opzione **[!UICONTROL NmsPipeline_Config]** sotto l&#39;attributo &quot;JSConnector&quot;. Questo javascript viene chiamato ogni volta che viene ricevuto un evento. Viene eseguito dal processo [!DNL pipelined].

Il file Javascript di esempio è cus:triggers.js.

### Funzione JavaScript {#function-js}

Il codice JavaScript [!DNL pipelined] deve iniziare con una funzione specifica.

Questa funzione viene chiamata una volta per ogni evento:

```
function processPipelineMessage(xmlTrigger) {}
```

Dovrebbe tornare come

```
<undefined/>
```

Riavvia [!DNL pipelined] dopo aver modificato il codice JavaScript.

### Formato dei dati del trigger {#trigger-format}

I dati [!DNL trigger] vengono passati alla funzione JS in formato XML.

* L&#39;attributo **[!UICONTROL @triggerId]** contiene il nome dell&#39; [!DNL trigger].
* L’elemento **Arricchimenti** in formato JSON contiene i dati generati da Adobe Analytics e viene allegato al trigger.
* **[!UICONTROL @offset]** è il &quot;puntatore&quot; del messaggio. Indica l’ordine del messaggio all’interno della coda.
* **[!UICONTROL @partition]** è un contenitore di messaggi all’interno della coda. L&#39;offset è relativo a una partizione. <br>Ci sono circa 15 partizioni nella coda.

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
>È un esempio specifico tratto da varie implementazioni possibili.

Il contenuto è definito in formato JSON in Adobe Analytics per ogni trigger.
Ad esempio, in un trigger LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** può contenere l’ID acquirente in formato stringa, utilizzato per eseguire la riconciliazione con i destinatari di Adobe Campaign. <br>Deve essere riconciliato per trovare l’ID acquirente, che è la chiave primaria.

* **[!UICONTROL timeGMT]** può contenere l’ora del trigger sul lato Adobe Analytics in formato Epoch UTC (secondi dall’1/01/1970 UTC).

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

### Eventi ordine di elaborazione{#order-events}

Gli eventi vengono elaborati uno alla volta, in base all’ordine di offset. Ogni thread di [!DNL pipelined] elabora una partizione diversa.

L’&quot;offset&quot; dell’ultimo evento recuperato viene memorizzato nel database. Pertanto, se il processo viene interrotto, viene riavviato dall’ultimo messaggio. Questi dati vengono memorizzati nello schema incorporato xtk:pipelineOffset.

Questo puntatore è specifico per ogni istanza e per ogni consumatore. Pertanto, quando molte istanze accedono alla stessa pipeline con consumatori diversi, ricevono tutti i messaggi e nello stesso ordine.

Il parametro **consumer** dell’opzione pipeline identifica l’istanza chiamante.

Attualmente, non è possibile avere code diverse per ambienti separati come &quot;staging&quot; o &quot;dev&quot;.

### Registrazione e gestione degli errori {#logging-error-handling}

I registri come logInfo() vengono indirizzati al registro [!DNL pipelined]. Errori come logError() vengono scritti nel registro [!DNL pipelined] e fanno sì che l&#39;evento venga messo in una coda di nuovi tentativi. In questo caso, è necessario controllare il registro pipeline.
I messaggi di errore vengono ritentati più volte nella durata impostata nelle opzioni [!DNL pipelined] .

A scopo di debug e monitoraggio, i dati del trigger completo vengono scritti nella tabella dell’attivatore nel campo &quot;data&quot; in formato XML. In alternativa, un logInfo() contenente i dati del trigger ha lo stesso scopo.

### Analisi dei dati {#data-parsing}

Questo codice Javascript di esempio analizza l’eVar01 negli arricchimenti.

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
Poiché questo codice viene utilizzato per tutti gli attivatori, la maggior parte dei dati non è necessaria. Pertanto, può essere lasciato vuoto se non presente.

### Memorizzazione del trigger {#storing-triggers-js}

>[!NOTE]
>
>È un esempio specifico tratto da varie implementazioni possibili.

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

Le prestazioni di questo codice devono essere ottimali in quanto viene eseguito ad alte frequenze e potrebbe causare potenziali effetti negativi per altre attività di marketing. Soprattutto se si elaborano più di un milione di eventi trigger all’ora sul server Marketing o se non viene sintonizzato correttamente.

Il contesto di questo JavaScript è limitato. Non tutte le funzioni dell’API sono disponibili. Ad esempio, getOption() o getCurrentdate() non funzionano.

Per accelerare l&#39;elaborazione, diversi thread di questo script vengono eseguiti contemporaneamente. Il codice deve essere thread safe.

## Memorizzazione degli eventi {#store-events}

>[!NOTE]
>
>È un esempio specifico tratto da varie implementazioni possibili.

### Schema evento pipeline {#pipeline-event-schema}

Gli eventi vengono memorizzati in una tabella di database. Viene utilizzato dalle campagne di marketing per indirizzare i clienti e arricchire le e-mail tramite i trigger.
Anche se ogni trigger può avere una struttura di dati distinta, tutti i trigger possono essere mantenuti in una singola tabella.
Il campo triggerType identifica da cui viene attivata l&#39;origine dei dati.

Di seguito è riportato un esempio di codice dello schema per questa tabella:

| Attributo | Tipo | Etichetta | Descrizione |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Lunga | Chiave principale | Chiave primaria interna del trigger. |
| dati | Per memoria | Dati di attivazione | Contenuto completo dei dati di attivazione in formato XML. A scopo di debug e controllo. |
| triggerType | Stringa 50 | TriggerType | Nome del trigger. Identifica il comportamento del cliente sul sito web. |
| shopper_id | Stringa 32 | shopper_id | Identificatore interno dell&#39;acquirente. Impostato dal flusso di lavoro di riconciliazione. Se zero, significa che il cliente è sconosciuto in Campaign. |
| shopper_key | Lunga | shopper_key | Identificatore esterno dell&#39;acquirente acquisito da Analytics. |
| creato | Datetime | Creato | L’ora in cui è stato creato l’evento in Campaign. |
| lastModified | Datetime | Ultima modifica | L’ultima volta che l’evento è stato modificato in Adobe. |
| timeGMT | Datetime | Timestamp | L’ora in cui l’evento è stato generato in Analytics. |

### Visualizzazione degli eventi {#display-events}

Gli eventi possono essere visualizzati con un modulo semplice basato sullo schema degli eventi.

>[!NOTE]
>
>Il nodo Evento pipeline non è incorporato e deve essere aggiunto, nonché il relativo modulo deve essere creato in Campaign. Queste operazioni sono riservate solo agli utenti esperti. Per ulteriori informazioni, consulta queste sezioni: [Gerarchia di navigazione](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy). e [Modifica di moduli](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Elaborazione degli eventi {#processing-the-events}

### Workflow di riconciliazione {#reconciliation-workflow}

La riconciliazione è il processo di corrispondenza del cliente da Adobe Analytics al database Adobe Campaign. Ad esempio, i criteri per la corrispondenza possono essere shopper_id.

Per motivi di prestazioni, la corrispondenza deve essere eseguita in modalità batch tramite un flusso di lavoro.
La frequenza deve essere impostata su 15 minuti per ottimizzare il carico di lavoro. Di conseguenza, il ritardo tra la ricezione di un evento in Adobe Campaign e la relativa elaborazione da parte di un flusso di lavoro di marketing è fino a 15 minuti.

### Opzioni per la riconciliazione delle unità in JavaScript {#options-unit-reconciliation}

È possibile eseguire la query di riconciliazione per ogni trigger nel JavaScript. Ha un impatto maggiore sulle prestazioni e fornisce risultati più veloci. Può essere richiesto per casi d’uso specifici quando è necessaria la reattività.

Può essere difficile da implementare se non è impostato alcun indice su shopper_id. Se i criteri si trovano su un server di database separato dal server di marketing, utilizza un collegamento al database che presenta prestazioni scadenti.

### Eliminare il flusso di lavoro {#purge-workflow}

I trigger vengono elaborati entro l’ora specificata. Il volume può essere di circa 1 milione di trigger all&#39;ora. Questo spiega perché è necessario implementare un flusso di lavoro di eliminazione. L&#39;eliminazione viene eseguita una volta al giorno ed elimina tutti gli attivatori che sono più vecchi di tre giorni.

### Flusso di lavoro della campagna {#campaign-workflow}

Il flusso di lavoro della campagna di attivazione è spesso simile ad altre campagne ricorrenti utilizzate.
Ad esempio, può iniziare con una query sui trigger che cercano eventi specifici nell’ultimo giorno. Tale destinazione viene utilizzata per inviare l’e-mail. Arricchimenti o dati possono provenire dal trigger. Può essere utilizzato in modo sicuro da Marketing in quanto non richiede alcuna configurazione.
