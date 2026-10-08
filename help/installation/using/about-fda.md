---
product: campaign
title: Introduzione a Federated Data Access
description: Scopri come accedere ed elaborare i dati in un database esterno
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: 'https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%
---
# Introduzione a Federated Data Access {#about-federated-data-access}



Adobe Campaign fornisce l&#39;opzione **Federated Data Access** (FDA) per elaborare le informazioni archiviate in uno o più database esterni: è possibile accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

## Prerequisiti {#operating-principle}

L’opzione FDA ti consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati provenienti dalle origini SQL.

Per utilizzare questa funzionalità, i prerequisiti sono elencati di seguito:

* **Configurazione**: l&#39;elenco dei database esterni compatibili dipende dal [modello di hosting](../../installation/using/hosting-models.md).
* **Versione database esterno**: è necessario disporre di un database esterno compatibile con il modulo FDA di Adobe Campaign.

  L&#39;elenco dei sistemi di database e delle versioni compatibili per ogni modello di hosting è descritto in dettaglio nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) di Campaign.

* **Autorizzazioni**: gli utenti devono inoltre disporre delle [autorizzazioni necessarie](../../installation/using/remote-database-access-rights.md) in Adobe Campaign e nel database esterno.

