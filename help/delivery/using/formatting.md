---
product: campaign
title: Formattazione
description: Formattazione
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# Formattazione{#formatting}

![](../../assets/common.svg)

## Modelli JavaScript {#javascript-templates}

Un modello JavaScript è un documento HTML o di testo che include codice JavaScript. Viene generato nello stesso modo di un contenuto e-mail in un’azione di consegna.

### Identificazione di un modello JavaScript {#identification-of-a-javascript-template}

Un modello JavaScript è identificato dal nome e dallo spazio dei nomi, come schemi e moduli. Si consiglia tuttavia di aggiungere l’opzione **.js** al nome del modello.

### Struttura di un modello JavaScript {#structure-of-a-javascript-template}

Esempio di modello di formattazione HTML JavaScript basato sullo schema &quot;cus:book&quot;:

```
<html>
  <body>
    <!-- Title of book -->
    <h1><%= content.@name %></h1>
    <ul>
      <% for each(var chapter in content.chapter) { %>
        <li><%= chapter.@name %></li>
      <% }%>
    </ul>
  </body>
</html>
```

Le varie direttive JavaScript vengono visualizzate nel seguente modulo:

* Unisci campi: visualizza il contenuto dei dati con la sintassi **`<%= <source> %>`** in cui `<source>`è il campo di origine dei dati da visualizzare.
* Blocchi di istruzione: esegue una serie di istruzioni JavaScript incluse tra i tag &lt;% e %>.

L&#39;oggetto **content** rappresenta l&#39;elemento principale del documento XML di input.

Nel nostro esempio, la riga seguente visualizza il contenuto del nome della rubrica:

```
<h1><%= content.@name %></h1>
```

Il codice seguente si ripete sull&#39;elemento di raccolta `<chapter>`:

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

Gli attributi e gli elementi del contenuto sono rappresentati come oggetti JavaScript e rispettano la struttura del documento di origine.

**Esempio**:

* **contenuto.@name**: recupera il valore dell&#39;attributo &quot;name&quot; dell&#39;elemento principale
* **contenuto.@`['name']`**: identico al contenuto **.Sintassi @name**
* **content.capitolo.length**: restituisce il numero di elementi sull&#39;elemento  `<chapter` di raccolta
* **content.capitolo`[0]`.@name**: recupera il nome del primo elemento `<chapter>`
* **capitolo.name()**: restituisce il nome dell’ `<chapter>` elemento
* **capitolo.parent().name()**: restituisce il nome dell&#39;elemento padre di  `<chapter>`

>[!CAUTION]
>
>Poiché il carattere &#39;-&#39; è riservato nel linguaggio JavaScript, il recupero del valore di qualsiasi attributo o elemento contenente questo carattere deve essere eseguito tramite la sintassi `['<field>']`.
>
>Ad esempio: `content.@['offer-id']`.

Tutta la potenza di un linguaggio di programmazione (variabili, loop, test condizionali, funzioni, ecc.) ) è disponibile per creare il documento di output. Le API SOAP sono accessibili per arricchire il documento di output.

Esempi:

* Prova condizionale:

   ```
   <% if (content.@number == 1 || content.@language == 'en') { %>
   <!-- Content to be displayed if test is true--> 
   <% } %>
   ```

* Chiamata di funzione:

   ```
   <!-- Displays a horizontal bar -->
   ;<% function DisplayHorizontalBar() { %>
     <hr/>
   <% } %> 
   
   <!-- The same function in a block  -->
   <% 
   function DisplayHorizontalBar2()
   {
     document.write('<hr/>');
   }
   %> 
   
   <!-- Returns the value in uppercase -->
   <% 
   function formatName(value)
   { 
     return value.toUpperCase(); 
   }
   %>
   
   <!-- Call functions -->
   <%= DisplayHorizontalBar1() %>
   <%= DisplayHorizontalBar2() %>
   <%= formatName(content.@name) %>
   ```

* Dichiarazioni e chiamata variabile:

   ```
   <%  var counter = 0; %>
   
   <%= counter += 10 %>
   ```

* Recupero e visualizzazione del nome di un destinatario con metodi statici:

   ```
   <% var recipient = nms.recipient.get(1246); %>
   <%= recipient.lastName %>
   ```

