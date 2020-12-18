---
solution: Campaign Classic
product: campaign
title: Aggiornamento della struttura del database
description: Aggiornamento della struttura del database
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---


# Aggiornamento della struttura del database{#updating-the-database-structure}

Per applicare le modifiche apportate agli schemi, avviate la procedura guidata di aggiornamento del database. Questa procedura guidata è accessibile tramite **[!UICONTROL Tools > Advanced > Update database structure]**. Controlla se la struttura fisica del database corrisponde alla relativa descrizione logica ed esegue gli script di aggiornamento SQL.

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

