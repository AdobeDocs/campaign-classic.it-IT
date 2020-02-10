---
title: Filtrare gli schemi
seo-title: Filtrare gli schemi
description: Filtrare gli schemi
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Filtrare gli schemi{#filtering-schemas}

## Filtri di sistema {#system-filters}

È possibile filtrare l&#39;accesso allo schema per utenti specifici, a seconda delle relative autorizzazioni. I filtri di sistema consentono di gestire le autorizzazioni di lettura e scrittura delle entità dettagliate negli schemi, utilizzando i parametri **readAccess** e **writeAccess** .

>[!NOTE]
>
>Questa limitazione si applica solo agli utenti non tecnici: un utente tecnico con le relative autorizzazioni o che utilizza un flusso di lavoro sarà in grado di recuperare e aggiornare i dati.

* **readAccess**: consente l&#39;accesso in sola lettura ai dati dello schema.

   **Avviso** - Tutte le tabelle collegate devono essere impostate con la stessa limitazione. Questa configurazione può influire sulle prestazioni.

* **writeAccess**: fornisce l&#39;accesso in scrittura ai dati dello schema.

Questi filtri vengono inseriti a livello di **elemento** principale degli schemi e, come illustrato negli esempi seguenti, possono essere formati per limitare l&#39;accesso.

* Limita autorizzazioni di scrittura

   In questo caso, il filtro viene utilizzato per non consentire le autorizzazioni di scrittura sullo schema per gli operatori senza l&#39;autorizzazione di amministrazione. Ciò significa che solo gli amministratori avranno le autorizzazioni di scrittura sulle entità descritte da questo schema.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Limitare le autorizzazioni di lettura e scrittura:

   In questo caso, il filtro viene utilizzato per bloccare le autorizzazioni LETTURA e SCRITTURA sullo schema per tutti gli operatori. Solo l&#39;account **interno** , rappresentato dall&#39;espressione &quot;$(loginId)!=0&quot;, dispone di tali autorizzazioni.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   I possibili valori di attributo **espr** utilizzati per definire la condizione sono TRUE o FALSE.

>[!NOTE]
>
>Se non viene specificato alcun filtro, tutti gli operatori avranno le autorizzazioni di lettura e scrittura per lo schema.

## Protezione degli schemi incorporati {#protecting-built-in-schemas}

Per impostazione predefinita, gli schemi predefiniti sono accessibili solo con autorizzazioni di scrittura per gli operatori con diritti di amministrazione:

* ncm:pubblicare
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
* xtk:fusione
* xtk:image
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

>[!CAUTION]
>
>Le autorizzazioni di lettura e scrittura per lo schema **xtk:sessionInfo** sono accessibili solo dall&#39;account interno di un&#39;istanza di Adobe Campaign.

## Modifica dei filtri di sistema degli schemi incorporati {#modifying-system-filters-of-built-in-schemas}

È comunque possibile modificare i filtri di sistema degli schemi out-of-the-box che per impostazione predefinita sono protetti a causa di problemi di compatibilità con versioni precedenti.

>[!NOTE]
>
>Adobe consiglia tuttavia di non modificare i parametri predefiniti per garantire una protezione ottimale.

1. Create un&#39;estensione per lo schema interessato o aprite un&#39;estensione esistente.
1. Aggiungete un elemento secondario **`<sysfilter name="<filter name>" _operation="delete"/>`** nell&#39;elemento principale per eliminare l&#39;applicazione del filtro sotto lo stesso nello schema di origine.
1. Se lo desiderate, potete aggiungere un nuovo filtro, come descritto in filtri [](#system-filters)di sistema.

