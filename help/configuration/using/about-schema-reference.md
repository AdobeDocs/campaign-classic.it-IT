---
product: campaign
title: Informazioni sul riferimento di schema in Adobe Campaign Classic
description: Scopri come configurare gli schemi di estensione per estendere il modello dati concettuale del database di Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 9%

---

# Informazioni sulla documentazione sugli schemi{#about-schema-reference}

Questo capitolo descrive come configurare gli schemi di estensione per estendere il modello dati concettuale del database di Adobe Campaign.

Per informazioni sulle tabelle integrate di Campaign e sulla loro interazione, consulta [Modello dati Campaign Classic](https://helpx.adobe.com/it/campaign/kb/acc-datamodel.html).

La struttura fisica e logica dei dati trasferiti nell’applicazione è descritta in XML. Obbedisce a una grammatica specifica di Adobe Campaign, denominata **schema**.

Uno schema è un documento XML associato a una tabella di database. Definisce la struttura dati e descrive la definizione SQL della tabella:

* Nome della tabella
* Campi
* Indici
* Collegamenti con altre tabelle

Descrive inoltre la struttura XML utilizzata per memorizzare i dati:

* Elementi e attributi
* Gerarchia di elementi
* Tipi di elementi e attributi
* Valori predefiniti
* Etichette, descrizioni e altre proprietà

Gli schemi consentono di definire un’entità nel database. Esiste uno schema per ogni entità.

L’illustrazione seguente mostra la posizione degli schemi nel sistema dati di Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintassi degli schemi {#syntax-of-schemas}

L’elemento principale dello schema è **`<srcschema>`**. Contiene il **`<element>`** e **`<attribute>`** sottoelementi.

Il primo **`<element>`** sottoelemento coincide con la radice dell’entità.

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

Il **`<element>`** I tag definiscono i nomi degli elementi di entità. **`<attribute>`** I tag dello schema definiscono i nomi degli attributi nel **`<element>`** i tag a cui sono stati collegati.

## Identificazione di uno schema {#identification-of-a-schema}

Uno schema di dati è identificato dal nome e dallo spazio dei nomi.

Uno spazio dei nomi consente di raggruppare un set di schemi per area di interesse. Ad esempio, il **cus** lo spazio dei nomi viene utilizzato per la configurazione specifica del cliente (**clienti**).

La chiave di identificazione di uno schema è una stringa creata utilizzando lo spazio dei nomi e il nome separato da due punti, ad esempio: **cus:recipient**.

>[!IMPORTANT]
>
>Il nome dello spazio dei nomi deve essere conciso e deve contenere solo caratteri autorizzati in conformità alle regole di denominazione XML.
>
>Gli identificatori non devono iniziare con caratteri numerici.
>
>I seguenti spazi dei nomi sono riservati per le descrizioni delle entità di sistema necessarie per il funzionamento dell’applicazione Adobe Campaign e non devono essere utilizzati: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.

