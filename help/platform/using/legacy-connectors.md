---
title: Connettori precedenti
seo-title: Connettori precedenti
description: Connettori precedenti
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# Connettori precedenti {#legacy-connectors}

I connettori FDA precedenti sono ancora supportati  Adobe. Tuttavia, si consiglia di sostituirli con alternative più recenti elencate in questa [pagina](../../platform/using/specific-configuration-database.md).

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

La connessione a un database esterno Netezza in FDA richiede configurazioni aggiuntive nel server Adobe Campaign :

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

1. Specificate le variabili di ambiente del server Adobe Campaign :

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib e /usr/local/nz/lib64. &quot;/usr/local/nz&quot; corrisponde al repository di installazione offerto per impostazione predefinita durante l&#39;installazione dei driver. Qui è necessario specificare il repository selezionato per l&#39;installazione.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: posizione del file odbc.ini. Netezza richiede anche questa seconda variabile per utilizzare il file odbc.ini.

1. In Campaign Classic, potete quindi configurare il vostro account Netezza esterno. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

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

## Configurare l&#39;accesso a Sybase IQ {#configure-access-to-sybase-iq}

La connessione a un database esterno Sybase IQ in FDA richiede configurazioni aggiuntive nel server Adobe Campaign :

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

1. In Campaign Classic, puoi quindi configurare il tuo account esterno Sybase IQ. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL Sybase IQ]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Corrisponde alla connessione ODBC (`<server_alias>`) definita al punto 5. Non necessariamente il nome del server stesso.

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

>[!NOTE]
>
>Per Windows, è necessario installare il client Sybase IQ sul server Adobe Campaign  e creare una connessione ODBC. Assicurarsi di creare un&#39;origine dati di sistema quando il server Adobe Campaign  (nlserver) è in esecuzione come servizio in Windows.

## Configurare l&#39;accesso a Teradata {#configure-access-to-teradata}

La connessione a un database esterno Teradata in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign . Per ulteriori informazioni su come configurare il database Teradata, consulta questa [pagina](../../platform/using/appendices-fda.md#teradata-configuration).

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

1. Specificate le variabili di ambiente del server Adobe Campaign :

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 e /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NLSPATH**: posizione del file opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

1. In Campaign Classic, puoi quindi configurare il tuo account esterno Teradata. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL Teradata]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: Teradata

   * **[!UICONTROL Server]**: URL del server Teradata

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

## Configurare l&#39;accesso a SAP HANA {#configure-access-to-sap-hana}

La connessione a un database esterno SAP HANA in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign :

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

1. Specificate le variabili di ambiente del server Adobe Campaign :

   * **LD_LIBRARY_PATH**: Deve includere il collegamento al client SAP Hana (per impostazione predefinita, /usr/sap/hdbclient/libodbcHDB.so).
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).

1. In Campaign Classic, puoi quindi configurare il tuo account esterno SAP Hana. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL SAP Hana]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del server SAP Hana

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente
