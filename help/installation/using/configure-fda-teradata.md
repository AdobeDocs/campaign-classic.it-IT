---
product: campaign
title: Configurare l’accesso alle Teradate
description: Scopri come configurare l’accesso alle Teradate in FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3a5856c3-b642-4722-97ff-6ae7107efdbe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1636'
ht-degree: 1%

---

# Configurare l’accesso alle Teradate {#configure-access-to-teradata}



Utilizzare Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Per configurare l’accesso a Teradata, segui la procedura riportata di seguito.

1. Installare e configurare [Teradate](#teradata-config)
1. Configurare la Teradata [account esterno](#teradata-external) in Campaign
1. Configurazione [configurazione aggiuntiva](#teradata-additional-configurations) per il server Teradata e Campaign

## Configurazione teradata {#teradata-config}

È necessario installare i driver per Teradata per implementare la connessione a Campaign.

1. Installare [Driver ODBC per Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   È costituito da tre pacchetti che possono essere installati su Red Hat (o CentOS)/Suse nell’ordine seguente:

   * TeraGSS
   * tdicu1510 (installarlo utilizzando setup_wrapper.sh)
   * tdodbc1510 (installarlo utilizzando setup_wrapper.sh)

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: **/etc/odbc.ini** per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver:

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     ```

     &quot;InstallDir&quot; corrisponde alla posizione del **odbcinst.ini** file.

   * **/etc/odbcinst.ini**

     ```
     [ODBC DRIVERS]
     teradata=Installed
     
     [teradata]
     Driver=/opt/teradata/client/17.10/lib64/tdataodbc_sb64.so
     APILevel=CORE
     ConnectFunctions=YYY
     DriverODBCVer=3.51
     SQLLevel=1
     ```

1. Specifica le variabili di ambiente del server Adobe Campaign:

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 e /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NLSPATH**: posizione del file opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>La connessione a un database esterno di Teradata in FDA richiede passaggi di configurazione aggiuntivi sul server Adobe Campaign. [Ulteriori informazioni](#teradata-additional-configurations).
>

## Teradata account esterno{#teradata-external}

L’account esterno Teradata ti consente di collegare l’istanza Campaign al database esterno Teradata.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clic **[!UICONTROL New]** e seleziona **[!UICONTROL External database]** as **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. Per configurare **[!UICONTROL Teradata]** account esterno, è necessario specificare:

   * **[!UICONTROL Type]**: scegli il **[!UICONTROL Teradata]** tipo.

   * **[!UICONTROL Server]**: URL o nome del server di Teradata

   * **[!UICONTROL Account]**: nome dell’account utilizzato per accedere al database Teradata

   * **[!UICONTROL Password]**: password utilizzata per la connessione al database Teradata

   * **[!UICONTROL Database]**: nome del database (facoltativo)

   * **[!UICONTROL Options]**: opzioni da trasmettere attraverso la Teradata. Utilizza il seguente formato: &#39;parameter=value&#39;. Utilizzare un punto e virgola come separatore tra i valori.

   * **[!UICONTROL Timezone]**: fuso orario impostato nella Teradata. [Ulteriori informazioni](#timezone)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| TD_MAX_SESSIONS | Specifica il numero massimo di sessioni di accesso che il Trasportatore parallelo di Teradate può acquisire per un processo operatore. |
| TimeZoneName | Nome del fuso orario del server. |
| Set di caratteri | Utilizzato per configurare il set di caratteri Teradata. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/Configuration-of-odbc.ini-in-UNIX/Linux-and-Apple-OS-X/Teradata-DSN-Options#rub1478609534082__table_N102D3_N102B6_N102B3_N10001). |
| IANAAppCodePage | Tabella codici applicazione ODBC. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/ODBC-Driver-for-Teradata-Application-Development/International-Character-Set-Support/Application-Code-Page) |

### Aggiungi altri account esterni ODBC {#add-external}

>[!NOTE]
>
> Questa opzione non è disponibile per le build precedenti alla versione 7.3.1.

Il driver di Teradata fornisce una propria libreria ODBC, ma questa potrebbe non essere compatibile con altri account esterni ODBC.

Se si desidera configurare un altro account esterno che utilizza anche ODBC, ad esempio Snowflake, è necessario aggiungere un&#39;opzione ODBCLib impostata al percorso della libreria ODBC predefinita (`/usr/lib/x86_64-linux-gnu/libodbc.so` su Debian e `/usr/lib64/libodbc.so` su RHEL/CentOS).

![](assets/ext_account_24.png)

### Query banding

Quando più utenti di Adobe Campaign si connettono allo stesso account esterno di Teradata FDA, il **[!UICONTROL Query banding]** Questa scheda ti consente di impostare una banda di query, ovvero un set di coppie chiave/valore, in una sessione.

![](assets/ext_account_20.png)

Quando questa opzione è configurata, ogni volta che un utente di Campaign esegue una query sul database delle Teradate, Adobe Campaign invia metadati, costituiti da un elenco di chiavi, associati a tale utente. Questi dati possono quindi essere utilizzati dagli amministratori di Teradate a scopo di audit o per gestire i diritti di accesso.

>[!NOTE]
>
>Per ulteriori informazioni su **[!UICONTROL Query banding]**, fare riferimento a [Documentazione sulle teradate](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

Per configurare l’assegnazione bande per le query, effettua le seguenti operazioni:

1. Utilizza il  **[!UICONTROL Default]** per immettere una banda di query predefinita che verrà utilizzata se a un utente non è associata alcuna banda di query. Se questo campo viene lasciato vuoto, gli utenti senza banda di query non potranno utilizzare Teradata.

1. Utilizza il **[!UICONTROL Users]** per specificare una banda di query per ogni utente. Puoi aggiungere tutte le coppie chiave/valore necessarie, ad esempio priorità=1;carico di lavoro=alto. Se all’utente non è assegnata alcuna banda di query, il **[!UICONTROL Default]** verrà applicato.

1. Controlla la **[!UICONTROL Active]** per attivare questa funzione

#### Risoluzione dei problemi dell’account esterno {#external-account-troubleshooting}

Se durante il test della connessione viene visualizzato il seguente errore **TIM-030008 Data &#39;2&#39;: caratteri mancanti (iRc=-53)** verificare che il driver ODBC sia installato correttamente e che LD_LIBRARY_PATH (Linux) / PATH (Windows) sia impostato per il server Campaign.

L’errore **Errore ODB-240000: [Microsoft][ODBC Driver Manager] Impossibile trovare il nome dell&#39;origine dati. Nessun driver predefinito specificato.** si verifica con Windows se si utilizza un driver 16.X. Adobe Campaign prevede che la teradata sia denominata &quot;{teradata}&#39; in odbcinst.ini.

* A partire da Campaign 18.10, è possibile aggiungere ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; nelle opzioni dell’account esterno. Il numero di versione può cambiare, il nome esatto può essere trovato eseguendo odbcad32.exe e accedendo alla scheda Driver.

* Se utilizzi una versione di Campaign precedente, dovrai copiare la sezione Teradata di odbcinst.ini creata dall’installazione del driver in una nuova sezione denominata Teradata. In questo caso è possibile utilizzare Regedit. Se la base è in latino1, sarà necessario aggiungere **APICharSize=1** nelle opzioni.

## Configurazioni aggiuntive {#teradata-additional-configurations}

<!--
### Compatibility {#teradata-compatibility}

**Based in Unicode**

| Database version | Driver version |  Minimal Campaign version required |  Note |
|:-:|:-:|:-:|:-:|
| 15  |  15 |  Campaign Classic 17.9 | Under Linux: Queries with timestamp may fail (fixed in build 8937 for 18.4 and 8977 for 18.10) In debug mode, warnings relative to bad memory usage in the driver may occur. |
| 15  | 16  | Campaign Classic 17.9  | Recommended setup for a Teradata 15 database under Linux.  |
|  16 | 16  | Campaign Classic 18.10 |  Unicode characters with surrogate pairs are not fully handled. Using surrogate characters in data should work. Using surrogates in a filtering condition of a query will not work without this change. |
| 16  |  15 |  Campaign Classic 19.0 |  &nbsp; |

**Based in Latin1**

Versions previous to Adobe Campaign Classic 17.9 only supported Teradata Latin-1 database.

Starting from Adobe Campaign Classic 17.9, we now support by default Teradata database in Unicode.

Customers with a Latin-1 Teradata database migrating to a recent Campaign Classic release will have to add the parameter APICharSize=1 in the options of the external account.
-->

### Configurazione utente {#user-configuration}

Nel database esterno sono necessari i seguenti diritti: crea/rilascia/esegui procedure personalizzate, crea/rilascia/inserisci/seleziona tabelle. Se desideri utilizzare le funzioni md5 e sha2 nell’istanza di Adobe Campaign, potrebbe essere necessario creare funzioni in modalità utente.

Assicurati di configurare il fuso orario corretto. Deve corrispondere a quanto verrà impostato nell’account esterno creato nell’istanza di Adobe Campaign.

Adobe Campaign non imposterà una modalità di protezione (fallback) sugli oggetti che creerà nel database. Potrebbe essere necessario impostare un valore predefinito per l’utente che Adobe Campaign utilizzerà per connettersi al database Teradata utilizzando la seguente query:

| disabilita fallback predefinito |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### Installazione di MD5 {#md5-installation}

Se desideri utilizzare le funzioni md5 nell’istanza di Adobe Campaign, dovrai installare la funzione modalità utente nel database di Teradata da questo [pagina](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

La sha1 del file scaricato è la seguente: 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Per installare md5:

1. Decomprimi il file md5_20080530.zip.

1. Vai alla directory md5/src.

1. Connettersi al database delle Teradate utilizzando bteq.

1. Esegui il seguente comando bteq:

   ```
   .run file = hash_md5.btq
   ```

### Installazione di SHA2 {#sha2-installation}

Se desideri utilizzare le funzioni sha2 nell’istanza di Adobe Campaign, devi installare la funzione modalità utente nel database delle Teradate da questo [pagina](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

L’sha1 del file scaricato è il seguente e87438d37424836358bd3902cf1adeb629349780.

Per installare sha2:

1. Decomprimi il file teradata-udf-sha2-1.0.zip.

1. Vai alla directory teradata-udf-sha2-1.0/src.

1. Connettersi al database delle Teradate utilizzando bteq.

1. Esegui i due seguenti comandi bteq:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### Installazione di UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Se si desidera utilizzare le funzioni udf_utf16to8 nell&#39;istanza di Adobe Campaign, installare la funzione della modalità utente nel database delle Teradate dalla **Kit di strumenti Unicode teradata**.

Lo sha1 del file scaricato è il seguente: e58235f434f52c71316a577cb48e20b97d24f470.

Per installare udf_utf16to8:

1. Decomprimi il file utk_release1.7.0.0.zip.

1. Cercate udf_utf16to8.o nei file estratti e individuate la directory che contiene il file. Deve essere denominato utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Connettersi al database delle Teradate utilizzando bteq.

1. Digita il seguente comando bteq:

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
   ```

## Configurazione del server Campaign per Linux {#campaign-server-linux}

Per l&#39;installazione del driver è necessario quanto segue:

* Driver ODBC di teradata, disponibile in questo [pagina](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Utilità e strumenti di teradata (utilizzati per il carico di massa), disponibili in [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Nomi di file e sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Se non è presente alcun pacchetto per la distribuzione Linux, puoi installarlo come descritto su CentOS 7 (ad esempio utilizzando il docker) e quindi copiare il contenuto di /opt/teradata sul server Adobe Campaign.

### Installazione driver ODBC {#odbc-installation}

Per installare il driver ODBC:

1. Estrai il file tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Passare alla directory tdodbc1620.

1. Potrebbe essere necessario correggere lo script di installazione:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Eseguire setup_wrapper.sh.

### Installazione di strumenti e utilità di teradata {#teradata-tools-installation}

Per installare gli strumenti:

1. Estrai il file TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Andare alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Eseguire setup_wrapper.sh.

1. Andare alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Eseguire setup_wrapper.sh.

1. Andare alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Eseguire setup_wrapper.sh.

1. Un file libtelapi.so deve essere disponibile in /opt/teradata/client/16.20/lib64.

## Configurazione del server Campaign per Windows {#campaign-server-windows}

È innanzitutto necessario scaricare Strumenti e utilità di Teradata per Windows. Puoi scaricarlo da questo [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Assicurarsi di installare il driver ODBC e la Teradata Parallel Transporter Base. Verrà installato telapi.dll utilizzato per eseguire il caricamento in massa sul database delle Teradate.

Assicurarsi che il percorso del driver e delle utilità sia nella variabile PATH che nlserver avrà durante l&#39;esecuzione. Per impostazione predefinita, il percorso è C:\Program Files (x86)\Teradata\Client\15.10\bin su Windows 32 bit o C:\Program Files\Teradata\Client\15.10\bin su 64 bit).

## Fuso orario {#timezone}

La teradata utilizza un nome di fuso orario non standard. L&#39;elenco è disponibile nella [Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign tenterà di convertire il fuso orario specificato nella configurazione esterna in un formato comprensibile alle Teradate. Se non viene trovata alcuna corrispondenza, per la sessione verrà trovato il fuso orario GMT+X (o GMT-X) dell’armadio, con un avviso nel registro.

La conversione viene eseguita leggendo un file denominato teradata_timezones.txt che deve trovarsi nella seguente directory datakit: /usr/local/neolane/nl6/datakit in linux. Se modifichi questo file, assicurati di contattare il team di Adobe Campaign per apportare la modifica nel codice sorgente; in caso contrario, il file verrà sovrascritto durante il prossimo aggiornamento di Campaign.

Il fuso orario utilizzato per la connessione verrà indicato quando si esegue nlserver con lo switch -verbose, ad esempio:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Se il fuso orario utilizzato non è quello corretto, è possibile aggiungere un&#39;opzione denominata &quot;TimeZoneName&quot; all&#39;account esterno. In tal caso, utilizzare il valore della Teradata, ad esempio &quot;TimeZoneName=Europe Central&quot;.

Quando si utilizza il caricamento in massa o il &quot;caricamento rapido&quot; nei documenti delle Teradate, Campaign non può indicare il fuso orario. Pertanto, si consiglia di impostare il fuso orario predefinito dell’utente che Campaign utilizzerà per connettersi:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
