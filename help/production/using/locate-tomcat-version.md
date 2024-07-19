---
product: campaign
title: Individuare la versione Tomcat in Adobe Campaign
description: Scopri come individuare la versione corrente del servlet web Tomcat incorporato utilizzato in un’istanza di Adobe Campaign
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Individua versione Tomcat{#locate-tomcat-version}

Adobe Campaign utilizza un **servlet Web incorporato denominato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l&#39;applicazione e qualsiasi interfaccia esterna (inclusa la console client, i collegamenti URL tracciati, le chiamate SOAP e altri). Di fronte a questo server spesso è presente un server web esterno (in genere IIS o Apache) per tutte le istanze Adobe Campaign rivolte all’esterno.

Segui la procedura seguente per individuare la versione esatta di Tomcat utilizzata in un&#39;istanza on-premise **Campaign Classic** per facilitare la risoluzione dei problemi.

## Tomcat utilizzato in Adobe Campaign

Tomcat viene eseguito su Java e richiede l’installazione di JDK. Per ulteriori informazioni, consulta Java Development Kit (JDK) nella sezione [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md).

Il Tomcat utilizzato in Adobe Campaign è una versione incorporata personalizzata che non utilizza tutte le funzioni della versione completa generalmente disponibile di Tomcat e potrebbe non soffrire di tutte le vulnerabilità della versione completa. Inoltre, Tomcat non deve essere esposto a Internet esterno e tutte le istanze Adobe Campaign esposte devono avere un server web esterno (IIS, Apache, ecc.) di fronte al Tomcat per proteggerlo.

Le versioni nuove o aggiornate delle versioni incorporate di Tomcat vengono rilasciate solo con nuove build di Adobe Campaign e non come patch separate al di fuori delle build di Adobe Campaign.

>[!AVAILABILITY]
>
>
> A partire da Campaign v7.4.1, Tomcat 10.1 è la versione predefinita.
>

## Come individuare la versione di Tomcat incorporata

Per individuare la versione di Tomcat incorporata in un’istanza di Adobe Campaign, effettua le seguenti operazioni.

>[!NOTE]
>
>Devi avere accesso ai file sul server Adobe Campaign che devi controllare. La procedura descritta di seguito si applica solo a **modelli di hosting on-premise**.

1. Passa alla sottocartella *\tomcat-11\lib* all&#39;interno della cartella di installazione di Adobe Campaign (ad esempio, *C:\Program Files\ [Installation_folder]* in Windows o */usr/local/neolane/nl6* in Linux).

1. Copiare il file *catalina.jar* in una cartella temporanea esterna, ad esempio il desktop, e rinominare l&#39;estensione da .jar a .zip.

1. Decomprimi il file copiato. Ne risulteranno molte sottocartelle e file.

1. Nei file/cartelle decompressi, aprire o leggere il seguente file contenuto utilizzando un editor di testo: *org/apache/catalina/util/ServerInfo.properties*. Potrebbe essere necessario aggiungere un’estensione .txt per facilitare l’apertura con un editor di testo.

1. Al termine, se si trova su un server, eliminare i file temporanei creati.

Ad esempio, il file *ServerInfo.properties* per Adobe Campaign contiene le seguenti informazioni, che indicano Tomcat v11.X:

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Una volta che sei in grado di stabilire la versione esatta di Tomcat utilizzata in una particolare istanza, potrebbe aiutarti nella risoluzione dei problemi relativi a Tomcat.

>[!NOTE]
>
>La versione principale della Tomcat incorporata viene aggiornata solo quando cambia la versione principale di Adobe Campaign (anche se le versioni precedenti potrebbero non essere più ufficialmente supportate, le informazioni potrebbero essere utili in quanto alcuni clienti potrebbero ancora eseguire queste versioni).
>

