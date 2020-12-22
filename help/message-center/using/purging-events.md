---
solution: Campaign Classic
product: campaign
title: Rimozione di eventi
description: Rimozione di eventi
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 6%

---


# Rimozione di eventi{#purging-events}

È possibile utilizzare la [procedura guidata di distribuzione](../../production/using/database-cleanup-workflow.md#deployment-wizard) per configurare per quanto tempo i dati devono essere memorizzati nel database.

La rimozione degli eventi viene eseguita automaticamente dal [flusso di lavoro di pulizia del database](../../production/using/database-cleanup-workflow.md). Questo flusso di lavoro elimina gli eventi ricevuti e memorizzati nelle istanze di esecuzione e negli eventi archiviati in un&#39;istanza di controllo.

Utilizzate le frecce come appropriato per modificare le impostazioni di eliminazione.

Impostazioni di eliminazione eventi in un&#39;istanza di controllo:

![](assets/messagecenter_delete_events_001.png)

Impostazioni di eliminazione eventi in un&#39;istanza di esecuzione:

![](assets/messagecenter_delete_events_002.png)

Per ulteriori informazioni sul flusso di lavoro di pulizia del database, consultare [questa sezione](../../production/using/database-cleanup-workflow.md).
