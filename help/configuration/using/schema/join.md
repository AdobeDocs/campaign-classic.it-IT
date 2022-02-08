---
product: campaign
title: Elementi e attributi dello schema
description: elemento join
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 1%

---

# elemento join {#join--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-7}

join:==EMPTY

## Attributi {#attributes-7}

* @dstFilterExpr (stringa)
* @xpath-dst (stringa)
* @xpath-src (stringa)

## Genitori {#parents-7}

`<element>`

## Bambini {#children-7}

Nessuno

## Descrizione {#description-7}

Consente di definire i campi che creano un join tra tabelle SQL.

## Uso e contesto di utilizzo {#use-and-context-of-use-5}

A `<join>`  può essere utilizzato solo se l’elemento principale  `<element>`  è di tipo &quot;link&quot;. Ciò significa che l’attributo &quot;@type=link&quot; deve essere dichiarato per l’elemento padre.

Non è necessario specificare il nome e lo spazio dei nomi della tabella remota nel `<join>`  elemento. Devono essere specificati nella padre  `<element>`.

Per convenzione, i collegamenti sono definiti alla fine dello schema.

Se la `<join>` non viene specificato quando l’elemento del tipo di collegamento è definito, il collegamento verrà posizionato automaticamente sulle chiavi primarie di entrambe le tabelle.

## Descrizione attributo {#attribute-description-7}

* **dstFilterExpr (stringa)**: questo attributo consente di limitare il numero di valori idonei nella tabella remota.
* **xpath-dst (stringa)**: questo attributo riceve un attributo Xpath (@name attribute of the remote table).
* **xpath-src (stringa)**: questo attributo riceve un attributo Xpath (@name attribute nello schema corrente).

## Esempi {#examples-6}

Collegamento tra il campo &quot;email&quot; della tabella corrente e il campo &quot;@interlocuty-id&quot; della tabella remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Collegamento filtrato alla tabella &quot;cus:Country&quot; in base al contenuto del campo &quot;@country&quot; che deve contenere il valore &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
