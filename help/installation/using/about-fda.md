---
product: campaign
title: Accesso a un database esterno
description: Scopri come accedere ed elaborare i dati in un database esterno
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# Guida introduttiva di Federated Data Access {#about-federated-data-access}

Adobe Campaign fornisce l&#39;opzione **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

## Prerequisiti {#operating-principle}

L’opzione FDA ti consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati dalle origini SQL.

Per utilizzare questa funzionalità, i prerequisiti sono elencati di seguito:

* **Configurazione**: ad eccezione, ad Snowflake, per impostare Federated Data Access è necessario un modello  **on-** premise o  **** ibridi. [Ulteriori informazioni](../../installation/using/hosting-models.md)
* **Versione** del database esterno: è necessario disporre di un database esterno compatibile con il modulo FDA di Adobe Campaign. L’elenco dei sistemi di database e delle versioni compatibili è dettagliato nella matrice di compatibilità di Campaign [a1/>.](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)
* **Autorizzazioni**: Gli utenti devono inoltre disporre delle autorizzazioni  [necessarie ](../../installation/using/remote-database-access-rights.md) in Adobe Campaign e nel database esterno.

