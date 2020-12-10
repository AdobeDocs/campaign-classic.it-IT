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
source-wordcount: '42'
ht-degree: 19%

---


# `<sysfilter>` element  {#sysfilter--element}

## Modello di contenuto {#content-model-15}

sysFilter:==condition

## Attributi {#attributes-15}

None

## Genitori {#parents-15}

`<element>`

## Bambini {#children-15}

`<condition>`

## Descrizione {#description-15}

Questo elemento consente di definire un filtro.

## Descrizione attributo {#attribute-description-15}

Questo elemento non ha attributi.

## Esempi {#examples-12}

Definizione di un filtro con una condizione per l&#39;attributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
