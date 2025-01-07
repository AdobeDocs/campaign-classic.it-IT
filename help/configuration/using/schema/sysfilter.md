---
product: campaign
title: Elementi e attributi - elemento sysfilter
description: Elementi e attributi
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 11%

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
