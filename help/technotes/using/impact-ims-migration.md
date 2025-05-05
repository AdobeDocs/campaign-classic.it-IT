---
title: Aggiornare l’interfaccia di Campaign dopo la migrazione IMS
description: Scopri come attivare gli impatti dell’interfaccia di Adobe Identity Management System Migration
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# Aggiornare l’interfaccia di Campaign dopo la migrazione IMS {#impact-ims-migration}

Dopo che [hai eseguito la migrazione degli operatori tecnici di Campaign a Developer Console](ims-migration.md) e che [hai eseguito la transizione a IMS per l&#39;autenticazione dell&#39;utente finale](migrate-users-to-ims.md), l&#39;ultimo passaggio consiste nell&#39;abilitare le restrizioni dell&#39;interfaccia utente e dell&#39;API per rimuovere le opzioni e le funzionalità specifiche dell&#39;autenticazione nativa. Questo aggiornamento è disponibile a partire da Campaign v7.4.1.

## Abilita restrizioni IMS {#ims-restrictions}

Per completare la migrazione ad Adobe Identify Management System (IMS), è necessario bloccare la creazione di nuovi utenti nativi, l’accesso degli utenti nativi e l’accesso API per gli operatori nativi. L’ambiente viene quindi protetto e standardizzato.

In qualità di utente del Cloud Service gestito/in hosting, contatta l’Adobe per abilitare questa restrizione e i relativi aggiornamenti nell’interfaccia utente del prodotto.

In qualità di utente on-premise/ibrido, segui questi passaggi:

1. Passare alla sezione `<imsConfig>` del file di configurazione dell&#39;istanza.
1. Per abilitare le restrizioni dell&#39;interfaccia utente, aggiornare l&#39;opzione `nonIMSOperatorMgmtInClientConsoleRestricted`, all&#39;interno dell&#39;elemento `nonIMSOperatorMgmtInClientConsole`, a `true`, come indicato di seguito:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Per abilitare le restrizioni API, aggiornare l&#39;opzione `disableAPI`, all&#39;interno dell&#39;elemento `nonIMSAuthnAPI`, a `true`, come indicato di seguito:

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

Alcuni operatori possono connettersi ad Adobe Campaign con un’autenticazione nativa. Questi operatori tecnici sono abilitati per impostazione predefinita e non devono essere modificati. Per consentire questa eccezione, per impostazione predefinita questi operatori tecnici vengono aggiunti all’elenco Consentiti. L&#39;elenco è disponibile nella sezione `<imsConfig>` del file di configurazione dell&#39;istanza, nell&#39;opzione `allowOperator` all&#39;interno dell&#39;elemento `nonIMSAuthnAPI`.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

Se è necessario aggiungere un operatore al inserisco nell&#39;elenco Consentiti di, aggiungere un nuovo elemento `allowOperator` con il nome dell&#39;operatore. Ad esempio, se desideri aggiungere un nuovo operatore con il nome `test`, aggiorna questa sezione come segue:

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## Impatti nell’interfaccia utente {#ims-impacts}

Una volta completata la migrazione e applicate le restrizioni come descritto di seguito, le seguenti modifiche vengono applicate al prodotto e alla relativa interfaccia utente.

### Gestione degli operatori {#manage-admin}

Non è più possibile creare, modificare, aggiornare o eliminare operatori con autenticazione nativa dalla console client.

Di conseguenza, queste azioni sono state disabilitate nella console client.

L’amministrazione degli operatori è centralizzata in Adobe Admin Console e le seguenti attività ora sono gestite esclusivamente tramite questa console. Scopri come creare utenti e assegnare autorizzazioni nella [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Opzioni non disponibili {#unavailable-migration}

Dopo la migrazione, le seguenti attività non sono più disponibili nella console client:

* Utilizza l&#39;opzione [Unisci righe selezionate](../../platform/using/updating-data.md#merge-data) per unire gli operatori.

* Aggiorna i seguenti campi per gli operatori:
   * Nome
   * Password
   * Etichetta
   * E-mail

* [Reimpostare la password di Campaign](../../production/using/lost-password.md)

* Modifica l&#39;origine XML degli operatori

* Operatori duplicati.


>[!MORELIKETHIS]
>
>* [Migrazione degli utenti finali a IMS](migrate-users-to-ims.md)
>* [Migrazione degli operatori tecnici alla console Adobe Developer](ims-migration.md)
>* [Note sulla versione più recente di Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Che cos&#39;è Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}
