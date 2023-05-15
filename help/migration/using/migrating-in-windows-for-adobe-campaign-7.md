---
product: campaign
title: Migrazione di una piattaforma Microsoft Windows ad Adobe Campaign v7
description: Scopri come migrare una piattaforma Microsoft Windows ad Adobe Campaign v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
hide: true
hidefromtoc: true
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# Migrazione di una piattaforma Microsoft Windows a Campaign v7{#migrating-in-windows-for-adobe-campaign}



Per un ambiente Microsoft Windows, i passaggi di migrazione sono i seguenti:

1. Arresta tutti i servizi - [Ulteriori informazioni](#service-stop).
1. Esegui il backup del database - [Ulteriori informazioni](#back-up-the-database).
1. Migrare la piattaforma - [Ulteriori informazioni](#deploying-adobe-campaign-v7).
1. Migrare il server di reindirizzamento (IIS) - [Ulteriori informazioni](#migrating-the-redirection-server--iis-).
1. Servizio di riavvio - [Ulteriori informazioni](#re-starting-the-services).
1. Elimina e pulisci la versione precedente di Adobe Campaign - [Ulteriori informazioni](#deleting-and-cleansing-adobe-campaign-previous-version).

## Interruzione del servizio {#service-stop}

In primo luogo, interrompere tutti i processi con accesso al database su tutti i computer interessati.

1. Tutti i server che utilizzano il modulo di reindirizzamento (**webmdl** servizio) deve essere arrestato. Per IIS, esegui il seguente comando:

   ```
   iisreset /stop
   ```

1. La **mta** modulo e relativi moduli figlio (**madre**) deve essere arrestato utilizzando i seguenti comandi:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Arresta i servizi Adobe Campaign su tutti i server. Accedi con i diritti di amministratore ed esegui il seguente comando:

   ```
   net stop nlserver6
   ```

<!--

   If you are migrating from v5.11, run the following command:

   ```
   net stop nlserver5
   ```

-->

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

## Esegui il backup del database Campaign {#back-up-the-database}

Questa è la procedura per il backup di Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v5** directory using the following command:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v5.back** folder and save it elsewhere in a safe location other than the server.

1. In the windows service management console, disable the automatic startup of the 5.11 application server service. You can also use the following command:

   ```
   sc config nlserver5 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v5. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

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

-->

<!--
### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v6** directory using the following command:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v6.back** folder and save it elsewhere in a safe location other than the server.

1. In the Windows service manager, deactivate the 6.02 application server automatic startup. You can also use the following command:

   ```
   sc config nlserver6 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v6. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

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

-->

1. Esegui un backup del database Adobe Campaign.
1. Esegui un backup del **Adobe Campaign v6** utilizzando il seguente comando:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Per precauzione, ti consigliamo di comprimere la **Adobe Campaign v6.back** e salvarlo altrove in un percorso sicuro diverso dal server.

1. Nella console di gestione dei servizi Windows, disattiva l&#39;avvio automatico del servizio server applicazioni 6.11. È inoltre possibile utilizzare il comando seguente:

   ```
   sc config nlserver6 start= disabled
   ```

## Distribuzione di Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La distribuzione di Adobe Campaign prevede due fasi:

* Installazione della build v7: questa operazione deve essere eseguita su ciascun server.
* L&#39;aggiornamento post: questo comando deve essere avviato su ogni istanza.

Per distribuire Adobe Campaign, esegui i seguenti passaggi:

1. Installa la build Adobe Campaign v7 più recente eseguendo il **setup.exe** file di installazione. Per ulteriori informazioni sull&#39;installazione del server Adobe Campaign in Windows, consulta [questa sezione](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7 è installato per impostazione predefinita nel **C:\Program Files\Adobe\Adobe Campaign v7** directory.

1. Per rendere disponibile il programma di installazione della console client, copia il **setup-client-7.0.XXXX.exe** nella directory di installazione di Adobe Campaign: **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Per ulteriori informazioni sull’installazione di Adobe Campaign in Windows, consulta [questa sezione](../../installation/using/installing-the-server.md).

1. Avvia l&#39;istanza per il primo utilizzo con i seguenti comandi:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Questi comandi consentono di creare il file system interno Adobe Campaign v7: **conf** (con **config-default.xml** e **serverConf.xml** file), **var** directory, ecc.

1. Copia e incolla (sovrascrivi) i file di configurazione e le sottocartelle di ogni istanza tramite il **Neolane v5.back**, **Neolane v6.back** o **Adobe Campaign v6.back** file di backup (a seconda della versione da cui stai eseguendo la migrazione - vedi [questa sezione](#back-up-the-database-and-the-current-installation)).
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
   >Per il primo comando di cui sopra, non copiare il **config-default.xml** file.

1. In **serverConf.xml** e **config-default.xml** file di Adobe Campaign v7, applica le configurazioni specifiche che avevi nella versione precedente di Adobe Campaign. Per **serverConf.xml** file, utilizza **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** o **Adobe Campaign v6/conf/serverConf.xml.diff** file.

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

## Migrazione del server di reindirizzamento {#migrating-the-redirection-server--iis-}

In questa fase, il server IIS deve essere arrestato. Fai riferimento a [Interruzione del servizio](#service-stop).

1. Apri **Gestione Internet Information Services (IIS)** console.
1. Modifica i binding (porte di ascolto) del sito utilizzato per la versione precedente di Adobe Campaign:

   * Fai clic con il pulsante destro del mouse sul sito utilizzato per la versione precedente di Adobe Campaign e seleziona **[!UICONTROL Edit bindings]**.
   * Per ogni tipo di porta di ascolto (**[!UICONTROL http]** e/o **[!UICONTROL https]**), seleziona la riga appropriata e fai clic su **[!UICONTROL Edit]**.
   * Immettere una porta diversa. Per impostazione predefinita, la porta di ascolto è 80 per http e 443 per https. Verifica che la nuova porta sia disponibile.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >Se il server IIS include diversi siti web per Adobe Campaign con una configurazione avanzata (porta condivisa e indirizzi IP diversi), contatta l’amministratore.

1. Crea un nuovo sito web per Adobe Campaign v7:

   * Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL Sites]** e seleziona **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * Immettere il nome del sito, **Adobe Campaign v7** per esempio.
   * Il percorso di accesso alla directory di base del sito web non viene utilizzato, ma il **[!UICONTROL Physical access path]** deve essere inserito. Immettere il percorso di accesso predefinito di IIS: **C:\inetpub\wwwroot**.
   * Fai clic sul pulsante **[!UICONTROL Connect as...]** come pulsante e assicurati che **[!UICONTROL Application user]** è selezionata.
   * È possibile lasciare i valori predefiniti nella **[!UICONTROL IP address]** e **[!UICONTROL Port]** campi. Se desideri utilizzare altri valori, assicurati che l’indirizzo IP e/o la porta siano disponibili.
   * Controlla la **[!UICONTROL Start Web site immediately]** scatola.

      ![](assets/_migration_iis_5_7.png)

1. Esegui il **iis_neolane_setup.vbs** script per configurare automaticamente le risorse utilizzate dal server Adobe Campaign nella directory virtuale creata in precedenza.

   * Questo file si trova nella **`[Adobe Campaign v7]`\conf** directory, dove **`[Adobe Campaign v7]`** è il percorso di accesso alla directory di installazione di Adobe Campaign. Il comando per l&#39;esecuzione dello script è il seguente (per gli amministratori):

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

   * In **[!UICONTROL Content view]** Assicurati che la configurazione del sito web sia configurata correttamente con le risorse Adobe Campaign:

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >Se la struttura ad albero non viene visualizzata, riavviare IIS.
      >
      >I seguenti passaggi di configurazione di IIS sono descritti in [questa sezione](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

<!--
## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. [Learn more](../../migration/using/general-configurations.md#security)
-->

## Servizi di riavvio {#re-starting-the-services}

Avvia i servizi IIS e Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Prima di passare al passaggio successivo, esegui un test completo della nuova installazione, assicurati che non ci siano regressioni e che tutto funzioni.

## Elimina la versione precedente {#deleting-and-cleansing-adobe-campaign-previous-version}

Procedura per eliminare Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5 {#adobe-campaign-v5}

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v5** website, then the **Neolane v5** application pool. 
1. Rename the **Neolane v5.back** folder as **Neolane v5**.
1. Uninstall Adobe Campaign v5 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Delete the **nlserver5** Windows service using the following command:

   ```
   sc delete nlserver5
   ```

1. Re-start the server.

### For Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Before you delete and cleanse the Adobe Campaign v6.02 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v6.02 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v6** website, then the **Neolane v6** application pool. 
1. Rename the **Neolane v6.back** folder as **Neolane v6**.
1. Uninstall Adobe Campaign v6.02 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Re-start the server.

-->

Prima di eliminare e pulire l’installazione di Adobe Campaign v6, è necessario applicare le seguenti raccomandazioni:

* Chiedi ai team funzionali di eseguire un controllo completo della nuova installazione.
* Disinstalla Adobe Campaign v6 solo una volta che sei sicuro che non è necessario eseguire il rollback.

1. In IIS, elimina la **Adobe Campaign v6** sito web, quindi **Adobe Campaign v6** pool di applicazioni.
1. Rinomina il **Adobe Campaign v6.back** cartella come **Adobe Campaign v6**.
1. Disinstallare Adobe Campaign v6 utilizzando la procedura guidata Aggiungi/rimuovi componenti .

   ![](assets/migration_wizard_2.png)

1. Riavvia il server.
