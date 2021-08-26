---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 18%

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
