---
title: Rifiuto tracciamento applicazione Web
seo-title: Rifiuto tracciamento applicazione Web
description: Rifiuto tracciamento applicazione Web
seo-description: null
page-status-flag: never-activated
uuid: c9b9eee2-a5be-4378-b2d7-53ed7121eae8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8f413002-bd32-426f-88b9-44cefae68593
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a62e4d072573f7ed1b77f755eb57838c70745592
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---


# Rifiuto tracciamento applicazione Web{#web-application-tracking-opt-out}

Adobe Campaign consente di interrompere il tracciamento dei comportamenti Web degli utenti finali che rifiutano il tracciamento del comportamento tramite cookie o Web beacon. La funzione include la possibilità di visualizzare un banner per presentare all’utente finale tale opzione; potete aggiungere questi banner alle applicazioni Web o alle pagine di destinazione.

Se un utente finale rinuncia al tracciamento del comportamento tramite cookie o Web beacon, tali informazioni vengono trasmesse al server di tracciamento di Adobe Campaign con API JavaScript. Nota che alcune giurisdizioni possono richiedere che il Cliente presenti agli utenti finali una clausola di rinuncia prima che sia possibile offrire (o che abbia altri requisiti legali), ed è responsabilità del Cliente rispettare le leggi applicabili.

>[!NOTE]
>
>Quando gli script seguono sempre le linee guida descritte nell&#39;elenco di controllo [Sicurezza e Privacy](https://helpx.adobe.com/campaign/kb/acc-security.html#dev).

## Configurazione del banner {#configuring-the-banner-}

Per essere visualizzato all&#39;interno di applicazioni Web o pagine di destinazione, il banner deve essere configurato.

Adobe Campaign viene fornito con un banner di esempio che devi adattare alle tue esigenze. Questa versione del banner viene visualizzata come blocco di personalizzazione nella cartella del modello di contenuto. Fare riferimento a [questa pagina](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>Per creare un banner personalizzato, dovete personalizzare il banner out-of-the-box.

Per attivare il banner, è necessario configurare le proprietà dell&#39;applicazione Web. Fare riferimento alla sezione [Progettazione di un&#39;applicazione](../../web/using/designing-a-web-application.md) Web.

Se il tracciamento Web è attivato, potete disporre di:

* Nessun banner.
* Configurate manualmente il banner su ciascuna pagina: selezionate questa opzione e selezionate il banner in ciascuna pagina nelle proprietà della pagina.

   ![](assets/pageproperties.png)

* Aggiungete automaticamente il banner a tutte le pagine: selezionate il banner direttamente nelle proprietà dell&#39;applicazione Web.

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>Per l’applicazione Web v5 è disponibile una modalità di compatibilità con lo stesso comportamento.

Il banner predefinito ha la struttura seguente:

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

È necessario sostituire il messaggio **Inserire qui** con il blocco contenente le informazioni di tracciamento. Questa sostituzione deve essere eseguita nel nuovo blocco di personalizzazione relativo al banner di rinuncia.

Il banner viene distribuito con un CSS specifico. Tuttavia, potete sovrascrivere gli stili durante la creazione e la configurazione di una pagina Web. Fare riferimento a [questa pagina](../../web/using/content-editor-interface.md).

## Impostazione del cookie di rinuncia tramite API {#setting-the-opt-out-cookie-using-api}

Adobe Campaign viene fornito con le API che consentono di gestire il valore del cookie e recuperare le preferenze utente.

Il nome del cookie è **acoptout**. I valori comuni sono:

* 0: l&#39;utente ha consentito il tracciamento Web (valore predefinito)
* 1: l&#39;utente ha vietato il tracciamento Web
* null: l&#39;utente non ha scelto, ma il tracciamento Web è consentito in quanto è il valore predefinito

Le API lato client disponibili per personalizzare il banner sono:

* **NL.ClientWebTracking.allow()**: Imposta il valore del cookie di rinuncia per consentire il tracciamento Web. Il tracciamento Web è consentito per impostazione predefinita.
* **NL.ClientWebTracking.forbid()**: Imposta il valore del cookie di rinuncia per impedire il tracciamento Web. Per il tracciamento Web è necessario che l&#39;input dell&#39;utente sia vietato.
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**: Chiude il banner di cookie di rinuncia dopo che l&#39;utente ha fatto clic sul pulsante Accetta o Rifiuta. (durante la fase di pubblicazione dell&#39;evento click)

   bannerDomElt {DOMElement} l&#39;elemento DOM principale del banner cookie che deve essere rimosso

* **NL.ClientWebTracking.hasUserPrefs()**: Restituisce true se l&#39;utente ha scelto le proprie preferenze per il tracciamento Web.
* **NL.ClientWebTracking.getUserPrefs()**: Restituisce il valore del cookie di rinuncia che definisce le preferenze dell&#39;utente.

Per scrivere un JSSP, sono disponibili le API lato server:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**: Genera la marcatura per il banner di rinuncia da inserire nella pagina JSSP

   **escapeJs {Boolean}**: true quando la marcatura generata deve essere preceduta per essere utilizzata in JavaScript.

   Restituisce l&#39;HTML della marcatura del banner di rinuncia che deve essere stampata nella pagina.

* **NL.ServerWebTracking._displayOptOutBanner()**

   Restituisce true se il banner di rinuncia deve essere visualizzato dopo che l&#39;amministratore ha selezionato un banner di rinuncia

   Questo codice viene chiamato quando l&#39;amministratore ha già scelto di utilizzare il banner di rifiuto del tracciamento Web.

   Il banner deve essere visualizzato se l&#39;utente non ha ancora scelto di essere tracciato o meno.

* **NL.ServerWebTracking.renderingOptOutBanner(escapeJs)**

   Consente di renderizzare la marcatura per il banner di rinuncia inserendola nella pagina JSSP. Viene chiamato come in Jssp tra &lt;% %>

   **escapeJs {Boolean}**: true quando è necessario che la marcatura generata sia preceduta dall&#39;escape per essere utilizzata in JavaScript

Esempio JSSP:

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```

