---
product: campaign
title: Estensione di uno schema
description: Scopri come estendere uno schema
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---

# Estensione di uno schema{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>Alcuni schemi incorporati non devono essere estesi: principalmente quelle per le quali sono definite le seguenti impostazioni:\
>**dataSource=&quot;file&quot;** e  **mappingType=&quot;xmlFile&quot;**.\
>I seguenti schemi non devono essere estesi: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules&lt;a11 9/>,** xtk:builder **,** xtk:connections **,** xtk:dbInit **,** xtk:funcList **, a28/>xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema&lt;a3 9/>,** xtk:scriptContext **,** xtk:session **,** xtk:sqlSchema **,** xtk:strings **.******
>Questo elenco non è esaustivo.

Esistono due metodi per estendere uno schema esistente:

1. Modifica diretta dello schema di origine.
1. Creazione di un altro schema con lo stesso nome ma con uno spazio dei nomi diverso. Il vantaggio è che è possibile estendere una tabella senza dover modificare lo schema originale.

   L&#39;elemento principale dello schema deve contenere l&#39;attributo **ExtendedSchema** con il nome dello schema da estendere come valore.

   Uno schema di estensione non dispone di uno schema proprio: lo schema generato dallo schema di origine viene compilato con i campi dello schema di estensione.

   >[!IMPORTANT]
   >
   >Non è consentito modificare gli schemi incorporati dell&#39;applicazione, ma il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento degli aggiornamenti futuri dell’applicazione. Questo può causare malfunzionamenti nell’utilizzo di Adobe Campaign.

   **Esempio**: estensione di  **nms:** recipientschema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Lo schema esteso **nms:recipient** viene compilato con il campo popolato nello schema di estensione:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   L&#39;attributo **varySchemas** sull&#39;elemento principale dello schema fa riferimento alle dipendenze sugli schemi di estensione.

   L&#39;attributo **ownedTo** sul campo viene compilato nello schema in cui è dichiarato.

>[!IMPORTANT]
>
>Per tenere conto delle modifiche, è necessario rigenerare gli schemi. Per ulteriori informazioni, consulta la sezione [Rigenerazione degli schemi](../../configuration/using/regenerating-schemas.md) .\
>Se le modifiche influiscono sulla struttura del database, è necessario eseguire un aggiornamento. Per ulteriori informazioni, consulta la sezione [Aggiornamento della struttura del database](../../configuration/using/updating-the-database-structure.md).
