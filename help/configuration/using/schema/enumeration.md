---
product: campaign
title: Elementi e attributi dello schema - elemento di enumerazione
description: elemento di enumerazione
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 6%

---

# elemento di enumerazione {#enumeration--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-5}

enumerazione:==(help| valore)

## Attributi {#attributes-5}

* @basetype (stringa)
* @default (stringa)
* @desc (stringa)
* @label (stringa)
* @name (stringa)
* @template (stringa)

## Genitori {#parents-5}

`<srcschema>`

## Elementi figli {#children-5}

* `<help>`
* `<value>`

## Descrizione {#description-5}

Questo elemento ci consente di definire un’enumerazione di valori. Un&#39;enumerazione appartiene allo schema in cui è definita, ma è accessibile tramite un altro schema.

## Uso e contesto di utilizzo {#use-and-context-of-use-4}

Le enumerazioni sono definite all&#39;inizio di uno schema (prima che l&#39;elemento principale sia definito).

## Descrizione attributo {#attribute-description-5}

* **basetype (stringa)**: tipo dei valori memorizzati nell&#39;enumerazione.

   Elenco dei tipi disponibili:

   * QUALSIASI
   * bidone
   * macchia
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * primarykey
   * short
   * stringa
   * orario
   * timespan
   * uuid

* **default (string)**: Valore predefinito. Il valore predefinito può anche essere uno dei valori definiti nell&#39;enumerazione.
* **desc (stringa)**: descrizione dell&#39;enumerazione.
* **label (stringa)**: etichetta di enumerazione.
* **name (stringa)**: nome interno dell&#39;enumerazione.
* **template (stringa)**: questo attributo definisce un riferimento a un `<enumeration>` elemento condiviso da diversi schemi. La definizione viene copiata automaticamente nello schema corrente.

## Esempi {#examples-4}

Esempio di valori di enumerazione i cui valori sono memorizzati nel database:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definizione di un&#39;enumerazione con un valore predefinito:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
