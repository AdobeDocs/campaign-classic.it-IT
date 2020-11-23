---
solution: Campaign Classic
product: campaign
title: Migrazione in Linux per Adobe Campaign v7
description: Migrazione in Linux per Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---


# Migrazione in Linux per Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## Procedura generale {#general-procedure}

Le fasi di migrazione in Linux sono le seguenti:

1. Arresta servizi: vedete [Interruzione](#service-stop)del servizio.
1. Salvate il database: vedete [Eseguire il backup del database e dell&#39;installazione](#back-up-the-database-and-the-existing-installation)esistente.
1. Disinstallare i pacchetti  versione Adobe Campaign precedenti: consultate [Disinstallazione  pacchetti](#uninstalling-adobe-campaign-previous-version-packages)di versioni precedenti di Adobe Campaign.
1. Migra la piattaforma: fate riferimento a [Distribuzione  Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Riavvia il servizio: fare riferimento ai servizi [di](#re-starting-services)riavvio.

## Interruzione del servizio {#service-stop}

In primo luogo, arrestate tutti i processi con accesso al database su tutti i computer interessati.

1. Accedete come **root**.
1. Tutti i server che utilizzano il modulo di reindirizzamento (servizio **webmdl** ) devono essere interrotti. Per Apache, eseguite il comando seguente:

   ```
   /etc/init.d/apache2 stop
   ```

1. Accedete di nuovo come **root**.
1. Arrestate  servizi della versione precedente di Adobe Campaign su tutti i server.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Se state effettuando la migrazione dalla v5.11, eseguite il comando seguente:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Verificate che  servizi Adobe Campaign siano interrotti su ciascun server.

   ```
   ps waux | grep nlserver
   ```

   L&#39;elenco dei processi attivi viene visualizzato insieme al relativo ID (PID).

1. Se uno o più processi Adobe Campaign  sono ancora attivi o bloccati dopo qualche minuto, eliminarli.

   ```
   killall nlserver
   ```

1. Se alcuni processi sono ancora attivi dopo alcuni minuti, è possibile forzarli a chiudersi utilizzando il comando:

   ```
   killall -9 nlserver
   ```

## Eseguire il backup del database e dell&#39;installazione esistente {#back-up-the-database-and-the-existing-installation}

La procedura dipende dalla versione precedente  Adobe Campaign.

### Migrazione da  Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Eseguire un backup del database Adobe Campaign .
1. Accedete come **neolane** ed effettuate un backup della directory **nl5** utilizzando il seguente comando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Come precauzione, consigliamo di comprimere la cartella **nl5.back** e salvarla in un percorso protetto diverso dal server.

1. Modificate il file **config-`<instance name>`.xml** (nella cartella **nl5.back** ), per impedire che **mta**, **wfserver**, **** stat, ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituire **autoStart** con **_autoStart** (ancora come **neolane**).

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

### Migrazione da  Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Eseguire un backup del database Adobe Campaign .
1. Effettuate l&#39;accesso come **neolane** ed effettuate un backup della directory **nl6** utilizzando il seguente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Come precauzione, consigliamo di comprimere la cartella **nl6.back** e salvarla in un percorso protetto diverso dal server.

1. Modificate il file **config-`<instance name>`.xml** (nella cartella **nl6.back** ) per impedire che **mta**, **wfserver**, **** stat, ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituire **autoStart** con **_autoStart** ( **Adobe Campaign**).

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

### Migrazione da  Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Eseguire un backup del database Adobe Campaign .
1. Effettuate l&#39;accesso come **neolane** ed effettuate un backup della directory **nl6** utilizzando il seguente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Come precauzione, consigliamo di comprimere la cartella **nl6.back** e salvarla in un percorso protetto diverso dal server.

## Disinstallazione  pacchetti di versioni precedenti di Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

La procedura dipende dalla versione precedente  Adobe Campaign.

### Disinstallazione  pacchetti Adobe Campaign v5 {#uninstalling-adobe-campaign-v5-packages}

1. Accedete come **root**.
1. Identificare i pacchetti Adobe Campaign  installati utilizzando il seguente comando.

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

1. Disinstallare  pacchetti Adobe Campaign v5.

   * In **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Disinstallazione  pacchetti Adobe Campaign v6 {#uninstalling-adobe-campaign-v6-packages}

In questa sezione viene illustrato come disinstallare  pacchetti Adobe Campaign v6.02 o v6.1.

1. Accedete come **root**.
1. Identificare i pacchetti Adobe Campaign  installati utilizzando il seguente comando.

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

1. Disinstallare  pacchetti Adobe Campaign v6.

   * In **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Implementazione  Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La procedura dipende dalla versione precedente  Adobe Campaign.

### Migrazione da  Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

La distribuzione  Adobe Campaign prevede due fasi:

* Installazione  pacchetti Adobe Campaign v7: questa operazione deve essere eseguita su ogni server.
* Post upgrade: questo comando deve essere avviato su ogni istanza.

Per distribuire  Adobe Campaign, eseguite i seguenti passaggi:

1. Installate i pacchetti Adobe Campaign v7  più recenti utilizzando il seguente comando:

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
   >Durante la migrazione dalla v5.11,  Adobe Campaign è installato nella directory **/usr/local/neolane/nl6/** per impostazione predefinita.
   >
   >Una volta installati i pacchetti, viene visualizzato il seguente messaggio: **Opzione &#39;WdbcTimeZone&#39; mancante**. Questo è normale.

1. Per rendere disponibile il programma di installazione della console client, copiatelo nella directory di installazione  Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Per ulteriori informazioni su come installare  Adobe Campaign in Linux, consulta [questa sezione](../../installation/using/installing-campaign-standard-packages.md).

1. Modificate il file **.bashrd** che corrisponde all&#39;utente **neolane** . Accedete come **neolano** ed eseguite il comando seguente:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Quando effettuate l’accesso come **neolane**, viene visualizzato il seguente messaggio: **nl5/env.sh: File o directory** non corrispondenti. Questo è normale.

   Alla fine del file, sostituite **nl5/env.sh** con **nl6/env.sh**.

1. Accedete come **root** e preparate l&#39;istanza utilizzando i seguenti comandi:

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
   >Questi comandi consentono di creare  sistema di file interni Adobe Campaign v6: **directory conf** (con i file **config-default.xml** e **serverConf.xml** ), directory **var** .

1. Passate alla cartella di backup **nl5.back** e copiate (sovrascrivete) i file di configurazione e le sottocartelle di ogni istanza. Accedete come **neolano** ed eseguite il comando seguente:

   >[!IMPORTANT]
   >
   >Per il primo comando di seguito, non copiate il file **config-default.xml** .

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Nei  file Adobe Campaign v7 **serverConf.xml** e **config-default.xml** , applicate le configurazioni specifiche per  Adobe Campaign v5. Per il file **serverConf.xml** , usate il file **nl5/conf/serverConf.xml.diff** .

   >[!NOTE]
   >
   >Quando generate i rapporti delle configurazioni da  Adobe Campaign v5 a  Adobe Campaign v7, accertatevi che i percorsi delle directory fisiche portino  Adobe Campaign v7 e non  Adobe Campaign v5.

1. Poiché la migrazione non è un&#39;installazione generica, è necessario forzare il riavvio del servizio di **tracciamento** . A questo scopo, aprite il file **nl6/conf/config-default.xml** e accertatevi che il servizio **trackogd** sia attivato (solo sui server di tracciamento/reindirizzamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se il servizio **trackogd** non viene avviato sul server di tracciamento, non verranno inoltrate informazioni di tracciamento.

1. Ricaricate la configurazione  Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avviare il processo di post-aggiornamento utilizzando il seguente comando (ancora come **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >È necessario specificare quale fuso orario utilizzare come riferimento durante l&#39;aggiornamento successivo (utilizzando l&#39;opzione **-timezone** ). In questo caso, utilizziamo il **fuso orario Europa/Parigi: &quot;Europa/Parigi&quot;**.

   >[!NOTE]
   >
   >Consigliamo vivamente di aggiornare la base a &quot;multi timezone&quot;. Per ulteriori informazioni sulle opzioni relative al fuso orario, consultate la sezione Fusi [orari](../../migration/using/general-configurations.md#time-zones) .

>[!IMPORTANT]
>
>Non avviare  servizi Adobe Campaign: le modifiche devono ancora essere apportate ad Apache.

### Migrazione da  Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

La distribuzione  Adobe Campaign prevede due fasi:

* Installazione  pacchetti Adobe Campaign v7: questa operazione deve essere eseguita su ogni server.
* Post upgrade: questo comando deve essere avviato su ogni istanza.

Per distribuire  Adobe Campaign, eseguite i seguenti passaggi:

1. Installate i pacchetti Adobe Campaign v7  più recenti utilizzando il seguente comando:

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
   > Adobe Campaign v7 è installato nella stessa directory per impostazione predefinita  Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Per rendere disponibile il programma di installazione della console client, copiatelo nella directory di installazione  Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Per ulteriori informazioni su come installare  Adobe Campaign in Linux, consulta [questa sezione](../../installation/using/installing-campaign-standard-packages.md).

1. Poiché la migrazione non è un&#39;installazione generica, è necessario forzare il riavvio del servizio di **tracciamento** . A questo scopo, aprite il file **nl6/conf/config-default.xml** e accertatevi che il servizio **trackogd** sia attivato (solo sui server di tracciamento/reindirizzamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se il servizio **trackogd** non viene avviato sul server di tracciamento, non verranno inoltrate informazioni di tracciamento.

1. Passate alla cartella di backup **nl6.back** e copiate (sovrascrivete) i file di configurazione e le sottocartelle di ogni istanza. Accedete come **neolano** ed eseguite il comando seguente:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Ricaricate la configurazione  Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avviare il processo di post-aggiornamento utilizzando il seguente comando (ancora come **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >La modalità &quot;multi timezone&quot; era disponibile solo in v6.02 per i motori di database PostSQL. Ora è disponibile indipendentemente dalla versione del motore di database in uso. Consigliamo vivamente di aggiornare la base a &quot;multi timezone&quot;. Per ulteriori informazioni sulle opzioni relative al fuso orario, consultate la sezione Fusi [orari](../../migration/using/general-configurations.md#time-zones) .

### Migrazione da  Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

La distribuzione  Adobe Campaign prevede due fasi:

* Installazione  pacchetti Adobe Campaign v7: questa operazione deve essere eseguita su ogni server.
* Post upgrade: questo comando deve essere avviato su ogni istanza.

Per distribuire  Adobe Campaign, eseguite i seguenti passaggi:

1. Installate i pacchetti Adobe Campaign v7  più recenti utilizzando il seguente comando:

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
   > Adobe Campaign v7 è installato nella directory **/usr/local/neolane/nl6/** per impostazione predefinita.

1. Per rendere disponibile il programma di installazione della console client, copiatelo nella directory di installazione  Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Per ulteriori informazioni su come installare  Adobe Campaign in Linux, consulta [questa sezione](../../installation/using/installing-campaign-standard-packages.md).

1. Passate alla cartella di backup **nl6.back** e copiate (sovrascrivete) i file di configurazione e le sottocartelle di ogni istanza. Accedete come **neolano** ed eseguite il comando seguente:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Ricaricate la configurazione  Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avviare il processo di post-aggiornamento utilizzando il seguente comando (ancora come **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migrazione del server di reindirizzamento (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Questa sezione è valida solo per la migrazione da  Adobe Campaign v5.11.

A questo punto, Apache deve essere fermato. Consultare: [Arresto](#service-stop)del servizio.

1. Accedete come **root**.
1. Modificate le variabili d&#39;ambiente Apache in modo che rimangano collegate alla directory **nl6** .

   * In **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * In **Red Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Quindi eseguite i seguenti comandi:

   * In **Debian**:

      Nel file **nlsrv.load** , sostituite **nl5** con **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Eliminate il collegamento del file **nlsrv.conf** e createne uno nuovo.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * In **Red Hat**:

      Andate alla directory **/usr/local/apache2/conf** , modificate il file **http.conf** e sostituite **nl5** con **nl6** nelle seguenti righe.

      In **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Andate al file **alias.conf** e sostituite tutti **nl5** con **nl6**. Per eseguire questa operazione in Debian, eseguite il comando seguente:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zone di protezione {#security-zones}

Se state eseguendo la migrazione dalla versione 6.02 o precedente, dovete configurare le aree di protezione prima di avviare i servizi. Per ulteriori informazioni, vedere [Sicurezza](../../migration/using/general-configurations.md#security).

## Riavvio dei servizi {#re-starting-services}

La procedura dipende dalla versione precedente  Adobe Campaign.

### Migrazione da  Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

Nei file **config-`<instance name>`.xml** , riattivate l&#39;avvio automatico di **mta**, **wfserver**, **stat**, ecc. servizi.

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

Avviate i servizi Apache e  Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Prima di passare al passaggio successivo, eseguite un test completo della nuova installazione, accertatevi che non ci siano regressioni e che tutto funzioni seguendo tutte le raccomandazioni nella sezione [Configurazioni](../../migration/using/general-configurations.md) generali.

### Migrazione da  Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

Nei file **config-`<instance name>`.xml** , riattivate l&#39;avvio automatico di **mta**, **wfserver**, **stat**, ecc. servizi.

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

Avviate i servizi Apache e  Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Verificate completamente la nuova installazione, verificate che non si regredisca e assicuratevi che tutto funzioni correttamente seguendo tutte le raccomandazioni della sezione [Configurazioni](../../migration/using/general-configurations.md) generali.

### Migrazione da  Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Avviate i servizi Apache e  Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Verificate completamente la nuova installazione, verificate che non si regredisca e assicuratevi che tutto funzioni correttamente seguendo tutte le raccomandazioni della sezione [Configurazioni](../../migration/using/general-configurations.md) generali.

## Eliminazione e pulizia  Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Questa sezione è valida solo per la migrazione da  Adobe Campaign v5.11.

Prima di eliminare e cancellare l&#39;installazione  Adobe Campaign v5, è necessario applicare le seguenti raccomandazioni:

* Fate in modo che i team operativi eseguano un controllo completo della nuova installazione.
* Disinstallate  Adobe Campaign v5 solo dopo aver verificato che non è necessario eseguire il rollback.

Eliminate la directory **nl5.back** . Accedete come **neolano** ed eseguite il comando seguente:

```
su - neolane
rm -rf nl5.back
```

Riavviate il server.
