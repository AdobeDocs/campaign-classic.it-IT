---
product: campaign
title: Introduzione a Federated Data Access
description: Scopri come accedere ed elaborare i dati in un database esterno
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Introduzione a Federated Data Access {#about-federated-data-access}



Adobe Campaign fornisce **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

## Prerequisiti {#operating-principle}

L’opzione FDA ti consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati provenienti dalle origini SQL.

Per utilizzare questa funzionalità, i prerequisiti sono elencati di seguito:

* **Configurazione**: l’elenco dei database esterni compatibili dipende dai [modello di hosting](../../installation/using/hosting-models.md).
* **Versione database esterno**: è necessario disporre di un database esterno compatibile con il modulo FDA di Adobe Campaign.

  L’elenco dei sistemi di database e delle versioni compatibili per ciascun modello di hosting è descritto in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Autorizzazioni**: gli utenti devono inoltre disporre [autorizzazioni necessarie](../../installation/using/remote-database-access-rights.md) in Adobe Campaign e sul database esterno.

