---
title: Prima di avviare la migrazione
seo-title: Prima di avviare la migrazione
description: Prima di avviare la migrazione
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 3%

---


# Prima di avviare la migrazione{#before-starting-migration}

>[!NOTE]
>
>In questo documento, i comandi collegati al database sono forniti come esempio. che possono variare a seconda della configurazione. Contattate l’amministratore del database.

## Avvisi {#warnings}

### Versione installata {#installed-version}

Prima di eseguire la migrazione, installate la build più recente della versione corrente in uso.

Controllare la versione sul server accedendo al **[!UICONTROL Help> About]** menu della console client utilizzando il comando **nlserver pdump** .

### Backup dei dati {#data-backup}

Prima di avviare un processo di migrazione, è **necessario** eseguire il backup dei dati.

### Ambiente {#environment}

* Non è possibile modificare il tipo di motore del database (DBMS). Ad esempio, non è possibile passare da un motore PostgreSQL a un motore Oracle. È tuttavia possibile passare da un motore Oracle 8 a un motore Oracle 10.
* Non è possibile passare da un database non Unicode a un database Unicode.

### Raccomandazione {#recommendation}

Poiché la procedura di migrazione è particolarmente delicata, raccomandiamo vivamente di leggere attentamente questo documento prima di avviare la procedura.

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

>[!NOTE]
>
>È possibile comunicare tra un server di marketing v6.02 e un server v7 Cloud Messaging o Power Booster/Cluster. Tuttavia, se decidi di mantenere il server di marketing v6.02, questo deve essere aggiornato con la build v6.02 più recente prima di eseguire la migrazione a Cloud Messaging o Power Booster/Cluster.

## Password utente {#user-passwords}

In v7, la connessione dell’operatore **interno** e **amministratore** deve essere protetta da una password. Si consiglia vivamente di assegnare password a questi account e a tutti gli account degli operatori, **prima della migrazione**. Se non avete specificato una password **interna**, non potrete connettervi. Per assegnare una password a **internal**, immettete il comando seguente:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La password **interna** deve essere identica per tutti i server di tracciamento. Per ulteriori informazioni, consultare le sezioni [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier) (Identificatore [interno) e](../../platform/using/access-management.md#about-permissions) About permissions (Informazioni sulle autorizzazioni).

