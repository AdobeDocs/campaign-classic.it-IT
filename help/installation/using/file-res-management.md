---
product: campaign
title: Gestione di file e risorse
feature: Installation, Application Settings
description: Scopri come configurare la gestione di file e risorse in Campaign
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# Gestione di file e risorse{#file-and-resmanagement}



## Limita il formato del file di caricamento {#limiting-uploadable-files}

Utilizza il **uploadWhiteList** per limitare i tipi di file disponibili per il caricamento sul server Adobe Campaign.

Questo attributo è disponibile all&#39;interno di **dataStore** elemento del **serverConf.xml** file. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questo [sezione](../../installation/using/the-server-configuration-file.md).

Il valore predefinito di questo attributo è **.+** e consente di caricare qualsiasi tipo di file.

Per limitare i formati possibili, sostituisci il valore dell’attributo con un’espressione regolare Java valida. È possibile immettere più valori separandoli con una virgola.

Ad esempio: **uploadWhiteList=&quot;.&#42;.png,.&#42;.jpg&quot;** consente di caricare i formati PNG e JPG sul server. Non verranno accettati altri formati.

È inoltre possibile impedire il caricamento di file importanti configurando il server Web. [Ulteriori informazioni](web-server-configuration.md)

>[!NOTE]
>
>Il **uploadWhiteList** attribute limita i tipi di file disponibili per il caricamento sul server Adobe Campaign. Tuttavia, quando la modalità di pubblicazione è **Server di tracciamento** o **Altri server Adobe Campaign**, il **uploadWhitelist** deve essere aggiornato anche su tali server.

## Configurazione della connessione proxy {#proxy-connection-configuration}

Puoi collegare il server Campaign a un sistema esterno tramite un proxy, utilizzando un’ **Trasferimento file** attività del flusso di lavoro, ad esempio. A questo scopo, devi configurare il **proxyConfig** sezione del **serverConf.xml** mediante un comando specifico. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questo [sezione](../../installation/using/the-server-configuration-file.md).

Sono possibili le seguenti connessioni proxy: HTTP, HTTPS, FTP, SFTP. A partire dalla versione 20.2 di Campaign, i parametri del protocollo HTTP e HTTPS sono **non più disponibile**. Tali parametri vengono ancora menzionati di seguito in quanto rimangono disponibili nelle build precedenti, incluso 9032.

>[!CAUTION]
>
>È supportata solo la modalità di autenticazione di base. Autenticazione NTLM non supportata.
>
>I proxy SOCKS non sono supportati.
>

È possibile utilizzare il comando seguente:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

i parametri del protocollo possono essere &quot;http&quot;, &quot;https&quot; o &quot;ftp&quot;.

Se imposti un FTP sulla stessa porta del traffico HTTP/HTTPS, puoi utilizzare quanto segue:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Le opzioni &quot;http&quot; e &quot;https&quot; vengono utilizzate solo quando il parametro del protocollo è &quot;ftp&quot; e indicano se il tunneling sulla porta specificata verrà eseguito su HTTPS o su HTTP.

Se utilizzi porte diverse per il traffico FTP/SFTP e HTTP/HTTPS sul server proxy, devi impostare il parametro del protocollo ‘ftp’.


Ad esempio:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Immettere quindi la password.

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

Se si utilizza lo stesso proxy per diversi tipi di connessione, solo il proxyHTTP verrà definito con useSingleProxy impostato su &quot;1&quot; o &quot;true&quot;.

Se disponi di connessioni interne che non devono passare attraverso il proxy, aggiungile nel parametro di override.

Se si desidera disattivare temporaneamente la connessione proxy, impostare il parametro abilitato su &quot;false&quot; o &quot;0&quot;.

Se devi utilizzare il connettore iOS HTTP/2 tramite un proxy, sono supportate le seguenti modalità proxy HTTP:

* HTTP senza autenticazione
* autenticazione HTTP di base

Per attivare la modalità proxy, è necessario apportare la seguente modifica nel `serverconf.xml` file:

```
<nmac useHTTPProxy="true">
```

Per ulteriori informazioni su questo connettore iOS HTTP/2, consulta questa [pagina](../../delivery/using/about-mobile-app-channel.md).

## Gestire le risorse pubbliche {#managing-public-resources}

Per essere disponibili al pubblico, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server accessibile dall’esterno. Possono quindi essere disponibili per destinatari o operatori esterni. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#managing-public-resources).

Le risorse pubbliche sono memorizzate in **/var/res/instance** directory della directory di installazione di Adobe Campaign.

L’URL corrispondente è: **http://server/res/instance** dove **istanza** è il nome dell’istanza di tracciamento.

È possibile specificare un&#39;altra directory aggiungendo un nodo al **conf-`<instance>`.xml** per configurare l&#39;archiviazione sul server. Ciò significa aggiungere le seguenti righe:

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

In questo caso, il nuovo URL per le risorse pubbliche fornito nella parte superiore della finestra della procedura guidata di distribuzione deve puntare a questa cartella.
