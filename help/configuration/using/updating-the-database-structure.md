---
title: Aggiornamento della struttura del database
seo-title: Aggiornamento della struttura del database
description: Aggiornamento della struttura del database
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 11%

---


# Aggiornamento della struttura del database{#updating-the-database-structure}

Per applicare le modifiche apportate agli schemi, avviate la procedura guidata di aggiornamento del database. Questa procedura guidata è accessibile tramite **[!UICONTROL Tools > Advanced > Update database structure]** . Controlla se la struttura fisica del database corrisponde alla relativa descrizione logica ed esegue gli script di aggiornamento SQL.

![](assets/d_ncs_integration_schema_update.png)

I moduli nel database vengono automaticamente popolati e attivati.

![](assets/d_ncs_integration_schema_update_select.png)

Le opzioni **[!UICONTROL Add stored procedures]** e **[!UICONTROL Import initialization data]** vengono utilizzate per avviare gli script SQL iniziali e i pacchetti di dati eseguiti al momento della creazione del database.

Potete importare un set di dati da un pacchetto di dati esterno. A questo scopo, selezionate **[!UICONTROL Import a package]** e immettete il file XML del pacchetto.

Seguite i passaggi e visualizzate lo script SQL di aggiornamento del database:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Si trova in un campo di modifica e può essere modificato per eliminare o aggiungere codice SQL.

Quindi, avviate l&#39;aggiornamento del database:

![](assets/d_ncs_integration_schema_update3.png)

