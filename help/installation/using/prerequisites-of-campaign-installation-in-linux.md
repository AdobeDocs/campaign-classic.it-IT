---
product: campaign
title: Prerequisiti per l’installazione di Campaign in Linux
description: Prerequisiti per l’installazione di Campaign in Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 1%

---

# Prerequisiti per installare Campaign su Linux{#prerequisites-of-campaign-installation-in-linux}

## Prerequisiti software {#software-prerequisites}

Questa sezione descrive i passaggi preliminari delle configurazioni necessari prima di installare Adobe Campaign.

La configurazione tecnica e software necessaria per l&#39;installazione di Adobe Campaign è descritta nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Come promemoria, è necessario installare e configurare correttamente i seguenti componenti:

* Apache, fare riferimento a [Matrice di compatibilità](../../rn/using/compatibility-matrix.md),
* Java JDK e OpenJDK, fai riferimento a [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Librerie, fare riferimento a [Librerie](#libraries),
* Livelli di accesso al database, fare riferimento a [Livelli di accesso al database](#database-access-layers),
* LibreOffice, fare riferimento a [Installazione di LibreOffice per Debian](#installing-libreoffice-for-debian) e [Installazione di LibreOffice per CentOS](#installing-libreoffice-for-centos),
* Font, fai riferimento a [Font per statistiche MTA](#fonts-for-mta-statistics) e [Font per istanze giapponesi](#fonts-for-japanese-instances).

>[!NOTE]
>
>Per installare una build inferiore o uguale a 8709 sulle piattaforme CentOS 7 e Debian 8, il modulo apache access_compat deve essere abilitato.

### Librerie {#libraries}

Per installare Adobe Campaign in Linux, assicurati di disporre delle librerie richieste.

* La libreria C deve essere in grado di supportare la modalità TLS (Thread Local Storage). Questa modalità è attiva nella maggior parte dei casi, tranne per alcuni kernel per i quali il supporto Xen è stato disabilitato.

   Per verificare questo, puoi utilizzare il **nome di annullamento -a | grep xen**, ad esempio.

   Se il comando non restituisce alcun elemento (riga vuota), significa che la configurazione è corretta.

* OpenSSL deve contenere la versione 0.9.8 **o** 1.0 **di OpenSSL.**

   Per le distribuzioni RHEL 7, è richiesta la versione 1.0 di OpenSSL.

* Per utilizzare Adobe Campaign, è necessario che sia installata la libreria **libicu** .

   Sono supportate le seguenti versioni di **libicu** (32 bit o 64 bit):

   * RHEL 7, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

   Per utilizzare Adobe Campaign, è necessario che la libreria libc-ares sia installata. Su RHEL/CentOS, esegui il seguente comando:

   ```
   yum install c-ares
   ```

   Su Debian:

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

Se utilizzato, il modulo SELinux deve essere configurato correttamente.

A questo scopo, accedi come root e immetti il seguente comando:

```
echo 0 >/selinux/enforce
```

Inoltre, nel file **/etc/sysconfig/httpd**, è stata aggiunta la seguente riga per fare riferimento allo script di configurazione dell&#39;ambiente Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

In RHEL e CentOS, quando SELinux è abilitato, sono stati rilevati problemi di compatibilità con i livelli client dei database. Per essere certi che Adobe Campaign sia in grado di funzionare correttamente, si consiglia di disabilitare SELinux.

**Applica il seguente processo:**

* Modifica il file **/etc/selinux/config**

* Modificare la linea SELINUX come segue:

```
SELINUX=disabled
```

### Font per le statistiche MTA {#fonts-for-mta-statistics}

Per visualizzare correttamente i rapporti sulle statistiche MTA (nms/fra/jsp/stat.jsp), aggiungi i font.

In Debian, aggiungi il comando:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

In Redhat, utilizzare il comando seguente:

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Font per istanze giapponesi {#fonts-for-japanese-instances}

I font di caratteri specifici sono necessari per le istanze giapponesi per esportare i rapporti in formato PDF.

In Debian, aggiungi il comando:

```
aptitude install fonts-ipafont
```

In Red Hat, aggiungi il comando:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Installazione di LibreOffice per Debian {#installing-libreoffice-for-debian}

Per Debian sono necessarie le seguenti configurazioni:

1. Installa i seguenti pacchetti standard:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installa i seguenti font (facoltativi ma altamente raccomandati per le istanze giapponesi):

   ```
   apt-get install fonts-ipafont
   ```

### Installazione di LibreOffice per CentOS {#installing-libreoffice-for-centos}

Con CentOS sono necessarie le seguenti configurazioni:

1. Installa i seguenti pacchetti standard:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Installa i seguenti font (facoltativi ma altamente consigliati per le istanze giapponesi):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Livelli di accesso al database {#database-access-layers}

I livelli di accesso per il motore di database utilizzato devono essere installati sul server ed essere accessibili tramite l’account Adobe Campaign. Le versioni e le modalità di installazione possono variare a seconda del motore di database utilizzato.

La versione pilota supportata è descritta in [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Controlla anche la sezione generale [Database](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign supporta tutte le versioni delle librerie client PostgreSQL dalla versione 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** e **libpq.so.3.1**).

L&#39;utilizzo di PostgreSQL con Adobe Campaign richiede anche l&#39;installazione delle librerie **pgcrypto** corrispondenti.

###  Oracle {#oracle}

Recupera la versione della libreria per Debian a 64 bit, ovvero: **libclntsh.so**, **libclntsh.so.11.1** e **libclntsh.so.10.1**.

È possibile ottenere un pacchetto Linux RPM dalla rete di tecnologia Oracle.

>[!NOTE]
>
>Se hai già installato il client Oracle ma l’ambiente globale (ad esempio: /etc/profile) non è configurato correttamente, è possibile aggiungere informazioni mancanti allo script **nl6/customer.sh** Per ulteriori informazioni, consulta [Variabili di ambiente](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Risoluzione dei problemi e best practice**

I problemi possono comparire dopo un client di Oracle o un aggiornamento del server, la modifica della versione o alla prima installazione dell&#39;istanza.

Se nella console client si notano ritardi imprevisti (una o più ore) nei registri, nell’ultima elaborazione del flusso di lavoro, nell’elaborazione successiva e così via, potrebbe esserci un problema tra la libreria del client Oracle e il server Oracle. Per evitare tali problemi

1. Assicurati di utilizzare il **client completo**.

   Sono stati identificati vari problemi durante l’utilizzo della versione Oracle Instant Client . Inoltre, è impossibile modificare il file Timezone sul client istantaneo.

1. Assicurati che le **versioni client** e la **versione del server di database** siano le **stesse**.

   È noto che la combinazione di versioni nonostante la matrice di compatibilità di Oracle e la raccomandazione per l’allineamento delle versioni client e server causa problemi.

   Controlla anche il valore ORACLE_HOME per assicurarti che punti alla versione client prevista (nel caso in cui sul computer siano installate diverse versioni).

1. Assicurati che il client e il server utilizzino lo stesso file **timezone**.

### DB2 {#db2}

La versione della libreria supportata è **libdb2.so**.

## Passaggi di implementazione {#implementation-steps}

Le installazioni Adobe Campaign per Linux devono essere eseguite nella seguente sequenza: installazione del server seguita dalla configurazione dell&#39;istanza.

Il processo di installazione è descritto in questo capitolo. Le fasi di installazione sono le seguenti:

* Passaggio 1: Installazione dell&#39;application server, fare riferimento a [Installazione di pacchetti con Linux](../../installation/using/installing-packages-with-linux.md).
* Passaggio 2: Integrazione con un server web (facoltativo, a seconda dei componenti distribuiti).

Una volta completati i passaggi di installazione, devi configurare le istanze, il database e il server. Per ulteriori informazioni, consulta [Informazioni sulla configurazione iniziale](../../installation/using/about-initial-configuration.md).
