---
solution: Campaign Classic
product: campaign
title: Distribuzione aziendale
description: Distribuzione aziendale
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 0%

---


# Distribuzione aziendale{#enterprise-deployment}

Questa è la configurazione più completa. Si basa sulla configurazione standard per una maggiore sicurezza e disponibilità:

* server di reindirizzamento dedicati dietro un sistema di bilanciamento del carico HTTP o TCP, per scalabilità e disponibilità,
* due server applicativi per una maggiore capacità di throughput e failover (tolleranza di errore) e isolati nella LAN.

La comunicazione generale tra server e processi viene eseguita secondo il seguente schema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Con questo tipo di configurazione, il throughput previsto può superare i 100.000 messaggi all&#39;ora con larghezza di banda e sintonizzazione adeguate.

## Caratteristiche {#features}

### Vantaggi {#advantages}

* Protezione ottimizzata: Nel computer della rete perimetrale sono installati solo i server che devono essere esposti all&#39;esterno.
* Alta disponibilità più semplice da garantire: Solo il computer visibile dall&#39;esterno deve essere gestito tenendo presente l&#39;elevata disponibilità.

### Svantaggi {#disadvantages}

Costi hardware e amministrativi più elevati.

### Apparecchiature consigliate {#recommended-equipment}

* Server applicazioni: 2 Ghz quad-core CPU, 4 GB di RAM, software RAID 1 disco rigido SATA da 80 GB.
* Server di reindirizzamento: 2 Ghz quad-core CPU, 4 GB di RAM, software RAID 1 disco rigido SATA da 80 GB.

>[!NOTE]
>
>È possibile riutilizzare un sistema di bilanciamento del carico esistente per il traffico verso i server di reindirizzamento.

## Procedura di installazione e configurazione {#installation-and-configuration-steps}

### Prerequisiti {#prerequisites}

* JDK su entrambi i server applicazioni,
* server Web (IIS, Apache) su entrambi i frons,
* accesso a un server di database su entrambi i server applicazioni,
* Cassetta postale accessibile tramite POP3,
* Creazione di due alias DNS sul sistema di bilanciamento del carico:

   * il primo esposto al pubblico per il monitoraggio e l&#39;indicazione del sistema di bilanciamento del carico su un indirizzo IP virtuale (VIP) e che viene quindi distribuito ai due server frontali,
   * il secondo è esposto agli utenti interni per l&#39;accesso tramite la console e indica un sistema di bilanciamento del carico su un indirizzo IP virtuale (VIP), che viene quindi distribuito ai due server applicazione.

