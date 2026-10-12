---
product: campaign
title: Comprendere la struttura dello schema in Adobe Campaign
description: Struttura dello schema
feature: Custom Resources
role: Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
TQID: 'https://experienceleague.adobe.com/dFZ38qRKX-4vTEYS9GosS5TdW-XhnoIq8ckbjnNEJmo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 6%
---
# Comprendere la struttura dello schema {#schema-structure}

Questa pagina elenca il modo in cui i tipi di dati di Adobe Campaign vengono associati ai tipi di dati di ciascun sistema di gestione del database.

Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8. Per ulteriori informazioni sulla struttura dello schema, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}.

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}

## Mappatura dei tipi di dati Adobe Campaign/DBMS {#mapping-the-types-of-adobe-campaign-dbms-data}

La tabella seguente elenca le mappature per i tipi di dati generati da Adobe Campaign per i diversi sistemi di gestione del database.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Stringa<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMERO(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMERO(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Breve<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMERO(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Doppio<br /> </td> 
   <td> PRECISIONE DOPPIA<br /> </td> 
   <td> MOBILE<br /> </td> 
  </tr> 
  <tr> 
   <td> Lungo<br /> </td> 
   <td> INTERO<br /> </td> 
   <td> NUMERO(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMERO(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Data<br /> </td> 
   <td> DATA<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Ora<br /> </td> 
   <td> ORA<br /> </td> 
   <td> MOBILE<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> MARCA TEMPORALE<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> MARCA TEMPORALE<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Intervallo di tempo<br /> </td> 
   <td> PRECISIONE DOPPIA<br /> </td> 
   <td> MOBILE<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TESTO<br /> </td> 
   <td> CLOB (NCLOB se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Ulteriori informazioni

Per ulteriori informazioni, consulta i seguenti collegamenti:

* [Introduzione agli schemi](about-schema-reference.md)
* [Mappatura del database](database-mapping.md)
* [Gestione dei collegamenti](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (documentazione di Campaign v8)
* [Gestione delle chiavi](database-keys.md)
