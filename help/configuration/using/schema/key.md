---
product: campaign
title: Elementi e attributi dello schema - elemento chiave
description: elemento chiave
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# elemento chiave {#key--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-8}

key:==keyfield

## Attributi {#attributes-8}

* @allowEmptyPart (booleano)
* @applyIf (stringa)
* @internal (booleano)
* @label (stringa)
* @name (MNTOKEN)
* @noDbIndex (booleano)

## Genitori {#parents-8}

`<element>`

## Bambini {#children-8}

`<keyfield>`

## Descrizione {#description-8}

Questo elemento ti consente di definire una chiave per identificare un record nella tabella.

Una tabella deve avere almeno una chiave.

## Uso e contesto di utilizzo {#use-and-context-of-use-6}

Come regola, le chiavi vengono dichiarate dopo l&#39;elemento principale dello schema e gli indici.

Una chiave è nota come composita se include diversi campi (ovvero diversi) `<keyfield>` bambini). Non utilizzare una chiave composita per definire una chiave primaria.

Se l&#39;elemento principale dello schema contiene l&#39;attributo &quot;@autopk=true&quot;, la chiave primaria è univoca. Possiamo avere una sola chiave primaria per schema.

I primi 1000 identificatori sono riservati; pertanto, se è necessario definire un intervallo di valori per le chiavi, inizia da 1000.

## Descrizione attributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: nel caso di una chiave composita, se questo attributo è attivato, la chiave viene considerata valida se almeno una delle chiavi non è vuota. In questo caso, il valore di nozione vuoto è &quot;0&quot; (booleano o per tutti i tipi di dati numerici). Per impostazione predefinita, è necessario immettere tutti i tasti che costituiscono una chiave composita.
* **applyIf (stringa)**: questo attributo consente di rendere la chiave facoltativa. Definisce la condizione in base alla quale verrà applicata la definizione della chiave. Questo attributo riceve un&#39;espressione XTK.
* **internal (booleano)**: se è attivato, questo attributo informa Adobe Campaign che la chiave è primaria.
* **label (stringa)**: etichetta della chiave.
* **nome (MNTOKEN)**: nome interno della chiave.
* **noDbIndex (booleano)**: se è attivato (noDbIndex=&quot;true&quot;), il campo corrispondente alla chiave non verrà indicizzato.

## Esempi {#examples-------}

Dichiarazione di una chiave composita che autorizza il campo &quot;@expr&quot; o &quot;alias&quot; a essere vuoto:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Dichiarazione di una chiave primaria sul campo &quot;Nome&quot; del tipo STRING in un `<srcschema>`  e la query SQL corrispondente:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
