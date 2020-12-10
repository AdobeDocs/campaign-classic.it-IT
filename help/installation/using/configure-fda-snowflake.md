---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso al Snowflake
description: Scoprite come configurare l'accesso al Snowflake in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 535339b5a9b39625100d630b0b831df143dbeb01
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 10%

---


# Configurare l&#39;accesso al Snowflake {#configure-access-to-snowflake}

Utilizzate l&#39;opzione Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi indicati di seguito per configurare l&#39;accesso a [!DNL Snowflake].

1. Configurare [!DNL Snowflake] su [CentOS](#snowflake-centos), [Windows](#snowflake-windows) o [Debian](#snowflake-debian)
1. Configurare l&#39; [!DNL Snowflake] [account esterno](#snowflake-external) in Campaign


>[!NOTE]
>
>[!DNL Snowflake] il connettore è disponibile per le distribuzioni in hosting e in sede. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake su CentOS {#snowflake-centos}

Per configurare [!DNL Snowflake] su CentOS, attenetevi alla procedura seguente:

1. Scaricare i driver ODBC per [!DNL Snowflake]. [Fate clic su ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) qui per iniziare il download.
1. È quindi necessario installare i driver ODBC su CentOs con il seguente comando:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare il Campaign Classic. A questo scopo, eseguite il comando seguente:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. In Campaign, puoi quindi configurare il tuo account esterno [!DNL Snowflake]. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consultare [questa sezione](#snowflake-external).

## Snowflake in Windows {#snowflake-windows}

1. Scaricare il driver ODBC [per Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Per installare il driver, è necessario disporre dei privilegi di amministratore. Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configurare il driver ODBC. Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign, puoi quindi configurare il tuo account esterno [!DNL Snowflake]. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consultare [questa sezione](#snowflake-external).

## Snowflake su Debian {#snowflake-debian}

1. Scaricare i driver ODBC per [!DNL Snowflake]. [Fate clic sul download ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) dell&#39;avvio.

1. È quindi necessario installare i driver ODBC su Debian con il seguente comando:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare il Campaign Classic. A questo scopo, eseguite il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign, puoi quindi configurare il tuo account esterno [!DNL Snowflake]. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consultare [questa sezione](#snowflake-external).

## Conto esterno Snowflake {#snowflake-external}

È necessario creare un account esterno [!DNL Snowflake] per collegare l&#39;istanza Campaign al database esterno [!DNL Snowflake].

1. Da Campaign **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Selezionare **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configurate l&#39;account esterno **[!UICONTROL Snowflake]**, dovete specificare:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**: URL del  [!DNL Snowflake] server

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

   ![](assets/snowflake.png)

1. Fare clic sulla scheda **[!UICONTROL Parameters]**, quindi sul pulsante **[!UICONTROL Deploy functions]** per creare le funzioni.

   ![](assets/snowflake_2.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| schema di lavoro | Schema del database da utilizzare per le tabelle di lavoro |
| warehouse | Nome del magazzino predefinito da utilizzare. Sostituirà l&#39;impostazione predefinita dell&#39;utente. |
| TimeZoneName | Per impostazione predefinita vuota, ovvero viene utilizzato il fuso orario del sistema del server app Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | parametro di sessione WEEK_START. Per impostazione predefinita, è impostato su 0. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | parametro di sessione USE_CACHED_RESULTS. Per impostazione predefinita, è impostato su TRUE. Questa opzione può essere utilizzata per disattivare i risultati del Snowflake memorizzati nella cache. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
