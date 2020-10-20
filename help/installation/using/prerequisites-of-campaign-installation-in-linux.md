---
title: Prerequisiti per l’installazione di Campaign in Linux
description: Prerequisiti per l’installazione di Campaign in Linux
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
translation-type: tm+mt
source-git-commit: f8539433274e531e34b7512ce1b6385d67e8e332
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 3%

---


# Prerequisiti per l’installazione di Campaign in Linux{#prerequisites-of-campaign-installation-in-linux}

## Prerequisiti software {#software-prerequisites}

Questa sezione descrive i passaggi preliminari per le configurazioni necessari prima di installare  Adobe Campaign.

La configurazione tecnica e software necessaria per l&#39;installazione  Adobe Campaign è dettagliata nella matrice [di](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)compatibilità.

Come promemoria, è necessario installare e configurare correttamente i seguenti componenti:

* Apache, fare riferimento a [Matrice](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)di compatibilità,
* Java JDK e OpenJDK, fare riferimento a [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Librerie, fare riferimento a [Librerie](#libraries),
* livelli di accesso al database, fare riferimento ai livelli [di accesso al](#database-access-layers)database,
* LibreOffice, fare riferimento a [Installazione di LibreOffice per Debian](#installing-libreoffice-for-debian) e [Installazione di LibreOffice per CentOS](#installing-libreoffice-for-centos),
* Font, fare riferimento a [Font per statistiche](#fonts-for-mta-statistics) MTA e [Font per istanze](#fonts-for-japanese-instances)giapponesi.

>[!NOTE]
>
>Per installare una build inferiore o uguale a 8709 sulle piattaforme CentOS 7 e Debian 8, è necessario abilitare il modulo apache access_compat.

### Librerie {#libraries}

Per installare  Adobe Campaign in Linux, accertatevi di disporre delle librerie necessarie.

* La libreria C deve essere in grado di supportare la modalità TLS (Thread Local Storage). Questa modalità è attiva nella maggior parte dei casi, tranne per alcuni kernel per i quali il supporto Xen è stato disattivato.

   Per verificare questo, è possibile utilizzare il **nome uname -a | grep xen** , ad esempio.

   Se il comando non restituisce nulla (riga vuota), significa che la configurazione è corretta.

* È necessario disporre della **versione 0.9.8** o **1.0** di OpenSSL.

   Per le distribuzioni RHEL 7, è necessaria la versione 1.0 di OpenSSL.

* Per utilizzare  Adobe Campaign, è necessario che sia installata la libreria **libicu** .

   Sono supportate le seguenti versioni di **libicu** (32 bit o 64 bit):

   * RHEL 7, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

   Per utilizzare  Adobe Campaign, è necessario che sia installata la libreria libc-ares. In RHEL/CentOS, eseguite il comando seguente:

   ```
   yum install c-ares
   ```

   Su Debian:

   ```
   aptitude install libc-ares2
   ```

### SELLinux {#selinux}

Se utilizzato, il modulo SELLinux deve essere configurato correttamente.

A questo scopo, accedete come root e immettete il comando seguente:

```
echo 0 >/selinux/enforce
```

Inoltre, nel file **/etc/sysconfig/httpd** , è stata aggiunta la riga seguente per fare riferimento allo script di configurazione dell&#39;ambiente Adobe Campaign :

```
. ~neolane/nl6/env.sh
```

In RHEL e CentOS, problemi di compatibilità con i livelli client dei database sono stati rilevati quando SELLinux è abilitato. Per essere certi  Adobe Campaign è in grado di funzionare correttamente, si consiglia di disattivare SELLinux.

**Applicate il seguente processo:**

* Modificare il file **/etc/selLinux/config**

* Modificate la linea SELINUX nel modo seguente:

```
SELINUX=disabled
```

### Font per le statistiche MTA {#fonts-for-mta-statistics}

Per visualizzare correttamente i rapporti sulle statistiche MTA (nms/fra/jsp/stat.jsp), aggiungete i font.

In Debian, aggiungete il comando:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

In Redhat, utilizzare il comando seguente:

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Font per istanze giapponesi {#fonts-for-japanese-instances}

I font di caratteri specifici sono necessari per le istanze giapponesi per esportare i rapporti in formato PDF.

In Debian, aggiungete il comando:

```
aptitude install fonts-ipafont
```

In Red Hat, aggiungete il comando:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Installazione di LibreOffice per Debian {#installing-libreoffice-for-debian}

Per Debian sono necessarie le seguenti configurazioni:

1. Installate i seguenti pacchetti standard:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installate i seguenti font (facoltativi ma altamente consigliati per le istanze giapponesi):

   ```
   apt-get install fonts-ipafont
   ```

### Installazione di LibreOffice per CentOS {#installing-libreoffice-for-centos}

Con CentOS sono necessarie le seguenti configurazioni:

1. Installate i seguenti pacchetti standard:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Installate i seguenti font (facoltativi ma consigliati per le istanze giapponesi):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Livelli di accesso al database {#database-access-layers}

I livelli di accesso per il motore di database utilizzato devono essere installati sul server e accessibili tramite l&#39;account Adobe Campaign . Le versioni e le modalità di installazione possono variare a seconda del motore di database utilizzato.

La versione pilota supportata è dettagliata nella matrice [di](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)compatibilità.

Consultare anche la sezione [Database](../../installation/using/database.md) generale.

### PostgreSQL {#postgresql}

 Adobe Campaign supporta tutte le versioni delle librerie client PostgreSQL dalla versione 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** e **libpq.so.3.1**).

L&#39;utilizzo di PostgreSQL con  Adobe Campaign richiede anche l&#39;installazione delle librerie **pgcrypto** corrispondenti.

### Oracle {#oracle}

Recuperate la versione della libreria per Debian a 64 bit, ovvero: **libclntsh.so**, **libclntsh.so.11.1** e **libclntsh.so.10.1**.

È possibile ottenere un pacchetto Linux RPM da Oracle Technology Network.

>[!NOTE]
>
>Se il client Oracle è già installato ma l&#39;ambiente globale (ad esempio: /etc/profile) non è configurato correttamente. È possibile aggiungere informazioni mancanti allo script **nl6/customer.sh** . Per ulteriori informazioni, vedere le variabili [di](../../installation/using/installing-packages-with-linux.md#environment-variables)ambiente.

**Risoluzione dei problemi e procedure ottimali**

I problemi possono presentarsi dopo un aggiornamento di Oracle client o server, una modifica di versione o alla prima installazione dell&#39;istanza.

Se nella console client si nota che nei registri sono presenti ritardi di tempo imprevisti (una o più ore), l&#39;ultima elaborazione del flusso di lavoro, l&#39;elaborazione successiva e così via, potrebbe verificarsi un problema tra la libreria del client Oracle e Oracle Server. Per evitare tali problemi

1. Accertatevi di utilizzare il client **** completo.

   Sono stati individuati diversi problemi durante l&#39;utilizzo della versione di Oracle Instant Client. Inoltre, è impossibile modificare il file Timezone sul client istantaneo.

1. Verificate che la versione **** client e la versione **del server di** database siano **uguali**.

   È noto che il mixaggio delle versioni nonostante la matrice di compatibilità e la raccomandazione di Oracle per allineare le versioni client e server causa problemi.

   Controllare inoltre il valore ORACLE_HOME per essere certi che punti alla versione client prevista (nel caso in cui sul computer siano installate più versioni).

1. Accertatevi che il client e il server utilizzino lo stesso file **** timezone.

### DB2 {#db2}

La versione della libreria supportata è **libdb2.so**.

## Passaggi di implementazione {#implementation-steps}

 installazioni Adobe Campaign per Linux devono essere eseguite nella seguente sequenza: l&#39;installazione del server seguita dalla configurazione dell&#39;istanza.

Il processo di installazione è descritto in questo capitolo. Le fasi di installazione sono le seguenti:

* Passaggio 1: Installazione del server applicazione, vedere [Installazione di pacchetti con Linux](../../installation/using/installing-packages-with-linux.md).
* Passaggio 2: Integrazione con un server Web (facoltativo, a seconda dei componenti distribuiti).

Una volta completati i passaggi di installazione, è necessario configurare le istanze, il database e il server. Per ulteriori informazioni, consulta [Informazioni sulla configurazione](../../installation/using/about-initial-configuration.md)iniziale.
