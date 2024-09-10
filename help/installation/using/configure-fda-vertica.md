---
product: campaign
title: Configurare l’accesso a [!DNL Vertica Analytics]
description: Scopri come configurare l’accesso a  [!DNL Vertica Analytics]  in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Configura l&#39;accesso a [!DNL Vertica Analytics] {#configure-fda-vertica}



Utilizza l&#39;opzione **Federated Data Access** (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Per configurare l&#39;accesso a [!DNL Vertica Analytics], eseguire la procedura seguente.

1. Configura [!DNL Vertica Analytics] in [CentOS](#vertica-centos), [Windows](#vertica-windows) o [Debian](#vertica-debian)
1. Configura l&#39;[!DNL Vertica Analytics] [account esterno](#vertica-external) in Campaign

![](assets/snowflake_3.png)

## [!DNL Vertica Analytics] su CentOS {#vertica-centos}

Per configurare [!DNL Vertica Analytics] su CentOS, eseguire la procedura seguente:

1. Scaricare i driver ODBC per [!DNL Vertica Analytics]. [Fare clic qui](https://www.vertica.com/download/vertica/client-drivers/) e scaricare il più recente RPM Linux.

1. È quindi necessario installare unixODBC con il seguente comando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Se in precedenza è stato installato il server [!DNL Vertica Analytics], verrà già installato un driver ODBC. In questo caso, aggiornare l&#39;unità come segue:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [VerVertica Analyticstica]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. In Adobe Campaign, puoi quindi configurare l&#39;account esterno [!DNL Vertica Analytics]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#vertica-external).

## [!DNL Vertica Analytics] su Windows {#vertica-windows}

1. Scarica il driver [ODBC per Windows](https://www.vertica.com/download/vertica/client-drivers/). Per installare il driver per Windows, è necessario attivare .NET Framework 3.5 oppure l&#39;Assistente all&#39;installazione tenterà di attivarlo e scaricarlo automaticamente.

1. Configurare il driver ODBC in Windows. Per ulteriori informazioni, consulta [questa pagina](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign, puoi quindi configurare l&#39;account esterno [!DNL Vertica Analytics]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#vertical-external).

## [!DNL Vertica Analytics] su Debian {#vertica-debian}

1. Scaricare i driver ODBC per [!DNL Vertica Analytics]. [Fai clic qui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) per iniziare a scaricare.

1. È quindi necessario installare unixODBC con il seguente comando:

   ```
   apt-get install unixODBC
   ```

1. Se in precedenza è stato installato il server [!DNL Vertica Analytics], verrà già installato un driver ODBC. In questo caso, aggiornare l&#39;unità come segue:

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [Vertica Analytics]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. In Adobe Campaign, puoi quindi configurare l&#39;account esterno [!DNL Vertica Analytics]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#vertica-external).

## Account esterno [!DNL Vertica Analytics] {#vertica-external}

È necessario creare un account esterno [!DNL Vertica Analytics] per collegare l&#39;istanza Campaign al database esterno [!DNL Vertica Analytics].

1. Dalla campagna **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come **[!UICONTROL Type]** del tuo account esterno.

1. Configurare l&#39;account esterno **[!UICONTROL Vertica Analytics]**. È necessario specificare:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL del server [!DNL Vertica Analytics]

   * **[!UICONTROL Account]**: nome dell&#39;utente

   * **[!UICONTROL Password]**: password dell&#39;account utente

   * **[!UICONTROL Database]**: nome del database

   ![](assets/vertica.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| TimeZoneName | Per impostazione predefinita, questo significa che viene utilizzato il fuso orario del server app di Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. |

