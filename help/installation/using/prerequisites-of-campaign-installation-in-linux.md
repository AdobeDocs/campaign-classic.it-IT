---
product: campaign
title: Prerequisiti per l’installazione di Campaign in Linux
description: Prerequisiti per l’installazione di Campaign in Linux
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 0%

---

# Prerequisiti per installare Campaign su Linux{#prerequisites-of-campaign-installation-in-linux}



## Prerequisiti software {#software-prerequisites}

Questa sezione descrive i passaggi di configurazione preliminari necessari prima di installare Adobe Campaign.

La configurazione tecnica e software necessaria per l’installazione di Adobe Campaign è descritta nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Come promemoria, è necessario installare e configurare correttamente i seguenti componenti:

* Apache, fare riferimento a [Compatibilità matrice](../../rn/using/compatibility-matrix.md),
* Java JDK e OpenJDK, fare riferimento a [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Librerie, fare riferimento a [Librerie](#libraries),
* Livelli di accesso al database, fare riferimento a [Livelli di accesso al database](#database-access-layers),
* LibreOffice, fare riferimento a [Installazione di LibreOffice per Debian](#installing-libreoffice-for-debian) e [Installazione di LibreOffice per CentOS](#installing-libreoffice-for-centos),
* Font, fare riferimento a [Font per le statistiche MTA](#fonts-for-mta-statistics) e [Font per istanze giapponesi](#fonts-for-japanese-instances).

>[!NOTE]
>
>Per installare una build inferiore o uguale a 8709 sulle piattaforme CentOS 7 e Debian 8, è necessario abilitare il modulo apache access_compat.

### Librerie {#libraries}

Per installare Adobe Campaign in Linux, assicurati di avere il librerie richiesto.

* La libreria C deve essere in grado di supportare la modalità TLS (Thread Local Storage). Questa modalità è attiva nella maggior parte dei casi tranne che con alcuni kernel per i quali il supporto Xen è stato disabilitato.

  Per verificarlo, puoi usare il **comando uname -a | grep xen** per esempio.

  Se il comando non restituisce alcun elemento (riga vuota), significa che la configurazione è corretta.

* È necessaria la versione OpenSSL **1.0.2.** o superiore.

  Per le distribuzioni RHEL 7/8, è richiesta la versione 1.0 di OpenSSL.

* Per utilizzare Adobe Campaign, è necessario disporre del **libicu** libreria installata.

  Le seguenti versioni di **libicu** sono supportati (32 bit o 64 bit):

   * 7/8, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

  Per utilizzare Adobe Campaign, è necessario che sia installata la libreria libc-ares. In RHEL/CentOS, esegui il seguente comando:

  ```
  yum install c-ares
  ```

  Su Debian:

  ```
  aptitude install libc-ares2
  ```

### Selinux {#selinux}

Quando viene utilizzato, il modulo SELinux deve essere configurato correttamente.

Per eseguire questa operazione, accedere come radice e immettere il comando seguente:

```
echo 0 >/selinux/enforce
```

Inoltre, nella sezione **/etc/sysconfig/httpd** file, è stata aggiunta la seguente riga per fare riferimento allo script di configurazione dell’ambiente Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

In RHEL e CentOS, quando SELinux è abilitato sono stati notati problemi di compatibilità con i livelli client dei database. Per garantire il corretto funzionamento di Adobe Campaign, si consiglia di disabilitare SELinux.

**Applica il seguente processo:**

* Modifica il file **/etc/selinux/config**

* Modificare la linea SELINUX come segue:

```
SELINUX=disabled
```

### Font per le statistiche MTA {#fonts-for-mta-statistics}

Affinché i rapporti sulle statistiche MTA (nms/fra/jsp/stat.jsp) vengano visualizzati correttamente, aggiungere i caratteri.

In Debian, aggiungere il comando:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

In Redhat, utilizzate il seguente comando:

* Per CentOS/RHEL 7:

  ```
  yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
  ```

* per RHEL 8:

  ```
  dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
  ```

### Font per istanze giapponesi {#fonts-for-japanese-instances}

I font con caratteri specifici sono necessari per le istanze giapponesi al fine di esportare i rapporti in formato PDF.

In Debian, aggiungi il comando:

```
aptitude install fonts-ipafont
```

In Red Hat, aggiungi il comando:

* Per RHEL 7:

  ```
  yum install ipa-gothic-fonts ipa-mincho-fonts
  ```

* per RHEL 8:

  ```
  dnf install vlgothic-fonts
  ```

### Installazione di LibreOffice per Debian {#installing-libreoffice-for-debian}

Per Debian, sono necessarie le seguenti configurazioni:

1. Installa i seguenti pacchetti standard:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installa i seguenti font (facoltativo ma consigliato per le istanze giapponesi):

   ```
   apt-get install fonts-ipafont
   ```

### Installazione di LibreOffice per CentOS {#installing-libreoffice-for-centos}

Le seguenti configurazioni sono necessarie con CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Livelli di accesso del database {#database-access-layers}

I livelli di accesso per il motore di database in uso devono essere installati nel server ed essere accessibili tramite l&#39;account Adobe Campaign. Le versioni e le modalità di installazione possono variare a seconda del motore di database utilizzato.

La versione pilota supportata è descritta nel [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Controlla anche il [Database](../../installation/using/database.md) sezione.

### PostgreSQL {#postgresql}

Adobe Campaign supporta tutte le versioni delle librerie client PostgreSQL dalla versione 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** e **libpq.so.3.1**).

L’utilizzo di PostgreSQL con Adobe Campaign richiede anche l’installazione della **pgcrypto** librerie.

###  Oracle {#oracle}

Recupera la versione della libreria per Debian a 64 bit, ovvero: **libclntsh.so**, **libclntsh.so.11.1** e **libclntsh.so.10.1**.

È possibile ottenere un pacchetto Linux RPM da Oracle Technology Network.

>[!NOTE]
>
>Se il client Oracle è già stato installato ma l’ambiente globale (ad esempio: /etc/profile) non è configurato correttamente, puoi aggiungere le informazioni mancanti al **nl6/customer.sh** script Per ulteriori informazioni, consulta [Variabili di ambiente](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Risoluzione dei problemi e best practice**

I problemi possono comparire dopo un aggiornamento del client Oracle o di un server, un cambio di versione o alla prima installazione del istanza.

Se si nota sulla console client che sono presenti ritardi imprevisti (una o più ore) nei log, workflow ultima elaborazione, elaborazione successiva e così via, potrebbe esserci un problema tra il libreria del client Oracle e Oracle Server. Per evitare tali problemi

1. Assicurati di utilizzare il **client completo**.

   Sono stati identificati diversi problemi durante l’utilizzo della versione Oracle Instant Client. Inoltre, è impossibile modificare il file del fuso orario sul client istantaneo.

1. Assicurati che il **versione client** e **versione del server di database** sono **uguale**.

   È noto che la combinazione di versioni nonostante la matrice di compatibilità di Oracle e la consiglio per allineare le versioni client e server causa problemi.

   Controllare inoltre ORACLE_HOME valore per assicurarsi che punti alla versione client prevista (nel caso in cui nel computer siano installate più versioni).

1. Assicurarsi che il client e il server utilizzino lo stesso **file** di fuso orario.

### DB2 {#db2}

La versione libreria supportata è **libdb2.so**.

## Passaggi di implementazione {#implementation-steps}

Le installazioni di Adobe Campaign per Linux devono essere eseguite nella seguente sequenza: installazione del server seguita dalla configurazione dell’istanza.

Il processo di installazione è descritto in questo capitolo. I passaggi di installazione sono i seguenti:

* Passaggio 1: installazione del server applicazioni, fare riferimento a [Installazione di pacchetti con Linux](../../installation/using/installing-packages-with-linux.md).
* Passaggio 2: integrazione con un server web (facoltativo, a seconda dei componenti distribuiti).

Una volta completati i passaggi di installazione, è necessario configurare le istanze, il database e il server. Per ulteriori informazioni, consulta [Informazioni sulla configurazione iniziale](../../installation/using/about-initial-configuration.md).
