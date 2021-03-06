---
product: campaign
title: Gestione di file e risorse
description: Scopri come configurare la gestione di file e risorse in Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 4ff86349d6b8966273585bf2a1ea0d785a7e87cb
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 1%

---

# Gestione di file e risorse{#file-and-resmanagement}

![](../../assets/v7-only.svg)

## Limita il formato del file di caricamento {#limiting-uploadable-files}

Utilizza la **uploadWhiteList** per limitare i tipi di file disponibili per il caricamento sul server Adobe Campaign.

Questo attributo è disponibile all&#39;interno della variabile **dataStore** elemento **serverConf.xml** file. Tutti i parametri disponibili nel **serverConf.xml** sono elencati in [sezione](../../installation/using/the-server-configuration-file.md).

Il valore predefinito di questo attributo è **.+** e consente di caricare qualsiasi tipo di file.

Per limitare i formati possibili, sostituisci il valore dell’attributo con un’espressione regolare java valida. È possibile immettere diversi valori separandoli con una virgola.

Ad esempio: **uploadWhiteList=&quot;.&#42;.png,&#42;.jpg&quot;** consente di caricare i formati PNG e JPG sul server. Non verranno accettati altri formati.

È inoltre possibile impedire il caricamento di file importanti configurando il server Web. [Ulteriori informazioni](web-server-configuration.md)

## Configurazione della connessione proxy {#proxy-connection-configuration}

Puoi collegare il server Campaign a un sistema esterno tramite un proxy utilizzando un **Trasferimento file** ad esempio, l’attività del flusso di lavoro . A questo scopo, devi configurare le **proxyConfig** della sezione **serverConf.xml** tramite un comando specifico. Tutti i parametri disponibili nel **serverConf.xml** sono elencati in [sezione](../../installation/using/the-server-configuration-file.md).

Sono possibili le seguenti connessioni proxy: HTTP, HTTPS, FTP, SFTP. A partire dalla versione 20.2 di Campaign, i parametri del protocollo HTTP e HTTPS sono **non più disponibile**. Tali parametri sono ancora indicati di seguito in quanto rimangono disponibili nelle build precedenti, tra cui 9032.

>[!CAUTION]
>
>È supportata solo la modalità di autenticazione di base. Autenticazione NTLM non supportata.
>
>I proxy SOCKS non sono supportati.

È possibile utilizzare il comando seguente:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

i parametri del protocollo possono essere &quot;http&quot;, &quot;https&quot; o &quot;ftp&quot;.

Se imposti FTP sulla stessa porta del traffico HTTP/HTTPS, puoi utilizzare quanto segue:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Le opzioni &quot;http&quot; e &quot;https&quot; vengono utilizzate solo quando il parametro del protocollo è &quot;ftp&quot; e indicano se il tunneling sulla porta specificata verrà eseguito su HTTPS o su HTTP.

Se utilizzi porte diverse per il traffico FTP/SFTP e HTTP/HTTPS sul server proxy, devi impostare il parametro del protocollo &quot;ftp&quot;.


Ad esempio:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Quindi inserisci la password.

Le connessioni HTTP sono definite nel parametro proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

Le connessioni HTTPS sono definite nel parametro proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

Le connessioni FTP/FTPS sono definite nel parametro proxyFTP:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Se si utilizza lo stesso proxy per diversi tipi di connessione, verrà definito solo il proxyHTTP con useSingleProxy impostato su &quot;1&quot; o &quot;true&quot;.

Se disponi di connessioni interne che devono passare attraverso il proxy, aggiungili nel parametro override.

Se desideri disattivare temporaneamente la connessione proxy, imposta il parametro abilitato su &quot;false&quot; o &quot;0&quot;.

Se devi utilizzare il connettore iOS HTTP/2 tramite un proxy, sono supportate le seguenti modalità proxy HTTP:

* HTTP senza autenticazione
* Autenticazione di base HTTP

Per attivare la modalità proxy, è necessario eseguire la seguente modifica nel `serverconf.xml` file:

```
<nmac useHTTPProxy="true">
```

Per ulteriori informazioni su questo connettore iOS HTTP/2, consulta [page](../../delivery/using/about-mobile-app-channel.md).

## Gestione delle risorse pubbliche {#managing-public-resources}

Per essere disponibili al pubblico, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server accessibile esternamente. Possono quindi essere disponibili per i destinatari o gli operatori esterni. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#managing-public-resources).

Le risorse pubbliche sono memorizzate nella **/var/res/instance** della directory di installazione di Adobe Campaign.

L’URL corrispondente è: **http://server/res/instance** dove **istanza** è il nome dell&#39;istanza di tracciamento.

Puoi specificare un’altra directory aggiungendo un nodo al **conf-`<instance>`.xml** per configurare lo storage sul server. Questo significa aggiungere le seguenti righe:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

In questo caso, il nuovo URL per le risorse pubbliche indicato nella parte superiore della finestra della procedura guidata di distribuzione deve puntare a questa cartella.
