---
product: campaign
title: Configurare l’accesso al Snowflake
description: Scopri come configurare l’accesso al Snowflake in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 22420452d4df2e8161c91a42ad0d20ceb4796e82
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---

# Configurare l’accesso al Snowflake {#configure-access-to-snowflake}

Utilizza l&#39;opzione **Federated Data Access** (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Per configurare l&#39;accesso a [!DNL Snowflake], eseguire la procedura seguente.

1. Configura [!DNL Snowflake] in [Linux](#snowflake-linux).
1. Configura l&#39;[!DNL Snowflake] [account esterno](#snowflake-external) in Campaign

>[!CAUTION]
>
>* Il connettore [!DNL Snowflake] è disponibile per le distribuzioni in hosting e on-premise. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/capability-matrix.md).
>
>* La versione minima supportata del driver ODBC [!DNL Snowflake] è **2.24.4**.
>

![](assets/snowflake_3.png)

## Snowflake su Linux {#snowflake-linux}

Per configurare [!DNL Snowflake] su Linux, eseguire la procedura seguente:

1. Prima dell&#39;installazione di ODBC, verificare che i seguenti pacchetti siano installati nella distribuzione Linux:

   * Per Red Hat/CentOS:

     ```
     yum update
     yum upgrade
     yum install -y grep sed tar wget perl curl
     ```

   * Per Debian:

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y grep sed tar wget perl curl
     ```

1. Prima di eseguire lo script, è possibile accedere a ulteriori informazioni con l&#39;opzione `--help`:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. Accedere alla directory in cui si trova lo script ed eseguire lo script seguente come utente root:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. Dopo aver installato i driver ODBC, è necessario riavviare Campaign Classic. A tale scopo, eseguire il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign, puoi quindi configurare l&#39;account esterno [!DNL Snowflake]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#snowflake-external).

## Account esterno Snowflake {#snowflake-external}

È necessario creare un account esterno [!DNL Snowflake] per collegare l&#39;istanza Campaign al database esterno [!DNL Snowflake].

1. Dalla campagna **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come **[!UICONTROL Type]** del tuo account esterno.

1. In **[!UICONTROL Configuration]**, selezionare [!DNL Snowflake] dal menu a discesa **[!UICONTROL Type]**.

   ![](assets/snowflake_5.png)

1. Aggiungi l&#39;URL **[!UICONTROL Server]** e **[!UICONTROL Database]**.

1. Configurare l&#39;autenticazione dell&#39;account esterno **[!UICONTROL Snowflake]**:

   * Per l&#39;autenticazione account/password è necessario specificare:

      * **[!UICONTROL Account]**: nome dell&#39;utente

      * **[!UICONTROL Password]**: password account utente.

     ![](assets/snowflake.png)

   * Per l&#39;autenticazione tramite coppia di chiavi, fare clic sulla scheda **[!UICONTROL Keypair Auth]** per utilizzare **[!UICONTROL Private key]** per autenticare e copiare e incollare **[!UICONTROL Private key]**.

     ![](assets/snowflake_4.png)

1. Fare clic sulla scheda **[!UICONTROL Parameters]** e quindi sul pulsante **[!UICONTROL Deploy functions]** per creare le funzioni.

   >[!NOTE]
   >
   >Affinché tutte le funzioni siano disponibili, è necessario creare le funzioni SQL di Adobe Campaign nel database remoto. Per ulteriori informazioni, consulta questa [pagina](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Al termine della configurazione, fai clic su **[!UICONTROL Save]**.

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|---|---|
| schema di lavoro | Schema di database da utilizzare per le tabelle di lavoro |
| data warehouse | Nome del magazzino predefinito da utilizzare. Sostituirà l’impostazione predefinita dell’utente. |
| TimeZoneName | Per impostazione predefinita, questo significa che viene utilizzato il fuso orario del server app di Campaign Classic. L’opzione può essere utilizzata per forzare il parametro di sessione TIMEZONE. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parametro di sessione WEEK_START. Per impostazione predefinita, è impostato su 0. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parametro di sessione USE_CACHED_RESULTS. Per impostazione predefinita, è impostato su TRUE. Questa opzione può essere utilizzata per disabilitare i risultati del Snowflake memorizzati nella cache. <br>Per ulteriori informazioni, consulta [questa pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| bulkThreads | Numero di thread da utilizzare per il caricatore di massa di Snowflake; un numero maggiore di thread indica prestazioni migliori per caricamenti di massa di maggiori dimensioni. Per impostazione predefinita, è impostato su 1. Il numero può essere regolato, a seconda del numero di thread della macchina. |
| chunkSize | Determina la dimensione del file del blocco di caricamento bulk. Per impostazione predefinita, è impostato su 128 MB. Può essere modificata per ottenere prestazioni migliori se utilizzata con bulkThreads. Un numero maggiore di thread attivi contemporaneamente garantisce prestazioni migliori. <br>Per ulteriori informazioni, consulta la [documentazione del Snowflake](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| NomeFase | Nome della fase interna di preprovisioning. Verrà utilizzato in modalità bulk load anziché creare una nuova fase temporanea. |
