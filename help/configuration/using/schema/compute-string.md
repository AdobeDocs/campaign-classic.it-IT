---
product: campaign
title: 'Elementi e attributi: elemento stringa di calcolo'
description: elemento stringa di calcolo
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# elemento stringa di calcolo {#compute-string--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-1}

stringa di calcolo:==EMPTY

## Attributi {#attributes-1}

@expr

## Padri {#parents-1}

`<element>`

## Elementi figli {#children-1}

Nessuna

## Descrizione {#description-1}

Il `<compute-string>` consente di generare una stringa basata su un’espressione XTK per visualizzare un’etichetta &quot;generata&quot; nell’interfaccia in base a diversi valori.

## Uso e contesto di utilizzo {#use-and-context-of-use-1}

In caso contrario `<compute-string>` è definito, un `<compute-string>` L&#39;elemento viene immesso per impostazione predefinita con i valori della chiave primaria nello schema.

## Descrizione attributo {#attribute-description-1}

* **expr (stringa)**: espressione XTK e/o Xpath

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
