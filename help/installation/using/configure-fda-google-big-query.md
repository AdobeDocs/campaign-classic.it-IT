---
product: campaign
title: Configurare l’accesso a Google BigQuery
description: Scopri come configurare l’accesso a Google BigQuery in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 2%

---

# Configurare l’accesso a Google BigQuery {#configure-fda-google-big-query}



Usa Adobe Campaign Classic **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a [!DNL Google BigQuery].

1. Configura [!DNL Google BigQuery] il [Windows](#google-windows) o [Linux](#google-linux)
1. Configurare [!DNL Google BigQuery] [account esterno](#google-external) in Adobe Campaign Classic
1. Configurazione [!DNL Google BigQuery] carico di massa del connettore attivato [Windows](#bulk-load-windows) o [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] il connettore è disponibile per le distribuzioni in hosting, ibride e on-premise. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## BigQuery Google su Windows {#google-windows}

### Configurazione del driver su Windows {#driver-window}

1. Scarica il file [Driver ODBC per Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configurare il driver ODBC in Windows. Per ulteriori informazioni, consulta [questa pagina](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Per [!DNL Google BigQuery] per il funzionamento del connettore, Adobe Campaign Classic richiede i seguenti parametri per la connessione:

   * **[!UICONTROL Project]**: crea o utilizza un progetto esistente.

     Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: crea un account di servizio.

     Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: il **[!UICONTROL Service account]** richiede un **[!UICONTROL Key File]** per un [!DNL Google BigQuery] tramite ODBC.

     Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** è facoltativo per una connessione ODBC. Poiché ogni query deve fornire il set di dati in cui si trova la tabella, specificando un **[!UICONTROL Dataset]** è obbligatorio per [!DNL Google BigQuery] Connettore FDA in Adobe Campaign Classic.

     Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic, puoi quindi configurare [!DNL Google BigQuery] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#google-external).

### Caricamento di massa configurato su Windows {#bulk-load-window}

>[!NOTE]
>
>Per il corretto funzionamento di Google Cloud SDK è necessario che sia installato Python.
>
>Si consiglia di utilizzare Python3, vedere [pagina](https://www.python.org/downloads/).

L’utility Bulk Load consente un trasferimento più rapido, grazie all’SDK di Google Cloud.

1. Scarica l&#39;archivio Windows a 64 bit (x86_64) da questo [pagina](https://cloud.google.com/sdk/docs/downloads-versioned-archives) ed estrarlo nella directory corrispondente.

1. Esegui il `google-cloud-sdk\install.sh` script. È necessario accettare l&#39;impostazione della variabile di percorso.

1. Dopo l’installazione, verifica che la variabile del percorso `...\google-cloud-sdk\bin` è impostato. In caso contrario, aggiungerlo manualmente.

1. In  `..\google-cloud-sdk\bin\bq.cmd` file, aggiungi `CLOUDSDK_PYTHON` variabile locale, che verrà reindirizzata alla posizione dell’installazione Python.

   Ad esempio:

   ![](assets/google-big-query_1.png)

1. Riavvia Adobe Campaign Classic per tenere conto delle modifiche.

## Google BigQuery su Linux {#google-linux}

### Configurazione del driver su Linux {#driver-linux}

Prima di configurare il driver, si noti che gli script e i comandi devono essere eseguiti dall&#39;utente root. Durante l’esecuzione dello script, si consiglia inoltre di utilizzare il DNS Google 8.8.8.8.

Per configurare [!DNL Google BigQuery] su Linux, segui i passaggi seguenti:

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

1. Prima di eseguire lo script, è possibile ottenere ulteriori informazioni specificando l&#39;argomento —help:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. Accedere alla directory in cui si trova lo script ed eseguire lo script seguente come utente root:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Caricamento di massa configurato su Linux {#bulk-load-linux}

>[!NOTE]
>
>Per il corretto funzionamento di Google Cloud SDK è necessario che sia installato Python.
>
>Si consiglia di utilizzare Python3, vedere [pagina](https://www.python.org/downloads/).

L’utility Bulk Load consente un trasferimento più rapido, grazie all’SDK di Google Cloud.

1. Prima dell&#39;installazione di ODBC, verificare che i seguenti pacchetti siano installati nella distribuzione Linux:

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

1. Accedere alla directory in cui si trova lo script ed eseguire lo script seguente:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Account esterno Google BigQuery {#google-external}

Devi creare un [!DNL Google BigQuery] account esterno per collegare l’istanza Adobe Campaign Classic al tuo [!DNL Google BigQuery] database esterno.

1. Da Adobe Campaign Classic **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come dell’account esterno **[!UICONTROL Type]**.

1. Configurare [!DNL Google BigQuery] account esterno, è necessario specificare:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: e-mail del **[!UICONTROL Service account]**. Per ulteriori informazioni, consulta [Documentazione di Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: nome del **[!UICONTROL Project]**. Per ulteriori informazioni, consulta [Documentazione di Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: seleziona **[!UICONTROL Click here to upload]** se scegli di caricare la chiave tramite Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: copia/incolla il percorso assoluto in questo campo se scegli di utilizzare una chiave preesistente.

   * **[!UICONTROL Dataset]**: nome del **[!UICONTROL Dataset]**. Per ulteriori informazioni, consulta [Documentazione di Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|:-:|:-:|
| ProxyType | Tipo di proxy utilizzato per connettersi a BigQuery tramite connettori ODBC e SDK. </br>Attualmente sono supportati HTTP (impostazione predefinita), http_no_tunnel, socks4 e socks5. |
| ProxyHost | Nome host o indirizzo IP in cui è possibile raggiungere il proxy. |
| ProxyPort | Numero di porta su cui è in esecuzione il proxy, ad esempio 8080 |
| ProxyUid | Nome utente utilizzato per il proxy autenticato |
| ProxyPwd | Password ProxyUid |
| bqpath | Tieni presente che questo è applicabile solo per lo strumento di caricamento in blocco (SDK per cloud). </br> Per evitare di utilizzare la variabile PATH o se la directory google-cloud-sdk deve essere spostata in un’altra posizione, con questa opzione puoi specificare il percorso esatto della directory bin dell’SDK cloud sul server. |
| GCloudConfigName | Tieni presente che questo è applicabile a partire dalla versione 7.3.4 e solo per lo strumento di caricamento in massa (Cloud SDK).</br> L’SDK di Google Cloud utilizza le configurazioni per caricare i dati nelle tabelle BigQuery. La configurazione denominata `accfda` memorizza i parametri per il caricamento dei dati. Tuttavia, questa opzione consente agli utenti di specificare un nome diverso per la configurazione. |
| GCloudDefaultConfigName | Tieni presente che questo è applicabile a partire dalla versione 7.3.4 e solo per lo strumento di caricamento in massa (Cloud SDK).</br> La configurazione SDK di Google Cloud attiva non può essere eliminata senza prima trasferire il tag attivo in una nuova configurazione. Questa configurazione temporanea è necessaria per ricreare la configurazione principale per il caricamento dei dati. Il nome predefinito per la configurazione temporanea è `default`, questo valore può essere modificato se necessario. |
| GCloudRecreateConfig | Tieni presente che questo è applicabile a partire dalla versione 7.3.4 e solo per lo strumento di caricamento in massa (Cloud SDK).</br> Se impostato su `false`, il meccanismo di caricamento in blocco evita di tentare di ricreare, eliminare o modificare le configurazioni dell’SDK di Google Cloud. Procede invece con il caricamento dei dati utilizzando la configurazione esistente sul computer. Questa funzione è utile quando altre operazioni dipendono dalle configurazioni dell’SDK di Google Cloud. </br> Se l’utente abilita questa opzione del motore senza una configurazione corretta, il meccanismo di caricamento in blocco emetterà un messaggio di avviso: `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`. Per evitare ulteriori errori, verrà utilizzato il meccanismo di caricamento bulk predefinito per Inserisci array ODBC. |

