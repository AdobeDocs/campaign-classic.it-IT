---
product: campaign
title: Elementi e attributi
description: elemento compute-string
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 6%

---

# elemento compute-string {#compute-string--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-1}

compute-string:==EMPTY

## Attributi {#attributes-1}

@expr

## Genitori {#parents-1}

`<element>`

## Bambini {#children-1}

Nessuno

## Descrizione {#description-1}

La `<compute-string>` consente di generare una stringa basata su un’espressione XTK per visualizzare un’etichetta &quot;generata&quot; nell’interfaccia in base a diversi valori.

## Uso e contesto di utilizzo {#use-and-context-of-use-1}

Quando no `<compute-string>` è definito come `<compute-string>` l’elemento viene immesso per impostazione predefinita con i valori della chiave primaria nello schema.

## Descrizione attributo {#attribute-description-1}

* **expr (stringa)**: Espressione XTK e/o Xpath

## Esempi {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Risultato della stringa calcolata su un destinatario: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
