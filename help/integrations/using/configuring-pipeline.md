---
title: Configurazione della pipeline
description: Scopri come configurare la pipeline
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 4f949d8db3aa3082acf1765bf66080b270cc6db4
workflow-type: tm+mt
source-wordcount: '909'
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

Prima di avviare la configurazione, verificare di disporre di:

* una versione recente di  Adobe Campaign (20.2.1 e versioni successive),
*  versione Adobe Analytics Standard

Sarà inoltre necessario:

*  autenticazione progetto I/O Adobe
* un IMSOrgID valido, l’identificatore del cliente del Experience Cloud  con  aggiunto Adobe Analytics
* Accesso sviluppatore all&#39;organizzazione IMS
* attiva la configurazione in  Adobe Analytics

## File di autenticazione e configurazione {#authentication-configuration}

L&#39;autenticazione è necessaria perché la pipeline è ospitata nell&#39;Adobe Experience Cloud.
Utilizza un paio di chiavi pubbliche e private. Questa procedura ha la stessa funzione di utente/password ma è più sicura.
L&#39;autenticazione è supportata per il Marketing Cloud tramite  progetto I/O Adobe.

## Passaggio 1: Creazione/aggiornamento  progetto I/O Adobe {#creating-adobe-io-project}

Per i clienti ospitati, puoi creare un ticket di assistenza clienti per abilitare la tua organizzazione con  Token account tecnici I/O di Adobe per l&#39;integrazione Triggers.

Per i clienti interni, consultate la pagina [Configurazione  I/O Adobe per Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) . Durante l&#39;aggiunta di API alla credenziale I/O del Adobe  è necessario selezionare **[!UICONTROL Adobe Analytics]** .

## Passaggio 2: Configurazione dell&#39;opzione pipeline NmsPipeline_Config {#configuring-nmspipeline}

Una volta impostata l&#39;autenticazione, la pipeline recupererà gli eventi. Vengono elaborati solo gli attivatori configurati in  Adobe Campaign. Il trigger deve essere stato generato da  Adobe Analytics e inviato alla pipeline che elaborerà solo gli attivatori configurati in  Adobe Campaign.
L&#39;opzione può essere configurata anche con un carattere jolly per intercettare tutti i trigger, indipendentemente dal nome.

1. In  Adobe Campaign, accedere al menu delle opzioni in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in **[!UICONTROL Explorer]**.

1. Selezionate l’ **[!UICONTROL NmsPipeline_Config]** opzione.

1. Nel **[!UICONTROL Value (long text)]** campo potete incollare il seguente codice JSON, che specifica due attivatori. È necessario assicurarsi di rimuovere i commenti.

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

Il parametro **Consumer** identifica l’istanza come uno di questi consumatori. L&#39;identità dell&#39;istanza chiamerà la pipeline. Potete compilarlo con il nome dell&#39;istanza che si trova nella pagina Monitoraggio della console client.

Il servizio pipeline tiene traccia dei messaggi recuperati da ogni consumatore. L’utilizzo di consumatori diversi per diverse istanze consente di verificare che ogni messaggio venga inviato a ogni istanza.

### Consigli sulle opzioni pipeline {#pipeline-option-recommendation}

Per configurare l&#39;opzione pipeline, attenersi alle seguenti raccomandazioni:

* Aggiungi o modifica attivatori in **[!UICONTROL Triggers]**, non devi modificare il resto.
* Assicurati che il JSON sia valido. Potete utilizzare una funzione di convalida JSON, ad esempio fare riferimento a questo [sito Web](http://jsonlint.com/) .
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
| dumpStatePeriodSec | Il periodo tra due discariche del processo di stato interno nello stato ```var/INSTANCE/pipelined.json.``` <br> interno è accessibile anche su richiesta: ```http://INSTANCE:7781/pipelined/status``` |
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

* Verificare che il [!DNL pipelined] processo sia in esecuzione.
* Controllate i registri di connessione della pipeline nel file pipelining.log.
* Verificare la connessione e se i ping sono ricevuti. I clienti ospitati possono utilizzare il monitoraggio dalla console client.
