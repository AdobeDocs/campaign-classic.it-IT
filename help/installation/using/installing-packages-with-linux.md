---
solution: Campaign Classic
product: campaign
title: Installazione di pacchetti con Linux
description: Installazione di pacchetti con Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 1%

---


# Installazione di pacchetti con Linux{#installing-packages-with-linux}

Per una piattaforma Linux a 32 bit, installate  Adobe Campaign a 32 bit. Per una piattaforma Linux a 64 bit, installate  Adobe Campaign a 64 bit.

Per ciascuna di queste versioni,  Adobe Campaign viene fornito con un pacchetto: **nlserver**. Questo pacchetto contiene i file binari e di configurazione per una determinata versione.

I comandi di installazione consentono di:

* Copiare i file in **/usr/local/neolane**
* Create un account Adobe Campaign Linux  (e il gruppo associato), creato con **/usr/local/neolane** come directory principale
* Create uno script automatico **/etc/init.d/nlserver6** da utilizzare all&#39;avvio oppure create un&#39;unità di sistema (a partire dalla versione 20.1).

>[!NOTE]
>
>L&#39;utente di sistema **neolane** non deve essere stato creato prima dell&#39;esecuzione del comando. L&#39;utente **neolane** viene creato automaticamente durante l&#39;installazione.
>
>Anche la directory **home** collegata all&#39;utente **neolane** viene creata automaticamente in **[!UICONTROL /usr/local/neolane]**. Verificare che lo spazio disponibile sul disco **[!UICONTROL /usr/local]** (diversi GB) sia sufficiente.

È possibile eseguire il comando **ping`hostname`** per essere certi che il server possa raggiungere se stesso.

## Distribuzione in base ai pacchetti RPM {#distribution-based-on-rpm--packages}

Per installare  Adobe Campaign su un sistema operativo RPM (RHEL, CentOS e SUSE), procedere come segue:

1. Dovete innanzitutto ottenere il pacchetto Adobe Campaign .

   Il file è denominato come di seguito, dove **XXXX** è il numero  di build Adobe Campaign:

   * **nlserver6-v7-XXXX-0.x86_64.** rpmper v7.
   * **nlserver6-XXXX-0.x86_64.** rpmfor v6.1.

   >[!CAUTION]
   >
   >Accertatevi di utilizzare il nome file corretto per la versione di  Adobe Campaign negli esempi di comando di questa sezione.

1. Per installarlo, collegarsi come **root** ed eseguire il comando seguente (dove **XXXX** è il numero  di build Adobe Campaign):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Il file rpm ha dipendenze su pacchetti che è possibile trovare sulle distribuzioni CentOS/Red Hat. Se non si desidera utilizzare alcune di queste dipendenze (ad esempio, se si desidera utilizzare  Oracle JDK invece di OpenJDK), potrebbe essere necessario utilizzare l&#39;opzione &quot;nodeps&quot; di rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Il comando &#39;bc&#39;, necessario per l&#39;esecuzione del netreport (fare riferimento a [questa sezione](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) per ulteriori informazioni), non è disponibile per impostazione predefinita in tutte le distribuzioni Linux. Per verificare se il comando è disponibile, eseguite il comando &#39;quale bc&#39;. In caso contrario, è necessario installarlo.

Con CentOS, è necessario installare il pacchetto bc.x86_64: collegarsi come **root** ed eseguire il comando seguente:

```
yum install bc.x86_64
```

## Distribuzione basata su APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 64 bit {#in-debian-64-bits}

Per installare  Adobe Campaign a 64 bit su un sistema operativo Debian a 64 bit, attenersi alla procedura seguente:

1. Dovete innanzitutto ottenere il pacchetto Adobe Campaign .

   * **nlserver6-v7-XXXX-linux-2.6-amd64.** debfor v7.
   * **nlserver6-XXXX-linux-2.6-amd64.** debfor v6.1.

   **** XXXX è il numero  di build Adobe Campaign.

   >[!CAUTION]
   >
   >Accertatevi di utilizzare il nome file corretto per la versione di  Adobe Campaign negli esempi di comando di questa sezione.

