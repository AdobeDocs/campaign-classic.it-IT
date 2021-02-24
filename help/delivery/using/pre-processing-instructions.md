---
solution: Campaign Classic
product: campaign
title: Istruzioni per la preelaborazione degli URL tracciati
description: Ulteriori informazioni sulle istruzioni pre-elaborazione da utilizzare per eseguire lo script dell'URL di un'e-mail e per tenerla ancora traccia.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 9f898e28b981ea4257c9f4b73a579d322ddbba89
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Istruzioni pre-elaborazione {#pre-processing-instructions}

Le istruzioni &lt;%@ non sono JavaScript, ma la sintassi è specifica per  Adobe Campaign.

Si applicano solo nel contesto della distribuzione dei contenuti. È l’unico modo per creare uno script per l’URL di un messaggio e-mail e tenerlo tracciato (oltre ai parametri dell’URL). Possono essere visualizzati come copia/incolla automatica applicata durante l&#39;analisi della consegna prima di rilevare i collegamenti da tracciare.

Esistono tre tipi di istruzioni:

* &quot;**include**&quot;: principalmente per fattorizzare alcune opzioni, blocchi di personalizzazione, file esterni o pagine
* &quot;**value**&quot;: per consentire l&#39;accesso ai campi della consegna, alle variabili di consegna e agli oggetti personalizzati caricati nella consegna
* &quot;**foreach**&quot;: per eseguire il ciclo continuo di un array caricato come oggetto personalizzato.

Possono essere testati direttamente dalla procedura guidata di consegna. Si applicano nell’anteprima del contenuto e quando fate clic sul pulsante di tracciamento per visualizzare l’elenco degli URL.

## &lt;>{#<%@-include}

Di seguito sono riportati alcuni esempi tra i più utilizzati:

* Incluso il collegamento alla pagina mirror: `<%@ include view="MirrorPage" %>`
* URL pagina mirror: &quot;Visualizza come `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* URL predefinito per l’annullamento della sottoscrizione: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Altri esempi:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Utilizzate il pulsante di personalizzazione nella procedura guidata di distribuzione per ottenere la sintassi corretta.

## &lt;>{#<%@-value}

Questa istruzione consente di accedere ai parametri della consegna costanti per tutti i destinatari.

Sintassi:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Dove:

* &quot;object&quot;: nome dell&#39;oggetto (esempio: consegna, fornitore e così via).
* &quot;xpath&quot;: xpath del campo.
* &quot;index&quot; (facoltativo): se &quot;object&quot; è un array (per oggetti script aggiuntivi), l&#39;indice degli elementi nell&#39;array (Inizia da 0).

L&#39;oggetto può essere:

* &quot;consegna&quot;: per la consegna corrente (vedere i dettagli e le restrizioni nella sottosezione seguente).
* &quot;provider&quot;: per il provider di consegna/routing corrente (nms:externalAccount).
* Un oggetto script aggiuntivo: se un oggetto viene caricato nel contesto tramite: **Proprietà** > **Personalizzazione** > **Aggiungi oggetti nel contesto di esecuzione**.
* Elemento del ciclo foreach: vedere la sezione [Foreach](#<%@-foreach) seguente.

### oggetto &quot;delivery&quot; {#delivery-object}

Per la personalizzazione delle e-mail, l&#39;oggetto di consegna è accessibile in due modi:

* In JavaScript. Ad esempio: `<%= delivery.myField %>`.

   Nei campi JavaScript per la distribuzione degli oggetti non sono supportati i campi personalizzati. Funzionano nell&#39;anteprima, ma non nell&#39;MTA perché l&#39;MTA può accedere solo allo schema di consegna out-of-the-box.

* Tramite `<%@ value object="delivery"` pre-elaborazione.

Per l&#39;istruzione `<%@ value object="delivery" xpath="@myCustomField" %>`, esiste un&#39;altra limitazione per le consegne inviate tramite mid-sourcing. Il campo personalizzato @myCustomField deve essere aggiunto allo schema nms:delivery sia sulle piattaforme di marketing che sulle piattaforme di mid-sourcing.

>[!NOTE]
>
>Per i parametri/variabili di consegna, utilizzare la sintassi seguente (utilizzando l&#39;oggetto di consegna):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#<%@-value-in-javascript}

Per consentire l&#39;utilizzo del valore &lt;%@ nelle sezioni di script, due oggetti speciali vengono sostituiti con &lt;% e %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Ad esempio:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#<%@-foreach}

Questa istruzione consente l&#39;iterazione su un array di oggetti caricati nella consegna per tenere traccia dei singoli collegamenti relativi agli oggetti.

Sintassi:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Dove:

* &quot;object&quot;: nome dell&#39;oggetto da cui iniziare, in genere un oggetto script aggiuntivo, ma può essere una consegna.
* &quot;xpath&quot; (facoltativo): xpath della raccolta su cui eseguire il ciclo. Il valore predefinito è &quot;.&quot;, ovvero l&#39;oggetto è l&#39;array su cui eseguire il ciclo.
* &quot;index&quot; (facoltativo): se xpath non è &quot;.&quot; e object è un array stesso, l&#39;indice dell&#39;elemento dell&#39;oggetto (inizia da 0).
* &quot;item&quot; (facoltativo): nome di un nuovo oggetto accessibile con il valore &lt;%@ all&#39;interno del ciclo foreach. Impostazione predefinita con il nome del collegamento nello schema.

Esempio:

Nelle proprietà di consegna/personalizzazione, caricate un array di articoli e una tabella di relazione tra il destinatario e gli articoli.

Per visualizzare i collegamenti a questi articoli è sufficiente utilizzare un codice JavaScript come segue:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Con questa soluzione, i collegamenti a tutti gli articoli vengono tracciati senza distinzione. Potete sapere che un destinatario ha fatto clic su un collegamento articolo, ma non potete sapere su quale articolo.

La soluzione consiste nel:

1. Precaricate tutti gli articoli possibili in un array di script aggiuntivo della consegna - articleList[] - il che significa che deve essere presente un numero limitato di articoli possibili.
1. Scrivere una funzione JavaScript all&#39;inizio del contenuto.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```
1. Visualizzare l&#39;articolo chiamando la funzione.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

