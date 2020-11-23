---
solution: Campaign Classic
product: campaign
title: Distribuzione standard
description: Distribuzione standard
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---


# Distribuzione standard{#standard-deployment}

Per questa configurazione sono necessari tre computer:

* Un server applicazione all&#39;interno della LAN per gli utenti finali (preparazione di campagne, rapporti, ecc.),
* Due server frontali nella rete perimetrale dietro un sistema di bilanciamento del carico.

I due server della rete perimetrale perimetrale DMZ, le pagine mirror e la consegna sono ridondanti per l&#39;elevata disponibilità.

Il server applicazioni della LAN serve gli utenti finali ed esegue tutti i processi ricorrenti (motore del flusso di lavoro). Pertanto, quando i picchi di carico vengono raggiunti sui server frontali, gli utenti dell&#39;applicazione non vengono interessati.

Il server del database può essere ospitato su un computer diverso da questi tre. In caso contrario, il server applicazioni e il server di database condividono lo stesso computer all&#39;interno della LAN, purché il sistema operativo sia supportato da  Adobe Campaign (Linux o Windows).

La comunicazione generale tra server e processi viene eseguita secondo il seguente schema:

![](assets/s_001_ncs_install_standardconfig.png)

Questo tipo di configurazione può gestire un numero elevato di destinatari (da 500.000 a 1.000.000), in quanto il server del database (e la larghezza di banda disponibile) è il fattore di limitazione principale.

## Caratteristiche {#features}

### Vantaggi {#advantages}

* Funzionalità di failover: la capacità di passare i processi a un computer in caso di problemi hardware sull&#39;altro.
* Prestazioni generali migliori, poiché le funzioni MTA e di reindirizzamento possono essere implementate su entrambi i computer dietro un sistema di bilanciamento del carico. Con due MTA attivi e una larghezza di banda sufficiente, è possibile raggiungere una velocità di trasmissione di 100.000 messaggi all&#39;ora.

## Procedura di installazione e configurazione {#installation-and-configuration-steps}

### Prerequisiti {#prerequisites}

* JDK su tutti e tre i computer,
* server Web (IIS, Apache) su entrambi i frons,
* accesso a un server di database su tutti e tre i computer,
* Cassetta postale accessibile tramite POP3,
* Creazione di due alias DNS:

   * il primo esposto al pubblico per il monitoraggio e l&#39;indicazione del sistema di bilanciamento del carico su un indirizzo IP virtuale (VIP) e che viene quindi distribuito ai due server frontali,
   * il secondo è esposto agli utenti interni per l’accesso tramite la console e lo stesso server applicazione.

* Firewall configurato per aprire STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 per  Oracle, 5432 per PostgreSQL, ecc.) porte. Per ulteriori informazioni, vedere la sezione Accesso al [database](../../installation/using/network-configuration.md#database-access).

### Installazione del server applicazione {#installing-the-application-server}

Attenetevi alla procedura per installare un&#39;istanza standalone dal  server applicazioni Adobe Campaign alla creazione del database (passaggio 12). Fare riferimento a [Installazione e configurazione (computer singolo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Poiché il computer non è un server di tracciamento, non tenete conto dell&#39;integrazione con il server Web.

Nei seguenti esempi, i parametri dell&#39;istanza sono:

* Nome dell’istanza: **demo**
* Maschera DNS: **console.campaign.net*** (solo per le connessioni console client e per i rapporti)
* Lingua: Inglese
* Database: **campagna:demo@dbsrv**

### Installazione dei due server frontali {#installing-the-two-frontal-servers}

La procedura di installazione e configurazione è identica su entrambi i computer.

La procedura è la seguente:

1. Installate il server Adobe Campaign .

   Per ulteriori informazioni, consulta [Prerequisiti per l&#39;installazione di Campaign in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Prerequisiti per l&#39;installazione di Campaign in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Seguite la procedura di integrazione con il server Web (IIS, Apache) descritta nelle sezioni seguenti:

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Create l’istanza **demo** . Esistono due modi per farlo:

   * Create l’istanza tramite la console:

      ![](assets/install_create_new_connexion.png)

      Per ulteriori informazioni, consultate [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).

      o

   * Create l&#39;istanza utilizzando le righe di comando:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      Per ulteriori informazioni, vedere [Creazione di un&#39;istanza](../../installation/using/command-lines.md#creating-an-instance).
   Il nome dell&#39;istanza è uguale a quello del server applicazione.

   La connessione al server con il modulo Web **** nlserver (pagine mirror, annullamento dell’iscrizione) verrà effettuata dall’URL del sistema di bilanciamento del carico (tracking.campaign.net).

1. Modificate l&#39; **interno** con lo stesso server applicazione.

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Collegate il database all&#39;istanza:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Nei file **config-default.xml** e **config-demo.xml** , abilitate i moduli **Web**, **trackinglogd** e **mta** .

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Modificate il file **serverConf.xml** e compilate:

   * la configurazione DNS del modulo MTA:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >Il parametro **nameServers** è utilizzato solo in Windows.

      For more on this, refer to [Delivery settings](../../installation/using/campaign-server-configuration.md#delivery-settings).

   * i server di monitoraggio ridondanti nei parametri di reindirizzamento:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      For more on this, refer to [Redundant tracking](../../installation/using/configuring-campaign-server.md#redundant-tracking).

1. Avviate il sito Web e verificate il reindirizzamento dall’URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Il browser deve visualizzare i messaggi seguenti (a seconda dell&#39;URL reindirizzato dal sistema di bilanciamento del carico):

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

1. Avviate il server Adobe Campaign .
1. Nella console Adobe Campaign , effettua la connessione utilizzando il login di **amministratore** senza una password e avvia la procedura guidata di distribuzione.

   Per ulteriori informazioni, vedere [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md).

   La configurazione è identica a un’istanza standalone, a parte la configurazione del modulo di tracciamento.

1. Compilate l’URL esterno (quello del sistema di bilanciamento del carico) utilizzato per il reindirizzamento e gli URL interni dei due server frontali.

   For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Usiamo l’istanza esistente dei due server di tracciamento creati in precedenza e utilizziamo il login **interno** .

