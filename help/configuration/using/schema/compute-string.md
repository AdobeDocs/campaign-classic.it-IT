---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

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

L’elemento `<compute-string>` consente di generare una stringa basata su un’espressione XTK per visualizzare un’etichetta &quot;generata&quot; nell’interfaccia in base a diversi valori.

## Uso e contesto di utilizzo {#use-and-context-of-use-1}

Quando non viene definito alcun elemento `<compute-string>`, per impostazione predefinita viene inserito un elemento `<compute-string>` con i valori della chiave primaria nello schema.

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
