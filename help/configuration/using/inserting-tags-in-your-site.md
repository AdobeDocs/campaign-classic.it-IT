---
product: campaign
title: Inserire i tag di tracciamento web nel sito
description: Scopri come inserire i tag di tracciamento web nel sito
feature: Configuration
role: Developer
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Inserire i tag di web tracking nel sito{#inserting-tags-in-your-site}

## Metodo semplice {#simple-method}

Questo metodo consiste nell&#39;inviare una chiamata HTTP al server di reindirizzamento inserendo un tag HTML **`<img>`** nel codice sorgente HTML della pagina Web che si desidera tracciare.

>[!IMPORTANT]
>
>Questo metodo utilizza i cookie inviati dal browser web per identificare il destinatario e non è affidabile al 100%.

**Esempio**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

Il tag inserito contatta il server di reindirizzamento.

![](assets/d_ncs_integration_webtracking_structure2.png)

Quando definisci una pagina da tracciare nella console, puoi generare un tag di tracciamento web di esempio da copiare e incollare nel codice sorgente della pagina web.

Quando si utilizzano i tag di tipo TRANSACTION, tuttavia, è necessario modificare il tag di esempio utilizzando JavaScript per inserire le informazioni sulla transazione (importo, numero di elementi) ed eventuali informazioni definite da uno schema di estensione.

### Inserimento statico di tag {#static-insertion-of-tags}

Per eseguire l’inserimento di tag statici, è sufficiente copiare e incollare i tag generati dalla console o costruiti manualmente nell’origine della pagina web.

**Esempio**: inserimento di un tag di tracciamento Web in una pagina che visualizza un modulo.

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

Inserimento di un tag di tracciamento web di tipo TRANSACTION nella pagina di conferma (&quot;amount.md&quot;).

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

### Generazione dinamica di tag di tracciamento web {#dynamic-generation-of-web-tracking-tags}

Quando le pagine web vengono generate dinamicamente, puoi aggiungere il tag di tracciamento web al momento della generazione della pagina.

**Esempio**: il tracciamento web è stato aggiunto ai JSP.

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

## Metodo ottimale {#optimum-method-}

Se desideri controllare le informazioni inviate al server di reindirizzamento, il modo più affidabile è quello di eseguire la query HTTP in modo sincrono utilizzando un linguaggio per la generazione delle pagine.

L&#39;URL creato deve rispettare le regole di sintassi definite in [Tag di tracciamento Web: definition](../../configuration/using/web-tracking-tag-definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>Il reindirizzamento e il tracciamento web utilizzano i cookie ed è importante che il server web che esegue la chiamata HTTP sincrona si trovi nello stesso dominio del server di reindirizzamento. I vari scambi HTTP devono trasmettere i cookie &quot;id&quot;, &quot;uuid&quot; e &quot;uuid230&quot;.

**Esempio**: generazione dinamica in Java, con autenticazione del destinatario utilizzando il numero di account.

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
