---
product: campaign
title: Individua la versione Tomcat in Adobe Campaign
description: Scopri come scoprire la versione corrente del servlet web Tomcat incorporato utilizzato in un’istanza di Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Individua versione Tomcat{#locate-tomcat-version}



Adobe Campaign utilizza un **servlet web incorporato chiamato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l’applicazione e qualsiasi interfaccia esterna (compresa la console client, i collegamenti URL tracciati, le chiamate SOAP e altri). Spesso è presente davanti a questo un server web esterno (in genere IIS o Apache) per qualsiasi istanza Adobe Campaign rivolta all’esterno.

Segui la procedura seguente per scoprire la versione esatta di Tomcat utilizzata in un **istanza on-premise di Campaign Classic** per facilitare la risoluzione dei problemi.

## Tomcat utilizzato in Adobe Campaign

Tomcat funziona su Java e richiede l&#39;installazione di JDK. Per ulteriori informazioni, consulta Java Development Kit (JDK) nella sezione [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md) sezione .

Il Tomcat utilizzato in Adobe Campaign è una versione incorporata personalizzata che non utilizza tutte le caratteristiche del rilascio completo disponibile di Tomcat, e potrebbe non subire tutte le vulnerabilità della versione completa. Anche Tomcat non dovrebbe essere esposto all&#39;Internet esterno e tutte le istanze Adobe Campaign esposte dovrebbero disporre di un server web esterno (IIS, Apache, ecc.). davanti al Tomcat per proteggerlo.

Le versioni nuove o aggiornate delle versioni incorporate di Tomcat vengono rilasciate solo con nuove build di Adobe Campaign e non come patch separate al di fuori delle build di Adobe Campaign.

## Come individuare la versione di Tomcat incorporata

Per individuare la versione di Tomcat incorporata in un’istanza di Adobe Campaign, segui i passaggi riportati di seguito.

>[!NOTE]
>
>Devi avere accesso ai file sul server Adobe Campaign che devi controllare. La procedura descritta di seguito si applica solo a **modelli di hosting on-premise**.

1. Passa a *\tomcat-7\lib* sottocartella all’interno della cartella di installazione di Adobe Campaign (ad esempio, *C:\Program Files\ [Cartella_Installazione]* in Windows, oppure */usr/local/neolane/nl6* in Linux).

   Se utilizzi una versione precedente di Adobe Campaign con Tomcat v6, utilizza *\tomcat-6\lib*.

1. Copia il file *catalina.jar* in una cartella temporanea esterna (ad esempio, il desktop) e rinomina l’estensione da .jar a .zip.

1. Decomprimi il file copiato. Ne risulteranno molte sottocartelle e file.

1. All&#39;interno dei file/cartelle decompressi, aprire o leggere il seguente file contenuto utilizzando un editor di testo: *org/apache/catalina/util/ServerInfo.properties*. Potrebbe essere necessario aggiungere un&#39;estensione .txt per facilitare l&#39;apertura con un editor di testo.

1. Al termine, se si trova su un computer server, eliminare i file temporanei creati.

Ad esempio, il *ServerInfo.properties* il file per Adobe Campaign conterrà le seguenti informazioni, indicando Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM GG AAAA HH:MM:SS*

Una volta che si è in grado di stabilire la versione esatta di Tomcat utilizzato in un particolare caso, può aiutarti a risolvere i problemi relativi a Tomcat.

>[!NOTE]
>
>La versione principale del Tomcat incorporato viene aggiornata solo quando cambia la versione principale di Adobe Campaign (anche se le versioni precedenti potrebbero non essere più supportate ufficialmente, le informazioni potrebbero essere utili in quanto alcuni clienti potrebbero ancora eseguire queste versioni).
>
>Ad esempio, Adobe Campaign v6.02 utilizzerà sempre Tomcat v6.x.
