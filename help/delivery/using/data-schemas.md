---
product: campaign
title: Utilizzare gli schemi di dati in Campaign
description: Scopri come utilizzare gli schemi di dati in Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Data Model
role: User, Developer, Data Engineer
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---

# Utilizzare gli schemi di dati in Campaign{#data-schemas}

Di seguito sono riportati alcuni principi generali relativi all’utilizzo degli schemi di dati in Adobe Campaign.

Per ulteriori informazioni sulla creazione e la configurazione di schemi di dati in Adobe Campaign, consulta [questa sezione](../../configuration/using/about-schema-edition.md).

## Struttura dello schema {#schema-structure}

Il documento XML di uno schema dati deve contenere **`<srcschema>`** elemento principale con **nome** e **namespace** attributi per popolare il nome dello schema e il relativo spazio dei nomi.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Il punto di ingresso dello schema è il suo elemento principale. È facile da identificare perché ha lo stesso nome dello schema e dovrebbe essere l’elemento secondario dell’elemento principale. La descrizione del contenuto inizia con questo elemento.

In uno schema di gestione dei contenuti, l’elemento principale è rappresentato dalla seguente riga:

```
<element name="book" template="ncm:content" xmlChildren="true">
```

Il **modello** l’attributo immesso nell’elemento principale ti consente di estendere lo schema con proprietà generiche a tutte le definizioni di contenuto come nome, data di creazione, autore, stringa associata e così via.

Queste proprietà sono descritte nella **ncm:contenuto** schema.

>[!NOTE]
>
>La presenza del **xmlChildren** L&#39;attributo indica che la struttura dati immessa tramite l&#39;elemento principale viene memorizzata in un documento XML dell&#39;istanza di contenuto.

>[!CAUTION]
>
>Quando crei un nuovo schema o durante un’estensione dello schema, devi mantenere lo stesso valore di sequenza di chiave primaria (@pkSequence) per l’intero schema.

## Tipi di dati {#data-types}

Di seguito è riportato un esempio di schema di gestione dei contenuti con i tipi compilati:

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

È possibile utilizzare diverse proprietà per arricchire **`<element>`** e **`<attribute>`** elementi dello schema dati.

Le proprietà principali utilizzate nella gestione dei contenuti sono le seguenti:

* **etichetta**: breve descrizione,
* **desc**: descrizione lunga,
* **predefinito**: espressione che restituisce un valore predefinito al momento della creazione del contenuto,
* **userEnum**: enumerazione gratuita per memorizzare e visualizzare i valori immessi tramite questo campo,
* **enum**: enumerazione fissa utilizzata quando l’elenco dei valori possibili è noto in anticipo.

Di seguito è riportato uno schema di esempio con le proprietà compilate:

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

Nel nostro esempio, il **`<chapter>`** e **`<page>`** Gli elementi sono elementi di raccolta. Il **non associato** deve pertanto essere aggiunto alla definizione di questi elementi:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>La presenza del **ordered=&quot;true&quot;** Questo attributo consente di ordinare gli elementi di raccolta inseriti.

## Elemento con riferimento a {#element-referencing}

Il riferimento agli elementi viene utilizzato in larga misura negli schemi di contenuto. Consente di raggruppare la definizione di un **`<element>`** in modo che sia possibile farvi riferimento su altri elementi con la stessa struttura.

Il **ref** L&#39;attributo dell&#39;elemento a cui fare riferimento deve essere completato con il percorso (XPath) dell&#39;elemento di riferimento.

**Esempio**: aggiunta di un **Appendice** sezione con la stessa struttura della sezione **`<chapter>`** del nostro schema di esempio.

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

La struttura del capitolo viene spostata nell’elemento con il nome &quot;section&quot; al di fuori dell’elemento principale. Il capitolo e la sezione fanno riferimento all’elemento &quot;section&quot;.

## Elemento “compute-string” {#compute-string}

A **Stringa di calcolo** è un&#39;espressione XPath utilizzata per creare una stringa che rappresenta un&#39;istanza di contenuto.

Di seguito è riportato uno schema di esempio con i relativi **Stringa di calcolo**:

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

Quando lo schema di origine viene salvato, la generazione estesa dello schema viene avviata automaticamente.

>[!NOTE]
>
>Il **Nome** edit control consente di immettere la chiave dello schema, costituita dal nome e dallo spazio dei nomi. Il **nome** e **namespace** gli attributi dell&#39;elemento principale dello schema vengono aggiornati automaticamente nel campo di modifica XML dello schema.
