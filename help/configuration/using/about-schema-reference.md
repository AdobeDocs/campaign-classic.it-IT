---
product: campaign
title: Informazioni sul riferimento a uno schema in Adobe Campaign Classic
description: Scopri come configurare gli schemi di estensione per estendere il modello dati concettuale del database Adobe Campaign Classic.
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 7%

---

# Informazioni sulla documentazione sugli schemi{#about-schema-reference}

Questo capitolo descrive come configurare gli schemi di estensione per estendere il modello dati concettuale del database Adobe Campaign.

Per una migliore comprensione delle tabelle integrate di Campaign e della loro interazione, fai riferimento al [modello dati Campaign Classic](https://helpx.adobe.com/it/campaign/kb/acc-datamodel.html).

La struttura fisica e logica dei dati trasferiti nell’applicazione è descritta in XML. Obbedisce a una grammatica specifica di Adobe Campaign, denominata **schema**.

Uno schema è un documento XML associato a una tabella di database. Definisce la struttura dati e descrive la definizione SQL della tabella:

* Nome della tabella
* Campi
* Indici
* Collegamenti ad altre tabelle

Descrive inoltre la struttura XML utilizzata per memorizzare i dati:

* Elementi e attributi
* Gerarchia degli elementi
* Tipi di elementi e attributi
* Valori predefiniti
* Etichette, descrizioni e altre proprietà.

Gli schemi consentono di definire un’entità nel database. Esiste uno schema per ogni entità.

L’illustrazione seguente mostra la posizione degli schemi nel sistema dati Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintassi degli schemi {#syntax-of-schemas}

L&#39;elemento principale dello schema è **`<srcschema>`**. Contiene i sottoelementi **`<element>`** e **`<attribute>`** .

Il primo sottoelemento **`<element>`** coincide con il livello principale dell’entità.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>L&#39;elemento principale dell&#39;entità ha lo stesso nome dello schema.

![](assets/s_ncs_configuration_schema_and_entity.png)

I tag **`<element>`** definiscono i nomi degli elementi di entità. **`<attribute>`** i tag dello schema definiscono i nomi degli attributi nei  **`<element>`** tag a cui sono stati collegati.

## Identificazione di uno schema {#identification-of-a-schema}

Uno schema di dati è identificato dal nome e dallo spazio dei nomi corrispondente.

Uno spazio dei nomi consente di raggruppare un set di schemi per area di interesse. Ad esempio, lo spazio dei nomi **cus** viene utilizzato per la configurazione specifica del cliente (**clienti**).

La chiave di identificazione di uno schema è una stringa creata utilizzando lo spazio dei nomi e il nome separati da due punti; ad esempio: **cus:recipient**.

>[!IMPORTANT]
>
>Il nome dello spazio dei nomi deve essere conciso e deve contenere solo caratteri autorizzati in conformità alle regole di denominazione XML.
>
>Gli identificatori non devono iniziare con caratteri numerici.
>
>I seguenti namespace sono riservati per le descrizioni delle entità di sistema necessarie per il funzionamento dell’applicazione Adobe Campaign e non devono essere utilizzati: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm&lt;a1 3/>,** xxl **.**

