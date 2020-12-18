---
solution: Campaign Classic
product: campaign
title: Richieste di accesso a dati personali
description: Scopri come gestire le richieste di privacy
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2444'
ht-degree: 21%

---


# Gestione delle richieste di privacy {#privacy-requests}

Per una presentazione generale sulla gestione della privacy, consulta [questa sezione](../../platform/using/privacy-management.md).

Queste informazioni si applicano alle normative GDPR, CCPA, PDPA e LGPD. Per ulteriori informazioni su tali normative, consulta [questa sezione](../../platform/using/privacy-management.md#privacy-management-regulations).

La rinuncia alla vendita di informazioni personali, specifica del CCPA, è spiegata in [questa sezione](#sale-of-personal-information-ccpa).

>[!IMPORTANT]
>
>Le procedure di installazione descritte in questo documento sono applicabili a partire dal Campaign Classic 18.4 (build 8931+). Se si utilizza una versione precedente, fare riferimento a questa [nota tecnica](https://helpx.adobe.com/it/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).

## Informazioni sulle richieste di privacy {#about-privacy-requests}

Per aiutarti a garantire l’idoneità alle normative sulla privacy, Adobe Campaign consente di gestire le richieste di accesso ed eliminazione. Il **diritto di accesso** e il **diritto all’oblio** (richiesta di eliminazione) sono illustrati in [questa sezione](../../platform/using/privacy-management.md#right-access-forgotten).

Vediamo come creare le richieste di accesso ed eliminazione, nonché come  Adobe Campaign le elabora.

### Principi {#principles}

 Adobe Campaign offre ai Data Controller due possibilità per eseguire le richieste di accesso ed eliminazione alla privacy:

* Tramite l&#39;interfaccia **Adobe Campaign**: per ogni richiesta di privacy, il Data Controller crea una nuova richiesta di privacy in  Adobe Campaign. Vedi [questa sezione](#create-privacy-request-ui).
* Tramite **API**:  Adobe Campaign fornisce un&#39;API che consente il processo automatico delle richieste di privacy utilizzando SOAP. Vedi [questa sezione](#automatic-privacy-request-api).

>[!NOTE]
>
>Per ulteriori informazioni sui dati personali e sulle diverse entità che gestiscono i dati (titolare del trattamento, responsabile del trattamento e interessato), consulta [Dati personali e utenti tipo](../../platform/using/privacy-and-recommendations.md#personal-data).

### Prerequisiti {#prerequesites}

 Adobe Campaign offre ai titolari del trattamento strumenti per creare ed elaborare richieste di accesso a dati personali per i dati memorizzati in Adobe Campaign. La gestione del rapporto con l’interessato (tramite e-mail, assistenza clienti o un portale web) rimane tuttavia responsabilità del titolare del trattamento.

In qualità di titolare del trattamento, avrai pertanto la responsabilità di confermare l’identità dell’interessato che presenta la richiesta e confermare che i dati restituiti al richiedente riguardano l’interessato.

### Installazione del pacchetto Privacy {#install-privacy-package}

Per utilizzare questa funzione, è necessario installare il pacchetto **[!UICONTROL Privacy Data Protection Regulation]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**. Per ulteriori informazioni su come installare i pacchetti, consultare la [documentazione dettagliata](../../installation/using/installing-campaign-standard-packages.md).

In **[!UICONTROL Administration]** > **[!UICONTROL Platform]** vengono create due nuove cartelle, specifiche di Privacy:

* **[!UICONTROL Privacy Requests]**: qui potrai creare le tue richieste sulla privacy e seguirne l&#39;evoluzione.
* **[!UICONTROL Namespaces]**: in questa area verrà definito il campo che verrà utilizzato per identificare l&#39;oggetto dati nel database Adobe Campaign .

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, ogni giorno vengono eseguiti tre flussi di lavoro tecnici per l&#39;elaborazione delle richieste di privacy.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: questo flusso di lavoro genera i dati del destinatario memorizzati in  Adobe Campaign e li rende disponibili per il download nella schermata della richiesta di privacy.
* **[!UICONTROL Delete privacy requests data]**: questo flusso di lavoro elimina i dati del destinatario memorizzati in  Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: questo flusso di lavoro cancella i file di richiesta di accesso che hanno più di 90 giorni.

In **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]** è stato aggiunto il **[!UICONTROL Privacy Data Right]** denominato right. Questo diritto denominato è richiesto ai Controllori dei dati per poter utilizzare gli strumenti per la privacy. Questo consente loro di creare nuove richieste, tenere traccia della loro evoluzione, utilizzare l&#39;API, ecc.

![](assets/privacy-right.png)

### Spazi dei nomi {#namesspaces}

Prima di creare le richieste di accesso a dati personali, è necessario definire lo spazio dei nomi che verrà utilizzato. Questa è la chiave che verrà utilizzata per identificare l&#39;oggetto dati nel database Adobe Campaign .

Sono disponibili tre spazi di nomi out-of-the-box: email, telefono e cellulare. Se è necessario un altro spazio nomi (ad esempio un campo personalizzato del destinatario), è possibile crearne uno nuovo da **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

## Creazione di una richiesta di accesso a dati personali {#create-privacy-request-ui}

L&#39; **interfaccia Adobe Campaign** consente di creare le richieste sulla privacy e di seguirne l&#39;evoluzione. Per creare una nuova richiesta di privacy, segui le istruzioni seguenti:

1. Accedete alla cartella della richiesta relativa alla privacy in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]**.

   ![](assets/privacy-requests-folder.png)

1. Questa schermata consente di visualizzare tutte le richieste di privacy correnti, il relativo stato e i registri. Fate clic su **[!UICONTROL New]** per creare una richiesta per la privacy.

   ![](assets/privacy-request-new.png)

1. Selezionare **[!UICONTROL Regulation]** (GDPR, CCPA, PDPA o LGPD), **[!UICONTROL Request type]** (Access or Delete), selezionare un **[!UICONTROL Namespace]** e inserire il **[!UICONTROL Reconciliation value]**. Se si utilizza email come namespace, digitare nell&#39;e-mail dell&#39;oggetto dati.

   ![](assets/privacy-request-properties.png)

I flussi di lavoro tecnici sulla privacy vengono eseguiti una volta al giorno ed elaborano ogni nuova richiesta:

* Elimina richiesta: i dati del destinatario memorizzati in  Adobe Campaign vengono cancellati.
* Richieste di accesso: i dati del destinatario memorizzati in  Adobe Campaign vengono generati e resi disponibili come file XML nella parte sinistra della schermata della richiesta.

![](assets/privacy-request-download.png)

### Elenco di tabelle {#list-of-tables}

Durante l&#39;esecuzione di una richiesta di eliminazione o di accesso alla privacy,  Adobe Campaign cerca tutti i dati dell&#39;oggetto dati in base alla **[!UICONTROL Reconciliation value]** in tutte le tabelle che hanno un collegamento alla tabella del destinatario (tipo proprio).

Di seguito è riportato l&#39;elenco delle tabelle pronte all&#39;uso che vengono prese in considerazione per l&#39;esecuzione delle richieste di privacy:

* Destinatari (destinatario)
* Registro delle consegne del destinatario (wideLogRcp)
* Registro di tracciamento destinatari (trackingLogRcp)
* Registro di consegna eventi archiviato (wideLogEventHisto)
* Contenuto elenco destinatari (rcpGrpRel)
* Proposta di offerta del visitatore (propositionVisitor)
* Visitatori (visitor)
* Cronologia iscrizioni (subHisto)
* Iscrizioni (iscrizione)
* Proposta di offerta del destinatario (propositionRcp)

Se sono state create tabelle personalizzate con un collegamento alla tabella dei destinatari (tipo proprio), verranno prese in considerazione. Ad esempio, se hai una tabella di transazione collegata alla tabella del destinatario e una tabella dei dettagli della transazione collegata alla tabella delle transazioni, entrambi vengono presi in considerazione.

>[!IMPORTANT]
>
>Se esegui richieste batch di privacy utilizzando i flussi di lavoro di eliminazione del profilo, prendi in considerazione le seguenti osservazioni:
>* L&#39;eliminazione del profilo tramite flussi di lavoro non elabora le tabelle figlio.
>* È necessario gestire l&#39;eliminazione per tutte le tabelle figlio.
>*  Adobe consiglia di creare un flusso di lavoro ETL che aggiunga le righe da eliminare nella tabella Accesso alla privacy e consenta al flusso di lavoro **[!UICONTROL Delete privacy requests data]** di eseguire l&#39;eliminazione. Suggeriamo di limitare a 200 profili al giorno da eliminare per motivi di prestazioni.


### Stati delle richieste di accesso a dati personali {#privacy-request-statuses}

Di seguito sono riportati i diversi stati delle richieste di accesso a dati personali:

* **[!UICONTROL New]** / **[!UICONTROL Retry pending]**: in corso, il flusso di lavoro non ha ancora elaborato la richiesta.
* **[!UICONTROL Processing]** / **[!UICONTROL Retry in progress]**: il flusso di lavoro sta elaborando la richiesta.
* **[!UICONTROL Delete pending]**: il flusso di lavoro ha identificato tutti i dati del destinatario da eliminare.
* **[!UICONTROL Delete in progress]**: il flusso di lavoro sta elaborando l’eliminazione.
* **[!UICONTROL Delete Confirmation Pending]** (Elimina richiesta in modalità di processo in due fasi): il flusso di lavoro ha elaborato la richiesta di accesso. È richiesta la conferma manuale per eseguire l&#39;eliminazione. Il pulsante è disponibile per 15 giorni.
* **[!UICONTROL Complete]**: l’elaborazione della richiesta è andata a buon fine.
* **[!UICONTROL Error]**: il flusso di lavoro ha rilevato un errore. Il motivo viene visualizzato nell&#39;elenco delle richieste di privacy nella colonna **[!UICONTROL Request status]**. Ad esempio, **[!UICONTROL Error data not found]** significa che nel database non è stato trovato nessun dato del destinatario corrispondente al **[!UICONTROL Reconciliation value]** dell’interessato.

### Processo in due fasi {#two-step-process}

Per impostazione predefinita, il processo **a 2 fasi** è attivato. Quando create una nuova richiesta di eliminazione in questa modalità,  Adobe Campaign esegue sempre prima una richiesta di accesso. Questo consente di controllare i dati prima di confermare l&#39;eliminazione.

Potete modificare questa modalità dalla schermata della versione per la richiesta della privacy. Fai clic su **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

Con la modalità in due fasi attivata, lo stato di una nuova richiesta di eliminazione cambia in **[!UICONTROL Confirm Delete Pending]**. Scaricate il file XML generato dalla schermata di richiesta della privacy e verificate i dati. Per confermare la cancellazione dei dati, fare clic sul pulsante **[!UICONTROL Confirm delete data]**.

![](assets/privacy-request-delete-data.png)

### URL JSSP {#jspp-url}

Durante l&#39;elaborazione delle richieste di Access,  Adobe Campaign genera un JSSP che recupera i dati del destinatario dal database ed li esporta in un file XML memorizzato nel computer locale. L&#39;URL JSSP è definito come segue:

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

dove @id è l’ID della richiesta di privacy.

Questo URL viene memorizzato nel campo **[!UICONTROL "File location" (@urlFile)]** dello schema **[!UICONTROL Privacy Requests (gdprRequest)]**.

Le informazioni sono disponibili nel database per 90 giorni. Una volta ripulita la richiesta dal flusso di lavoro tecnico, le informazioni vengono rimosse dal database e l’URL diventa obsoleto. Verificare che l&#39;URL sia ancora valido prima di scaricare i dati da una pagina Web.

Di seguito è riportato un esempio del file di dati dell&#39;oggetto dati:

![](assets/privacy-access-file.png)

I controller dei dati possono creare facilmente un&#39;applicazione Web con l&#39;URL JSSP corrispondente per rendere disponibile il file dei dati dell&#39;oggetto dati da una pagina Web.

![](assets/privacy-gdpr-jssp.png)

Di seguito è riportato un frammento di codice che puoi utilizzare come esempio nell&#39;attività dell&#39;applicazione Web **[!UICONTROL Page]**.

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

Poiché l&#39;accesso al file di dati dell&#39;oggetto dati è limitato, l&#39;accesso anonimo alla pagina Web deve essere disattivato. Solo l&#39;operatore con il nome **[!UICONTROL Privacy Data Right]** a destra può accedere alla pagina e scaricare i dati.

## Processo di richiesta privacy automatica {#automatic-privacy-request-api}

 Adobe Campaign fornisce un **API** che consente di impostare un processo automatico di richiesta della privacy.

Con l&#39;API, il processo di privacy generale è lo stesso di [utilizzando l&#39;interfaccia](#create-privacy-request-ui). L&#39;unica differenza è la creazione della richiesta per la privacy. Invece di creare la richiesta in  Adobe Campaign, un POST contenente le informazioni sulla richiesta viene inviato a Campaign. Per ogni richiesta, nella schermata **[!UICONTROL Privacy Requests]** viene aggiunta una nuova voce. I flussi di lavoro tecnici sulla Privacy elaborano quindi la richiesta, allo stesso modo di una richiesta aggiunta utilizzando l&#39;interfaccia.

Se utilizzate l&#39;API per inviare richieste di privacy, per verificare i dati restituiti è consigliabile lasciare attivata la procedura **2 fasi** per le prime richieste di eliminazione. Al termine dei test, potete disattivare il processo in due fasi in modo che il processo di richiesta Delete possa essere eseguito automaticamente.

L&#39;API JS **[!UICONTROL CreateRequestByName]** è definita come segue.

>[!NOTE]
>
>Se si utilizza l&#39;API **gdprRequest**, è comunque possibile utilizzarla, ma si consiglia di utilizzare la nuova API **privacyRequest**.

>[!IMPORTANT]
>
>Per utilizzare l&#39;API è necessario il diritto **[!UICONTROL Privacy Data Right]** denominato.

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
>Il campo &#39;Regulation&#39; è disponibile solo se si utilizza Campaign Classic 20.2 (build 9178+).
>
>Se state effettuando la migrazione alla versione 20.2 e se state già utilizzando l&#39;API, dovete aggiungere il campo &quot;Regulation&quot; come mostrato sopra. Se utilizzate una build precedente, potete continuare a utilizzare l&#39;API senza il campo &quot;Regulation&quot;.

### Chiamata esterna dell&#39;API {#invoking-api-externally}

Di seguito è riportato un esempio di come è possibile richiamare l&#39;API esternamente (autenticazione tramite l&#39;API e dettagli specifici sull&#39;API Privacy). Per ulteriori informazioni sull&#39;API Privacy, consultare la [documentazione API](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/s-nms-privacyRequest.html). È inoltre possibile consultare la [Documentazione sulle chiamate al servizio Web](../../configuration/using/web-service-calls.md).

Innanzitutto, è necessario eseguire l&#39;autenticazione tramite l&#39;API:

1. Scaricate il file WSDL **xtk:session** tramite questo URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Utilizzate il metodo &quot;Logon&quot; e passate un nome utente e una password come parametri nella richiesta. Riceverete una risposta contenente un token di sessione. Ecco un esempio che utilizza SoapUI.

   ![](assets/privacy-api.png)

1. Utilizzate il token di sessione restituito come autenticazione per tutte le chiamate API successive. Scade dopo 24 ore.

Quindi richiamate l&#39;API Privacy:

1. Scaricate il WSDL dall&#39;URL seguente: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Utilizzate **[!UICONTROL CreateRequestByName]** per creare una richiesta per la privacy specifica.

   Di seguito è riportato un esempio che utilizza il simbolo **[!UICONTROL CreateRequestByName]**. Tenete presente che usiamo il token di sessione fornito sopra come autenticazione. La risposta è l’ID della richiesta creata.

   ![](assets/privacy-api-2.png)

   Per facilitare l&#39;esecuzione dei passaggi descritti qui sopra, considera quanto segue:

   * È possibile utilizzare uno schema **queryDef** nello schema **nms:gdprRequest** per verificare lo stato della richiesta di Access.
   * È possibile utilizzare uno schema **queryDef** nello schema **nms:gdprRequestData** per ottenere il risultato della richiesta di Access.
   * Per poter scaricare il file XML da **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, è necessario aver effettuato l&#39;accesso e accedervi da un IP inserito nella lista bianca. A tal fine, create un&#39;applicazione Web che consenta di accedere al file generato dalla JSSP.

### Chiamata dell&#39;API da un JS {#invoking-api-from-js}

Di seguito è riportato un esempio di come richiamare l&#39;API da un JS all&#39;interno di un Campaign Classic.

>[!NOTE]
>
>Il campo &#39;Regulation&#39; è disponibile solo se si utilizza Campaign Classic 20.2 (build 9178+).
>
>Se state effettuando la migrazione alla versione 20.2 e se state già utilizzando l&#39;API, dovete aggiungere il campo &quot;Regulation&quot; (Regola). Se utilizzate una build precedente, potete continuare a utilizzare l&#39;API senza il campo &quot;Regulation&quot;.

* Se utilizzi **una build precedente (con il pacchetto GDPR)**, puoi continuare a utilizzare l&#39;API senza il campo &quot;Regulation&quot; come mostrato di seguito:

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

* Se state eseguendo la migrazione a 20.2 **e se state già utilizzando l&#39;API, dovete aggiungere il campo &quot;Regulation&quot; come illustrato di seguito:**

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

* Se si utilizza **Campaign Classic 20.2 (build 9178+) o superiore**, il campo &#39;Regulation&#39; è facoltativo, come illustrato di seguito:

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

Oltre agli [Strumenti di gestione del consenso](../../platform/using/privacy-management.md#consent-management) forniti da  Adobe Campaign, è possibile verificare se un consumatore ha rinunciato alla vendita di Dati Personali.

Un consumatore decide, attraverso il tuo sistema, di non dare il consenso per la vendita dei propri dati personali a terzi. In Adobe Campaign, potrai archiviare e tenere traccia di questo tipo di informazioni.

Affinché questo funzioni, è necessario estendere la tabella Profili e aggiungere un campo **[!UICONTROL Opt-Out for CCPA]**.

>[!IMPORTANT]
>
>In qualità di titolare del trattamento è tua responsabilità ricevere la richiesta dell’interessato e tenere traccia delle date della richiesta in conformità con il CCPA. In qualità di fornitore di tecnologia, ci limitiamo a offrire un modo per esprimere la rinuncia. Per ulteriori informazioni sul tuo ruolo in quanto titolare del trattamento, consulta [Dati personali e utenti tipo](../../platform/using/privacy-and-recommendations.md#personal-data).

### Prerequisito {#ccpa-prerequisite}

Per sfruttare queste informazioni, è necessario creare questo campo in Adobe Campaign Classic. A questo scopo, è possibile aggiungere un campo booleano alla tabella **[!UICONTROL Recipient]**. Quando viene creato un nuovo campo, questo viene automaticamente supportato dall’API di Campaign.

Se utilizzi una tabella di destinatari personalizzata, devi eseguire anche questa operazione.

Per informazioni più dettagliate su come creare un nuovo campo, fare riferimento alla [Documentazione sull&#39;edizione dello schema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>La modifica degli schemi è un’operazione sensibile che deve essere eseguita solo da utenti esperti.

1. Andate a **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, selezionate **[!UICONTROL Recipients]** come **[!UICONTROL Document type]** e fate clic su **[!UICONTROL Next]**. Per ulteriori informazioni sull&#39;aggiunta di campi a una tabella, vedere [questa sezione](../../configuration/using/new-field-wizard.md).

   ![](assets/privacy-ccpa-1.png)

1. Per **[!UICONTROL Field type]**, selezionare **[!UICONTROL SQL field]**. Per l&#39;etichetta, utilizzare **[!UICONTROL Opt-Out for CCPA]**. Selezionare il tipo **[!UICONTROL 8-bit integer (boolean)]** e definire il seguente **[!UICONTROL Relative path]** univoco: @OPTOUTCCPA. Fai clic su **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   In questo modo si estende o si crea lo schema **[!UICONTROL Recipient (cus)]**. Fare clic su di esso per verificare che il campo sia stato aggiunto correttamente.

   ![](assets/privacy-ccpa-3.png)

1. Fare clic sul nodo **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** dell&#39;elenco di esplorazione. In **[!UICONTROL Recipient (nms)]**, in &quot;General Package&quot;, aggiungere un elemento `<input>` e utilizzare, per il valore xpath, il percorso relativo definito al punto 2. Per ulteriori informazioni sull&#39;identificazione di un modulo, vedere [questa sezione](../../configuration/using/identifying-a-form.md).

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Disconnetti e ricollega. Segui i passaggi descritti nella sezione successiva per verificare che il campo sia disponibile nei dettagli di un destinatario.

### Utilizzo {#usage}

Compilare il valore del campo e seguire le linee guida e le regole del CCPA relative alla vendita dei dati è responsabilità del titolare del trattamento.

Sono disponibili diversi metodi per compilare i valori:

* Utilizzo dell&#39;interfaccia di Campaign modificando i dettagli del destinatario
* Utilizzo dell&#39;API
* Mediante un flusso di lavoro di importazione dati

Accertati di non vendere mai a terzi le informazioni personali dei profili che hanno espresso la rinuncia.

1. Per modificare lo stato di rifiuto, andare su **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** e selezionare un destinatario. Nella scheda **[!UICONTROL General]** viene visualizzato il campo configurato nella sezione precedente.

   ![](assets/privacy-ccpa-5.png)

1. Configurare l&#39;elenco destinatari per visualizzare la colonna a comparsa. Per informazioni su come configurare gli elenchi, fare riferimento alla [documentazione dettagliata](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

   ![](assets/privacy-ccpa-6.png)

1. Fai clic sulla colonna per ordinare i destinatari in base alle informazioni di rinuncia. Potete anche creare un filtro per visualizzare solo i destinatari che hanno rinunciato. Per ulteriori informazioni sulla creazione di filtri, vedere [questa sezione](../../platform/using/creating-filters.md).

   ![](assets/privacy-ccpa-7.png)
