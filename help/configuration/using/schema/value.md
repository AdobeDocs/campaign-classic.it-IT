---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 5%

---

# elemento value {#value--element}

## Modello dei contenuti {#content-model-16}

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

## Figli {#children-16}

`<help>`

## Descrizione {#description-16}

Questo elemento ti consente di definire i valori memorizzati in un’enumerazione.

## Descrizione dell&#39;attributo {#attribute-description-16}

* **applyIf (string)**: questo attributo consente di rendere facoltativo un valore di enumerazione. Riceve un&#39;espressione XTK.
* **desc (stringa)**: descrizione del valore di enumerazione.
* **enabledIf (stringa)**: condizione per attivare il valore di enumerazione.
* **img (stringa)**: immagine collegata all’enumerazione nel modulo &quot;namespace:image_name&quot;. L&#39;immagine deve essere importata sul server dell&#39;applicazione.
* **etichetta (stringa)**: etichetta del valore di enumerazione.
* **nome (stringa)**: nome interno del valore di enumerazione.
* **value (stringa)**: valore del valore di enumerazione. Il tipo di valore viene definito in base al tipo di enumerazione. Se l&#39;enumerazione è di tipo stringa di caratteri, può contenere solo valori di tipo stringa di caratteri.

## Esempi {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
