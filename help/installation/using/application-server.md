---
title: Application Server
seo-title: Application Server
description: Application Server
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Application Server{#application-server}

I livelli di accesso al database richiesti devono essere installati sul server e accessibili dall&#39;account Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

Il generatore dinamico di pagine Web utilizza la tecnologia JSP 1.2. Per questo, un motore Tomcat (da Apache) è incluso nell&#39;applicazione. Richiede un Java Development Kit (JDK) installato su tutti i server in cui è installata l’applicazione Adobe Campaign.

È innanzitutto necessario installare un JDK sui computer in cui si desidera eseguire il server applicazione Adobe Campaign (processo Web **** nlserver), perché include un contenitore servlet, Apache Tomcat, utilizzato per generare pagine Web dinamiche (rapporti, moduli Web, ecc.).

L&#39;applicazione è stata approvata per Java Development Kit (JDK) sviluppato da Oracle e per **OpenJDK**.

Le versioni supportate sono dettagliate nella matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità.

>[!NOTE]
>
>Può essere installato utilizzando la versione JDK appropriata già utilizzata da altre applicazioni sul computer.
>  
>Durante l&#39;installazione, non è necessario eseguire l&#39;integrazione con i browser Web.
>
>In un computer che esegue solo gli agenti di consegna (processo **nlserver mta** ) o il server del flusso di lavoro (processo wfserver **** nlserver), l&#39;installazione di un JDK non è necessaria.

Per scaricare Java JDK, effettua la connessione a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Avviso: è necessario scaricare un JDK, non un JRE.**

>[!CAUTION]
>
>Per mantenere le prestazioni operative della piattaforma e garantire la compatibilità con la versione installata, è necessario disabilitare le funzioni di aggiornamento JDK automatico in Windows e Linux.

Per installare il JDSL in un ambiente Linux, è preferibile utilizzare un gestore pacchetti.

In Debian 7 e 8, utilizzate il seguente comando:

```
aptitude install openjdk-7-jdk
```

Per RHEL 6, utilizzare il comando seguente:

```
yum install java-1.8.0-openjdk
```

Per RHEL 7, utilizzare il comando seguente:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

In Linux, OpenSSL deve essere installato. Le versioni supportate da Adobe Campaign sono **OpenSSL 1.0.1** e **OpenSSL 0.9.8**. Sono accettate le versioni da 0.9.8g a 0.9.8o.

>[!NOTE]
>
>Per RHEL 6 e CentOS 6, è richiesto openSSL 1.0.

## Esportazione dei rapporti {#exporting-reports}

Adobe Campaign consente di esportare i rapporti sulle piattaforme in formato Microsoft Excel e Adobe PDF. Per il formato Microsoft Excel, Adobe Campaign utilizza **LibreOffice**. Per il formato Adobe PDF, Adobe Campaign utilizza il convertitore **PhantomJS** . PhantomJs è incluso nel pacchetto di fabbrica e LibreOffice deve essere installato sui computer in cui viene eseguito il server applicazione Adobe Campaign (processo Web **** nlserver).

>[!NOTE]
>
>Per Linux, dovrete aggiungere dei font. Per ulteriori informazioni, consultate [Font per statistiche](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)MTA.

## SpamAssassin {#spamassassin}

SpamAssassin consente di assegnare un punteggio alle e-mail per determinare se un messaggio rischi di essere considerato indesiderabile dagli strumenti anti-spam utilizzati alla ricezione. L&#39;installazione è facoltativa.

La qualifica delle e-mail come indesiderabili da SpamAssassin si basa interamente su regole di filtraggio e punteggio. Queste regole devono pertanto essere aggiornate almeno una volta al giorno affinché l&#39;installazione di SpamAssassin e la sua integrazione in Adobe Campaign siano completamente funzionanti e per garantire la pertinenza dei punteggi assegnati alle consegne prima dell&#39;invio. Questo aggiornamento è responsabilità dell&#39;amministratore del server che ospita SpamAssassin.

Le versioni supportate minime sono: **3.2.5** e **3.3.2**.

SpamAssassin richiede un accesso a Internet HTTP (tcp/80).

Le fasi di installazione e configurazione per SpamAssassin sono presentate in [Configuring SpamAssassin](../../installation/using/configuring-spamassassin.md).
