---
product: campaign
title: Configurare l’accesso al Hadoop
description: Scopri come configurare l’accesso al Hadoop in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 1%

---

# Configurare l’accesso al Hadoop {#configure-access-to-hadoop}



Utilizzare Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso al Hadoop.

1. Configura [database di hadoop](#configuring-hadoop)
1. Configurare il Hadoop [account esterno](#hadoop-external) in Campaign

## Configurazione di Hadoop 3.0 {#configuring-hadoop}

La connessione a un database esterno di Hadoop in FDA richiede le seguenti configurazioni sul server Adobe Campaign. Questa configurazione è disponibile sia per Windows che per Linux.

1. Scaricare i driver ODBC per il Hadoop a seconda della versione del sistema operativo in uso. I driver sono disponibili su [questa pagina](https://www.cloudera.com/downloads.html).

1. È quindi necessario installare i driver ODBC e creare un DSN per la connessione Hive. Le istruzioni sono reperibili in [questa pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A tale scopo, eseguire il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic, puoi quindi configurare i [!DNL Hadoop] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#hadoop-external).

## Account esterno hadoop {#hadoop-external}

Il [!DNL Hadoop] l’account esterno ti consente di collegare l’istanza Campaign al database esterno del Hadoop.

1. In Campaign Classic, configura il tuo [!DNL Hadoop] account esterno. Dalla sezione **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come dell’account esterno **[!UICONTROL Type]**.

1. Configurare **[!UICONTROL Hadoop]** account esterno, è necessario specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: nome del DNS

   * **[!UICONTROL Account]**: nome dell’utente

   * **[!UICONTROL Password]**: password dell’account utente

   * **[!UICONTROL Database]**: nome del database, se non specificato nel DSN. Può essere lasciato vuoto se specificato nel DSN

   * **[!UICONTROL Time zone]**: fuso orario del server

   ![](assets/hadoop3.png)

Il connettore supporta le seguenti opzioni ODBC:

| Nome | Elemento “value” |
|---|---|
| ODBCMgr | iODBC |
| data warehouse | 04/02 |

Il connettore supporta anche le seguenti opzioni Hive:

| Nome | Elemento “value” | Descrizione |
|---|---|---|
| bulkKey | BLOB di Azure o chiave di accesso DataLake | Per i caricatori bulk wasb:// o wasbs:// (ad esempio, se lo strumento di caricamento bulk inizia con wasb:// o wasbs://). <br>È la chiave di accesso per il bucket BLOB o DataLake per il caricamento in blocco. |
| hdfsPort | numero di porta <br>impostato per impostazione predefinita su 8020 | Per il caricamento bulk HDFS (ad esempio se lo strumento di caricamento bulk inizia con webhdfs:// o webhdfss://). |
| bucketNumber | 20 | Numero di bucket durante la creazione di una tabella cluster. |
| fileFormat | PARQUET | Formato di file predefinito per le tabelle di lavoro. |


## Configurazione del Hadoop 2.1 {#configure-access-hadoop-2}

Se è necessario connettersi al Hadoop 2.1, procedere come segue per [Windows](#for-windows) o [Linux](#for-linux).

### Hadoop 2.1 per Windows {#for-windows}

1. Installare ODBC e [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) driver per Windows.
1. Creare il DSN (Data Source Name) eseguendo lo strumento ODBC DataSource Administrator. Un esempio di DSN di sistema per Hive è disponibile per la modifica.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Creare l’account esterno del Hadoop, come descritto in [questa sezione](#hadoop-external).

### Hadoop 2.1 per Linux {#for-linux}

1. Installa unixodbc per Linux.

   ```
   apt-get install unixodbc
   ```

1. Scarica e installa i driver ODBC per Apache Hive da HortonWorks: [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html).

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

1. Creare il DSN (Data Source Name) e modificare il file odbc.ini. Quindi, crea un DSN per la connessione Hive.

   Ecco un esempio per HDInsight per impostare una connessione chiamata &quot;virale&quot;:

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
   >Il **UseNativeQuery** Questo parametro è molto importante. Campaign riconosce l’hive e non funziona correttamente se non è impostato UseNativeQuery. In genere, il driver o il connettore SQL Hive riscrive le query e altera l&#39;ordine delle colonne.

   La configurazione dell’autenticazione dipende dalla configurazione dell’hive o del Hadoop. Ad esempio, per HD Insight, utilizza AuthMech=6 per l’autenticazione utente/password, come descritto [qui](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Esporta le variabili.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Configurare i driver Hortonworks tramite /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   Devi utilizzare UTF-16 per connetterti con Campaign e unix-odbc (libodbcinst).

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

1. Creare l’account esterno del Hadoop, come descritto in [questa sezione](#hadoop-external).
