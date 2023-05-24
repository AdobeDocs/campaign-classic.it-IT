---
product: campaign
title: Istruzioni di pre-elaborazione per gli URL tracciati
description: Scopri di più sulle istruzioni di pre-elaborazione da utilizzare per creare uno script per l’URL di un’e-mail e tenerne traccia
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 2%

---

# Istruzioni di pre-elaborazione {#pre-processing-instructions}



Puoi utilizzare una sintassi specifica nel contenuto della consegna per aggiungere istruzioni e creare uno script per l’URL dell’e-mail tracciata. Le istruzioni &lt;%@ non sono JavaScript: questa sintassi è specifica di Adobe Campaign.

Si applicano solo nel contesto del contenuto della consegna. È l’unico modo per generare uno script per l’URL di un’e-mail e continuarne la tracciabilità (oltre ai parametri URL). Possono essere viste come un copia/incolla automatico applicato durante l’analisi della consegna prima di rilevare i collegamenti da tracciare.

Esistono tre tipi di istruzioni:

* **[!DNL include]**: principalmente per fattorizzare parte del codice in opzioni, blocchi di personalizzazione, file esterni o pagine. [Ulteriori informazioni](#include)
* **[!DNL value]**: per consentire l’accesso ai campi della consegna, alle variabili di consegna e agli oggetti personalizzati caricati nella consegna. [Ulteriori informazioni](#value)
* **[!DNL foreach]**: per eseguire il loop di un array caricato come oggetto personalizzato. [Ulteriori informazioni](#foreach)

Possono essere testati direttamente dalla procedura guidata di consegna. Vengono applicati nell’anteprima del contenuto e quando fai clic sul pulsante di tracciamento per visualizzare l’elenco degli URL.

## [!DNL include] {#include}

I seguenti esempi sono tra i più comunemente utilizzati:

* Inclusione del collegamento alla pagina speculare:

   ```
   <%@ include view="MirrorPage" %>  
   ```

* URL pagina mirror:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* URL predefinito per l’annullamento dell’abbonamento:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* Altri esempi:

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   Utilizza il pulsante di personalizzazione nella consegna guidata per ottenere la sintassi corretta.

## [!DNL value] {#value}

Questa istruzione consente di accedere ai parametri della consegna che sono costanti per tutti i destinatari.

Sintassi:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

Dove:

* **[!DNL object]**: nome dell’oggetto (ad esempio: consegna, provider e così via).
L’oggetto può essere:
   * **[!DNL delivery]**: per la consegna corrente (consulta dettagli e restrizioni nella sottosezione seguente).
   * **[!DNL provider]**: per il provider/ciclo di consegna corrente (nms:externalAccount).
   * Un oggetto script aggiuntivo: se un oggetto viene caricato nel contesto tramite: **Proprietà** > **Personalizzazione** > **Aggiungere oggetti nel contesto di esecuzione**.
   * Elemento del ciclo foreach: vedere [Foreach](#foreach) sezione successiva.
* **[!DNL xpath]**: xpath del campo.
* **[!DNL index]** (facoltativo): se **[!DNL object]** è un array (per oggetti script aggiuntivi), indice dell’elemento nell’array (inizia da 0).

### [!DNL delivery] oggetto {#delivery-object}

Per la personalizzazione delle e-mail, l’oggetto di consegna è accessibile in due modi:

* Utilizzo di JavaScript:

   ```
   <%= delivery.myField %>`.
   ```

   I campi personalizzati di consegna degli oggetti JavaScript non sono supportati. Funzionano nell’anteprima, ma non nell’MTA perché l’MTA può accedere solo allo schema di consegna predefinito.

* Utilizzo di una pre-elaborazione:

   ```
   <%@ value object="delivery"
   ```


**Attenzione**

Se utilizzi quanto segue per le consegne inviate tramite mid-sourcing, il campo personalizzato **@myCustomField** deve essere aggiunto allo schema nms:delivery sia sulle piattaforme di marketing che su quelle di mid-sourcing:

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

Per i parametri/variabili di consegna, utilizza la sintassi seguente (utilizzando l’oggetto di consegna):

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] in una sezione JavaScript {#value-in-javascript}

Per consentire l’utilizzo del valore &lt;%@ nelle sezioni JavaScript, due oggetti speciali vengono sostituiti con &lt;% e %>:

```
<%@ value object='startScript' %>
<%@ value object='endScript' %>
```

Ad esempio:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Questa istruzione consente di eseguire l’iterazione su un array di oggetti caricati nella consegna per monitorare i singoli collegamenti correlati agli oggetti.

Sintassi:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

Dove:

* **[!DNL object]**: nome dell’oggetto da cui iniziare, in genere un oggetto script aggiuntivo, ma può essere una consegna.
* **[!DNL xpath]** (facoltativo): xpath della raccolta su cui eseguire il ciclo. Il valore predefinito è &quot;.&quot;, ovvero l&#39;oggetto corrisponde all&#39;array su cui eseguire il ciclo.
* **[!DNL index]** (facoltativo): se xpath non è &quot;.&quot; e l’oggetto è un array stesso, indice dell’oggetto (inizia da 0).
* **[!DNL item]** (facoltativo): nome di un nuovo oggetto accessibile con il valore &lt;%@ all&#39;interno del ciclo foreach. Predefinito con il nome del collegamento nello schema.

Esempio:

Nelle proprietà/personalizzazione della consegna, carica un array di articoli e una tabella di relazione tra destinatario e articoli.

La visualizzazione di collegamenti a questi articoli può essere eseguita semplicemente con JavaScript, come segue:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Con questa soluzione, i collegamenti a tutti gli articoli sono tracciati senza distinzione. Puoi sapere che un destinatario ha fatto clic su un collegamento di articolo, ma non puoi sapere su quale articolo.

La soluzione consiste nel:

1. Precarica tutti i possibili articoli in un array di script aggiuntivo della consegna - articleList[] - il che significa che deve esistere un numero finito di articoli possibili.
1. Scrivi una funzione JavaScript all’inizio del contenuto.

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
