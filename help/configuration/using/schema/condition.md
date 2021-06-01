---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 8%

---

# elemento condizione {#condition--element}

## Modello dei contenuti {#content-model-2}

condizione:==EMPTY

## Attributi {#attributes-2}

* @boolOperator (stringa)
* @enabledIf (stringa)
* @expr (stringa)

## Genitori {#parents-2}

`<sysfilter>`

## Figli {#children-2}

Nessuno

## Descrizione {#description-2}

Questo elemento ti consente di definire una condizione di filtro.

## Uso e contesto di utilizzo {#use-and-context-of-use-2}

Un elemento `<sysfiler>` può contenere diverse condizioni di filtro.

## Descrizione dell&#39;attributo {#attribute-description-2}

* **boolOperator (stringa)**: se più  `<conditions>` sono definiti all’interno dello stesso   `<sysfilter>` elemento, questo attributo consente di combinarli. Per impostazione predefinita, il collegamento logico è tra gli elementi `<condition>` è &quot;AND&quot;. L’attributo &quot;@boolOperator&quot; consente di combinare collegamenti di tipo &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (stringa)**: test di attivazione della condizione.
* **expr (stringa)**: un&#39;espressione XTK.

## Esempi {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
