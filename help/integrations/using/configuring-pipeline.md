---
product: campaign
title: Configurazione della pipeline
description: Scopri come configurare la pipeline
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 1%

---

# Configurazione della pipeline {#configuring-pipeline}

I parametri di autenticazione come l’ID cliente, la chiave privata e l’endpoint di autenticazione sono configurati nei file di configurazione dell’istanza.
L’elenco dei trigger da elaborare è configurato in un’opzione in formato JSON.
I trigger vengono utilizzati per il targeting tramite un flusso di lavoro della campagna che invia e-mail. La campagna è configurata in modo che un cliente con entrambi gli eventi di attivazione riceva un’e-mail.

>[!CAUTION]
>
>In caso di distribuzione ibrida, assicurati che la pipeline sia configurata in un’istanza intermedia.

## Prerequisiti {#prerequisites}

Prima di avviare questa configurazione, controlla che stai utilizzando:

* Adobe Campaign 20.3, 20.2.4, 19.1.8 o [!DNL Gold Standard] 11 minimo
* Versione Adobe Analytics Standard

Sarà inoltre necessario:

* Adobe I/O di autenticazione del progetto
* è stato aggiunto un IMSOrgID valido, l’identificatore del cliente Experience Cloud con Adobe Analytics
* Accesso per sviluppatori all’organizzazione IMS
* configurazione trigger eseguita in Adobe Analytics

## File di autenticazione e configurazione {#authentication-configuration}

L’autenticazione è necessaria perché la pipeline è ospitata in Adobe Experience Cloud.
Utilizza un paio di chiavi pubbliche e private. Questo processo ha la stessa funzione di utente/password ma è più sicuro.
L’autenticazione è supportata per il Marketing Cloud tramite Progetto Adobe I/O.

## Passaggio 1: Creazione/aggiornamento del progetto Adobe I/O {#creating-adobe-io-project}

Per i clienti in hosting, puoi creare un ticket di assistenza clienti per abilitare la tua organizzazione con i token account tecnici Adobe I/O per l’integrazione Triggers.

Per i clienti On Premise , consulta la pagina [Adobe I/O di configurazione per Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) . Tieni presente che devi selezionare **[!UICONTROL Adobe Analytics]** durante l’aggiunta di API alle credenziali di Adobe I/O.

## Passaggio 2: Configurazione dell’opzione della pipeline NmsPipeline_Config {#configuring-nmspipeline}

Una volta impostata l’autenticazione, la pipeline recupererà gli eventi. Elabora solo gli attivatori configurati in Adobe Campaign. Il trigger deve essere stato generato da Adobe Analytics e inviato alla pipeline che elaborerà solo gli attivatori configurati in Adobe Campaign.
È inoltre possibile configurare l’opzione con un carattere jolly per individuare tutti i trigger, indipendentemente dal nome.

1. In Adobe Campaign, accedi al menu delle opzioni in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** nel **[!UICONTROL Explorer]**.

1. Selezionare l&#39;opzione **[!UICONTROL NmsPipeline_Config]**.

1. Nel campo **[!UICONTROL Value (long text)]** puoi incollare il seguente codice JSON, che specifica due trigger. È necessario assicurarsi di rimuovere i commenti.

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

1. Puoi anche scegliere di incollare il seguente codice JSON che cattura tutti i trigger.

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

La pipeline funziona come un modello di fornitore e di consumatore. I messaggi vengono utilizzati solo per un singolo consumatore: ogni consumatore ottiene la propria copia dei messaggi.

Il parametro **Consumer** identifica l&#39;istanza come uno di questi consumatori. L’identità dell’istanza chiamerà la pipeline. Puoi riempirlo con il nome dell’istanza che si trova nella pagina Monitoraggio della Console client.

Il servizio pipeline tiene traccia dei messaggi recuperati da ogni consumatore. L’utilizzo di consumatori diversi per istanze diverse consente di assicurarti che ogni messaggio venga inviato a ogni istanza.

