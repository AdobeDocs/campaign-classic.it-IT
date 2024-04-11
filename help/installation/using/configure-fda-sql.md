---
product: campaign
title: Configurare l'accesso a Microsoft SQL Server
description: Scopri come configurare l’accesso a Microsoft SQL Server
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 1%

---

# Configurare l&#39;accesso a Microsoft SQL Server {#configure-fda-sql}



Utilizzare Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno di Microsoft SQL Server. Segui i passaggi seguenti per configurare l’accesso a [!DNL Microsoft SQL Server].

1. Configura [!DNL Microsoft SQL Server] il [CentOS](#sql-centos).
1. Configura [!DNL Microsoft SQL Server] il [Linux](#sql-linux).
1. Configura [!DNL Microsoft SQL Server] il [Windows](#sql-windows).
1. Configurare [!DNL Microsoft SQL Server] [account esterno](#sql-external) in Campaign

## Microsoft SQL Server su CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] è disponibile su CentOS 7 e 6.

Per configurare [!DNL Microsoft SQL Server] su CentOS, segui i passaggi seguenti:

1. Scaricare e installare il driver ODBC SQL con il comando seguente:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. In Adobe Campaign, puoi quindi configurare i [!DNL Microsoft SQL Server] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#sql-external).

## Microsoft SQL Server su Linux {#sql-linux}

>[!NOTE]
>
> Se utilizzi una versione precedente di Adobe Campaign (precedente alla versione 7.2.1), devi installare `unix ODBC drivers`.

1. Scaricare il driver MS ODBC da [questa pagina](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. Esegui il comando seguente come utente root:

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. In Adobe Campaign, puoi quindi configurare i [!DNL Microsoft SQL Server] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#sql-external).

## Microsoft SQL Server su Windows {#sql-windows}

Per configurare [!DNL Microsoft SQL Server] in Windows:

1. In Windows, fai clic su **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. Dalla sezione **[!UICONTROL ODBC Data Sources (64-bit)]** nuova finestra, fai clic su **[!UICONTROL Add...]**.

1. Verificare se SQL Server Native Client v11 è elencato in **[!UICONTROL Create New Data Source]** finestra.

1. Se il client nativo di SQL Server non è elencato, è possibile scaricarlo in [questa pagina](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. In Adobe Campaign, puoi quindi configurare i [!DNL Microsoft SQL Server] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#sql-external).

## Account esterno di Microsoft SQL Server {#sql-external}

Devi creare un [!DNL Microsoft SQL Server] account esterno per collegare la tua istanza Campaign al tuo [!DNL Microsoft SQL Server] database esterno.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come dell’account esterno **[!UICONTROL Type]**.

1. Sotto **[!UICONTROL Configuration]**, seleziona [!DNL Microsoft SQL Server] dal **[!UICONTROL Type]** a discesa.

   ![](assets/sql.png)

1. Configurare **[!UICONTROL Microsoft SQL Server]** autenticazione account esterno:

   * **[!UICONTROL Server]**: URL del [!DNL Microsoft SQL Server] server.

   * **[!UICONTROL Account]**: nome dell’utente.

   * **[!UICONTROL Password]**: password dell’account utente.

   * **[!UICONTROL Database]**: nome del database (facoltativo).

   * **[!UICONTROL Timezone]**: fuso orario impostato in [!DNL Microsoft SQL Server]. [Ulteriori informazioni](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Fai clic su **[!UICONTROL Parameters]** , quindi la scheda **[!UICONTROL Deploy functions]** per creare funzioni.

   >[!NOTE]
   >
   >Affinché tutte le funzioni siano disponibili, è necessario creare le funzioni SQL di Adobe Campaign nel database remoto. Per ulteriori informazioni, consulta questa [pagina](../../configuration/using/adding-additional-sql-functions.md).

1. Clic **[!UICONTROL Save]** al termine della configurazione.

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| Autenticazione | Tipo di autenticazione supportato dal connettore. Valore attualmente supportato: ActiveDirectoryMSI. <br> Per ulteriori informazioni, consulta l’esempio 8 di [Documentazione di Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Crittografa | Specifica se le connessioni utilizzano la crittografia TLS in rete. I valori possibili sono **sì/obbligatorio (18.0 e versioni successive)**, **no/optional (18.0 e versioni successive)**, e **strict (18.0 e versioni successive)**. Il valore predefinito è impostato su **sì** nella versione 18.0 o successiva e **no** nelle versioni precedenti. <br>Per ulteriori informazioni, consulta [Documentazione di Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Abilita la crittografia utilizzando un certificato server autofirmato, se utilizzato con **Crittografa**. <br>Valori accettati: **sì** o **no** (valore predefinito, che indica che il certificato del server verrà convalidato). |
