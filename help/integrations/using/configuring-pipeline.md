---
product: campaign
title: Configurazione della pipeline
description: Scopri come configurare la pipeline
feature: Triggers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# Configurazione della pipeline {#configuring-pipeline}



I parametri di autenticazione come l’ID cliente, la chiave privata e l’endpoint di autenticazione sono configurati nei file di configurazione dell’istanza.
L’elenco dei trigger da elaborare è configurato in un’opzione in formato JSON.
I trigger vengono utilizzati per il targeting da un flusso di lavoro della campagna che invia e-mail. La campagna è impostata in modo che un cliente con entrambi gli eventi di attivazione riceva un’e-mail.

## Prerequisiti {#prerequisites}

Prima di avviare questa configurazione, verifica di utilizzare:

* Almeno una delle seguenti build di Adobe Campaign:
   * 19.1.8.9039
   * 19.1.4.9032 - Gold Standard 11
   * 20.2.4.9187
   * 20.3.1.
* Versione Adobe Analytics Standard

Sono inoltre necessari:

* Autenticazione progetto di Adobe I/O
* un ID organizzazione valido: per trovare l’ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}
* accesso per sviluppatori all’organizzazione
* configurazione dei trigger eseguita in Adobe Analytics

## File di autenticazione e configurazione {#authentication-configuration}

È necessaria l’autenticazione perché la pipeline è ospitata in Adobe Experience Cloud.
Utilizza una coppia di chiavi pubbliche e private. Questo processo ha la stessa funzione di un utente/password, ma è più sicuro.
L’autenticazione è supportata per il Marketing Cloud tramite il progetto Adobe I/O.

## Passaggio 1: creazione/aggiornamento del progetto Adobe I/O {#creating-adobe-io-project}

Per i clienti in hosting, puoi creare un ticket di assistenza clienti per abilitare la tua organizzazione con Adobi I/O di token di account tecnici per l’integrazione Triggers.

Per i clienti On-Premise, consulta [Configurazione di Adobe I/O per Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) pagina. Tieni presente che devi selezionare **[!UICONTROL Adobe Analytics]** durante l’aggiunta dell’API alle credenziali Adobe I/O.

## Passaggio 2: configurazione dell’opzione NmsPipeline_Config pipeline {#configuring-nmspipeline}

Una volta impostata l’autenticazione, la pipeline recupererà gli eventi. Elabora solo i trigger configurati in Adobe Campaign. Il trigger deve essere stato generato da Adobe Analytics e inviato alla pipeline, che elaborerà solo i trigger configurati in Adobe Campaign.
L’opzione può anche essere configurata con un carattere jolly per acquisire tutti i trigger, indipendentemente dal nome.

1. In Adobe Campaign, accedi al menu delle opzioni in **[!UICONTROL Administration]** > **[!UICONTROL Platform]**  > **[!UICONTROL Options]** nel **[!UICONTROL Explorer]**.

1. Seleziona la **[!UICONTROL NmsPipeline_Config]** opzione.

1. In **[!UICONTROL Value (long text)]** , puoi incollare il seguente codice JSON, che specifica due trigger. Assicurati di rimuovere i commenti.

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

1. Puoi anche scegliere di incollare il seguente codice JSON che rileva tutti i trigger.

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

La pipeline funziona come un modello di fornitore e di consumatore. I messaggi vengono utilizzati solo per un singolo consumatore: ogni consumatore riceve la propria copia dei messaggi.

Il **Consumatore** Il parametro identifica l’istanza come uno di questi consumer. L’identità dell’istanza chiamerà la pipeline. È possibile compilarlo con il nome dell’istanza che si trova nella pagina Monitoraggio della console client.

Il servizio pipeline tiene traccia dei messaggi recuperati da ciascun consumatore. L’utilizzo di consumer diversi per istanze diverse consente di assicurarsi che ogni messaggio venga inviato a ogni istanza.

