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
source-wordcount: '210'
ht-degree: 3%

---


# `<join>` element  {#join--element}

## Modello di contenuto {#content-model-7}

join:==EMPTY

## Attributi {#attributes-7}

* @dstFilterExpr (stringa)
* @xpath-dst (stringa)
* @xpath-src (stringa)

## Genitori {#parents-7}

`<element>`

## Bambini {#children-7}

None

## Descrizione {#description-7}

Consente di definire i campi che creano un join tra tabelle SQL.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use-5}

Un elemento `<join>` può essere utilizzato solo se l&#39;elemento `<element>` principale è di tipo &#39;link&#39;. Ciò significa che l&#39;elemento padre deve avere dichiarato l&#39;attributo &quot;@type=link&quot;.

Non è necessario specificare il nome e lo spazio dei nomi della tabella remota nell&#39;elemento `<join>`. Devono essere specificati nella `<element>` padre.

Per convenzione, i collegamenti sono definiti alla fine dello schema.

Se l&#39;elemento `<join>` non viene specificato quando l&#39;elemento del tipo di collegamento è definito, il collegamento viene posizionato automaticamente sulle chiavi primarie di entrambe le tabelle.

## Descrizione attributo {#attribute-description-7}

* **dstFilterExpr (stringa)**: questo attributo consente di limitare il numero di valori idonei nella tabella remota.
* **xpath-dst (stringa)**: questo attributo riceve un attributo Xpath (@name attributo della tabella remota).
* **xpath-src (stringa)**: questo attributo riceve un attributo Xpath (@name nello schema corrente).

## Esempi {#examples-6}

Collegamento tra il campo &#39;email&#39; della tabella corrente e il campo &quot;@anima-id&quot; della tabella remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Collegamento filtrato alla tabella &quot;cus:Country&quot; in base al contenuto del campo &quot;@country&quot; che deve contenere il valore &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
