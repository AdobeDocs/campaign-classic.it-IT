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
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---


# Configurazione della pipeline {#configuring-pipeline}

I parametri di autenticazione come l&#39;ID cliente, la chiave privata e l&#39;endpoint di autenticazione sono configurati nei file di configurazione dell&#39;istanza.
L&#39;elenco di attivatori da elaborare è configurato in un&#39;opzione. È in formato JSON.
Il trigger viene elaborato immediatamente utilizzando il codice JavaScript. Viene salvata in una tabella di database senza ulteriore elaborazione in tempo reale.
I trigger vengono utilizzati per il targeting tramite un flusso di lavoro della campagna che invia e-mail. La campagna è impostata in modo che un cliente con entrambi gli eventi di attivazione riceva un’e-mail.

## Prerequisiti {#prerequisites}

L&#39;utilizzo [!DNL Experience Cloud Triggers] in Campaign richiede:

*  Adobe Campaign 6.11 build 8705 o versione successiva.
* Adobe  Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select o Standard.

Le configurazioni preliminari sono:

* Creazione di un file di chiave privata e quindi creazione dell&#39;applicazione Auth registrata con quella chiave.
* Configurazione degli attivatori in Adobe  Analytics.

La configurazione Adobe  Analytics non rientra nell&#39;ambito di questo documento.

 Adobe Campaign richiede le seguenti informazioni da Adobe  Analytics:

* Nome dell&#39;applicazione Auth.
* IMSOrgId, l’identificatore del cliente Experience Cloud .
* I nomi degli attivatori configurati in  Analytics.
* Nome e formato dei campi di dati da riconciliare con il database Marketing.

Parte di questa configurazione è uno sviluppo personalizzato e richiede quanto segue:

* Conoscenza di lavoro dell&#39;analisi JSON, XML e Javascript in  Adobe Campaign.
* Conoscenza operativa delle API QueryDef e Writer.
* Nozioni di funzionamento di crittografia e autenticazione utilizzando chiavi private.

>[!NOTE]
>
>Poiché la modifica del codice JS richiede competenze tecniche, non provate a farlo senza una comprensione adeguata. <br>Gli attivatori vengono salvati in una tabella di database. Pertanto, i dati di attivazione possono essere utilizzati dagli operatori di marketing nei flussi di lavoro di targeting.

## File di autenticazione e configurazione {#authentication-configuration}

L&#39;autenticazione è necessaria in quanto Pipeline è ospitata in Adobe Experience Cloud.
Se il server Marketing è ospitato in sede, quando accede alla pipeline, deve autenticarsi per disporre di una connessione protetta.
Utilizza un paio di chiavi pubbliche e private. Questa procedura è la stessa funzione di utente/password, solo più sicura.

### IMSOrgId {#imsorgid}

