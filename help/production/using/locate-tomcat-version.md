---
solution: Campaign Classic
product: campaign
title: Individuare la versione Tomcat in  Adobe Campaign
description: Scoprite come scoprire la versione corrente del servlet Web Tomcat incorporato utilizzato in un'istanza di  Adobe Campaign.
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 49e49d5e35d14a31236cc4f78188cdf77353fbbf
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# Individuazione della versione Tomcat{#locate-tomcat-version}

 Adobe Campaign utilizza un **servlet Web incorporato denominato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l&#39;applicazione e qualsiasi interfaccia esterna (inclusa la console client, i collegamenti URL tracciati, le chiamate SOAP e altri). Spesso davanti a questo è presente un server Web esterno (in genere IIS o Apache) per tutte le istanze Adobe Campaign  esterne.

Seguire la procedura seguente per scoprire la versione esatta di Tomcat utilizzata in un **Campaign Classic on-premise instance** per facilitare la risoluzione dei problemi.

## Tomcat utilizzato in  Adobe Campaign

Tomcat viene eseguito su Java e richiede l&#39;installazione di JDK. Per ulteriori informazioni, vedi Java Development Kit (JDK) nella sezione [Campaign Compatibilità Matrix](../../rn/using/compatibility-matrix.md).

Il Tomcat utilizzato in  Adobe Campaign è una versione incorporata personalizzata che non utilizza tutte le caratteristiche del rilascio completo disponibile di Tomcat, e potrebbe non subire tutte le vulnerabilità della versione completa. Il Tomcat non dovrebbe essere esposto anche a Internet esterno, e le istanze Adobe Campaign  esposte dovrebbero avere un server Web esterno (IIS, Apache, ecc.) davanti al Tomcat per proteggerlo.

Le versioni nuove o aggiornate delle versioni incorporate di Tomcat vengono rilasciate solo con nuove build di  Adobe Campaign stesso e non come patch separate al di fuori delle  build Adobe Campaign.

## Come individuare la versione di Tomcat incorporato

Per individuare la versione di Tomcat incorporato in un&#39;istanza di  Adobe Campaign, procedere come segue.

>[!NOTE]
>
>È necessario avere accesso ai file sul server Adobe Campaign  che è necessario controllare. La procedura descritta di seguito si applica solo ai **modelli di hosting locali**.

1. Andate alla sottocartella *\tomcat-7\lib* all&#39;interno della cartella di installazione  Adobe Campaign (ad esempio, *C:\Program Files\ [Installation_folder]* in Windows oppure */usr/local/neolane/nl6* in Linux).

   Se state eseguendo una versione precedente di  Adobe Campaign con Tomcat v6, utilizzate *\tomcat-6\lib*.

1. Copiate il file *catalina.jar* in una cartella temporanea esterna (ad esempio, il desktop) e rinominate l&#39;estensione da .jar a .zip.

1. Decomprimete il file copiato. Ne risulteranno molte sottocartelle e file.

1. All’interno dei file o delle cartelle decompressi, aprite o leggete il seguente file contenuto utilizzando un editor di testo: *org/apache/catalina/util/ServerInfo.properties*. Potrebbe essere necessario aggiungere un&#39;estensione .txt per facilitare l&#39;apertura con un editor di testo.

1. Al termine, se si trova su un computer server, eliminare i file temporanei creati.

Ad esempio, il file *ServerInfo.properties* per  Adobe Campaign conterrà le seguenti informazioni, indicando Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM GG AAAA HH:MM:SS*

Una volta che si è in grado di stabilire la versione esatta di Tomcat utilizzato in un particolare esempio, può essere di aiuto nella risoluzione dei problemi relativi a Tomcat.

>[!NOTE]
>
>La versione principale di Tomcat incorporato viene aggiornata solo quando la versione principale di  Adobe Campaign cambia (anche se le versioni precedenti potrebbero non essere più supportate ufficialmente, le informazioni potrebbero essere utili in quanto alcuni clienti potrebbero ancora eseguire queste versioni).
>
>Ad esempio,  Adobe Campaign v6.02 utilizzerà sempre Tomcat v6.x.