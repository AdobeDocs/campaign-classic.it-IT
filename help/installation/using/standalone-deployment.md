---
product: campaign
title: Implementazione autonoma
description: Implementazione autonoma
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 2%

---

# Implementazione autonoma{#standalone-deployment}



Questa configurazione include tutti i componenti dello stesso computer:

* processo di applicazione (web),
* processo di consegna (mta),
* processo di reindirizzamento (tracciamento),
* processo di workflow e operazioni pianificate (wfserver),
* processo di mail non recapitate (inMail),
* processo di statistica (stat).

La comunicazione generale tra i processi viene effettuata secondo il seguente schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Questo tipo di configurazione può essere eseguito quando si gestiscono elenchi con meno di 100.000 destinatari e con, ad esempio, i seguenti livelli software:

* Linux
* Apache
* PostgreSQL
* Qmail.

Con la crescita del volume, una variante di questa architettura sposta il server di database in un altro computer per migliorare le prestazioni.

>[!NOTE]
>
>È inoltre possibile utilizzare un server di database esistente se dispone di risorse sufficienti.

## Funzioni {#features}

### Vantaggi {#advantages}

* Completamente indipendente e a basso costo di configurazione (non sono richieste licenze fatturabili se viene utilizzato il software open-source elencato di seguito).
* Installazione e configurazione di rete semplificate.

### Svantaggi {#disadvantages}

* Computer critico in caso di problemi.
* Larghezza di banda limitata durante la trasmissione dei messaggi (nella nostra esperienza, circa decine di migliaia di e-mail all&#39;ora).
* Potenziale rallentamento dell’applicazione durante la trasmissione.
* Il server applicazioni deve essere disponibile dall&#39;esterno (ad esempio nella zona demilitarizzata) in quanto ospita il server di reindirizzamento.

## Passaggi per l’installazione e la configurazione {#installation-and-configuration-steps}

### Prerequisiti {#prerequisites}

* JDK
* Server web (IIS, Apache),
* Accesso a un server di database,
* Cassetta postale di mancato recapito accessibile tramite POP3,
* Creazione di due alias DNS:

   * la prima esposizione al pubblico per il tracciamento e il puntamento verso il computer sulla sua IP pubblica;
   * il secondo alias esposto agli utenti interni per l&#39;accesso alla console e che punta allo stesso computer.

* Firewall configurato per aprire SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 ad Oracle, 5432 per PostgreSQL, ecc.) porte. Per ulteriori informazioni, vedere [Configurazione di rete](../../installation/using/network-configuration.md).

Negli esempi seguenti, i parametri della variante sono:

* Nome dell&#39;istanza: **demo**
* Maschera DNS: **console.campaign.net&#42;** (solo per le connessioni della console client e per i report)
* Database: **campagna:demo@dbsrv**

### Installazione e configurazione (singolo computer) {#installing-and-configuring--single-machine-}

Applica i seguenti passaggi:

