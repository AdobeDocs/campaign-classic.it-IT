---
product: campaign
title: Filtraggio degli schemi
description: Filtraggio degli schemi
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Filtrare gli schemi{#filtering-schemas}

## Filtri di sistema {#system-filters}

Puoi filtrare l’accesso allo schema per utenti specifici, a seconda delle loro autorizzazioni. I filtri di sistema consentono di gestire le autorizzazioni di lettura e scrittura delle entità dettagliate negli schemi, utilizzando i parametri **readAccess** e **writeAccess**.

>[!NOTE]
>
>Questa restrizione si applica solo agli utenti non tecnici: un utente tecnico, con le autorizzazioni correlate o che utilizza un flusso di lavoro, potrà recuperare e aggiornare i dati.

* **readAccess**: fornisce accesso in sola lettura ai dati dello schema.

  **Avviso** - Tutte le tabelle collegate devono essere impostate con la stessa restrizione. Questa configurazione può influire sulle prestazioni.

* **writeAccess**: fornisce accesso in scrittura ai dati dello schema.

Questi filtri vengono immessi al livello **elemento** principale degli schemi e, come mostrato negli esempi seguenti, possono essere formati per limitare l&#39;accesso.

* Limita autorizzazioni SCRITTURA

  In questo caso, il filtro viene utilizzato per non consentire le autorizzazioni di SCRITTURA sullo schema per gli operatori che non dispongono dell’autorizzazione AMMINISTRAZIONE. Ciò significa che solo gli amministratori avranno autorizzazioni di scrittura sulle entità descritte da questo schema.

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* Limita le autorizzazioni di LETTURA e SCRITTURA:

  In questo caso, il filtro viene utilizzato per non consentire le autorizzazioni di LETTURA e SCRITTURA sullo schema per tutti gli operatori. Solo l&#39;account **internal**, rappresentato dall&#39;espressione &quot;$(loginId).=0&quot;, dispone delle seguenti autorizzazioni.

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  I possibili valori dell&#39;attributo **expr** utilizzati per definire la condizione sono TRUE o FALSE.

>[!NOTE]
>
>Se non viene specificato alcun filtro, tutti gli operatori disporranno di autorizzazioni di lettura e scrittura per lo schema.

## Schemi incorporati di Protect {#protecting-built-in-schemas}

Per impostazione predefinita, gli schemi incorporati sono accessibili solo con autorizzazioni di SCRITTURA per gli operatori con diritti di AMMINISTRAZIONE:

* ncm:pubblicazione
* nl:monitoraggio
* nms:calendario
* xtk:builder
* xtk:connessioni
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:immagine
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:stringhe
* xtk:xslt

>[!IMPORTANT]
>
>Le autorizzazioni di LETTURA e SCRITTURA per lo schema **xtk:sessionInfo** sono accessibili solo dall&#39;account interno di un&#39;istanza di Adobe Campaign.

## Modificare i filtri di sistema degli schemi incorporati {#modifying-system-filters-of-built-in-schemas}

Puoi comunque modificare i filtri di sistema degli schemi predefiniti, che per impostazione predefinita sono protetti a causa di problemi di compatibilità con versioni precedenti.

>[!NOTE]
>
>Tuttavia, l’Adobe consiglia di non modificare i parametri predefiniti per garantire una sicurezza ottimale.

1. Crea un&#39;estensione per lo schema interessato o apri un&#39;estensione esistente.
1. Aggiungere un elemento figlio **`<sysfilter name="<filter name>" _operation="delete"/>`** nell&#39;elemento principale per eliminare l&#39;applicazione del filtro nello stesso schema di origine.
1. Se lo desideri, puoi aggiungere un nuovo filtro, come descritto in [Filtri di sistema](#system-filters).
