---
product: campaign
title: Configurare l’accesso alle Vertiche analytics
description: Scopri come configurare l’accesso alle Vertiche analytics in FDA
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---

# Configurare l’accesso alle Vertiche analytics {#configure-fda-vertica}



Utilizzare Campaign **Federated Data Access** (FDA) opzione per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a [!DNL Vertica Analytics].

1. Configura [!DNL Vertica Analytics] su [CentOS](#vertica-centos), [Windows](#vertica-windows) o [Debian](#vertica-debian)
1. Configura le [!DNL Vertica Analytics] [account esterno](#vertica-external) in Campaign

![](assets/snowflake_3.png)

## vertiche analytics su CentOS {#vertica-centos}

Per configurare [!DNL Vertica Analytics] su CentOS, segui i passaggi seguenti:

1. Scaricare i driver ODBC per [!DNL Vertica Analytics]. [Fai clic qui](https://www.vertica.com/download/vertica/client-drivers/) e scarica l&#39;ultimo Linux RPM.

1. È quindi necessario installare unixODBC con il seguente comando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Se in precedenza è stato installato il [!DNL Vertica Analytics] Server, verrà già installato un driver ODBC. In questo caso, aggiornare l&#39;unità come segue:

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

1. In Adobe Campaign puoi quindi configurare il [!DNL Vertica Analytics] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#vertica-external).

## vertiche analytics in Windows {#vertica-windows}

1. Scarica la [Driver ODBC per Windows](https://www.vertica.com/download/vertica/client-drivers/). Per installare il driver per Windows, è necessario abilitare .NET Framework 3.5 oppure la procedura guidata di installazione tenterà di abilitarlo e scaricarlo automaticamente.

1. Configurare il driver ODBC in Windows. Per ulteriori informazioni, consulta [questa pagina](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign puoi quindi configurare il [!DNL Vertica Analytics] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#vertical-external).

## vertiche analytics su Debian {#vertica-debian}

1. Scaricare i driver ODBC per [!DNL Vertica Analytics]. [Fai clic qui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) inizia a scaricare.

1. È quindi necessario installare unixODBC con il seguente comando:

   ```
   apt-get install unixODBC
   ```

1. Se in precedenza è stato installato il [!DNL Vertica Analytics] Server, verrà già installato un driver ODBC. In questo caso, aggiornare l&#39;unità come segue:

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

1. In Adobe Campaign puoi quindi configurare il [!DNL Vertica Analytics] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#vertica-external).

## vertica analytics account esterno {#vertica-external}

È necessario creare un [!DNL Vertica Analytics] account esterno per collegare la tua istanza Campaign al tuo [!DNL Vertica Analytics] database esterno.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configura le **[!UICONTROL Vertica Analytics]** account esterno, devi specificare:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL del [!DNL Vertica Analytics] server

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

   ![](assets/vertica.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| TimeZoneName | Per impostazione predefinita è vuoto e indica che viene utilizzato il fuso orario del sistema dell’app server Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. |

