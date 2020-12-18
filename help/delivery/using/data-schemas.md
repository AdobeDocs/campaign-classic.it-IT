---
solution: Campaign Classic
product: campaign
title: Schemi di dati
description: Schemi di dati
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---


# Schemi di dati{#data-schemas}

Di seguito sono riportati alcuni principi generali relativi all’utilizzo degli schemi di dati in  Adobe Campaign.

Per ulteriori informazioni sulla creazione e la configurazione di schemi di dati in  Adobe Campaign, consultare [questa sezione](../../configuration/using/about-schema-edition.md).

## Struttura dello schema {#schema-structure}

Il documento XML di uno schema dati deve contenere gli attributi **`<srcschema>`** root con gli attributi **name** e **namespace** per compilare il nome dello schema e il relativo spazio dei nomi.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Il punto di ingresso dello schema è il suo elemento principale. È facile da identificare perché ha lo stesso nome dello schema e dovrebbe essere l&#39;elemento secondario dell&#39;elemento principale. La descrizione del contenuto inizia con questo elemento.

In uno schema di gestione del contenuto, l&#39;elemento principale è rappresentato dalla seguente riga:

```
<element name="book" template="ncm:content" xmlChildren="true">
```

L&#39;attributo **template** immesso nell&#39;elemento principale consente di estendere lo schema con proprietà generiche a tutte le definizioni di contenuto come nome, data di creazione, autore, stringa associata, ecc.

Tali proprietà sono descritte nello schema **ncm:content**.

>[!NOTE]
>
>La presenza dell&#39;attributo **xmlChildren** indica che la struttura dati immessa tramite l&#39;elemento principale è memorizzata in un documento XML dell&#39;istanza di contenuto.

>[!CAUTION]
>
>Durante la creazione di un nuovo schema o durante un&#39;estensione dello schema, è necessario mantenere lo stesso valore di sequenza della chiave primaria (@pkSequence) per l&#39;intero schema.

## Tipi di dati {#data-types}

Esempio di uno schema di gestione del contenuto con i tipi compilati:

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## Properties {#properties}

È possibile utilizzare diverse proprietà per arricchire gli elementi **`<element>`** e **`<attribute>`** dello schema di dati.

Le proprietà principali utilizzate nella gestione dei contenuti sono le seguenti:

* **label**: breve descrizione,
* **desc**: descrizione lunga,
* **predefinito**: espressione che restituisce un valore predefinito per la creazione di contenuto,
* **userEnum**: enumerazione gratuita per memorizzare e visualizzare i valori immessi in questo campo,
* **enum**: enumerazione fissa utilizzata quando l&#39;elenco dei valori possibili è noto in anticipo.

Di seguito è riportato lo schema di esempio con le proprietà compilate:

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## Elementi della raccolta {#collection-elements}

Una raccolta è un elenco di elementi con lo stesso nome e lo stesso livello gerarchico.

Nel nostro esempio, gli elementi **`<chapter>`** e **`<page>`** sono elementi della raccolta. L&#39;attributo **unbound** deve pertanto essere aggiunto alla definizione di questi elementi:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>La presenza dell&#39;attributo **ordered=&quot;true&quot;** consente di ordinare gli elementi della raccolta inseriti.

## Elemento che fa riferimento a {#element-referencing}

Il riferimento agli elementi viene utilizzato molto negli schemi di contenuto. Consente di fattorizzare la definizione di un elemento **`<element>`** in modo che possa essere utilizzato come riferimento su altri elementi con la stessa struttura.

L&#39;attributo **ref** sull&#39;elemento a cui fare riferimento deve essere completato con il percorso (XPath) dell&#39;elemento di riferimento.

**Esempio**: aggiunta di un&#39; **** appendice con la stessa struttura dell&#39; **`<chapter>`** elemento dello schema di esempio.

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

La struttura del capitolo viene spostata nell&#39;elemento con il nome &quot;sezione&quot; al di fuori dell&#39;elemento principale. Il capitolo e la sezione fanno riferimento all&#39;elemento &quot;sezione&quot;.

## Stringa di calcolo {#compute-string}

Una **stringa di calcolo** è un&#39;espressione XPath utilizzata per creare una stringa che rappresenta un&#39;istanza di contenuto.

Di seguito è riportato lo schema di esempio con la relativa **stringa di calcolo**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## Modifica degli schemi {#editing-schemas}

Il campo di modifica consente di inserire il contenuto XML dello schema di origine:

![](assets/d_ncs_integration_schema_edition.png)

Quando lo schema di origine viene salvato, la generazione dello schema esteso viene avviata automaticamente.

>[!NOTE]
>
>Il controllo di modifica **Name** consente di immettere la chiave dello schema, costituita dal nome e dallo spazio dei nomi. Gli attributi **name** e **namespace** dell&#39;elemento principale dello schema vengono aggiornati automaticamente nel campo di modifica XML dello schema.
