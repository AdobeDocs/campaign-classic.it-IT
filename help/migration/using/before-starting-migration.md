---
solution: Campaign Classic
product: campaign
title: Prima di avviare la migrazione
description: Prima di avviare la migrazione
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 1%

---


# Prima di avviare la migrazione{#before-starting-migration}

>[!NOTE]
>
>In questo documento, i comandi collegati al database sono forniti come esempio. che possono variare a seconda della configurazione. Contattate l’amministratore del database.

## Avvisi {#warnings}

* Il processo di migrazione deve essere eseguito solo da utenti esperti. È necessario essere assistiti da almeno un esperto del database, un amministratore di sistema e uno sviluppatore di applicazioni  Adobe Campaign.
* Prima di avviare la migrazione, verificate che i sistemi e i componenti di sistema utilizzati siano effettivamente compatibili con v7. Consultate la matrice [di](../../rn/using/compatibility-matrix.md)compatibilità.
* Se utilizzi  Adobe Campaign Cloud Messaging (mid-sourcing), contatta  Adobe prima di avviare l&#39;intera procedura di migrazione.
* Prima di avviare un processo di migrazione, è **necessario** eseguire il backup dei dati.
* Il completamento del processo di migrazione potrebbe richiedere diversi giorni.
*  Adobe Campaign v7 è più rigido rispetto alle versioni 5.11 e 6.02 in termini di configurazione. Questo è principalmente per evitare problemi come la corruzione dei dati e per preservare l&#39;integrità dei dati nel database. Di conseguenza, alcune funzioni offerte nelle release v5.11 e v6.02 potrebbero non funzionare più nella release v7 e potrebbero pertanto dover essere adattate dopo la migrazione. Prima di iniziare la produzione, consigliamo di testare sistematicamente tutte le configurazioni, in particolare i flussi di lavoro necessari per utilizzare  Adobe Campaign.

### Versione installata {#installed-version}

Prima di eseguire la migrazione, installate la build più recente della versione corrente in uso.

Controllare la versione sul server accedendo al **[!UICONTROL Help> About]** menu della console client utilizzando il comando **nlserver pdump** .

### Backup dei dati {#data-backup}

Prima di avviare un processo di migrazione, è **necessario** eseguire il backup dei dati.

### Ambiente {#environment}

* Non è possibile modificare il tipo di motore del database (DBMS). Ad esempio, non è possibile passare da un motore PostgreSQL a un motore Oracle . Tuttavia, è possibile passare da un motore Oracle 8  a un motore Oracle 10 .
* Non è possibile passare da un database non Unicode a un database Unicode.

### Raccomandazione {#recommendation}

Poiché la procedura di migrazione è delicata, si consiglia vivamente di leggere attentamente questo documento prima di avviare la procedura.

## Passaggi di migrazione {#migration-steps}

La procedura di migrazione deve essere eseguita su **tutti** i server e in un ordine particolare.

* Nel caso di una piattaforma **** indipendente (modalità a macchina singola), l’applicazione viene migrata completamente.
* Nel caso di una piattaforma **** standard (enterprise), le fasi di migrazione sono le seguenti:

   1. Esegui la migrazione del server di marketing.
   1. Migrate il server di posta (mta).
   1. Migrare i server di reindirizzamento e tracciamento (Apache / IIS).

* Nel caso di una piattaforma **** Cloud Messaging, i server di esecuzione sono ospitati  Adobe Campaign. Contattate  Adobe Campaign per coordinare la migrazione tra server diversi.
* Nel caso di una piattaforma **** Power Booster o Power Cluster, le fasi di migrazione sono le seguenti:

   1. Migrare i server di reindirizzamento e tracciamento (Apache / IIS).
   1. Migrare i server Power Booster/Cluster.
   1. Esegui la migrazione del server di marketing.

## Password utente {#user-passwords}

In v7, la connessione dell’operatore **interno** e **amministratore** deve essere protetta da una password. Si consiglia vivamente di assegnare password a questi account e a tutti gli account degli operatori, **prima della migrazione**. Se non avete specificato una password **interna**, non potrete connettervi. Per assegnare una password a **internal**, immettete il comando seguente:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La password **interna** deve essere identica per tutti i server di tracciamento. Per ulteriori informazioni, consultare le sezioni [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier) (Identificatore [interno) e](../../platform/using/access-management.md#about-permissions) About permissions (Informazioni sulle autorizzazioni).

