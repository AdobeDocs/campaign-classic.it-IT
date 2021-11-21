---
product: campaign
title: Schemi di dati
description: Schemi di dati
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# Schemi di dati{#data-schemas}

![](../../assets/common.svg)

Di seguito sono riportati alcuni principi generali relativi all’utilizzo degli schemi di dati in Adobe Campaign.

Per ulteriori informazioni sulla creazione e la configurazione di schemi di dati in Adobe Campaign, consulta [questa sezione](../../configuration/using/about-schema-edition.md).

## Struttura dello schema {#schema-structure}

Il documento XML di uno schema dati deve contenere **`<srcschema>`** elemento principale con **name** e **namespace** attributi per popolare il nome dello schema e il relativo spazio dei nomi.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Il punto di ingresso dello schema è il suo elemento principale. È facile da identificare perché ha lo stesso nome dello schema e dovrebbe essere l&#39;elemento secondario dell&#39;elemento principale. La descrizione del contenuto inizia con questo elemento.

In uno schema di gestione del contenuto, l’elemento principale è rappresentato dalla seguente riga:

```
<element name="book" template="ncm:content" xmlChildren="true">
```

La **template** l’attributo inserito nell’elemento principale consente di estendere lo schema con proprietà generiche a tutte le definizioni di contenuto, come nome, data di creazione, autore, stringa associata, ecc.

Queste proprietà sono descritte nella sezione **ncm:content** schema.

>[!NOTE]
>
>La presenza di **xmlChildren** l&#39;attributo indica che la struttura dati immessa tramite l&#39;elemento principale è memorizzata in un documento XML dell&#39;istanza di contenuto.

>[!CAUTION]
>
>Durante la creazione di un nuovo schema o durante un&#39;estensione dello schema, è necessario mantenere lo stesso valore di sequenza della chiave primaria (@pkSequence) per l&#39;intero schema.

## Tipi di dati {#data-types}

Ecco un esempio di uno schema di gestione dei contenuti con i tipi compilati:

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

Varie proprietà possono essere utilizzate per arricchire il **`<element>`** e **`<attribute>`** elementi dello schema dati.

Le proprietà principali utilizzate nella gestione dei contenuti sono le seguenti:

* **etichetta**: breve descrizione,
* **desc**: descrizione lunga,
* **default**: espressione che restituisce un valore predefinito nella creazione del contenuto,
* **userEnum**: enumerazione gratuita per memorizzare e visualizzare i valori immessi tramite questo campo,
* **enum**: enumerazione fissa utilizzata quando l&#39;elenco dei valori possibili è noto in anticipo.

Ecco il nostro schema di esempio con le proprietà inserite:

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

## Elementi di raccolta {#collection-elements}

Una raccolta è un elenco di elementi con lo stesso nome e lo stesso livello gerarchico.

Nel nostro esempio, il **`<chapter>`** e **`<page>`** Gli elementi sono elementi di raccolta. La **non legato** L&#39;attributo deve pertanto essere aggiunto alla definizione di questi elementi:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>La presenza di **ordered=&quot;true&quot;** L&#39;attributo ti consente di ordinare gli elementi della raccolta inseriti.

## Riferimento a un elemento {#element-referencing}

Il riferimento agli elementi viene utilizzato molto negli schemi di contenuto. Consente di fattorizzare la definizione di un **`<element>`** in modo che possa essere fatto riferimento ad altri elementi con la stessa struttura.

La **ref** l&#39;attributo sull&#39;elemento a cui si fa riferimento deve essere completato con il percorso (XPath) dell&#39;elemento di riferimento.

**Esempio**: aggiunta di un **Appendice** con la stessa struttura **`<chapter>`** elemento dello schema di esempio.

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

La struttura del capitolo viene spostata nell’elemento con il nome &quot;sezione&quot; al di fuori dell’elemento principale. Il capitolo e la sezione fanno riferimento all&#39;elemento &quot;sezione&quot;.

## Elemento “compute-string” {#compute-string}

A **Stringa di calcolo** è un&#39;espressione XPath utilizzata per creare una stringa che rappresenta un&#39;istanza di contenuto.

Ecco il nostro esempio di schema con i relativi **Stringa di calcolo**:

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
>La **Nome** il controllo di modifica consente di immettere la chiave dello schema, costituita dal nome e dallo spazio dei nomi. La **name** e **namespace** gli attributi dell&#39;elemento principale dello schema vengono aggiornati automaticamente nel campo di modifica XML dello schema.