* Recupero e visualizzazione del nome di un destinatario con metodi non statici:

   ```
   <% var query = xtk.queryDef.create(
     <queryDef schema="nms:recipient" operation="get">
       <select>
         <node expr="@lastName"/>
       </select>
       <where>
         <condition expr="@id=1246"/>
       </where>
     </queryDef>);
   
     var recipient = query.ExecuteQuery();
   %>
   
   <%= recipient.@lastName %>
   ```

### Inclusione di un modello JavaScript {#including-a-javascript-template}

Puoi costituire una libreria di funzioni o variabili da utilizzare in un secondo momento. A questo scopo, importa il modello JavaScript con la funzione **eval** . Questo consente di arricchire i contesti con funzioni aggiuntive dichiarate in altri modelli JavaScript.

**Esempio**: importazione di  **common.** jsptemplate.

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### Modifica di un modello JavaScript {#editing-a-javascript-template}

L’area di modifica consente di compilare il contenuto del modello JavaScript:

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>Lo schema del modello dati associato deve essere popolato per l&#39;inizializzazione degli oggetti JavaScript.

Per generare l’anteprima del documento di output in qualsiasi momento, seleziona un contenuto e un formato di output (HTML, testo, XML), quindi fai clic su **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>Non è necessario salvare le modifiche per visualizzare in anteprima il documento di output.

### Esempio di creazione e utilizzo di un modello JavaScript {#example-of-how-to-create-and-use-a-javascript-template}

Di seguito è riportata la configurazione necessaria per implementare la seguente gestione dei contenuti utilizzando un modello JavaScript:

![](assets/d_ncs_content_sample_1.png)

Questo esempio include i seguenti passaggi:

1. Crea il seguente schema (in questo caso: **neo:news**):

   ```
   <srcSchema _cs="Invitation (neo)"   entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Invitation" mappingType="sql" name="news" namespace="neo" xtkschema="xtk:srcSchema">
   
     <enumeration basetype="string" default="en" name="language">
       <value label="Français" name="fr" value="fr"/>
       <value label="English" name="gb" value="gb"/>
     </enumeration>
   
     <enumeration basetype="string" name="css">
       <value label="Blue" name="bl" value="blue"/>
       <value label="Orange" name="or" value="orange"/>
     </enumeration>
   
     <element label="Intervenants" name="attendee">
       <key internal="true" name="id">
         <keyfield xpath="@id"/>
       </key>
       <attribute label="Name" name="name" type="string"/>
       <element label="Image" name="image" target="xtk:fileRes" type="link"/>
       <attribute label="Description" name="description" type="string"/>
       <attribute default="Gid()" label="Id" name="id" type="long"/>
     </element>
   
     <element label="Invitation" name="news" template="ncm:content" xmlChildren="true">
   
       <compute-string expr="@name"/>
       <attribute enum="language" label="Language" name="language" type="string"/>
       <attribute enum="css" label="Stylesheet" name="css" type="string"/>
       <attribute label="Title" name="title" type="string"/>
       <element label="Presentation" name="presentation" type="html"/>
       <attribute label="Date" name="date" type="date"/>
       <element label="Attendees list" name="attendeesList" ordered="true" ref="attendee" unbound="true"/>
   
     </element>
   </srcSchema>
   ```

1. Crea il modulo di tipo **[!UICONTROL Content management]** collegato (**neo:news**)

   ```
   <form _cs="News (neo)" entitySchema="xtk:form"  img="xtk:form.png" label="News"  name="news" namespace="neo" type="contentForm" xtkschema="xtk:form">
   
     <container type="iconbox">
       <container label="Invitation">
         <input xpath="@langue"/>
         <input xpath="@css"/>
         <input xpath="@title"/>
         <input xpath="@date"/>
         <input xpath="presentation"/>
       </container>
   
       <container label="Intervenants">
         <container toolbarCaption="Liste des intervenants" type="notebooklist" xpath="attendeesList" xpath-label="@nom">
           <container>
             <input xpath="@nom"/>
             <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
               <sysFilter>
                 <condition expr="@isImage = true"/>
               </sysFilter>
             </input>
             <input xpath="@description"/>
           </container>
         </container>
       </container>
     </container>
   
   </form>
   ```

