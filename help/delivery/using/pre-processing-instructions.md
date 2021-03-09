---
solution: Campaign Classic
product: campaign
title: Istruzioni di pre-elaborazione per gli URL tracciati
description: Ulteriori informazioni sulle istruzioni di pre-elaborazione da utilizzare per creare uno script dell’URL di un messaggio e-mail e tenerlo comunque traccia.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 3454af2faffacd43fa1ad852529dad175340a237
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Istruzioni per la preelaborazione {#pre-processing-instructions}

Le istruzioni &lt;%@ non sono JavaScript, la sintassi è specifica di Adobe Campaign.

Si applicano solo nel contesto del contenuto di consegna. È l’unico modo per creare uno script per l’URL di un’e-mail e tenerlo tracciato (oltre ai parametri URL). Possono essere visualizzati come una copia/incolla automatica applicata durante l’analisi della consegna prima di rilevare i collegamenti da tracciare.

Sono disponibili tre tipi di istruzioni:

* &quot;**include**&quot;: principalmente per fattorizzare alcuni codici in opzioni, blocchi di personalizzazione, file esterni o pagine
* &quot;**value**&quot;: per consentire l’accesso ai campi della consegna, alle variabili di consegna e agli oggetti personalizzati caricati nella consegna
* &quot;**foreach**&quot;: per eseguire il ciclo continuo di una matrice caricata come oggetto personalizzato.

Possono essere testati direttamente dalla procedura guidata di consegna. Si applicano nell’anteprima del contenuto e quando fai clic sul pulsante di tracciamento per visualizzare l’elenco degli URL.

## &lt;>{#include}

Gli esempi seguenti sono tra i più utilizzati:

* Incluso il collegamento alla pagina speculare: `<%@ include view="MirrorPage" %>`
* URL pagina speculare: &quot;Visualizza come `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* URL di annullamento della sottoscrizione predefinito: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Altri esempi:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Utilizza il pulsante di personalizzazione nella procedura guidata di consegna per ottenere la sintassi corretta.

## &lt;>{#value}

Questa istruzione fornisce l’accesso ai parametri della consegna costanti per tutti i destinatari.

Sintassi:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Dove:

* &quot;object&quot;: nome dell&#39;oggetto (esempio: consegna, fornitore e così via).
* &quot;xpath&quot;: xpath del campo.
* &quot;index&quot; (facoltativo): se &quot;object&quot; è una matrice (per oggetti script aggiuntivi), l&#39;indice di elemento nella matrice (Starts at 0).

L&#39;oggetto può essere:

* &quot;consegna&quot;: per la consegna corrente (vedi dettagli e restrizioni nella sottosezione seguente).
* &quot;provider&quot;: per il provider/indirizzamento di consegna corrente (nms:externalAccount).
* Un oggetto script aggiuntivo: se un oggetto viene caricato nel contesto tramite: **Proprietà** > **Personalizzazione** > **Aggiungi oggetti nel contesto di esecuzione**.
* Elemento del ciclo foreach: vedi la sezione [Foreach](#foreach) di seguito.

### oggetto &quot;delivery&quot; {#delivery-object}

Per la personalizzazione delle e-mail, l’oggetto di consegna è accessibile in due modi:

* In JavaScript. Ad esempio: `<%= delivery.myField %>`.

   I campi personalizzati di consegna oggetti JavaScript non sono supportati. Funzionano nell’anteprima, ma non nell’MTA perché l’MTA può accedere solo allo schema di consegna predefinito.

* Tramite la pre-elaborazione di `<%@ value object="delivery"`.

Per l’istruzione `<%@ value object="delivery" xpath="@myCustomField" %>`, esiste un altro limite per le consegne inviate tramite mid-sourcing. Il campo personalizzato @myCustomField deve essere aggiunto allo schema nms:delivery sia sulle piattaforme di marketing che di mid-sourcing.

>[!NOTE]
>
>Per i parametri/variabili di consegna, utilizza la sintassi seguente (utilizzando l’oggetto di consegna):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#value-in-javascript}

Per consentire l&#39;utilizzo del valore &lt;%@ nelle sezioni di script, due oggetti speciali vengono sostituiti con &lt;% e %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Ad esempio:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#foreach}

Questa istruzione consente l’iterazione su un array di oggetti caricati nella consegna per tenere traccia dei singoli collegamenti relativi agli oggetti.

Sintassi:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Dove:

* &quot;object&quot;: nome dell’oggetto da cui iniziare, in genere un oggetto script aggiuntivo, ma può essere una consegna.
* &quot;xpath&quot; (facoltativo): xpath della raccolta su cui eseguire il ciclo. Il valore predefinito è &quot;.&quot;, ovvero l’oggetto è la matrice su cui eseguire il ciclo.
* &quot;index&quot; (facoltativo): se xpath non è &quot;.&quot; e l&#39;oggetto è un array stesso, l&#39;indice dell&#39;elemento dell&#39;oggetto (inizia da 0).
* &quot;item&quot; (facoltativo): nome di un nuovo oggetto accessibile con il valore &lt;%@ all&#39;interno del ciclo foreach. Impostazione predefinita con il nome del collegamento nello schema.

Esempio:

Nelle proprietà/personalizzazione di consegna, carica un array di articoli e una tabella di relazione tra destinatario e articoli.

La visualizzazione di collegamenti a questi articoli può essere effettuata semplicemente con un JavaScript come segue:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Con questa soluzione, i collegamenti a tutti gli articoli vengono tracciati senza distinzione. Puoi sapere che un destinatario ha fatto clic su un collegamento a un articolo, ma non puoi sapere su quale articolo.

La soluzione è:

1. Precaricare tutti gli articoli possibili in un array di script aggiuntivo della consegna - articleList[] - il che significa che deve esserci un numero finito di articoli possibili.
1. Scrivi una funzione JavaScript all&#39;inizio del contenuto.

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
1. Visualizza l&#39;articolo chiamando la funzione .

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

