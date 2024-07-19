---
product: campaign
title: Implementazione aziendale
description: Implementazione aziendale
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 3%

---

# Implementazione aziendale{#enterprise-deployment}



Questa è la configurazione più completa. Si basa sulla configurazione standard per una maggiore sicurezza e disponibilità:

* server di reindirizzamento dedicati basati su un load balancer HTTP o TCP, per la scalabilità e la disponibilità,
* due server applicazioni per migliorare il throughput e la capacità di failover (fault tolerance) e che sono isolati nella LAN.

La comunicazione generale tra server e processi viene eseguita in base allo schema seguente:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Con questo tipo di configurazione, il throughput previsto può superare le 100.000 e-mail all&#39;ora con larghezza di banda e ottimizzazione appropriate.

## Funzioni {#features}

### Vantaggi {#advantages}

* Protezione ottimizzata: solo i server che devono essere esposti all&#39;esterno vengono installati nel computer nella DMZ.
* Elevata disponibilità più facile da garantire: solo il computer visibile dall&#39;esterno deve essere gestito tenendo presente l&#39;elevata disponibilità.

### Svantaggi {#disadvantages}

Costi più elevati per l&#39;hardware e l&#39;amministrazione.

### Attrezzature consigliate {#recommended-equipment}

* Application server: CPU quad-core da 2 Ghz, 4 GB di RAM, disco rigido SATA RAID 1 da 80 GB software.
* Server di reindirizzamento: CPU quad-core da 2 Ghz, 4 GB di RAM, disco rigido SATA RAID 1 da 80 GB software.

>[!NOTE]
>
>È possibile riutilizzare un load balancer esistente per il traffico verso i server di reindirizzamento.

## Passaggi per l’installazione e la configurazione {#installation-and-configuration-steps}

### Prerequisiti {#prerequisites}

* JDK su entrambi i server applicazioni,
* Server web (IIS, Apache) su entrambi i frontali,
* Accesso a un server di database su entrambi i server applicazioni
* Cassetta postale di mancato recapito accessibile tramite POP3,
* Creazione di due alias DNS nel load balancer:

   * il primo esposto al pubblico per il tracciamento e il puntamento al load balancer su un indirizzo IP virtuale (VIP) e che viene quindi distribuito ai due server frontali,
   * il secondo esposto agli utenti interni per l’accesso tramite la console e che punta a un load balancer su un indirizzo IP virtuale (VIP) e che viene quindi distribuito ai due server applicazioni.

