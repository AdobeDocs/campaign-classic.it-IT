---
product: campaign
title: Aggiornamento della struttura del database
description: Aggiornamento della struttura del database
feature: Configuration
role: Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
TQID: https://experienceleague.adobe.com/y4P6bZcEyVIdfI4LHMivPIRVzb1Z4sV7ewISWqk29F0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 137
ht-degree: 8%

---

# Aggiornamento della struttura del database{#updating-the-database-structure}



Per applicare le modifiche apportate agli schemi, avviare l&#39;Assistente all&#39;aggiornamento del database. L&#39;assistente è accessibile tramite **[!UICONTROL Tools > Advanced > Update database structure]**. Controlla se la struttura fisica del database corrisponde alla relativa descrizione logica ed esegue gli script di aggiornamento SQL.

![](assets/d_ncs_integration_schema_update.png)

I moduli nel database vengono compilati e attivati automaticamente.

![](assets/d_ncs_integration_schema_update_select.png)

Le opzioni **[!UICONTROL Add stored procedures]** e **[!UICONTROL Import initialization data]** vengono utilizzate per avviare gli script SQL iniziali e i pacchetti di dati eseguiti al momento della creazione del database.

Puoi importare un set di dati da un pacchetto di dati esterno. A tale scopo, selezionare **[!UICONTROL Import a package]** e immettere il file XML del pacchetto.

Seguire la procedura riportata di seguito e visualizzare lo script SQL di aggiornamento del database:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Si trova in un campo di modifica e può essere modificato per eliminare o aggiungere codice SQL.

Quindi, avviare l&#39;aggiornamento del database:

![](assets/d_ncs_integration_schema_update3.png)
