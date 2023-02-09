---
product: campaign
title: Elementi e attributi dello schema - elemento del campo chiave
description: elemento chiave
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# elemento chiave {#keyfield--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-9}

keyfield:==EMPTY

## Attributi {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Genitori {#parents-9}

`<key>`  ,  `<dbindex />`

## Elementi figli {#children-9}

Nessuna

## Descrizione {#description-9}

Questo elemento definisce i campi da integrare in un indice o in una chiave.

## Descrizione attributo {#attribute-description-9}

* **xlink (MNTOKEN)**: consente di fare riferimento automaticamente a chiavi esterne definite nel join per una tabella di relazione (collegamento N-N).
* **xpath (MNTOKEN)**: definizione di un indice o di una chiave su un `<attribute>`  elemento. Questo attributo riceve un percorso Xpath che definisce il percorso dell&#39;attributo dello schema che definisce la chiave o l&#39;indice.

## Esempi {#examples-}

Selezione del campo &quot;sName&quot; in un indice con un percorso Xpath su &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