IMSOrgId è l’identificatore del cliente in Adobe Experience Cloud.
Impostatelo nel file instance serverConf.xml, sotto l’attributo IMSOrgId.
Esempio:

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Generazione di chiavi {#key-generation}

La chiave è un paio di file. È in formato RSA e dura 4096 byte. Può essere generato con uno strumento open source come OpenSSL. Ogni volta che lo strumento viene eseguito, viene generata una nuova chiave in modo casuale.
Per comodità, i passaggi sono elencati di seguito:

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Esempio di file private_key.pem:

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Esempio di file public_key.pem:

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Le chiavi non devono essere generate da PuttyGen, OpenSSL è la scelta migliore.

### Creazione di client di autenticazione in Adobe Experience Cloud {#oauth-client-creation}

È necessario creare un&#39;applicazione di tipo JWT effettuando l&#39;accesso ad Adobe  Analytics nell&#39;account organizzazione corretto in **[!UICONTROL Admin]** > **[!UICONTROL User Management]** > **[!UICONTROL Legacy Oath application]**.

Effettuate le seguenti operazioni:

1. Selezionare il **[!UICONTROL Service Account (JWT Assertion)]**.
1. Inserire il **[!UICONTROL Application Name]**.
1. Registra il **[!UICONTROL Public key]**.
1. Selezionare l&#39;attivatore **[!UICONTROL Scopes]**.

   ![](assets/triggers_5.png)

1. Fate clic su **[!UICONTROL Create]** e controllate il **[!UICONTROL Application ID]** e **[!UICONTROL Application Secret]** create.

   ![](assets/triggers_6.png)

### Registrazione del nome dell&#39;applicazione in  Adobe Campaign Classic {#application-name-registration}

L&#39;ID applicazione del client Auth creato deve essere configurato in  Adobe Campaign. Potete farlo modificando il file di configurazione dell&#39;istanza nell&#39;elemento collegato, in particolare l&#39;attributo appName.

Esempio:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Cifratura chiave {#key-encription}

Per poter essere utilizzata da un pipeline, la chiave privata deve essere crittografata. La cifratura viene eseguita utilizzando la funzione cryptString Javascript e deve essere eseguita sulla stessa istanza della tubazione.

Un esempio di crittografia di chiave privata con JavaScript è disponibile in questa [pagina](../../integrations/using/pipeline-troubleshooting.md).

La chiave privata crittografata deve essere registrata  Adobe Campaign. È possibile farlo modificando il file di configurazione dell&#39;istanza nell&#39;elemento pipeline, in particolare l&#39;attributo authPrivateKey.

Esempio:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Avvio automatico processo tubato {#pipelined-auto-start}

Il processo tubato deve essere avviato automaticamente.
Per eseguire questa operazione, impostate l’elemento nel file di configurazione su autostart=&quot;true&quot;:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Riavvio processo tubato {#pipelined-restart}

Può anche essere avviata manualmente utilizzando la riga di comando:

```
nlserver start pipelined@instance
```

Per rendere effettive le modifiche è necessario riavviare il sistema:

```
nlserver restart pipelined@instance
```

In caso di errori, cercate gli errori nell’output standard (se avviato manualmente) o nel file di registro con le tubazioni. Per ulteriori informazioni sulla risoluzione dei problemi, consultare la sezione Risoluzione dei problemi del documento.

### Opzioni di configurazione pipeline {#pipelined-configuration-options}

| Opzione | Descrizione |
|:-:|:-:|
| appName | ID dell’applicazione OAuth (ID applicazione) registrata in Adobe  Analytics (dove è stata caricata la chiave pubblica): Admin (Amministratore) > User Management (Gestione utente) > Legacy Oath application (Applicazione giurata legacy). Fare riferimento a questa[sezione](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL per ottenere i &quot;token gateway&quot;. <br> Valore predefinito: https://api.omniture.com |
| authPrivateKey | Chiave privata (parte pubblica caricata in Adobe  Analytics (consultare questa sezione). AES crittografato con l&#39;opzione XtkSecretKey: xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | Disattiva autenticazione (la connessione senza token gateway è accettata solo da alcuni endpoint pipeline di sviluppo) |
| findPipelineEndpoint | URL per scoprire l&#39;endpoint di Pipeline Services da utilizzare per questo tenant. Valore predefinito: https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | Il periodo compreso tra 2 discariche dello stato interno del processo nello stato var/INSTANCE/pipelined.json è accessibile anche on-demand all&#39;indirizzo http://INSTANCE/pipelined/status (porta 7781). |
| forzatoPipelineEndpoint | Disabilitare l&#39;individuazione di PipelineServicesEndpoint e forzarla |
| monitorServerPort | Il processo di tubazione ascolta su questa porta per fornire lo stato interno del processo all&#39;indirizzo http://INSTANCE/pipelined/status (porta 7781). |
| puntatoreFlushMessageCount | Quando questo numero di messaggi viene elaborato, gli offset vengono salvati nel database. Il valore predefinito è 1000 |
| puntatoreFlushPeriodSec | Dopo questo periodo, gli offset verranno salvati nel database. Il valore predefinito è 5 (secondi) |
| processingJSThread | Numero di messaggi di elaborazione thread dedicati con connettori JS personalizzati. Il valore predefinito è 4 |
| processingThread | Numero di messaggi di elaborazione thread dedicati con codice incorporato. Il valore predefinito è 4 |
| tryPeriodSec | Ritardo tra i tentativi (in presenza di errori di elaborazione). Il valore predefinito è 30 (secondi) |
| tryValiditySec | Ignora il messaggio se non è stato elaborato correttamente dopo questo periodo (troppi tentativi). Il valore predefinito è 300 (secondi) |
