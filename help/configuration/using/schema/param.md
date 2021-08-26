---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 6%

---

# elemento param {#param--element}

![](../../../assets/v7-only.svg)

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

Questo elemento ti consente di definire un parametro per la chiamata a un metodo SOAP.

## Descrizione attributo {#attribute-description-12}

* **desc (stringa)**: descrizione che riguarda l’ `<param>` elemento.
* **inout (stringa)**: questo attributo definisce se il parametro si trova o meno all’input (in) o all’output (out) della chiamata SOAP. Se questo attributo non è specificato, il parametro predefinito è input (&quot;@inout=in&quot;).
* **etichetta (stringa)**:  `<param>` etichetta
* **localizzabile (stringa)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **nome (MNTOKEN)**: nome interno  `<param>`
* **tipo (stringa)**: questo attributo definisce il tipo di  `<param>` elemento

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
   * collegamento
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * primarykey
   * short
   * string
   * orario
   * timespan
   * uuid

## Esempi {#examples-9}

Definizione dell&#39;impostazione in entrata &quot;serviceName&quot; del tipo di stringa di caratteri:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
