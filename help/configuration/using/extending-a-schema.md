---
title: Estensione di uno schema
seo-title: Estensione di uno schema
description: Estensione di uno schema
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 7%

---


# Estensione di uno schema{#extending-a-schema}

>[!IMPORTANT]
>
>Alcuni schemi predefiniti non devono essere estesi: principalmente quelle per le quali sono definite le seguenti impostazioni:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>I seguenti schemi non devono essere estesi: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, ******************************************ncm:publishing, nl:monitoraggio, nms:calendario, nms:remoteTracking,  nmsAgentRules:userxtk:builder, xtk:connection, xtk:dbInit, xtk:funcList, xtk:fusion, xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext, xtk:session, xtk:sqlSchema, stringhe**************xtk:xtk:.
>Questo elenco non è esaustivo.

Esistono due metodi per estendere uno schema esistente:

1. Modifica diretta dello schema di origine.
1. Creazione di un altro schema con lo stesso nome, ma con uno spazio nomi diverso. Il vantaggio è che è possibile estendere una tabella senza dover modificare lo schema originale.

   L&#39;elemento principale dello schema deve contenere l&#39;attributo **extendedSchema** con il nome dello schema da estendere come valore.

   Uno schema di estensione non ha uno schema specifico: lo schema generato dallo schema di origine sarà compilato con i campi dello schema di estensione.

   >[!IMPORTANT]
   >
   >Non è consentito modificare gli schemi predefiniti dell&#39;applicazione, ma il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento degli aggiornamenti futuri dell&#39;applicazione. Ciò può causare malfunzionamenti nell&#39;uso di  Adobe Campaign.

   **Esempio**: estensione dello schema **nms:destinatario** .

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Lo schema esteso **nms:destinatario** è compilato con il campo popolato nello schema di estensione:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   L&#39;attributo **differentSchemas** sull&#39;elemento principale dello schema fa riferimento alle dipendenze degli schemi di estensione.

   L&#39;attributo **membersTo** nel campo viene compilato nello schema in cui è dichiarato.

>[!IMPORTANT]
>
>Per tenere conto delle modifiche, è necessario rigenerare gli schemi. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Se le modifiche influiscono sulla struttura del database, è necessario eseguire un aggiornamento. Per ulteriori informazioni, consulta la sezione [Aggiornamento della struttura del database](../../configuration/using/updating-the-database-structure.md).