### Raccomandazioni sulle opzioni della pipeline {#pipeline-option-recommendation}

Per configurare l’opzione Pipeline, segui questi consigli:

* Aggiungi o modifica attivatori sotto **[!UICONTROL Triggers]**, non devi modificare il resto.
* Assicurati che il JSON sia valido. È possibile utilizzare una convalida JSON, per esempio, fare riferimento a questo [sito Web](http://jsonlint.com/).
* &quot;name&quot; corrisponde all’ID trigger. Un carattere jolly &quot;*&quot; rileva tutti gli attivatori.
* &quot;Consumer&quot; corrisponde al nome dell&#39;istanza o dell&#39;applicazione chiamante.
* Pipelined supporta anche l’argomento &quot;alias&quot;.
* È sempre necessario riavviare la pipeline dopo aver apportato modifiche.

## Passaggio 3: Configurazione opzionale {#step-optional}

Puoi modificare alcuni parametri interni in base ai requisiti di caricamento, ma assicurati di testarli prima di inserirli in produzione.

L&#39;elenco dei parametri facoltativi è disponibile di seguito:

| Opzione | Descrizione |
|:-:|:-:|
| appName(Legacy) | AppID dell’applicazione OAuth registrata nell’applicazione Oath legacy in cui è stata caricata la chiave pubblica. Per ulteriori informazioni, consulta questa [pagina](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint(Legacy) | URL per ottenere token gateway. Predefinito: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | La chiave privata, parte pubblica caricata nell&#39;applicazione Oath legacy, AES crittografato con l&#39;opzione XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Disattiva l’autenticazione, la connessione senza token gateway verrà accettata solo da alcuni endpoint della pipeline di sviluppo. |
| discoverPipelineEndpoint | URL per trovare l’endpoint di Pipeline Services da utilizzare per questo tenant. Predefinito: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Il periodo tra due immagini del processo di stato interno in ```var/INSTANCE/pipelined.json.``` <br> Lo stato interno è accessibile anche su richiesta: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Disattiva il rilevamento di PipelineServicesEndpoint per forzarlo |
| monitorServerPort | Il processo condotto ascolterà su questa porta per fornire il processo di stato interno qui: ```http://INSTANCE:PORT/pipelined/status```. <br>Il valore predefinito è 7781 |
| puntatoreFlushMessageCount | Quando questo numero di messaggi viene elaborato, gli offset verranno salvati nel database. <br> Il valore predefinito è 1000 |
| puntatoreFlushPeriodSec | Dopo questo periodo, gli offset verranno salvati nel database. <br>Il valore predefinito è 5 (sec) |
| processingJSThreads | Numero di messaggi dedicati per l’elaborazione di thread con connettori JS personalizzati. <br> Il valore predefinito è 4 |
| processingThreads | Numero di thread dedicati che elaborano messaggi con codice incorporato. <br>Il valore predefinito è 4 |
| tryPeriodSec | Ritardo tra tentativi in caso di errori di elaborazione. <br>Il valore predefinito è 30 (sec) |
| tryValiditySec | Ignora il messaggio se non viene elaborato correttamente dopo questo periodo (troppi tentativi). <br>Il valore predefinito è 300 (sec) |

### Avvio automatico del processo pipeline {#pipelined-process-autostart}

Il processo pipeline deve essere avviato automaticamente.

Per questo, imposta l&#39;elemento &lt; pipelined > nel file di configurazione su autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Riavvio processo pipeline {#pipelined-process-restart}

Per rendere effettive le modifiche è necessario riavviare il sistema:

```
nlserver restart pipelined@instance
```

## Passaggio 4: Convalida {#step-validation}

Per convalidare la configurazione della pipeline per il provisioning, segui i passaggi seguenti:

* Assicurati che il processo [!DNL pipelined] sia in esecuzione.
* Controlla il file pipelined.log per i registri di connessione della pipeline.
* Verifica la connessione e se i ping vengono ricevuti. I clienti ospitati possono utilizzare il monitoraggio dalla console client.
