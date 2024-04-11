---
product: campaign
title: Integrazione tramite SOAP (lato server)
description: Integrazione tramite SOAP (lato server)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---

# Integrazione tramite SOAP (lato server){#integration-via-soap-server-side}



I servizi web SOAP forniti per la gestione delle offerte sono diversi da quelli solitamente utilizzati in Adobe Campaign. È possibile accedervi tramite l’URL di interazione descritto nella sezione precedente e presentare o aggiornare le offerte per un determinato contatto.

## Proposta di offerte {#offer-proposition}

Per una proposta di offerta tramite SOAP, aggiungi **nms:proposition#Propose** seguito dai seguenti parametri:

* **targetId**: chiave primaria del destinatario (può essere una chiave composita).
* **maxCount**: specifica il numero di proposte di offerta per il contatto.
* **contesto**: consente di aggiungere informazioni di contesto nello schema dello spazio. Se lo schema utilizzato è **nms:interazione**, **`<empty>`** deve essere aggiunto.
* **categorie**: specifica le categorie a cui devono appartenere le offerte.
* **temi**: specifica i temi a cui devono appartenere le offerte.
* **uuid**: valore del cookie permanente di Adobe Campaign (&quot;uuid230&quot;).
* **nli**: valore del cookie di sessione di Adobe Campaign (&quot;nlid&quot;).
* **noProp**: utilizza il valore &quot;true&quot; per disattivare l’inserimento della proposta.

>[!NOTE]
>
>Il **targetId** e **maxCount** impostazioni obbligatorie. Le altre sono facoltative.

In risposta alla query, il servizio SOAP restituirà i seguenti parametri:

* **interfaceId**: ID dell’interazione.
* **proposte**: elemento XML, contiene l’elenco delle proposte, ciascuna con il proprio ID e la propria rappresentazione HTML.

## Aggiornamento offerta {#offer-update}

Aggiungi il **nms:interazione#UpdateStatus** all&#39;URL, seguito dai seguenti parametri:

* **proposta**: stringa di caratteri che contiene l’ID della proposta fornito come output durante una proposta di offerta. Fai riferimento a [Proposta di offerta](#offer-proposition).
* **stato**: tipo di stringa, specifica il nuovo stato dell’offerta. I valori possibili sono elencati nella **propositionStatus** enumerazione, nel **nms:comune** schema. Ad esempio, il numero 3 corrisponde al valore **Accettato** stato.
* **contesto**: elemento XML che consente di aggiungere informazioni di contesto nello schema dello spazio. Se lo schema utilizzato è **nms:interazione**, **`<empty>`** deve essere aggiunto.

## Esempio di utilizzo di una chiamata SOAP {#example-using-a-soap-call}

Di seguito è riportato un esempio di codice per una chiamata SOAP:

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
