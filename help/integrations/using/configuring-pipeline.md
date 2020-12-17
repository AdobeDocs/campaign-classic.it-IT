---
solution: Campaign Classic
product: campaign
title: Configurazione della pipeline
description: Scopri come configurare la pipeline
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 0abdbbc33350cf6ec85488483dadb177e685818b
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 1%

---


# Configurazione della pipeline {#configuring-pipeline}

I parametri di autenticazione come l&#39;ID cliente, la chiave privata e l&#39;endpoint di autenticazione sono configurati nei file di configurazione dell&#39;istanza.
L&#39;elenco di attivatori da elaborare è configurato in un&#39;opzione in formato JSON.
I trigger vengono utilizzati per il targeting tramite un flusso di lavoro della campagna che invia e-mail. La campagna è impostata in modo che un cliente con entrambi gli eventi di attivazione riceva un’e-mail.

>[!CAUTION]
>
>In caso di distribuzione ibrida, accertati che la pipeline sia configurata su un&#39;istanza intermedia.

## Prerequisiti {#prerequisites}

Prima di avviare la configurazione, verificare che:

*  rilascio minimo di Adobe Campaign 20.3
*  versione Adobe Analytics Standard

Sarà inoltre necessario:

*  autenticazione del progetto Adobe I/O
* un IMSOrgID valido, l’identificatore del cliente del Experience Cloud  con  aggiunto Adobe Analytics
* Accesso sviluppatore all&#39;organizzazione IMS
* attiva la configurazione in  Adobe Analytics

## File di autenticazione e configurazione {#authentication-configuration}

L&#39;autenticazione è necessaria perché la pipeline è ospitata nell&#39;Adobe Experience Cloud.
Utilizza un paio di chiavi pubbliche e private. Questa procedura ha la stessa funzione di utente/password ma è più sicura.
L&#39;autenticazione è supportata per il Marketing Cloud tramite  progetto Adobe I/O.

## Passaggio 1: Creazione/aggiornamento  progetto Adobe I/O {#creating-adobe-io-project}

Per i clienti ospitati, puoi creare un ticket di assistenza clienti per abilitare la tua organizzazione con  Token account tecnici Adobe I/O per l&#39;integrazione Triggers.

Per i clienti di On Premise, fare riferimento alla pagina [Configuring  Adobe I/O for Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md). È necessario selezionare **[!UICONTROL Adobe Analytics]** quando si aggiunge API alla credenziale Adobe I/O .

## Passaggio 2: Configurazione dell&#39;opzione pipeline NmsPipeline_Config {#configuring-nmspipeline}

Una volta impostata l&#39;autenticazione, la pipeline recupererà gli eventi. Vengono elaborati solo gli attivatori configurati in  Adobe Campaign. Il trigger deve essere stato generato da  Adobe Analytics e inviato alla pipeline che elaborerà solo gli attivatori configurati in  Adobe Campaign.
L&#39;opzione può essere configurata anche con un carattere jolly per intercettare tutti i trigger, indipendentemente dal nome.

1. In  Adobe Campaign, accedere al menu delle opzioni in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in **[!UICONTROL Explorer]**.

1. Selezionare l&#39;opzione **[!UICONTROL NmsPipeline_Config]**.

