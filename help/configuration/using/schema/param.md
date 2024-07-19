---
product: campaign
title: 'Elementi e attributi dello schema: elemento param'
description: elemento param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 9%

---

# elemento param {#param--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-12}

parametro:==guida

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

## Padri {#parents-12}

`<parameters>`

## Elementi figli {#children-12}

`<help>`

## Descrizione {#description-12}

Questo elemento ti consente di definire un parametro per la chiamata di un metodo SOAP.

## Descrizione attributo {#attribute-description-12}

* **desc (stringa)**: descrizione relativa all&#39;elemento `<param>`.
* **inout (stringa)**: questo attributo definisce se il parametro si trova o meno nell&#39;input (in) o nell&#39;output (out) della chiamata SOAP. Se questo attributo non è specificato, il parametro predefinito è input (&quot;@inout=in&quot;).
* **etichetta (stringa)**: `<param>` etichetta
* **localizzabile (stringa)**: se attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **nome (MNTOKEN)**: nome interno di `<param>`
* **tipo (stringa)**: questo attributo definisce il tipo dell&#39;elemento `<param>`

  Elenco dei tipi disponibili:

   * QUALSIASI
   * raccoglitore
   * blob
   * booleano
   * byte
   * CDATA
   * Data e ora
   * datetimetz
   * datetimenotz
   * data
   * DOMDocument
   * DOMElement
   * doppio
   * enum
   * mobile
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * chiave primaria
   * corto
   * stringa
   * ora
   * intervallo di tempo
   * uuid

## Esempi {#examples-9}

Definizione dell’impostazione in entrata &quot;serviceName&quot; del tipo di stringa di caratteri:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
