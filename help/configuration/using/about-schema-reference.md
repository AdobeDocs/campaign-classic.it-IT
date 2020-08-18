---
title: Informazioni sul riferimento allo schema in Adobe Campaign Classic
description: Scoprite come configurare gli schemi di estensione per estendere il modello di dati concettuali del database Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d4ebaaf90d88cbec9a4d24d79eaf7c46890d933a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---


# Informazioni sul riferimento di schema{#about-schema-reference}

Questo capitolo descrive come configurare gli schemi di estensione per estendere il modello di dati concettuali del database Adobe Campaign .

Per una migliore comprensione delle tabelle integrate in Campaign e della loro interazione, fai riferimento al modello [dati](https://helpx.adobe.com/it/campaign/kb/acc-datamodel.html)Campaign Classic.

La struttura fisica e logica dei dati trasferiti nell’applicazione è descritta in XML. It obeys a grammar specific to Adobe Campaign, called a **schema**.

Uno schema è un documento XML associato a una tabella di database. Definisce la struttura dei dati e descrive la definizione SQL della tabella:

* Nome della tabella
* Campi
* Indici
* Collegamenti con altre tabelle

Inoltre, descrive la struttura XML utilizzata per memorizzare i dati:

* Elementi e attributi
* Gerarchia degli elementi
* Tipi di elementi e attributi
* Valori predefiniti
* Etichette, descrizioni e altre proprietà.

Gli schemi consentono di definire un&#39;entità nel database. Esiste uno schema per ogni entità.

L&#39;illustrazione seguente mostra la posizione degli schemi nel sistema dati Adobe Campaign :

![](assets/reference_schema_intro.png)

## Sintassi degli schemi {#syntax-of-schemas}

L&#39;elemento principale dello schema è **`<srcschema>`**. Contiene i **`<element>`** sottoelementi e i **`<attribute>`** sottoelementi.

Il primo **`<element>`** sottoelemento coincide con il livello principale dell&#39;entità.

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

I **`<element>`** tag definiscono i nomi degli elementi di entità. **`<attribute>`** i tag dello schema definiscono i nomi degli attributi nei **`<element>`** tag a cui sono stati collegati.

## Identificazione di uno schema {#identification-of-a-schema}

Uno schema dati è identificato dal nome e dallo spazio dei nomi.

Uno spazio dei nomi consente di raggruppare un set di schemi per area di interesse. Ad esempio, lo spazio dei nomi **focus** viene utilizzato per la configurazione specifica del cliente (**clienti**).

>[!IMPORTANT]
>
>Come standard, il nome dello spazio nomi deve essere conciso e deve contenere solo caratteri autorizzati in conformità alle regole di denominazione XML.
>
>Gli identificatori non devono iniziare con caratteri numerici.

Alcuni spazi dei nomi sono riservati alle descrizioni delle entità di sistema richieste per il funzionamento dell&#39;applicazione Adobe Campaign :

* **xtk**: per quanto riguarda i dati del sistema di piattaforma,
* **nl**: per quanto riguarda l&#39;uso generale della domanda,
* **nms**: riguardo alla consegna (destinatario, consegna, tracciamento, ecc.),
* **ncm**: per quanto riguarda la gestione dei contenuti,
* **temp**: riservato agli schemi temporanei.

La chiave di identificazione di uno schema è una stringa creata utilizzando lo spazio dei nomi e il nome separati da due punti; ad esempio: **cus:destinatario**.
