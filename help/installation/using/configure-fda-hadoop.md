---
product: campaign
title: Configurare l’accesso al Hadoop
description: Scopri come configurare l’accesso al Hadoop in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 1%

---

# Configurare l&#39;accesso al Hadoop {#configure-access-to-hadoop}

Utilizza l’opzione Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi riportati di seguito per configurare l’accesso al Hadoop.

1. Configura [database di Hadoop](#configuring-hadoop)
1. Configura il Hadoop [account esterno](#hadoop-external) in Campaign

## Configurazione del Hadoop 3.0 {#configuring-hadoop}

La connessione a un database esterno di Hadoop in FDA richiede le seguenti configurazioni sul server Adobe Campaign. Questa configurazione è disponibile sia per Windows che per Linux.

1. Scaricare i driver ODBC per Hadoop a seconda della versione del sistema operativo in uso. I driver si trovano in [questa pagina](https://www.cloudera.com/downloads.html).

1. È quindi necessario installare i driver ODBC e creare un DSN per la connessione Hive. Le istruzioni sono disponibili in [questa pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A questo scopo, esegui il seguente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic puoi quindi configurare l’account esterno [!DNL Hadoop]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#hadoop-external).

## Account esterno hadoop {#hadoop-external}

L’account esterno [!DNL Hadoop] ti consente di collegare l’istanza Campaign al database esterno del Hadoop.

1. In Campaign Classic, configura l’account esterno [!DNL Hadoop]. Dal menu **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configura l’account esterno **[!UICONTROL Hadoop]** , devi specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Nome del DNS

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database se non specificato in DSN. Può essere lasciato vuoto se specificato nel DSN

   * **[!UICONTROL Time zone]**: Fuso orario server

   ![](assets/hadoop3.png)

Il connettore supporta le seguenti opzioni ODBC:

| Nome | Elemento “value” |
|---|---|
| ODBCMgr | iODBC |
| magazzino | 02/01/04 |

Il connettore supporta anche le seguenti opzioni Hive:

| Nome | Elemento “value” | Descrizione |
|---|---|---|
| bulkKey | Chiave di accesso BLOB di Azure o DataLake | Per caricatori di massa wasb:// o wasbs:// (ad esempio se lo strumento di caricamento di massa inizia con wasb:// o wasbs://). <br>È la chiave di accesso per il bucket BLOB o DataLake per il caricamento in serie. |
| hdfsPort | numero di porta <br>impostato per impostazione predefinita su 8020 | Per il caricamento in serie HDFS (cioè se lo strumento di caricamento in serie inizia con webhdfs:// o webhdfss://). |
| bubenNumber | 20 | Numero di bucket durante la creazione di una tabella cluster. |
| fileFormat | PARQUET | Formato di file predefinito per le tabelle di lavoro. |


## Configurazione del Hadoop 2.1 {#configure-access-hadoop-2}

Per connettersi al Hadoop 2.1, segui i passaggi descritti di seguito per [Windows](#for-windows) o [Linux](#for-linux).

### Hadoop 2.1 per Windows {#for-windows}

1. Installa i driver ODBC e [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) per Windows.
1. Creare il DSN (Data Source Name) eseguendo lo strumento Amministratore origine dati ODBC. È disponibile un esempio DSN di sistema per Hive da modificare.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Crea l&#39;account esterno del Hadoop, come descritto in [questa sezione](#hadoop-external).

### Hadoop 2.1 per Linux {#for-linux}

1. Installa unixodbc per Linux.

   ```
   apt-get install unixodbc
   ```

1. Scarica e installa driver ODBC per Apache Hive da HortonWorks: [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Controllare la posizione dei file ODBC.

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

1. Crea il DSN (Data Source Name) e modifica il file odbc.ini. Quindi, crea un DSN per la tua connessione Hive.

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
   >Il parametro **UseNativeQuery** qui è molto importante. Campaign riconosce Hive e non funziona correttamente se non è impostato UseNativeQuery. In genere, il driver o il connettore Hive SQL riscriveranno le query e manometteranno l&#39;ordine delle colonne.

   La configurazione dell&#39;autenticazione dipende dalla configurazione Hive/Hadoop. Ad esempio, per HD Insight, utilizza AuthMech=6 per l&#39;autenticazione utente/password, come descritto [qui](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Esporta le variabili.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Imposta i driver Hortonworks tramite /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   Devi utilizzare UTF-16 per connettersi con Campaign e unix-odbc (libodbcinst).

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

1. Crea l&#39;account esterno del Hadoop, come descritto in [questa sezione](#hadoop-external).
