---
title: Gestione dati SQL
description: Ulteriori informazioni sull'attività del flusso di lavoro di gestione dati SQL
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 1%

---


# Gestione dati SQL{#sql-data-management}

L&#39;attività **SQL Data Management** consente di creare script SQL personalizzati per creare e compilare tabelle di lavoro.

## Prerequisiti {#prerequisites}

Prima di configurare l&#39;attività, accertatevi che siano soddisfatti i seguenti prerequisiti:

* L&#39;attività è disponibile solo per le origini dati remote. Il pacchetto **[!UICONTROL FDA]** (Federated Data Access) deve quindi essere installato nell&#39;istanza (vedere [questa sezione](../../platform/using/about-fda.md)).
* Lo schema in uscita deve esistere nel database ed essere collegato a un database FDA (per ulteriori informazioni sugli schemi di dati, consultare [questa sezione](../../configuration/using/about-schema-reference.md)).
* L&#39;operatore che esegue il flusso di lavoro deve avere il **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** nome right. For more on named rights, refer to [this section](../../platform/using/access-management.md#named-rights).

## Configurazione dell&#39;attività di gestione dati SQL {#configuring-the-sql-data-management-activity}

1. Specificate l&#39;attività **[!UICONTROL Label]**.
1. Selezionate l&#39;account **[!UICONTROL External account]** da utilizzare, quindi selezionate il **[!UICONTROL Outbound schema]** collegamento a questo account esterno.

   >[!CAUTION]
   >
   >Lo schema in uscita è fisso e non può essere modificato.

1. Aggiungete lo script SQL.

   >[!CAUTION]
   >
   >È responsabilità del writer dello script SQL assicurarsi che lo script SQL sia funzionale e che i relativi riferimenti (nomi di campi, ecc.) sono conformi allo schema in uscita.

   Se si desidera caricare un codice SQL esistente, selezionare l&#39; **[!UICONTROL The SQL script is contained in an entity stored in the database]** opzione. Gli script SQL devono essere creati e memorizzati nel **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** menu.

   In caso contrario, digitare o copiare/incollare lo script SQL nell&#39;area dedicata.

   ![](assets/sql_datamanagement.png)

   L&#39;attività consente di utilizzare le seguenti variabili nello script:

   * **activity.tableName**: Nome SQL della tabella di lavoro in uscita.
   * **task.entrionTransitionByName(‘name’).tableName**: Nome SQL della tabella di lavoro gestita dalla transizione in entrata da utilizzare (la transizione è identificata dal nome).

      >[!NOTE]
      >
      >Il valore (&#39;name&#39;) corrisponde al **[!UICONTROL Name]** campo delle proprietà di transizione.

1. Se lo script SQL contiene già comandi per creare una tabella di lavoro in uscita, deselezionare l&#39; **[!UICONTROL Automatically create work table]** opzione. In caso contrario, una tabella di lavoro viene creata automaticamente dopo l&#39;esecuzione del flusso di lavoro.
1. Fate clic **[!UICONTROL Ok]** per confermare la configurazione dell&#39;attività.

L&#39;attività ora è configurata. È pronto per essere eseguito nel flusso di lavoro.

>[!CAUTION]
>
>Una volta eseguita l&#39;attività, il conteggio dei record di transizione in uscita è solo indicativo. Può variare a seconda del livello di complessità dello script SQL.
>  
>Se l&#39;attività viene riavviata, l&#39;intero script viene eseguito dall&#39;inizio, indipendentemente dal suo stato di esecuzione.

## Esempi di script SQL {#sql-script-samples}

>[!NOTE]
>
>Gli esempi di script in questa sezione sono destinati ad essere eseguiti in PostgreSQL.

Lo script seguente consente di creare una tabella di lavoro e di inserire dati in questa stessa tabella di lavoro:

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

Lo script seguente consente di eseguire un&#39;operazione CTAS (CREATE TABLE AS SELECT) e creare un indice della tabella di lavoro:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

Lo script seguente consente di unire due tabelle di lavoro:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

