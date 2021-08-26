---
product: campaign
title: Server dell’applicazione
description: Server dell’applicazione
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---

# Server dell’applicazione{#application-server}

![](../../assets/v7-only.svg)

I livelli di accesso al database richiesti devono essere installati sul server e accessibili dall’account Adobe Campaign.

## Kit di sviluppo Java - JDK {#java-development-kit---jdk}

Il generatore dinamico di pagine web utilizza la tecnologia JSP 1.2. Per questo, un motore Tomcat (da Apache) è incluso nell&#39;applicazione. Richiede un Java Development Kit (JDK), installato su tutti i server in cui è installata l&#39;applicazione Adobe Campaign.

È innanzitutto necessario installare un JDK nei computer in cui si desidera eseguire il server dell&#39;applicazione Adobe Campaign (**nlserver web** processo) perché incorpora un contenitore servlet, Apache Tomcat, utilizzato per generare pagine Web dinamiche (report, moduli web, ecc.).

L&#39;applicazione è stata approvata per Java Development Kit (JDK) sviluppato da Oracle e per **OpenJDK**.

Le versioni supportate sono descritte in dettaglio in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Può essere installato utilizzando la versione JDK appropriata già utilizzata da altre applicazioni sul computer.
>  
>Durante l&#39;installazione, non è necessario eseguire l&#39;integrazione con i browser Web.
>
>Su un computer che esegue solo agenti di consegna (**nlserver mta** processo) o sul server del flusso di lavoro (**nlserver wfserver** processo), l&#39;installazione di un JDK non è necessaria.

Per scaricare Java JDK, connettiti a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Avviso: devi scaricare un JDK, non un JRE.**

>[!CAUTION]
>
>Per mantenere le prestazioni del funzionamento della piattaforma e garantire la compatibilità con la versione installata, è necessario disabilitare le funzioni di aggiornamento automatico JDK in Windows e Linux.

Per installare JDSL in un ambiente Linux, è preferibile utilizzare un gestore di pacchetti.

In Debian 8 e 9, utilizza il seguente comando:

```
aptitude install openjdk-8-jdk
```

Per RHEL 7, utilizzare il seguente comando:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

In Linux, OpenSSL deve essere installato. Le versioni supportate da Adobe Campaign sono **OpenSSL 1.0.1** e **OpenSSL 0.9.8**. Sono accettate le sottoversioni da 0.9.8g a 0.9.8o.

## Esportazione dei rapporti {#exporting-reports}

Adobe Campaign consente di esportare i rapporti delle piattaforme in formato Microsoft Excel e Adobe PDF. Per il formato Microsoft Excel, Adobe Campaign utilizza **LibreOffice**. Per il formato Adobe PDF, Adobe Campaign utilizza il convertitore **PhantomJS**. PhantomJs è incluso nel pacchetto di fabbrica e LibreOffice deve essere installato sui computer sui quali viene eseguito il server applicazioni Adobe Campaign (**nlserver web** processo).

>[!NOTE]
>
>Per Linux, sarà necessario aggiungere font. Per ulteriori informazioni, consulta [Font per statistiche MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin consente di assegnare un punteggio alle e-mail per determinare se un messaggio rischia di essere considerato indesiderabile dagli strumenti anti-spam utilizzati alla ricezione. L&#39;installazione è facoltativa.

La qualifica delle e-mail come indesiderabile da SpamAssassin si basa interamente su regole di filtraggio e punteggio. Queste regole devono quindi essere aggiornate almeno una volta al giorno affinché l’installazione di SpamAssassin e la sua integrazione in Adobe Campaign siano pienamente funzionanti e garantiscano la pertinenza dei punteggi assegnati alle consegne prima dell’invio. Questo aggiornamento è responsabilità dell&#39;amministratore del server che ospita SpamAssassin.

La versione minima supportata è: **3.4**

SpamAssassin richiede un accesso a Internet HTTP (tcp/80).

Le fasi di installazione e configurazione per SpamAssassin sono presentate in [Configurazione di SpamAssassin](../../installation/using/configuring-spamassassin.md).
