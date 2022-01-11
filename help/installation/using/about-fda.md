---
product: campaign
title: Accesso a un database esterno
description: Scopri come accedere ed elaborare i dati in un database esterno
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: a23f66a4822f3c87770c5c9741e91f78778931cb
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 3%

---

# Introduzione a Federated Data Access {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign fornisce **Federated Data Access** (FDA) opzione per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

## Prerequisiti {#operating-principle}

L’opzione FDA ti consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati dalle origini SQL.

Per utilizzare questa funzionalità, i prerequisiti sono elencati di seguito:

* **Configurazione**: l&#39;elenco del database esterno compatibile dipende dal [modello di hosting](../../installation/using/hosting-models.md).
* **Versione database esterna**: è necessario disporre di un database esterno compatibile con il modulo FDA di Adobe Campaign.

   L’elenco dei sistemi di database e delle versioni compatibili per modello di hosting è dettagliato in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Autorizzazioni**: gli utenti devono inoltre avere [autorizzazioni necessarie](../../installation/using/remote-database-access-rights.md) in Adobe Campaign e sul database esterno.

