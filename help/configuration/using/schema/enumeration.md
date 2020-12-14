---
solution: Campaign Classic
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 5%

---


# elemento di enumerazione {#enumeration--element}

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

## Bambini {#children-5}

* `<help>`
* `<value>`

## Descrizione {#description-5}

Questo elemento consente di definire un&#39;enumerazione di valori. Un&#39;enumerazione appartiene allo schema in cui è definita, ma è accessibile tramite un altro schema.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use-4}

Le enumerazioni sono definite all&#39;inizio di uno schema (prima della definizione dell&#39;elemento principale).

## Descrizione attributo {#attribute-description-5}

* **basetype (stringa)**: tipo dei valori memorizzati nell&#39;enumerazione.

   Elenco dei tipi disponibili:

   * QUALSIASI
   * bin
   * blob
   * boolean
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
   * string
   * orario
   * periodo
   * uuid

* **default (string)**: Valore predefinito. Il valore predefinito può anche essere uno dei valori definiti nell&#39;enumerazione.
* **desc (stringa)**: descrizione dell&#39;enumerazione.
* **label (stringa)**: etichetta di enumerazione.
* **name (stringa)**: nome interno dell&#39;enumerazione.
* **template (stringa)**: questo attributo definisce un riferimento a un  `<enumeration>` elemento condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.

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
