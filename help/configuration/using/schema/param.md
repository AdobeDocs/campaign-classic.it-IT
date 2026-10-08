---
product: campaign
title: 'Elementi e attributi dello schema: elemento param'
description: elemento param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
TQID: 'https://experienceleague.adobe.com/fiMkJtGU90FP-G6BJhTnIrgBJ39uIJaakqKD49EhXS0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 12%
---
# elemento param {#param--element}


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

## Elementi secondari {#children-12}

`<help>`

## Descrizione {#description-12}

Questo elemento ti consente di definire un parametro per la chiamata a un metodo SOAP.

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
  * collegamento
  * lungo
  * promemoria
  * MNTOKEN
  * percentuale
  * chiave primaria
  * breve
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
