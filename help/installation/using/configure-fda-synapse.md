---
product: campaign
title: Configurare l’accesso a Synapse
description: Scopri come configurare l’accesso a Synapse in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 59d0277a-7588-4504-94e3-50f87b60da8a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 2%

---

# Configurare l’accesso all’Azure synapse {#configure-access-to-azure-synapse}



Utilizza l&#39;opzione [Federated Data Access](../../installation/using/about-fda.md) (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Segui i passaggi seguenti per configurare l&#39;accesso a **Microsoft Azure synapse Analytics**.

1. Configura Azure synapse in [CentOS](#azure-centos), [Windows](#azure-windows) o [Debian](#azure-debian)
1. Configura l&#39;Azure synapse [account esterno](#azure-external) in Campaign

## Azure synapse su CentOS {#azure-centos}

>[!CAUTION]
>
>* Per installare un driver ODBC sono necessari i privilegi radice.
>* I driver ODBC Red Hat Enterprise forniti da Microsoft possono essere utilizzati anche con CentOS per la connessione a SQL Server.
>* La versione 13.0 funziona con Red Hat 6 e 7.

Per configurare l’Azure synapse su CentOS, effettua le seguenti operazioni:

1. Installare innanzitutto il driver ODBC. Puoi trovarlo in questa [pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >Questo è esclusivo per la versione 13 del driver ODBC.

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

1. Se necessario, è possibile installare le intestazioni di sviluppo unixODBC eseguendo il comando seguente:

   ```
   sudo yum install unixODBC-devel
   ```

1. Dopo aver installato i driver, è possibile testare e verificare il driver ODBC ed eseguire una query sul database, se necessario. Esegui il comando seguente:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campaign, puoi quindi configurare l&#39;account esterno [!DNL Azure Synapse]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#azure-external).

1. Poiché Azure synapse Analytics comunica tramite la porta TCP 1433, è necessario aprire questa porta sul firewall. Usa il comando seguente:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Per consentire la comunicazione dal lato di Analytics per l’Azure synapse, potrebbe essere necessario aggiungere l’IP pubblico al inserisco nell&#39;elenco Consentiti di. A tale scopo, fare riferimento alla [documentazione di Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. Nel caso di iptables, esegui il seguente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## Azure synapse su Windows {#azure-windows}

>[!NOTE]
>
>Questo è esclusivo per la versione 13 del driver ODBC, ma Adobe Campaign Classic può anche utilizzare i driver client nativi di SQL Server 11.0 e 10.0.

Per configurare l&#39;Azure synapse su Windows:

1. Installare innanzitutto il driver ODBC di Microsoft. Puoi trovarlo in [questa pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Scegliere i seguenti file da installare:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Una volta installato il driver ODBC, è possibile eseguirne il test, se necessario. Per ulteriori informazioni, consulta questa [pagina](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. In Campaign Classic, puoi quindi configurare l&#39;account esterno [!DNL Azure Synapse]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#azure-external).

1. Poiché Analytics di Azure synapse comunica tramite la porta TCP 1433, è necessario aprire questa porta in Windows Defender Firewall. Per ulteriori informazioni, consulta [Documentazione di Windows](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

## Azure synapse su Debian {#azure-debian}

**Prerequisiti:**

* Per installare un driver ODBC sono necessari i privilegi radice.
* Per installare il pacchetto msodbcsql è necessario Curl. Se non è installato, eseguire il comando seguente:

  ```
  sudo apt-get install curl
  ```

Per configurare l’Azure synapse su Debian:

1. Installare innanzitutto il driver ODBC di Microsoft per SQL Server. Utilizzare i comandi seguenti per installare il driver ODBC 13.1 per SQL Server:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Se si verifica l&#39;errore seguente **&quot;Impossibile trovare il driver di metodo /usr/lib/apt/methods/https&quot;** durante la chiamata all&#39;aggiornamento **sudo apt-get**, eseguire il comando:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. È ora necessario installare mssql-tools con i seguenti comandi. Gli strumenti Mssq sono necessari per utilizzare l&#39;utilità BCP (Bulk Copy Program) e per eseguire le query.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. Se necessario, è possibile installare le intestazioni di sviluppo unixODBC eseguendo il comando seguente:

   ```
   sudo yum install unixODBC-devel
   ```

1. Dopo aver installato i driver, è possibile testare e verificare il driver ODBC ed eseguire una query sul database, se necessario. Esegui il comando seguente:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campaign Classic è ora possibile configurare l&#39;account esterno [!DNL Azure Synapse]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#azure-external).

1. Per configurare iptables su Debian in modo da garantire la connessione con Analytics di Azure synapse, abilita la porta TCP 1433 in uscita per il tuo nome host con il seguente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Per consentire la comunicazione dal lato di Analytics per l’Azure synapse, potrebbe essere necessario aggiungere l’IP pubblico al inserisco nell&#39;elenco Consentiti di. A tale scopo, fare riferimento alla [documentazione di Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Azure synapse account esterno {#azure-external}

L&#39;account esterno [!DNL Azure Synapse] ti consente di collegare l&#39;istanza Campaign al database esterno dell&#39;Azure synapse.

Per creare il tuo account esterno [!DNL Azure Synapse], segui la procedura seguente:

1. Dalla campagna **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come **[!UICONTROL Type]** del tuo account esterno.

   ![](assets/azure_1.png)

1. In **[!UICONTROL Configuration]**, selezionare **[!UICONTROL Azure Synapse Analytics]** dal menu a discesa **[!UICONTROL Type]**.

   ![](assets/azure_2.png)

1. Configurare l&#39;account esterno [!DNL Azure Synapse]:

   * Per l’autenticazione standard, devi specificare:

      * **[!UICONTROL Server]**: URL del server di Azure synapse

      * **[!UICONTROL Account]**: nome dell&#39;utente

      * **[!UICONTROL Password]**: password dell&#39;account utente

      * **[!UICONTROL Database]**: nome del database

     ![](assets/azure_3.png)

   * Per l&#39;autenticazione delle identità gestite assegnate dal sistema, è necessario specificare:

      * **[!UICONTROL Server]**: URL del server di Azure synapse

      * **[!UICONTROL Database]**: nome del database

      * **[!UICONTROL Options]**: aggiungere la seguente sintassi `Authentication=ActiveDirectoryMsi`

     ![](assets/azure_4.png)

1. Fai clic su **[!UICONTROL Save]**.

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| Autenticazione | Tipo di autenticazione supportato dal connettore. Valore attualmente supportato: ActiveDirectoryMSI. </br>Per ulteriori informazioni, fare riferimento al documento [SQL](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings) (esempio di stringhe di connessione n°8). |
