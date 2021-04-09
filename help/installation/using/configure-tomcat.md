---
solution: Campaign Classic
product: campaign
title: Configurazione di Campaign Tomcat
description: Configurazione di Campaign Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 8ab0aab42accbd1253d53e8133f5af0a38c724ea
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Configura Apache Tomcat {#configuring-tomcat}

Adobe Campaign utilizza un **servlet web incorporato denominato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l’applicazione e qualsiasi interfaccia esterna (inclusa la console client, i collegamenti URL tracciati, le chiamate SOAP e altri). Spesso è presente davanti a questo un server web esterno (in genere IIS o Apache) per qualsiasi istanza Adobe Campaign rivolta all’esterno.

Ulteriori informazioni su Tomcat in Campaign e su come individuare la versione Tomcat in [questa pagina](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Questa procedura è limitata alle distribuzioni **on-premise**.


## Porta predefinita per Apache Tomcat {#default-port-for-tomcat}

Quando la porta di ascolto 8080 del server Tomcat è già occupata con un&#39;altra applicazione necessaria per la configurazione, è necessario sostituire la porta 8080 con una gratuita (ad esempio 8090). Per modificarlo, modifica il file **server.xml** salvato nella directory **/tomcat-8/conf** della cartella di installazione di Adobe Campaign.

Quindi modifica la porta delle pagine relay JSP. A questo scopo, modifica il file **serverConf.xml** salvato nella directory **/conf** della directory di installazione di Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mappare una cartella in Apache Tomcat {#mapping-a-folder-in-tomcat}

Per definire le impostazioni specifiche del cliente, è possibile creare un file **user_contexts.xml** nella cartella **/tomcat-8/conf**, che contiene anche il file **contexts.xml**.

Questo file conterrà il seguente tipo di informazioni:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessario, questa operazione può essere riprodotta sul lato server.
