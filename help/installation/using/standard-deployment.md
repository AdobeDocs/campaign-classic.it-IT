---
product: campaign
title: Implementazione standard
description: Implementazione standard
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 3%

---

# Implementazione standard{#standard-deployment}



Per questa configurazione sono necessari tre computer:

* Un server applicazioni nella rete LAN per gli utenti finali (preparazione di campagne, creazione di rapporti, ecc.),
* Due server frontali nella DMZ dietro un load balancer.

I due server nella DMZ gestiscono il tracciamento, le pagine mirror e la distribuzione e sono ridondanti per un&#39;elevata disponibilità.

Il server applicazioni nella LAN è al servizio degli utenti finali ed esegue tutti i processi ricorrenti (motore del flusso di lavoro). Pertanto, quando si raggiungono i picchi di carico sui server frontali, gli utenti dell’applicazione non sono interessati.

Il server di database può essere ospitato in un computer separato da questi tre. In caso contrario, il server applicazioni e il server database condividono lo stesso computer nella LAN, purché il sistema operativo sia supportato da Adobe Campaign (Linux o Windows).

La comunicazione generale tra server e processi viene eseguita in base allo schema seguente:

![](assets/s_001_ncs_install_standardconfig.png)

Questo tipo di configurazione è in grado di gestire un numero elevato di destinatari (da 500.000 a 1.000.000) poiché il server del database (e la larghezza di banda disponibile) rappresenta il principale fattore di limitazione.

## Funzioni {#features}

### Vantaggi {#advantages}

* Funzionalità di failover: possibilità di passare da un computer all&#39;altro in caso di problemi hardware.
* Migliori prestazioni complessive, poiché le funzioni MTA e di reindirizzamento possono essere implementate su entrambi i computer dietro un load balancer. Con due MTA attivi e una larghezza di banda sufficiente, è possibile raggiungere tassi di trasmissione nell’area di 100.000 mail all’ora.

## Passaggi per l’installazione e la configurazione {#installation-and-configuration-steps}

### Prerequisiti {#prerequisites}

* JDK su tutti e tre i computer,
* Server web (IIS, Apache) su entrambi i frontali,
* Accesso a un server di database su tutti e tre i computer,
* Cassetta postale di mancato recapito accessibile tramite POP3,
* Creazione di due alias DNS:

   * il primo esposto al pubblico per il tracciamento e il puntamento al load balancer su un indirizzo IP virtuale (VIP) e che viene quindi distribuito ai due server frontali,
   * il secondo esposto agli utenti interni per l’accesso tramite la console e che punta allo stesso application server.

* Firewall configurato per aprire STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 ad Oracle, 5432 per PostgreSQL, ecc.) porte. Per ulteriori informazioni, vedere la sezione [Accesso al database](../../installation/using/network-configuration.md#database-access).

### Installazione del server applicazioni {#installing-the-application-server}

Segui i passaggi per installare un’istanza autonoma dal server applicazioni Adobe Campaign alla creazione del database (passaggio 12). Fare riferimento a [Installazione e configurazione (computer singolo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Poiché il computer non è un server di tracciamento, non prendere in considerazione l&#39;integrazione con il server Web.

Negli esempi seguenti, i parametri della variante sono:

* Nome dell&#39;istanza: **demo**
* Maschera DNS: **console.campaign.net&#42;** (solo per le connessioni della console client e per i report)
* Lingua: inglese
* Database: **campagna:demo@dbsrv**

### Installazione dei due server frontali {#installing-the-two-frontal-servers}

La procedura di installazione e configurazione è identica in entrambi i computer.

I passaggi sono i seguenti:

1. Installa il server Adobe Campaign.

   Per ulteriori informazioni, consulta [Prerequisiti per l&#39;installazione di Campaign in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Prerequisiti per l&#39;installazione di Campaign in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Segui la procedura di integrazione del server web (IIS, Apache) descritta nelle sezioni seguenti:

   * Per Linux: [Integrazione in un server Web per Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Per Windows: [Integrazione in un server Web per Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Crea l&#39;istanza **demo**. Esistono due modi per farlo:

   * Crea l’istanza tramite la console:

     ![](assets/install_create_new_connexion.png)

     Per ulteriori informazioni, consulta [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).

     o

   * Crea l’istanza utilizzando le righe di comando:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     Per ulteriori informazioni, consulta [Creazione di un&#39;istanza](../../installation/using/command-lines.md#creating-an-instance).

   Il nome dell&#39;istanza è uguale a quello del server applicazioni.

   La connessione al server con il modulo **nlserver web** (pagine mirror, annullamento abbonamento) verrà effettuata dall&#39;URL del load balancer (tracking.campaign.net).

1. Modificare **internal** nello stesso modo del server applicazioni.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Collega il database all’istanza:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Nei file **config-default.xml** e **config-demo.xml**, abilita i moduli **web**, **trackinglogd** e **mta**.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Modifica il file **serverConf.xml** e popola:

   * la configurazione DNS del modulo MTA:

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >Il parametro **nameServers** è utilizzato solo in Windows.

     Per ulteriori informazioni, consulta [Impostazioni di consegna](configure-delivery-settings.md).

   * i server di tracciamento ridondanti nei parametri di reindirizzamento:

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     Per ulteriori informazioni, consulta [Tracciamento ridondante](configuring-campaign-server.md#redundant-tracking).

1. Avviare il sito Web e verificare il reindirizzamento dall&#39;URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Il browser deve visualizzare i seguenti messaggi (a seconda dell’URL reindirizzato dal load balancer):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   o

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Avvio del server Web e test della configurazione](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Per Windows: [Avvio del server Web e test della configurazione](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Avvia il server Adobe Campaign.
1. Nella console Adobe Campaign, connettiti utilizzando l&#39;accesso **admin** senza password e avvia la procedura guidata di distribuzione.

   Per ulteriori informazioni, consulta [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md).

   La configurazione è identica a un’istanza indipendente, a parte la configurazione del modulo di tracciamento.

1. Popola l’URL esterno (quello del load balancer) utilizzato per il reindirizzamento e gli URL interni dei due server frontali.

   Per ulteriori informazioni, consulta [Configurazione del tracciamento](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Utilizziamo l&#39;istanza esistente dei due server di monitoraggio creati in precedenza e utilizziamo l&#39;accesso **internal**.
