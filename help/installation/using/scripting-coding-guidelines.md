---
product: campaign
title: Linee guida per scripting e codifica
description: Scopri le linee guida da seguire per lo sviluppo in Adobe Campaign (flussi di lavoro, JavaScript, JSSP, ecc.)
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 1f96c3df-0ef2-4f5f-9c36-988cbcc0769f
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 4%

---

# Linee guida per scripting e codifica {#scripting-coding-guidelines}



## Scripting

Per ulteriori dettagli, consulta la [documentazione JSAPI per Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it).

Se esegui uno script utilizzando workflow, applicazioni web e jssp, segui le best practice:

* Cercare di evitare il più possibile di utilizzare le istruzioni SQL.

* Se necessario, utilizza funzioni con parametri (istruzione di preparazione) invece della concatenazione di stringhe.

  Pratica non valida:

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
  ```

  Buone pratiche:

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
  ```

  >[!IMPORTANT]
  >
  >sqlSelect non supporta questa funzionalità, pertanto è necessario utilizzare la funzione query della classe DBEngine:

  ```
  var cnx = application.getConnection()
  var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
  for each(var row in stmt) logInfo(row[0] + " : " + row[1])
  cnx.dispose()
  ```

Per evitare SQL injection, è necessario aggiungere le funzioni SQL al inserisco nell&#39;elenco Consentiti di da utilizzare in Adobe Campaign. Una volta aggiunte al inserisco nell&#39;elenco Consentiti di, queste diventano visibili agli operatori nell’editor di espressioni. Consulta [questa pagina](../../configuration/using/adding-additional-sql-functions.md).

>[!IMPORTANT]
>
>Se si utilizza una build precedente alla 8140, l&#39;opzione **XtkPassUnknownSQLFunctionsToRDBMS** potrebbe essere impostata su &#39;1&#39;. Se si desidera proteggere il database, eliminare questa opzione o impostarla su &#39;0&#39;.

Se si utilizza l&#39;input dell&#39;utente per generare filtri nelle query o nelle istruzioni SQL, è sempre necessario eseguirne l&#39;escape (fare riferimento alla [documentazione JSAPI di Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it) - Protezione dei dati: funzioni di escape). Queste funzioni sono:

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## Protezione del nuovo modello dati

### Base cartella

Consulta queste pagine:

