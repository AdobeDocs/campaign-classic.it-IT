---
product: campaign
title: 'Elementi e attributi: elemento stringa di calcolo'
description: elemento stringa di calcolo
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
TQID: 'https://experienceleague.adobe.com/vLSA9oDdBg-0sElc6QlusY-YviNyRU8Fq6yXRrFrN1g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%
---
# elemento stringa di calcolo {#compute-string--element}


## Modello di contenuto {#content-model-1}

stringa di calcolo:==EMPTY

## Attributi {#attributes-1}

@expr

## Padri {#parents-1}

`<element>`

## Elementi secondari {#children-1}

Nessuno

## Descrizione {#description-1}

L&#39;elemento `<compute-string>` consente di generare una stringa basata su un&#39;espressione XTK per visualizzare un&#39;etichetta &quot;generata&quot; nell&#39;interfaccia basata su più valori.

## Uso e contesto di utilizzo {#use-and-context-of-use-1}

Se non è definito alcun elemento `<compute-string>`, per impostazione predefinita viene immesso un elemento `<compute-string>` con i valori della chiave primaria nello schema.

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
