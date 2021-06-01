---
product: campaign
title: Migrazione in Windows per Adobe Campaign 7
description: Migrazione in Windows per Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 1%

---

# Migrazione in Windows per Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## Procedura generale {#general-procedure}

Per Windows, i passaggi di migrazione sono i seguenti:

1. Servizi di arresto: fare riferimento a [Arresto del servizio](#service-stop).
1. Eseguire il backup del database: fare riferimento a [Eseguire il backup del database e dell&#39;installazione corrente](#back-up-the-database-and-the-current-installation).
1. Esegui la migrazione della piattaforma: fai riferimento a [Distribuzione di Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Esegui la migrazione del server di reindirizzamento (IIS): fare riferimento a [Migrazione del server di reindirizzamento (IIS)](#migrating-the-redirection-server--iis-).
1. Servizio di riavvio: fare riferimento a [Riavvio dei servizi](#re-starting-the-services).
1. Elimina e cancella la versione precedente di Adobe Campaign: fare riferimento a [Eliminazione e pulizia della versione precedente di Adobe Campaign](#deleting-and-cleansing-adobe-campaign-previous-version).

## Arresto del servizio {#service-stop}

In primo luogo, interrompere tutti i processi con accesso al database su tutti i computer interessati.

1. Tutti i server che utilizzano il modulo di reindirizzamento (**webmdl** servizio) devono essere arrestati. Per IIS, esegui il seguente comando:

   ```
   iisreset /stop
   ```

1. Il modulo **mta** e i relativi moduli figlio (**mtachild**) devono essere interrotti utilizzando i seguenti comandi:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Arresta i servizi Adobe Campaign su tutti i server. Accedi con i diritti di amministratore ed esegui il seguente comando:

   ```
   net stop nlserver6
   ```

   Se stai eseguendo la migrazione dalla versione v5.11, esegui il seguente comando:

   ```
   net stop nlserver5
   ```

1. Per ogni server, assicurati che i servizi Adobe Campaign siano correttamente arrestati. Accedi con i diritti di amministratore ed esegui il seguente comando:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   Viene visualizzato l’elenco dei processi attivi con il relativo ID (PID).

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Se uno o più processi Adobe Campaign sono ancora attivi o bloccati dopo qualche minuto, eliminali. Accedi con i diritti di amministratore ed esegui il seguente comando:

   ```
   taskkill /IM nlserver* /T
   ```

1. Se alcuni processi sono ancora attivi dopo alcuni minuti, puoi forzarli a chiuderli utilizzando il comando :

   ```
   taskkill /F /IM nlserver* /T
   ```

## Eseguire il backup del database e dell&#39;installazione corrente {#back-up-the-database-and-the-current-installation}

La procedura dipende dalla versione precedente di Adobe Campaign.

### Migrazione da Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Esegui un backup del database Adobe Campaign.
1. Esegui un backup della directory **Neolane v5** utilizzando il seguente comando:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >Per precauzione, ti consigliamo di comprimere la cartella **Neolane v5.back** e salvarla altrove in un percorso sicuro diverso dal server.

1. Nella console di gestione dei servizi Windows, disattivare l&#39;avvio automatico del servizio server applicazioni 5.11. È inoltre possibile utilizzare il comando seguente:

   ```
   sc config nlserver5 start= disabled
   ```

1. Modifica il **config-`<instance name>`.xml** (nel **Neolane v5. indietro**) per impedire che **mta**, **wfserver**, **stat**, ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituisci **autoStart** con **_autoStart**.

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
1. Esegui un backup della directory **Neolane v6** utilizzando il seguente comando:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >Per precauzione, ti consigliamo di comprimere la cartella **Neolane v6.back** e salvarla altrove in un percorso sicuro diverso dal server.

1. In Gestione servizi Windows, disattivare l&#39;avvio automatico del server applicazioni 6.02. È inoltre possibile utilizzare il comando seguente:

   ```
   sc config nlserver6 start= disabled
   ```

1. Modifica il **config-`<instance name>`.xml** (nel **Neolane v6. indietro**) per impedire che **mta**, **wfserver**, **stat**, ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituisci **autoStart** con **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
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
1. Esegui un backup della directory **Adobe Campaign v6** utilizzando il seguente comando:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Per precauzione, ti consigliamo di comprimere la cartella **Adobe Campaign v6.back** e salvarla altrove in un percorso sicuro diverso dal server.

1. Nella console di gestione dei servizi Windows, disattiva l&#39;avvio automatico del servizio server applicazioni 6.11. È inoltre possibile utilizzare il comando seguente:

   ```
   sc config nlserver6 start= disabled
   ```

## Distribuzione di Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La distribuzione di Adobe Campaign prevede due fasi:

* Installazione della build v7: questa operazione deve essere eseguita su ciascun server.
* L&#39;aggiornamento post: questo comando deve essere avviato su ogni istanza.

Per distribuire Adobe Campaign, esegui i seguenti passaggi:

1. Installa la build Adobe Campaign v7 più recente eseguendo il file di installazione **setup.exe** . Per ulteriori informazioni sull&#39;installazione del server Adobe Campaign in Windows, consulta [questa sezione](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7 è installato per impostazione predefinita nella directory **C:\Program Files\Adobe\Adobe Campaign v7** .

1. Per rendere disponibile il programma di installazione della console client, copia il file **setup-client-7.0.XXXX.exe** nella directory di installazione di Adobe Campaign: **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Per ulteriori informazioni sull&#39;installazione di Adobe Campaign in Windows, consulta [questa sezione](../../installation/using/installing-the-server.md).

1. Avvia l&#39;istanza per il primo utilizzo con i seguenti comandi:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Questi comandi consentono di creare il file system interno Adobe Campaign v7: Directory **conf** (con la directory **config-default.xml** e i file **serverConf.xml**), **var**, ecc.

1. Copia e incolla (sovrascrivi) i file di configurazione e le sottocartelle di ogni istanza tramite il file di backup **Neolane v5.back**, **Neolane v6.back** o **Adobe Campaign v6.back** (a seconda della versione da cui stai eseguendo la migrazione - consulta [questa sezione](#back-up-the-database-and-the-current-installation)).
1. A seconda della versione da cui stai eseguendo la migrazione, esegui i seguenti comandi:

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >Per il primo comando di cui sopra, non copiare il file **config-default.xml**.

1. Nei file **serverConf.xml** e **config-default.xml** di Adobe Campaign v7, applica le configurazioni specifiche presenti nella versione precedente di Adobe Campaign. Per il file **serverConf.xml**, utilizza il file **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** o **Adobe Campaign v6/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Quando esegui il reporting delle configurazioni dalla versione precedente di Adobe Campaign ad Adobe Campaign v7, assicurati che i percorsi alle directory fisiche conducano ad Adobe Campaign v7 (e non a Neolane v5, Neolane v6 o Adobe Campaign v6).

1. Ricarica la configurazione Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avvia il processo di post-aggiornamento utilizzando il seguente comando:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>Non avviare ancora i servizi Adobe Campaign: è necessario apportare alcune modifiche a IIS.

## Migrazione del server di reindirizzamento (IIS) {#migrating-the-redirection-server--iis-}

In questa fase, il server IIS deve essere arrestato. Fare riferimento a [Arresto del servizio](#service-stop).

1. Apri la console **Internet Information Services (IIS) Manager** .
1. Modifica i binding (porte di ascolto) del sito utilizzato per la versione precedente di Adobe Campaign:

   * Fai clic con il pulsante destro del mouse sul sito utilizzato per la versione precedente di Adobe Campaign e seleziona **[!UICONTROL Edit bindings]**.
   * Per ogni tipo di porta di ascolto (**[!UICONTROL http]** e/o **[!UICONTROL https]**), seleziona la riga appropriata e fai clic su **[!UICONTROL Edit]**.
   * Immettere una porta diversa. Per impostazione predefinita, la porta di ascolto è 80 per http e 443 per https. Verifica che la nuova porta sia disponibile.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >Se il server IIS include diversi siti web per Adobe Campaign con una configurazione avanzata (porta condivisa e indirizzi IP diversi), contatta l’amministratore.

1. Crea un nuovo sito web per Adobe Campaign v7:

   * Fai clic con il pulsante destro del mouse sulla cartella **[!UICONTROL Sites]** e seleziona **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * Immetti il nome del sito, ad esempio **Adobe Campaign v7**.
   * Il percorso di accesso alla directory di base del sito web non viene utilizzato, ma il campo **[!UICONTROL Physical access path]** deve essere inserito. Immettere il percorso di accesso predefinito di IIS: **C:\inetpub\wwwroot**.
   * Fai clic sul pulsante **[!UICONTROL Connect as...]** come e accertati che l&#39;opzione **[!UICONTROL Application user]** sia selezionata.
   * È possibile lasciare i valori predefiniti nei campi **[!UICONTROL IP address]** e **[!UICONTROL Port]** . Se desideri utilizzare altri valori, assicurati che l’indirizzo IP e/o la porta siano disponibili.
   * Seleziona la casella **[!UICONTROL Start Web site immediately]** .

      ![](assets/_migration_iis_5_7.png)

1. Esegui lo script **iis_neolane_setup.vbs** per configurare automaticamente le risorse utilizzate dal server Adobe Campaign nella directory virtuale creata in precedenza.

   * Questo file si trova nella directory **`[Adobe Campaign v7]`\conf**, dove **`[Adobe Campaign v7]`** è il percorso di accesso alla directory di installazione di Adobe Campaign. Il comando per l&#39;esecuzione dello script è il seguente (per gli amministratori):

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * Fai clic su **[!UICONTROL OK]** per confermare l’esecuzione dello script.

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Immetti il numero del sito web creato in precedenza per Adobe Campaign v7 e fai clic su **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Viene visualizzato un messaggio di conferma:

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * Nella scheda **[!UICONTROL Content view]** , accertati che la configurazione del sito web sia configurata correttamente con le risorse Adobe Campaign:

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >Se la struttura ad albero non viene visualizzata, riavviare IIS.
      >
      >I seguenti passaggi di configurazione di IIS sono descritti in [questa sezione](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

## Zone di sicurezza {#security-zones}

Se stai eseguendo la migrazione dalla versione v6.02 o precedente, devi configurare le aree di protezione prima di avviare i servizi. Per ulteriori informazioni, consulta [Sicurezza](../../migration/using/general-configurations.md#security).

## Riavvio dei servizi {#re-starting-the-services}

Avvia i servizi IIS e Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Prima di passare al passaggio successivo, esegui un test completo della nuova installazione, assicurati che non vi siano regressioni e che tutto funzioni seguendo tutte le raccomandazioni nella sezione [Configurazioni generali](../../migration/using/general-configurations.md) .

## Eliminazione e pulizia della versione precedente di Adobe Campaign {#deleting-and-cleansing-adobe-campaign-previous-version}

La procedura dipende dalla versione precedente di Adobe Campaign.

### Adobe Campaign v5 {#adobe-campaign-v5}

Prima di eliminare e pulire l’installazione di Adobe Campaign v5, è necessario applicare le seguenti raccomandazioni:

* Chiedi ai team funzionali di eseguire un controllo completo della nuova installazione.
* Disinstalla Adobe Campaign v5 solo una volta che sei sicuro che non è necessario eseguire il rollback.

1. In IIS, elimina il sito Web **Neolane v5** e quindi il pool di applicazioni **Neolane v5**.
1. Rinomina la cartella **Neolane v5.back** come **Neolane v5**.
1. Disinstalla Adobe Campaign v5 utilizzando la procedura guidata Aggiungi/rimuovi componenti .

   ![](assets/migration_wizard_2.png)

1. Elimina il servizio **nlserver5** Windows utilizzando il seguente comando:

   ```
   sc delete nlserver5
   ```

1. Riavvia il server.

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Prima di eliminare e pulire l’installazione di Adobe Campaign v6.02, è necessario applicare le seguenti raccomandazioni:

* Chiedi ai team funzionali di eseguire un controllo completo della nuova installazione.
* Disinstalla Adobe Campaign v6.02 solo se sei sicuro che non è necessario eseguire il rollback.

1. In IIS, elimina il sito Web **Neolane v6** e quindi il pool di applicazioni **Neolane v6**.
1. Rinomina la cartella **Neolane v6.back** come **Neolane v6**.
1. Disinstalla Adobe Campaign v6.02 utilizzando la procedura guidata Aggiungi/rimuovi componenti .

   ![](assets/migration_wizard_2.png)

1. Riavvia il server.

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

Prima di eliminare e pulire l’installazione di Adobe Campaign v6, è necessario applicare le seguenti raccomandazioni:

* Chiedi ai team funzionali di eseguire un controllo completo della nuova installazione.
* Disinstalla Adobe Campaign v6 solo una volta che sei sicuro che non è necessario eseguire il rollback.

1. In IIS, elimina il sito web **Adobe Campaign v6** e quindi il pool di applicazioni **Adobe Campaign v6**.
1. Rinomina la cartella **Adobe Campaign v6.back** come **Adobe Campaign v6**.
1. Disinstallare Adobe Campaign v6 utilizzando la procedura guidata Aggiungi/rimuovi componenti .

   ![](assets/migration_wizard_2.png)

1. Riavvia il server.
