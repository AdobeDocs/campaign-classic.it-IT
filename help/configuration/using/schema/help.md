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
source-wordcount: '46'
ht-degree: 17%

---


# `<help>` element  {#help--element}

## Modello di contenuto {#content-model-6}

help:==EMPTY

## Attributi {#attributes-6}

None

## Genitori {#parents-6}

`<srcschema>`  ,   `<element>`   ,    `<attribute>`    ,     `<enumeration>`     ,      `<value>`      ,      `<param />`,       `<method />`

## Bambini {#children-6}

None

## Descrizione {#description-6}

Questo elemento consente di descrivere un elemento `<element>` o `<attribute>`   element. Può contenere solo testo ed è memorizzato in XML nel database.

## Descrizione attributo {#attribute-description-6}

Questo elemento non ha attributi.

## Esempi {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
