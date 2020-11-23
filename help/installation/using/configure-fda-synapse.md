---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso a Synapse
description: Scoprite come configurare l'accesso a Synapse in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---


# Configurare l&#39;accesso a  Azure synapse {#configure-access-to-azure-synapse}

Utilizzate l&#39;opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguite i passaggi riportati di seguito per configurare l&#39;accesso a Microsoft  Azure synapse Analytics.

1. Configurare  Azure synapse su [CentOS](#azure-centos), [Windows](#azure-windows) o [Debian](#azure-debian)
1. Configurare l&#39;account [](#azure-external) esterno  Azure synapse in Campaign

##  Azure synapse su CentOS {#azure-centos}

>[!CAUTION]
>
>* Per installare un driver ODBC è necessario disporre dei privilegi di root.
>* I driver ODBC Red Hat Enterprise forniti da Microsoft possono essere utilizzati anche con CentOS per connettersi a SQL Server.
>* La versione 13.0 funziona con Red Hat 6 e 7.


Per configurare  Azure synapse su CentOS, attenetevi alla procedura seguente:

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

1. In Campaign, puoi quindi configurare il tuo account [!DNL Azure Synapse] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta [questa sezione](#azure-external).

1. Poiché  Azure synapse Analytics comunica attraverso la porta TCP 1433, è necessario aprire questa porta sul firewall. Usa il comando seguente:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Per consentire la comunicazione da  lato di Azure synapse Analytics, potrebbe essere necessario aggiungere l&#39;IP pubblico al inserire nell&#39;elenco Consentiti di . A tal fine, fare riferimento alla documentazione [di](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)Azure.

1. Nel caso di iptables, eseguire il comando seguente:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

##  Azure synapse in Windows {#azure-windows}

>[!NOTE]
>
>Questa funzione è esclusiva della versione 13 del driver ODBC, ma Adobe Campaign Classic può anche utilizzare i driver client nativi di SQL Server 11.0 e 10.0.

Per configurare  Azure synapse in Windows:

1. Innanzitutto, installare il driver Microsoft ODBC. Potete trovarlo in [questa pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Scegliete i file seguenti da installare:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Una volta installato il driver ODBC, è possibile verificarlo se necessario. Per ulteriori informazioni, consulta questa [pagina](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Azure Synapse] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta [questa sezione](#azure-external).

1. Poiché  Azure synapse Analytics comunica attraverso la porta TCP 1433, è necessario aprire questa porta su Windows Defender Firewall. For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

##  Azure synapse su Debian {#azure-debian}

**Prerequisiti:**

* Per installare un driver ODBC è necessario disporre dei privilegi di root.
* Curl è necessario per installare il pacchetto msobcsql. Se non è installato, eseguite il comando seguente:

   ```
   sudo apt-get install curl
   ```

Per configurare  Azure synapse su Debian:

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

1. In Campaign Classic, ora puoi configurare il tuo account [!DNL Azure Synapse] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta [questa sezione](#azure-external).

1. Per configurare iptables su Debian per garantire la connessione con  Azure synapse Analytics, abilita la porta TCP 1433 in uscita per il tuo nome host con il seguente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Per consentire la comunicazione da  lato di Azure synapse Analytics, potrebbe essere necessario aggiungere l&#39;IP pubblico al inserire nell&#39;elenco Consentiti di . A tal fine, fare riferimento alla documentazione [di](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)Azure.


##  account esterno Azure synapse {#azure-external}

L&#39;account [!DNL Azure Synapse] esterno consente di collegare l&#39;istanza Campaign al database esterno  Azure synapse.

Per creare un account [!DNL Azure Synapse] esterno, effettuate le seguenti operazioni:

1. Da Campaign **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Selezionate **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

   ![](assets/azure_1.png)

1. Configurate l&#39;account [!DNL Azure Synapse] esterno, dovete specificare:

   * **[!UICONTROL Type]**:  Azure synapse Analytics

   * **[!UICONTROL Server]**: URL del server Azure synapse 

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

