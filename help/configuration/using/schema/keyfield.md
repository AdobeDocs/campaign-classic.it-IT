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
source-wordcount: '101'
ht-degree: 7%

---


# elemento keyfield {#keyfield--element}

## Modello di contenuto {#content-model-9}

keyfield:==EMPTY

## Attributi {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Genitori {#parents-9}

`<key>`  ,  `<dbindex />`

## Bambini {#children-9}

None

## Descrizione {#description-9}

Questo elemento definisce i campi da integrare in un indice o in una chiave.

## Descrizione attributo {#attribute-description-9}

* **xlink (MNTOKEN)**: consente di fare automaticamente riferimento a chiavi esterne definite nel join per una tabella di relazione (collegamento N-N).
* **xpath (MNTOKEN)**: definizione di un indice o di una chiave su un  `<attribute>`  elemento. Questo attributo riceve un Xpath che definisce il percorso dell&#39;attributo dello schema che definisce la chiave o l&#39;indice.

## Esempi {#examples-}

Selezione del campo &quot;sName&quot; in un indice con un percorso Xpath su &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
