---
product: campaign
title: Rinuncia al tracciamento delle applicazioni web
description: Rinuncia al tracciamento delle applicazioni web
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 3%

---

# Rinuncia al tracciamento delle applicazioni web{#web-application-tracking-opt-out}



Adobe Campaign consente di interrompere il tracciamento dei comportamenti web degli utenti finali che rinunciano al tracciamento dei comportamenti tramite cookie o web beacon. La funzione include la possibilità di visualizzare un banner per presentare all’utente finale tale opzione; puoi aggiungere questi banner nelle applicazioni web o nelle pagine di destinazione.

Se un utente finale rinuncia al tracciamento dei comportamenti tramite cookie o web beacon, tali informazioni vengono trasmesse al server di tracciamento di Adobe Campaign con API JavaScript. Tieni presente che alcune giurisdizioni possono richiedere che il Cliente presenti agli utenti finali un consenso prima che un diniego possa essere offerto (o avere altri requisiti legali), ed è responsabilità del Cliente rispettare le leggi applicabili.

>[!NOTE]
>
>Quando gli script seguono sempre le linee guida descritte nel [Lista di controllo protezione e privacy](https://helpx.adobe.com/campaign/kb/acc-security.html#dev).

## Configurazione del banner {#configuring-the-banner-}

Per essere visualizzato all’interno di applicazioni Web o pagine di destinazione, è necessario configurare il banner.

Adobe Campaign viene fornito con un banner di esempio che devi adattare alle tue esigenze. Questa versione del banner viene visualizzata come un blocco di personalizzazione situato nella cartella del modello di contenuto. Consulta [questa pagina](../../delivery/using/personalization-blocks.md).

>[!IMPORTANT]
>
>Per creare un banner personalizzato, devi personalizzare il banner preconfigurato.

Per attivare il banner, è necessario configurare le proprietà dell&#39;applicazione Web. Fai riferimento a [Progettazione di un’applicazione web](designing-a-web-application.md) sezione .

Se è attivato il tracciamento Web, è possibile disporre di:

* Nessun banner.
* Configura il banner manualmente su ogni pagina: seleziona questa opzione e seleziona il banner in ogni pagina nelle proprietà della pagina.

   ![](assets/pageproperties.png)

* Aggiungi automaticamente il banner a tutte le pagine: selezionare il banner direttamente nelle proprietà dell&#39;applicazione Web.

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>Per l&#39;applicazione Web v5 è disponibile una modalità di compatibilità con lo stesso comportamento.

Il banner predefinito ha la seguente struttura:

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

È necessario sostituire **Inserisci qui il messaggio** con il blocco contenente le informazioni di tracciamento. Questa sostituzione deve essere eseguita nel nuovo blocco di personalizzazione relativo al banner di rinuncia.

Il banner viene fornito con un CSS specifico. Tuttavia, puoi sovrascrivere gli stili durante la creazione e la configurazione di una pagina web. Consulta [questa pagina](content-editor-interface.md).

## Impostazione del cookie di rinuncia tramite API {#setting-the-opt-out-cookie-using-api}

Adobe Campaign viene fornito con API che ti consentono di gestire il valore dei cookie e recuperare le preferenze utente.

Il nome del cookie è **acoptout**. I valori comuni sono:

* 0: l&#39;utente ha consentito il web tracking (valore predefinito)
* 1: l&#39;utente ha proibito il web tracking
* null: utente non selezionato ma il tracciamento Web è consentito in quanto è il valore predefinito

Le API lato client disponibili per personalizzare il banner sono:

* **NL.ClientWebTracking.allow()**: Imposta il valore del cookie di rinuncia per consentire il tracciamento Web. Il tracciamento web è consentito per impostazione predefinita.
* **NL.ClientWebTracking.forbid()**: Imposta il valore del cookie di rinuncia per impedire il tracciamento Web. Il tracciamento web richiede che l&#39;input dell&#39;utente sia vietato.
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**: Chiude il banner cookie di rinuncia dopo che l’utente ha fatto clic sul pulsante Accetta o Rifiuta . (durante la fase di propagazione degli eventi di clic)

   bannerDomElt {DOMElement} l&#39;elemento DOM radice del banner cookie che deve essere rimosso

* **NL.ClientWebTracking.hasUserPrefs()**: Restituisce true se l&#39;utente ha scelto le proprie preferenze per il tracciamento Web.
* **NL.ClientWebTracking.getUserPrefs()**: Restituisce il valore del cookie di rinuncia che definisce le preferenze dell&#39;utente.

Se è necessario scrivere un JSSP, sono disponibili le API lato server:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**: Genera il markup per il banner di rinuncia da inserire nella pagina JSSP

   **escapeJs {Boolean}**: true quando il markup generato deve essere escape per essere utilizzato in JavaScript.

   Restituisce il HTML del markup del banner di rinuncia che deve essere stampato nella pagina.

* **NL.ServerWebTracking._displayOptOutBanner()**

   Restituisce &quot;true&quot; se il banner di rinuncia deve essere visualizzato dopo che un banner di rinuncia è stato selezionato dall&#39;amministratore

   Questo codice viene chiamato quando l&#39;amministratore ha già scelto di utilizzare il banner di rinuncia al web tracking.

   Il banner deve essere visualizzato se l’utente non ha ancora scelto di essere tracciato o meno.

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   Esegue il rendering del markup per il banner di rinuncia inserendolo nella pagina JSSP. Viene chiamato così come è in Jssp tra &lt;% %>

   **escapeJs {Boolean}**: true quando il markup generato deve essere escape per essere utilizzato in JavaScript

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
