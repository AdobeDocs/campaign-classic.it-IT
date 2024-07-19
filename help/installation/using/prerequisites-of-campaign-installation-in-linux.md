---
product: campaign
title: Prerequisiti per l’installazione di Campaign in Linux
description: Prerequisiti per l'installazione di Campaign in Linux
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo a distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Prerequisiti per installare Campaign su Linux{#prerequisites-of-campaign-installation-in-linux}

## Prerequisiti software {#software-prerequisites}

Questa sezione descrive i passaggi di configurazione preliminari necessari prima di installare Adobe Campaign.

La configurazione tecnica e software necessaria per l&#39;installazione di Adobe Campaign è descritta nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Come promemoria, è necessario installare e configurare correttamente i seguenti componenti:

* Apache, fare riferimento a [Matrice di compatibilità](../../rn/using/compatibility-matrix.md),
* Java JDK e OpenJDK, fare riferimento a [Java Development Kit - JDK](../../installation/using/application-server.md#jdk),
* Librerie, fai riferimento a [Librerie](#libraries),
* Livelli di accesso al database, fare riferimento a [Livelli di accesso al database](#database-access-layers),
* LibreOffice, fare riferimento a [Installazione di LibreOffice per Debian](#installing-libreoffice-for-debian) e [Installazione di LibreOffice per CentOS](#installing-libreoffice-for-centos),
* Font, fai riferimento a [Font per statistiche MTA](#fonts-for-mta-statistics) e [Font per istanze giapponesi](#fonts-for-japanese-instances).


### Biblioteche {#libraries}

Per installare Adobe Campaign in Linux, assicurati di avere il librerie richiesto.

* La libreria C deve essere in grado di supportare la modalità TLS (Thread Local Storage). Questa modalità è attiva nella maggior parte dei casi tranne che con alcuni kernel per i quali il supporto Xen è stato disabilitato.

  Per verificarlo, puoi usare il **comando uname -a | grep xen** per esempio.

  Se il comando non restituisce una riga vuota, significa che la configurazione è corretta.

* È necessario disporre della versione **1.0.2** di OpenSSL o successiva.

  Per le distribuzioni RHEL, è richiesta la versione 1.0 di OpenSSL.

* Per utilizzare Adobe Campaign, è necessario che sia installata la libreria **libicu**.

### SELinux {#selinux}

Quando viene utilizzato, il modulo SELinux deve essere configurato correttamente.

Per eseguire questa operazione, accedere come radice e immettere il comando seguente:

```
echo 0 >/selinux/enforce
```

Inoltre, nel file **/etc/sysconfig/httpd** è stata aggiunta la seguente riga per fare riferimento allo script di configurazione dell&#39;ambiente Adobe Campaign:

```
. ~neolane/nl6/env.sh
```

In RHEL e CentOS, quando SELinux è abilitato sono stati notati problemi di compatibilità con i livelli client dei database. Per garantire il corretto funzionamento di Adobe Campaign, si consiglia di disabilitare SELinux.

**Applica il seguente processo:**

* Modifica il file **/etc/selinux/config**

* Modificare la riga SELINUX come segue:

```
SELINUX=disabled
```

### Font per le statistiche MTA {#fonts-for-mta-statistics}

Per visualizzare correttamente i rapporti sulle statistiche MTA (nms/fra/jsp/stat.jsp), aggiungi i font.

In Debian, aggiungi il comando:

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Utilizza il seguente comando per RHEL:

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### Font per istanze giapponesi {#fonts-for-japanese-instances}

Font di caratteri specifici sono necessari per le istanze Giapponese per esportare i report in formato PDF.

In Debian, aggiungere il comando:

```
apt install fonts-ipafont
```

Per RHEL, aggiungere il seguente comando:

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### Installazione di LibreOffice per Debian {#installing-libreoffice-for-debian}

Per Debian, sono necessarie le seguenti configurazioni:

1. Installa i seguenti pacchetti standard:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installa i seguenti font (facoltativo ma altamente consigliato per Giapponese istanze):

   ```
   apt-get install fonts-ipafont
   ```

### Installazione di LibreOffice per CentOS {#installing-libreoffice-for-centos}

Le seguenti configurazioni sono necessarie con CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Livelli di accesso del database {#database-access-layers}

I layer accesso per il motore di database in uso devono essere installati nel server ed essere accessibili tramite il Adobe Campaign account. Le versioni e le modalità di installazione possono variare a seconda del motore di database utilizzato.

La versione pilota supportata è descritta nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Controlla anche la sezione generale [Database](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign supporta tutte le versioni delle librerie client PostgreSQL dalla versione 9.6: **libpq.so.5**.

L&#39;utilizzo di PostgreSQL con Adobe Campaign richiede anche l&#39;installazione delle librerie **pgcrypto** corrispondenti.

### Oracle {#oracle}

Recupera la versione libreria per Debian a 64 bit, cioè: libclntsh.so, libclntsh.so.19.1 **,** libclntsh.so.18.1 **,** libclntsh.so.12.1 **,** libclntsh.so.11.1 **o** libclntsh.so.10.1 **.******

È possibile ottenere un pacchetto RPM Linux da Oracle Technology Network.

>[!NOTE]
>
>Se hai già installato il client Oracle ma l&#39;ambiente globale (per istanza: /etc/profile) non è configurato correttamente, puoi aggiungere le **informazioni mancanti allo script nl6/customer.sh** Per ulteriori informazioni, fai riferimento a [Variabili](../../installation/using/installing-packages-with-linux.md#environment-variables) d&#39;ambiente.

**Risoluzione dei problemi e procedure consigliate**

I problemi possono comparire dopo un aggiornamento di un client o di un server Oracle, dopo una modifica della versione o alla prima installazione dell’istanza.

Se noti nella console client che nei registri sono presenti ritardi imprevisti (una o più ore), nell’ultima elaborazione del flusso di lavoro, nell’elaborazione successiva e così via, potrebbe esserci un problema tra la libreria del client Oracle e il server Oracle. Per evitare tali problemi

1. Assicurarsi di utilizzare il **client completo**.

   Sono stati identificati vari problemi durante l&#39;utilizzo della versione Oracle Instant Client. Inoltre, è impossibile modificare il file Timezone su Instant Client.

1. Assicurarsi che la **versione client e la versione** del **server database corrispondano a quella del server database****.**

   È noto che la combinazione delle versioni nonostante la matrice di compatibilità di Oracle e i consigli per l’allineamento delle versioni client e server causano problemi.

   Controlla anche il valore ORACLE_HOME per assicurarti che punti alla versione client prevista (nel caso in cui sul computer siano installate più versioni).

1. Assicurarsi che il client e il server utilizzino lo stesso **file del fuso orario**.

## Passaggi di implementazione {#implementation-steps}

Le installazioni di Adobe Campaign per Linux devono essere eseguite nella seguente sequenza: installazione del server seguita dalla configurazione dell’istanza.

Il processo di installazione è descritto in questo capitolo. I passaggi di installazione sono i seguenti:

* Passaggio 1: installazione del server applicazioni, consultare [Installazione di pacchetti con Linux](../../installation/using/installing-packages-with-linux.md).
* Passaggio 2: integrazione con un server web (facoltativo, a seconda dei componenti distribuiti).

Una volta completati i passaggi di installazione, è necessario configurare le istanze, il database e il server. Per ulteriori informazioni, consulta [Informazioni sulla configurazione iniziale](../../installation/using/about-initial-configuration.md).
