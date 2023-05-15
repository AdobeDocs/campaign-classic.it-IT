---
product: campaign
title: Installazione di pacchetti con Linux
description: Installazione di pacchetti con Linux
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 1%

---

# Installazione di pacchetti con Linux{#installing-packages-with-linux}



Per una piattaforma Linux a 32 bit, installare Adobe Campaign a 32 bit. Per una piattaforma Linux a 64 bit, installare Adobe Campaign a 64 bit.

Per ciascuna di queste versioni, Adobe Campaign viene fornito con un pacchetto: **nlserver**. Questo pacchetto contiene i file binari e di configurazione per una determinata versione.

I comandi di installazione consentono di:

* Copia i file in **/usr/local/neolane**
* Crea un account Adobe Campaign Linux (e il gruppo associato), che viene creato con **/usr/local/neolane** come home directory
* Creare uno script automatico **/etc/init.d/nlserver6** da utilizzare all&#39;avvio o creare un&#39;unità di sistema (a partire dalla versione 20.1).

>[!NOTE]
>
>La **neolano** l&#39;utente di sistema non deve essere stato creato prima dell&#39;esecuzione del comando. La **neolano** l&#39;utente viene creato automaticamente durante l&#39;installazione.
>
>La **home** directory collegata al **neolano** viene creato automaticamente anche in **[!UICONTROL /usr/local/neolane]**. Assicurati che ci sia spazio sufficiente sul **[!UICONTROL /usr/local]** disco (diversi GB).

Puoi eseguire il **ping`hostname`** per assicurarsi che il server possa raggiungere se stesso.

## Distribuzione basata su pacchetti RPM {#distribution-based-on-rpm--packages}

Per installare Adobe Campaign su un sistema operativo RPM (RHEL, CentOS e SUSE), esegui i seguenti passaggi:

1. Devi prima ottenere il pacchetto Adobe Campaign.

   Il file viene denominato come segue, dove **XXXX** è il numero della build Adobe Campaign:

   * **nlserver6-v7-XXXX-0.x86_64.rpm** per v7.
   * **nlserver6-XXXX-0.x86_64.rpm** per la versione 6.1.

   >[!CAUTION]
   >
   >Assicurati di utilizzare il nome file corretto per la versione di Adobe Campaign negli esempi di comando di questa sezione.

1. Per installarlo, connettiti come **root** ed esegui il seguente comando (dove **XXXX** è il numero di build di Adobe Campaign):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Il file rpm ha dipendenze da pacchetti che è possibile trovare sulle distribuzioni CentOS/Red Hat. Se non si desidera utilizzare alcune di queste dipendenze (ad esempio, se si desidera utilizzare Oracle JDK invece di OpenJDK), potrebbe essere necessario utilizzare l&#39;opzione &quot;nodeps&quot; di rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Il comando &#39;bc&#39;, necessario per l&#39;esecuzione del rapporto di rete (fare riferimento a [questa sezione](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) per ulteriori informazioni), non è disponibile per impostazione predefinita su tutte le distribuzioni Linux. Per verificare se il comando è disponibile, esegui il comando &#39;quale bc&#39;. In caso contrario, è necessario installarlo.

Con CentOS, devi installare il pacchetto bc.x86_64: connetti come **root** ed esegui il comando seguente:

```
yum install bc.x86_64
```

## Distribuzione basata su APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 64 bit {#in-debian-64-bits}

Per installare Adobe Campaign a 64 bit su un sistema operativo Debian a 64 bit, esegui i seguenti passaggi:

1. Devi prima ottenere il pacchetto Adobe Campaign.

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** per v7.
   * **nlserver6-XXXX-linux-2.6-amd64.deb** per la versione 6.1.

   **XXXX** è il numero di build di Adobe Campaign.

   >[!CAUTION]
   >
   >Assicurati di utilizzare il nome file corretto per la versione di Adobe Campaign negli esempi di comando di questa sezione.

