---
product: campaign
title: 'Elementi e attributi dello schema: elemento di enumerazione'
description: elemento enumerazione
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 6%

---

# elemento enumerazione {#enumeration--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-5}

enumerazione:==(valore help|)

## Attributi {#attributes-5}

* @basetype (stringa)
* @default (stringa)
* @desc (stringa)
* @label (stringa)
* @name (stringa)
* @template (stringa)

## Padri {#parents-5}

`<srcschema>`

## Elementi figli {#children-5}

* `<help>`
* `<value>`

## Descrizione {#description-5}

Questo elemento ci consente di definire un’enumerazione di valori. Un’enumerazione appartiene allo schema in cui è definita, ma è accessibile tramite un altro schema.

## Uso e contesto di utilizzo {#use-and-context-of-use-4}

Le enumerazioni vengono definite all’inizio di uno schema (prima che sia definito l’elemento principale).

## Descrizione attributo {#attribute-description-5}

* **basetype (string)**: tipo di valori memorizzati nell’enumerazione.

  Elenco dei tipi disponibili:

   * QUALSIASI
   * raccoglitore
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * doppio
   * enum
   * galleggiare
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percent
   * chiave primaria
   * corto
   * stringa
   * orario
   * intervallo di tempo
   * uuid

* **impostazione predefinita (stringa)**: valore predefinito. Il valore predefinito può anche essere uno dei valori definiti nell’enumerazione.
* **desc (stringa)**: descrizione enumerazione.
* **etichetta (stringa)**: etichetta di enumerazione.
* **nome (stringa)**: nome interno dell’enumerazione.
* **modello (stringa)**: questo attributo definisce un riferimento a un `<enumeration>` condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.

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

Definizione di un’enumerazione con un valore predefinito:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