1. Seguire la procedura di installazione per il server Adobe Campaign: pacchetto **nlserver** su Linux o **setup.exe** su Windows.

   Per ulteriori informazioni, consulta [Prerequisiti per l&#39;installazione di Campaign in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Prerequisiti per l&#39;installazione di Campaign in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Una volta installato il server Adobe Campaign, avviare il server applicazioni (Web) utilizzando il comando **nlserver web -tomcat** (il modulo Web consente di avviare Tomcat in modalità server Web standalone in ascolto sulla porta 8080) e di assicurarsi che Tomcat venga avviato correttamente:

   ```sql
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >La prima volta che il modulo Web viene eseguito, crea i file **config-default.xml** e **serverConf.xml** nella directory **conf** nella cartella di installazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

   Premere **Ctrl+C** per arrestare il server.

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Primo avvio del server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Per Windows: [Primo avvio del server](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Modifica la password **internal** utilizzando il comando:

   ```
   nlserver config -internalpassword
   ```

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Crea l&#39;istanza **demo** con le maschere DNS per il tracciamento (in questo caso, **tracking.campaign.net**) e l&#39;accesso alle console client (in questo caso, **console.campaign.net**). Esistono due modi per farlo:

   * Crea l’istanza tramite la console:

     ![](assets/install_create_new_connexion.png)

     Per ulteriori informazioni, consulta [Creare un&#39;istanza e accedere](../../installation/using/creating-an-instance-and-logging-on.md).

     o

   * Crea l’istanza utilizzando le righe di comando:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Per ulteriori informazioni, consulta [Creazione di un&#39;istanza](../../installation/using/command-lines.md#creating-an-instance).

1. Modifica il file **config-demo.xml** (creato nel passaggio precedente accanto a **config-default.xml**) e assicurati che i processi **mta** (consegna), **wfserver** (flusso di lavoro), **inMail** (messaggi non recapitati) e **stat** (statistiche) siano abilitati. Quindi configura l’indirizzo del server delle statistiche:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Modifica il file **serverConf.xml** e specifica il dominio di consegna, quindi specifica gli indirizzi IP (o host) dei server DNS utilizzati dal modulo MTA per rispondere alle query DNS di tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Il parametro **nameServers** è utilizzato solo in Windows.

   Per ulteriori informazioni, consulta [Configurazione del server Campaign](../../installation/using/configuring-campaign-server.md).

1. Copiare il programma di installazione della console client **setup-client-7.XXX.exe** nella cartella **/datakit/nl/eng/jsp**. [Ulteriori informazioni](../../installation/using/client-console-availability-for-windows.md).

1. Segui la procedura di integrazione del server web (IIS, Apache) descritta nelle sezioni seguenti:

   * Per Linux: [Integrazione in un server Web per Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Per Windows: [Integrazione in un server Web per Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Avvia il sito web e testa il reindirizzamento utilizzando l’URL: https://tracking.campaign.net/r/test.

   Il browser deve visualizzare il seguente messaggio:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Avvio del server Web e test della configurazione](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Per Windows: [Avvio del server Web e test della configurazione](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Avviare il server Adobe Campaign (**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux) ed eseguire nuovamente il comando **nlserver pdump** per verificare la presenza di tutti i moduli abilitati.

   >[!NOTE]
   >
   >A partire dalla versione 20.1, è consigliabile utilizzare il comando seguente (per Linux): **systemctl start nlserver**

   ```sql
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Questo comando consente inoltre di conoscere il numero di versione e di build del server Adobe Campaign installato nel computer.

1. Verifica il modulo **nlserver web** utilizzando l&#39;URL: https://console.campaign.net/nl/jsp/logon.jsp

   Questo URL consente di accedere alla pagina di download per il programma di configurazione client.

   Immetti l&#39;accesso **internal** e la password associata quando raggiungi la pagina di controllo degli accessi. [Ulteriori informazioni](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Avviare la console client di Adobe Campaign (dalla pagina di download precedente o avviata direttamente sul server per un&#39;installazione di Windows), impostare l&#39;URL della connessione al server su https://console.campaign.net e connettersi utilizzando l&#39;accesso **internal**.

   Consulta [questa pagina](../../installation/using/creating-an-instance-and-logging-on.md) e [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

   La procedura guidata di creazione del database viene visualizzata quando si esegue il primo accesso:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Segui i passaggi della procedura guidata e crea il database associato all’istanza di connessione.

   Per ulteriori informazioni, vedere [Creazione e configurazione del database](../../installation/using/creating-and-configuring-the-database.md).

   Una volta creato il database, disconnettersi.

1. Accedi nuovamente alla console client utilizzando l&#39;accesso **admin** senza password e avvia la procedura guidata di distribuzione (menu **[!UICONTROL Tools > Advanced]**) per completare la configurazione dell&#39;istanza.

   Per ulteriori informazioni, consulta [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md).

   I parametri principali da impostare sono i seguenti:

   * Email delivery: indirizzo del mittente e della risposta e cassetta postale di errore per la mail non recapitata.
   * Tracciamento: popolare l&#39;URL esterno utilizzato per il reindirizzamento e l&#39;URL interno, fare clic su **Registrazione sui server di tracciamento** e quindi convalidarlo nell&#39;istanza **demo** del server di tracciamento.

     Per ulteriori informazioni, consulta [Configurazione del tracciamento](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Poiché il server Adobe Campaign viene utilizzato sia come server applicazioni che come server di reindirizzamento, l’URL interno utilizzato per raccogliere i registri di tracciamento e trasferire gli URL è una connessione interna diretta a Tomcat (https://localhost:8080).

   * Gestione dei messaggi non recapitati: immetti i parametri per gestire i messaggi non recapitati (non prendere in considerazione la sezione **Messaggi non recapitati non elaborati**).
   * Accesso da: fornisci i due URL per i rapporti, i moduli web e le pagine mirror.

     ![](assets/d_ncs_install_web_url.png)
