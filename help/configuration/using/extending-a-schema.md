---
product: campaign
title: Estendere uno schema
description: Scopri come estendere uno schema
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# Estendere uno schema{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>Alcuni schemi incorporati non devono essere estesi: principalmente quelle per le quali sono definite le seguenti impostazioni:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>I seguenti schemi non devono essere estesi: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:pubblicazione**, **nl:monitoraggio**, **nms:calendario**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connessioni**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusione**, **xtk: solo**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:stringhe**.
>Questo elenco non è esaustivo.

Esistono due metodi per estendere uno schema esistente:

1. Modifica diretta dello schema di origine.
1. Creazione di un altro schema con lo stesso nome ma con uno spazio dei nomi diverso. Il vantaggio è che è possibile estendere una tabella senza dover modificare lo schema originale.

   L&#39;elemento principale dello schema deve contenere **ExtendedSchema** attributo con il nome dello schema da estendere come valore.

   Uno schema di estensione non dispone di uno schema proprio: lo schema generato dallo schema di origine viene compilato con i campi dello schema di estensione.

   >[!IMPORTANT]
   >
   >Non è consentito modificare gli schemi incorporati dell&#39;applicazione, ma il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento degli aggiornamenti futuri dell’applicazione. Questo può causare malfunzionamenti nell’utilizzo di Adobe Campaign.

   **Esempio**: estensione del **nms:recipient** schema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   La **nms:recipient** lo schema esteso viene compilato con il campo popolato nello schema dell&#39;estensione:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   La **DependSchemas** l&#39;attributo sull&#39;elemento principale dello schema fa riferimento alle dipendenze negli schemi di estensione.

   La **ownedTo** l&#39;attributo sul campo viene compilato nello schema in cui è dichiarato.

>[!IMPORTANT]
>
>Per tenere conto delle modifiche, è necessario rigenerare gli schemi. Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/regenerating-schemas.md).\
>Se le modifiche influiscono sulla struttura del database, è necessario eseguire un aggiornamento. Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/updating-the-database-structure.md).