1. Crea i modelli JavaScript con il contenuto dei messaggi per i formati HTML e Testo .

   * Nel nostro esempio, per HTML:

      ```
      <html>     
        <head>         
          <title>Newsletter</title>
           <style type="text/css">
            .body {font-family:Verdana, Arial, Helvetica, sans-serif; font-size:10px; color:#514c48; margin-left: auto; margin-right: auto;}
            .body table {width:748; border: solid 1px; cellpadding:0; cellspacing:0"}
           </style>
        </head>     
        <body>
          <p><center><%= mirrorPage %></center></p>
          <center>
            <table>      
             <tr>
              <td>                                                         
                <img src="[LOGO]"/>                                   
              </td>
              <td>
                <h1><%= content.@title %></h1>
              </td>
             </tr>
             <tr>
      
             <td>
              <div >                                    
                <h0><%= hello,</h0>                              
                <p><%= content.presentation %></p>                                          
      
                <h0>Useful information</h0>                              
                <p>                                  
                  <img src="[IMAGE 1]"/>When? <br/><%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.</p><br/>                                       
                <p>                                  
                  <img src="[IMAGE 2]"/>Who? <br>Meet our favorite authors and illustrators and get a signed copy of their book.</p><br/>                                                         
                <p>                                  
                  <img src="[IMAGE 3]"/>Attendance is free but there is a limited number of seats: sign up now!</p>
            </div>
            </td>
      
              <td>                                                    
               <div style="text-align:left; width:210; height:400px; background:url([IMAGE DE FOND])">
      
                  <h0><%= participant %></h0>
                  <%
                  var i
                  var iLength = content.attendeesList.length()
                  for (i=0; i<iLength; i++)
                  { %>
                  <p>
                    <%= generateImgTag(content.attendeesList[i].@["image-id"]) %>  <%= content.attendeesList[i].@description %>
                  </p>  
                  <% }  
                  %>                              
               </div2>
              </td>
          </tr>
        </table>
      </center>
      </body>    
      </html>
      ```

   * Per il testo:

      ```
      <%= content.@title %>
      <%= content.presentation %>
      
      *** When? On <%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.
      
      *** Who? Come and meet our favorite authors and illustrators and get a signed copy of their books. 
      
      *** Attendance is free but there is a limited number of seats: sign up now!
      
      Guests:
      ******************
      <%
      var i
      var iLength = content.attendeesList.length()
      //for (i=(iLength-1); i>-1; i--)
      for( i=0 ; i<iLength ; i++ )
        { %>
        Description <%= i %> : <%= content.attendeesList[i].@description %>
        <% }  
      %>
      ```

1. Ora crea il modello di pubblicazione utilizzato per entrambi i formati:

   * Per HTML:

      ![](assets/d_ncs_content_sample_2.png)

   * Per testo:

      ![](assets/d_ncs_content_sample_3.png)

1. Puoi quindi utilizzare questo modello di contenuto nelle consegne.

   Per ulteriori informazioni, consulta [Utilizzo di un modello di contenuto](using-a-content-template.md).

## Schede di stile XSL {#xsl-stylesheets}

Il linguaggio XSLT consente di modificare un documento XML in un documento di output. A seconda del metodo di output del foglio di stile, il documento risultante può essere generato in HTML, testo normale o un altro albero XML.

Questa trasformazione è a sua volta dettagliata in XML in un documento noto come foglio di stile.

### Identificazione di un foglio di stile {#identifying-a-stylesheet}

Un foglio di stile è identificato dal nome e dallo spazio dei nomi, come schemi e moduli. Si consiglia tuttavia di aggiungere l&#39;estensione **.xsl** al nome del foglio di stile.

La chiave di identificazione di un foglio di stile è una stringa formata dallo spazio dei nomi e dal nome separato da due punti; ad esempio: **cus:book.xsl**.

### Struttura di un foglio di stile {#structure-of-a-stylesheet}

Esempio di un foglio di stile di formattazione HTML basato sullo schema di esempio &quot;cus:book&quot;:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>
  <!-- Point of entry of the stylesheet -->
  <xsl:template match="/book">
    <html>
      <body>
        <!-- Book title -->
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <!-- List of chapters -->
          <xsl:for-each select="child::chapter">
            <li><xsl:value-of select="@name"/></li>
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Un foglio di stile è un documento XML conforme alle regole seguenti:

* i valori degli attributi sono compresi tra virgolette,
* un elemento deve avere un marcatore di apertura e un marcatore di chiusura,
* sostituire i caratteri &#39;&lt;&#39; o &#39;&amp;&#39; con le entità **&#39;&lt;&#39;** o **&#39;&amp;&#39;**,
* ogni elemento XSL deve utilizzare lo spazio dei nomi **xsl**.

