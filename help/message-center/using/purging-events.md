---
title: Rimozione di eventi
seo-title: Rimozione di eventi
description: Rimozione di eventi
seo-description: null
page-status-flag: never-activated
uuid: bbce6813-dfa8-418c-9b52-06e814c15265
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2f643080-93b4-4c9f-80cf-b1770b149e6c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 8%

---


# Rimozione di eventi{#purging-events}

È possibile utilizzare la procedura guidata di distribuzione per configurare per quanto tempo i dati devono essere memorizzati nel database.

La rimozione degli eventi viene eseguita automaticamente dal **[!UICONTROL Database cleanup]** flusso di lavoro. Questo flusso di lavoro elimina gli eventi ricevuti e memorizzati nelle istanze di esecuzione e negli eventi archiviati in un&#39;istanza di controllo.

Utilizzate le frecce come appropriato per modificare le impostazioni di eliminazione.

Impostazioni di eliminazione eventi in un&#39;istanza di controllo:

![](assets/messagecenter_delete_events_001.png)

Impostazioni di eliminazione eventi in un&#39;istanza di esecuzione:

![](assets/messagecenter_delete_events_002.png)

Per ulteriori informazioni sul flusso di lavoro di pulizia del database, consulta [questa sezione](../../production/using/database-cleanup-workflow.md).
