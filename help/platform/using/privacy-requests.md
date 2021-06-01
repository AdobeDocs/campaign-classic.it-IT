---
product: campaign
title: Richieste di accesso a dati personali
description: Scopri come gestire le richieste di accesso a dati personali
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2415'
ht-degree: 100%

---

# Gestione delle richieste di accesso a dati personali {#privacy-requests}

Per una presentazione generale sulla gestione della privacy, consulta [questa sezione](../../platform/using/privacy-management.md).

Queste informazioni si applicano alle normative GDPR, CCPA, PDPA e LGPD. Per ulteriori informazioni su tali normative, consulta [questa sezione](../../platform/using/privacy-management.md#privacy-management-regulations).

La rinuncia alla vendita di informazioni personali, specifica del CCPA, è spiegata in [questa sezione](#sale-of-personal-information-ccpa).

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

## Informazioni sulle richieste di accesso a dati personali {#about-privacy-requests}

Per aiutarti a garantire l’idoneità alle normative sulla privacy, Adobe Campaign consente di gestire le richieste di accesso ed eliminazione. Il **diritto di accesso** e il **diritto all’oblio** (richiesta di eliminazione) sono illustrati in [questa sezione](../../platform/using/privacy-management.md#right-access-forgotten).

Vediamo come creare le richieste di accesso ed eliminazione e come Adobe Campaign le elabora.

### Principi {#principles}

Adobe Campaign offre ai titolari del trattamento dei dati due possibilità per eseguire le richieste di accesso e cancellazione dei dati personali:

* Tramite l’**interfaccia di Adobe Campaign**: per ogni richiesta di accesso a dati personali, il titolare del trattamento dei dati crea una nuova richiesta di accesso ai dati personali in Adobe Campaign. Vedi [questa sezione](#create-privacy-request-ui).
* Tramite **API**: Adobe Campaign fornisce un’API che consente il processo automatico delle richieste di accesso a dati personali utilizzando SOAP. Vedi [questa sezione](#automatic-privacy-request-api).

>[!NOTE]
>
>Per ulteriori informazioni sui dati personali e sulle diverse entità che gestiscono i dati (titolare del trattamento, responsabile del trattamento e interessato), consulta [Dati personali e utenti tipo](../../platform/using/privacy-and-recommendations.md#personal-data).

### Prerequisiti {#prerequesites}

 Adobe Campaign offre ai titolari del trattamento strumenti per creare ed elaborare richieste di accesso a dati personali per i dati memorizzati in Adobe Campaign. La gestione del rapporto con l’interessato (tramite e-mail, assistenza clienti o un portale web) rimane tuttavia responsabilità del titolare del trattamento.

In qualità di titolare del trattamento, avrai pertanto la responsabilità di confermare l’identità dell’interessato che presenta la richiesta e confermare che i dati restituiti al richiedente riguardano l’interessato.

### Installazione del pacchetto Privacy {#install-privacy-package}

Per utilizzare questa funzione, è necessario installare il pacchetto **[!UICONTROL Privacy Data Protection Regulation]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**. Per ulteriori informazioni su come installare i pacchetti, consulta la [documentazione dettagliata](../../installation/using/installing-campaign-standard-packages.md).

Due nuove cartelle, specifiche di Privacy, vengono create in **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: qui puoi creare le richieste di Privacy e tracciarne l’evoluzione.
* **[!UICONTROL Namespaces]**: questo campo verrà utilizzato per identificare l’interessato nel database di Adobe Campaign.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, tre flussi di lavoro tecnici vengono eseguiti ogni giorno per elaborare le richieste relative ai dati personali.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: questo flusso di lavoro genera i dati del destinatario memorizzati in Adobe Campaign e li rende disponibili per il download nella schermata della richiesta di accesso a dati personali.
* **[!UICONTROL Delete privacy requests data]**: questo flusso di lavoro elimina i dati del destinatario memorizzati in Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: questo flusso di lavoro cancella i file di richiesta di accesso che sono stati creati da più di 90 giorni.

In **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]** è stata aggiunta l’autorizzazione denominata **[!UICONTROL Privacy Data Right]**. Questa autorizzazione denominata è necessaria per i titolari del trattamento dei dati affinché possano utilizzare gli strumenti per la privacy. Consente loro di creare nuove richieste, tracciare la loro evoluzione, utilizzare l’API, ecc.

![](assets/privacy-right.png)

### Spazi dei nomi {#namesspaces}

Prima di creare le richieste di accesso a dati personali, è necessario definire lo spazio dei nomi che verrà utilizzato. Questa chiave verrà utilizzata per identificare l’interessato nel database di Adobe Campaign.

Sono disponibili tre namespace predefiniti: e-mail, telefono e cellulare. Se hai bisogno di un namespace diverso (ad esempio un campo destinatario personalizzato), puoi crearne uno nuovo da **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

## Creazione di una richiesta di accesso a dati personali {#create-privacy-request-ui}

L’**interfaccia di Adobe Campaign** consente di creare le richieste di accesso ai dati personali e di tracciarne l’evoluzione. Per creare una nuova richiesta di accesso a dati personali, segui queste istruzioni:

1. Accedi alla cartella della richiesta di accesso a dati personali in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]**.

   ![](assets/privacy-requests-folder.png)

1. Questa schermata ti consente di visualizzare tutte le richieste di accesso a deati personali correnti, il loro stato e i registri. Fai clic su **[!UICONTROL New]** per creare una richiesta di accesso a dati personali.

   ![](assets/privacy-request-new.png)

1. Seleziona **[!UICONTROL Regulation]** (RGPD, CCPA, PDPA o LGPD), **[!UICONTROL Request type]** (accesso o eliminazione), seleziona un **[!UICONTROL Namespace]** e immetti il **[!UICONTROL Reconciliation value]**. Se utilizzi l’e-mail come namespace, digita l’e-mail dell’interessato.

   ![](assets/privacy-request-properties.png)

I flussi di lavoro tecnici per la privacy vengono eseguiti una volta al giorno ed elaborano ogni nuova richiesta:

* Richiesta di eliminazione: i dati del destinatario memorizzati in Adobe Campaign vengono cancellati.
* Richiesta di accesso: i dati del destinatario memorizzati in Adobe Campaign vengono generati e resi disponibili come file XML nella parte sinistra della schermata di richiesta.

![](assets/privacy-request-download.png)

### Elenco delle tabelle {#list-of-tables}

Durante l’esecuzione di una richiesta di eliminazione o di accesso ai dati personali, Adobe Campaign cerca tutti i dati dell’interessato in base al **[!UICONTROL Reconciliation value]** in tutte le tabelle che presentano un collegamento alla tabella dei destinatari (di tipo proprio).

Di seguito è riportato l’elenco delle tabelle pronte all’uso prese in considerazione per l’esecuzione delle richieste di accesso a dati personali:

* Destinatari (recipient)
* Registro delle consegne ai destinatari (broadLogRcp)
* Registro di tracciamento dei destinatari (trackingLogRcp)
* Registro di consegna degli eventi archiviati (broadLogEventHisto)
* Contenuto dell’elenco destinatari (rcpGrpRel)
* Proposta di offerta del visitatore (propositionVisitor)
* Visitatori (visitor)
* Storico abbonamenti (subHisto)
* Abbonamenti (subscription)
* Proposta di offerta del destinatario (propositionRcp)

Se hai creato tabelle personalizzate con un collegamento alla tabella dei profili (di tipo proprio), anche queste verranno considerate. Ad esempio, se disponi di una tabella di transazioni collegata alla tabella dei destinatari e una tabella di dettagli delle transazioni collegata alla tabella delle transazioni, verranno entrambe considerate.

>[!IMPORTANT]
>
>Se esegui richieste batch di accesso a dati personali utilizzando flussi di lavoro per l’eliminazione del profilo, tieni presente le seguenti osservazioni:
>* L’eliminazione del profilo tramite flussi di lavoro non elabora eventuali tabelle secondarie.
>* È necessario gestire l’eliminazione per tutte le tabelle secondarie.
>* Adobe consiglia di creare un flusso di lavoro ETL che aggiunga le righe da eliminare nella tabella di accesso ai dati personali e consenta al flusso di lavoro **[!UICONTROL Delete privacy requests data]** di eseguire l’eliminazione. Consigliamo di limitare l’eliminazione a 200 profili al giorno, per motivi di prestazioni.


### Stati delle richieste di accesso a dati personali {#privacy-request-statuses}

Di seguito sono riportati i diversi stati delle richieste di accesso a dati personali:

* **[!UICONTROL New]** / **[!UICONTROL Retry pending]**: in corso, il flusso di lavoro non ha ancora elaborato la richiesta.
* **[!UICONTROL Processing]** / **[!UICONTROL Retry in progress]**: il flusso di lavoro sta elaborando la richiesta.
* **[!UICONTROL Delete pending]**: il flusso di lavoro ha identificato tutti i dati del destinatario da eliminare.
* **[!UICONTROL Delete in progress]**: il flusso di lavoro sta elaborando l’eliminazione.
* **[!UICONTROL Delete Confirmation Pending]** (richiesta di eliminazione in modalità di processo in due fasi): il flusso di lavoro ha elaborato la richiesta di accesso. Per eseguire l’eliminazione, è richiesta una conferma manuale. Il pulsante è disponibile per 15 giorni.
* **[!UICONTROL Complete]**: l’elaborazione della richiesta è andata a buon fine.
* **[!UICONTROL Error]**: il flusso di lavoro ha rilevato un errore. Il motivo viene visualizzato nell’elenco delle richieste di accesso a dati personali nella colonna **[!UICONTROL Request status]**. Ad esempio, **[!UICONTROL Error data not found]** significa che nel database non è stato trovato nessun dato del destinatario corrispondente al **[!UICONTROL Reconciliation value]** dell’interessato.

### Processo in due fasi {#two-step-process}

Il **processo in due fasi** è attivato per impostazione predefinita. Quando crei una nuova richiesta di eliminazione utilizzando questa modalità, Adobe Campaign esegue sempre prima una richiesta di accesso. Questo ti consente di controllare i dati prima di confermarne l’eliminazione.

Puoi modificare questa modalità dalla schermata di modifica della richiesta di accesso a dati personali. Fai clic su **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

Attivando la modalità in 2 passaggi, lo stato di una nuova richiesta di eliminazione diventa **[!UICONTROL Confirm Delete Pending]**. Scarica il file XML generato dalla schermata di richiesta di accesso a dati personali e controlla i dati. Per confermare la cancellazione dei dati, fai clic sul pulsante **[!UICONTROL Confirm delete data]**.

![](assets/privacy-request-delete-data.png)

### URL JSSP {#jspp-url}

Quando si elaborano le richieste di accesso, Adobe Campaign genera un JSSP che recupera i dati del destinatario dal database ed li esporta in un file XML memorizzato nel computer locale. L’URL JSSP è definito come segue:

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

dove @id è l’ID della richiesta di accesso a dati personali.

Questo URL viene memorizzato nel campo **[!UICONTROL "File location" (@urlFile)]** dello schema **[!UICONTROL Privacy Requests (gdprRequest)]**.

Le informazioni sono disponibili nel database per 90 giorni. Una volta pulita la richiesta dal flusso di lavoro tecnico, le informazioni vengono rimosse dal database e l’URL diventa obsoleto. Controlla che l’URL sia ancora valido prima di scaricare i dati da una pagina web.

Ecco un esempio del file di dati dell’interessato:

![](assets/privacy-access-file.png)

I titolari del trattamento dei dati possono creare facilmente un’applicazione web che includa l’URL JSSP corrispondente per rendere disponibile il file di dati dell’interessato da una pagina web.

![](assets/privacy-gdpr-jssp.png)

Questo è uno snippet di codice che puoi utilizzare come esempio nell’attività **[!UICONTROL Page]** dell’applicazione web .

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

Poiché l’accesso al file di dati dell’interessato è limitato, l’accesso anonimo alla pagina web deve essere disattivato. Solo gli operatori che dispongono delle autorizzazioni denominate **[!UICONTROL Privacy Data Right]** possono accedere alla pagina e scaricare i dati.

## Processo automatico di richiesta di accesso a dati personali {#automatic-privacy-request-api}

Adobe Campaign fornisce un’**API** che consente di impostare un processo automatico di richiesta di accesso a dati personali.

Con l’API, il processo generale di accesso a dati personali è uguale al processo che si segue quando si [utilizza l’interfaccia](#create-privacy-request-ui). L’unica differenza consiste nella creazione della richiesta di accesso a dati personali. Invece di creare la richiesta in Adobe Campaign, viene inviato a Campaign un POST contenente le informazioni sulla richiesta. Per ogni richiesta, viene aggiunta una nuova voce nella schermata **[!UICONTROL Privacy Requests]**. I flussi di lavoro tecnici per la privacy elaborano quindi la richiesta, come per una richiesta aggiunta utilizzando l’interfaccia.

Se utilizzi l’API per inviare richieste di accesso a dati personali, ti consigliamo di lasciare attivato il **processo in 2 fasi** per le prime richieste di eliminazione, per poter verificare i dati restituiti. Al termine dei test, puoi disattivare il processo in due fasi in modo che il processo di richiesta di eliminazione possa essere eseguito automaticamente.

L’API JS **[!UICONTROL CreateRequestByName]** è definita come segue.

>[!NOTE]
>
>Se utilizzavi già l’API **gdprRequest**, puoi continuare a utilizzarla ma è consigliabile usare la nuova API **privacyRequest**.

>[!IMPORTANT]
>
>Per utilizzare l’API è necessario disporre dell’autorizzazione denominata **[!UICONTROL Privacy Data Right]**.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>Il campo “regulation” è disponibile solo se si utilizza Campaign Classic 20.2 (build 9178+).
>
>Se stai eseguendo la migrazione alla versione 20.2 e stavi già utilizzando l’API, devi aggiungere il campo “regulation” come mostrato in precedenza. Se utilizzi una build precedente, puoi continuare a utilizzare l’API senza il campo “regulation”.

### Richiamare l’API esternamente {#invoking-api-externally}

Ecco un esempio di come richiamare l’API esternamente (autenticazione tramite l’API e dettagli specifici sull’API Privacy). Per ulteriori informazioni sull&#39;API Privacy, consulta la [documentazione API](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/s-nms-privacyRequest.html). È inoltre possibile consultare la [documentazione sulle chiamate al servizio web](../../configuration/using/web-service-calls.md).

Innanzitutto, devi eseguire l’autenticazione tramite l’API:

1. Scarica il file WSDL **xtk:session** tramite questo URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Utilizza il metodo “Logon” e passa un nome utente e una password come parametri nella richiesta. Riceverai una risposta contenente un token di sessione. Ecco un esempio che utilizza SoapUI.

   ![](assets/privacy-api.png)

1. Utilizza il Token di sessione restituito come autenticazione per tutte le chiamate API successive. Scade dopo 24 ore.

Quindi invoca l’API Privacy:

1. Scarica il file WSDL da questo URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Utilizza **[!UICONTROL CreateRequestByName]** per creare una richiesta di accesso a dati personali specifica.

   Di seguito è riportato un esempio che utilizza **[!UICONTROL CreateRequestByName]**. Osserva come viene utilizzato il token di sessione fornito in precedenza come autenticazione. La risposta è l’ID della richiesta creata.

   ![](assets/privacy-api-2.png)

   Per aiutarti a eseguire i passaggi precedenti, considera quanto segue:

   * È possibile utilizzare **queryDef** nello schema **nms:gdprRequest** per controllare lo stato della richiesta di accesso.
   * È possibile utilizzare **queryDef** nello schema **nms:gdprRequestData** per ottenere il risultato della richiesta di accesso.
   * Per scaricare il file XML da **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, è necessario aver effettuato l’accesso e accedervi da un IP inserito nell’elenco degli indirizzi consentiti. A questo scopo, crea un’applicazione web che ti consenta di accedere al file generato da JSSP.

### Richiamare l’API da un JS {#invoking-api-from-js}

Ecco un esempio di come richiamare l’API da un JS all’interno di Campaign Classic.

>[!NOTE]
>
>Il campo “regulation” è disponibile solo se si utilizza Campaign Classic 20.2 (build 9178+).
>
>Se stai eseguendo la migrazione alla versione 20.2 e stavi già utilizzando l’API, devi aggiungere il campo “regulation”. Se utilizzi una build precedente, puoi continuare a utilizzare l’API senza il campo “regulation”.

* Se utilizzi **una build precedente (con pacchetto GDPR)**, puoi continuare a utilizzare l’API senza il campo “regulation” come mostrato di seguito:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Se stai **eseguendo la migrazione a 20.2** e stavi già utilizzando l’API, devi aggiungere il campo “regulation” come mostrato di seguito:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Se utilizzi **Campaign Classic 20.2 (build 9178+) o versione successiva**, il campo “regulation” è facoltativo, come illustrato di seguito:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

## Rinuncia alla vendita di informazioni personali (CCPA) {#sale-of-personal-information-ccpa}

Il **California Consumer Privacy Act** (CCPA) fornisce ai residenti della California nuovi diritti in merito alle loro informazioni personali e impone responsabilità in materia di protezione dei dati a determinate entità che conducono attività commerciali in California.

La configurazione e l’utilizzo delle richieste di accesso ed eliminazione sono comuni sia al GDPR che al CCPA. Questa sezione presenta la rinuncia alla vendita di dati personali, specifica del CCPA.

Oltre a utilizzare gli strumenti di [gestione del consenso](../../platform/using/privacy-management.md#consent-management) forniti da Adobe Campaign, puoi verificare se un consumatore ha negato il consenso alla vendita dei suoi dati personali.

Un consumatore decide, attraverso il tuo sistema, di non dare il consenso per la vendita dei propri dati personali a terzi. In Adobe Campaign, potrai archiviare e tenere traccia di questo tipo di informazioni.

Affinché ciò funzioni, devi estendere la tabella dei profili e aggiungere un campo **[!UICONTROL Opt-Out for CCPA]**.

>[!IMPORTANT]
>
>In qualità di titolare del trattamento è tua responsabilità ricevere la richiesta dell’interessato e tenere traccia delle date della richiesta in conformità con il CCPA. In qualità di fornitore di tecnologia, ci limitiamo a offrire un modo per esprimere la rinuncia. Per ulteriori informazioni sul tuo ruolo in quanto titolare del trattamento, consulta [Dati personali e utenti tipo](../../platform/using/privacy-and-recommendations.md#personal-data).

### Prerequisito {#ccpa-prerequisite}

Per sfruttare queste informazioni, è necessario creare tale campo in Adobe Campaign Standard. A questo scopo, aggiungi un campo booleano alla tabella **[!UICONTROL Recipient]**. Quando viene creato un nuovo campo, questo viene automaticamente supportato dall’API di Campaign.

Devi eseguire questa operazione anche se utilizzi una tabella dei destinatari personalizzata.

Per informazioni più dettagliate su come creare un nuovo campo, consulta la [documentazione sull’edizione dello schema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>La modifica degli schemi è un’operazione delicata e deve essere eseguita solo da utenti esperti.

1. Passa a **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, seleziona **[!UICONTROL Recipients]** come **[!UICONTROL Document type]** e fai clic su **[!UICONTROL Next]**. Per ulteriori informazioni sull’aggiunta di campi a una tabella, consulta [questa sezione](../../configuration/using/new-field-wizard.md).

   ![](assets/privacy-ccpa-1.png)

1. Per **[!UICONTROL Field type]**, seleziona **[!UICONTROL SQL field]**. Per l’etichetta, utilizza **[!UICONTROL Opt-Out for CCPA]**. Seleziona il tipo **[!UICONTROL 8-bit integer (boolean)]** e definisci il seguente **[!UICONTROL Relative path]** univoco: @OPTOUTCCPA. Fai clic su **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   Questo estenderà o creerà lo schema **[!UICONTROL Recipient (cus)]**. Fai clic su di esso per verificare che il campo sia stato aggiunto correttamente.

   ![](assets/privacy-ccpa-3.png)

1. Fai clic sul nodo **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** dell’Explorer. In **[!UICONTROL Recipient (nms)]**, in “General Package” (Pacchetto generale), aggiungi un elemento `<input>` e per il valore xpath utilizz, il percorso relativo definito nel passaggio 2. Per ulteriori informazioni sulla pubblicazione di una risorsa, consulta [questa sezione](../../configuration/using/identifying-a-form.md).

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Disconnettiti e riconnettiti. Segui i passaggi descritti nella sezione successiva per verificare che il campo sia disponibile nei dettagli di un destinatario.

### Utilizzo {#usage}

Compilare il valore del campo e seguire le linee guida e le regole del CCPA relative alla vendita dei dati è responsabilità del titolare del trattamento.

Sono disponibili diversi metodi per compilare i valori:

* Mediante l’interfaccia di Campaign, modificando i dettagli del destinatario
* Mediante l’API
* Mediante un flusso di lavoro di importazione dati

Accertati di non vendere mai a terzi le informazioni personali dei profili che hanno espresso la rinuncia.

1. Per modificare lo stato di rinuncia, passa a **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** e seleziona un destinatario. Nella scheda **[!UICONTROL General]** viene visualizzato il campo configurato nella sezione precedente.

   ![](assets/privacy-ccpa-5.png)

1. Configura l’elenco dei destinatari affinché venga visualizzata la colonna della rinuncia. Per informazioni su come configurare gli elenchi, consulta la [documentazione dettagliata](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

   ![](assets/privacy-ccpa-6.png)

1. Fai clic sulla colonna per ordinare i destinatari in base alle informazioni di rinuncia. Puoi anche creare un filtro per visualizzare solo i destinatari che hanno rinunciato. Per ulteriori informazioni sulla creazione di filtri, consulta [questa sezione](../../platform/using/creating-filters.md).

   ![](assets/privacy-ccpa-7.png)
