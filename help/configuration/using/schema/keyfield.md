---
product: campaign
title: 'Elementi e attributi dello schema: elemento del campo chiave'
description: elemento keyfield
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# elemento keyfield {#keyfield--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-9}

keyfield:==VUOTO

## Attributi {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Padri {#parents-9}

`<key>`  ,  `<dbindex />`

## Elementi figli {#children-9}

Nessuno

## Descrizione {#description-9}

Questo elemento definisce i campi da integrare in un indice o in una chiave.

## Descrizione attributo {#attribute-description-9}

* **xlink (MNTOKEN)**: consente di fare riferimento automaticamente alle chiavi esterne definite nel join per una tabella di relazione (collegamento N-N).
* **xpath (MNTOKEN)**: definizione di un indice o di una chiave su un `<attribute>`  elemento. Questo attributo riceve un Xpath che definisce il percorso dell’attributo dello schema che definisce la chiave o l’indice.

## Esempi {#examples-}

Selezione del campo &quot;sName&quot; in un indice con un Xpath su &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
