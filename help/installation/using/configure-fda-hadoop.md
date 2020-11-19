---
title: Configurare l'accesso ad Hadoop
description: Scoprite come configurare l'accesso ad Hadoop in FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: acb505fac39222e53a3acab6b5c93d10c9d11ba8
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# Configurare l&#39;accesso ad Hadoop {#configure-access-to-hadoop}

Utilizzate l&#39;opzione Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguite i passaggi riportati di seguito per configurare l&#39;accesso ad Hadoop.

1. Configurare il database [Hadoop](#configuring-hadoop)
1. Configurare l&#39;account [](#hadoop-external) esterno Hadoop in Campaign

## Configurazione di Hadoop 3.0 {#configuring-hadoop}

La connessione a un database esterno Hadoop in FDA richiede le seguenti configurazioni sul server Adobe Campaign . Questa configurazione è disponibile per Windows e Linux.

1. Scaricate i driver ODBC per Hadoop a seconda della versione del sistema operativo in uso. I driver si trovano in [questa pagina](https://www.cloudera.com/downloads.html).

1. È quindi necessario installare i driver ODBC e creare un DSN per la connessione Hive. Le istruzioni sono disponibili in [questa pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare il Campaign Classic. A questo scopo, eseguite il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Hadoop] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta [questa sezione](#hadoop-external).

## Account esterno hadoop {#hadoop-external}

L&#39;account [!DNL Hadoop] esterno consente di collegare l&#39;istanza Campaign al database esterno di Hadoop.

1. In Campaign Classic, configura il tuo account [!DNL Hadoop] esterno. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

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


## Configurazione di Hadoop 2.1 {#configure-access-hadoop-2}

Se dovete connettervi ad Hadoop 2.1, seguite i passaggi descritti di seguito per [Windows](#for-windows) o [Linux](#for-linux).

### Hadoop 2.1 per Windows {#for-windows}

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

1. Create l&#39;account esterno Hadoop, come illustrato in [questa sezione](#hadoop-external).

### Hadoop 2.1 per Linux {#for-linux}

1. Installate unixodbc per Linux.

   ```
   apt-get install unixodbc
   ```

1. Scaricare e installare driver ODBC per Apache Hive da HortonWorks: [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html).

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

1. Create l&#39;account esterno Hadoop, come illustrato in [questa sezione](#hadoop-external).

