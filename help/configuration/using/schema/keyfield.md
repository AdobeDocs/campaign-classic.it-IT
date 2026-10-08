---
product: campaign
title: 'Elementi e attributi dello schema: elemento del campo chiave'
description: elemento keyfield
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: 'https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY'
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
source-wordcount: '106'
ht-degree: 6%
---
# elemento keyfield {#keyfield--element}


## Modello di contenuto {#content-model-9}

keyfield:==VUOTO

## Attributi {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Padri {#parents-9}

`<key>`  ,  `<dbindex />`

## Elementi secondari {#children-9}

Nessuno

## Descrizione {#description-9}

Questo elemento definisce i campi da integrare in un indice o in una chiave.

## Descrizione attributo {#attribute-description-9}

* **xlink (MNTOKEN)**: consente di fare riferimento automaticamente alle chiavi esterne definite nel join per una tabella di relazioni (collegamento N-N).
* **xpath (MNTOKEN)**: definizione di un indice o di una chiave in un elemento `<attribute>`. Questo attributo riceve un Xpath che definisce il percorso dell’attributo dello schema che definisce la chiave o l’indice.

## Esempi {#examples-}

Selezione del campo &quot;sName&quot; in un indice con un Xpath su &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
