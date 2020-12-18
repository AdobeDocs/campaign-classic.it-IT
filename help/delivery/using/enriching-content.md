---
solution: Campaign Classic
product: campaign
title: Arricchimento del contenuto
description: Arricchimento del contenuto
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---


# Arricchimento del contenuto{#enriching-content}

Gli aggregati consentono di arricchire il contenuto con dati esterni. Questi dati provengono da query generiche o tabelle collegate.

## Query generiche {#generic-queries}

Le query sono configurate tramite il modello di pubblicazione nella scheda **[!UICONTROL Aggregator]**.

I dati recuperati arricchiranno il documento di output XML tramite il relativo elemento principale.

Esempio di restituzione da una query sullo schema del destinatario (**nms:destinatario**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

L&#39;elemento **`<collection-recipient>`** rappresenta l&#39;elemento di input del documento risultante da una query. I dati recuperati vengono restituiti sotto questo elemento; nel nostro esempio, un elenco di destinatari.

### Aggiunta di una query {#adding-a-query}

I parametri di query vengono modificati tramite una procedura guidata.

1. Nella prima pagina, specificare l&#39;etichetta e lo schema contenente i dati da recuperare.

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >Il campo di modifica **Path** viene utilizzato per rinominare l&#39;elemento di output della query.

1. La pagina successiva consente di selezionare i dati da recuperare.

   ![](assets/d_ncs_content_query2.png)

1. La pagina successiva definisce la condizione del filtro.

   ![](assets/d_ncs_content_query3.png)

1. L&#39;ultima pagina avvia un&#39;anteprima dei dati restituiti dalla query.

   ![](assets/d_ncs_content_query4.png)

## Tabelle collegate {#linked-tables}

I collegamenti consentono di recuperare dati esterni collegati al contenuto.

Esistono due tipi di dati collegati:

* Collegamenti contenuto: questa è la modalità di gestione del contenuto nativa. Il contenuto del collegamento viene integrato automaticamente nel documento di output XML.
* I collegamenti alle tabelle esterne consentono di accedere a tutte le altre tabelle del database con il vincolo di recuperare i dati del collegamento selezionato con un aggregatore.

### Collegamento a uno schema di contenuto {#link-to-a-content-schema}

Un collegamento contenuto è dichiarato nello schema dati come segue:

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

La definizione del collegamento viene compilata su un **tipo** **`<element>`** e l&#39;attributo **espandereSchemaTarget** fa riferimento allo schema di destinazione (&quot;cus:Chapter&quot; nel nostro esempio). Lo schema di riferimento deve essere uno schema di contenuto.

Il contenuto dell&#39;elemento di destinazione arricchisce l&#39;elemento di collegamento, ovvero l&#39;elemento **`<chapter>`** nello schema di esempio:

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>La **stringa di calcolo** del collegamento viene presentata dall&#39;attributo **computeString**.

Nel modulo di input, il controllo di modifica del collegamento è dichiarato come segue:

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

L&#39;icona **[!UICONTROL Magnifier]** consente di aprire il modulo di modifica dell&#39;elemento collegato.

#### Raccolta di collegamenti {#link-collection}

Per compilare una raccolta di collegamenti, aggiungere l&#39;attributo **unbound=&quot;true&quot;** alla definizione dell&#39;elemento di collegamento nello schema dati:

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

Il contenuto dell&#39;elemento di destinazione arricchisce ogni elemento di raccolta:

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

Nel modulo di input, il controllo elenco è dichiarato come segue:

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

Per visualizzare la **stringa di calcolo** degli elementi di destinazione, viene visualizzata una colonna predefinita.

### Collegamenti alle tabelle esterne {#links-to-external-tables}

Un collegamento a una tabella esterna viene dichiarato nello schema dati come segue:

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

La definizione del collegamento viene compilata su un **collegamento** di tipo **`<element>`** e l&#39;attributo **target** fa riferimento allo schema di destinazione (&quot;nms:destinatario&quot; nel nostro esempio).

Per convenzione, i collegamenti devono essere dichiarati dall&#39;elemento principale dello schema di dati.

La **stringa di calcolo** e la chiave dell&#39;elemento di destinazione arricchiscono gli attributi **`<name>-id`** e **`<name>-cs`** sull&#39;elemento principale.

Nel nostro esempio, il collegamento è popolato nello schema &quot;cus:book&quot;, il contenuto dei dati del collegamento è contenuto negli attributi &quot;mainContact-id&quot; e &quot;mainContact-cs&quot;:

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

Il controllo per la modifica dei collegamenti è dichiarato come segue:

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

È possibile limitare la scelta degli elementi di destinazione aggiungendo l&#39;elemento **`<sysfilter>`** tramite la definizione del collegamento nel modulo di input:

```
<input xpath="mainContact">
  <!-- Filter the selection of the link on the Adobe domain -->
  <sysFilter>
    <condition expr="@domain =  'adobe.com '"/>
  </sysFilter>
</input>
```

>[!NOTE]
>
>Questa limitazione si applica anche ai collegamenti di contenuto.

#### Raccolta di collegamenti {#link-collection-1}

La definizione della raccolta è identica alla definizione di un elenco sugli elementi della raccolta:

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

Nel modulo di input, il controllo elenco è dichiarato come segue:

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>L’elenco è modificabile e consente di selezionare il collegamento da un controllo di tipo &quot;link&quot; illustrato sopra.

Il contenuto dell&#39;elemento di destinazione arricchisce ogni elemento di raccolta nel documento di output:

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### Aggregazione dei collegamenti {#link-aggregation}

Il contenuto di ciascun collegamento a cui si fa riferimento è limitato alla chiave interna e alla **stringa di calcolo** dell&#39;elemento di destinazione.

Uno script JavaScript viene utilizzato per arricchire il contenuto dei collegamenti tramite query SOAP.

**Esempio**: Aggiungendo il nome del destinatario al collegamento &quot;mainContact&quot; e i collegamenti della raccolta &quot;contact&quot;:

```
// Update <mainContact> link
var mainContactId = content.@['mainContact-id']
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+mainContactId}/>
      </where>
    </queryDef>)

var recipient = query.ExecuteQuery()
content.mainContact.@lastName = recipient.@lastName

// Update <contact> link collection
for each(var contact in content.contact)
{
  var contactId = contact.@['recipient-id']
  var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+contactId}/>
      </where>
    </queryDef>
  )
  
  var recipient = query.ExecuteQuery()
  contact.@lastName = recipient.@lastName
}
```

Il risultato ottenuto dopo l&#39;esecuzione dello script:

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

Il contenuto del codice JavaScript viene aggiunto tramite la cartella **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** e deve essere popolato nel modello di pubblicazione per ogni trasformazione.

![](assets/d_ncs_content_link5.png)

