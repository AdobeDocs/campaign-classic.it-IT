---
product: campaign
title: Accesso a un database esterno
description: Scopri come accedere ed elaborare i dati in un database esterno
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# Introduzione a Federated Data Access {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign fornisce **Federated Data Access** (FDA) opzione per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

## Prerequisiti {#operating-principle}

L’opzione FDA ti consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati dalle origini SQL.

Per utilizzare questa funzionalità, i prerequisiti sono elencati di seguito:

* **Configurazione**: ad eccezione del Snowflake, è necessario un **on-premise** o **ibrido** modello di hosting per configurare Federated Data Access. [Ulteriori informazioni](../../installation/using/hosting-models.md)
* **Versione database esterna**: è necessario disporre di un database esterno compatibile con il modulo FDA di Adobe Campaign. L’elenco dei sistemi di database e delle versioni compatibili è dettagliato in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Autorizzazioni**: gli utenti devono inoltre avere [autorizzazioni necessarie](../../installation/using/remote-database-access-rights.md) in Adobe Campaign e sul database esterno.

