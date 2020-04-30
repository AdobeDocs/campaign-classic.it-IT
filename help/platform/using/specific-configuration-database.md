---
title: Accesso a un database esterno
seo-title: Accesso a un database esterno
description: Accesso a un database esterno
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 04684fd2933ef19a8ebfd6cbe77e78a34c66ffe3

---


# Configurazioni specifiche per tipo di database {#specific-configurations-by-database-type}

A seconda dei database esterni a cui si desidera accedere da Adobe Campaign, sarà necessario eseguire determinate configurazioni specifiche. Tali configurazioni prevedono essenzialmente l&#39;installazione di driver e la dichiarazione di variabili di ambiente appartenenti a ciascun RDBMS sul server Adobe Campaign.

Come regola generale, devi installare il livello client corrispondente nel database esterno sul server Adobe Campaign.

>[!NOTE]
>
>Le versioni compatibili sono elencate in Matrice [compatibilità](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA)campagna.

<!--
## Configure access to Azure Synapse {#configure-access-to-azure-synapse}

### Azure Synapse on CentOS {#azure-centos}

1. Download mysql57-community-release.noarch.rpm. You can find it in this [page](https://dev.mysql.com/downloads/repo/yum).

1. Install the client library:

    ```
    $ yum install mysql57-community-release-el7-9.noarch.rpm
    $ yum install mysql-community-libs
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Debian {#azure-debian}

1. Download mysql-apt-config.deb. You can find it in this [page](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

1. Install the client library:

    ```
    $ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
    $ apt update
    $ apt install libmysqlclient20
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Windows {#azure-windows}

1. Download the C connector. You can find it in this [page](https://dev.mysql.com/downloads/connector/c).

1. Make sure the directory that contains libmysqlclient.dll is added to the PATH environment variable that nlserver will use.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

-->

## Configurare l&#39;accesso a Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] il connettore è disponibile per le distribuzioni in hosting e in sede. For more on this, refer to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Fiocco di neve su CentOS {#snowflake-centos}

1. Scaricare i driver ODBC per [!DNL Snowflake]. [Fate clic qui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) per iniziare a scaricare.
1. È quindi necessario installare i driver ODBC su CentOs con il seguente comando:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A questo scopo, eseguite il comando seguente:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. In Campaign Classic potete quindi configurare l&#39;account [!DNL Snowflake] esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Selezionate l’account **[!UICONTROL Snowflake]** esterno incorporato.

1. Configurate l&#39;account **[!UICONTROL Snowflake]** esterno, dovete specificare:

   * **[!UICONTROL Server]**: URL del [!DNL Snowflake] server

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database
   ![](assets/snowflake.png)

1. Fare clic sulla **[!UICONTROL Parameters]** scheda e quindi sul **[!UICONTROL Deploy functions]** pulsante per creare le funzioni.

   ![](assets/snowflake_2.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| schema di lavoro | Schema del database da utilizzare per le tabelle di lavoro |
| warehouse | Nome del magazzino predefinito da utilizzare. Sostituirà l&#39;impostazione predefinita dell&#39;utente. |
| TimeZoneName | Per impostazione predefinita vuota, ovvero viene utilizzato il fuso orario del sistema del server app Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | parametro di sessione WEEK_START. Per impostazione predefinita, è impostato su 0. <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | parametro di sessione USE_CACHED_RESULTS. Per impostazione predefinita, è impostato su TRUE. Questa opzione può essere utilizzata per disattivare i risultati di Snowflake memorizzati nella cache. <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Fiocco di neve su Debian {#snowflake-debian}

1. Scaricare i driver ODBC per [!DNL Snowflake]. [Fai clic qui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) per iniziare a scaricare.

1. È quindi necessario installare i driver ODBC su Debian con il seguente comando:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A questo scopo, eseguite il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic potete quindi configurare l&#39;account [!DNL Snowflake] esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Selezionate l’account **[!UICONTROL Snowflake]** esterno incorporato.

1. Per configurare l&#39;account **[!UICONTROL Snowflake]** esterno, dovete specificare:

   * **[!UICONTROL Server]**: URL del [!DNL Snowflake] server

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database
   ![](assets/snowflake.png)

1. Fare clic sulla **[!UICONTROL Parameters]** scheda e quindi sul **[!UICONTROL Deploy functions]** pulsante per creare le funzioni.

   ![](assets/snowflake_2.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| schema di lavoro | Schema del database da utilizzare per le tabelle di lavoro |
| warehouse | Nome del magazzino predefinito da utilizzare. Sostituirà l&#39;impostazione predefinita dell&#39;utente. |
| TimeZoneName | Per impostazione predefinita vuota, ovvero viene utilizzato il fuso orario del sistema del server app Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | parametro di sessione WEEK_START. Per impostazione predefinita, è impostato su 0.  <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | parametro di sessione USE_CACHED_RESULTS. Per impostazione predefinita, è impostato su TRUE. Questa opzione può essere utilizzata per disattivare i risultati di Snowflake memorizzati nella cache. <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Snowflake on Windows {#snowflake-windows}

1. Scaricare il driver [ODBC per Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Per installare il driver, è necessario disporre dei privilegi di amministratore. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configurare il driver ODBC. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign Classic potete quindi configurare l&#39;account [!DNL Snowflake] esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Selezionate l’account **[!UICONTROL Snowflake]** esterno incorporato.

1. Per configurare l&#39;account **[!UICONTROL Snowflake]** esterno, dovete specificare:

   * **[!UICONTROL Server]**: URL del [!DNL Snowflake] server

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database
   ![](assets/snowflake.png)

1. Fare clic sulla **[!UICONTROL Parameters]** scheda e quindi sul **[!UICONTROL Deploy functions]** pulsante per creare le funzioni.

   ![](assets/snowflake_2.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|---|
| schema di lavoro | Schema del database da utilizzare per le tabelle di lavoro |
| warehouse | Nome del magazzino predefinito da utilizzare. Sostituirà l&#39;impostazione predefinita dell&#39;utente. |
| TimeZoneName | Per impostazione predefinita vuota, ovvero viene utilizzato il fuso orario del sistema del server app Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | parametro di sessione WEEK_START. Per impostazione predefinita, è impostato su 0. <br>Per ulteriori informazioni, consultare [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | Per impostazione predefinita, è impostato su TRUE. Questa opzione può essere utilizzata per disabilitare i risultati della fiocco di neve memorizzati nella cache (parametro di sessione USE_CACHED_RESULTS) <br>Per ulteriori informazioni, consultate [questa pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

## Configurare l&#39;accesso a Hadoop 3.0 {#configure-access-to-hadoop-3}

La connessione a un database esterno Hadoop in FDA richiede le seguenti configurazioni sul server Adobe Campaign. Questa configurazione è disponibile per Windows e Linux.

1. Scaricate i driver ODBC per Hadoop a seconda della versione del sistema operativo in uso. I driver si trovano in [questa pagina](https://www.cloudera.com/downloads.html).

1. È quindi necessario installare i driver ODBC e creare un DSN per la connessione Hive. Le istruzioni sono disponibili in [questa pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A questo scopo, eseguite il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic potete quindi configurare l&#39;account esterno Snowflake. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic su **[!UICONTROL Create]** e selezionate **[!UICONTROL External database]** come tipo di account.

1. Per configurare l’account **[!UICONTROL  Hadoop]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Nome del DNS

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database se non specificato in DSN. Può essere lasciato vuoto se specificato nel DSN

   * **[!UICONTROL Time zone]**: Fuso orario server
   ![](assets/hadoop3.png)

Il connettore supporta le seguenti opzioni ODBC:

| Nome | Valore |
|---|---|
| ODBCMgr | iODBC |
| warehouse | 1/2/4 |

Il connettore supporta anche le seguenti opzioni Hive:

| Nome | Valore | Descrizione |
|---|---|---|
| bulkKey | BLOB di Azure o chiave di accesso DataLake | Per wasb:// o wasbs:// caricatori di massa (ad es. se lo strumento di caricamento di massa inizia con wasb:// o wasbs://). <br>È la chiave di accesso per il blob o DataLake bucket per il caricamento di massa. |
| hdfsPort | numero di porta <br>impostato per impostazione predefinita su 8020 | Per il carico in massa HDFS (ad esempio, se lo strumento di caricamento in blocco inizia con webhdfs:// o webhdfss://). |
| buketsNumber | 20 | Numero di bucket durante la creazione di una tabella cluster. |
| fileFormat | PARQUET | Formato file predefinito per le tabelle di lavoro. |

## Configurare l&#39;accesso a Hadoop 2.1 {#configure-access-to-hadoop}

### Per Windows {#for-windows}

1. Installare i driver ODBC e [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) per Windows.
1. Creare il DSN (Nome origine dati) eseguendo lo strumento Amministratore origine dati ODBC. È disponibile un esempio DSN di sistema per Hive da modificare.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Create l&#39;account esterno Hadoop, come illustrato in [questa sezione della pagina](../../platform/using/external-accounts.md#hadoop-external-account) .

### Per Linux {#for-linux}

1. Installate unixodbc per Linux.

   ```
   apt-get install unixodbc
   ```

1. Scaricare e installare driver ODBC per Apache Hive da HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Controllare il percorso dei file ODBC.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Create il DSN (Nome origine dati) e modificate il file odbc.ini. Quindi, create un DSN per la connessione Hive.

   Di seguito è riportato un esempio per HDInsight per impostare una connessione denominata &quot;viral&quot;:

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >Il parametro **UseNativeQuery** è molto importante. Campaign è consapevole dell&#39;Hive e non funzionerà correttamente se non viene impostato UseNativeQuery. In genere, il driver o il connettore Hive SQL riscrive le query e altera l&#39;ordine delle colonne.

   La configurazione dell&#39;autenticazione dipende dalla configurazione Hive/Hadoop. Ad esempio, per HD Insight, utilizzate AuthMech=6 per l’autenticazione utente/password, come descritto [qui](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Esportare le variabili.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Impostare i driver di Hortonworks tramite /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   Devi usare UTF-16 per poter connettersi con Campaign e unix-odbc (libodbcinst).

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. È ora possibile verificare la connessione utilizzando isql.

   ```
   isql vorac
   isql vorac -v
   ```

1. Create l&#39;account esterno Hadoop, come illustrato in [questa sezione della pagina](../../platform/using/external-accounts.md#hadoop-external-account) .

## Configurare l&#39;accesso a Netezza {#configure-access-to-netezza}

La connessione a un database esterno di Netezza in FDA richiede configurazioni aggiuntive nel server di Adobe Campaign:

1. Installare i driver ODBC per Netezza, in base al sistema operativo utilizzato:

   * **nz-linuxclient-v7.2.0.0.tar.gz** per Linux. Selezionate la cartella che corrisponde al sistema operativo in uso (linux o linux64) e avviate il comando di rimozione del pacchetto. È possibile lasciare l&#39;installazione da eseguire nella directory archivio suggerita per impostazione predefinita: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** per Windows. Decomprimete il file e avviate lo script eseguibile corrispondente al sistema operativo in uso: nzodbcsetup.exe o nzodbcsetup64.exe. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: **/etc/odbc.ini** per i parametri generali e **/etc/odbcinst.ini** per la dichiarazione dei driver.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; corrisponde alla posizione del file odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Specifica le variabili di ambiente del server Adobe Campaign:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib e /usr/local/nz/lib64. &quot;/usr/local/nz&quot; corrisponde al repository di installazione offerto per impostazione predefinita durante l&#39;installazione dei driver. Qui è necessario specificare il repository selezionato per l&#39;installazione.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: posizione del file odbc.ini. Netezza richiede anche questa seconda variabile per utilizzare il file odbc.ini.

1. In Campaign Classic potete quindi configurare il vostro account Netezza esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL Netezza]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL del server Netezza

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

>[!NOTE]
>
>Non vengono prese in considerazione le operazioni sugli schemi contenenti chiavi primarie generate automaticamente.
>
>Nella tabella verrà utilizzata la clausola **Organizza su** sul primo indice definito nello schema. Poiché questa clausola è limitata a 1-4 colonne con Netezza, l&#39;indice non può contenere più di 4 colonne.

## Configurare l&#39;accesso a Oracle {#configure-access-to-oracle}

La connessione a un database Oracle esterno in FDA richiede configurazioni aggiuntive nel server Adobe Campaign.

### Per Linux {#for-linux-1}

1. Installare il client completo Oracle corrispondente alla versione di Oracle in uso.
1. Aggiungete le definizioni TNS all&#39;installazione. Per eseguire questa operazione, specificateli in un file **tnsnames.ora** nell&#39;archivio /etc/oracle. Se il repository non esiste, crearlo.

   Quindi create una nuova variabile di ambiente TNS_ADMIN: esportare TNS_ADMIN=/etc/oracle e riavviare il computer.

1. Integrare Oracle nel server Adobe Campaign (nlserver). A tal fine, verificate che il file **customer.sh** sia presente nella cartella &quot;nl6&quot; della struttura ad albero del server Adobe Campaign e che includa i collegamenti alle librerie Oracle.

   Ad esempio, per un client nella versione 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Questi valori (in particolare ORACLE_HOME) dipendono dai repository di installazione. Prima di fare riferimento a tali valori, verificate la struttura ad albero.

1. Installare le librerie necessarie per Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

### Per Windows {#for-windows-1}

1. Installare il client Oracle.
1. Nella cartella C:Oracle, create un file **tnsnames.ora** contenente la definizione TNS.

   Aggiungere una variabile di ambiente TNS_ADMIN con C:Oracle come valore e riavviare il computer.

## Configurare l&#39;accesso a Sybase IQ {#configure-access-to-sybase-iq}

La connessione a un database esterno Sybase IQ in FDA richiede configurazioni aggiuntive nel server Adobe Campaign:

1. Verificate che il pacchetto unixodbc sia sul server.
1. Installate **iq_odbc**. Un errore può verificarsi alla fine dell&#39;installazione. Questo errore può essere ignorato.
1. Installate **iq_client_common**. Alla fine dell&#39;installazione può verificarsi un errore Java. Questo errore può essere ignorato.
1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: /etc/odbc.ini per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver:

   * **/etc/odbc.ini** (sostituite valori come `<server_alias>` caratteri personalizzati):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Aggiungete il percorso della nuova libreria libodbc16.so nella variabile LD_LIBRARY_PATH. A tale scopo:

   * Se utilizzi un file customer.sh per dichiarare il percorso: aggiungete il percorso /opt/sybase/IQ-16_0/lib64 per la variabile LD_LIBRARY_PATH.
   * In caso contrario, utilizzare un comando Unix.

1. In Campaign Classic, puoi quindi configurare il tuo account esterno Sybase IQ. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL Sybase IQ]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Corrisponde alla connessione ODBC (`<server_alias>`) definita al punto 5. Non necessariamente il nome del server stesso.

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

>[!NOTE]
>
>Per Windows, devi installare il client IQ Sybase sul server Adobe Campaign e creare una connessione ODBC. Assicurati di creare un&#39;origine dati di sistema quando il server Adobe Campaign (nlserver) è in esecuzione come servizio in Windows.

## Configurare l&#39;accesso a Teradata {#configure-access-to-teradata}

La connessione a un database esterno Teradata in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign. Per ulteriori informazioni su come configurare il database Teradata, consulta questo [articolo](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html).

1. Installare il driver [ODBC per Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

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

      &quot;InstallDir&quot; corrisponde alla posizione del file **odbcinst.ini** .

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

1. In Campaign Classic, puoi quindi configurare il tuo account esterno Teradata. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL Teradata]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: Teradata

   * **[!UICONTROL Server]**: URL del server Teradata

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

## Configurare l&#39;accesso a SAP HANA {#configure-access-to-sap-hana}

La connessione a un database esterno SAP HANA in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign:

1. Installare i driver ODBC per SAP HANA, in base al sistema operativo utilizzato:

   * **hdb_client_linux.tgz** per Linux. Una volta decompresso, avviate il comando hdbinst e seguite le istruzioni per completare l&#39;installazione dei driver.
   * **hdb_client_windows.zip** per Windows. Decomprimete il file e avviate il file eseguibile: **hdbinst.exe**. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: /etc/odbc.ini per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; corrisponde alla posizione del file **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Specifica le variabili di ambiente del server Adobe Campaign:

   * **LD_LIBRARY_PATH**: Deve includere il collegamento al client SAP Hana (per impostazione predefinita, /usr/sap/hdbclient/libodbcHDB.so).
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).

1. In Campaign Classic puoi quindi configurare il tuo account esterno SAP Hana. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL SAP Hana]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del server SAP Hana

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente
