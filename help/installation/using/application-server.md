---
product: campaign
title: Server dell’applicazione
description: Server dell’applicazione
feature: Installation
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 1%

---

# Server dell’applicazione{#application-server}



I livelli di accesso al database richiesti devono essere installati sul server e accessibili dall’account Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

Il generatore di pagine web dinamiche utilizza la tecnologia JSP 1.2. Per questo, nell’applicazione è incluso un motore Tomcat (di Apache). Richiede un Java Development Kit (JDK), installato su tutti i server in cui è installata l’applicazione Adobe Campaign.

È innanzitutto necessario installare un JDK nei computer in cui si desidera eseguire il server applicazioni Adobe Campaign (**nlserver web** processo ) perché incorpora un contenitore servlet, Apache Tomcat, utilizzato per generare pagine web dinamiche (rapporti, moduli web, ecc.).

L’applicazione è stata approvata per Java Development Kit (JDK) sviluppato da Oracle e per **OpenJDK**.

Le versioni supportate sono dettagliate in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Può essere installata utilizzando la versione JDK appropriata già utilizzata da altre applicazioni sul computer.
>  
>Durante l’installazione, non è necessario eseguire l’integrazione con i browser web.
>
>In un computer che esegue solo agenti di consegna (**mta nlserver** processo) o il server del flusso di lavoro (**nlserver wfserver** processo), l&#39;installazione di un JDK non è necessaria.

Per scaricare Java JDK, connettiti a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Avviso: è necessario scaricare un JDK, non un JRE.**

>[!CAUTION]
>
>Per mantenere le prestazioni operative della piattaforma e garantire la compatibilità con la versione installata, è necessario disabilitare le funzioni di aggiornamento automatico JDK in Windows e Linux.

Per installare JDSL in un ambiente Linux, è preferibile utilizzare un gestore di pacchetti.

In Debian 8 e 9, usa il seguente comando:

```
aptitude install openjdk-8-jdk
```

Per RHEL 7, utilizzare il comando seguente:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

In Linux, OpenSSL deve essere installato. Adobe Campaign supporta OpenSSL versione 1.0.2 o successiva.

## Esportazione di report {#exporting-reports}

Adobe Campaign consente di esportare i rapporti della piattaforma in formato Microsoft Excel e Adobe PDF. Per il formato Microsoft Excel, Adobe Campaign utilizza **LibreOffice**. Per il formato Adobe PDF, Adobe Campaign utilizza **PhantomJS** convertitore. PhantomJs è incluso nel pacchetto di fabbrica e LibreOffice deve essere installato sui computer su cui viene eseguito il server applicazioni Adobe Campaign (**nlserver web** processo).

>[!NOTE]
>
>Per Linux, è necessario aggiungere font. Per ulteriori informazioni, consulta [Font per le statistiche MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin ti consente di assegnare un punteggio alle e-mail per determinare se un messaggio rischia di essere considerato indesiderato dagli strumenti anti-spam utilizzati alla ricezione. L&#39;installazione è facoltativa.

La qualifica delle e-mail come indesiderate da SpamAssassin si basa interamente sulle regole di filtro e di punteggio. Queste regole devono quindi essere aggiornate almeno una volta al giorno affinché l’installazione di SpamAssassin e la sua integrazione in Adobe Campaign siano completamente funzionali e per garantire la pertinenza dei punteggi assegnati alle consegne prima dell’invio. Questo aggiornamento è responsabilità dell&#39;amministratore del server che ospita SpamAssassin.

La versione minima supportata è: **3,4**

SpamAssassin richiede un accesso a Internet HTTP (tcp/80).

Le fasi di installazione e configurazione di SpamAssassin sono presentate in [Configurazione di SpamAssassin](../../installation/using/configuring-spamassassin.md).
