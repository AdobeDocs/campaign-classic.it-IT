---
product: campaign
title: Integrazione in un server web per Linux
description: Scopri come integrare Campaign in un server web (Linux)
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 0e88ac270423ad419237264e562a03ab0c42efb5
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Integrazione in un server web per Linux {#integration-into-a-web-server-for-linux}


Adobe Campaign include Apache Tomcat che funge da punto di ingresso nel server applicazioni tramite HTTP (e SOAP).

Puoi utilizzare questo server Tomcat integrato per soddisfare le richieste HTTP.

In questo caso:

* la porta di ascolto predefinita è 8080. Per modificarlo, fare riferimento a [questa sezione](configure-tomcat.md).
* Le console client si connettono quindi utilizzando un URL come:

  ```
  https://<computer>:8080
  ```

Tuttavia, per motivi di sicurezza e amministrazione, si consiglia di utilizzare un server Web dedicato come punto di ingresso principale per il traffico HTTP quando il computer che esegue Adobe Campaign è esposto su Internet e si desidera aprire l&#39;accesso alla console al di fuori della rete.

Un server web consente inoltre di garantire la riservatezza dei dati con il protocollo HTTP.

Allo stesso modo, è necessario utilizzare un server Web quando si desidera utilizzare la funzionalità di tracciamento, disponibile solo come modulo di estensione per un server Web.

>[!NOTE]
>
>Se non utilizzi la funzionalità di tracciamento, puoi eseguire un’installazione standard di Apache o IIS con un reindirizzamento a Campaign. Il modulo di estensione del server Web di tracciamento non è richiesto.

## Configurazione del server web Apache con Debian {#configuring-the-apache-web-server-with-debian}

Questo processo si applica se Apache è stato installato in una distribuzione basata su APT.

Applica i seguenti passaggi:

1. Disattiva i moduli caricati per impostazione predefinita utilizzando il comando seguente:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Assicurati che **alias**, **authz_host** e **mime** I moduli sono ancora abilitati. A questo scopo, utilizza il seguente comando:

   ```
   a2enmod  alias authz_host mime
   ```

1. Creare il file **nlsrv.load** in **/etc/apache2/mods-available** e inserisci il seguente contenuto:

   In Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Creare il file **nlsrv.conf** in **/etc/apache2/mods-available** utilizzando il comando seguente:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Attiva questo modulo con il seguente comando:

   ```
    a2enmod nlsrv
   ```

   Se utilizzi il **mod_rewrite** per le pagine Adobe Campaign, è necessario rinominare il **nlsrv.load** e **nlsrv.conf** file in **zz-nlsrv.load** e **zz-nlsrv.conf**. Per attivare il modulo, esegui il comando seguente:

   ```
   a2enmod zz-nlsrv
   ```

1. Modifica il **/etc/apache2/envars** , aggiungere le righe seguenti:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Salva le modifiche.

1. Quindi aggiungi gli utenti Adobe Campaign al gruppo di utenti Apache e viceversa utilizzando il seguente tipo di comando:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Riavvia Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## Configurazione del server web Apache in RHEL {#configuring-apache-web-server-in-rhel}

Questa procedura si applica se Apache è stato installato e protetto in un pacchetto basato su RPM (RHEL, CentOS e Suse).

Applica i seguenti passaggi:

1. In `httpd.conf` , attiva i seguenti moduli Apache:

   ```
   alias
   authz_host
   mime
   ```

1. Disattiva i seguenti moduli:

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   Commenta le funzioni collegate ai moduli disattivati:

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. Creare un file di configurazione specifico di Adobe Campaign in `/etc/httpd/conf.d/` cartella. Ad esempio `CampaignApache.conf`

1. Per **RHEL7**, aggiungi le seguenti istruzioni nel file:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Per **RHEL7**:

   Aggiungi il `/etc/systemd/system/httpd.service` file con il seguente contenuto:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Aggiorna il modulo utilizzato dal sistema:

   ```
   systemctl daemon-reload
   ```

1. Quindi aggiungi gli operatori Adobe Campaign al gruppo di operatori Apache e viceversa, eseguendo il comando:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   I nomi dei gruppi da utilizzare dipendono dalla configurazione di Apache.

1. Esegui Apache e il server Adobe Campaign.

   Per RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Avvio del server web e verifica della configurazione{#launching-the-web-server-and-testing-the-configuration}

Ora puoi testare la configurazione avviando Apache. Il modulo Adobe Campaign ora deve mostrare il proprio banner sulla console (due banner su alcuni sistemi operativi):

```
 /etc/init.d/apache start
```

Vengono visualizzate le seguenti informazioni:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Verifica quindi che risponda inviando un URL di test.

Puoi eseguire il test dalla riga di comando eseguendo:

```
 telnet localhost 80  
```

È necessario ottenere:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

Quindi immetti:

```
GET /r/test
```

Vengono visualizzate le seguenti informazioni:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

Puoi anche richiedere l’URL `https://myserver.adobe.com/r/test` da un browser Web.
