---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 8%

---

# elemento condizione {#condition--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-2}

condizione:==EMPTY

## Attributi {#attributes-2}

* @boolOperator (stringa)
* @enabledIf (stringa)
* @expr (stringa)

## Genitori {#parents-2}

`<sysfilter>`

## Bambini {#children-2}

Nessuno

## Descrizione {#description-2}

Questo elemento ti consente di definire una condizione di filtro.

## Uso e contesto di utilizzo {#use-and-context-of-use-2}

Uno `<sysfiler>`  L’elemento può contenere diverse condizioni di filtro.

## Descrizione attributo {#attribute-description-2}

* **boolOperator (stringa)**: se diversi `<conditions>` sono definite all&#39;interno della stessa  `<sysfilter>` questo attributo consente di combinarle. Per impostazione predefinita, il collegamento logico è compreso tra `<condition>` element è &quot;AND&quot;. L’attributo &quot;@boolOperator&quot; consente di combinare collegamenti di tipo &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (stringa)**: test di attivazione della condizione.
* **expr (stringa)**: un&#39;espressione XTK.

## Esempi {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
