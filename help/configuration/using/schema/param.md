---
solution: Campaign Classic
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 6%

---


# `<param>` element  {#param--element}

## Modello di contenuto {#content-model-12}

param:==help

## Attributi {#attributes-12}

* @_operation (stringa)
* @desc (stringa)
* @enum (stringa)
* @inout (stringa)
* @label (stringa)
* @localizable (stringa)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (stringa)

## Genitori {#parents-12}

`<parameters>`

## Bambini {#children-12}

`<help>`

## Descrizione {#description-12}

Questo elemento consente di definire un parametro per richiamare un metodo SOAP.

## Descrizione attributo {#attribute-description-12}

* **desc (stringa)**: descrizione relativa all’ `<param>` elemento.
* **inout (stringa)**: questo attributo definisce se il parametro si trova o meno all&#39;input (in) o all&#39;output (out) della chiamata SOAP. Se questo attributo non è specificato, il parametro predefinito è input (&quot;@inout=in&quot;).
* **label (stringa)**:  `<param>` label
* **localizzabile (stringa)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **name (MNTOKEN)**: nome interno del  `<param>`
* **type (stringa)**: questo attributo definisce il tipo di  `<param>` elemento

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

## Esempi {#examples-9}

Definizione dell&#39;impostazione &quot;serviceName&quot; in entrata del tipo di stringa di caratteri:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
