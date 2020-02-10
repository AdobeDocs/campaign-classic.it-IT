---
title: Installazione di pacchetti con Linux
seo-title: Installazione di pacchetti con Linux
description: Installazione di pacchetti con Linux
seo-description: null
page-status-flag: never-activated
uuid: d83f00b5-500b-406a-a3d6-ea5639f244f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 04faa9f3-d160-4060-b26e-44333f2faf71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ad1a83d40f5a841b01aaeb17fe271b44f2480dd

---


# Installazione di pacchetti con Linux{#installing-packages-with-linux}

Per una piattaforma Linux a 32 bit, installa Adobe Campaign a 32 bit. Per una piattaforma Linux a 64 bit, installa Adobe Campaign a 64 bit.

Per ciascuna di queste versioni, Adobe Campaign include un pacchetto: **nlserver**. Questo pacchetto contiene i file binari e di configurazione per una determinata versione.

I comandi di installazione consentono di:

* Copiare i file in **/user/local/neolane**
* Create un account Linux Adobe Campaign (e il gruppo associato), creato con **/usr/local/neolane** come directory principale
* Creare uno script automatico **/etc/init.d/nlserver6** da utilizzare all&#39;avvio

Questo pacchetto viene compilato utilizzando GCC 4, il che implica dipendenze con versioni specifiche delle librerie che non sono sempre disponibili sulla piattaforma di installazione.

>[!NOTE]
>
>L&#39;utente del sistema **neolano** non deve essere stato creato prima dell&#39;esecuzione del comando. L&#39;utente **neolane** viene creato automaticamente durante l&#39;installazione.
>
>Viene creata automaticamente anche la directory **principale** collegata all&#39;utente del **neolane** in **[!UICONTROL /usr/local/neolane]**. Verificare che lo spazio sul **[!UICONTROL /usr/local]** disco sia sufficiente (diversi GB).

È possibile eseguire il **comando ping`hostname`**per assicurarsi che il server possa raggiungere se stesso.

## Distribuzione in base ai pacchetti RPM {#distribution-based-on-rpm--packages}

Per installare Adobe Campaign su un sistema operativo RPM (RHEL, CentOS e SUSE), effettua i seguenti passaggi:

1. Devi prima ottenere il pacchetto Adobe Campaign.

   Il file è denominato come di seguito, dove **XXXX** è il numero di build di Adobe Campaign:

   * **nlserver6-v7-XXXX-0.x86_64.rpm** per v7.
   * **nlserver6-XXXX-0.x86_64.rpm** per v6.1.
   >[!CAUTION]
   >
   >Accertatevi di utilizzare il nome file corretto per la versione di Adobe Campaign negli esempi di comando di questa sezione.

1. Per installarlo, connettiti come **root** ed esegui il seguente comando (dove **XXXX** è il numero di build di Adobe Campaign):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Il file rpm ha dipendenze su pacchetti che è possibile trovare sulle distribuzioni CentOS/Red Hat. Se non si desidera utilizzare alcune di queste dipendenze (ad esempio, se si desidera utilizzare Oracle JDK invece di OpenJDK), potrebbe essere necessario utilizzare l&#39;opzione &quot;nodeps&quot; di rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Il comando &#39;bc&#39;, necessario per eseguire il netreport (fare riferimento a [questa sezione](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) per ulteriori informazioni), non è disponibile per impostazione predefinita in tutte le distribuzioni Linux. Per verificare se il comando è disponibile, eseguite il comando &#39;quale bc&#39;. In caso contrario, è necessario installarlo.

Con CentOS, è necessario installare il pacchetto bc.x86_64: collegarsi come **root** ed eseguire il comando seguente:

```
yum install bc.x86_64
```

**Esempio di installazione su SLES 11 SP2:**

* Disattiva **[!UICONTROL libboost_regex]** :

   ```
   zypper remove libboost_regex1_36_0
   ```

* Installare Oracle Java o OpenJDK (per ulteriori informazioni, fare riferimento a [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk)):

   ```
   ./jdk-6uxx-linux-x64-rpm.bin
   ```

