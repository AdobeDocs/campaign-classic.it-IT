---
product: campaign
title: Prima di avviare la migrazione
description: Prima di avviare la migrazione
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Prerequisiti{#before-starting-migration}

![](../../assets/v7-only.svg)

In questa pagina sono elencati i passaggi specifici da eseguire prima di avviare il processo di migrazione. È inoltre necessario fare riferimento a [questa pagina](about-migration.md) per ulteriori informazioni.

>[!NOTE]
>
>In questo documento, i comandi vengono forniti come esempi. Possono variare a seconda della configurazione.

1. Controlla la tua versione di Adobe Campaign: prima di eseguire la migrazione, installa la build più recente della versione corrente in uso.
1. Esegui il backup dei dati.
1. Controlla il tuo ambiente: non è possibile modificare il sistema del motore di database (DBMS). Ad esempio, non è possibile passare da un motore PostgreSQL a un motore di Oracle. Tuttavia, puoi passare alla versione più recente del motore di database. Non è possibile passare da un database non Unicode a un database Unicode.

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

>[!CAUTION]
>
>La **interno** La password deve essere identica per tutti i server di tracciamento. Per ulteriori informazioni, consulta la [Identificatore interno](../../installation/using/configuring-campaign-server.md#internal-identifier) e [Autorizzazioni](../../platform/using/access-management.md) sezioni.
