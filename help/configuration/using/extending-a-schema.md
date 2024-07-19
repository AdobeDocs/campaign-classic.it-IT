---
product: campaign
title: Estendere uno schema
description: Scopri come estendere uno schema
role: Data Engineer, Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# Estendere uno schema{#extending-a-schema}

>[!IMPORTANT]
>
>Alcuni schemi integrati non devono essere estesi: principalmente quelli per i quali sono definite le seguenti impostazioni:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>I seguenti schemi non devono essere estesi: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, {16 8}nms:userAgentRules **,** xtk:builder **,** xtk:connections **,** xtk:dbInit **,** xtk:funcList **,** xtk:fusion **,** xtk: jst **,** xtk:navtree **,** xtk:query Def **,** xtk:resourceMenu **,** xtk:schema **,** xtk:scriptContext **,** xtk:session **,** xtk:sqlSchema **,** xtk:string **.**
>Questo elenco non è esaustivo.

Esistono due metodi per estendere uno schema esistente:

1. Modifica diretta dello schema di origine.
1. Creazione di un altro schema con lo stesso nome ma uno spazio dei nomi diverso. Il vantaggio è che è possibile estendere una tabella senza dover modificare lo schema originale.

   L&#39;elemento radice dello schema deve contenere l&#39;attributo **extendedSchema** con il nome dello schema da estendere come valore.

   Uno schema di estensione non dispone di un proprio schema: lo schema generato dallo schema di origine verrà compilato con i campi dello schema di estensione.

   >[!IMPORTANT]
   >
   >Non è consentito modificare gli schemi incorporati dell’applicazione, ma il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento di aggiornamenti futuri dell’applicazione. Questo può causare malfunzionamenti nell’utilizzo di Adobe Campaign.

   **Esempio**: estensione dello schema **nms:recipient**.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Lo schema esteso **nms:recipient** viene compilato con il campo popolato nello schema dell&#39;estensione:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   L&#39;attributo **dependSchemas** dell&#39;elemento principale dello schema fa riferimento alle dipendenze dagli schemi di estensione.

   L&#39;attributo **membersTo** del campo viene compilato nello schema in cui è dichiarato.

>[!IMPORTANT]
>
>Per tenere conto delle modifiche, è necessario rigenerare gli schemi. Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/regenerating-schemas.md).\
>Se le modifiche influiscono sulla struttura del database, devi eseguire un aggiornamento. Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/updating-the-database-structure.md).
