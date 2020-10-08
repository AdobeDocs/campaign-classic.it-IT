---
title: Raccomandazioni specifiche per RDBMS
seo-title: Raccomandazioni specifiche per RDBMS
description: Raccomandazioni specifiche per RDBMS
seo-description: null
page-status-flag: never-activated
uuid: 637c1b5a-0484-4734-a012-eb4ba8036263
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: b2219912-5570-45d2-8b52-52486e29d008
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 1%

---


# Raccomandazioni specifiche per RDBMS{#rdbms-specific-recommendations}

Per facilitare l&#39;impostazione dei piani di manutenzione, questa sezione elenca alcune raccomandazioni/best practice adattate ai vari motori RDBMS che  Adobe Campaign supporta. Tuttavia, queste sono solo raccomandazioni. Sta a voi adattarli alle vostre esigenze, in conformità con la vostra procedura interna e i vostri vincoli. L&#39;amministratore del database ha la responsabilità di creare ed eseguire tali piani.

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

1. L&#39;esecuzione del seguente comando consente di individuare tabelle e indici di grandi dimensioni:

   ```
   select * from uvSpace;
   ```

### Manutenzione semplice {#simple-maintenance}

In PostgreSQL, i comandi tipici che si possono utilizzare sono **vuoto pieno** e **reindicizzati**.

Di seguito è riportato un esempio tipico di un piano di manutenzione SQL da eseguire regolarmente con i due comandi seguenti:

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>*  Adobe consiglia di iniziare con tabelle più piccole: in questo modo, se il processo ha esito negativo su tabelle di grandi dimensioni (dove il rischio di fallimento è più elevato), almeno una parte della manutenzione è stata completata.
>*  Adobe riordina l&#39;aggiunta delle tabelle specifiche del modello dati che possono essere soggette a aggiornamenti significativi. Questo può essere il caso di **NmsRecipient** se si dispone di flussi di replica dati giornalieri di grandi dimensioni.
>* I comandi **sottovuoto** e **reindicizzati** bloccheranno la tabella, che mette in pausa alcuni processi durante la manutenzione.
>* Per le tabelle molto grandi (generalmente sopra 5 Gb), **vuoto pieno** può diventare abbastanza inefficiente e richiede molto tempo.  Adobe non consiglia di utilizzarlo per la tabella **YyyNmsBroadLogXxx** .
>* Questa operazione di manutenzione può essere implementata da un flusso di lavoro Adobe Campaign , utilizzando un&#39; **[!UICONTROL SQL]** attività (per ulteriori informazioni, consulta [questa sezione](../../workflow/using/architecture.md)). Accertatevi di pianificare la manutenzione per un periodo di attività basso che non entri in conflitto con la finestra di backup.

>



### Ricreazione di un database {#rebuilding-a-database}

PostgreSQL non fornisce un modo semplice per eseguire una ricostruzione della tabella online, dal momento che il **vuoto intero** blocca la tabella, impedendo così la produzione regolare. Ciò significa che la manutenzione deve essere eseguita quando la tabella non è utilizzata. Potete effettuare le seguenti operazioni:

* eseguire la manutenzione quando la piattaforma Adobe Campaign  viene arrestata,
* arrestate i vari servizi secondari  Adobe Campaign che potrebbero scrivere nella tabella in fase di ricostruzione (**nlserver arresta wfserver instance_name** per arrestare il processo del flusso di lavoro).

Di seguito è riportato un esempio di deframmentazione delle tabelle che utilizza funzioni specifiche per generare la DDL necessaria. Il seguente SQL consente di creare due nuove funzioni: **GenRebuildTablePart1** e **GenRebuildTablePart2**, che possono essere utilizzati per generare il DDL necessario per ricreare una tabella.

* La prima funzione consente di creare una tabella di lavoro (** _tmp** qui) che è una copia della tabella originale.
* La seconda funzione elimina quindi la tabella originale e rinomina la tabella di lavoro e i relativi indici.
* L&#39;utilizzo di due funzioni invece di una indica che se la prima ha esito negativo, non si rischia di eliminare la tabella originale.

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

L&#39;esempio seguente può essere utilizzato in un flusso di lavoro per ricreare le tabelle necessarie anziché utilizzare il comando **vuoto/ricostruzione** :

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

## Oracle {#oracle}

Contattare l&#39;amministratore del database per conoscere le procedure più adatte alla versione di Oracle in uso.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Per Microsoft SQL Server, potete utilizzare il piano di manutenzione descritto [in questa pagina](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

L&#39;esempio seguente riguarda Microsoft SQL Server 2005. Se usate un’altra versione, contattate l’amministratore del database per informazioni sulle procedure di manutenzione.

