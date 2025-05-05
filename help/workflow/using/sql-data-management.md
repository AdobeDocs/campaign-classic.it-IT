---
product: campaign
title: Gestione dati SQL
description: Ulteriori informazioni sull'attività del flusso di lavoro di Gestione dati SQL
feature: Workflows
hide: true
hidefromtoc: true
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 4%

---

# Gestione dati SQL{#sql-data-management}



L&#39;attività **Gestione dati SQL** consente di scrivere script SQL personalizzati per creare e popolare tabelle di lavoro.

## Prerequisiti {#prerequisites}

Prima di configurare l’attività, assicurati di soddisfare i seguenti prerequisiti:

* L’attività è disponibile solo per le origini dati remote. Il pacchetto **[!UICONTROL FDA]** (Federated Data Access) deve pertanto essere installato nell&#39;istanza. [Ulteriori informazioni](../../installation/using/about-fda.md).

  Per ulteriori informazioni, a seconda della versione di Campaign in uso, consulta le sezioni seguenti:

  ![](assets/do-not-localize/v7.jpeg) [Documentazione di Campaign v7](../../installation/using/about-fda.md)

  ![](assets/do-not-localize/v8.png) [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html?lang=it)

* Lo schema in uscita deve esistere nel database ed essere collegato a un database FDA.
* L&#39;operatore che esegue il flusso di lavoro deve disporre dell&#39;autorizzazione denominata **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]**. [Ulteriori informazioni](../../platform/using/access-management-named-rights.md).

## Configurazione dell&#39;attività di gestione dati SQL {#configuring-the-sql-data-management-activity}

1. Specificare l&#39;attività **[!UICONTROL Label]**.
1. Seleziona **[!UICONTROL External account]** da utilizzare, quindi seleziona **[!UICONTROL Outbound schema]** collegato a questo account esterno.

   >[!CAUTION]
   >
   >Lo schema In uscita è fisso e non può essere modificato.

1. Aggiungere lo script SQL.

   >[!CAUTION]
   >
   >È responsabilità dell&#39;autore dello script SQL verificare che lo script SQL funzioni e che i relativi riferimenti (nomi di campi, ecc.) siano conformi allo schema in uscita.

   Per caricare un codice SQL esistente, selezionare l&#39;opzione **[!UICONTROL The SQL script is contained in an entity stored in the database]**. Gli script SQL devono essere creati e memorizzati nel menu **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]**.

   In caso contrario, digitare o copiare e incollare lo script SQL nell&#39;area dedicata.

   ![](assets/sql_datamanagement.png)

   L’attività ti consente di utilizzare le seguenti variabili nello script:

   * **activity.tableName**: nome SQL della tabella di lavoro in uscita.
   * **task.incomingTransitionByName(‘name’).tableName**: Nome SQL della tabella di lavoro della transizione in ingresso da utilizzare (la transizione è identificata dal relativo nome).

     >[!NOTE]
     >
     >Il valore (&#39;name&#39;) corrisponde al campo **[!UICONTROL Name]** delle proprietà di transizione.

1. Se lo script SQL contiene già comandi per la creazione di una tabella di lavoro in uscita, deselezionare l&#39;opzione **[!UICONTROL Automatically create work table]**. In caso contrario, una tabella di lavoro viene creata automaticamente una volta eseguito il flusso di lavoro.
1. Fare clic su **[!UICONTROL Ok]** per confermare la configurazione dell&#39;attività.

L’attività adesso è configurata. È pronto per essere eseguito nel flusso di lavoro.

>[!CAUTION]
>
>Una volta eseguita l’attività, il conteggio dei record di transizione in uscita è solo indicativo. Può variare in base al livello di complessità dello script SQL.
>  
>Se l’attività viene riavviata, l’intero script viene eseguito dal suo inizio, indipendentemente dallo stato di esecuzione.

## Esempi di script SQL {#sql-script-samples}

>[!NOTE]
>
>Gli esempi di script in questa sezione devono essere eseguiti in PostgreSQL.

Lo script sottostante consente di creare una tabella di lavoro e di inserire dati nella stessa tabella di lavoro:

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

Lo script seguente consente di eseguire un&#39;operazione CTAS (CREATE TABLE AS SELECT) e di creare un indice della tabella di lavoro:

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
