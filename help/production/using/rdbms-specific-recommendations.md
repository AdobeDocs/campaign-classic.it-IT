---
product: campaign
title: Raccomandazioni specifiche per RDBMS
description: Raccomandazioni specifiche per RDBMS
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# Raccomandazioni specifiche per RDBMS{#rdbms-specific-recommendations}

![](../../assets/v7-only.svg)

Per facilitare l’impostazione dei piani di manutenzione, in questa sezione sono elencate alcune raccomandazioni e best practice adattate ai vari motori RDBMS supportati da Adobe Campaign. Tuttavia, si tratta solo di raccomandazioni. Spetta a voi adattarli alle vostre esigenze, in linea con la vostra procedura interna e i vostri vincoli. L&#39;amministratore del database ha la responsabilità di creare ed eseguire questi piani.

## PostgreSQL {#postgresql}

### Rilevamento di tabelle di grandi dimensioni {#detecting-large-tables}

1. È possibile aggiungere la visualizzazione seguente al database:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. Puoi eseguire questa query per individuare tabelle e indici di grandi dimensioni:

   ```
   SELECT * FROM uvSpace;
   ```

   In alternativa, è possibile eseguire questa query, ad esempio per visualizzare tutte le dimensioni dell&#39;indice collettivamente:

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### Manutenzione semplice {#simple-maintenance}

In PostgreSQL è possibile utilizzare le seguenti parole chiave tipiche:

* VUOTO (COMPLETO, ANALISI, VERBOSE)
* REINDEX

Per eseguire l&#39;operazione VACUUM, analizzarla e temporizzarla, è possibile utilizzare la sintassi seguente:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

È consigliabile non omettere l’istruzione ANALYZE. In caso contrario, la tabella svuotata viene lasciata senza statistiche. Il motivo è che viene creata una nuova tabella, quindi quella precedente viene eliminata. Di conseguenza, l’ID oggetto (OID) della tabella cambia, ma non vengono calcolate statistiche. Di conseguenza, si verificheranno immediatamente problemi di prestazioni.

Di seguito è riportato un esempio tipico di un piano di manutenzione SQL da eseguire regolarmente:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;
REINDEX TABLE nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;
REINDEX TABLE nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;
REINDEX TABLE xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;
REINDEX TABLE xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;
REINDEX TABLE xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;
REINDEX TABLE xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;
REINDEX TABLE xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;
REINDEX TABLE xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;
REINDEX TABLE xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;
REINDEX TABLE nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;
REINDEX TABLE nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
REINDEX TABLE nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe consiglia di iniziare con tabelle più piccole: in questo modo, se il processo non riesce su tabelle di grandi dimensioni (dove il rischio di guasto è più elevato), almeno una parte della manutenzione è stata completata.
>* Adobe consiglia di aggiungere le tabelle specifiche del modello dati, soggette a aggiornamenti significativi. Questo può essere il caso **NmsRecipient** se si dispone di flussi di replica dei dati giornalieri di grandi dimensioni.
>* Le istruzioni VACUUM e REINDEX bloccano la tabella, che mette in pausa alcuni processi durante l’esecuzione della manutenzione.
>* Per tabelle molto grandi (generalmente superiori a 5 Gb), l&#39;istruzione VACUUM FULL può diventare piuttosto inefficiente e richiedere molto tempo. Adobe sconsiglia di utilizzarlo per il **YyyNmsBroadLogXxx** tabella.
>* Questa operazione di manutenzione può essere implementata da un flusso di lavoro Adobe Campaign, utilizzando un **[!UICONTROL SQL]** attività. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/architecture.md). Assicurati di pianificare la manutenzione per un tempo di attività ridotto che non entri in conflitto con la finestra di backup.

>


### Ricostruzione di un database {#rebuilding-a-database}

PostgreSQL non fornisce un modo semplice per eseguire una ricostruzione della tabella online, poiché l&#39;istruzione VACUUM FULL blocca la tabella, impedendo così la produzione regolare. Ciò significa che la manutenzione deve essere eseguita quando la tabella non viene utilizzata. Puoi effettuare le seguenti operazioni:

* eseguire la manutenzione quando la piattaforma Adobe Campaign viene arrestata,
* interrompi i vari sottoservizi Adobe Campaign che è probabile scrivano nella tabella in corso di ricostruzione (**nlserver interrompi nome istanza wfserver** per interrompere il processo del flusso di lavoro).

Di seguito è riportato un esempio di deframmentazione della tabella utilizzando funzioni specifiche per generare la DDL necessaria. Il seguente SQL consente di creare due nuove funzioni: **GenRebuildTablePart1** e **GenRebuildTablePart2**, che può essere utilizzato per generare la DDL necessaria per ricreare una tabella.

* La prima funzione consente di creare una tabella di lavoro (** _tmp** qui) che è una copia della tabella originale.
* La seconda funzione elimina quindi la tabella originale e rinomina la tabella di lavoro e i relativi indici.
* L&#39;utilizzo di due funzioni invece di una indica che se la prima ha esito negativo, non si corre il rischio di eliminare la tabella originale.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

L’esempio seguente può essere utilizzato in un flusso di lavoro per ricreare le tabelle richieste anziché utilizzare il **vuoto/ricostruzione** comando:

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

##  Oracle {#oracle}

