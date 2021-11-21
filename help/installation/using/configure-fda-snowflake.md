---
product: campaign
title: Configurare l’accesso al Snowflake
description: Scopri come configurare l’accesso al Snowflake in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 10%

---

# Configurare l’accesso al Snowflake {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

Utilizzare Campaign **Federated Data Access** (FDA) opzione per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a [!DNL Snowflake].

1. Configura [!DNL Snowflake] su [CentOS](#snowflake-centos), [Windows](#snowflake-windows) o [Debian](#snowflake-debian)
1. Configura le [!DNL Snowflake] [account esterno](#snowflake-external) in Campaign


>[!NOTE]
>
>[!DNL Snowflake] è disponibile per le distribuzioni in hosting e on-premise. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake su CentOS {#snowflake-centos}

Per configurare [!DNL Snowflake] su CentOS, segui i passaggi seguenti:

1. Scaricare i driver ODBC per [!DNL Snowflake]. [Fai clic qui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) per iniziare a scaricare.
1. È quindi necessario installare i driver ODBC su CentOs con il seguente comando:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A questo scopo, esegui il seguente comando:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. In Campaign, puoi quindi configurare il tuo [!DNL Snowflake] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#snowflake-external).

## Snowflake su Windows {#snowflake-windows}

1. Scarica la [Driver ODBC per Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Per installare il driver, è necessario disporre di privilegi di livello amministratore. Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configurare il driver ODBC. Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign, puoi quindi configurare il tuo [!DNL Snowflake] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#snowflake-external).

## Snowflake su Debian {#snowflake-debian}

1. Scaricare i driver ODBC per [!DNL Snowflake]. [Fai clic qui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) inizia a scaricare.

1. È quindi necessario installare i driver ODBC su Debian con il seguente comando:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Dopo aver scaricato e installato i driver ODBC, è necessario riavviare Campaign Classic. A questo scopo, esegui il seguente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign, puoi quindi configurare il tuo [!DNL Snowflake] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#snowflake-external).

## account esterno Snowflake {#snowflake-external}

È necessario creare un [!DNL Snowflake] account esterno per collegare la tua istanza Campaign al tuo [!DNL Snowflake] database esterno.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configura le **[!UICONTROL Snowflake]** account esterno, devi specificare:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**: URL del [!DNL Snowflake] server

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

   ![](assets/snowflake.png)

1. Fai clic sul pulsante **[!UICONTROL Parameters]** quindi seleziona **[!UICONTROL Deploy functions]** per creare funzioni.

   ![](assets/snowflake_2.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| schema di lavoro | Schema di database da utilizzare per le tabelle di lavoro |
| magazzino | Nome del magazzino predefinito da utilizzare. Sostituirà il valore predefinito dell’utente. |
| TimeZoneName | Per impostazione predefinita è vuoto e indica che viene utilizzato il fuso orario del sistema dell’app server Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parametro di sessione WEEK_START. Per impostazione predefinita, è impostato su 0. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parametro di sessione USE_CACHED_RESULTS . Per impostazione predefinita, è impostato su TRUE. Questa opzione può essere utilizzata per disabilitare i risultati della cache del Snowflake. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
