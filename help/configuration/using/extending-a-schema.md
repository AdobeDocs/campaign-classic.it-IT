---
solution: Campaign Classic
product: campaign
title: Estensione di uno schema
description: Scopri come estendere uno schema
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---


# Estensione di uno schema{#extending-a-schema}

>[!IMPORTANT]
>
>Alcuni schemi predefiniti non devono essere estesi: principalmente quelle per le quali sono definite le seguenti impostazioni:\
>**dataSource=&quot;file&quot;** e  **mappingType=&quot;xmlFile&quot;**.\
>I seguenti schemi non devono essere estesi: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, &lt;a10/ ncm:publishing **,** nl:monitoring **,** nms:Calendar **,** nms:remoteTracking **,** nms:userAgentRules&lt;a1 9/>, **xtk:builder**, **xtk:Connections**, **xtk:dbInit**, **xtk:funcList**, a28/>xtk:fusion **,** xtk: jst **,** xtk:navtree **,** xtk:queryDef **,** xtk:resourceMenu **,** xtk:schema&lt;a3 9/>, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.********
>Questo elenco non è esaustivo.

Esistono due metodi per estendere uno schema esistente:

1. Modifica diretta dello schema di origine.
1. Creazione di un altro schema con lo stesso nome, ma con uno spazio nomi diverso. Il vantaggio è che è possibile estendere una tabella senza dover modificare lo schema originale.

   L&#39;elemento principale dello schema deve contenere l&#39;attributo **extendedSchema** con il nome dello schema da estendere come valore.

   Uno schema di estensione non ha uno schema specifico: lo schema generato dallo schema di origine sarà compilato con i campi dello schema di estensione.

   >[!IMPORTANT]
   >
   >Non è consentito modificare gli schemi predefiniti dell&#39;applicazione, ma il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento degli aggiornamenti futuri dell&#39;applicazione. Ciò può causare malfunzionamenti nell&#39;uso di  Adobe Campaign.

   **Esempio**: estensione di  **nms:** targetSchema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Lo schema esteso **nms:Recipiente** è compilato con il campo popolato nello schema di estensione:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   L&#39;attributo **differentSchemas** nell&#39;elemento principale dello schema fa riferimento alle dipendenze negli schemi di estensione.

   L&#39;attributo **membersTo** del campo completa lo schema in cui è dichiarato.

>[!IMPORTANT]
>
>Per tenere conto delle modifiche, è necessario rigenerare gli schemi. Per ulteriori informazioni, consultare la sezione [Rigenerazione degli schemi](../../configuration/using/regenerating-schemas.md).\
>Se le modifiche influiscono sulla struttura del database, è necessario eseguire un aggiornamento. Per ulteriori informazioni, consulta la sezione [Aggiornamento della struttura del database](../../configuration/using/updating-the-database-structure.md).

