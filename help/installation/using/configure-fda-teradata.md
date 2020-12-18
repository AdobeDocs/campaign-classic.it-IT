---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso ad Teradata
description: Scoprite come configurare l'accesso ad Teradata in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---


# Configurare l&#39;accesso ad Teradata {#configure-access-to-teradata}

Utilizzate l&#39;opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguite i passaggi riportati di seguito per configurare l&#39;accesso ad Teradata.

1. Installare e configurare [driver Teradata](#teradata-config)
1. Configurare l&#39;account Teradata [esterno](#teradata-external) in Campaign
1. Configurare [configurazione aggiuntiva](#teradata-additional-configurations) per il server Teradata e Campaign

## Configurazione teradata {#teradata-config}

Devi installare i driver affinché Teradata possa implementare la connessione a Campaign.

1. Installare il driver ODBC [per Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   È composto da tre pacchetti che possono essere installati su Red Hat (o CentOS)/Suse nell&#39;ordine seguente:

   * TeraGSS
   * tdicu1510 (installarlo utilizzando setup_wrapper.sh)
   * tdodbc1510 (installarlo utilizzando setup_wrapper.sh)

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

1. Specificate le variabili di ambiente del server Adobe Campaign :

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 e /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NLSPATH**: posizione del file opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>La connessione a un database esterno Teradata in FDA richiede passaggi aggiuntivi per le configurazioni sul server Adobe Campaign . [Ulteriori informazioni](#teradata-additional-configurations).


## Account esterno teradata{#teradata-external}

L&#39;account esterno di Teradata consente di collegare l&#39;istanza Campaign al database esterno di Teradata.

1. Da Campaign **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fare clic su **[!UICONTROL New]** e selezionare **[!UICONTROL External database]** come **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. Per configurare l&#39;account esterno **[!UICONTROL Teradata]**, è necessario specificare:

   * **[!UICONTROL Type]**: Scegliete il  **[!UICONTROL Teradata]** tipo.

   * **[!UICONTROL Server]**: URL o nome del server Teradata

   * **[!UICONTROL Account]**: Nome dell&#39;account utilizzato per accedere al database Teradata

   * **[!UICONTROL Password]**: Password utilizzata per connettersi al database Teradata

   * **[!UICONTROL Database]**: Nome del database (facoltativo)

   * **[!UICONTROL Options]**: Opzioni da passare attraverso Teradata. Utilizzate il formato seguente: &#39;parameter=value&#39;. Utilizzare una semicolona come separatore tra i valori.

   * **[!UICONTROL Timezone]**: Fuso orario impostato in Teradata. [Ulteriori informazioni](#timezone)

### Banda query

Quando più utenti Adobe Campaign  si connettono allo stesso account esterno di FDA Teradata, la scheda **[!UICONTROL Query banding]** consente di impostare una banda di query, ovvero un insieme di coppie chiave/valore, in una sessione.

![](assets/ext_account_20.png)

Quando questa opzione è configurata, ogni volta che un utente di Campaign esegue una query sul database Teradata,  Adobe Campaign invierà i metadati, costituiti da un elenco di chiavi, associate a questo utente. Questi dati possono quindi essere utilizzati dagli amministratori di Teradata a scopo di controllo o per gestire i diritti di accesso.

>[!NOTE]
>
>Per ulteriori informazioni su **[!UICONTROL Query banding]**, fare riferimento alla [documentazione Teradata](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

Per configurare la banding delle query, effettuate le seguenti operazioni:

1. Utilizzate **[!UICONTROL Default]** per inserire una banda di query predefinita che verrà utilizzata se un utente non dispone di una banda di query associata. Se questo campo viene lasciato vuoto, gli utenti senza banda di query non potranno utilizzare Teradata.

1. Utilizzare il campo **[!UICONTROL Users]** per specificare una banda di query per ogni utente. È possibile aggiungere tutte le coppie chiave/valore necessarie, ad esempio priorità=1;carico di lavoro=alto. Se all&#39;utente non è assegnata alcuna banda di query, verrà applicato il campo **[!UICONTROL Default]**.

1. Selezionare la casella **[!UICONTROL Active]** per attivare questa funzione

#### Risoluzione dei problemi degli account esterni {#external-account-troubleshooting}

Se durante il test della connessione **TIM-030008 Date &#39;2&#39; viene visualizzato il seguente errore: caratteri mancanti (iRc=-53)** assicurarsi che il driver ODBC sia installato correttamente e che LD_LIBRARY_PATH (Linux) / PATH (Windows) sia impostato per il server Campaign.

Errore **ODB-240000 ODBC: [Nome origine dati Microsoft][ODBC Driver Manager] non trovato e nessun driver predefinito specificato.** si verifica con Windows se si utilizza un driver 16.X.  Adobe Campaign prevede che l&#39;teradata verrà denominato &#39;{teradata}&#39; in odbcinst.ini.

* A partire da Campaign 18.10, è possibile aggiungere ODBCDRiverName=&quot;Driver ODBC del database Teradata 16.10&quot; nelle opzioni dell&#39;account esterno. Il numero di versione può cambiare, il nome esatto può essere trovato eseguendo odbcad32.exe e l&#39;accesso alla scheda Driver.

* Se utilizzi una versione precedente di Campaign, dovrai copiare la sezione Teradata di odbcinst.ini creata dall&#39;installazione del driver in una nuova sezione denominata Teradata. In questo caso è possibile utilizzare il regedit. Se la base è in latin1, è necessario aggiungere **APICharSize=1** nelle opzioni.

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

Nel database esterno sono richiesti i seguenti diritti: creare/rilasciare/eseguire procedure personalizzate, creare/rilasciare/inserire/selezionare tabelle. È inoltre possibile che sia necessario creare funzioni di modalità utente se si desidera utilizzare le funzioni md5 e sha2 nell&#39;istanza di Adobe Campaign .

Accertatevi di configurare il fuso orario corretto. Deve corrispondere a quanto verrà impostato nell&#39;account esterno creato nell&#39;istanza di Adobe Campaign .

 Adobe Campaign non imposterà una modalità di protezione (fallback) per gli oggetti che verranno creati nel database. Potrebbe essere necessario impostare un valore predefinito per l&#39;utente che  Adobe Campaign utilizzerà per connettersi al database Teradata utilizzando la seguente query:

| disattiva fallback predefinito |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### Installazione di MD5 {#md5-installation}

Se si desidera utilizzare le funzioni md5 nell&#39;istanza di Adobe Campaign , è necessario installare la funzione modalità utente nel database Teradata da questa [pagina](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

Lo sha1 del file scaricato è il seguente 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Per installare md5:

1. Decomprimete il file md5_20080530.zip.

1. Andate alla directory md5/src.

1. Connettiti al database Teradata utilizzando bteq.

1. Eseguite il seguente comando bteq:

   ```
   .run file = hash_md5.btq
   ```

### Installazione SHA2 {#sha2-installation}

Se si desidera utilizzare le funzioni sha2 nell&#39;istanza di Adobe Campaign , è necessario installare la funzione modalità utente nel database Teradata da questa [pagina](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

Lo sha1 del file scaricato è il seguente e87438d37424836358bd3902cf1adeb629349780.

Per installare sha2:

1. Decomprimete il file teradata-udf-sha2-1.0.zip.

1. Andate alla directory teradata-udf-sha2-1.0/src.

1. Connettiti al database Teradata utilizzando bteq.

1. Eseguite i due comandi bteq seguenti:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### Installazione di UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Se si desidera utilizzare le funzioni udf_utf16to8 nell&#39;istanza di Adobe Campaign , è necessario installare la funzione modalità utente nel database Teradata dal **kit di strumenti Teradata unicode** di questa [pagina](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

Lo sha1 del file scaricato è il seguente e58235f434f52c71316a577cb48e20b97d24f470.

Per installare udf_utf16to8:

1. Decomprimete il file utk_release1.7.0.0.zip.

1. Cercate udf_utf16to8.o nei file estratti e andate alla directory che contiene il file. Deve essere denominato utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 UDFs/suselLinux-x8664/udf_install/.

1. Connettiti al database Teradata utilizzando bteq.

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
   ```

## Configurazione del server delle campagne per Linux {#campaign-server-linux}

Per l&#39;installazione del driver è necessario quanto segue:

* Driver teradata ODBC, che si trova in questa [pagina](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata Tools and Utilities (utilizzato per il caricamento di massa), che si trova in questa [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Nomi file e sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f 4fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Se non è presente alcun pacchetto per la distribuzione Linux, è possibile installare come spiegato in un CentOS 7 (ad esempio utilizzando docker) e copiare quindi il contenuto di /opt/teradata sul server Adobe Campaign .

### Installazione driver ODBC {#odbc-installation}

Per installare il driver ODBC:

1. Estrarre il file tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Andate alla directory tdodbc1620.

1. Potrebbe essere necessario correggere lo script di installazione:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Eseguire setup_wrapper.sh.

### Installazione di strumenti e utility teradata {#teradata-tools-installation}

Per installare Strumenti:

1. Estrarre il file TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Andate alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Eseguire setup_wrapper.sh.

1. Andate alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Eseguire setup_wrapper.sh.

1. Andate alla directory TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Eseguire setup_wrapper.sh.

1. Un file libtelapi.so deve essere disponibile in /opt/teradata/client/16.20/lib64.

## Configurazione del server delle campagne per Windows {#campaign-server-windows}

È innanzitutto necessario scaricare Teradata Tools e utility per Windows. È possibile scaricarlo da questa [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Installare il driver ODBC e Teradata Parallel Transporter Base. Verrà installato telapi.dll utilizzato per eseguire il caricamento in massa sul database Teradata.

Verificare che il percorso del driver e delle utility sia nella variabile PATH che nlserver avrà durante l&#39;esecuzione. Per impostazione predefinita, il percorso è C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit).

## Fuso orario {#timezone}

Teradata utilizza un nome di fuso orario non standard. È possibile trovare l&#39;elenco nel [sito Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA).  Adobe Campaign cercherà di convertire il fuso orario indicato nella configurazione esterna in qualcosa che Teradata capisce. Se non viene trovata una corrispondenza, verrà trovato il fuso orario GMT+X (o GMT-X) più chiuso per la sessione, con un avviso nel registro.

La conversione viene eseguita leggendo un file denominato teradata_timezones.txt che dovrebbe trovarsi nella seguente directory di datakit: /usr/local/neolane/nl6/datakit sotto linux. Se modifichi questo file, contatta il team Adobe Campaign  per apportare la modifica al codice sorgente, altrimenti il file verrà sovrascritto durante il prossimo aggiornamento di Campaign.

Il fuso orario utilizzato per la connessione viene indicato quando si esegue nlserver con lo switch -verbose, ad esempio:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Se il fuso orario utilizzato non è quello corretto, è possibile aggiungere un&#39;opzione denominata &quot;TimeZoneName&quot; sull&#39;account esterno. In tal caso, utilizzate il valore Teradata, ad esempio &quot;TimeZoneName=Europe Central&quot;.

Quando nei documenti Teradata viene utilizzato un carico in massa o un &quot;caricamento rapido&quot;, Campaign non è in grado di indicare il fuso orario. Pertanto, si consiglia di impostare il fuso orario predefinito per l&#39;utente che Campaign utilizzerà per connettersi:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
