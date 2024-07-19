---
product: campaign
title: 'Elementi e attributi dello schema: elemento chiave'
description: elemento chiave
feature: Schema Extension
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 1%

---

# elemento chiave {#key--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-8}

chiave:==campo chiave

## Attributi {#attributes-8}

* @allowEmptyPart (boolean)
* @applicableIf (stringa)
* @internal (boolean)
* @label (stringa)
* @name (MNTOKEN)
* @noDbIndex (boolean)

## Padri {#parents-8}

`<element>`

## Elementi figli {#children-8}

`<keyfield>`

## Descrizione {#description-8}

Questo elemento ti consente di definire una chiave per identificare un record nella tabella.

Una tabella deve avere almeno una chiave.

## Uso e contesto di utilizzo {#use-and-context-of-use-6}

Di regola, le chiavi vengono dichiarate dopo l’elemento principale dello schema e gli indici.

Una chiave è nota come composita se include diversi campi (ad esempio diversi `<keyfield>` elementi secondari). Non utilizzare una chiave composita per definire una chiave primaria.

Se l’elemento principale dello schema contiene l’attributo &quot;@autopk=true&quot;, la chiave primaria è univoca. È possibile disporre di una sola chiave primaria per schema.

I primi 1000 identificatori sono riservati, quindi se è necessario definire un intervallo di valori per le chiavi, inizia da 1000.

## Descrizione attributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: nel caso di una chiave composita, se questo attributo è attivato, la chiave viene considerata valida se almeno una delle chiavi non è vuota. In questo caso, il valore della nozione vuoto è &quot;0&quot; (booleano o per tutti i tipi di dati numerici). Per impostazione predefinita, è necessario immettere tutti i tasti che compongono una chiave composita.
* **applyIf (stringa)**: questo attributo ti consente di rendere facoltativa la chiave. Definisce la condizione in base alla quale verrà applicata la definizione di chiave. Questo attributo riceve un&#39;espressione XTK.
* **internal (booleano)**: se è attivato, questo attributo consente ad Adobe Campaign di sapere che la chiave è primaria.
* **etichetta (stringa)**: etichetta della chiave.
* **nome (MNTOKEN)**: nome interno della chiave.
* **noDbIndex (booleano)**: se attivato (noDbIndex=&quot;true&quot;), il campo corrispondente alla chiave non verrà indicizzato.

## Esempi {#examples-------}

Dichiarazione di una chiave composita che autorizza il campo &quot;@expr&quot; o &quot;alias&quot; a essere vuoto:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Dichiarazione di una chiave primaria nel campo &quot;Name&quot; di tipo STRING in un `<srcschema>` e query SQL corrispondente:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
