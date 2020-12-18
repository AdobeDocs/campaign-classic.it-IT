---
solution: Campaign Classic
product: campaign
title: Integrazione in un server web per Linux
description: Scopri come integrare Campaign in un server Web (Linux)
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 2%

---


# Integrazione in un server web per Linux{#integration-into-a-web-server-for-linux}

 Adobe Campaign include Apache Tomcat che funge da punto di ingresso nel server dell’applicazione tramite HTTP (e SOAP).

Potete utilizzare questo server Tomcat integrato per soddisfare le richieste HTTP.

In questo caso:

* la porta di ascolto predefinita è 8080. Per modificarlo, fare riferimento a [Configurazione di Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* Le console client si connettono quindi utilizzando un URL come:

   ```
   http://<computer>:8080
   ```

Tuttavia, per motivi di sicurezza e amministrazione, si consiglia di utilizzare un server Web dedicato come punto di ingresso principale per il traffico HTTP quando il computer che esegue  Adobe Campaign è esposto su Internet e si desidera aprire l&#39;accesso alla console all&#39;esterno della rete.

Un server Web consente inoltre di garantire la riservatezza dei dati con il protocollo HTTP.

Analogamente, è necessario utilizzare un server Web quando si desidera utilizzare la funzionalità di tracciamento, disponibile solo come modulo di estensione per un server Web.

>[!NOTE]
>
>Se non utilizzate la funzionalità di tracciamento, potete eseguire un&#39;installazione standard di Apache o IIS con un reindirizzamento a Campaign. Il modulo di estensione del server Web di tracciamento non è richiesto.

## Configurazione del server Web Apache con Debian {#configuring-the-apache-web-server-with-debian}

Questo processo si applica se Apache è stato installato in una distribuzione basata su APT.

Effettuate le seguenti operazioni:

1. Per impostazione predefinita, disattivate i moduli caricati utilizzando il seguente comando:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Assicurarsi che i moduli **alias**, **authz_host** e **mime** siano ancora attivati. A questo scopo, utilizzate il comando seguente:

   ```
   a2enmod  alias authz_host mime
   ```

1. Create il file **nlsrv.load** in **/etc/apache2/mods-available** e inserite il contenuto seguente:

   In Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Create il file **nlsrv.conf** in **/etc/apache2/mods-available** utilizzando il comando seguente:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Attivate questo modulo con il seguente comando:

   ```
    a2enmod nlsrv
   ```

   Se si utilizza il modulo **mod_rewrite** per  pagine Adobe Campaign, è necessario rinominare i file **nlsrv.load** e **nlsrv.conf** in **zz-nlsrv.load** e **zz-nlsrv.conf**. Per attivare il modulo, eseguire il comando seguente:

   ```
   a2enmod zz-nlsrv
   ```

1. Modificate il file **/etc/apache2/envars**, aggiungete le seguenti righe:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Salvare le modifiche.

1. Quindi aggiungete  utenti Adobe Campaign al gruppo di utenti Apache e viceversa utilizzando il seguente tipo di comando:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Riavviate Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## Configurazione del server Web Apache in RHEL {#configuring-apache-web-server-in-rhel}

Questa procedura si applica se avete installato e protetto Apache in un pacchetto basato su RPM (RHEL, CentOS e Suse).

Effettuate le seguenti operazioni:

1. Nel file `httpd.conf`, attivate i seguenti moduli Apache:

   ```
   alias
   authz_host
   mime
   ```

1. Disattivate i seguenti moduli:

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

   Commentare le funzioni collegate ai moduli disattivati:

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

1. Create un file di configurazione  Adobe Campaign specifico nella cartella `/etc/httpd/conf.d/`. Ad esempio `CampaignApache.conf`

1. Per **RHEL7**, aggiungete le seguenti istruzioni nel file:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Per **RHEL7**:

   Aggiungete il file `/etc/systemd/system/httpd.service` con il contenuto seguente:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Aggiornare il modulo utilizzato dal sistema:

   ```
   systemctl daemon-reload
   ```

1. Quindi, aggiungere  operatori Adobe Campaign al gruppo di operatori Apache e viceversa, eseguendo il comando:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   I nomi dei gruppi da utilizzare dipendono dalla configurazione di Apache.

1. Eseguite Apache e il server Adobe Campaign .

   Per RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Avvio del server Web e verifica della configurazione{#launching-the-web-server-and-testing-the-configuration}

È ora possibile verificare la configurazione avviando Apache. Il modulo Adobe Campaign  deve ora visualizzare il banner sulla console (due banner in alcuni sistemi operativi):

```
 /etc/init.d/apache start
```

Vengono visualizzate le informazioni seguenti:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Verificate quindi che risponda inviando un URL di prova.

È possibile eseguire la verifica dalla riga di comando eseguendo:

```
 telnet localhost 80  
```

È necessario ottenere:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

Quindi immettete:

```
GET /r/test
```

Vengono visualizzate le informazioni seguenti:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

È inoltre possibile richiedere l&#39;URL [`https://<computer>`](https://myserver.adobe.com/r/test) da un browser Web.