1. Nel campo **[!UICONTROL Value (long text)]** potete incollare il seguente codice JSON, che specifica due attivatori. È necessario assicurarsi di rimuovere i commenti.

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
           "triggers": [ // Array of triggers.
               {
                   "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                   "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
               }, {
                   "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                   "jsConnector": "cus:triggers.js" // Can use the same JS for all.
               },
           ]
       }
   ]
   }
   ```

1. Potete anche scegliere di incollare il seguente codice JSON che cattura tutti i trigger.

   ```
   {
   "topics": [
     {
       "name": "triggers",
       "consumer":  "customer_dev",
       "triggers": [
         {
           "name": "*",
           "jsConnector": "cus:pipeline.js"
         }
       ]
     }
   ]
   }
   ```

### Il parametro Consumer {#consumer-parameter}

La tubazione funziona come un modello di fornitore e consumatore. I messaggi vengono consumati solo per un singolo consumatore: ogni consumatore riceve la propria copia dei messaggi.

Il parametro **Consumer** identifica l&#39;istanza come uno di questi consumatori. L&#39;identità dell&#39;istanza chiamerà la pipeline. Potete compilarlo con il nome dell&#39;istanza che si trova nella pagina Monitoraggio della console client.

Il servizio pipeline tiene traccia dei messaggi recuperati da ogni consumatore. L’utilizzo di consumatori diversi per diverse istanze consente di verificare che ogni messaggio venga inviato a ogni istanza.

### Suggerimenti per l&#39;opzione pipeline {#pipeline-option-recommendation}

Per configurare l&#39;opzione pipeline, attenersi alle seguenti raccomandazioni:

* Aggiungere o modificare attivatori in **[!UICONTROL Triggers]**, non modificare gli altri.
* Assicurati che il JSON sia valido. È possibile utilizzare una Convalida JSON, fare riferimento a questo [sito Web](http://jsonlint.com/), ad esempio.
* &quot;name&quot; corrisponde all&#39;ID attivatore. Un carattere jolly &quot;*&quot; intercetta tutti i trigger.
* &quot;Consumer&quot; corrisponde al nome dell&#39;istanza o dell&#39;applicazione chiamante.
* Pipeline supporta anche l&#39;argomento &quot;alias&quot;.
* Dopo aver apportato le modifiche, riavviare sempre la pipeline.

## Passaggio 3: Configurazione opzionale {#step-optional}

È possibile modificare alcuni parametri interni in base ai requisiti di carico, ma assicurarsi di verificarli prima di metterli in produzione.

L&#39;elenco dei parametri opzionali è riportato di seguito:

| Opzione | Descrizione |
|:-:|:-:|
| appName(Legacy) | AppID dell’applicazione OAuth registrata nell’applicazione giuramento legacy in cui è stata caricata la chiave pubblica. Per ulteriori informazioni, consulta questa [pagina](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint(Legacy) | URL per ottenere token gateway. Predefinito: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | La chiave privata, parte pubblica caricata nell’applicazione Legacy Oath, AES crittografata con l’opzione XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Disattiva l&#39;autenticazione. La connessione senza token gateway verrà accettata solo da alcuni endpoint pipeline di sviluppo. |
| findPipelineEndpoint | URL per trovare l&#39;endpoint di Pipeline Services da utilizzare per questo tenant. Predefinito: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Periodo tra due discariche del processo di stato interno in ```var/INSTANCE/pipelined.json.``` <br> Lo stato interno è accessibile anche su richiesta: ```http://INSTANCE:7781/pipelined/status``` |
| forzatoPipelineEndpoint | Disabilitare il rilevamento di PipelineServicesEndpoint per forzarlo |
| monitorServerPort | Il processo condotto sarà in ascolto su questa porta per fornire il processo di stato interno qui: ```http://INSTANCE:PORT/pipelined/status```. <br>Il valore predefinito è 7781 |
| puntatoreFlushMessageCount | Quando questo numero di messaggi viene elaborato, gli offset verranno salvati nel database. <br> Il valore predefinito è 1000 |
| puntatoreFlushPeriodSec | Dopo questo periodo, gli offset verranno salvati nel database. <br>Il valore predefinito è 5 (secondi) |
| processingJSThread | Numero di messaggi di elaborazione thread dedicati con connettori JS personalizzati. <br> Il valore predefinito è 4 |
| processingThread | Numero di messaggi di elaborazione thread dedicati con codice incorporato. <br>Il valore predefinito è 4 |
| tryPeriodSec | Ritardo tra i tentativi in caso di errori di elaborazione. <br>Il valore predefinito è 30 (secondi) |
| tryValiditySec | Ignora il messaggio se non è stato elaborato correttamente dopo questo periodo (troppi tentativi). <br>Il valore predefinito è 300 (secondi) |

### Avvio automatico processo tubato {#pipelined-process-autostart}

Il processo tubato deve essere avviato automaticamente.

Per questo, impostate l&#39;elemento &lt; pipeline > nel file di configurazione su autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Riavvio processo tubato {#pipelined-process-restart}

Per rendere effettive le modifiche è necessario riavviare il sistema:

```
nlserver restart pipelined@instance
```

## Passaggio 4: Convalida {#step-validation}

Per convalidare la configurazione della pipeline per il provisioning, attenetevi alla procedura seguente:

* Assicurarsi che il processo [!DNL pipelined] sia in esecuzione.
* Controllate i registri di connessione della pipeline nel file pipelining.log.
* Verificare la connessione e se i ping sono ricevuti. I clienti ospitati possono utilizzare il monitoraggio dalla console client.
