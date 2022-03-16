---
product: campaign
title: Elementi e attributi - elemento sysfilter
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 13%

---

# elemento sysfilter {#sysfilter--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-15}

sysFilter:==condition

## Attributi {#attributes-15}

Nessuno

## Genitori {#parents-15}

`<element>`

## Bambini {#children-15}

`<condition>`

## Descrizione {#description-15}

Questo elemento ti consente di definire un filtro.

## Descrizione attributo {#attribute-description-15}

Questo elemento non ha attributi.

## Esempi {#examples-12}

Definizione di un filtro con una condizione sull&#39;attributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
