---
product: campaign
title: Arricchimento del contenuto
description: Arricchimento del contenuto
feature: Data Management
exl-id: a4472a7c-a16b-4d10-a8ca-f74ca5f62de4
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# Arricchimento del contenuto{#enriching-content}

![](../../assets/common.svg)

Gli aggregati consentono di arricchire il contenuto con dati esterni. Questi dati provengono da query generiche o tabelle collegate.

## Query generiche {#generic-queries}

Le query vengono configurate tramite il modello di pubblicazione nel **[!UICONTROL Aggregator]** scheda .

I dati recuperati arricchiranno il documento di output XML tramite il relativo elemento principale.

Esempio di restituzione da una query sullo schema del destinatario (**nms:recipient**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

La **`<collection-recipient>`** rappresenta l’elemento di input del documento risultante da una query. I dati recuperati vengono restituiti sotto questo elemento; nel nostro esempio, un elenco di destinatari.

### Aggiunta di una query {#adding-a-query}

I parametri della query vengono modificati mediante una procedura guidata.

1. Nella prima pagina, specifica l’etichetta e lo schema contenente i dati da recuperare.

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >Campo di modifica **Percorso** viene utilizzato per rinominare l’elemento di output della query.

1. La pagina successiva ti consente di selezionare i dati da recuperare.

   ![](assets/d_ncs_content_query2.png)

1. La pagina successiva definisce la condizione del filtro.

   ![](assets/d_ncs_content_query3.png)

1. L’ultima pagina avvia un’anteprima dei dati restituiti dalla query.

   ![](assets/d_ncs_content_query4.png)

## Tabelle collegate {#linked-tables}

I collegamenti ti consentono di recuperare dati esterni collegati al contenuto.

Esistono due tipi di dati collegati:

* Collegamenti al contenuto: è la modalità di gestione del contenuto nativa. Il contenuto del collegamento viene integrato automaticamente nel documento di output XML.
* I collegamenti a tabelle esterne consentono di accedere a tutte le altre tabelle del database con il vincolo di recuperare i dati del collegamento selezionato con un aggregatore.

### Collegamento a uno schema di contenuto {#link-to-a-content-schema}

Un collegamento di contenuto viene dichiarato nello schema dati come segue:

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

La definizione del collegamento viene compilata su un **string**-type **`<element>`** e **expandSchemaTarget** l’attributo fa riferimento allo schema di destinazione (&quot;cus:capitolo&quot; nel nostro esempio). Lo schema a cui si fa riferimento deve essere uno schema di contenuto.

Il contenuto dell’elemento di destinazione arricchisce l’elemento di collegamento, ovvero **`<chapter>`** nel nostro schema di esempio:

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>La **Stringa di calcolo** del collegamento è presentato dal **computeString** attributo.

Nel modulo di input, il controllo di modifica del collegamento viene dichiarato come segue:

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

La **[!UICONTROL Magnifier]** consente di aprire il modulo di modifica dell’elemento collegato.

#### Raccolta collegamenti {#link-collection}

Per compilare una raccolta di collegamenti, aggiungi la variabile **unbound=&quot;true&quot;** alla definizione dell’elemento di collegamento nello schema dati:

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

Il contenuto dell’elemento di destinazione arricchisce ogni elemento di raccolta:

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

Per visualizzare la colonna **Stringa di calcolo** degli elementi oggetto di targeting.

### Collegamenti a tabelle esterne {#links-to-external-tables}

Nello schema dati viene dichiarato un collegamento a una tabella esterna come segue:

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

La definizione del collegamento viene compilata su un **collegamento**-type **`<element>`** e **target** l’attributo fa riferimento allo schema di destinazione (&quot;nms:recipient&quot; nel nostro esempio).

Per convenzione, i collegamenti devono essere dichiarati dall’elemento principale dello schema dati.

La **Stringa di calcolo** e la chiave dell’elemento di destinazione arricchisce il **`<name>-id`** e **`<name>-cs`** attributi sull&#39;elemento principale.

Nel nostro esempio, il collegamento è popolato nello schema &quot;cus:book&quot;, il contenuto dei dati del collegamento è contenuto negli attributi &quot;mainContact-id&quot; e &quot;mainContact-cs&quot;:

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

Il controllo della modifica del collegamento viene dichiarato come segue:

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

Puoi limitare la scelta degli elementi di destinazione aggiungendo il **`<sysfilter>`** tramite la definizione del collegamento nel modulo di input:

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
>Questa restrizione si applica anche ai collegamenti di contenuto.

#### Raccolta collegamenti {#link-collection-1}

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
>L’elenco è modificabile e consente di selezionare il collegamento da un controllo di tipo &quot;link&quot; presentato in precedenza.

Il contenuto dell’elemento di destinazione arricchisce ogni elemento di raccolta nel documento di output:

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### Aggregazione dei collegamenti {#link-aggregation}

Il contenuto di ogni collegamento a cui si fa riferimento è limitato alla chiave interna e alla **Stringa di calcolo** dell’elemento di destinazione.

Per arricchire il contenuto dei collegamenti tramite query SOAP viene utilizzato uno script JavaScript.

**Esempio**: Aggiunta del nome del destinatario al link &quot;mainContact&quot; e ai link della raccolta &quot;contact&quot;:

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

Il risultato ottenuto dopo l’esecuzione dello script:

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

Il contenuto del codice JavaScript viene aggiunto tramite il **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** devono essere compilati nel modello di pubblicazione per ogni trasformazione.

![](assets/d_ncs_content_link5.png)