1. Per installarlo, collegarsi come **root** ed eseguire il comando seguente (dove **XXXX** è il numero  di build Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Se mancano dipendenze, eseguire il comando seguente:

   ```
   apt-get install -f
   ```

**Specifiche Debian 8/9**

Quando installate  Adobe Campaign su un sistema operativo Debian 8/9, considerate quanto segue:

* OpenSSL deve essere installato in anticipo.
* Installate libicu52 (Debian 8) o libicu57 (Debian 9), libprotobuf9 (Debian8) e libc-ares2 con i seguenti comandi:

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* Installate JDK7 con il seguente comando:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## Personalizzazione dei parametri {#personalizing-parameters}

Alcuni parametri possono essere personalizzati tramite il file **customer.sh**

Se si esegue l&#39;installazione per la prima volta, il file **customer.sh** potrebbe non essere ancora presente sul server. Createla e accertatevi che disponga dei diritti di esecuzione. In caso contrario, digitate il comando seguente:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codifica server {#server-encoding}

Per impostazione predefinita, il server viene avviato in un ambiente iso8859-15. Tuttavia, il server può essere avviato in un ambiente UTF-8.

>[!CAUTION]
>
>Questa modifica interessa le interazioni con il file system (file caricati tramite un flusso di lavoro o uno script JavaScript) e la codifica dei file. Si consiglia pertanto di utilizzare l&#39;ambiente predefinito.

Tuttavia, per creare un&#39;istanza **giapponese**, è necessario utilizzare un ambiente UTF-8.

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

Alcune combinazioni richiedono modifiche all&#39;ambiente utilizzato per eseguire  Adobe Campaign. È possibile creare e modificare un file specifico (`/usr/local/neolane/nl6/customer.sh`) per aggiungere modifiche specifiche all&#39;ambiente Adobe Campaign .

Se necessario, modificare il file **customer.sh** utilizzando il comando **vi customer.sh** e adattare la configurazione o aggiungere righe mancanti:

* Per il client Oracle :

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   Il contenuto della variabile di ambiente  ORACLE_HOME corrisponde alla directory di installazione  Oracle.

   Il contenuto della variabile TNS_ADMIN deve corrispondere alla posizione del file **tnsnames.ora**.

* Per LibreOffice:

   Per eseguire  Adobe Campaign su una versione esistente di LibreOffice, sono necessarie configurazioni aggiuntive: dovete specificare i percorsi di accesso alla directory di installazione. Ad esempio:

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

   Per impostazione predefinita, lo script di configurazione dell&#39;ambiente Adobe Campaign  (`~/nl6/env.sh`) cerca la directory di installazione JDK. Poiché questo comportamento non è affidabile al 100%, è necessario specificare quale JDK deve essere utilizzato. A tal fine, è possibile forzare la variabile di ambiente **JDK_HOME** utilizzando il seguente comando:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Questo è un esempio. Verificate che la versione JDK utilizzata corrisponda al nome della directory.

   Per verificare la configurazione JDK, accedete come utente del sistema Adobe Campaign  con il seguente comando:

   ```
   su - neolane
   ```

Per tenere conto delle modifiche, è necessario riavviare il servizio Adobe Campaign .

I comandi sono i seguenti:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

A partire da 20.1, si consiglia di utilizzare i seguenti comandi:

```
systemctl stop nlserver
systemctl start nlserver
```

###  client Oracle in Linux {#oracle-client-in-linux}

Quando si utilizza  Oracle con  Adobe Campaign, è necessario configurare i livelli client  Oracle in Linux.

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

   Fare riferimento a [Variabili di ambiente](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Configurazione per  Adobe Campaign

   Per completare l&#39;installazione del client Oracle  per  Adobe Campaign, è necessario creare un collegamento simbolico per il file **.so** utilizzato da  Adobe Campaign.

   A questo scopo, utilizzate i seguenti comandi:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

In caso di problemi, accertatevi che i pacchetti elencati nella [ documentazione di installazione Oracle](https://www.oracle.com/pls/db112/portal.portal_db?selected=11) siano installati correttamente.

## Controlli di installazione {#installation-checks}

È ora possibile eseguire una prova di installazione iniziale utilizzando i comandi seguenti:

```
su - neolane
nlserver pdump
```

Quando  Adobe Campaign non viene avviato, la risposta è:

```
no task
```

## Primo avvio del server {#first-start-up-of-the-server}

Una volta completato il test di installazione, immettete il comando seguente:

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

Questi comandi consentono di creare file di configurazione **config-default.xml** e **serverConf.xml**. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Premere **Ctrl+C** per arrestare il processo, quindi immettere il comando seguente:

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

## Password per l&#39;identificatore interno {#password-for-the-internal-identifier}

Il server Adobe Campaign  definisce un login tecnico denominato **internal** che dispone di tutti i diritti in tutte le istanze. Subito dopo l&#39;installazione, il login non dispone di una password. È obbligatorio definirne una.

Vedere la sezione [Identificatore interno](../../installation/using/campaign-server-configuration.md#internal-identifier).
