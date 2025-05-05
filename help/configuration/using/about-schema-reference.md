---
product: campaign
title: Introduzione agli schemi in Adobe Campaign
description: Scopri come lavorare con gli schemi ed estendere il modello concettuale dei dati del database Adobe Campaign
feature: Schema Extension
role: Data Engineer, Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 1%

---

# Introduzione agli schemi {#about-schema-reference}

## Che cos’è uno schema {#what-is-a-schema}

Questo capitolo descrive come configurare gli schemi di estensione per estendere il modello dati concettuale del database di Adobe Campaign.

Per una migliore comprensione di Campaign tabelle incorporate e della loro interazione, fare riferimento al [modello](about-data-model.md) di dati Campaign Classic.

In Adobe Campaign, la struttura fisica e logica dei dati trasportati nel applicazione è descritta in XML. Uno **schema** è un documento XML associato a una tabella di database. Definisce la struttura dei dati e descrive la definizione SQL della tabella:

* Nome della tabella
* Campi
* Indici
* Collegamenti con altre tabelle

Descrive inoltre la struttura XML utilizzata per memorizzare i dati:

* Elementi e attributi
* Gerarchia di elementi
* Tipi di elementi e attributi
* Valori predefiniti
* Etichette, descrizioni e altre proprietà.

Gli schemi consentono di definire un&#39;entità nel database. Esiste uno schema per ogni entità.

Nella figura seguente viene illustrata la posizione degli schemi nel sistema di dati Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintassi degli schemi {#syntax-of-schemas}

L&#39;elemento principale dello schema è **`<srcschema>`**. Contiene gli **`<element>`** e **`<attribute>`** sottoelementi.

Il primo sottoelemento **`<element>`** coincide con la radice dell&#39;entità.

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
>L’elemento principale dell’entità ha lo stesso nome dello schema.

![](assets/s_ncs_configuration_schema_and_entity.png)

I tag **`<element>`** definiscono i nomi degli elementi di entità. **`<attribute>`** tag dello schema definiscono i nomi degli attributi nei tag **`<element>`** a cui sono stati collegati.

## Identificazione di uno schema {#identification-of-a-schema}

Uno schema di dati è identificato dal suo nome e dal suo spazio dei nomi.

Uno spazio nomi consente di raggruppare un insieme di schemi per area di interesse. Ad esempio, lo **spazio dei nomi cus** viene utilizzato per la configurazione specifica del cliente (**clienti**).

La chiave di identificazione di uno schema è una stringa creata utilizzando lo spazio dei nomi e il nome separati da due punti; Ad esempio: **cus:recipient**.

>[!IMPORTANT]
>
>* Il nome dello spazio dei nomi deve essere conciso e deve contenere solo caratteri autorizzati in conformità con le regole di denominazione XML.
>
>* Gli identificatori non devono iniziare con caratteri numerici.
>
>* I seguenti namespace sono riservati alle descrizioni delle entità di sistema necessarie per il funzionamento del applicazione Adobe Campaign e non devono essere utilizzati: xtk, nl **,** nms **, ncm**, **&#x200B;**&#x200B;temp **,** ncl **,** crm **,** xxl **.**&#x200B;**&#x200B;**
>
