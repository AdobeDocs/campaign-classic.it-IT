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
source-git-commit: 4f1f1cd9c5ebb77fbb01cadad6c587ed2fe64dcc
workflow-type: tm+mt
source-wordcount: '1835'
ht-degree: 0%

---


# Configurazioni specifiche per tipo di database {#specific-configurations-by-database-type}

A seconda dei database esterni a cui si desidera accedere da  Adobe Campaign, sarà necessario eseguire determinate configurazioni specifiche. Tali configurazioni prevedono essenzialmente l&#39;installazione di driver e la dichiarazione di variabili di ambiente appartenenti a ciascun RDBMS sul server di Adobe Campaign .

Per ulteriori informazioni sui connettori legacy quali Teradata, Hadoop 2.1 o Netezza, fare riferimento a questa [pagina](../../platform/using/legacy-connectors.md).

Come regola generale, è necessario installare il livello client corrispondente nel database esterno sul server del Adobe Campaign .

>[!NOTE]
>
>Le versioni compatibili sono elencate in Matrice [compatibilità](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA)campagna.

## Configurare l&#39;accesso ad Azure Synapse {#configure-access-to-azure-synapse}

### Account esterno della sincronizzazione di Azure {#azure-external}

L&#39;account [!DNL Azure] esterno consente di collegare l&#39;istanza Campaign al database esterno di Azure Synapse.
Per creare un account esterno [!DNL Azure Synapse] esterno:

1. In Campaign Classic, configura il tuo account [!DNL Azure Synapse] esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clic **[!UICONTROL New]**.

1. Selezionate **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configurate l&#39;account [!DNL Azure Synapse] esterno, dovete specificare:

   * **[!UICONTROL Type]**: Azure Synapse  Analytics

   * **[!UICONTROL Server]**: URL del server Azure Synapse

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database
   ![](assets/azure_1.png)

### Azure Synapse su CentOS {#azure-centos}

**Prerequisiti:**

* Per installare un driver ODBC è necessario disporre dei privilegi di root.
* I driver ODBC Red Hat Enterprise forniti da Microsoft possono essere utilizzati anche con CentOS per connettersi a SQL Server.
* La versione 13.0 funziona con Red Hat 6 e 7.

Per configurare Azure Synapse su CentOS:

1. Innanzitutto, installare il driver ODBC. Potete trovarlo in questa [pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >Questo è esclusivo della versione 13 del driver ODBC.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. Se necessario, è possibile installare intestazioni di sviluppo univxODBC eseguendo il comando seguente:

   ```
   sudo yum install unixODBC-devel
   ```

1. Dopo aver installato i driver, è possibile verificare e verificare il driver ODBC ed eseguire una query sul database, se necessario. Eseguite il comando seguente:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Azure Synapse] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#azure-external).

1. Poiché Azure Synapse  Analytics comunica attraverso la porta TCP 1433, è necessario aprire questa porta sul firewall. Usa il comando seguente:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Per consentire la comunicazione dal lato di Azure Synapse Analytics, potrebbe essere necessario aggiungere l&#39;IP pubblico al elenco consentiti . A tal fine, fare riferimento alla documentazione [di](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)Azure.

