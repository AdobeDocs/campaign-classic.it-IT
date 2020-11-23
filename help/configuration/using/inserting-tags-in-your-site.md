---
solution: Campaign Classic
product: campaign
title: Inserimento di etichette nel sito
description: Inserimento di etichette nel sito
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 5%

---


# Inserimento di etichette nel sito{#inserting-tags-in-your-site}

## Metodo semplice {#simple-method}

Questo metodo consiste nell’inviare una chiamata HTTP al server di reindirizzamento inserendo un tag **`<img>`** HTML nel codice sorgente HTML della pagina Web che si desidera tracciare.

>[!IMPORTANT]
>
>Questo metodo utilizza i cookie inviati dal browser Web per identificare il destinatario e non è affidabile al 100%.

**Esempio**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

Il tag inserito contatta il server di reindirizzamento.

![](assets/d_ncs_integration_webtracking_structure2.png)

Quando definite una pagina da tracciare nella console, potete generare un tag di tracciamento Web di esempio da copiare e incollare nel codice sorgente della pagina Web.

Quando si utilizzano i tag di tipo TRANSACTION, tuttavia, è necessario modificare il tag di esempio utilizzando JavaScript per inserire le informazioni sulla transazione (quantità, numero di elementi) e qualsiasi informazione definita da uno schema di estensione.

### Inserimento statico dei tag {#static-insertion-of-tags}

Per eseguire l’inserimento di tag statici, è sufficiente copiare e incollare i tag generati dalla console oppure creati manualmente nella sorgente della pagina Web.

**Esempio**: inserimento di un tag di tracciamento Web in una pagina in cui è visualizzato un modulo.

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

Inserimento di un tag di tracciamento Web di tipo TRANSACTION nella pagina di conferma (&quot;amount.md&quot;).

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### Generazione dinamica di tag di tracciamento Web {#dynamic-generation-of-web-tracking-tags}

Quando le pagine Web vengono generate in modo dinamico, potete aggiungere il tag di tracciamento Web al momento della generazione della pagina.

**Esempio**: Tracciamento Web aggiunto ai JSP.

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## Metodo Optimum {#optimum-method-}

Se si desidera controllare le informazioni inviate al server di reindirizzamento, il modo più affidabile è quello di eseguire la query HTTP in modo sincrono utilizzando un linguaggio di generazione della pagina.

L’URL creato deve rispettare le regole di sintassi definite nel tag di tracciamento [Web: definizione](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>Il reindirizzamento e il monitoraggio Web utilizzano i cookie ed è importante che il server Web che esegue la chiamata HTTP sincrona si trovi nello stesso dominio del server di reindirizzamento. I vari scambi HTTP devono trasmettere i cookie &#39;id&#39;, &#39;uuid&#39; e &#39;uuid230&#39;.

**Esempio**: Generazione dinamica in Java, con autenticazione del destinatario utilizzando il numero di account.

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```

