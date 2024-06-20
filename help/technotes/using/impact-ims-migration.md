---
title: Aggiornare l’interfaccia di Campaign dopo la migrazione IMS
description: Scopri come attivare gli impatti dell’interfaccia di Adobe Identity Management System Migration
source-git-commit: ab1bb91bdbc9961b4f3f0feba7cfd354b02b6511
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# Aggiornare l’interfaccia di Campaign dopo la migrazione IMS {#impact-ims-migration}

Una volta che [migrazione degli operatori tecnici di Campaign a Console sviluppatori](ims-migration.md) e [è stata effettuata la transizione a IMS per l’autenticazione dell’utente finale](migrate-users-to-ims.md), l’ultimo passaggio consiste nell’abilitare l’interfaccia utente e le restrizioni API per rimuovere le opzioni e le funzionalità specifiche dell’autenticazione nativa. Questo aggiornamento è disponibile a partire da Campaign v7.4.1.

## Abilita restrizioni IMS {#ims-restrictions}

Per completare la migrazione ad Adobe Identify Management System (IMS), è necessario bloccare la creazione di nuovi utenti nativi, l’accesso degli utenti nativi e l’accesso API per gli operatori nativi. L’ambiente viene quindi protetto e standardizzato.

In qualità di utente del Cloud Service gestito/in hosting, contatta l’Adobe per abilitare questa restrizione e i relativi aggiornamenti nell’interfaccia utente del prodotto.

In qualità di utente on-premise/ibrido, segui questi passaggi:

1. Accedi a `<imsConfig>` del file di configurazione dell’istanza.
1. Per abilitare le restrizioni dell’interfaccia utente, aggiorna il `nonIMSOperatorMgmtInClientConsoleRestricted` all&#39;interno del `nonIMSOperatorMgmtInClientConsole` elemento, a `true`, come segue:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Per abilitare le restrizioni API, aggiorna la `disableAPI` all&#39;interno del `nonIMSAuthnAPI` elemento, a `true`, come segue:

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

Alcuni operatori possono connettersi ad Adobe Campaign con un’autenticazione nativa. Questi operatori tecnici sono abilitati per impostazione predefinita e non devono essere modificati. Per consentire questa eccezione, per impostazione predefinita questi operatori tecnici vengono aggiunti all’elenco Consentiti. Puoi trovare questo elenco in `<imsConfig>` del file di configurazione dell’istanza, nella sezione `allowOperator` all&#39;interno del `nonIMSAuthnAPI` elemento.

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

Se devi aggiungere un operatore al inserisco nell&#39;elenco Consentiti di, aggiungi un nuovo `allowOperator` con il nome dell&#39;operatore. Ad esempio, per aggiungere un nuovo operatore con il nome `test`, aggiorna questa sezione come segue:

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

L’amministrazione degli operatori è centralizzata in Adobe Admin Console e le seguenti attività ora sono gestite esclusivamente tramite questa console. Scopri come creare utenti e assegnare autorizzazioni in [Documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Opzioni non disponibili {#unavailable-migration}

Dopo la migrazione, le seguenti attività non sono più disponibili nella console client:

* Utilizza il [Opzione Unisci righe selezionate](../../platform/using/updating-data.md#merge-data) per unire gli operatori.

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
>* [Che cos’è Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}

