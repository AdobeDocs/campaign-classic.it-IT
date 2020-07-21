---
title: Appendici
seo-title: Appendici FDA
description: Appendici FDA
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 789799f79608c26126d70e896bd1b7a6df33e4fa
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---


# Appendici {#fda-appendices}

## Configurazioni aggiuntive Teradata {#teradata-configuration}

### Compatibilità {#teradata-compatibility}

**Basato in Unicode**

| Versione database | Versione driver | Versione minima della campagna richiesta | Nota |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | In Linux: Le query con marca temporale potrebbero non riuscire (corrette nella build 8937 per 18.4 e 8977 per 18.10) In modalità debug, potrebbero verificarsi avvisi relativi all&#39;utilizzo di memoria errato nel driver. |
| 15 | 16 | Campaign Classic 17.9 | Impostazione consigliata per un database Teradata 15 in Linux. |
| 16 | 16 | Campaign Classic 18.10 | I caratteri Unicode con coppie di surrogati non vengono gestiti completamente. L&#39;utilizzo di caratteri sostitutivi nei dati dovrebbe funzionare. L&#39;utilizzo di surrogati in una condizione di filtro di una query non funzionerà senza questa modifica. |
| 16 | 15 | non supportato |   |

**Basato in Latin1**

Le versioni precedenti  Adobe Campaign Classic 17.9 supportavano solo il database Teradata Latin-1.

A partire  Adobe Campaign Classic 17.9, ora è supportato dal database Teradata predefinito in Unicode.

I clienti con un database Latino-1 Teradata che eseguono la migrazione a una versione recente di Campaign Classic dovranno aggiungere il parametro APICharSize=1 nelle opzioni dell’account esterno.

### Configurazione del database {#database-configuration}

#### Configurazione utente {#user-configuration}

Sono richiesti i seguenti diritti: creare/rilasciare/eseguire procedure personalizzate, creare/rilasciare/inserire/selezionare tabelle. È inoltre possibile che sia necessario creare funzioni di modalità utente se si desidera utilizzare le funzioni md5 e sha2 nell&#39;istanza del Adobe Campaign .

Accertatevi di configurare il fuso orario corretto. Deve corrispondere a quanto verrà impostato nell&#39;account esterno creato nell&#39;istanza del Adobe Campaign .

 Adobe Campaign non imposta una modalità di protezione (fallback) sugli oggetti che verranno creati nel database. Potrebbe essere necessario impostare un valore predefinito per l&#39;utente che  Adobe Campaign utilizzerà per connettersi al database Teradata utilizzando la seguente query:

| disattiva fallback predefinito |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### Installazione di MD5 {#md5-installation}

Se si desidera utilizzare le funzioni md5 nell&#39;istanza  Adobe Campaign, è necessario installare la funzione modalità utente nel database Teradata da questa [pagina](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

Lo sha1 del file scaricato è il seguente 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Per installare md5:

1. Decomprimete il file md5_20080530.zip.

1. Andate alla directory md5/src.

1. Connettiti al tuo database Teradata utilizzando bteq.

1. Eseguite il seguente comando bteq:

   ```
   .run file = hash_md5.btq
   ```

#### Installazione SHA2 {#sha2-installation}

Se si desidera utilizzare le funzioni sha2 nell&#39;istanza del Adobe Campaign , è necessario installare la funzione modalità utente nel database Teradata da questa [pagina](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

Lo sha1 del file scaricato è il seguente e87438d37424836358bd3902cf1adeb629349780.

Per installare sha2:

1. Decomprimete il file teradata-udf-sha2-1.0.zip.

1. Andate alla directory teradata-udf-sha2-1.0/src.

1. Connettiti al tuo database Teradata utilizzando bteq.

1. Eseguite i due comandi bteq seguenti:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### Installazione di UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Se si desidera utilizzare le funzioni udf_utf16to8 nell&#39;istanza  Adobe Campaign, sarà necessario installare la funzione modalità utente nel database Teradata dal kit **di strumenti** Teradata unicode di questa [pagina](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

Lo sha1 del file scaricato è il seguente e58235f434f52c71316a577cb48e20b97d24f470.

Per installare udf_utf16to8:

1. Decomprimete il file utk_release1.7.0.0.zip.

1. Cercate udf_utf16to8.o nei file estratti e andate alla directory che contiene il file. Deve essere denominato utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselLinux-x8664/udf_install/.

1. Connettiti al tuo database Teradata utilizzando bteq.

1. Digitate il seguente comando bteq:

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   
### Configurazione del server Campaign per Linux {#campaign-server-linux}

Per l&#39;installazione del driver è necessario quanto segue:

