---
solution: Campaign Classic
product: campaign
title: Gestione dati SQL
description: Ulteriori informazioni sull'attività del flusso di lavoro SQL Data Management
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 3%

---


# Gestione dati SQL{#sql-data-management}

L&#39;attività **SQL Data Management** consente di scrivere script SQL personalizzati per creare e popolare tabelle di lavoro.

## Prerequisiti {#prerequisites}

Prima di configurare l’attività, verifica che siano soddisfatti i seguenti prerequisiti:

* L’attività è disponibile solo per le origini dati remote. Il pacchetto **[!UICONTROL FDA]** (Federated Data Access) deve quindi essere installato nell’istanza. [Ulteriori informazioni](../../installation/using/about-fda.md).
* Lo schema in uscita deve esistere nel database ed essere collegato a un database FDA. [Ulteriori informazioni](../../configuration/using/about-schema-reference.md).
* L’operatore che esegue il flusso di lavoro deve avere il **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** con nome right. [Ulteriori informazioni](../../platform/using/access-management-named-rights.md).

## Configurazione dell&#39;attività SQL Data Management {#configuring-the-sql-data-management-activity}

1. Specifica l&#39;attività **[!UICONTROL Label]**.
1. Seleziona il **[!UICONTROL External account]** da utilizzare, quindi seleziona il **[!UICONTROL Outbound schema]** collegato a questo account esterno.

   >[!CAUTION]
   >
   >Lo schema in uscita è fisso e non può essere modificato.

1. Aggiungi lo script SQL.

   >[!CAUTION]
   >
   >È responsabilità dell&#39;autore dello script SQL assicurarsi che lo script SQL funzioni e che i relativi riferimenti (nomi di campi, ecc.) sono conformi allo schema in uscita.

   Se si desidera caricare un codice SQL esistente, selezionare l&#39;opzione **[!UICONTROL The SQL script is contained in an entity stored in the database]**. Gli script SQL devono essere creati e memorizzati nel menu **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]**.

   In caso contrario, digitare o copiare-incollare lo script SQL nell&#39;area dedicata.

   ![](assets/sql_datamanagement.png)

   L’attività ti consente di utilizzare le seguenti variabili nello script:

   * **activity.tableName**: Nome SQL della tabella di lavoro in uscita.
   * **task.entrionTransitionByName(‘name’).tableName**: Nome SQL della tabella di lavoro gestita dalla transizione in entrata da utilizzare (la transizione è identificata dal suo nome).

      >[!NOTE]
      >
      >Il valore (&#39;name&#39;) corrisponde al campo **[!UICONTROL Name]** delle proprietà di transizione.

1. Se lo script SQL contiene già comandi per creare una tabella di lavoro in uscita, deselezionare l&#39;opzione **[!UICONTROL Automatically create work table]**. In caso contrario, una tabella di lavoro viene creata automaticamente una volta eseguito il flusso di lavoro.
1. Fai clic su **[!UICONTROL Ok]** per confermare la configurazione dell’attività.

L’attività è ora configurata. È pronto per essere eseguito nel flusso di lavoro.

>[!CAUTION]
>
>Una volta eseguita l’attività, il conteggio dei record di transizione in uscita è indicativo solo. Può variare a seconda del livello di complessità dello script SQL.
>  
>Se l’attività viene riavviata, l’intero script viene eseguito dall’inizio, indipendentemente dallo stato di esecuzione.

## Esempi di script SQL {#sql-script-samples}

>[!NOTE]
>
>Gli esempi di script in questa sezione devono essere eseguiti in PostgreSQL.

Lo script sottostante consente di creare una tabella di lavoro e inserire dati in questa stessa tabella di lavoro:

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

Lo script sottostante consente di eseguire un&#39;operazione CTAS (CREATE TABLE AS SELECT) e creare un indice della tabella di lavoro:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

Lo script sottostante consente di unire due tabelle di lavoro:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