* Firewall configurato per aprire STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 per  Oracle, 5432 per PostgreSQL, ecc.) porte. Per ulteriori informazioni, vedere la sezione Accesso al [database](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Se i server applicazioni puntano a una singola istanza di database, dopo l&#39;importazione di un pacchetto standard in un&#39;istanza, lo schema contenuto nel pacchetto non viene caricato nell&#39;altra istanza.
>  
>Se i server applicazioni puntano a una singola istanza di database, dopo la modifica dello schema in un&#39;istanza, lo schema non viene caricato nell&#39;altra istanza.
>
>Per risolvere questi problemi, è necessario riavviare il processo ‘web@default’ nella seconda istanza in cui si è verificato un errore.

### Installazione e configurazione del server applicazione 1 {#installing-and-configuring-the-application-server-1}

Nei seguenti esempi, i parametri dell&#39;istanza sono:

* Nome dell’istanza: demo
* Maschera DNS: tracking.campaign.net*, console.campaign.net* (il server dell’applicazione gestisce gli URL per connessioni e rapporti della console client e per pagine mirror e pagine senza iscrizione)
* Lingua: Inglese
* Database: campagna:demo@dbsrv

I passaggi per l&#39;installazione del primo server sono:

1. Seguite la procedura di installazione per il server Adobe Campaign : **pacchetto nlserver** in Linux o **setup.exe** in Windows.

   Per ulteriori informazioni, consulta [Prerequisiti per l&#39;installazione di Campaign in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Prerequisiti per l&#39;installazione di Campaign in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Una volta installato il server Adobe Campaign , avviate il server applicazione (web) utilizzando il **server di comando web -tomcat** (il modulo Web consente di avviare Tomcat in modalità server Web indipendente in ascolto sulla porta 8080) e per assicurarsi che Tomcat avvii correttamente:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >La prima volta che il modulo Web viene eseguito, crea i file **config-default.xml** e **serverConf.xml** nella directory **conf** all&#39;interno della cartella di installazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

   Premere **Ctrl+C** per arrestare il server.

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Primo avvio del server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Per Windows: [Primo avvio del server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Modificare la password **interna** utilizzando il comando:

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Create l’istanza **demo** con le maschere DNS per il tracciamento (in questo caso, **tracking.campaign.net**) e l’accesso alle console client (in questo caso, **console.campaign.net**). Esistono due modi per farlo:

   * Create l’istanza tramite la console:

      ![](assets/install_create_new_connexion.png)

      Per ulteriori informazioni, consultate [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).

      o

   * Create l&#39;istanza utilizzando le righe di comando:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      Per ulteriori informazioni, vedere [Creazione di un&#39;istanza](../../installation/using/command-lines.md#creating-an-instance).

1. Modificate il file **config-demo.xml** (creato tramite il comando precedente e situato accanto al file **config-default.xml** ), verificate che i processi **mta** (consegna), **wfserver** (flusso di lavoro), **inMail** **** **** (messaggi di rimbalzo) estat(statistiche) siano abilitati, quindi configurate l&#39;indirizzo del server di statistiche di appapp:

   ```
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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Modificate il file **serverConf.xml** e specificate il dominio di consegna, quindi specificate gli indirizzi IP (o host) dei server DNS utilizzati dal modulo MTA per rispondere alle query DNS di tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >I parametri **nameServers** vengono utilizzati solo in Windows.

   Per ulteriori informazioni, consulta Configurazione [del server](../../installation/using/campaign-server-configuration.md)Campaign.

1. Copiate il programma di configurazione della console client (**setup-client-7.XX**, **YYYY.exe** per v7 o **setup-client-6.XX**, **YYYY.exe** per v6.1) nella cartella **/datakit/nl/eng/jsp** .

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Disponibilità della console client per Linux](../../installation/using/client-console-availability-for-linux.md)
   * Per Windows: [Disponibilità della console client per Windows](../../installation/using/client-console-availability-for-windows.md).

1. Avviate il server Adobe Campaign  (**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux) ed eseguite di nuovo **nlserver pdump** per verificare la presenza di tutti i moduli abilitati.

   >[!NOTE]
   >
   >A partire da 20.1, si consiglia di utilizzare il seguente comando (per Linux): **system start nlserver**


   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Questo comando consente inoltre di conoscere la versione e il numero di build del server Adobe Campaign  installato sul computer.

1. Verificate il modulo Web **del** server utilizzando l&#39;URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Questo URL consente di accedere alla pagina di download per il programma di configurazione client.

   Inserite il login **interno** e la password associata quando raggiungete la pagina di controllo dell&#39;accesso.

   ![](assets/s_ncs_install_access_client.png)

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Disponibilità della console client per Linux](../../installation/using/client-console-availability-for-linux.md)
   * Per Windows: [Disponibilità della console client per Windows](../../installation/using/client-console-availability-for-windows.md)

### Installazione e configurazione del server applicazione 2 {#installing-and-configuring-the-application-server-2}

Effettuate le seguenti operazioni:

1. Installate il server Adobe Campaign .
1. Copiare i file dell&#39;istanza creata sul server applicazione 1.

   Manteniamo lo stesso nome di istanza del server applicazione 1.

1. Modificate l&#39; **interno** nello stesso modo del server applicazione 1.
1. Collegate il database all&#39;istanza:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Modificate il file **config-demo.xml** (creato tramite il comando precedente e situato accanto al file **config-default.xml** ), verificate che i processi **mta** (consegna), **wfserver** (flusso di lavoro), **inMail** **** **** (messaggi di rimbalzo) estat(statistiche) siano abilitati, quindi configurate l&#39;indirizzo del server di statistiche di appapp:

   ```
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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Modificate il file **serverConf.xml** e compilate la configurazione DNS del modulo MTA:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Il parametro **nameServers** è utilizzato solo in Windows.

   Per ulteriori informazioni, consulta Configurazione [del server](../../installation/using/campaign-server-configuration.md)Campaign.

1. Avviate i server Adobe Campaign .

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Primo avvio del server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Per Windows: [Primo avvio del server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installazione e configurazione dei server frontali {#installing-and-configuring-the-frontal-servers}

Le procedure di installazione e configurazione sono identiche su entrambi i computer.

La procedura è la seguente:

1. Installare il server Adobe Campaign ,
1. Conformarsi alla procedura di integrazione con il server Web (IIS, Apache) descritta nelle sezioni seguenti:

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Copiate i file **config-demo.xml** e **serverConf.xml** creati durante l&#39;installazione. Nel file **config-demo.xml** , attivate il processo **trackinglogd** e disattivate i processi **mta**, **inmail**, **wfserver** **** estat.
1. Modificate il file **serverConf.xml** e compilate i server di tracciamento ridondanti nei parametri del reindirizzamento:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Avviate il sito Web e verificate il reindirizzamento dall’URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Il browser deve visualizzare i messaggi seguenti (a seconda dell&#39;URL reindirizzato dal sistema di bilanciamento del carico):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   o

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Avvio del server Web e verifica della configurazione](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Per Windows: [Avvio del server Web e verifica della configurazione](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Avviate il server Adobe Campaign .

