---
product: campaign
title: Prima di avviare la migrazione
description: Prima di avviare la migrazione
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# Prima di avviare la migrazione{#before-starting-migration}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>In questo documento, i comandi collegati al database vengono forniti come esempio. Questi possono variare a seconda della loro configurazione. Contattare l&#39;amministratore del database.

## Avvisi {#warnings}

* Il processo di migrazione deve essere eseguito solo da utenti esperti. Devi essere assistito da almeno un esperto di database, un amministratore di sistema e uno sviluppatore di applicazioni di Adobe Campaign.
* Prima di avviare la migrazione, verifica che i sistemi e i componenti di sistema utilizzati siano in realtà compatibili con v7. Consulta la [matrice di compatibilità](../../rn/using/compatibility-matrix.md).
* Se utilizzi Adobe Campaign Cloud Messaging (mid-sourcing), contatta l’Adobe prima di avviare l’intera procedura di migrazione.
* Prima di avviare un processo di migrazione, **deve** eseguire il backup dei dati.
* Il processo di migrazione potrebbe richiedere diversi giorni per essere completato.
* Adobe Campaign v7 è più rigoroso rispetto alle versioni 5.11 e 6.02 in termini di configurazione. Questo è principalmente per evitare problemi come la corruzione dei dati e per preservare l&#39;integrità dei dati nel database. Di conseguenza, alcune funzioni offerte nelle versioni v5.11 e v6.02 potrebbero non funzionare più nella versione v7 e potrebbero quindi essere adattate dopo la migrazione. Prima di mettere in produzione qualsiasi cosa, ti consigliamo di testare sistematicamente tutte le configurazioni, in particolare i flussi di lavoro necessari per utilizzare Adobe Campaign.

### Versione installata {#installed-version}

Prima di eseguire la migrazione, installa la build più recente della versione corrente in uso.

Controlla la versione sul server accedendo al **[!UICONTROL Help> About]** nella console client utilizzando **pdump nlserver** comando.

### Backup dei dati {#data-backup}

Prima di avviare un processo di migrazione, **deve** eseguire il backup dei dati.

### Ambiente {#environment}

* Non è possibile modificare il tipo di motore di database (DBMS). Ad esempio, non è possibile passare da un motore PostgreSQL a un motore di Oracle. Tuttavia, è possibile passare da un motore di Oracle 8 a un motore di Oracle 10.
* Impossibile passare da un database non Unicode a un database Unicode.

### Consiglio {#recommendation}

Poiché la procedura di migrazione è sensibile, si consiglia vivamente di leggere attentamente questo documento prima di avviare la procedura.

## Passaggi di migrazione {#migration-steps}

La procedura di migrazione deve essere espletata **tutto** server e in un ordine particolare.

* Nel caso di un **piattaforma indipendente** (modalità macchina singola), l&#39;applicazione viene migrata completamente.
* Nel caso di un **piattaforma standard** (azienda), le fasi di migrazione sono le seguenti:

   1. Esegui la migrazione del server di marketing.
   1. Eseguire la migrazione del server di posta (mta).
   1. Esegui la migrazione dei server di reindirizzamento e tracking (Apache / IIS).

* Nel caso di un **Piattaforma di messaggistica cloud**, i server di esecuzione sono ospitati in Adobe Campaign. Contatta Adobe Campaign per coordinare la migrazione tra server diversi.
* Nel caso di un **Piattaforma Power Booster o Power Cluster**, le fasi di migrazione sono le seguenti:

   1. Esegui la migrazione dei server di reindirizzamento e tracking (Apache / IIS).
   1. Eseguire la migrazione dei server Power Booster/Cluster.
   1. Esegui la migrazione del server di marketing.

## Password utente {#user-passwords}

Nella versione v7, **interno** e **admin** la connessione dell&#39;operatore deve essere protetta da una password. Si consiglia vivamente di assegnare password a questi account e a tutti gli account dell&#39;operatore, **prima della migrazione**. Se non hai specificato una password per **interno**, non sarà possibile connettersi. Per assegnare una password a **interno**, immetti il comando seguente:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La **interno** La password deve essere identica per tutti i server di tracciamento. Per ulteriori informazioni, consulta la [Identificatore interno](../../installation/using/configuring-campaign-server.md#internal-identifier) e [Autorizzazioni](../../platform/using/access-management.md) sezioni.
