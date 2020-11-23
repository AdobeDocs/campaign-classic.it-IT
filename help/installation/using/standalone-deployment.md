---
solution: Campaign Classic
product: campaign
title: Distribuzione autonoma
description: Distribuzione autonoma
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Distribuzione autonoma{#standalone-deployment}

Questa configurazione include tutti i componenti sullo stesso computer:

* processo applicativo (web),
* processo di consegna (MTA),
* processo di reindirizzamento (tracciamento),
* processo del flusso di lavoro e attività pianificate (wfserver),
* processo di posta indesiderata (inMail),
* processo statistico (stato).

La comunicazione globale tra i processi viene eseguita secondo il seguente schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Questo tipo di configurazione può essere eseguito quando si gestiscono elenchi di meno di 100.000 destinatari e con, ad esempio, i seguenti livelli software:

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

Con la crescita del volume, una variante di questa architettura sposta il server del database su un altro computer per migliorare le prestazioni.

>[!NOTE]
>
>Un server di database esistente può essere utilizzato anche se dispone di risorse sufficienti.

## Caratteristiche {#features}

### Vantaggi {#advantages}

* Costi di configurazione completamente indipendenti e bassi (non sono richieste licenze fatturabili se viene utilizzato il software open-source elencato di seguito).
* Installazione semplificata e configurazione della rete.

### Svantaggi {#disadvantages}

* Un computer critico in caso di incidente.
* Larghezza di banda limitata durante la trasmissione dei messaggi (per esperienza, circa decine di migliaia di messaggi all&#39;ora).
* Potenziale rallentamento dell’applicazione durante la trasmissione.
* Il server applicazione deve essere disponibile dall&#39;esterno (ad esempio, nella rete perimetrale), dal momento che ospita il server di reindirizzamento.

## Procedura di installazione e configurazione {#installation-and-configuration-steps}

### Prerequisiti {#prerequisites}

* JDK,
* Server Web (IIS, Apache),
* accesso a un server di database,
* Cassetta postale accessibile tramite POP3,
* Creazione di due alias DNS:

   * il primo esposto al pubblico per il monitoraggio e l&#39;puntamento al computer sul suo IP pubblico;
   * il secondo alias esposto agli utenti interni per l&#39;accesso alla console e indirizzato allo stesso computer.

* Firewall configurato per aprire SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 per  Oracle, 5432 per PostgreSQL, ecc.) porte. Per ulteriori informazioni, vedere Configurazione [](../../installation/using/network-configuration.md)di rete.

Nei seguenti esempi, i parametri dell&#39;istanza sono:

* Nome dell’istanza: **demo**
* Maschera DNS: **console.campaign.net*** (solo per le connessioni console client e per i rapporti)
* Database: **campagna:demo@dbsrv**

### Installazione e configurazione (computer singolo) {#installing-and-configuring--single-machine-}

Effettuate le seguenti operazioni:

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

   * Per Linux: [Primo avvio del server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Per Windows: [Primo avvio del server](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. Modificate il file **config-demo.xml** (creato nel passaggio precedente accanto a **config-default.xml**) e assicuratevi che i processi **mta** (consegna), **wfserver** (flusso di lavoro), **inMail** **** (messaggi di rimbalzo) e stat (statistiche) siano abilitati. Quindi configurate l&#39;indirizzo del server di statistiche:

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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Modificate il file **serverConf.xml** e specificate il dominio di consegna, quindi specificate gli indirizzi IP (o host) dei server DNS utilizzati dal modulo MTA per rispondere alle query DNS di tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Il parametro **nameServers** è utilizzato solo in Windows.

   Per ulteriori informazioni, consulta Configurazione [del server](../../installation/using/campaign-server-configuration.md)Campaign.

1. Copiate il programma di configurazione della console client (**setup-client-7.XX**, **YYYY.exe** per v7 o **setup-client-6.XX**, **YYYY.exe** per v6.1) nella cartella **/datakit/nl/eng/jsp** .

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Disponibilità della console client per Linux](../../installation/using/client-console-availability-for-linux.md)
   * Per Windows: [Disponibilità della console client per Windows](../../installation/using/client-console-availability-for-windows.md)

1. Seguite la procedura di integrazione con il server Web (IIS, Apache) descritta nelle sezioni seguenti:

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Avviate il sito Web e verificate il reindirizzamento utilizzando l’URL: https://tracking.campaign.net/r/test.

   Il browser deve visualizzare il seguente messaggio:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Avvio del server Web e verifica della configurazione](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Per Windows: [Avvio del server Web e verifica della configurazione](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Verificate il modulo Web **del** server utilizzando l&#39;URL: https://console.campaign.net/nl/jsp/logon.jsp

   Questo URL consente di accedere alla pagina di download per il programma di configurazione client.

   Inserite il login **interno** e la password associata quando raggiungete la pagina di controllo dell&#39;accesso.

   ![](assets/s_ncs_install_access_client.png)

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Disponibilità della console client per Linux](../../installation/using/client-console-availability-for-linux.md)
   * Per Windows: [Disponibilità della console client per Windows](../../installation/using/client-console-availability-for-windows.md)

1. Avviate la console client Adobe Campaign  (dalla pagina di download precedente o avviata direttamente sul server per un&#39;installazione di Windows), impostate l&#39;URL della connessione del server su https://console.campaign.net e collegatevi utilizzando l&#39;accesso **interno** .

   Fare riferimento a [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md) e all&#39;identificatore [](../../installation/using/campaign-server-configuration.md#internal-identifier)interno.

   La creazione guidata del database viene visualizzata al primo accesso:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Seguire i passaggi della procedura guidata e creare il database associato all&#39;istanza di connessione.

   Per ulteriori informazioni, vedere [Creazione e configurazione del database](../../installation/using/creating-and-configuring-the-database.md).

   Una volta creato il database, disconnettetevi.

1. Accedete nuovamente alla console client utilizzando il login di **amministratore** senza una password e avviate la procedura guidata di distribuzione ( **[!UICONTROL Tools > Advanced]** menu) per completare la configurazione dell&#39;istanza.

   Per ulteriori informazioni, vedere [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md).

   I parametri principali da impostare sono i seguenti:

   * Invio e-mail: mittente e indirizzi di risposta e la casella di posta di errore per la posta indesiderata.
   * Tracciamento: Compilate l’URL esterno utilizzato per il reindirizzamento e l’URL interno, fate clic su **Registrazione nei server di tracciamento** e convalidatelo nell’istanza **demo** del server di tracciamento.

      For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Poiché il server Adobe Campaign  viene utilizzato sia come server applicazione che come server di reindirizzamento, l’URL interno utilizzato per raccogliere i registri di tracciamento e trasferire gli URL è una connessione interna diretta a Tomcat (https://localhost:8080).

   * Gestione rimbalzi: Inserite i parametri per gestire la posta **non elaborata (non tenete conto della sezione Posta** non elaborata).
   * Accesso da: Fornire i due URL per report, moduli Web e pagine mirror.

      ![](assets/d_ncs_install_web_url.png)

