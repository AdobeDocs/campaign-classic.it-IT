---
product: campaign
title: Individuare la versione Tomcat in Adobe Campaign
description: Scopri come individuare la versione corrente del servlet web Tomcat incorporato utilizzato in un’istanza di Adobe Campaign
feature: Monitoring
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Individua versione Tomcat{#locate-tomcat-version}



Adobe Campaign utilizza un **servlet web incorporato denominato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l’applicazione e qualsiasi interfaccia esterna (inclusa la console client, i collegamenti URL tracciati, le chiamate SOAP e altre). Di fronte a questo server spesso è presente un server web esterno (in genere IIS o Apache) per tutte le istanze Adobe Campaign rivolte all’esterno.

Seguire la procedura riportata di seguito per individuare la versione esatta di Tomcat utilizzata in un **Istanza on-premise di Campaign Classic** per facilitare la risoluzione dei problemi.

## Tomcat utilizzato in Adobe Campaign

Tomcat viene eseguito su Java e richiede l’installazione di JDK. Per ulteriori informazioni, consulta Java Development Kit (JDK) in [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md) sezione.

Il Tomcat utilizzato in Adobe Campaign è una versione incorporata personalizzata che non utilizza tutte le funzioni della versione completa generalmente disponibile di Tomcat e potrebbe non soffrire di tutte le vulnerabilità della versione completa. Inoltre, Tomcat non deve essere esposto a Internet esterno e tutte le istanze Adobe Campaign esposte devono avere un server web esterno (IIS, Apache, ecc.) di fronte al Tomcat per proteggerlo.

Le versioni nuove o aggiornate delle versioni incorporate di Tomcat vengono rilasciate solo con nuove build di Adobe Campaign e non come patch separate al di fuori delle build di Adobe Campaign.

## Come individuare la versione di Tomcat incorporata

Per individuare la versione di Tomcat incorporata in un’istanza di Adobe Campaign, effettua le seguenti operazioni.

>[!NOTE]
>
>Devi avere accesso ai file sul server Adobe Campaign che devi controllare. La procedura descritta di seguito si applica solo a **modelli di hosting on-premise**.

1. Accedi a *\tomcat-7\lib* sottocartella nella cartella di installazione di Adobe Campaign (ad esempio, *File C:\Program\ [Installation_folder]* in Windows, oppure */usr/local/neolane/nl6* in Linux).

1. Copiare il file *catalina.jar* in una cartella temporanea esterna (ad esempio sul desktop) e rinomina l’estensione da .jar a .zip.

1. Decomprimi il file copiato. Ne risulteranno molte sottocartelle e file.

1. All’interno dei file/cartelle decompressi, apri o leggi il seguente file contenuto utilizzando un editor di testo: *org/apache/catalina/util/ServerInfo.properties*. Potrebbe essere necessario aggiungere un’estensione .txt per facilitare l’apertura con un editor di testo.

1. Al termine, se si trova su un server, eliminare i file temporanei creati.

Ad esempio, *ServerInfo.properties* il file per Adobe Campaign conterrà le seguenti informazioni, che indicano Tomcat v8.5.X:

*`server.info=Apache Tomcat/8.5.X`*

*`server.number=8.5.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Una volta che sei in grado di stabilire la versione esatta di Tomcat utilizzata in una particolare istanza, potrebbe aiutarti nella risoluzione dei problemi relativi a Tomcat.

>[!NOTE]
>
>La versione principale della Tomcat incorporata viene aggiornata solo quando cambia la versione principale di Adobe Campaign (anche se le versioni precedenti potrebbero non essere più ufficialmente supportate, le informazioni potrebbero essere utili in quanto alcuni clienti potrebbero ancora eseguire queste versioni).
>