* Driver ODBC Teradata, che si trova in questa [pagina](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Strumenti e utility Teradata (utilizzati per il caricamento in blocco), che si trova in questa [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Nomi file e sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f 4fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Se non è presente alcun pacchetto per la distribuzione Linux, è possibile installare come spiegato in un CentOS 7 (ad esempio utilizzando docker) e copiare il contenuto di /opt/teradata sul server di Adobe Campaign .

#### Installazione driver ODBC {#odbc-installation}

Per installare il driver ODBC:

1. Estrarre il file tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Andate alla directory tdodbc1620.

1. Potrebbe essere necessario correggere lo script di installazione:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Eseguire setup_wrapper.sh.

#### Installazione di strumenti e utility Teradata {#teradata-tools-installation}

Per installare Strumenti:

1. Estrarre il file TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Andate alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Eseguire setup_wrapper.sh.

1. Andate alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Eseguire setup_wrapper.sh.

1. Andate alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Eseguire setup_wrapper.sh.

1. Un file libtelapi.so deve essere disponibile in /opt/teradata/client/16.20/lib64.

#### Configurazione driver {#driver-configuration}

Per ulteriori informazioni sulla configurazione del driver, consultare questa [sezione](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Variabili di ambiente {#environment-varaiables}

Per ulteriori informazioni sulle variabili di ambiente del server di Adobe Campaign , consultare questa [sezione](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Configurazione del server campagna per Windows #campaign-server-windows}

È innanzitutto necessario scaricare gli strumenti e le utility Teradata per Windows. Puoi scaricarlo da questa [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Accertatevi di installare il driver ODBC e la Teradata Parallel Transporter Base. Verrà installato telapi.dll utilizzato per eseguire il caricamento in massa sul database Teradata.

Verificare che il percorso del driver e delle utility sia nella variabile PATH che nlserver avrà durante l&#39;esecuzione. Per impostazione predefinita, il percorso è C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit).

### Risoluzione di problemi di account esterni {#external-account-troubleshooting}

Se durante il test della connessione **TIM-030008 Date &#39;2&#39; viene visualizzato il seguente errore: caratteri mancanti (iRc=-53)** assicurarsi che il driver ODBC sia installato correttamente e che LD_LIBRARY_PATH (Linux) / PATH (Windows) sia impostato per il server Campaign.

Errore ODBC **ODB-240000:[Nome origine dati Microsoft][ODBC Driver Manager]non trovato e nessun driver predefinito specificato.** si verifica con Windows se si utilizza un driver 16.X.  Adobe Campaign prevede che i teradata siano denominati &#39;{teradata}&#39; in odbcinst.ini.
Se si dispone di una versione server di Adobe Campaign 18.10 , è possibile aggiungere ODBCDRiverName=&quot;Driver ODBC 16.10 del database Teradata&quot; nelle opzioni dell&#39;account esterno. Il numero di versione può cambiare, il nome esatto può essere trovato eseguendo odbcad32.exe e l&#39;accesso alla scheda Driver.
Per la versione inferiore a 18.10, sarà necessario copiare la sezione Teradata di odbcinst.ini creata dall&#39;installazione del driver in una nuova sezione chiamata Teradata,regedit può essere utilizzato in questo caso.

Se la base è in latin1, è necessario aggiungere APICharSize=1 nelle opzioni.

### Fuso orario {#timezone}

Teradata utilizza un nome di fuso orario non standard. L&#39;elenco è disponibile nel sito [Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA).  Adobe Campaign cercherà di convertire il fuso orario indicato nella configurazione esterna in qualcosa che Teradata capisce. Se non viene trovata una corrispondenza, verrà trovato il fuso orario GMT+X (o GMT-X) più chiuso per la sessione, con un avviso nel registro.

La conversione viene eseguita leggendo un file denominato teradata_timezones.txt che dovrebbe trovarsi nella seguente directory di datakit: /usr/local/neolane/nl6/datakit sotto linux. Se modifichi questo file, contatta il team del Adobe Campaign  per apportare la modifica al codice sorgente, altrimenti il file verrà sovrascritto durante il prossimo aggiornamento di Campaign.

Il fuso orario utilizzato per la connessione viene indicato quando si esegue nlserver con lo switch -verbose, ad esempio:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Se il fuso orario utilizzato non è quello corretto, è possibile aggiungere un&#39;opzione denominata &quot;TimeZoneName&quot; sull&#39;account esterno. In tal caso, utilizzate il valore Teradata, ad esempio &quot;TimeZoneName=Europe Central&quot;.

Quando nei documenti Teradata viene utilizzato un carico in massa o un &quot;caricamento rapido&quot;, Campaign non è in grado di indicare il fuso orario. Pertanto, si consiglia di impostare il fuso orario predefinito per l&#39;utente che Campaign utilizzerà per connettersi:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## Configurazione di MySQL 5.7 {#mysql-57-configuration}

### Configurazione server {#server-configuration-mysql}

La configurazione del server non richiede passaggi di installazione specifici.  Adobe Campaign deve funzionare con un database latin1, con valori predefiniti in MySQL o con un database unicode.

### Installazione driver {#driver-installation-mysql}

#### Debian {#debian-mysql}

Scarica mysql-apt-config.deb da questa [pagina](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

Installare la libreria client:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

Scarica il connettore C da questa [pagina](https://dev.mysql.com/downloads/connector/c). È consigliabile scaricare la versione 5.7.

Accertatevi che la directory che contiene libmysqlclient.dll sia aggiunta alla variabile di ambiente PATH che nlserver utilizzerà.

#### CentOS {#centos-mysql}

Scarica mysql57-community-release.noarch.rpm da questa [pagina](https://dev.mysql.com/downloads/repo/yum).

Installare la libreria client:

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### Configurazione account esterno {#external-account-mysql}

La configurazione dell&#39;account esterno non richiede passaggi specifici. Accertatevi che il fuso orario e l&#39;opzione Usa dati Unicode siano impostati in base al database.
