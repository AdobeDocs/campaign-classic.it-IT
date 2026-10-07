---
product: campaign
title: 'Elementi e attributi dello schema: elemento di enumerazione'
description: elemento enumerazione
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
TQID: 'https://experienceleague.adobe.com/w8b-2HEtYRMOd9yHFLtvS0vS2tdLDzuIakLfrqImsGo'
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
source-wordcount: '198'
ht-degree: 11%
---
# elemento enumerazione {#enumeration--element}


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

## Elementi secondari {#children-5}

* `<help>`
* `<value>`

## Descrizione {#description-5}

Questo elemento ci consente di definire un’enumerazione di valori. Un’enumerazione appartiene allo schema in cui è definita, ma è accessibile tramite un altro schema.

## Uso e contesto di utilizzo {#use-and-context-of-use-4}

Le enumerazioni vengono definite all’inizio di uno schema (prima che sia definito l’elemento principale).

## Descrizione attributo {#attribute-description-5}

* **basetype (stringa)**: tipo dei valori memorizzati nell&#39;enumerazione.

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

* **default (stringa)**: valore predefinito. Il valore predefinito può anche essere uno dei valori definiti nell’enumerazione.
* **desc (stringa)**: descrizione enumerazione.
* **etichetta (stringa)**: etichetta di enumerazione.
* **nome (stringa)**: nome interno dell&#39;enumerazione.
* **modello (stringa)**: questo attributo definisce un riferimento a un elemento `<enumeration>` condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.

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
