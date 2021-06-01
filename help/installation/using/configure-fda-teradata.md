---
product: campaign
title: Configurare l’accesso alle Teradate
description: Scopri come configurare l’accesso alle Teradate in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3a5856c3-b642-4722-97ff-6ae7107efdbe
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---

# Configurare l&#39;accesso alla Teradata {#configure-access-to-teradata}

Utilizza l’opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi riportati di seguito per configurare l’accesso alle Teradate.

1. Installa e configura [driver di Teradata](#teradata-config)
1. Configura la Teradata [account esterno](#teradata-external) in Campaign
1. Configurazione [configurazione aggiuntiva](#teradata-additional-configurations) per il server Teradata e Campaign

## Configurazione teradata {#teradata-config}

Per implementare la connessione a Campaign, devi installare i driver per la Teradata.

1. Installare il driver [ODBC per Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   È composto da tre pacchetti che possono essere installati su Red Hat (o CentOS)/Suse nel seguente ordine:

   * TeraGSS
   * tdicu1510 (installalo utilizzando setup_wrapper.sh)
   * tdodbc1510 (installalo utilizzando setup_wrapper.sh)

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: **/etc/odbc.ini** per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; corrisponde alla posizione del file **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
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


## Account esterno Teradata{#teradata-external}

L’account esterno Teradata ti consente di collegare l’istanza Campaign al database esterno Teradata.

1. Dalla campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fare clic su **[!UICONTROL New]** e selezionare **[!UICONTROL External database]** come **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. Per configurare l’account esterno **[!UICONTROL Teradata]**, devi specificare:

   * **[!UICONTROL Type]**: Scegli il  **[!UICONTROL Teradata]** tipo.

   * **[!UICONTROL Server]**: URL o nome del server Teradata

   * **[!UICONTROL Account]**: Nome dell’account utilizzato per accedere al database delle Teradate

   * **[!UICONTROL Password]**: Password utilizzata per la connessione al database delle Teradate

   * **[!UICONTROL Database]**: Nome del database (facoltativo)

   * **[!UICONTROL Options]**: Opzioni da passare attraverso le Teradate. Utilizza il formato seguente: &#39;parameter=value&#39;. Utilizzare una semicolonna come separatore tra i valori.

   * **[!UICONTROL Timezone]**: Fuso orario impostato in Teradata. [Ulteriori informazioni](#timezone)

### Proiezione query

Quando più utenti Adobe Campaign si collegano allo stesso account esterno della Teradata FDA, la scheda **[!UICONTROL Query banding]** ti consente di impostare una banda di query, ovvero un set di coppie chiave/valore, su una sessione.

![](assets/ext_account_20.png)

Quando questa opzione è configurata, ogni volta che un utente di Campaign esegue una query sul database di Teradata, Adobe Campaign invia metadati, costituiti da un elenco di chiavi associate a questo utente. Questi dati possono quindi essere utilizzati dagli amministratori delle Teradate a scopo di controllo o per gestire i diritti di accesso.

>[!NOTE]
>
>Per ulteriori informazioni su **[!UICONTROL Query banding]**, consulta la [documentazione sulle Teradate](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

Per configurare la banding delle query, effettua le seguenti operazioni:

1. Utilizzare **[!UICONTROL Default]** per immettere una banda di query predefinita che verrà utilizzata se un utente non ha una banda di query associata. Se questo campo viene lasciato vuoto, gli utenti senza banda di query non saranno in grado di utilizzare la Teradata.

1. Utilizza il campo **[!UICONTROL Users]** per specificare una banda di query per ogni utente. È possibile aggiungere tutte le coppie chiave/valore necessarie, ad esempio priority=1;carico di lavoro=alto. Se all’utente non è assegnata alcuna banda di query, viene applicato il campo **[!UICONTROL Default]** .

1. Seleziona la casella **[!UICONTROL Active]** per attivare questa funzione

#### Risoluzione dei problemi relativi all&#39;account esterno {#external-account-troubleshooting}

Se durante il test della connessione viene visualizzato il seguente errore **TIM-030008 Date &#39;2&#39;: caratteri mancanti (iRc=-53)** assicurati che il driver ODBC sia installato correttamente e che LD_LIBRARY_PATH (Linux) / PATH (Windows) sia impostato per il server Campaign.

Errore **ODB-240000 ODBC: [Microsoft][ODBC Driver Manager] Nome origine dati non trovato e nessun driver predefinito specificato.** si verifica con Windows se si utilizza un driver 16.X. Adobe Campaign prevede che la teradata venga denominata &#39;{teradata}&#39; in odbcinst.ini.

* A partire da Campaign 18.10, è possibile aggiungere ODBCDRiverName=&quot;Driver ODBC del database di Teradata 16.10&quot; nelle opzioni dell’account esterno. Il numero di versione può cambiare, il nome esatto può essere trovato eseguendo odbcad32.exe e accedendo alla scheda Driver.

* Se utilizzi una versione precedente di Campaign, dovrai copiare la sezione Teradata di odbcinst.ini creata dall’installazione del driver in una nuova sezione denominata Teradata. In questo caso è possibile utilizzare Regedit. Se la base è in latin1, è necessario aggiungere **APICharSize=1** nelle opzioni.

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

Nel database esterno sono necessari i seguenti diritti: creare/rilasciare/eseguire procedure personalizzate, creare/rilasciare/inserire/selezionare tabelle. È inoltre possibile creare funzioni di modalità utente se si desidera utilizzare le funzioni md5 e sha2 nell’istanza Adobe Campaign.

Assicurati di configurare il fuso orario corretto. Deve corrispondere a ciò che verrà impostato nell’account esterno creato nell’istanza di Adobe Campaign.

Adobe Campaign non imposta una modalità di protezione (fallback) sugli oggetti che creerà nel database. Potrebbe essere necessario impostare un valore predefinito per l’utente che Adobe Campaign utilizzerà per connettersi al database di Teradata utilizzando la seguente query:

| disattiva fallback predefinito |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### Installazione MD5 {#md5-installation}

Se desideri utilizzare le funzioni md5 nella tua istanza di Adobe Campaign, dovrai installare la funzione di modalità utente nel database delle Teradate da questa [pagina](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

Lo sha1 del file scaricato è il seguente 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Per installare md5:

1. Decomprimi il file md5_20080530.zip.

1. Vai alla directory md5/src .

1. Connettiti al database delle Teradate utilizzando bteq.

1. Esegui il seguente comando bteq:

   ```
   .run file = hash_md5.btq
   ```

### Installazione SHA2 {#sha2-installation}

Se desideri utilizzare le funzioni sha2 nella tua istanza di Adobe Campaign, dovrai installare la funzione di modalità utente nel database di Teradata da questa [pagina](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

Lo sha1 del file scaricato è il seguente e87438d37424836358bd3902cf1adeb629349780.

Per installare sha2:

1. Decomprimi il file teradata-udf-sha2-1.0.zip.

1. Vai alla directory teradata-udf-sha2-1.0/src .

1. Connettiti al database delle Teradate utilizzando bteq.

1. Esegui i due seguenti comandi bteq:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### Installazione di UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Se desideri utilizzare le funzioni udf_utf16to8 nell&#39;istanza di Adobe Campaign, dovrai installare la funzione di modalità utente nel database delle Teradate dal **kit di strumenti unicode di Teradata** di questa [pagina](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

Lo sha1 del file scaricato è il seguente e58235f434f52c71316a577cb48e20b97d24f470.

Per installare udf_utf16to8:

1. Decomprimi il file utk_release1.7.0.0.zip.

1. Cerca l&#39;udf_utf16to8.o nei file estratti e passa alla directory che contiene il file. Deve essere denominato utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Connettiti al database delle Teradate utilizzando bteq.

1. Digitare il seguente comando bteq:

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

* Driver ODBC Teradata, disponibile in questa [pagina](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Strumenti e utility teradata (utilizzati per il caricamento in serie), che si trova in questa [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Nomi di file e sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f4 4fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Se non c&#39;è alcun pacchetto per la distribuzione Linux, è possibile installare come spiegato su un CentOS 7 (per esempio utilizzando docker) e quindi copiare il contenuto di /opt/teradata sul server Adobe Campaign.

### Installazione driver ODBC {#odbc-installation}

Per installare il driver ODBC:

1. Estrai il file tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Vai alla directory tdodbc1620.

1. Potrebbe essere necessario correggere lo script di installazione:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Esegui setup_wrapper.sh.

### Installazione di strumenti e utility di teradata {#teradata-tools-installation}

Per installare Strumenti:

1. Estrai il file TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Vai alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Esegui setup_wrapper.sh.

1. Vai alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2 .

1. Esegui setup_wrapper.sh.

1. Vai alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Esegui setup_wrapper.sh.

1. Un file libtelapi.so dovrebbe essere disponibile in /opt/teradata/client/16.20/lib64.

## Configurazione del server Campaign per Windows {#campaign-server-windows}

Prima di tutto è necessario scaricare strumenti e utilità di Teradata per Windows. Puoi scaricarlo da questa [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Assicurati di installare il driver ODBC e la base del trasportatore parallelo Teradata. Verrà installato telapi.dll utilizzato per eseguire il caricamento in massa sul database delle Teradate.

Assicurati che il percorso del driver e delle utility sia nella variabile PATH che nlserver avrà durante l&#39;esecuzione. Per impostazione predefinita, il percorso è C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit).

## Fuso orario {#timezone}

La teradata utilizza un nome di fuso orario non standard. È possibile trovare l&#39;elenco nel [sito Teradate](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign cercherà di convertire il fuso orario specificato nella configurazione esterna in qualcosa che le Teradate possano comprendere. Se non viene trovata una corrispondenza, verrà trovato il fuso orario GMT+X (o GMT-X) più vicino per la sessione, con un avviso nel registro.

La conversione viene eseguita leggendo un file denominato teradata_timezones.txt che dovrebbe trovarsi nella seguente directory del datakit: /usr/local/neolane/nl6/datakit sotto linux. Se modifichi questo file, contatta il team Adobe Campaign per apportare la modifica al codice sorgente, altrimenti il file verrà sovrascritto durante il prossimo aggiornamento di Campaign.

Il fuso orario utilizzato per la connessione viene indicato quando si esegue nlserver con lo switch -verbose, ad esempio:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Se il fuso orario utilizzato non è quello corretto, è possibile aggiungere sull’account esterno un’opzione denominata &quot;TimeZoneName&quot;. In questo caso, utilizza il valore della Teradata, ad esempio &quot;TimeZoneName=Europe Central&quot;.

Quando si utilizza il caricamento in serie o il &quot;caricamento rapido&quot; nei documenti di Teradata, Campaign non può indicare il fuso orario. Pertanto, si consiglia di impostare il fuso orario predefinito dell’utente che Campaign utilizzerà per connettersi:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
