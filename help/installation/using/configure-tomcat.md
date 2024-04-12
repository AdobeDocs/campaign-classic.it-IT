---
product: campaign
title: Configurazione di Campaign Tomcat
description: Configurazione di Campaign Tomcat
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Configurare Apache Tomcat {#configuring-tomcat}



Adobe Campaign utilizza un **servlet web incorporato denominato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l’applicazione e qualsiasi interfaccia esterna (inclusa la console client, i collegamenti URL tracciati, le chiamate SOAP e altre). Di fronte a questo server spesso è presente un server web esterno (in genere IIS o Apache) per tutte le istanze Adobe Campaign rivolte all’esterno.

Ulteriori informazioni su Tomcat in Campaign e su come individuare la versione Tomcat in [questa pagina](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Questa procedura è limitata a **on-premise** distribuzioni.
>

## Porta predefinita per Apache Tomcat {#default-port-for-tomcat}

Quando la porta di ascolto 8080 del server Tomcat è già occupata con un&#39;altra applicazione necessaria per la configurazione, è necessario sostituire la porta 8080 con una libera (ad esempio, 8090). Per modificarlo, modifica il **server.xml** file salvato in **/tomcat-8/conf** della cartella di installazione di Adobe Campaign.

Quindi modifica la porta delle pagine di inoltro JSP. Per eseguire questa operazione, modifica il **serverConf.xml** file salvato in **/conf** directory della directory di installazione di Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mappare una cartella in Apache Tomcat {#mapping-a-folder-in-tomcat}

Per definire le impostazioni specifiche del cliente, puoi creare un’ **user_contexts.xml** file in **/tomcat-8/conf** cartella, che contiene anche **contexts.xml** file.

Questo file conterrà il seguente tipo di informazioni:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessario, questa operazione può essere riprodotta sul lato server.

## Nascondi il report di errori Tomcat {#hide-tomcat-error-report}

Per motivi di sicurezza, si consiglia vivamente di nascondere il rapporto di errore Tomcat. Ecco i passaggi.

1. Apri **server.xml** file che si trova in **/tomcat-8/conf** directory della cartella di installazione di Adobe Campaign:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Aggiungi il seguente elemento in basso dopo tutti gli elementi contestuali esistenti:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Riavvia nlserver e i server web Apache.
