---
product: campaign
title: Elementi e attributi - elemento valore
description: Elementi e attributi
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
TQID: https://experienceleague.adobe.com/rGaA--VHVGxCBHX5SgZUQQ9AwMgOTYWqMYGpYWU4-WY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 4%

---

# elemento valore {#value--element}


## Modello di contenuto {#content-model-16}

valore:==guida

## Attributi {#attributes-16}

* @applicableIf (stringa)
* @desc (stringa)
* @enabledIf (stringa)
* @img (stringa)
* @label (stringa)
* @name (stringa)
* @value (stringa)

## Padri {#parents-16}

`<enumeration>`

## Elementi secondari {#children-16}

`<help>`

## Descrizione {#description-16}

Questo elemento ti consente di definire i valori memorizzati in un’enumerazione.

## Descrizione attributo {#attribute-description-16}

* **applicabileIf (stringa)**: questo attributo consente di rendere facoltativo un valore di enumerazione. Riceve un’espressione XTK.
* **desc (stringa)**: descrizione del valore di enumerazione.
* **enabledIf (stringa)**: condizione per attivare il valore di enumerazione.
* **img (stringa)**: immagine collegata all&#39;enumerazione nel modulo &quot;namespace:image_name&quot;. L&#39;immagine deve essere importata nel server applicazioni.
* **etichetta (stringa)**: etichetta del valore di enumerazione.
* **nome (stringa)**: nome interno del valore di enumerazione.
* **valore (stringa)**: valore dell&#39;enumerazione. Il tipo di valore è definito in base al tipo di enumerazione. Se l’enumerazione è di tipo stringa di caratteri, può contenere solo valori di tipo stringa di caratteri.

## Esempi {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