Un foglio di stile deve iniziare con il marcatore elemento principale XSL **`<xsl:stylesheet>`** e terminare con il marcatore **`</xsl:stylesheet>`**. Lo spazio dei nomi XSL deve essere definito nel marcatore di apertura come segue:

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

L&#39;elemento **`<xsl:output>`** specifica il formato del documento generato. Specifica il set di caratteri desiderato e il formato di output.

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

Le istruzioni seguenti descrivono la configurazione del foglio di stile per la formattazione del documento di output.

```
<xsl:template match="/book">
  <html>
    <body>
      <!-- Book title -->
      <h1><xsl:value-of select="@name"/></h1>
      <lu>
        <!-- List of chapters -->
        <xsl:for-each select="child::chapter">
          <li><xsl:value-of select="@name"/></li>
        </xsl:for-each>
      </lu>
    </body>
  </html>
</xsl:template>
```

Per impostazione predefinita, il processore XSLT cerca il **template** che si applica al nodo principale o principale del documento XML di input. La costruzione del documento di output inizia con questo **template**.

Nel nostro esempio, una pagina HTML viene generata dallo schema &quot;cus:book&quot; visualizzando il nome del libro e l&#39;elenco dei capitoli.

>[!NOTE]
>
>Per ulteriori informazioni sul linguaggio XSLT, fare riferimento a un documento di riferimento XSLT.

### Visualizzazione di HTML/XML {#displaying-html-xml}

Per visualizzare un campo **html**, utilizza l&#39;opzione **disable-output-escape=&quot;yes&quot;** dalla direttiva **`<xsl:value-of>`**. Questo consente di evitare la sostituzione dei caratteri con la relativa entità XML (ad esempio &lt; con &lt;).

La direttiva **`<xsl:text>`** con l&#39;opzione **disable-output-escape=&quot;yes&quot;** consente di inserire tag JavaScript per campi di personalizzazione o test condizionali.

Esempi:

* Visualizzazione del contenuto di un campo di tipo &quot;html&quot;:

   ```
   <xsl:value-of select="summary" disable-output-escaping="yes"/>
   ```

* Inserimento del campo di personalizzazione **&lt;%= recipient.email %>**:

   ```
   <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
   ```