1. Nel caso di iptables, eseguire il comando seguente:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Azure Synapse in Windows {#azure-windows}

>[!NOTE]
>
>Questa funzione è esclusiva della versione 13 del driver ODBC, ma  Adobe Campaign Classic può anche utilizzare i driver client nativi di SQL Server 11.0 e 10.0.

Per configurare Azure Synapse su Windows:

1. Innanzitutto, installare il driver Microsoft ODBC. Potete trovarlo in questa [pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Scegliete i file seguenti da installare:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Una volta installato il driver ODBC, è possibile verificarlo se necessario. For more on this, refer to this [page](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Azure Synapse] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#azure-external).

1. Poiché Azure Synapse  Analytics comunica attraverso la porta TCP 1433, è necessario aprire questa porta su Windows Defender Firewall. For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Azure Synapse su Debian {#azure-debian}

**Prerequisiti:**

* Per installare un driver ODBC è necessario disporre dei privilegi di root.
* Curl è necessario per installare il pacchetto msobcsql. Se non è installato, eseguite il comando seguente:

   ```
   sudo apt-get install curl
   ```

Per configurare Azure Synapse su Debian:

1. Innanzitutto, installate il driver Microsoft ODBC per SQL Server. Utilizzare i comandi seguenti per installare ODBC Driver 13.1 per SQL Server:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Se viene visualizzato il seguente errore **&quot;Impossibile trovare il driver del metodo /usr/lib/apt/methods/https&quot;** quando si chiama **sudo apt-get update**, eseguire il comando:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. È ora necessario installare mssql-tools con i seguenti comandi. Gli strumenti Mssq sono necessari per utilizzare l&#39;utilità del programma di copia in blocco (o BCP) e per eseguire query.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. Se necessario, è possibile installare intestazioni di sviluppo univxODBC eseguendo il comando seguente:

   ```
   sudo yum install unixODBC-devel
   ```

1. Dopo aver installato i driver, è possibile verificare e verificare il driver ODBC ed eseguire una query sul database, se necessario. Eseguite il comando seguente:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campaign Classic, ora puoi configurare il tuo account [!DNL Azure Synapse] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#azure-external).

1. Per configurare le iptables su Debian per garantire la connessione con Azure Synapse  Analytics, abilita la porta TCP 1433 in uscita per il tuo nome host con il comando seguente:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Per consentire la comunicazione dal lato di Azure Synapse Analytics, potrebbe essere necessario aggiungere l&#39;IP pubblico al elenco consentiti . A tal fine, fare riferimento alla documentazione [di](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)Azure.

## Configurare l&#39;accesso a Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] il connettore è disponibile per le distribuzioni in hosting e in sede. For more on this, refer to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Conto esterno fiocco di neve {#snowflake-external}

L&#39;account [!DNL Snowflake] esterno consente di collegare l&#39;istanza Campaign al database esterno Snowflake.

1. In Campaign Classic, configura il tuo account [!DNL Snowflake] esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clic **[!UICONTROL New]**.

1. Selezionate **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configurate l&#39;account **[!UICONTROL Snowflake]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

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

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Snowflake] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#snowflake-external).

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

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Snowflake] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snowflake on Windows {#snowflake-windows}

1. Scaricare il driver [ODBC per Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Per installare il driver, è necessario disporre dei privilegi di amministratore. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configurare il driver ODBC. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Snowflake] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#snowflake-external).

## Configurare l&#39;accesso a Hadoop 3.0 {#configure-access-to-hadoop-3}

### Account esterno Hadoop {#hadoop-external}

L&#39;account [!DNL Hadoop] esterno consente di collegare l&#39;istanza Campaign al database esterno di Hadoop.

1. In Campaign Classic, configura il tuo account [!DNL Hadoop] esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clic **[!UICONTROL New]**.

1. Selezionate **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configurate l&#39;account **[!UICONTROL Hadoop]** esterno, dovete specificare:

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

### Configurazione di Hadoop 3.0 {#configuring-hadoop}

La connessione a un database esterno Hadoop in FDA richiede le seguenti configurazioni sul server del Adobe Campaign . Questa configurazione è disponibile per Windows e Linux.

1. Scaricate i driver ODBC per Hadoop a seconda della versione del sistema operativo in uso. I driver si trovano in [questa pagina](https://www.cloudera.com/downloads.html).

1. È quindi necessario installare i driver ODBC e creare un DSN per la connessione Hive. Le istruzioni sono disponibili in [questa pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A questo scopo, eseguite il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Hadoop] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#hadoop-external).

## Configurare l&#39;accesso a Oracle {#configure-access-to-oracle}

### Conto esterno Oracle {#oracle-external}

L&#39;account [!DNL Oracle] esterno consente di collegare l&#39;istanza Campaign al database esterno di Hadoop.

1. In Campaign Classic, configura il tuo account [!DNL oracle] esterno. Dal **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clic **[!UICONTROL New]**.

1. Selezionate **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configurate l&#39;account **[!UICONTROL Oracle]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Nome del DNS

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Time zone]**: Fuso orario server
   ![](assets/oracle_config.png)

### Oracle su Linux {#for-linux-1}

La connessione a un database Oracle esterno in FDA richiede configurazioni aggiuntive nel server del Adobe Campaign .

1. Installare il client completo Oracle corrispondente alla versione di Oracle in uso.
1. Aggiungete le definizioni TNS all&#39;installazione. Per eseguire questa operazione, specificateli in un file **tnsnames.ora** nell&#39;archivio /etc/oracle. Se il repository non esiste, crearlo.

   Quindi create una nuova variabile di ambiente TNS_ADMIN: esportare TNS_ADMIN=/etc/oracle e riavviare il computer.

1. Integrare Oracle nel server del Adobe Campaign  (nlserver). A questo scopo, verificate che il file **customer.sh** sia presente nella cartella &quot;nl6&quot; della struttura ad albero del server di Adobi Campaign  e che includa i collegamenti alle librerie Oracle.

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

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Oracle] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#oracle-external).

### Oracle su Windows {#for-windows-1}

La connessione a un database Oracle esterno in FDA richiede configurazioni aggiuntive nel server del Adobe Campaign .

1. Installare il client Oracle.

1. Nella cartella C:Oracle, create un file **tnsnames.ora** contenente la definizione TNS.

1. Aggiungere una variabile di ambiente TNS_ADMIN con C:Oracle come valore e riavviare il computer.

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Oracle] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta questa [sezione](../../platform/using/specific-configuration-database.md#oracle-external).