---
product: campaign
title: Processo automatico di richiesta di accesso a dati personali
description: Scopri come impostare un processo automatico di richiesta di accesso a dati personali
feature: Privacy, Privacy Tools
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 100%

---

# Processo automatico di richiesta di accesso a dati personali {#automatic-privacy-request-api}



Adobe Campaign fornisce un’**API** che consente di impostare un processo automatico di richiesta di accesso a dati personali.

Con l’API, il processo generale di accesso a dati personali è uguale al processo che si segue quando si [utilizza l’interfaccia](privacy-requests-ui.md). L’unica differenza consiste nella creazione della richiesta di accesso a dati personali. Invece di creare la richiesta in Adobe Campaign, viene inviato a Campaign un POST contenente le informazioni sulla richiesta. Per ogni richiesta, viene aggiunta una nuova voce nella schermata **[!UICONTROL Privacy Requests]**. I flussi di lavoro tecnici per la privacy elaborano quindi la richiesta, come per una richiesta aggiunta utilizzando l’interfaccia.

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

## Richiamare l’API esternamente {#invoking-api-externally}

Ecco un esempio di come richiamare l’API esternamente (autenticazione tramite l’API e dettagli specifici sull’API Privacy). Per ulteriori informazioni sull&#39;API Privacy, consulta la [documentazione API](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=it). È inoltre possibile consultare la [documentazione sulle chiamate al servizio web](../../configuration/using/web-service-calls.md).

Innanzitutto, devi eseguire l’autenticazione tramite l’API:

1. Scarica il file WSDL **xtk:session** tramite questo URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Utilizza il metodo “Logon” e passa un nome utente e una password come parametri nella richiesta. Riceverai una risposta contenente un token di sessione. Ecco un esempio che utilizza SoapUI.

   ![](assets/do-not-localize/privacy-api.png)

1. Utilizza il Token di sessione restituito come autenticazione per tutte le chiamate API successive. Scade dopo 24 ore.

Quindi invoca l’API Privacy:

1. Scarica il file WSDL da questo URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Utilizza **[!UICONTROL CreateRequestByName]** per creare una richiesta di accesso a dati personali specifica.

   Di seguito è riportato un esempio che utilizza **[!UICONTROL CreateRequestByName]**. Osserva come viene utilizzato il token di sessione fornito in precedenza come autenticazione. La risposta è l’ID della richiesta creata.

   ![](assets/do-not-localize/privacy-api-2.png)

   Per aiutarti a eseguire i passaggi precedenti, considera quanto segue:

   * È possibile utilizzare **queryDef** nello schema **nms:gdprRequest** per controllare lo stato della richiesta di accesso.
   * È possibile utilizzare **queryDef** nello schema **nms:gdprRequestData** per ottenere il risultato della richiesta di accesso.
   * Per scaricare il file XML da **“$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id”**, è necessario aver effettuato l’accesso e accedervi da un IP inserito nell’elenco Consentiti. A questo scopo, crea un’applicazione web che ti consenta di accedere al file generato da JSSP.

## Richiamare l’API da un JS {#invoking-api-from-js}

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
  This code calls an API to create new Privacy request on the DB.
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
  This code calls an API to create new Privacy request on the DB.
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
  This code calls an API to create new Privacy request on the DB.
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
