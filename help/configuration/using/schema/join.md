---
product: campaign
title: 'Elementi e attributi dello schema: elemento join'
description: elemento join
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
TQID: 'https://experienceleague.adobe.com/qze6zOBr1DxBIClCPPjIAZ2BeS7mMwnTFuoMw2-d9Cw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 2%
---
# elemento join {#join--element}


## Modello di contenuto {#content-model-7}

join:==EMPTY

## Attributi {#attributes-7}

* @dstFilterExpr (stringa)
* @xpath-dst (stringa)
* @xpath-src (stringa)

## Padri {#parents-7}

`<element>`

## Elementi secondari {#children-7}

Nessuno

## Descrizione {#description-7}

Consente di definire i campi che creano un join tra tabelle SQL.

## Uso e contesto di utilizzo {#use-and-context-of-use-5}

Un elemento `<join>` può essere utilizzato solo se l&#39;elemento padre `<element>` è di tipo &#39;link&#39;. Ciò significa che l’elemento padre deve avere l’attributo &quot;@type=link&quot; dichiarato.

Non è necessario specificare nome e spazio dei nomi della tabella remota nell&#39;elemento `<join>`. È necessario specificarli nell&#39;elemento padre `<element>`.

Per convenzione, i collegamenti sono definiti alla fine dello schema.

Se l&#39;elemento `<join>` non viene specificato quando viene definito l&#39;elemento del tipo di collegamento, il collegamento verrà inserito automaticamente nelle chiavi primarie di entrambe le tabelle.

## Descrizione attributo {#attribute-description-7}

* **dstFilterExpr (stringa)**: questo attributo consente di limitare il numero di valori idonei nella tabella remota.
* **xpath-dst (stringa)**: questo attributo riceve un Xpath (attributo @name della tabella remota).
* **xpath-src (stringa)**: questo attributo riceve un Xpath (attributo @name nello schema corrente).

## Esempi {#examples-6}

Collegamento tra il campo &quot;e-mail&quot; della tabella corrente e il campo &quot;@compagny-id&quot; della tabella remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Collegamento filtrato verso la tabella &quot;cus:Country&quot; in base al contenuto del campo &quot;@country&quot; che deve contenere il valore &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