* Installate OpenSSL 1.0 (per ulteriori informazioni, consultate [Librerie](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#libraries)):

   ```
   yast -i libopenssl1_0_0-1.0.0c-18.42.1.x86_64.rpm
   ```

   È necessario creare alias che puntino ai file della libreria OpenSSL:

   ```
   ln -s /lib64/libssl.so.1.0.0 /lib64/libssl.so.10
   ln -s /lib64/libcrypto.so.1.0.0 /lib64/libcrypto.so.10
   ```

* Installate libicu 4.2 (per ulteriori informazioni, consultate [Librerie](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#libraries)):

   ```
   yast -i libicu-4.2-7.3.1.x86_64.rpm
   ```

* Installa il pacchetto del server Adobe Campaign:

   ```
   yast -i nlserver6-v7-xxx-x.x86_64.rpm
   ```

## Distribuzione basata su APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 32 bit {#in-debian-32-bits}

Per installare Adobe Campaign a 32 bit su un sistema operativo Debian a 32 bit, effettua i seguenti passaggi:

1. Devi prima ottenere i due pacchetti Adobe Campaign.

   * **nlserver6-v7-XXXX-linux-2.6-intel.deb** per v7.
   * **nlserver6-XXXX-linux-2.6-intel.deb** per v6.1.
   **XXXX** è il numero di build di Adobe Campaign.

   >[!CAUTION]
   >
   >Accertatevi di utilizzare il nome file corretto per la versione di Adobe Campaign negli esempi di comando di questa sezione.

1. Per installarlo, connettiti come **root** ed esegui il seguente comando (dove **XXXX** è il numero di build di Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-intel.deb
   ```

   Se mancano dipendenze, eseguire il comando seguente:

   ```
   apt-get install -f
   ```

### In Debian 64 bit {#in-debian-64-bits}

Per installare Adobe Campaign a 64 bit su un sistema operativo Debian a 64 bit, effettua i seguenti passaggi:

1. Devi prima ottenere il pacchetto Adobe Campaign.

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** per v7.
   * **nlserver6-XXXX-linux-2.6-amd64.deb** per v6.1.
   **XXXX** è il numero di build di Adobe Campaign.

   >[!CAUTION]
   >
   >Accertatevi di utilizzare il nome file corretto per la versione di Adobe Campaign negli esempi di comando di questa sezione.

1. Per installarlo, connettiti come **root** ed esegui il seguente comando (dove **XXXX** è il numero di build di Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

**Specifiche Debian 7/8**

Durante l&#39;installazione di Adobe Campaign su un sistema operativo Debian 7, tieni presente quanto segue:

* OpenSSL deve essere installato in anticipo.
* Installate libicu48 (Debian 7), libicu52 (Debian 8) o libicu57 (Debian 9), libprotobuf9 (Debian8) e libc-ares2 con i seguenti comandi:

   ```
   aptitude install libicu48 (Debian 7) libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 7/8)
   ```

* Installate JDK7 con il seguente comando:

   ```
   aptitude install openjdk-7-jdk (Debian 7/8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## Personalizzazione dei parametri {#personalizing-parameters}

Alcuni parametri possono essere personalizzati tramite il file **customer.sh**

Se si esegue l&#39;installazione per la prima volta, il file **customer.sh** potrebbe non esistere ancora sul server. Createla e accertatevi che disponga dei diritti di esecuzione. In caso contrario, digitate il comando seguente:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codifica server {#server-encoding}

Per impostazione predefinita, il server viene avviato in un ambiente iso8859-15. Tuttavia, il server può essere avviato in un ambiente UTF-8.

>[!CAUTION]
>
>Questa modifica interessa le interazioni con il file system (file caricati tramite un flusso di lavoro o uno script JavaScript) e la codifica dei file. È quindi consigliabile utilizzare l&#39;ambiente predefinito.

Tuttavia, per creare un&#39;istanza **** giapponese è necessario utilizzare un ambiente UTF-8.

Per abilitare l&#39;ambiente UTF-8, utilizzare il comando seguente:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Lingua predefinita per il server {#default-language-for-the-server}

L&#39;installazione supporta sia l&#39;inglese che il francese. L&#39;inglese è utilizzato per impostazione predefinita.

Per passare al francese, immettete i seguenti comandi:

```
su - neolane
vi nl6/customer.sh
```

e aggiungete la seguente riga:

```
export neolane_LANG=fra
```

Per garantire la corretta lettura dei messaggi di sistema, le console devono trovarsi in una tabella codici corrispondente alla lingua (ISO-8859-1 o -15 per il francese).

### Variabili di ambiente {#environment-variables}

Le seguenti variabili di ambiente devono essere definite correttamente.

Alcune combinazioni richiedono modifiche all&#39;ambiente utilizzato per l&#39;esecuzione di Adobe Campaign. È possibile creare e modificare un file (`/usr/local/neolane/nl6/customer.sh`) specifico per aggiungere modifiche specifiche all&#39;ambiente Adobe Campaign.

Se necessario, modificate il file **customer.sh** utilizzando il comando **vi customer.sh** e adattate la configurazione o aggiungete le righe mancanti:

* Per il client Oracle:

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   Il contenuto della variabile di ambiente ORACLE_HOME corrisponde alla directory di installazione di Oracle.

   Il contenuto della variabile TNS_ADMIN deve corrispondere alla posizione del file **tnsnames.ora** .

* Per LibreOffice:

   Per eseguire Adobe Campaign su una versione esistente di LibreOffice, sono necessarie configurazioni aggiuntive: dovete specificare i percorsi di accesso alla directory di installazione. Ad esempio:

   * Debian

      Sono forniti i valori predefiniti per OOO_INSTALL_DIR, OOOO_BASIS_INSTALL_DIR, OOO_URE_INSTALL_DIR. È possibile sostituirli in **customer.sh** se il layout dell&#39;installazione di LibreOffice è diverso:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      Utilizzate i seguenti valori predefiniti:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* Per Java Development Kit (JDK):

   Per impostazione predefinita, lo script di configurazione dell&#39;ambiente Adobe Campaign (`~/nl6/env.sh`) cerca la directory di installazione JDK. Poiché questo comportamento non è affidabile al 100%, è necessario specificare quale JDK deve essere utilizzato. A questo scopo, potete applicare la variabile di ambiente **JDK_HOME** utilizzando il seguente comando:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Questo è un esempio. Verificate che la versione JDK utilizzata corrisponda al nome della directory.

   Per verificare la configurazione JDK, accedi come utente del sistema Adobe Campaign con il seguente comando:

   ```
   su - neolane
   ```

Per tenere conto delle modifiche, devi riavviare il servizio Adobe Campaign.

I comandi sono i seguenti:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

### Client Oracle in Linux {#oracle-client-in-linux}

Quando si utilizza Oracle con Adobe Campaign, è necessario configurare i livelli client Oracle in Linux.

* Utilizza il client completo
* Definizione TNS

   Le definizioni TNS devono essere aggiunte durante la fase di installazione. A questo scopo, utilizzate i seguenti comandi:

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* Variabili di ambiente

   Fare riferimento a Variabili [di](../../installation/using/installing-packages-with-linux.md#environment-variables)ambiente.

* Configurazione per Adobe Campaign

   Per completare l&#39;installazione del client Oracle per Adobe Campaign, è necessario creare un collegamento simbolico per il file **.so** utilizzato da Adobe Campaign.

   A questo scopo, utilizzate i seguenti comandi:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

Se si verifica un problema, verificare che i pacchetti elencati nella documentazione [di installazione di](http://www.oracle.com/pls/db112/portal.portal_db?selected=11) Oracle siano correttamente installati.

## Controlli di installazione {#installation-checks}

È ora possibile eseguire una prova di installazione iniziale utilizzando i comandi seguenti:

```
su - neolane
nlserver pdump
```

Quando Adobe Campaign non viene avviato, la risposta è:

```
no task
```

## Primo avvio del server {#first-start-up-of-the-server}

Al termine del test di installazione, immettete il comando seguente:

```
nlserver web
```

Vengono quindi visualizzate le informazioni seguenti:

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Questi comandi consentono di creare file di configurazione **config-default.xml** e **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Premere **Ctrl+C** per interrompere il processo, quindi digitare il comando seguente:

```
nlserver start web
```

Vengono quindi visualizzate le informazioni seguenti:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Per interromperlo, immettere:

```
nlserver stop web
```

Vengono quindi visualizzate le informazioni seguenti:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Password per l’identificatore interno {#password-for-the-internal-identifier}

Il server Adobe Campaign definisce un login tecnico denominato **interno** che dispone di tutti i diritti in tutte le istanze. Subito dopo l&#39;installazione, il login non dispone di una password. È obbligatorio definirne una.

Vedere sezione Identificatore [](../../installation/using/campaign-server-configuration.md#internal-identifier)interno.
