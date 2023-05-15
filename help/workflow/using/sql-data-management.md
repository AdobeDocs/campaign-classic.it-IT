---
product: campaign
title: Gestione dati SQL
description: Ulteriori informazioni sull'attività del flusso di lavoro SQL Data Management
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# Gestione dati SQL{#sql-data-management}



La **Gestione dati SQL** attività consente di creare script SQL personalizzati per creare e popolare tabelle di lavoro.

## Prerequisiti {#prerequisites}

Prima di configurare l’attività, verifica che siano soddisfatti i seguenti prerequisiti:

* L’attività è disponibile solo per le origini dati remote. La **[!UICONTROL FDA]** Pertanto, il pacchetto (Federated Data Access) deve essere installato nell’istanza. [Ulteriori informazioni](../../installation/using/about-fda.md).

   Per ulteriori informazioni, a seconda della versione di Campaign, consulta queste sezioni:

   ![](assets/do-not-localize/v7.jpeg)[  Documentazione di Campaign v7](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[  Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html)

* Lo schema in uscita deve esistere nel database ed essere collegato a un database FDA.
* L’operatore che esegue il flusso di lavoro deve avere **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** a destra. [Ulteriori informazioni](../../platform/using/access-management-named-rights.md).

## Configurazione dell&#39;attività di gestione dati SQL {#configuring-the-sql-data-management-activity}

1. Specifica l’attività **[!UICONTROL Label]**.
1. Seleziona la **[!UICONTROL External account]** da utilizzare, quindi seleziona la **[!UICONTROL Outbound schema]** collegato a questo account esterno.

   >[!CAUTION]
   >
   >Lo schema in uscita è fisso e non può essere modificato.

1. Aggiungi lo script SQL.

   >[!CAUTION]
   >
   >È responsabilità dell&#39;autore dello script SQL assicurarsi che lo script SQL funzioni e che i relativi riferimenti (nomi di campi, ecc.) sono conformi allo schema in uscita.

   Se si desidera caricare un codice SQL esistente, selezionare la **[!UICONTROL The SQL script is contained in an entity stored in the database]** opzione . Gli script SQL devono essere creati e memorizzati nel **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** menu.

   In caso contrario, digitare o copiare-incollare lo script SQL nell&#39;area dedicata.

   ![](assets/sql_datamanagement.png)

   L’attività ti consente di utilizzare le seguenti variabili nello script:

   * **activity.tableName**: Nome SQL della tabella di lavoro in uscita.
   * **task.entrinTransitionByName(‘name’).tableName**: Nome SQL della tabella di lavoro gestita dalla transizione in entrata da utilizzare (la transizione è identificata dal suo nome).

      >[!NOTE]
      >
      >Il valore (&#39;name&#39;) corrisponde al valore **[!UICONTROL Name]** dalle proprietà della transizione.

1. Se lo script SQL contiene già comandi per creare una tabella di lavoro in uscita, deselezionare la **[!UICONTROL Automatically create work table]** opzione . In caso contrario, una tabella di lavoro viene creata automaticamente una volta eseguito il flusso di lavoro.
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