* Aggiunta del test condizionale **&lt;% if (recipient.language == &#39;en&#39;) `{` %>**:

   ```
   <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
   ```

### Inclusi fogli di stile {#including-stylesheets}

È possibile creare una libreria di modelli o variabili da condividere tra diversi fogli di stile. Il &quot;longMonth&quot; **template**, presentato sopra, è un esempio tipico del vantaggio di individuare un modello in remoto in un foglio di stile in modo che possa essere riutilizzato in un secondo momento.

La direttiva **`<xsl:include>`** indica il nome del foglio di stile da includere nel documento.

**Esempio**: incluso il foglio di stile &quot;common.xsl&quot;.

```
<? xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:include href="common.xsl"/> 
  <xsl:output encoding="ISO-8859-1" method="jsp" indent="yes"/>
  ...
</xsl:stylesheet>
```

>[!NOTE]
>
>Il nome dello spazio dei nomi non deve essere immesso nel riferimento del foglio di stile da includere. Come standard, questo foglio di stile viene creato con lo spazio dei nomi utente.

### Modifica di un foglio di stile {#editing-a-stylesheet}

La zona di modifica consente di compilare il contenuto del foglio di stile:

![](assets/d_ncs_content_form14.png)

Per generare un’anteprima del documento di output in qualsiasi momento, seleziona un’istanza di contenuto e il formato (HTML, testo, XML), quindi fai clic su **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>Non è necessario salvare le modifiche nel foglio di stile per visualizzare l&#39;anteprima del documento di output.

## Gestione delle immagini {#image-management}

### Riferimento immagine {#image-referencing}

È possibile fare riferimento alle immagini inserite nel documento di output HTML con riferimenti assoluti o relativi.

Il riferimento relativo consente di inserire l&#39;URL del server contenente le immagini nelle opzioni **NcmResourceDir** e **NcmResourcesDirPreview** . Queste opzioni contengono il percorso delle immagini per la pubblicazione e l’anteprima nella console client di Adobe Campaign.

Queste due opzioni sono accessibili tramite la schermata di gestione delle opzioni nella cartella **[!UICONTROL Administration > Platform > Options]** .

**Esempio**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

Durante l&#39;elaborazione del foglio di stile, l&#39;attributo **_resPath** sull&#39;elemento principale del documento XML di input viene compilato automaticamente con una o più opzioni a seconda del contesto (anteprima o pubblicazione).

Esempio di utilizzo dell’opzione di posizionamento dell’immagine e del relativo utilizzo con un’immagine:

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>Si consiglia di dichiarare una variabile contenente il riferimento del server in cui vengono memorizzate le immagini (&quot;resPath&quot; nel nostro esempio).

### Utilizzo delle risorse pubbliche {#using-public-resources}

È inoltre possibile utilizzare **[!UICONTROL Public resources]** per dichiarare le immagini e caricarle sul server a seconda delle impostazioni di istanza immesse nella procedura guidata di distribuzione.

Puoi quindi richiamare queste immagini nel contenuto. a questo scopo, utilizza la seguente sintassi nello schema di gestione del contenuto:

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

Nel modulo, il campo per la selezione dell’immagine verrà aggiunto tramite la seguente sintassi:

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>Per ulteriori informazioni su **[!UICONTROL Public resources]** e su come configurarli e utilizzarli, consulta [questa sezione](../../installation/using/deploying-an-instance.md#managing-public-resources).

## Visualizzazione data {#date-display}

Nel documento di input XML, le date sono memorizzate nel formato XML interno: **AAAA/MM/GG HH:MM:SS** (esempio 2018/10/01 12:23:30).

Adobe Campaign fornisce funzioni di formattazione della data per i modelli JavaScript e i fogli di stile XSL descritti di seguito.

### Formattazione data JavaScript {#javascript-date-formatting}

Per visualizzare una data nel formato desiderato, Adobe Campaign fornisce la funzione **formatDate** che prende come input il contenuto della data e una stringa che specifica il formato di output con la seguente sintassi: **%4Y/%2M/%2D %2H%2N%2S**

Esempi:

* Visualizza la data nel formato **31/10/2018**:

   ```
    <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
   ```

* Visualizza la data nel formato **Luglio 2018**:

   ```
   <%
    function displayDate(date)
     {
       var aMonth = 
       [ 'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December' ];
   
       var month = formatDate(content.@date, "%2M")
       var year = formatDate(content.@date, "%4Y")
   
       return aMonth[month-1]+" "+year;
     }
   %>
   
   <%= displayDate(content.@date) %>
   ```

### Formattazione data XSL {#xsl-date-formatting}

Nella sintassi XSLT non è presente una funzione di gestione della data standard. Per visualizzare una data nel formato desiderato, Adobe Campaign fornisce la funzione esterna **formato data**. Questa funzione assume come input il contenuto della data e una stringa che specifica il formato di output con la seguente sintassi: **%4Y/%2M/%2D %2H%2N%2S**

Esempi:

* Per visualizzare la data nel formato **01/10/2018**:

   ```
   <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
   ```

* Per visualizzare la data nel formato **Luglio 2018**:

   ```
   <!-- Returns the month in the form of a string with the month number as input -->
   <xsl:template name="longMonth">
     <xsl:param name="monthNumber"/>
   
     <xsl:choose>
       <xsl:when test="$monthNumber = 1">January</xsl:when>
       <xsl:when test="$monthNumber = 2">February</xsl:when>
       <xsl:when test="$monthNumber = 3">March</xsl:when>
       <xsl:when test="$monthNumber = 4">April</xsl:when>
       <xsl:when test="$monthNumber = 5">May</xsl:when>
       <xsl:when test="$monthNumber = 6">June</xsl:when>
       <xsl:when test="$monthNumber = 7">July</xsl:when>
       <xsl:when test="$monthNumber = 8">August</xsl:when>
       <xsl:when test="$monthNumber = 9">September</xsl:when>
       <xsl:when test="$monthNumber = 10">October</xsl:when>
       <xsl:when test="$monthNumber = 11">November</xsl:when>
       <xsl:when test="$monthNumber = 12">December</xsl:when>
     </xsl:choose>
   </xsl:template> 
   
   <!-- Display date -->
   <xsl:call-template name="longMonth">
     <xsl:with-param name="monthNumber">
       <xsl:value-of select="external:date-format(@date, '%2M')"/>
     </xsl:with-param>
   </xsl:call-template>
    <xsl:value-of select="external:date-format(@date, '%4y')"/>
   ```
