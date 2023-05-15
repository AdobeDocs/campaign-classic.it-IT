---
product: campaign
title: Introduzione a Federated Data Access
description: Scopri come accedere ed elaborare i dati in un database esterno
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Introduzione a Federated Data Access {#about-federated-data-access}



Adobe Campaign fornisce **Federated Data Access** (FDA) opzione per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

## Prerequisiti {#operating-principle}

L’opzione FDA ti consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati dalle origini SQL.

Per utilizzare questa funzionalità, i prerequisiti sono elencati di seguito:

* **Configurazione**: l&#39;elenco del database esterno compatibile dipende dal [modello di hosting](../../installation/using/hosting-models.md).
* **Versione database esterna**: è necessario disporre di un database esterno compatibile con il modulo FDA di Adobe Campaign.

   L’elenco dei sistemi di database e delle versioni compatibili per modello di hosting è dettagliato in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Autorizzazioni**: gli utenti devono inoltre avere [autorizzazioni necessarie](../../installation/using/remote-database-access-rights.md) in Adobe Campaign e sul database esterno.