Contatta l’amministratore del database per informazioni sulle procedure più adatte alla tua versione dell’Oracle.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Per Microsoft SQL Server è possibile utilizzare il piano di manutenzione descritto in [questa pagina](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

L&#39;esempio seguente riguarda Microsoft SQL Server 2005. Se utilizzi un’altra versione, contatta l’amministratore del database per informazioni sulle procedure di manutenzione.

1. Per prima cosa, connettersi a Microsoft SQL Server Management Studio con un accesso con diritti di amministratore.
1. Vai a **[!UICONTROL Management > Maintenance Plans]** cartella, fai clic con il pulsante destro del mouse e scegli **[!UICONTROL Maintenance Plan Wizard]**.
1. Fai clic su **[!UICONTROL Next]** quando viene visualizzata la prima pagina.
1. Selezionare il tipo di piano di manutenzione che si desidera creare (programmi separati per ogni attività o una singola pianificazione per l&#39;intero piano), quindi fare clic sul **[!UICONTROL Change...]** pulsante .
1. In **[!UICONTROL Job schedule properties]** seleziona le impostazioni di esecuzione desiderate e fai clic su **[!UICONTROL OK]**, quindi fai clic su **[!UICONTROL Next]**.
1. Selezionare le attività di manutenzione da eseguire, quindi fare clic su **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >È consigliabile eseguire almeno le attività di manutenzione riportate di seguito. È inoltre possibile selezionare l&#39;attività di aggiornamento delle statistiche, anche se è già eseguita dal flusso di lavoro di pulizia del database.

1. Nell’elenco a discesa, selezionare il database in cui si desidera eseguire il **[!UICONTROL Database Check Integrity]** compito.
1. Seleziona il database e fai clic su **[!UICONTROL OK]**, quindi fai clic su **[!UICONTROL Next]**.
1. Configura la dimensione massima allocata al database, quindi fai clic su **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >Se la dimensione del database supera questa soglia, il piano di manutenzione tenterà di eliminare i dati non utilizzati per liberare spazio.

1. Riorganizza o ricostruisci l&#39;indice:

   * Se il tasso di frammentazione dell’indice è compreso tra il 10% e il 40%, si consiglia una riorganizzazione.

      Scegliere i database e gli oggetti (tabelle o viste) da riorganizzare, quindi fare clic su **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >A seconda della configurazione, è possibile scegliere le tabelle selezionate in precedenza oppure tutte le tabelle del database.

   * Se il tasso di frammentazione dell’indice è superiore al 40%, si consiglia di effettuare una ricostruzione.

      Selezionare le opzioni che si desidera applicare all&#39;attività di ricostruzione dell&#39;indice, quindi fare clic su **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >Il processo di ricostruzione dell&#39;indice è più restrittivo in termini di utilizzo del processore e blocca le risorse del database. Seleziona la **[!UICONTROL Keep index online while reindexing]** se desideri che l&#39;indice sia disponibile durante la ricostruzione.

1. Seleziona le opzioni da visualizzare nel rapporto di attività, quindi fai clic su **[!UICONTROL Next]**.
1. Controllare l&#39;elenco delle attività configurate per il piano di manutenzione, quindi fare clic su **[!UICONTROL Finish]**.

   Viene visualizzato un riepilogo del piano di manutenzione e degli stati dei vari passaggi.

1. Una volta completato il piano di manutenzione, fai clic su **[!UICONTROL Close]**.
1. Nell&#39;elenco di cartelle di Microsoft SQL Server fare doppio clic sul pulsante **[!UICONTROL Management > Maintenance Plans]** cartella.
1. Seleziona il piano di manutenzione Adobe Campaign: i vari passaggi sono descritti in dettaglio in un flusso di lavoro.

   È stato creato un oggetto nella **[!UICONTROL SQL Server Agent > Jobs]** cartella. Questo oggetto consente di avviare il piano di manutenzione. Nel nostro esempio, esiste un solo oggetto in quanto tutte le attività di manutenzione fanno parte dello stesso piano.

   >[!IMPORTANT]
   >
   >Affinché questo oggetto possa essere eseguito, è necessario che l&#39;agente Microsoft SQL Server sia abilitato.

**Configurazione di un database separato per le tabelle di lavoro**

>[!NOTE]
>
>Questa configurazione è facoltativa.

La **WdbcOptions_TempDbName** consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server. Questo ottimizza i backup e la replica.

È possibile utilizzare questa opzione se si desidera creare le tabelle di lavoro (ad esempio le tabelle create durante l’esecuzione di un flusso di lavoro) in un altro database.

Quando si imposta l&#39;opzione su &quot;tempdb.dbo.&quot;, le tabelle di lavoro vengono create nel database temporaneo predefinito di Microsoft SQL Server. L&#39;amministratore del database deve consentire l&#39;accesso in scrittura al database tempdb.

Se l&#39;opzione è impostata, viene utilizzata su tutti i database Microsoft SQL Server configurati in Adobe Campaign (database principale e account esterni). Se due account esterni condividono lo stesso server, possono verificarsi conflitti (in quanto tempdb è univoco). Allo stesso modo, se due istanze Campaign utilizzano lo stesso server MSSQL, potrebbero esserci conflitti se utilizzano lo stesso tempdb.
