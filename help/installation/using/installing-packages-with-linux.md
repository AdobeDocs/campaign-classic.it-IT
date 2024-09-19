---
product: campaign
title: Installazione di pacchetti con Linux
description: Installazione di pacchetti con Linux
feature: Installation, Application Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: fee880f4b200b322c2b2a0034f17975993c862b3
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%

---

# Installazione di pacchetti con Linux{#installing-packages-with-linux}

Adobe Campaign viene fornito con il pacchetto **nlserver** che contiene i file binari e di configurazione per una determinata versione.



I comandi di installazione consentono di:

* Copia i file in **/usr/local/neolane**
* Creare un account Adobe Campaign Linux (e il gruppo associato) creato con **/usr/local/neolane** come home directory
* Creare uno script automatico **/etc/init.d/nlserver6** da utilizzare all&#39;avvio o creare un&#39;unità di sistema

>[!NOTE]
>
>L&#39;utente di sistema **neolane** non deve essere stato creato prima dell&#39;esecuzione del comando. L&#39;utente **neolane** viene creato automaticamente durante l&#39;installazione.
>
>Anche la directory **home** collegata all&#39;utente **neolane** viene creata automaticamente in **[!UICONTROL /usr/local/neolane]**. Verificare che lo spazio sul disco **[!UICONTROL /usr/local]** sia sufficiente.

È possibile eseguire il comando **ping`hostname`** per assicurarsi che il server possa raggiungere se stesso.

## Distribuzione basata su pacchetti RPM {#distribution-based-on-rpm--packages}

>[!AVAILABILITY]
>
>A partire dalla versione 7.4.1, le librerie XML per i pacchetti RPM Linux non sono più incluse in Campaign. È necessario installare queste librerie.
> 

Per installare Adobe Campaign su un sistema operativo RPM (RHEL, CentOS), effettuare le seguenti operazioni:

1. Ottieni il pacchetto Adobe Campaign. Il nome del file è **nlserver6-v7-XXXX-0.x86_64.rpm**, dove **XXXX** è il numero di build di Adobe Campaign.

   >[!CAUTION]
   >
   >Assicurati di utilizzare il nome file corretto per la versione di Adobe Campaign negli esempi di comandi di questa sezione.

1. Per installarlo, connettiti come **root** ed esegui il seguente comando, dove **XXXX** è il numero di build di Adobe Campaign:

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Il file rpm dipende dai pacchetti che si trovano nelle distribuzioni CentOS/Red Hat. Se non desideri utilizzare alcune di queste dipendenze (ad esempio, se desideri utilizzare Oracle JDK invece di OpenJDK), potresti dover utilizzare l’opzione &quot;nodeps&quot; di rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Il comando `bc`, obbligatorio per l&#39;esecuzione di [netreport](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), non è disponibile per impostazione predefinita in tutte le distribuzioni Linux. Per verificare se il comando è disponibile, eseguire il comando `which bc`. In caso contrario, devi installarlo.

Con CentOS è necessario installare il pacchetto bc.x86_64: connettiti come **root** ed esegui il comando seguente:

```
yum install bc.x86_64
```

## Distribuzione basata su APT (Debian) {#distribution-based-on-apt--debian-}

Per installare Adobe Campaign su un sistema operativo Debian a 64 bit, attieniti alla seguente procedura:

1. Ottieni il pacchetto Adobe Campaign. Il nome del file è **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, dove **XXXX** è il numero di build di Adobe Campaign.

   >[!CAUTION]
   >
   >Assicurati di utilizzare il nome file corretto per la versione di Adobe Campaign negli esempi di comandi di questa sezione.

1. Per installarlo, connettiti come **root** ed esegui il seguente comando, dove **XXXX** è il numero di build di Adobe Campaign:

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   In caso di dipendenze mancanti, eseguire il comando seguente:

   ```
   apt-get install -f
   ```


1. Quando installi Adobe Campaign su un sistema operativo Debian, considera quanto segue:

* OpenSSL deve essere installato in anticipo.
* Installa libicu e libc-aresYY, dove XX è la versione, con i seguenti comandi:

  ```
  apt install libicuXX
  ```

  ```
  apt install libc-aresXX
  ```

  ```
  apt install openjdk-XX-jdk
  ```

## Personalizzazione dei parametri {#personalizing-parameters}

