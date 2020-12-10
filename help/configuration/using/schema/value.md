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
source-wordcount: '146'
ht-degree: 5%

---


# `<value>` element  {#value--element}

## Modello di contenuto {#content-model-16}

value:==help

## Attributi {#attributes-16}

* @applyIf (stringa)
* @desc (stringa)
* @enabledIf (stringa)
* @img (stringa)
* @label (stringa)
* @name (stringa)
* @value (stringa)

## Genitori {#parents-16}

`<enumeration>`

## Bambini {#children-16}

`<help>`

## Descrizione {#description-16}

Questo elemento consente di definire i valori memorizzati in un&#39;enumerazione.

## Descrizione attributo {#attribute-description-16}

* **applyIf (stringa)**: questo attributo consente di rendere facoltativo un valore di enumerazione. Riceve un&#39;espressione XTK.
* **desc (stringa)**: descrizione del valore di enumerazione.
* **enabledIf (stringa)**: condizione per attivare il valore di enumerazione.
* **img (stringa)**: immagine collegata all&#39;enumerazione nel modulo &quot;namespace:image_name&quot;. L&#39;immagine deve essere importata nel server dell&#39;applicazione.
* **label (stringa)**: dell&#39;etichetta del valore di enumerazione.
* **name (stringa)**: nome interno del valore di enumerazione.
* **value (stringa)**: del valore di enumerazione. Il tipo di valore è definito in base al tipo di enumerazione. Se l&#39;enumerazione è di tipo stringa di caratteri, può contenere solo valori di tipo stringa di caratteri.

## Esempi {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
