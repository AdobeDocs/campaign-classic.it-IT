---
product: campaign
title: Individua la versione Tomcat in Adobe Campaign
description: Scopri come scoprire la versione corrente del servlet web Tomcat incorporato utilizzato in un’istanza di Adobe Campaign.
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Individua Tomcat versione{#locate-tomcat-version}

Adobe Campaign utilizza un **servlet web incorporato denominato Apache Tomcat** per elaborare le richieste HTTP/HTTPS tra l’applicazione e qualsiasi interfaccia esterna (inclusa la console client, i collegamenti URL tracciati, le chiamate SOAP e altri). Spesso è presente davanti a questo un server web esterno (in genere IIS o Apache) per qualsiasi istanza Adobe Campaign rivolta all’esterno.

Segui la procedura seguente per scoprire la versione esatta di Tomcat utilizzata in un **istanza on-premise di Campaign Classic** per aiutarti a risolvere i problemi.

## Tomcat utilizzato in Adobe Campaign

Tomcat funziona su Java e richiede l&#39;installazione di JDK. Per ulteriori informazioni, consulta Java Development Kit (JDK) nella sezione [Matrice di compatibilità della campagna](../../rn/using/compatibility-matrix.md) .

Il Tomcat utilizzato in Adobe Campaign è una versione incorporata personalizzata che non utilizza tutte le caratteristiche del rilascio completo disponibile di Tomcat, e potrebbe non subire tutte le vulnerabilità della versione completa. Anche Tomcat non dovrebbe essere esposto all&#39;Internet esterno e tutte le istanze Adobe Campaign esposte dovrebbero disporre di un server web esterno (IIS, Apache, ecc.). davanti al Tomcat per proteggerlo.

Le versioni nuove o aggiornate delle versioni incorporate di Tomcat vengono rilasciate solo con nuove build di Adobe Campaign e non come patch separate al di fuori delle build di Adobe Campaign.

## Come individuare la versione di Tomcat incorporata

Per individuare la versione di Tomcat incorporata in un’istanza di Adobe Campaign, segui i passaggi riportati di seguito.

>[!NOTE]
>
>Devi avere accesso ai file sul server Adobe Campaign che devi controllare. La procedura descritta di seguito si applica solo ai **modelli di hosting on-premise**.

1. Passa alla sottocartella *\tomcat-7\lib* all&#39;interno della cartella di installazione di Adobe Campaign (ad esempio, *C:\Program Files\ [Installation_folder]* in Windows o */usr/local/neolane/nl6* in Linux).

   Se utilizzi una versione precedente di Adobe Campaign con Tomcat v6, utilizza *\tomcat-6\lib*.

1. Copia il file *catalina.jar* in una cartella temporanea esterna (ad esempio, il desktop) e rinomina l&#39;estensione da .jar a .zip.

1. Decomprimi il file copiato. Ne risulteranno molte sottocartelle e file.

1. All&#39;interno dei file/cartelle decompressi, aprire o leggere il seguente file contenuto utilizzando un editor di testo: *org/apache/catalina/util/ServerInfo.properties*. Potrebbe essere necessario aggiungere un&#39;estensione .txt per facilitare l&#39;apertura con un editor di testo.

1. Al termine, se si trova su un computer server, eliminare i file temporanei creati.

Ad esempio, il file *ServerInfo.properties* per Adobe Campaign conterrà le seguenti informazioni, indicando Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM GG AAAA HH:MM:SS*

Una volta che si è in grado di stabilire la versione esatta di Tomcat utilizzato in un particolare caso, può aiutarti a risolvere i problemi relativi a Tomcat.

>[!NOTE]
>
>La versione principale del Tomcat incorporato viene aggiornata solo quando cambia la versione principale di Adobe Campaign (anche se le versioni precedenti potrebbero non essere più supportate ufficialmente, le informazioni potrebbero essere utili in quanto alcuni clienti potrebbero ancora eseguire queste versioni).
>
>Ad esempio, Adobe Campaign v6.02 utilizzerà sempre Tomcat v6.x.
