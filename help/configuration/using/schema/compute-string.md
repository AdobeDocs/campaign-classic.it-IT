---
solution: Campaign Classic
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---


# elemento stringa di calcolo {#compute-string--element}

## Modello di contenuto {#content-model-1}

compute-string:==EMPTY

## Attributi {#attributes-1}

@expr

## Genitori {#parents-1}

`<element>`

## Bambini {#children-1}

None

## Descrizione {#description-1}

L&#39;elemento `<compute-string>` consente di generare una stringa basata su un&#39;espressione XTK per visualizzare un&#39;etichetta &quot;predefinita&quot; nell&#39;interfaccia in base a diversi valori.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use-1}

Se non è definito alcun elemento `<compute-string>`, per impostazione predefinita viene immesso un elemento `<compute-string>` con i valori della chiave primaria nello schema.

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
