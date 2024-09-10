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
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# Gestione di file e risorse{#file-and-resmanagement}



## Limita il formato del file di caricamento {#limiting-uploadable-files}

Utilizza l&#39;attributo **uploadWhiteList** per limitare i tipi di file disponibili per il caricamento sul server Adobe Campaign.

Questo attributo è disponibile nell&#39;elemento **dataStore** del file **serverConf.xml**. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Il valore predefinito di questo attributo è **.+** e consente di caricare qualsiasi tipo di file.

Per limitare i formati possibili, sostituisci il valore dell’attributo con un’espressione regolare Java valida. È possibile immettere più valori separandoli con una virgola.

Ad esempio: **uploadWhiteList=&quot;.&#42;.png,.&#42;.jpg&quot;** ti consentirà di caricare i formati PNG e JPG sul server. Non verranno accettati altri formati.

È inoltre possibile impedire il caricamento di file importanti configurando il server Web. [Ulteriori informazioni](web-server-configuration.md)

>[!NOTE]
>
>L&#39;attributo **uploadWhiteList** limita i tipi di file disponibili per il caricamento sul server Adobe Campaign. Tuttavia, quando la modalità di pubblicazione è **Server di tracciamento** o **Altri server Adobe Campaign**, anche l&#39;attributo **uploadWhitelist** deve essere aggiornato su tali server.

## Configurazione della connessione proxy {#proxy-connection-configuration}

Puoi connettere il server Campaign a un sistema esterno tramite un proxy, utilizzando ad esempio un&#39;attività del flusso di lavoro **Trasferimento file**. Per ottenere questo risultato, è necessario configurare la sezione **proxyConfig** del file **serverConf.xml** tramite un comando specifico. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Sono possibili le seguenti connessioni proxy: HTTP, HTTPS, FTP, SFTP. A partire dalla versione 20.2 di Campaign, i parametri del protocollo HTTP e HTTPS sono **non più disponibili**. Tali parametri vengono ancora menzionati di seguito in quanto rimangono disponibili nelle build precedenti, incluso 9032.

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

Per attivare la modalità proxy, è necessario apportare la seguente modifica nel file `serverconf.xml`:

```
<nmac useHTTPProxy="true">
```

Per ulteriori informazioni su questo connettore iOS HTTP/2, consulta questa [pagina](../../delivery/using/about-mobile-app-channel.md).

## Gestire le risorse pubbliche {#managing-public-resources}

Per essere disponibili al pubblico, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server accessibile dall’esterno. Possono quindi essere disponibili per destinatari o operatori esterni. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#managing-public-resources).

Le risorse pubbliche sono archiviate nella directory **/var/res/instance** della directory di installazione di Adobe Campaign.

L&#39;URL corrispondente è: **http://server/res/instance** dove **istanza** è il nome dell&#39;istanza di rilevamento.

È possibile specificare un&#39;altra directory aggiungendo un nodo al file **conf-`<instance>`.xml** per configurare l&#39;archiviazione nel server. Ciò significa aggiungere le seguenti righe:

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
