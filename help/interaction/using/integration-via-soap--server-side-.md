---
title: Integrazione tramite SOAP (lato server)
seo-title: Integrazione tramite SOAP (lato server)
description: Integrazione tramite SOAP (lato server)
seo-description: null
page-status-flag: never-activated
uuid: 678371c5-4246-4886-994e-30dbbc70f14a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 477a2c31-0403-4db1-a372-c75dca58380d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Integrazione tramite SOAP (lato server){#integration-via-soap-server-side}

I servizi Web SOAP forniti per la gestione delle offerte sono diversi da quelli generalmente utilizzati in Adobe Campaign. È possibile accedervi tramite l&#39;URL di interazione descritto nella sezione precedente e consentire di presentare o aggiornare le offerte per un determinato contatto.

## Proposta di offerta {#offer-proposition}

Per una proposta di offerta tramite SOAP, aggiungete il comando **nms:proposition#Propose** seguito dai seguenti parametri:

* **targetId**: chiave primaria del destinatario (può essere una chiave composita).
* **maxCount**: specifica il numero di proposte di offerta per il contatto.
* **contesto**: consente di aggiungere informazioni di contesto nello schema dello spazio. Se lo schema utilizzato è **nms:interazioni**, **`<empty>`** aggiungere.
* **categorie**: specifica le categorie a cui devono appartenere le offerte.
* **temi**: specifica i temi a cui devono appartenere le offerte.
* **uuid**: del cookie permanente di Adobe Campaign (&quot;uuid230&quot;).
* **nli**: del cookie di sessione di Adobe Campaign (&quot;nlid&quot;).
* **noProp**: utilizzate il valore &quot;true&quot; per disattivare l&#39;inserimento della proposta.

>[!NOTE]
>
>Le impostazioni **targetId** e **maxCount** sono obbligatorie. Gli altri sono facoltativi.

In risposta alla query, il servizio SOAP restituirà i seguenti parametri:

* **actionId**: ID dell’interazione.
* **proposizioni**: L&#39;elemento XML contiene l&#39;elenco delle proposizioni, ciascuna con un proprio ID e una propria rappresentazione HTML.

## Aggiornamento offerta {#offer-update}

Aggiungete il comando **nms:interactive#UpdateStatus** all’URL, seguito dai seguenti parametri:

* **proposta**: stringa di caratteri, contiene l&#39;ID di proposta fornito come output durante una proposta di offerta. Fare riferimento alla proposta [di offerta](#offer-proposition).
* **status**: tipo di stringa, specifica il nuovo stato dell&#39;offerta. I valori possibili sono elencati nell&#39;enumerazione **propositionStatus** , nello schema **nms:common** . Ad esempio, out-of-the-box, il numero 3 corrisponde allo stato **Accettato** .
* **contesto**: Elemento XML, consente di aggiungere informazioni contestuali nello schema dello spazio. Se lo schema utilizzato è **nms:interazioni**, **`<empty>`** aggiungere.

## Esempio di utilizzo di una chiamata SOAP {#example-using-a-soap-call}

Esempio di codice per una chiamata SOAP:

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
