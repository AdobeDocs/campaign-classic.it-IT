---
product: campaign
title: Implementazione standard
description: Implementazione standard
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---

# Implementazione standard{#standard-deployment}

![](../../assets/v7-only.svg)

Per questa configurazione sono necessari tre computer:

* un server applicativo all&#39;interno della LAN per gli utenti finali (preparazione di campagne, reporting, ecc.),
* Due server frontali nella DMZ dietro un load balancer.

I due server della DMZ gestiscono il tracciamento, le pagine mirror e la consegna e sono ridondanti per l&#39;elevata disponibilità.

Il server applicazioni nella LAN serve gli utenti finali ed esegue tutti i processi ricorrenti (motore del flusso di lavoro). Pertanto, quando i carichi di picco vengono raggiunti sui server frontali, gli utenti dell’applicazione non sono interessati.

Il server di database può essere ospitato su un computer separato da questi tre. In caso contrario, il server dell&#39;applicazione e il server del database possono condividere lo stesso computer all&#39;interno della LAN, purché il sistema operativo sia supportato da Adobe Campaign (Linux o Windows).

La comunicazione generale tra server e processi viene eseguita secondo il seguente schema:

![](assets/s_001_ncs_install_standardconfig.png)

Questo tipo di configurazione può gestire un gran numero di destinatari (da 500.000 a 1.000.000) in quanto il server di database (e la larghezza di banda disponibile) è il fattore limitante principale.

## Funzioni {#features}

### Vantaggi {#advantages}

* Funzionalità di failover: la possibilità di passare i processi a un computer in caso di problemi hardware nell&#39;altro.
* Prestazioni generali migliori, poiché le funzioni MTA e di reindirizzamento possono essere implementate su entrambi i computer dietro un load balancer. Con due MTA attivi e una larghezza di banda sufficiente, è possibile raggiungere una velocità di trasmissione di 100.000 mail all&#39;ora.

## Passaggi di installazione e configurazione {#installation-and-configuration-steps}

### Prerequisiti {#prerequisites}

* JDK su tutti e tre i computer,
* server web (IIS, Apache) su entrambi i frontals,
* Accesso a un server di database su tutti e tre i computer,
* Cassetta di posta non recapitata accessibile tramite POP3,
* Creazione di due alias DNS:

   * la prima persona esposta al pubblico per il tracciamento e l’individuazione del load balancer su un indirizzo IP virtuale (VIP) e che viene quindi distribuita ai due server frontali,
   * il secondo è stato esposto agli utenti interni per l’accesso tramite la console e punta allo stesso server applicativo.

* Firewall configurato per aprire STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 per Oracle, 5432 per PostgreSQL, ecc.) porte. Per ulteriori informazioni, consulta la sezione [Accesso al database](../../installation/using/network-configuration.md#database-access).

### Installazione dell&#39;application server {#installing-the-application-server}

Segui i passaggi per installare un’istanza autonoma dal server delle applicazioni Adobe Campaign alla creazione del database (passaggio 12). Fai riferimento a [Installazione e configurazione (computer singolo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Poiché il computer non è un server di tracciamento, non tenere conto dell&#39;integrazione con il server Web.

Negli esempi seguenti, i parametri dell’istanza sono:

* Nome dell’istanza: **demo**
* Maschera DNS: **console.campaign.net*** (solo per le connessioni alla console client e per i rapporti)
* Lingua: Inglese
* Database: **campagna:demo@dbsrv**

### Installazione dei due server frontali {#installing-the-two-frontal-servers}

La procedura di installazione e configurazione è identica su entrambi i computer.

Le fasi sono le seguenti:

1. Installa il server Adobe Campaign.

   Per ulteriori informazioni, consulta [Prerequisiti per l’installazione di Campaign in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Prerequisiti per l’installazione di Campaign in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Segui la procedura di integrazione del server web (IIS, Apache) descritta nelle sezioni seguenti:

   * Per Linux: [Integrazione in un server web per Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Per Windows: [Integrazione in un server Web per Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Crea il **demo** istanza. Ci sono due modi per farlo:

   * Crea l’istanza tramite la console:

      ![](assets/install_create_new_connexion.png)

      Per ulteriori informazioni, consulta [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).

      o

   * Crea l&#39;istanza utilizzando le righe di comando:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      Per ulteriori informazioni, consulta [Creazione di un’istanza](../../installation/using/command-lines.md#creating-an-instance).
   Il nome dell&#39;istanza è lo stesso dell&#39;application server.

   Connessione al server con il **web nlserver** Il modulo (pagine mirror, annullamento dell’abbonamento) verrà creato dall’URL del load balancer (tracking.campaign.net).

1. Modificare la **interno** allo stesso modo dell&#39;application server.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Collega il database all&#39;istanza:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. In **config-default.xml** e **config-demo.xml** file, abilita **web**, **trackinglogd** e **mta** moduli.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Modifica le **serverConf.xml** file e compilazione:

   * la configurazione DNS del modulo MTA:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >La **nameServers** viene utilizzato solo in Windows.

      Per ulteriori informazioni, consulta [Impostazioni di consegna](configure-delivery-settings.md).

   * i server di tracciamento ridondanti nei parametri di reindirizzamento:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      Per ulteriori informazioni, consulta [Tracciamento ridondante](configuring-campaign-server.md#redundant-tracking).

1. Avvia il sito web e verifica il reindirizzamento dall&#39;URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Il browser deve visualizzare i seguenti messaggi (a seconda dell’URL reindirizzato dal load balancer):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   o

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Per ulteriori informazioni, consulta le sezioni seguenti:

   * Per Linux: [Avvio del server Web e verifica della configurazione](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Per Windows: [Avvio del server Web e verifica della configurazione](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Avvia il server Adobe Campaign.
1. Nella console Adobe Campaign, effettua la connessione utilizzando **admin** accedi senza password e avvia la procedura guidata di distribuzione.

   Per ulteriori informazioni, consulta [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md).

   La configurazione è identica a un’istanza autonoma, a parte la configurazione del modulo di tracciamento.

1. Popolare l’URL esterno (quello del load balancer) utilizzato per il reindirizzamento e gli URL interni dei due server frontali.

   Per ulteriori informazioni, consulta [Configurazione del tracciamento](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Utilizziamo l’istanza esistente dei due server di tracciamento creati in precedenza e utilizziamo il **interno** accesso.