Alcuni parametri possono essere personalizzati tramite il file **customer.sh**

Se si esegue l&#39;installazione per la prima volta, è possibile che il file **customer.sh** non esista ancora nel server.

Creala e assicurati che disponga dei diritti di esecuzione. In caso contrario, immetti il seguente comando:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codifica server {#server-encoding}

Per impostazione predefinita, il server viene avviato in un ambiente iso8859-15. Tuttavia, il server può essere avviato in un ambiente UTF-8.

>[!CAUTION]
>
>Questa modifica influisce sulle interazioni con il file system (file caricati tramite un flusso di lavoro o uno script di JavaScript) e sulla codifica del file. È quindi consigliabile utilizzare l’ambiente predefinito.

Per creare una **istanza giapponese**, è necessario utilizzare un ambiente UTF-8.

Per abilitare l’ambiente UTF-8, utilizza il seguente comando:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Variabili di ambiente {#environment-variables}

Le seguenti variabili di ambiente devono essere definite correttamente.

Alcune combinazioni richiedono modifiche all’ambiente utilizzato per eseguire Adobe Campaign. È possibile creare e modificare un file specifico (`/usr/local/neolane/nl6/customer.sh`) per aggiungere modifiche specifiche all&#39;ambiente Adobe Campaign.

Se necessario, modificare il file **customer.sh** utilizzando il comando **vi customer.sh** e adattare la configurazione o aggiungere le righe mancanti:

* Per il client di Oracle:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  Il contenuto della variabile di ambiente ORACLE_HOME corrisponde alla directory di installazione di Oracle.

  Il contenuto della variabile TNS_ADMIN deve corrispondere alla posizione del file **tnsnames.ora**.

* Per LibreOffice:

  Per eseguire Adobe Campaign su una versione esistente di LibreOffice, sono necessarie configurazioni aggiuntive: è necessario specificare i percorsi di accesso alla directory di installazione. Ad esempio:

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

  Per impostazione predefinita, lo script di configurazione dell&#39;ambiente Adobe Campaign (`~/nl6/env.sh`) cerca la directory di installazione JDK. Tuttavia, si consiglia di specificare quale JDK deve essere utilizzato. A tale scopo, è possibile forzare la variabile di ambiente **JDK_HOME** utilizzando il comando seguente:

  ```
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >Assicurati che la versione JDK utilizzata corrisponda al nome della directory.

  Per testare la configurazione JDK, accedi come utente di Adobe Campaign con il seguente comando:

  ```
  su - neolane
  ```

Per poter tenere conto delle modifiche, è necessario riavviare il servizio Adobe Campaign.

I comandi sono i seguenti:

```
systemctl stop nlserver
systemctl start nlserver
```

### Client Oracle in Linux {#oracle-client-in-linux}

Quando si utilizza Oracle con Adobe Campaign, è necessario configurare i livelli client Oracle in Linux.

* Utilizza il client completo
* Definizione TNS

  Le definizioni TNS devono essere aggiunte durante la fase di installazione. A tale scopo, utilizzare i seguenti comandi:

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Variabili di ambiente

  Consulta [Variabili di ambiente](#environment-variables).

* Configurazione per Adobe Campaign

  Per completare l&#39;installazione del client Oracle per Adobe Campaign, è necessario creare un collegamento simbolico per il file **.so** utilizzato da Adobe Campaign.

  A tale scopo, utilizzare i seguenti comandi:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

In caso di problemi, assicurati che i pacchetti elencati nella documentazione di installazione di Oracle siano installati correttamente.

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

Una volta completato il test di installazione, immettere il seguente comando:

```
nlserver web
```

Vengono quindi visualizzate le seguenti informazioni:

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Questi comandi consentono di creare **config-default.xml** e **serverConf.xml** file di configurazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Premere **Ctrl+C** per arrestare il processo, quindi immettere il comando seguente:

```
nlserver start web
```

Vengono quindi visualizzate le seguenti informazioni:

```sql
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

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Password per l’identificatore interno {#password-for-the-internal-identifier}

Il server Adobe Campaign definisce un account di accesso tecnico denominato **internal** che dispone di tutti i diritti su tutte le istanze. Subito dopo l&#39;installazione, l&#39;account di accesso non dispone di una password. È obbligatorio definirne uno.

Per ulteriori informazioni, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).