### Raccomandazioni sulle opzioni della pipeline {#pipeline-option-recommendation}

Per configurare l’opzione Pipeline, segui queste raccomandazioni:

* Aggiungi o modifica trigger in **[!UICONTROL Triggers]**, non modificare il resto.
* Verifica che il JSON sia valido. Puoi utilizzare una convalida JSON, fai riferimento a questa [sito web](https://jsonlint.com/) ad esempio.
* &quot;name&quot; corrisponde all’ID del trigger. Un carattere jolly &quot;*&quot; acquisirà tutti i trigger.
* &quot;Consumer&quot; corrisponde al nome dell’istanza o dell’applicazione chiamante.
* Pipelined supporta anche l’argomento &quot;alias&quot;.
* Dopo aver apportato modifiche, è sempre necessario riavviare la pipeline.

## Passaggio 3: configurazione opzionale {#step-optional}

Puoi modificare alcuni parametri interni in base ai requisiti di carico, ma assicurati di testarli prima di metterli in produzione.

L’elenco dei parametri opzionali è disponibile di seguito:

| Opzione | Descrizione |
|:-:|:-:|
| appName(Legacy) | AppID dell’applicazione OAuth registrata nell’applicazione Oath legacy in cui è stata caricata la chiave pubblica. Per ulteriori informazioni, consulta questa [pagina](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint(Legacy) | URL per ottenere i token del gateway. Predefinito: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | La chiave privata, parte pubblica caricata nell’applicazione Oath legacy, AES è crittografata con l’opzione XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Disabilita l’autenticazione: la connessione senza token gateway verrà accettata solo da alcuni endpoint della pipeline di sviluppo. |
| findPipelineEndpoint | URL per trovare l’endpoint dei servizi di pipeline da utilizzare per questo tenant. Predefinito: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Periodo tra due immagini del processo di stato interno in ```var/INSTANCE/pipelined.json.``` <br> Lo stato interno è accessibile anche on-demand qui: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Disattiva il rilevamento di PipelineServicesEndpoint per forzarlo |
| monitorServerPort | Il processo pipeline ascolterà su questa porta per fornire il processo di stato interno qui: ```http://INSTANCE:PORT/pipelined/status```. <br>Il valore predefinito è 7781 |
| pointerFlushMessageCount | Quando questo numero di messaggi viene elaborato, gli offset vengono salvati nel database. <br> Il valore predefinito è 1000 |
| pointerFlushPeriodSec | Trascorso questo periodo, gli offset verranno salvati nel database. <br>Il valore predefinito è 5 (sec) |
| processingJSThreads | Numero di thread dedicati che elaborano i messaggi con connettori JS personalizzati. <br> Il valore predefinito è 4 |
| processingThreads | Numero di thread dedicati che elaborano i messaggi con codice incorporato. <br>Il valore predefinito è 4 |
| retryPeriodSec | Ritardo tra nuovi tentativi in caso di errori di elaborazione. <br>Il valore predefinito è 30 (sec) |
| retryValiditySec | Ignora il messaggio se non viene elaborato correttamente dopo questo periodo (troppi tentativi). <br>Il valore predefinito è 300 (sec) |

### Avvio automatico del processo pipeline {#pipelined-process-autostart}

Il processo pipeline deve essere avviato automaticamente.

Per questo, imposta l’elemento &lt; pipeline > nel file di configurazione su autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Riavvio del processo pipeline {#pipelined-process-restart}

Per rendere effettive le modifiche è necessario riavviare il computer:

```
nlserver restart pipelined@instance
```

## Passaggio 4: convalida {#step-validation}

Per convalidare la configurazione della pipeline per il provisioning, effettua le seguenti operazioni:

* Assicurati che le [!DNL pipelined] processo in esecuzione.
* Controlla il file pipeline.log per i registri di connessione della pipeline.
* Verifica la connessione e se vengono ricevuti ping. I clienti in hosting possono utilizzare il monitoraggio dalla console client.