1. Per installarlo, connettiti come **root** ed esegui il seguente comando (dove **XXXX** è il numero di build di Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Se mancano dipendenze, esegui il seguente comando:

   ```
   apt-get install -f
   ```

**Specifiche Debian 8/9**

Quando installi Adobe Campaign su un sistema operativo Debian 8/9, considera quanto segue:

* OpenSSL deve essere installato in precedenza.
* Installa libicu52 (Debian 8) o libicu57 (Debian 9), libprotobuf9 (Debian8) e libc-ares2 con i seguenti comandi:

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* Installa JDK7 con il seguente comando:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## Personalizzazione dei parametri {#personalizing-parameters}

Alcuni parametri possono essere personalizzati tramite il **customer.sh** file

Se si esegue l&#39;installazione per la prima volta, la **customer.sh** file potrebbe non esistere sul server. Crealo e assicurati che disponga dei diritti di esecuzione. In caso contrario, immettere il comando seguente:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codifica server {#server-encoding}

Per impostazione predefinita, il server viene avviato in un ambiente iso8859-15. Tuttavia, il server può essere avviato in un ambiente UTF-8.

>[!CAUTION]
>
>Questa modifica interessa le interazioni con il file system (file caricati tramite un flusso di lavoro o uno script JavaScript) e la codifica dei file. Si consiglia quindi di utilizzare l’ambiente predefinito.

Tuttavia, per creare un **istanza giapponese**, è necessario utilizzare un ambiente UTF-8.

Per abilitare l&#39;ambiente UTF-8, utilizza il comando seguente:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Lingua predefinita per il server {#default-language-for-the-server}

L&#39;installazione supporta sia inglese che francese. L’inglese viene utilizzato per impostazione predefinita.

Per passare al francese, immettere i seguenti comandi:

```
su - neolane
vi nl6/customer.sh
```

e aggiungi la seguente riga:

```
export neolane_LANG=fra
```

Per garantire la corretta lettura dei messaggi di sistema, le console devono trovarsi in una tabella di codice corrispondente alla lingua (ISO-8859-1 o -15 per il francese).

### Variabili di ambiente {#environment-variables}

Le seguenti variabili di ambiente devono essere definite correttamente.

Alcune combinazioni richiedono modifiche all’ambiente utilizzato per l’esecuzione di Adobe Campaign. Un file specifico (`/usr/local/neolane/nl6/customer.sh`) può essere creata e modificata per aggiungere modifiche specifiche all’ambiente Adobe Campaign.

Se necessario, modifica il **customer.sh** utilizzando **vi customer.sh** comanda e adatta la configurazione o aggiungi le righe mancanti:

* Per il client Oracle:

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   Il contenuto della variabile di ambiente ORACLE_HOME corrisponde alla directory di installazione di Oracle.

   Il contenuto della variabile TNS_ADMIN deve corrispondere alla posizione della variabile **tnsnames.ora** file.

* Per LibreOffice:

   Per eseguire Adobe Campaign su una versione esistente di LibreOffice, sono necessarie configurazioni aggiuntive: è necessario specificare i percorsi di accesso alla directory di installazione. Per esempio:

   * Debian

      Vengono forniti i valori predefiniti per OOO_INSTALL_DIR e OOO_BASIS_INSTALL_DIR. È possibile sostituirli in **customer.sh** se il layout dell&#39;installazione di LibreOffice è diverso:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      ```

   * CentOs

      Utilizza i seguenti valori predefiniti:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      ```

* Per Java Development Kit (JDK):

   Per impostazione predefinita, lo script di configurazione dell’ambiente Adobe Campaign (`~/nl6/env.sh`) cerca la directory di installazione di JDK. Poiché questo comportamento non è affidabile al 100%, è necessario specificare quale JDK deve essere utilizzato. A questo scopo, puoi forzare la **JDK_HOME** variabile di ambiente utilizzando il comando seguente:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Questo è un esempio. Assicurati che la versione JDK utilizzata corrisponda al nome della directory.

   Per verificare la configurazione JDK, accedi come utente di sistema Adobe Campaign con il seguente comando:

   ```
   su - neolane
   ```

È necessario riavviare il servizio Adobe Campaign per tenere conto delle modifiche.

I comandi sono i seguenti:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

A partire dalla versione 20.1, è consigliabile utilizzare i seguenti comandi:

```
systemctl stop nlserver
systemctl start nlserver
```

### Client Oracle in Linux {#oracle-client-in-linux}

Quando utilizzi Oracle con Adobe Campaign, devi configurare i livelli client di Oracle in Linux.

* Utilizzare il client completo
* Definizione TNS

   Le definizioni TNS devono essere aggiunte durante la fase di installazione. A questo scopo, utilizza i seguenti comandi:

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* Variabili di ambiente

   Fai riferimento a [Variabili di ambiente](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Configurazione per Adobe Campaign

   Per completare l’installazione del client Oracle per Adobe Campaign, devi creare un collegamento simbolico per il **.so** file utilizzato da Adobe Campaign.

   A questo scopo, utilizza i seguenti comandi:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

Se incontri un problema, assicurati che i pacchetti elencati in [Documentazione di installazione di Oracle](https://docs.oracle.com/) installati correttamente.

## Controlli di installazione {#installation-checks}

È ora possibile eseguire un test di installazione iniziale utilizzando i seguenti comandi:

```
su - neolane
nlserver pdump
```

Quando Adobe Campaign non viene avviato, la risposta è:

```
no task
```

## Primo avvio del server {#first-start-up-of-the-server}

Al termine del test di installazione, immettere il comando seguente:

```
nlserver web
```

Vengono quindi visualizzate le seguenti informazioni:

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Questi comandi consentono di creare **config-default.xml** e **serverConf.xml** file di configurazione. Tutti i parametri disponibili nel **serverConf.xml** sono elencati in [sezione](../../installation/using/the-server-configuration-file.md).

Press **Ctrl+C** per interrompere il processo, immettere il comando seguente:

```
nlserver start web
```

Vengono quindi visualizzate le seguenti informazioni:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Per interromperlo, immetti:

```
nlserver stop web
```

Vengono quindi visualizzate le seguenti informazioni:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Password per l’identificatore interno {#password-for-the-internal-identifier}

Il server Adobe Campaign definisce un accesso tecnico denominato **interno** che ha tutti i diritti su tutte le istanze. Subito dopo l&#39;installazione, l&#39;accesso non dispone di una password. È obbligatorio definirne uno.

Per ulteriori informazioni, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).