1. Innanzitutto, collegatevi a Microsoft SQL Server Management Studio con un login con diritti di amministratore.
1. Passate alla **[!UICONTROL Management > Maintenance Plans]** cartella, fate clic con il pulsante destro del mouse e scegliete **[!UICONTROL Maintenance Plan Wizard]**
1. Fare clic **[!UICONTROL Next]** quando viene visualizzata la prima pagina.
1. Selezionare il tipo di piano di manutenzione da creare (programmi separati per ogni attività o singola pianificazione per l&#39;intero piano), quindi fare clic sul **[!UICONTROL Change...]** pulsante.
1. Nella **[!UICONTROL Job schedule properties]** finestra, selezionare le impostazioni di esecuzione desiderate e fare clic su **[!UICONTROL OK]** , quindi fare clic su **[!UICONTROL Next]** .
1. Selezionate le attività di manutenzione da eseguire, quindi fate clic su **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >È consigliabile eseguire almeno le attività di manutenzione indicate di seguito. È anche possibile selezionare l&#39;attività di aggiornamento delle statistiche, anche se è già eseguita dal flusso di lavoro di pulizia del database.

1. Nell&#39;elenco a discesa, selezionare il database sul quale si desidera eseguire l&#39; **[!UICONTROL Database Check Integrity]** attività.
1. Selezionate il database e fate clic su **[!UICONTROL OK]** , quindi fate clic su **[!UICONTROL Next]** .
1. Configura la dimensione massima allocata al database, quindi fai clic su **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >Se la dimensione del database supera questa soglia, il piano di manutenzione tenterà di eliminare i dati inutilizzati per liberare spazio.

1. Riorganizzare o ricreare l’indice:

   * Se il tasso di frammentazione dell&#39;indice è compreso tra 10% e 40%, si consiglia di riorganizzarlo.

      Scegliere i database e gli oggetti (tabelle o viste) da riorganizzare, quindi fare clic su **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >A seconda della configurazione, è possibile scegliere le tabelle selezionate in precedenza oppure tutte le tabelle del database.

   * Se il tasso di frammentazione dell&#39;indice è superiore al 40%, si consiglia di effettuare una nuova generazione.

      Selezionare le opzioni che si desidera applicare all&#39;attività di ricreazione indice, quindi fare clic su **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >Il processo di ricreazione dell&#39;indice è più restrittivo in termini di utilizzo del processore e blocca le risorse del database. Fate clic sull&#39; **[!UICONTROL Keep index online while reindexing]** opzione se desiderate che l&#39;indice sia disponibile durante la ricostruzione.

1. Selezionate le opzioni che desiderate visualizzare nel rapporto attività, quindi fate clic su **[!UICONTROL Next]** .
1. Controllare l&#39;elenco delle attività configurate per il piano di manutenzione, quindi fare clic su **[!UICONTROL Finish]** .

   Viene visualizzato un riepilogo del piano di manutenzione e degli stati dei vari passaggi.

1. Una volta completato il piano di manutenzione, fare clic su **[!UICONTROL Close]** .
1. In Microsoft SQL Server Explorer, fate doppio clic sulla **[!UICONTROL Management > Maintenance Plans]** cartella.
1. Selezionate il piano di manutenzione  Adobe Campaign: i vari passaggi sono descritti in dettaglio in un flusso di lavoro.

   Un oggetto è stato creato nella **[!UICONTROL SQL Server Agent > Jobs]** cartella. Questo oggetto consente di avviare il piano di manutenzione. Nel nostro esempio esiste un solo oggetto, in quanto tutte le attività di manutenzione fanno parte dello stesso piano.

   >[!CAUTION]
   >
   >Affinché l&#39;oggetto possa essere eseguito, è necessario che l&#39;agente di Microsoft SQL Server sia abilitato.

**Configurazione di un database separato per le tabelle di lavoro**

>[!NOTE]
>
>Questa configurazione è facoltativa.

L&#39;opzione **WdbcOptions_TempDbName** consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server. In questo modo vengono ottimizzati backup e replica.

Questa opzione può essere utilizzata per creare tabelle di lavoro (ad esempio, le tabelle create durante l&#39;esecuzione di un flusso di lavoro) in un altro database.

Quando si imposta l&#39;opzione su &quot;tempdb.dbo.&quot;, le tabelle di lavoro verranno create nel database temporaneo predefinito di Microsoft SQL Server. L&#39;amministratore del database deve consentire l&#39;accesso in scrittura al database tempdb.

Se questa opzione è impostata, verrà utilizzata in tutti i database di Microsoft SQL Server configurati in  Adobe Campaign (database principale e account esterni). Si noti che se due account esterni condividono lo stesso server, possono verificarsi conflitti (in quanto tempdb sarà univoco). Allo stesso modo, se due istanze Campaign utilizzano lo stesso server MSSQL, potrebbero verificarsi conflitti se utilizzano lo stesso tempdb.
