---
product: campaign
title: Linee guida per scripting e codifica
description: Ulteriori informazioni sulle linee guida da seguire nello sviluppo in Adobe Campaign (flussi di lavoro, JavaScript, JSSP, ecc.).
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 1f96c3df-0ef2-4f5f-9c36-988cbcc0769f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 5%

---

# Linee guida per scripting e codifica {#scripting-coding-guidelines}

## Scripting

Per ulteriori informazioni, consulta la [documentazione JSAPI della campagna](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Se esegui lo script utilizzando workflow, applicazioni web, jssp, segui queste best practice:

* Provare a evitare di utilizzare le istruzioni SQL il più possibile.

* Se necessario, utilizzare funzioni con parametri (istruzione di preparazione) invece della concatenazione di stringhe.

   Cattiva pratica:

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
   ```

   Buona pratica:

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
   ```

   >[!IMPORTANT]
   >
   >sqlSelect non supporta questa funzione, pertanto devi utilizzare la funzione di query della classe DBEngine:

   ```
   var cnx = application.getConnection()
   var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
   for each(var row in stmt) logInfo(row[0] + " : " + row[1])
   cnx.dispose()
   ```

Per evitare iniezioni SQL, è necessario aggiungere le funzioni SQL all&#39;elenco consentiti da utilizzare in Adobe Campaign. Una volta aggiunti all’elenco consentiti, diventano visibili agli operatori nell’editor espressioni. Consulta [questa pagina](../../configuration/using/adding-additional-sql-functions.md).

>[!IMPORTANT]
>
>Se utilizzi una build precedente a 8140, l&#39;opzione **XtkPassUnknownSQLFunctionsToRDBMS** potrebbe essere impostata su &#39;1&#39;. Se desideri proteggere il database, elimina questa opzione (o impostala su &quot;0&quot;).

Se utilizzi l’input dell’utente per creare filtri in query o istruzioni SQL, devi sempre eseguirne l’escape (consulta la [documentazione JSAPI di Campaign](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) - Protezione dei dati: funzioni di escape). Queste funzioni sono:

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## Protezione del nuovo modello dati

### Base cartelle

Fai riferimento a queste pagine:

* [Proprietà di accesso alla cartella](../../platform/using/access-management.md)
* [Cartella collegata](../../configuration/using/configuration.md#linked-folder)

### Diritti denominati

Oltre al modello di sicurezza basato su cartelle, puoi utilizzare diritti denominati per limitare le azioni dell’operatore:

* È possibile aggiungere alcuni filtri di sistema (sysFilter) per impedire la lettura/scrittura nei dati (vedere [questa pagina](../../configuration/using/filtering-schemas.md)).

   ```
   <sysFilter name="writeAccess">    
       <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
   </sysFilter>
   ```

* È inoltre possibile proteggere alcune azioni (metodo SOAP) definite negli schemi. È sufficiente impostare l&#39;attributo di accesso con il diritto corrispondente denominato come valore.

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
>È possibile utilizzare i diritti denominati nel nodo del comando in un navtree. Offre una migliore esperienza utente ma non fornisce alcuna protezione (usa solo il lato client per nasconderli/disattivarli). È necessario utilizzare l&#39;attributo di accesso.

### Tabella di overflow

Se è necessario proteggere i dati riservati (parte di uno schema) a seconda del livello di accesso dell’operatore, non nasconderli nella definizione del modulo (condizioni enabledIf/visibleIf).

L’entità completa viene caricata dalla schermata , ed è possibile visualizzarla anche nella definizione della colonna. A questo scopo, devi creare una tabella di overflow. Fai riferimento a [questa pagina](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## Aggiunta di sottotitoli nelle applicazioni web

È buona norma aggiungere un captcha nelle pagine di destinazione/nelle pagine di abbonamento pubbliche. Sfortunatamente, aggiungere un captcha nelle pagine DCE (Digital Content Editor) non è facile. Ti mostreremo come aggiungere un captcha v5 o un Google reCAPTCHA.

Il modo generale per aggiungere un captcha nel DCE consiste nel creare un blocco di personalizzazione per includerlo facilmente nel contenuto della pagina. Sarà necessario aggiungere un&#39;attività **Script** e un **Test**.

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
   * Le linee 7 alla fine della maniglia errori.
   * La linea 4 consente di modificare le dimensioni della casella grigia del captcha (larghezza/altezza) e la lunghezza della parola generata (minWordSize/maxWordSize).
   * Prima di utilizzare Google reCAPTCHA, è necessario registrarsi su Google e creare un nuovo sito reCAPTCHA.

      `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`
   Dovresti essere in grado di disabilitare il pulsante di convalida, ma poiché non disponiamo di un pulsante/collegamento standard, è meglio farlo nell’HTML stesso. Per informazioni su come farlo, fai riferimento a [questa pagina](https://developers.google.com/recaptcha/).

### Aggiornamento dell&#39;applicazione web

1. Accedi alle proprietà dell&#39;applicazione web per aggiungere una variabile booleana denominata **captchaValid**.

   ![](assets/scripting-captcha.png)

1. Tra l’ultima pagina e l’attività **[!UICONTROL Storage]** , aggiungi un **[!UICONTROL Script]** e un **[!UICONTROL Test]**.

   Collega il ramo **[!UICONTROL True]** al **[!UICONTROL Storage]** e l’altro alla pagina che avrà il captcha.

   ![](assets/scripting-captcha2.png)

1. Modificare la condizione del ramo True con `"[vars/captchaValid]"` è uguale a True.

   ![](assets/scripting-captcha3.png)

1. Modifica l’attività **[!UICONTROL Script]** . Il contenuto dipenderà dal motore captcha selezionato.

1. Infine, puoi aggiungere il blocco personalizzato nella pagina: fare riferimento a [questa pagina](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>Per l’integrazione reCAPTCHA, è necessario aggiungere JavaScript lato client nell’HTML (in `<head>...</head>`):
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Captcha campagna

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

Linea 6: puoi inserire qualsiasi tipo di messaggio di errore.

### Google ricontcha

Fare riferimento alla [documentazione ufficiale](https://developers.google.com/recaptcha/docs/verify).

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

Per usare JSON.parse devi includere &quot;shared/json2.js&quot; nella tua webApp:

![](assets/scripting-captcha6.png)

A partire dalla build 8797, per utilizzare l’URL dell’API di verifica, è necessario aggiungerlo all’elenco consentiti nel file serverConf aggiungendo nel nodo urlPermission :

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`