* Firewall configurato per aprire STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 ad Oracle, 5432 per PostgreSQL, ecc.) porte. Per ulteriori informazioni, vedere la sezione [Accesso al database](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Se i server applicazioni puntano a una singola istanza di database, dopo aver importato un pacchetto standard in un&#39;istanza, lo schema contenuto nel pacchetto non viene caricato nell&#39;altra istanza.
>  
>Se i server applicazioni puntano a una singola istanza di database, dopo aver modificato lo schema in un&#39;istanza, lo schema non viene caricato sull&#39;altra istanza.
>
>Per risolvere questi problemi, è necessario riavviare il processo &#39;web@default&#39; sulla seconda istanza in cui si è verificato l&#39;errore.

### Installazione e configurazione del server applicazioni 1 {#installing-and-configuring-the-application-server-1}

Negli esempi seguenti, i parametri della variante sono:

* Nome dell’istanza: demo
* Maschera DNS: tracking.campaign.net&#42;, console.campaign.net&#42; (il server applicazioni gestisce gli URL per le connessioni e i report della console client e per le pagine mirror e le pagine di annullamento abbonamento)
* Lingua: inglese
* Database: campaign:demo@dbsrv

I passaggi per l&#39;installazione del primo server sono i seguenti:

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

   * Per Linux: [Primo avvio del server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Per Windows: [Primo avvio del server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Modifica la password **internal** utilizzando il comando:

   ```
   nlserver config -internalpassword
   ```

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Crea l&#39;istanza **demo** con le maschere DNS per il tracciamento (in questo caso, **tracking.campaign.net**) e l&#39;accesso alle console client (in questo caso, **console.campaign.net**). Esistono due modi per farlo:

   * Crea l’istanza tramite la console:

     ![](assets/install_create_new_connexion.png)

     Per ulteriori informazioni, consulta [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).

     o

   * Crea l’istanza utilizzando le righe di comando:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Per ulteriori informazioni, consulta [Creazione di un&#39;istanza](../../installation/using/command-lines.md#creating-an-instance).

1. Modifica il file **config-demo.xml** (creato tramite il comando precedente e posizionato accanto al file **config-default.xml**), verifica che i processi **mta** (consegna), **wfserver** (flusso di lavoro), **inMail** (messaggi di rimbalzo) e **stat** (statistiche) siano abilitati, quindi configura l&#39;indirizzo del server delle statistiche **app**:

   ```xml
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Modifica il file **serverConf.xml** e specifica il dominio di consegna, quindi specifica gli indirizzi IP (o host) dei server DNS utilizzati dal modulo MTA per rispondere alle query DNS di tipo MX.

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >I parametri **nameServers** sono utilizzati solo in Windows.

   Per ulteriori informazioni, consulta [Configurazione del server Campaign](../../installation/using/configuring-campaign-server.md).

1. Copiare il programma di installazione della console client **setup-client-7.XX**, **YYYY.exe** nella cartella **/datakit/nl/eng/jsp**. [Ulteriori informazioni](../../installation/using/client-console-availability-for-windows.md).

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

1. Verificare il modulo **nlserver web** utilizzando l&#39;URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Questo URL consente di accedere alla pagina di download per il programma di configurazione client. [Ulteriori informazioni](../../installation/using/client-console-availability-for-windows.md).

   Immetti l&#39;accesso **internal** e la password associata quando raggiungi la pagina di controllo degli accessi.

   ![](assets/s_ncs_install_access_client.png)

### Installazione e configurazione del server applicazioni 2 {#installing-and-configuring-the-application-server-2}

Applica i seguenti passaggi:

1. Installa il server Adobe Campaign.
1. Copiare i file dell&#39;istanza creata sul server applicazioni 1.

   Manteniamo lo stesso nome di istanza del server applicazioni 1.

1. Modificare **internal** in modo che corrisponda al server applicazioni 1.
1. Collega il database all’istanza:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Modifica il file **config-demo.xml** (creato tramite il comando precedente e posizionato accanto al file **config-default.xml**), verifica che i processi **mta** (consegna), **wfserver** (flusso di lavoro), **inMail** (messaggi di rimbalzo) e **stat** (statistiche) siano abilitati, quindi configura l&#39;indirizzo del server delle statistiche **app**:

   ```xml
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Modifica il file **serverConf.xml** e popola la configurazione DNS del modulo MTA:

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Il parametro **nameServers** è utilizzato solo in Windows.

   Per ulteriori informazioni, consulta [Configurazione del server Campaign](../../installation/using/configuring-campaign-server.md).

1. Avvia i server Adobe Campaign.

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Primo avvio del server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Per Windows: [Primo avvio del server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installazione e configurazione dei server frontali {#installing-and-configuring-the-frontal-servers}

Le procedure di installazione e configurazione sono identiche in entrambi i computer.

I passaggi sono i seguenti:

1. Installare il server Adobe Campaign,
1. Rispetta la procedura di integrazione del server web (IIS, Apache) descritta nelle sezioni seguenti:

   * Per Linux: [Integrazione in un server Web per Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Per Windows: [Integrazione in un server Web per Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Copiare i file **config-demo.xml** e **serverConf.xml** creati durante l&#39;installazione. Nel file **config-demo.xml**, attivare il processo **trackinglogd** e disattivare i processi **mta**, **inmail**, **wfserver** e **stat**.
1. Modifica il file **serverConf.xml** e popola i server di tracciamento ridondanti nei parametri del reindirizzamento:

   ```xml
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Avvia il sito Web e verifica il reindirizzamento dall&#39;URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Il browser deve visualizzare i seguenti messaggi (a seconda dell’URL reindirizzato dal load balancer):

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   o

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Avvio del server Web e test della configurazione](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Per Windows: [Avvio del server Web e test della configurazione](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Avvia il server Adobe Campaign.
