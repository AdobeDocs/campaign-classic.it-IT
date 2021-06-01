---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 7%

---

# elemento chiave {#keyfield--element}

## Modello dei contenuti {#content-model-9}

keyfield:==EMPTY

## Attributi {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Genitori {#parents-9}

`<key>`  ,  `<dbindex />`

## Figli {#children-9}

Nessuno

## Descrizione {#description-9}

Questo elemento definisce i campi da integrare in un indice o in una chiave.

## Descrizione dell&#39;attributo {#attribute-description-9}

* **xlink (MNTOKEN)**: consente di fare riferimento automaticamente a chiavi esterne definite nel join per una tabella di relazione (collegamento N-N).
* **xpath (MNTOKEN)**: definizione di un indice o di una chiave su un  `<attribute>`  elemento. Questo attributo riceve un percorso Xpath che definisce il percorso dell&#39;attributo dello schema che definisce la chiave o l&#39;indice.

## Esempi {#examples-}

Selezione del campo &quot;sName&quot; in un indice con un percorso Xpath su &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
