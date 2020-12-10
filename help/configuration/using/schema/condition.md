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
source-wordcount: '92'
ht-degree: 8%

---


# `<condition>` element  {#condition--element}

## Modello di contenuto {#content-model-2}

condizione:==EMPTY

## Attributi {#attributes-2}

* @boolOperator (stringa)
* @enabledIf (stringa)
* @expr (stringa)

## Genitori {#parents-2}

`<sysfilter>`

## Bambini {#children-2}

None

## Descrizione {#description-2}

Questo elemento consente di definire una condizione di filtro.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use-2}

Un elemento `<sysfiler>` può contenere diverse condizioni di filtraggio.

## Descrizione attributo {#attribute-description-2}

* **boolOperator (stringa)**: se più  `<conditions>` sono definiti all&#39;interno dello stesso   `<sysfilter>` elemento, questo attributo consente di combinarli. Per impostazione predefinita, il collegamento logico è compreso tra `<condition>` elementi è &quot;AND&quot;. L&#39;attributo &quot;@boolOperator&quot; consente di combinare collegamenti di tipo &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (stringa)**: test di attivazione della condizione.
* **expr (stringa)**: un&#39;espressione XTK.

## Esempi {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
