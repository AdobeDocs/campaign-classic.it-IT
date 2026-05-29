---
product: campaign
title: Elementi e attributi - elemento sysfilter
description: Elementi e attributi
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
TQID: https://experienceleague.adobe.com/hjsD-JSGBPnwyj1IsLDo-tUy-63apy0-6kT9vngaaQk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 45
ht-degree: 17%

---

# elemento sysfilter {#sysfilter--element}


## Modello di contenuto {#content-model-15}

sysFilter:==condizione

## Attributi {#attributes-15}

Nessuno

## Padri {#parents-15}

`<element>`

## Elementi secondari {#children-15}

`<condition>`

## Descrizione {#description-15}

Questo elemento ti consente di definire un filtro.

## Descrizione attributo {#attribute-description-15}

Questo elemento non ha attributi.

## Esempi {#examples-12}

Definizione di un filtro con una condizione sull’attributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
