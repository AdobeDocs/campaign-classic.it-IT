---
product: campaign
title: Configurare la pipeline
description: Scopri come configurare la pipeline per l’integrazione Campaign - Triggers
feature: Triggers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---

# Configurare la pipeline {#configuring-pipeline}

I parametri di autenticazione come l’ID cliente, la chiave privata e l’endpoint di autenticazione sono configurati nei file di configurazione dell’istanza.

L’elenco dei trigger da elaborare è configurato in un’opzione in formato JSON.

I trigger vengono utilizzati per il targeting da un flusso di lavoro della campagna che invia e-mail. La campagna è impostata in modo che un cliente con entrambi gli eventi di attivazione riceva un’e-mail.

## Prerequisiti {#prerequisites}

Prima di avviare questa configurazione, verifica di disporre di:

* Un progetto Adobe Developer
* Un ID organizzazione valido. Per trovare l&#39;ID organizzazione, fare riferimento a [questa pagina](https://experienceleague.adobe.com/it/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* Accesso per sviluppatori all’organizzazione
* Una configurazione dei trigger valida in Adobe Analytics

È necessaria l’autenticazione perché la pipeline è ospitata in Adobe Experience Cloud. Utilizza un’autenticazione supportata per tramite un progetto Adobe Developer.

## Passaggio 1: creare/aggiornare il progetto Adobe Developer {#creating-adobe-io-project}

Abilita la tua organizzazione con i token di account Adobe Developer per l’integrazione Triggers.

Scopri come creare il tuo account tecnico Adobe in [questa pagina](../../integrations/using/oauth-technical-account.md). È necessario selezionare **[!UICONTROL Adobe Analytics]** durante l&#39;aggiunta dell&#39;API alle credenziali di Adobe Developer.

## Passaggio 2: configurare l&#39;opzione pipeline {#configuring-nmspipeline}

Una volta impostata l&#39;autenticazione, la pipeline recupererà gli eventi. Elabora solo i trigger configurati in Adobe Campaign. Il trigger deve essere stato generato da Adobe Analytics e inviato alla pipeline, che elaborerà solo i trigger configurati in Adobe Campaign.

L’opzione può anche essere configurata con un carattere jolly per acquisire tutti i trigger, indipendentemente dal nome.

1. In Adobe Campaign, accedere al menu delle opzioni in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in **[!UICONTROL Explorer]**.

1. Seleziona l’opzione **[!UICONTROL NmsPipeline_Config]**.

1. **[!UICONTROL Value (long text)]** Nel campo è possibile incollare il seguente codice JSON, che specifica due attivatori. Assicurati di rimuovere commenti.

   ```json
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

   ```json
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

### Impostare il parametro Consumer {#consumer-parameter}

La pipeline funziona like un modello di fornitore e consumatore. I messaggi vengono consumati solo per un singolo consumatore: ogni consumatore ottiene la propria copia dei messaggi.

Il parametro **Consumer** identifica l&#39;istanza come uno di questi consumer. L’identità dell’istanza chiamerà la pipeline. È possibile compilarlo con il nome dell’istanza che si trova nella pagina Monitoraggio della console client.

Il servizio pipeline tiene traccia dei messaggi recuperati da ciascun consumatore. L’utilizzo di consumer diversi per istanze diverse consente di assicurarsi che ogni messaggio venga inviato a ogni istanza.

### Raccomandazioni sulle opzioni della pipeline {#pipeline-option-recommendation}

Per configurare l’opzione Pipeline, segui queste raccomandazioni:

* Aggiungi o modifica i trigger in **[!UICONTROL Triggers]**.
* Verifica che il JSON sia valido.
* Il parametro **Name** corrisponde all&#39;ID del trigger. Un carattere jolly &quot;*&quot; acquisirà tutti i trigger.
* Il parametro **Consumer** corrisponde al nome dell&#39;istanza o dell&#39;applicazione chiamante.
* il processo `pipelined` supporta anche l&#39;argomento &quot;alias&quot;.
* È sempre necessario riavviare `pipelined` processo dopo aver apportato modifiche.

## (facoltativo) Passaggio 3: configurazione aggiuntiva {#step-optional}

Puoi modificare alcuni parametri interni in base ai requisiti di carico, ma assicurati di testarli prima di applicarli all’ambiente di produzione.

L’elenco dei parametri facoltativi è:

| Opzione | Descrizione |
|:-:|:-:|
| appName(Legacy) | AppID dell’applicazione OAuth registrata nell’applicazione Oath legacy in cui è stata caricata la chiave pubblica. Per ulteriori informazioni, consulta questa [pagina](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint(Legacy) | URL per ottenere i token del gateway. Predefinito: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | Chiave privata, parte pubblica caricata nell&#39;applicazione Oath legacy, AES crittografata con l&#39;opzione XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Disabilita l’autenticazione: la connessione senza token gateway verrà accettata solo da alcuni endpoint della pipeline di sviluppo. |
| findPipelineEndpoint | URL per trovare l’endpoint dei servizi di pipeline da utilizzare per questo tenant. Predefinito: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Periodo tra due immagini del processo dello stato interno in ```var/INSTANCE/pipelined.json.``` <br> Lo stato interno è accessibile anche on-demand qui: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Disattiva il rilevamento di PipelineServicesEndpoint per forzarlo |
| monitorServerPort | Il processo pipeline ascolterà su questa porta per fornire il processo dello stato interno qui: ```http://INSTANCE:PORT/pipelined/status```. <br>Il valore predefinito è 7781 |
| pointerFlushMessageCount | Quando questo numero di messaggi viene elaborato, gli offset vengono salvati nel database. Il valore predefinito di <br> è 1000 |
| pointerFlushPeriodSec | Trascorso questo periodo, gli offset verranno salvati nel database. <br>Il valore predefinito è 5 (sec) |
| processingJSThreads | Numero di thread dedicati che elaborano i messaggi con connettori JS personalizzati. Il valore predefinito di <br> è 4 |
| processingThreads | Numero di thread dedicati che elaborano i messaggi con codice incorporato. <br>Il valore predefinito è 4 |
| retryPeriodSec | Ritardo tra nuovi tentativi in caso di errori di elaborazione. <br>Il valore predefinito è 30 (sec) |
| retryValiditySec | Ignora il messaggio se non viene elaborato correttamente dopo questo periodo (troppi tentativi). <br>Il valore predefinito è 300 (secondi) |

### Avvio automatico del processo pipeline {#pipelined-process-autostart}

Il processo `pipelined` deve essere avviato automaticamente.

Per questo, imposta l&#39;elemento `<`pipeline`>` nel file di configurazione su autostart=&quot;true&quot;:

```sql
 <pipelined autoStart="true" ... "/>
```

### Riavvio del processo pipeline {#pipelined-process-restart}

Per rendere effettive le modifiche è necessario riavviare il computer:

```sql
nlserver restart pipelined@instance
```

## Passaggio 4: convalida {#step-validation}

Per convalidare la configurazione della pipeline per il provisioning, seguire i passaggi seguenti:

* Assicurati che il `pipelined` processo sia in esecuzione.
* Verificare la presenza di registri di `pipelined.log` connessione della pipeline.
* Verificare la connessione e se vengono ricevuti i ping. I clienti ospitati possono utilizzare il monitoraggio dalla console client.
