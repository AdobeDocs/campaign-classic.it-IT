---
product: campaign
title: Migrazione in Linux per Adobe Campaign v7
description: Migrazione in Linux per Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---

# Migrazione in Linux per Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## Procedura generale {#general-procedure}

I passaggi di migrazione in Linux sono i seguenti:

1. Servizi di arresto: vedere [Arresto del servizio](#service-stop).
1. Salva il database: vedere [Eseguire il backup del database e dell&#39;installazione esistente](#back-up-the-database-and-the-existing-installation).
1. Disinstalla i pacchetti della versione precedente di Adobe Campaign: consulta [Disinstallazione dei pacchetti della versione precedente di Adobe Campaign](#uninstalling-adobe-campaign-previous-version-packages).
1. Esegui la migrazione della piattaforma: fai riferimento a [Distribuzione di Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Servizio di riavvio: fare riferimento a [Riavvio di servizi](#re-starting-services).

## Arresto del servizio {#service-stop}

In primo luogo, interrompere tutti i processi con accesso al database su tutti i computer interessati.

1. Accedi come **root**.
1. Tutti i server che utilizzano il modulo di reindirizzamento (**webmdl** servizio) devono essere arrestati. Per Apache, esegui il seguente comando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Accedi di nuovo come **root**.
1. Arresta i servizi della versione precedente di Adobe Campaign su tutti i server.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Se stai eseguendo la migrazione dalla versione v5.11, esegui il seguente comando:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Assicurati che i servizi Adobe Campaign siano arrestati su ogni server.

   ```
   ps waux | grep nlserver
   ```

   Viene visualizzato l’elenco dei processi attivi insieme al relativo ID (PID).

1. Se uno o più processi Adobe Campaign sono ancora attivi o bloccati dopo qualche minuto, eliminali.

   ```
   killall nlserver
   ```

1. Se alcuni processi sono ancora attivi dopo alcuni minuti, puoi forzarli a chiuderli utilizzando il comando :

   ```
   killall -9 nlserver
   ```

## Eseguire il backup del database e dell&#39;installazione esistente {#back-up-the-database-and-the-existing-installation}

La procedura dipende dalla versione precedente di Adobe Campaign.

### Migrazione da Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Esegui un backup del database Adobe Campaign.
1. Accedi come **neolane** e fai un backup della directory **nl5** utilizzando il seguente comando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Per precauzione, ti consigliamo di comprimere la cartella **nl5.back** e salvarla in un percorso sicuro diverso dal server.

1. Modifica il file **config-`<instance name>`.xml** (nella cartella **nl5.back**) per impedire che il file **mta**, **wfserver**, **stat** ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituisci **autoStart** con **_autoStart** (ancora come **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migrazione da Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Esegui un backup del database Adobe Campaign.
1. Accedi come **neolane** e fai un backup della directory **nl6** utilizzando il seguente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Per precauzione, ti consigliamo di comprimere la cartella **nl6.back** e salvarla in un percorso sicuro diverso dal server.

1. Modifica il file **config-`<instance name>`.xml** (nella cartella **nl6.back**) per impedire che il file **mta**, **wfserver**, **stat**, ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituisci **autoStart** con **_autoStart** (ancora come **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migrazione da Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Esegui un backup del database Adobe Campaign.
1. Accedi come **neolane** e fai un backup della directory **nl6** utilizzando il seguente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Per precauzione, ti consigliamo di comprimere la cartella **nl6.back** e salvarla in un percorso sicuro diverso dal server.

## Disinstallazione dei pacchetti della versione precedente di Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

La procedura dipende dalla versione precedente di Adobe Campaign.

### Disinstallazione dei pacchetti Adobe Campaign v5 {#uninstalling-adobe-campaign-v5-packages}

1. Accedi come **root**.
1. Identifica i pacchetti Adobe Campaign installati utilizzando il seguente comando.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Viene visualizzato l&#39;elenco dei pacchetti installati:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * In **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Disinstalla i pacchetti Adobe Campaign v5.

   * In **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Disinstallazione dei pacchetti Adobe Campaign v6 {#uninstalling-adobe-campaign-v6-packages}

Questa sezione mostra come disinstallare i pacchetti Adobe Campaign v6.02 o v6.1.

1. Accedi come **root**.
1. Identifica i pacchetti Adobe Campaign installati utilizzando il seguente comando.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Viene visualizzato l&#39;elenco dei pacchetti installati:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * In **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Disinstalla i pacchetti Adobe Campaign v6.

   * In **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Distribuzione di Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La procedura dipende dalla versione precedente di Adobe Campaign.

### Migrazione da Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

La distribuzione di Adobe Campaign prevede due fasi:

* Installazione dei pacchetti Adobe Campaign v7: questa operazione deve essere eseguita su ciascun server.
* L&#39;aggiornamento post: questo comando deve essere avviato su ogni istanza.

Per distribuire Adobe Campaign, esegui i seguenti passaggi:

1. Installa i pacchetti Adobe Campaign v7 più recenti utilizzando il seguente comando:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >È necessario installare correttamente i pacchetti prima di passare al passaggio successivo.

   >[!NOTE]
   >
   >Durante la migrazione dalla versione v5.11, Adobe Campaign viene installato nella directory **/usr/local/neolane/nl6/** per impostazione predefinita.
   >
   >Una volta installati i pacchetti, viene visualizzato il seguente messaggio: Opzione **&#39;WdbcTimeZone&#39; mancante**. Questo è normale.

1. Per rendere disponibile il programma di installazione della console client, copialo nella directory di installazione di Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Per ulteriori informazioni su come installare Adobe Campaign in Linux, consulta [questa sezione](../../installation/using/installing-campaign-standard-packages.md).

1. Modifica il file **.bashrd** che corrisponde all&#39;utente **neolane**. Accedi come **neolane** ed esegui il seguente comando:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Quando effettui l&#39;accesso come **neolane**, viene visualizzato il seguente messaggio: **nl5/env.sh : Nessun file o directory di questo tipo**. Questo è normale.

   Alla fine del file, sostituisci **nl5/env.sh** con **nl6/env.sh**.

1. Accedi come **root** e prepara l&#39;istanza utilizzando i seguenti comandi:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >Questi comandi consentono di creare il sistema di file interni Adobe Campaign v6: Directory **conf** (con la directory **config-default.xml** e **file serverConf.xml**), **var**.

1. Vai alla cartella di backup **nl5.back** e copia (sovrascrive) i file di configurazione e le sottocartelle di ogni istanza. Accedi come **neolane** ed esegui il seguente comando:

   >[!IMPORTANT]
   >
   >Per il primo comando sottostante, non copiare il file **config-default.xml**.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Nei file Adobe Campaign v7 **serverConf.xml** e **config-default.xml** , applica le configurazioni specifiche disponibili per Adobe Campaign v5. Per il file **serverConf.xml**, utilizza il file **nl5/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Quando esegui il reporting delle configurazioni da Adobe Campaign v5 ad Adobe Campaign v7, assicurati che i percorsi alle directory fisiche conducano ad Adobe Campaign v7 e non ad Adobe Campaign v5.

1. Poiché la migrazione non è un&#39;installazione generica, è necessario forzare il riavvio del servizio **trackinglogd**. A questo scopo, apri il file **nl6/conf/config-default.xml** e assicurati che il servizio **trackinglogd** sia attivato (solo sui server di tracciamento/reindirizzamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se il servizio **trackinglogd** non viene avviato sul server di tracciamento, non verranno inoltrate informazioni di tracciamento.

1. Ricarica la configurazione Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avvia il processo di post-aggiornamento utilizzando il seguente comando (ancora come **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >È necessario specificare quale fuso orario utilizzare come riferimento durante l&#39;aggiornamento successivo (utilizzando l&#39;opzione **-timezone** ). In questo caso, utilizziamo il fuso orario Europa/Parigi **-timezone: &quot;Europa/Parigi&quot;**.

   >[!NOTE]
   >
   >Consigliamo vivamente di aggiornare la base a &quot;multi-timezone&quot;. Per ulteriori informazioni sulle opzioni relative al fuso orario, consulta la sezione [Fusi orari](../../migration/using/general-configurations.md#time-zones) .

>[!IMPORTANT]
>
>Non avviare ancora i servizi Adobe Campaign: ad Apache devono ancora essere apportate modifiche.

### Migrazione da Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

La distribuzione di Adobe Campaign prevede due fasi:

* Installazione dei pacchetti Adobe Campaign v7: questa operazione deve essere eseguita su ciascun server.
* L&#39;aggiornamento post: questo comando deve essere avviato su ogni istanza.

Per distribuire Adobe Campaign, esegui i seguenti passaggi:

1. Installa i pacchetti Adobe Campaign v7 più recenti utilizzando il seguente comando:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >È necessario installare correttamente i pacchetti prima di passare al passaggio successivo.

   >[!NOTE]
   >
   >Adobe Campaign v7 è installato nella stessa directory per impostazione predefinita di Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Per rendere disponibile il programma di installazione della console client, copialo nella directory di installazione di Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Per ulteriori informazioni su come installare Adobe Campaign in Linux, consulta [questa sezione](../../installation/using/installing-campaign-standard-packages.md).

1. Poiché la migrazione non è un&#39;installazione generica, è necessario forzare il riavvio del servizio **trackinglogd**. A questo scopo, apri il file **nl6/conf/config-default.xml** e assicurati che il servizio **trackinglogd** sia attivato (solo sui server di tracciamento/reindirizzamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se il servizio **trackinglogd** non viene avviato sul server di tracciamento, non verranno inoltrate informazioni di tracciamento.

1. Vai alla cartella di backup **nl6.back** e copia (sovrascrive) i file di configurazione e le sottocartelle di ogni istanza. Accedi come **neolane** ed esegui il seguente comando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Ricarica la configurazione Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avvia il processo di post-aggiornamento utilizzando il seguente comando (ancora come **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >La modalità &quot;multi timezone&quot; era disponibile solo nella versione 6.02 per i motori di database PostgreSQL. È ora disponibile indipendentemente dalla versione del motore di database in uso. Consigliamo vivamente di aggiornare la base a &quot;multi-timezone&quot;. Per ulteriori informazioni sulle opzioni relative al fuso orario, consulta la sezione [Fusi orari](../../migration/using/general-configurations.md#time-zones) .

### Migrazione da Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

La distribuzione di Adobe Campaign prevede due fasi:

* Installazione dei pacchetti Adobe Campaign v7: questa operazione deve essere eseguita su ciascun server.
* L&#39;aggiornamento post: questo comando deve essere avviato su ogni istanza.

Per distribuire Adobe Campaign, esegui i seguenti passaggi:

1. Installa i pacchetti Adobe Campaign v7 più recenti utilizzando il seguente comando:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >È necessario installare correttamente i pacchetti prima di passare al passaggio successivo.

   >[!NOTE]
   >
   >Per impostazione predefinita, Adobe Campaign v7 è installato nella directory **/usr/local/neolane/nl6/** .

1. Per rendere disponibile il programma di installazione della console client, copialo nella directory di installazione di Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Per ulteriori informazioni su come installare Adobe Campaign in Linux, consulta [questa sezione](../../installation/using/installing-campaign-standard-packages.md).

1. Vai alla cartella di backup **nl6.back** e copia (sovrascrive) i file di configurazione e le sottocartelle di ogni istanza. Accedi come **neolane** ed esegui il seguente comando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Ricarica la configurazione Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avvia il processo di post-aggiornamento utilizzando il seguente comando (ancora come **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migrazione del server di reindirizzamento (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Questa sezione si applica solo durante la migrazione da Adobe Campaign v5.11.

A questo punto, Apache deve essere arrestato. Fai riferimento a: [Arresto del servizio](#service-stop).

1. Accedi come **root**.
1. Modifica le variabili di ambiente Apache per farle collegare alla directory **nl6** .

   * In **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * In **Red Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Esegui quindi i seguenti comandi:

   * In **Debian**:

      Nel file **nlsrv.load** sostituisci **nl5** con **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Elimina il collegamento del file **nlsrv.conf** e creane uno nuovo.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * In **Red Hat**:

      Vai alla directory **/usr/local/apache2/conf**, modifica il file **http.conf** e sostituisci **nl5** con **nl6** nelle seguenti righe.

      In **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Vai al file **alias.conf** e sostituisci tutti i **nl5** con **nl6**. Per eseguire questa operazione in Debian, esegui il seguente comando:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zone di sicurezza {#security-zones}

Se stai eseguendo la migrazione dalla versione v6.02 o precedente, devi configurare le aree di protezione prima di avviare i servizi. Per ulteriori informazioni, consulta [Sicurezza](../../migration/using/general-configurations.md#security).

## Riavvio dei servizi {#re-starting-services}

La procedura dipende dalla versione precedente di Adobe Campaign.

### Migrazione da Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

Nei file **config-`<instance name>`.xml**, riattiva l&#39;avvio automatico del **mta**, **wfserver**, **stat**, ecc. servizi.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Avvia i servizi Apache e Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Prima di passare al passaggio successivo, esegui un test completo della nuova installazione, assicurati che non vi siano regressioni e che tutto funzioni seguendo tutte le raccomandazioni nella sezione [Configurazioni generali](../../migration/using/general-configurations.md) .

### Migrazione da Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

Nei file **config-`<instance name>`.xml**, riattiva l&#39;avvio automatico del **mta**, **wfserver**, **stat**, ecc. servizi.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Avvia i servizi Apache e Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Verifica completamente la nuova installazione, verifica che non regredisca e assicurati che tutto funzioni correttamente seguendo tutte le raccomandazioni nella sezione [Configurazioni generali](../../migration/using/general-configurations.md) .

### Migrazione da Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Avvia i servizi Apache e Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Verifica completamente la nuova installazione, verifica che non regredisca e assicurati che tutto funzioni correttamente seguendo tutte le raccomandazioni nella sezione [Configurazioni generali](../../migration/using/general-configurations.md) .

## Eliminazione e pulizia di Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Questa sezione si applica solo durante la migrazione da Adobe Campaign v5.11.

Prima di eliminare e pulire l’installazione di Adobe Campaign v5, è necessario applicare le seguenti raccomandazioni:

* Chiedi ai team funzionali di eseguire un controllo completo della nuova installazione.
* Disinstalla Adobe Campaign v5 solo una volta che sei sicuro che non è necessario eseguire il rollback.

Elimina la directory **nl5.back** . Accedi come **neolane** ed esegui il seguente comando:

```
su - neolane
rm -rf nl5.back
```

Riavvia il server.
