---
product: campaign
title: Configurare l'accesso a Google BigQuery
description: Scopri come configurare l’accesso a Google BigQuery in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 5d2ec0836fe5f106e0c56e5abbe7bab9332d7e18
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 2%

---

# Configurare l&#39;accesso a Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Utilizza Adobe Campaign Classic **Federated Data Access** (FDA) opzione per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a [!DNL Google BigQuery].

1. Configura [!DNL Google BigQuery] su [Windows](#google-windows) o [Linux](#google-linux)
1. Configura le [!DNL Google BigQuery] [account esterno](#google-external) in Adobe Campaign Classic
1. Configurazione [!DNL Google BigQuery] carico in blocco del connettore [Windows](#bulk-load-windows) o [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] è disponibile per le distribuzioni in hosting, ibride e on-premise. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery su Windows {#google-windows}

### Driver configurato su Windows {#driver-window}

1. Scarica la [Driver ODBC per Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configurare il driver ODBC in Windows. Per ulteriori informazioni, consulta [questa pagina](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Per [!DNL Google BigQuery] Connettore per funzionare, Adobe Campaign Classic richiede i seguenti parametri per connettersi:

   * **[!UICONTROL Project]**: crea o utilizza un progetto esistente.

      Per ulteriori informazioni, consulta [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: creare un account di servizio.

      Per ulteriori informazioni, consulta [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: la **[!UICONTROL Service account]** richiede un **[!UICONTROL Key File]** per [!DNL Google BigQuery] connessione tramite ODBC.

      Per ulteriori informazioni, consulta [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** è facoltativo per una connessione ODBC. Poiché ogni query deve fornire il set di dati in cui si trova la tabella, specificando **[!UICONTROL Dataset]** è obbligatorio per [!DNL Google BigQuery] Connettore FDA in Adobe Campaign Classic.

      Per ulteriori informazioni, consulta [page](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic puoi quindi configurare il [!DNL Google BigQuery] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#google-external).

### Caricamento in serie configurato su Windows {#bulk-load-window}

>[!NOTE]
>
>Per il funzionamento dell’SDK di Google Cloud è necessario installare Python.
>
>Consigliamo di utilizzare Python3, consulta questo [page](https://www.python.org/downloads/).

L&#39;utilità di caricamento collettivo consente un trasferimento più veloce, che viene ottenuto tramite Google Cloud SDK.

1. Scarica l&#39;archivio Windows a 64 bit (x86_64) da questo [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) ed estrarlo nella directory corrispondente.

1. Esegui il `google-cloud-sdk\install.sh` script. È necessario accettare l&#39;impostazione della variabile di percorso.

1. Dopo l&#39;installazione, controlla che la variabile del percorso `...\google-cloud-sdk\bin` è impostato. In caso contrario, aggiungilo manualmente.

1. In  `..\google-cloud-sdk\bin\bq.cmd` aggiungi il `CLOUDSDK_PYTHON` variabile locale, che reindirizza alla posizione dell&#39;installazione Python.

   Ad esempio:

   ![](assets/google-big-query_1.png)

1. Riavvia Adobe Campaign Classic per prendere in considerazione le modifiche.

## Google BigQuery su Linux {#google-linux}

### Driver configurato su Linux {#driver-linux}

Prima di configurare il driver, tenere presente che lo script e i comandi devono essere eseguiti dall&#39;utente principale. Si consiglia inoltre di utilizzare Google DNS 8.8.8.8 durante l&#39;esecuzione dello script.

Per configurare [!DNL Google BigQuery] su Linux, segui i passaggi seguenti:

1. Prima dell&#39;installazione ODBC, verificare che i seguenti pacchetti siano installati nella distribuzione Linux:

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

1. Aggiornare il sistema prima dell&#39;installazione:

   * Per Red Hat/CentOS:

      ```
      # install unixODBC driver manager
      yum install -y unixODBC
      ```

   * Per Debian:

      ```
      # install unixODBC driver manager
      apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
      ```

1. Accedi alla directory in cui si trova lo script ed esegui il seguente script:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Caricamento in serie configurato su Linux {#bulk-load-linux}

>[!NOTE]
>
>Per il funzionamento dell’SDK di Google Cloud è necessario installare Python.
>
>Consigliamo di utilizzare Python3, consulta questo [page](https://www.python.org/downloads/).

L&#39;utilità di caricamento collettivo consente un trasferimento più veloce, che viene ottenuto tramite Google Cloud SDK.

1. Prima dell&#39;installazione ODBC, verificare che i seguenti pacchetti siano installati nella distribuzione Linux:

   * Per Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y python3
      ```

   * Per Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y python3
      ```

1. Accedi alla directory in cui si trova lo script ed esegui il seguente script:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Account esterno Google BigQuery {#google-external}

È necessario creare un [!DNL Google BigQuery] account esterno per collegare la tua istanza Adobe Campaign Classic al tuo [!DNL Google BigQuery] database esterno.

1. Da Adobe Campaign Classic **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configura le [!DNL Google BigQuery] account esterno, devi specificare:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: E-mail del tuo **[!UICONTROL Service account]**. Per ulteriori informazioni, consulta [Documentazione di Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Nome della **[!UICONTROL Project]**. Per ulteriori informazioni, consulta [Documentazione di Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: select **[!UICONTROL Click here to upload]** se scegli di caricare la chiave tramite Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: copia/incolla il percorso assoluto in questo campo se scegli di utilizzare una chiave preesistente.
   * **[!UICONTROL Dataset]**: Nome della **[!UICONTROL Dataset]**. Per ulteriori informazioni, consulta [Documentazione di Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Elemento “value” | Descrizione |
|:-:|:-:|:-:|
| ProxyType | string | Tipo di proxy utilizzato per la connessione a BigQuery tramite connettori ODBC e SDK. </br>HTTP (predefinito), http_no_tunnel, socks4 e socks5 sono attualmente supportati. |
| ProxyHost | string | Nome host o indirizzo IP in cui è possibile raggiungere il proxy. |
| ProxyPort | numero | Numero di porta su cui è in esecuzione il proxy, ad esempio 8080 |
| ProxyUid | string | Nome utente utilizzato per il proxy autenticato |
| ProxyPwd | string | Password ProxyUid |
| bqpath | string | Questo è applicabile solo per lo strumento a caricamento collettivo (Cloud SDK). </br> Per evitare di utilizzare la variabile PATH o se la directory google-cloud-sdk deve essere spostata in un’altra posizione, puoi specificare con questa opzione il percorso esatto della directory cloud sdk bin sul server. |
