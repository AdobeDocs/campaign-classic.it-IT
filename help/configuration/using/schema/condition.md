---
product: campaign
title: 'Elementi e attributi dello schema: elemento condizione'
description: elemento condizione
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
TQID: https://experienceleague.adobe.com/Jx8bLCt1UEqAZDm0cSuexx25js-e5xTsvkeSMzVCUHw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 95
ht-degree: 5%

---

# elemento condizione {#condition--element}


## Modello di contenuto {#content-model-2}

condizione:==VUOTO

## Attributi {#attributes-2}

* @boolOperator (stringa)
* @enabledIf (stringa)
* @expr (stringa)

## Padri {#parents-2}

`<sysfilter>`

## Elementi secondari {#children-2}

Nessuno

## Descrizione {#description-2}

Questo elemento ti consente di definire una condizione di filtro.

## Uso e contesto di utilizzo {#use-and-context-of-use-2}

Un elemento `<sysfiler>` può contenere diverse condizioni di filtro.

## Descrizione attributo {#attribute-description-2}

* **boolOperator (stringa)**: se più di `<conditions>` sono definiti nello stesso elemento `<sysfilter>`, questo attributo consente di combinarli. Per impostazione predefinita, il collegamento logico è tra `<condition>` elementi ed è &quot;AND&quot;. L’attributo &quot;@boolOperator&quot; consente di combinare collegamenti di tipo &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (stringa)**: test di attivazione condizione.
* **expr (stringa)**: espressione XTK.

## Esempi {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
