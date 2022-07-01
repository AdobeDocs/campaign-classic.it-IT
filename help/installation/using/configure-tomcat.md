---
product: campaign
title: Configurazione di Campaign Tomcat
description: Configurazione di Campaign Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 1%

---

# Configurare Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign utilizza un **servlet web incorporato chiamato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l’applicazione e qualsiasi interfaccia esterna (compresa la console client, i collegamenti URL tracciati, le chiamate SOAP e altri). Spesso è presente davanti a questo un server web esterno (in genere IIS o Apache) per qualsiasi istanza Adobe Campaign rivolta all’esterno.

Scopri di più su Tomcat in Campaign e su come individuare la tua versione Tomcat in [questa pagina](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Questa procedura è limitata a **on-premise** distribuzioni.

## Porta predefinita per Apache Tomcat {#default-port-for-tomcat}

Quando la porta di ascolto 8080 del server Tomcat è già occupata con un&#39;altra applicazione necessaria per la configurazione, è necessario sostituire la porta 8080 con una gratuita (ad esempio 8090). Per modificarlo, modifica il **server.xml** file salvati in **/tomcat-8/conf** della cartella di installazione di Adobe Campaign.

Quindi modifica la porta delle pagine relay JSP. Per eseguire questa operazione, modifica la variabile **serverConf.xml** file salvati in **/conf** della directory di installazione di Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mappare una cartella in Apache Tomcat {#mapping-a-folder-in-tomcat}

Per definire le impostazioni specifiche per il cliente, puoi creare una **user_contexts.xml** nel **/tomcat-8/conf** che contiene anche **contexts.xml** file.

Questo file conterrà il seguente tipo di informazioni:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessario, questa operazione può essere riprodotta sul lato server.

## Nascondere il report di errore Tomcat {#hide-tomcat-error-report}

Per motivi di sicurezza, consigliamo vivamente di nascondere il rapporto di errore Tomcat. Di seguito sono riportati i passaggi da seguire.

1. Apri **server.xml** nel file **/tomcat-8/conf** directory della cartella di installazione di Adobe Campaign:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Aggiungi il seguente elemento in basso dopo tutti gli elementi di contesto esistenti:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```
1. Riavvia il server nlserver e i server web Apache.