* [Proprietà di accesso alle cartelle](../../platform/using/access-management.md)
* [Cartella collegata](../../configuration/using/configuration.md#linked-folder)

### Diritti denominati

Oltre al modello di protezione basato su cartelle, è possibile utilizzare i diritti denominati per limitare le azioni dell&#39;operatore:

* Puoi aggiungere alcuni filtri di sistema (sysFilter) per impedire la lettura/scrittura nei tuoi dati (consulta [questa pagina](../../configuration/using/filtering-schemas.md)).

  ```
  <sysFilter name="writeAccess">    
      <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
  </sysFilter>
  ```

* Puoi anche proteggere alcune azioni (metodo SOAP) definite negli schemi. È sufficiente impostare l’attributo di accesso con il diritto denominato corrispondente come valore.

  ```
  <method name="grantVIPAccess" access="myNewRole">
      <parameters>
  ...
      </parameters>
  </method>
  ```

  Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>È possibile utilizzare i diritti denominati nel nodo del comando in una struttura ad albero. Offre una migliore esperienza utente, ma non fornisce alcuna protezione (utilizza solo il lato client per nasconderli o disabilitarli). Devi utilizzare l’attributo di accesso.

### Tabella di overflow

Se devi proteggere i dati riservati (parte di uno schema) a seconda del livello di accesso dell’operatore, non nasconderli nella definizione del modulo (condizioni enabledIf/visibleIf).

L’entità completa viene caricata dalla schermata, e puoi anche visualizzarla nella definizione della colonna. A questo scopo, è necessario creare una tabella di overflow. Fai riferimento a [questa pagina](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## Aggiunta di captcha nelle applicazioni web

È buona prassi aggiungere un captcha nelle pagine di destinazione pubbliche o nelle pagine di abbonamento. Sfortunatamente, aggiungere un captcha nelle pagine DCE (Digital Content Editor) non è facile. Ti mostreremo come aggiungere un captcha v5 o un reCAPTCHA Google.

Il modo generale per aggiungere un captcha nel DCE consiste nel creare un blocco di personalizzazione per includerlo facilmente nel contenuto della pagina. Dovrai aggiungere un&#39;attività **Script** e un **Test**.

### Blocco di personalizzazione

1. Vai a **[!UICONTROL Resources]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Personalization blocks]** e creane uno nuovo.

1. Utilizza il tipo di contenuto **[!UICONTROL Web application]** e seleziona **[!UICONTROL Visible in the customization menus]**.

   Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/personalization-blocks.md).

   Ecco un esempio di **Captcha campagna**:

   ```javascript
   <%
   var captchaID = CaptchaIDGen();
   %>
   <img src="/nms/jsp/captcha.jsp?captchaID=<%=captchaID%>&width=200&height=50&minWordSize=8&maxWordSize=8"/>
   <input id="captchaValue" name="captchaValue" <%= String(ctx.vars.captchaValid) === "false" ? class="ui-state-error" : "" %>>
   <input type="hidden" name="captchaID" value="<%=captchaID%>"/>
   <%
   if( serverForm.isInputErroneous("captchaValue") ) {
   %>
   <script type="text/javascript"> 
   $("#captchaValue").addClass("ui-state-error")
   </script>
   <%
   }
   %>
   ```

   * Le linee da 1 a 6 generano tutti gli input necessari.
   * Le righe 7 alla fine gestiscono gli errori.
   * La riga 4 consente di modificare le dimensioni della casella grigia captcha (larghezza/altezza) e la lunghezza della parola generata (minWordSize/maxWordSize).
   * Prima di utilizzare Google reCAPTCHA, è necessario registrarsi su Google e creare un nuovo sito reCAPTCHA.

     `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`

   Dovresti poter disabilitare il pulsante di convalida, ma poiché non disponiamo di pulsanti/collegamenti standard, è meglio farlo nel HTML stesso. Per informazioni su come eseguire questa operazione, fare riferimento a [questa pagina](https://developers.google.com/recaptcha/).

### Aggiornamento dell’applicazione web

1. Accedi alle proprietà dell&#39;applicazione Web per aggiungere una variabile booleana denominata **captchaValid**.

   ![](assets/scripting-captcha.png)

1. Tra l&#39;ultima pagina e l&#39;attività **[!UICONTROL Storage]**, aggiungere **[!UICONTROL Script]** e **[!UICONTROL Test]**.

   Collegare il ramo **[!UICONTROL True]** a **[!UICONTROL Storage]** e l&#39;altro alla pagina che avrà il captcha.

   ![](assets/scripting-captcha2.png)

1. Modificare la condizione del ramo True con `"[vars/captchaValid]"` uguale a True.

   ![](assets/scripting-captcha3.png)

1. Modifica l&#39;attività **[!UICONTROL Script]**. Il contenuto dipenderà dal motore captcha scelto.

1. Infine, puoi aggiungere il blocco personalizzato nella pagina: fai riferimento a [questa pagina](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>Per l&#39;integrazione reCAPTCHA, è necessario aggiungere JavaScript lato client nel HTML (in `<head>...</head>`):
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Campaign captcha

```javascript
var captchaID = request.getParameter("captchaID");
var captchaValue = request.getParameter("captchaValue");
  
if( !CaptchaValidate(captchaID, captchaValue) ) {
  serverForm.logInputError("captchaValue",
                           "The characters you typed for the captcha must match the image ones.",
                           "captchaValue")
  ctx.vars.captchaValid = false
}
else
  ctx.vars.captchaValid = true
```

Riga 6: puoi inserire qualsiasi messaggio di errore.

### Google recaptcha

Consulta la [documentazione ufficiale](https://developers.google.com/recaptcha/docs/verify).

```javascript
ctx.vars.captchaValid = false
var gReCaptchaResponse = request.getParameter("g-recaptcha-response");
  
// Call reCaptcha API to validate it
var req = new HttpClientRequest("https://www.google.com/recaptcha/api/siteverify")
req.method = "POST"
req.header["Content-Type"] = "application/x-www-form-urlencoded"
req.body = "secret=YOUR_SECRET_HERE&response=" + encodeURIComponent(gReCaptchaResponse)
req.execute()
var response = req.response
if( response.code == 200 ) {
  captchaRes = JSON.parse(response.body.toString(response.codePage));
  ctx.vars.captchaValid = captchaRes.success
}
  
if( ctx.vars.captchaValid == false ) {
  serverForm.logInputError("reCaptcha",
                           "Please validate the captcha",
                           "reCaptcha")
  logInfo("reCaptcha not validated")
}
```

Per utilizzare JSON.parse è necessario includere &quot;shared/json2.js&quot; nel WebApp:

![](assets/scripting-captcha6.png)

A partire dalla build 8797, per utilizzare l’URL dell’API di verifica, è necessario aggiungerlo al inserisco nell&#39;elenco Consentiti di nel file serverConf aggiungendo nel nodo urlPermission:

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`
