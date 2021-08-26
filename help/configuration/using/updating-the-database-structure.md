---
product: campaign
title: Aggiornamento della struttura del database
description: Aggiornamento della struttura del database
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# Aggiornamento della struttura del database{#updating-the-database-structure}

![](../../assets/v7-only.svg)

Per applicare le modifiche apportate agli schemi, avvia la procedura guidata di aggiornamento del database. Questa procedura guidata è accessibile tramite **[!UICONTROL Tools > Advanced > Update database structure]** . Controlla se la struttura fisica del database corrisponde alla relativa descrizione logica ed esegue gli script di aggiornamento SQL.

![](assets/d_ncs_integration_schema_update.png)

I moduli nel database vengono compilati e attivati automaticamente.

![](assets/d_ncs_integration_schema_update_select.png)

Le opzioni **[!UICONTROL Add stored procedures]** e **[!UICONTROL Import initialization data]** vengono utilizzate per avviare gli script SQL iniziali e i pacchetti di dati eseguiti al momento della creazione del database.

Puoi importare un set di dati da un pacchetto di dati esterno. A questo scopo, seleziona **[!UICONTROL Import a package]** e immetti il file XML del pacchetto.

Seguire i passaggi e visualizzare lo script SQL di aggiornamento del database:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Questo si trova in un campo di modifica e può essere modificato per eliminare o aggiungere codice SQL.

Quindi, avvia l&#39;aggiornamento del database:

![](assets/d_ncs_integration_schema_update3.png)
