---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso a Google BigQuery
description: Scopri come configurare l’accesso a Google BigQuery in FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---


# Configurare l&#39;accesso a Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Utilizza l&#39;opzione Adobe Campaign Classic **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a [!DNL Google BigQuery].

1. Configurare [!DNL Google BigQuery] su [Windows](#google-windows) o [Linux](#google-linux)
1. Configura l&#39; [!DNL Google BigQuery] [account esterno](#google-external) in Adobe Campaign Classic
1. Imposta il carico di massa del connettore [!DNL Google BigQuery] su [Windows](#bulk-load-windows) o [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] connettore è disponibile per distribuzioni ibride e on-premise. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery su Windows {#google-windows}

### Driver configurato su Windows {#driver-window}

1. Scaricare il driver [ODBC per Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configurare il driver ODBC in Windows. Per ulteriori informazioni, consulta [questa pagina](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Affinché il connettore [!DNL Google BigQuery] funzioni, Adobe Campaign Classic richiede i seguenti parametri per la connessione:

   * **[!UICONTROL Project]**: crea o utilizza un progetto esistente.

      Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: creare un account di servizio.

      Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: l&#39; **[!UICONTROL Service account]** utente richiede una  **[!UICONTROL Key File]** per una  [!DNL Google BigQuery] connessione tramite ODBC.

      Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**:  **[!UICONTROL Dataset]** è facoltativo per una connessione ODBC. Poiché ogni query deve fornire il set di dati in cui si trova la tabella, specificare un **[!UICONTROL Dataset]** è obbligatorio per [!DNL Google BigQuery] Connettore FDA in Adobe Campaign Classic.

      Per ulteriori informazioni, consulta questa [pagina](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic puoi quindi configurare l’account esterno [!DNL Google BigQuery]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#google-external).

### Caricamento in serie configurato su Windows {#bulk-load-window}

>[!NOTE]
>
>Per il funzionamento dell’SDK di Google Cloud è necessario installare Python.
>
>Si consiglia di utilizzare Python3: consulta questa [pagina](https://www.python.org/downloads/).

L&#39;utilità di caricamento collettivo consente un trasferimento più veloce, che viene ottenuto tramite l&#39;SDK di Google Cloud.

1. Scarica l&#39;archivio Windows a 64 bit (x86_64) da questo [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) ed estrarlo nella directory corrispondente.

1. Esegui lo script `google-cloud-sdk\install.sh`. Devi accettare l&#39;impostazione della variabile di percorso.

1. Dopo l&#39;installazione, controlla che la variabile del percorso `...\google-cloud-sdk\bin` sia impostata. In caso contrario, aggiungilo manualmente.

1. Nel file `..\google-cloud-sdk\bin\bq.cmd`, aggiungi la variabile locale `CLOUDSDK_PYTHON` che verrà reindirizzata alla posizione dell&#39;installazione Python.

   Ad esempio:

   ![](assets/google-big-query_1.png)

1. Riavvia Adobe Campaign Classic per prendere in considerazione le modifiche.

## Google BigQuery su Linux {#google-linux}

### Driver configurato su Linux {#driver-linux}

1. Prima di installare il driver ODBC, è necessario aggiornare il sistema. Su Linux o CentOS, esegui il seguente comando:

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. È quindi necessario installare la gestione driver unixODBC con il seguente comando:

   ```
   # switch to root user
   sudo su
   ```

   Su Debian:

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. Scarica il driver ODBC [Magnitude Simba Linux (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Quindi, trasferire il file tarball in una cartella temporanea sul tuo computer o utilizzare il comando wget:

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Estrarre il file di tarball principale come segue dove **TarballName** è il nome del pacchetto di tarball contenente il driver:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Accedere alla cartella estratta ed estrarre il file di tarball interno corrispondente alla versione del driver. Installalo in un&#39;altra cartella temporanea, nel seguente esempio BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Accedi alla posizione temporanea in cui è stato estratto il file di tarball principale e copia i file `GoogleBigQueryODBC.did` e `setup/simba.googlebigqueryodbc.ini` nella nuova cartella creata nel passaggio precedente:

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Crea la directory di installazione come segue:

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Copia il contenuto della directory nella nuova directory di installazione:

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Sostituisci `<INSTALLDIR>` con `/opt/simba/googlebigqueryodbc` in `simba.googlebigqueryodbc.ini` nella directory di installazione:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Cambia i valori `DriverManagerEncoding` in UTF-16 e `SwapFilePath` in `simba.googlebigqueryodbc.ini`. Se necessario, puoi anche modificare le impostazioni di registrazione.

   Di seguito è riportato un esempio di file di configurazione aggiornato a livello di driver:

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Se utilizzi un file di driver di sistema o un file `odbcinst.ini` corrente, configura `/etc/odbcinst.ini` per puntare alla posizione del driver Google BigQuery `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

   Ad esempio:

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. Trova il percorso delle librerie di gestione driver unixODBC e aggiungi i percorsi della libreria `unixODBC` e `googlebigqueryodbc` alla variabile `LD_LIBRARY_PATH environment`.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. In Adobe Campaign Classic puoi quindi configurare l’account esterno [!DNL Google BigQuery]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#google-external).

### Caricamento in serie configurato su Linux {#bulk-load-linux}

>[!NOTE]
>
>Per il funzionamento dell’SDK di Google Cloud è necessario installare Python.
>
>Si consiglia di utilizzare Python3: consulta questa [pagina](https://www.python.org/downloads/).

L&#39;utilità di caricamento collettivo consente un trasferimento più veloce, che viene ottenuto tramite l&#39;SDK di Google Cloud.

1. Scarica l&#39;archivio Linux a 64 bit (x86_64) in questa [pagina](https://cloud.google.com/sdk/docs/downloads-versioned-archives) ed estrai nella directory corrispondente.

1. Esegui lo script `google-cloud-sdk\install.sh`. È necessario accettare l&#39;impostazione della variabile di percorso.

1. Dopo l&#39;installazione, controlla che la variabile del percorso `...\google-cloud-sdk\bin` sia impostata. In caso contrario, aggiungilo manualmente.

1. Se si desidera evitare di utilizzare la variabile `PATH` o se si desidera spostare la directory `google-cloud-sdk` in un&#39;altra posizione, utilizzare il valore dell&#39;opzione `bqpath` durante la configurazione di **[!UICONTROL External account]** per specificare il percorso esatto della directory bin sul sistema.

1. Riavvia Adobe Campaign Classic per prendere in considerazione le modifiche.

## Account esterno Google BigQuery {#google-external}

È necessario creare un account esterno [!DNL Google BigQuery] per collegare l&#39;istanza Adobe Campaign Classic al database esterno [!DNL Google BigQuery].

1. In Adobe Campaign Classic **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configura l’account esterno [!DNL Google BigQuery] , devi specificare:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: Email del tuo  **[!UICONTROL Service account]**. Per ulteriori informazioni, consulta la [documentazione di Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Nome del  **[!UICONTROL Project]**. Per ulteriori informazioni, consulta la [documentazione di Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: seleziona  **[!UICONTROL Click here to upload]** se scegli di caricare la chiave tramite Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: copia/incolla il percorso assoluto in questo campo se scegli di utilizzare una chiave preesistente.
   * **[!UICONTROL Dataset]**: Nome del  **[!UICONTROL Dataset]**. Per ulteriori informazioni, consulta la [documentazione di Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
