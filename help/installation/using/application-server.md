---
product: campaign
title: Server dell’applicazione
description: Server dell’applicazione
feature: Installation
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 387bcf39c13cc1f9544433b9441769f4b16b52ca
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 1%

---

# Server dell’applicazione{#application-server}

I livelli di accesso al database richiesti devono essere installati sul server e accessibili dall’account Adobe Campaign.

## Java Development Kit - JDK {#jdk}

Java Development Kit, o JDK, è un kit di sviluppo software. È il componente fondamentale che consente lo sviluppo di applicazioni Java e applet Java.

Il generatore di pagine web dinamiche utilizza la tecnologia JSP. Per questo, nell’applicazione è incluso un motore Tomcat (di Apache). Richiede un Java Development Kit (JDK), installato su tutti i server in cui è installata l’applicazione Adobe Campaign.

È innanzitutto necessario installare un JDK nei computer in cui si desidera eseguire il server applicazioni di Adobe Campaign (**nlserver web** process) perché include un contenitore servlet, Apache Tomcat, utilizzato per generare pagine Web dinamiche (report, moduli Web, ecc.).

L&#39;applicazione è stata approvata per Java Development Kit (JDK) sviluppato da Oracle e per **OpenJDK**.

Le versioni supportate sono descritte in dettaglio nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md) di Campaign.


>[!AVAILABILITY]
>
>* A partire dalla versione 7.4.1, Campaign richiede almeno **Java JDK 11**. Se il server Campaign è installato in un ambiente Windows, Java Runtime (JRE) non viene più rilevato automaticamente. La variabile di ambiente JRE_HOME deve essere impostata sulla cartella in cui Campaign può individuare il file `bin/server/jvm.dll`. Ad esempio, se JDK 11 è installato nella cartella `C:\Program Files\Java\jdk-11`, JRE_HOME deve essere `C:\Program Files\Java\jdk-11`.
>
>* A partire dalla versione v7.4.1, Tomcat 10.1 è la versione predefinita.
>

### Raccomandazioni

Durante l’installazione e l’aggiornamento di Java Development Kit, applica i seguenti consigli:

* Java Development Kit può essere installato utilizzando la versione JDK appropriata già utilizzata da altre applicazioni sul computer.

* Durante l’installazione di JDK, non è richiesta l’integrazione con i browser web.

* In un computer che esegue solo gli agenti di consegna (**nlserver mta** processo) o il server del flusso di lavoro (**nlserver wfserver** processo), l&#39;installazione di un JDK non è richiesta.

* Quando aggiorni la versione Java, devi prima disinstallare la versione precedente. Entrambe le versioni di Java installate nello stesso computer possono causare conflitti.

  In qualità di cliente on-premise, puoi verificare che la `LD_LIBRARY_PATH` [variabile di ambiente](installing-packages-with-linux.md#environment-variables) sia impostata sulla versione più recente (ad esempio. java11). Se è impostata su una versione precedente (ad es. Java8), quindi deve essere aggiornato. Per JDK 11, il percorso per individuare le librerie JDK è `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Passaggi per l’installazione

Java Development Kit è specifico per la piattaforma: sono necessari programmi di installazione separati per ciascun sistema operativo.

Per scaricare JDK, connettiti al [sito Web Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Assicurati di scaricare Java Development Kit (JDK) e non un ambiente Java Runtime (JRE).


Per installare JDSL in un ambiente Linux, Adobe consiglia di utilizzare un gestore di pacchetti.

Per Debian, usa il seguente comando:

```sql
apt install openjdk-11-jdk-headless
```

Per RHEL, utilizzare il comando seguente:

```sql
dnf install java-11-openjdk-headless
```



## Esportare rapporti {#exporting-reports}

Puoi utilizzare Adobe Campaign per esportare rapporti in Microsoft Excel e Adobe PDF.

* Per il formato Microsoft Excel, Adobe Campaign si basa su **LibreOffice**.

* Per il formato Adobe PDF, Adobe Campaign utilizza il convertitore **PhantomJS**. PhantomJs è incluso nel pacchetto di fabbrica e LibreOffice deve essere installato sui computer su cui viene eseguito il server applicazioni Adobe Campaign (**nlserver Web** processo).

>[!NOTE]
>
>Per Linux, è necessario aggiungere font. Per ulteriori informazioni, consulta [Caratteri per le statistiche MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin ti consente di assegnare un punteggio alle e-mail per determinare se un messaggio rischia di essere considerato indesiderato dagli strumenti anti-spam utilizzati alla ricezione. L&#39;installazione è facoltativa.

La qualifica delle e-mail come indesiderate da SpamAssassin si basa interamente sulle regole di filtro e di punteggio. Queste regole devono quindi essere aggiornate almeno una volta al giorno affinché l’installazione di SpamAssassin e la sua integrazione in Adobe Campaign siano completamente funzionali e per garantire la pertinenza dei punteggi assegnati alle consegne prima dell’invio. Questo aggiornamento è responsabilità dell&#39;amministratore del server che ospita SpamAssassin.

Versione minima supportata: **3.4**

SpamAssassin richiede un accesso a Internet HTTP (tcp/80).

Le fasi di installazione e configurazione per SpamAssassin sono presentate in [Configurazione di SpamAssassin](../../installation/using/configuring-spamassassin.md).
