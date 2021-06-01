---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---

# elemento stringa di calcolo {#compute-string--element}

## Modello dei contenuti {#content-model-1}

compute-string:==EMPTY

## Attributi {#attributes-1}

@expr

## Genitori {#parents-1}

`<element>`

## Figli {#children-1}

Nessuno

## Descrizione {#description-1}

L’elemento `<compute-string>` consente di generare una stringa basata su un’espressione XTK per visualizzare un’etichetta &quot;generata&quot; nell’interfaccia in base a diversi valori.

## Uso e contesto di utilizzo {#use-and-context-of-use-1}

Quando non viene definito alcun elemento `<compute-string>`, per impostazione predefinita viene inserito un elemento `<compute-string>` con i valori della chiave primaria nello schema.

## Descrizione dell&#39;attributo {#attribute-description-1}

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
