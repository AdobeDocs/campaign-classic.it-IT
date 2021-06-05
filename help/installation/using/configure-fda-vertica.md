---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso a Vertica
description: Scopri come configurare l’accesso a Vertica in FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: a7c080fe4db72f659659c7cac8f2c02031822e04
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 4%

---


# Configurare l&#39;accesso a Vertica {#configure-fda-vertica}

Utilizza l’opzione Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a [!DNL Vertica].

1. Configura [!DNL Vertica] su [CentOS](#vertica-centos), [Windows](#vertica-windows) o [Debian](#vertica-debian)
1. Configura l’ [!DNL Vertica] [account esterno](#vertica-external) in Campaign


>[!NOTE]
>
>[!DNL Vertica] connettore è disponibile per distribuzioni ibride e on-premise. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica su CentOS {#vertica-centos}

Per configurare [!DNL Vertica] su CentOS, segui i passaggi seguenti:

1. Scarica i driver ODBC per [!DNL Vertica]. [Fai clic ](https://www.vertica.com/download/vertica/client-drivers/) qui e scarica l&#39;ultimo Linux RPM.

1. È quindi necessario installare unixODBC con il seguente comando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Se in precedenza è stato installato il server [!DNL Vertica], verrà installato un driver ODBC. In questo caso, aggiornare l&#39;unità come segue:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. In Adobe Campaign puoi quindi configurare l’account esterno [!DNL Vertica]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#vertica-external).

## Vertica su Windows {#vertica-windows}

1. Scaricare il driver [ODBC per Windows](https://www.vertica.com/download/vertica/client-drivers/). Per installare il driver per Windows, è necessario abilitare .NET Framework 3.5 oppure la procedura guidata di installazione tenterà di abilitarlo e scaricarlo automaticamente.

1. Configurare il driver ODBC in Windows. Per ulteriori informazioni, consulta [questa pagina](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign puoi quindi configurare l’account esterno [!DNL Vertica]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#vertical-external).

## Vertica su Debian {#vertica-debian}

1. Scarica i driver ODBC per [!DNL Vertica]. [Fai clic su download ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) dell&#39;herestart.

1. È quindi necessario installare unixODBC con il seguente comando:

   ```
   apt-get install unixODBC
   ```

1. Se in precedenza è stato installato il server [!DNL Vertica], verrà installato un driver ODBC. In questo caso, aggiornare l&#39;unità come segue:

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
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. In Adobe Campaign puoi quindi configurare l’account esterno [!DNL Vertica]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#vertica-external).

## Account esterno Vertica {#vertica-external}

Devi creare un account esterno [!DNL Vertica] per collegare l’istanza Campaign al database esterno [!DNL Vertica].

1. Dalla campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configura l’account esterno **[!UICONTROL Vertica]** , devi specificare:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL del  [!DNL Vertica] server

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database
   ![](assets/vertica.png)
