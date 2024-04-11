---
product: campaign
title: Prima di avviare la migrazione
description: Prima di avviare la migrazione
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Prerequisiti{#before-starting-migration}



In questa pagina sono elencati i passaggi specifici da eseguire prima di avviare il processo di migrazione. Devi inoltre fare riferimento a [questa pagina](about-migration.md) per maggiori informazioni.

>[!NOTE]
>
>In questo documento, i comandi vengono forniti come esempi. Possono variare a seconda della configurazione.

1. Verifica la versione di Adobe Campaign: prima di eseguire la migrazione, installa la build più recente della versione corrente in uso.
1. Eseguire il backup dei dati.
1. Controllare l&#39;ambiente: non è possibile modificare il sistema del motore di database (DBMS). Non è possibile, ad esempio, passare da un motore PostgreSQL a un motore di Oracle. È tuttavia possibile passare alla versione più recente del modulo di gestione di database. Non è possibile passare da un database non Unicode a un database Unicode.

## Passaggi di migrazione {#migration-steps}

La procedura di migrazione deve essere effettuata il **tutto** e in un ordine particolare.

* Nel caso di un **piattaforma indipendente** (modalità a computer singolo), l&#39;applicazione viene migrata nella sua interezza.
* Nel caso di un **piattaforma standard** (enterprise), i passaggi di migrazione sono i seguenti:

   1. Esegui la migrazione del server di marketing.
   1. Esegui la migrazione del server di posta (mta).
   1. Esegui la migrazione dei server di reindirizzamento e tracciamento (Apache/IIS).

* Nel caso di un **Piattaforma di messaggistica cloud**, i server di esecuzione sono ospitati in Adobe Campaign. Contatta Adobe Campaign per coordinare la migrazione tra server diversi.
* Nel caso di un **piattaforma Power Booster o Power Cluster**, i passaggi di migrazione sono i seguenti:

   1. Esegui la migrazione dei server di reindirizzamento e tracciamento (Apache/IIS).
   1. Eseguire la migrazione dei server Power Booster/Cluster.
   1. Esegui la migrazione del server di marketing.

## Password utente {#user-passwords}

Nella versione 7, **interno** e **admin** la connessione dell&#39;operatore deve essere protetta da una password. Si consiglia vivamente di assegnare password a questi account e a tutti gli account operatore, **prima della migrazione**. Se non è stata specificata una password per **interno**, non sarà possibile connettersi. Per assegnare una password a **interno**, immetti il comando seguente:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>Il **interno** la password deve essere identica per tutti i server di tracciamento. Per ulteriori informazioni, consulta [Identificatore interno](../../installation/using/configuring-campaign-server.md#internal-identifier) e [Autorizzazioni](../../platform/using/access-management.md) sezioni.
