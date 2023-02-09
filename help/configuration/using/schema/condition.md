---
product: campaign
title: Elementi e attributi dello schema - elemento condizione
description: elemento condizione
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

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

## Elementi figli {#children-2}

Nessuna

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
