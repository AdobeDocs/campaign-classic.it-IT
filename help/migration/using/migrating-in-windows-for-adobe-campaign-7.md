---
solution: Campaign Classic
product: campaign
title: Migrazione in Windows per Adobe Campaign 7
description: Migrazione in Windows per Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 1%

---


# Migrazione in Windows per Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## Procedura generale {#general-procedure}

Per Windows, i passaggi di migrazione sono i seguenti:

1. Arresta servizi: fare riferimento a [Service Stop](#service-stop).
1. Eseguire il backup del database: fare riferimento a [Eseguire il backup del database e dell&#39;installazione](#back-up-the-database-and-the-current-installation)corrente.
1. Migra la piattaforma: fate riferimento a [Distribuzione  Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Migrare il server di reindirizzamento (IIS): fare riferimento a [Migrazione del server di reindirizzamento (IIS)](#migrating-the-redirection-server--iis-).
1. Riavvia il servizio: fare riferimento a [Riavvio dei servizi](#re-starting-the-services).
1. Elimina e pulisci la versione precedente  Adobe Campaign: fare riferimento a [Eliminazione e pulizia  versione](#deleting-and-cleansing-adobe-campaign-previous-version)precedente di Adobe Campaign.

## Interruzione del servizio {#service-stop}

In primo luogo, arrestate tutti i processi con accesso al database su tutti i computer interessati.

1. Tutti i server che utilizzano il modulo di reindirizzamento (servizio **webmdl** ) devono essere arrestati. Per IIS, eseguite il comando seguente:

   ```
   iisreset /stop
   ```

1. Il modulo **mta** e i relativi moduli secondari (**mtachild**) devono essere interrotti utilizzando i seguenti comandi:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Arrestate  servizi Adobe Campaign su tutti i server. Effettuate l&#39;accesso con diritti di amministratore ed eseguite il comando seguente:

   ```
   net stop nlserver6
   ```

   Se state effettuando la migrazione dalla v5.11, eseguite il comando seguente:

   ```
   net stop nlserver5
   ```

1. Per ciascun server, assicurarsi che  servizi Adobe Campaign siano correttamente arrestati. Effettuate l&#39;accesso con diritti di amministratore ed eseguite il comando seguente:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   Viene visualizzato l’elenco dei processi attivi con il relativo ID (PID).

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Se uno o più processi Adobe Campaign  sono ancora attivi o bloccati dopo qualche minuto, eliminarli. Effettuate l&#39;accesso con diritti di amministratore ed eseguite il comando seguente:

   ```
   taskkill /IM nlserver* /T
   ```

1. Se alcuni processi sono ancora attivi dopo alcuni minuti, è possibile forzarli a chiudersi utilizzando il comando:

   ```
   taskkill /F /IM nlserver* /T
   ```

## Eseguire il backup del database e dell&#39;installazione corrente {#back-up-the-database-and-the-current-installation}

La procedura dipende dalla versione precedente  Adobe Campaign.

### Migrazione da  Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Eseguire un backup del database Adobe Campaign .
1. Eseguire un backup della directory **Neolane v5** utilizzando il seguente comando:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >Come precauzione, consigliamo di comprimere la cartella **Neolane v5.back** e salvarla altrove in un percorso sicuro diverso dal server.

1. Nella console di gestione servizi di Windows, disattivate l&#39;avvio automatico del servizio server applicazioni 5.11. È inoltre possibile utilizzare il comando seguente:

   ```
   sc config nlserver5 start= disabled
   ```

1. Modificate **config-`<instance name>`.xml** (in **Neolane v5). back** folder) per impedire che **mta**, **wfserver**, **stat**, ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituire **autoStart** con **_autoStart**.

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
1. Eseguire un backup della directory **Neolane v6** utilizzando il seguente comando:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >Come precauzione, consigliamo di comprimere la cartella **Neolane v6.back** e salvarla altrove in un percorso sicuro diverso dal server.

1. In Gestione servizi di Windows, disattivare l&#39;avvio automatico del server applicazioni 6.02. È inoltre possibile utilizzare il comando seguente:

   ```
   sc config nlserver6 start= disabled
   ```

1. Modificate **config-`<instance name>`.xml** (in **Neolane v6). back** folder) per impedire che **mta**, **wfserver**, **stat**, ecc. l&#39;avvio automatico dei servizi. Ad esempio, sostituire **autoStart** con **_autoStart**.

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

### Migrazione da  Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Eseguire un backup del database Adobe Campaign .
1. Eseguite un backup della directory **Adobe Campaign v6** utilizzando il seguente comando:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Come precauzione, consigliamo di comprimere la cartella **Adobe Campaign v6.back** e salvarla altrove in un percorso sicuro diverso dal server.

1. Nella console di gestione servizi di Windows, disattivate l&#39;avvio automatico del servizio server applicazioni 6.11. È inoltre possibile utilizzare il comando seguente:

   ```
   sc config nlserver6 start= disabled
   ```

## Implementazione  Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La distribuzione  Adobe Campaign prevede due fasi:

* Installazione di build v7: questa operazione deve essere eseguita su ogni server.
* Post upgrade: questo comando deve essere avviato su ogni istanza.

Per distribuire  Adobe Campaign, eseguite i seguenti passaggi:

1. Installate la build Adobe Campaign v7 più recente  eseguendo il file di installazione **setup.exe** . Per ulteriori informazioni sull&#39;installazione del server Adobe Campaign  in Windows, consultare [questa sezione](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   > Adobe Campaign v7 è installato per impostazione predefinita nella directory **C:\Program Files\Adobe\Adobe Campaign v7** .

1. Per rendere disponibile il programma di installazione della console client, copiate il file **setup-client-7.0.XXXX.exe** nella directory di installazione di Adobe Campaign : **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Per ulteriori informazioni sull&#39;installazione  Adobe Campaign in Windows, consultare [questa sezione](../../installation/using/installing-the-server.md).

1. Iniziate l’istanza per il primo utilizzo con i seguenti comandi:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Questi comandi consentono di creare il file system interno  Adobe Campaign v7: **directory conf** (con i file **config-default.xml** e **serverConf.xml** ), directory **var** , ecc.

1. Copiate e incollate (sovrascrivete) i file di configurazione e le sottocartelle di ogni istanza tramite il file di backup **Neolane v5.back**, **Neolane v6.back** o **Adobe Campaign v6.back** (a seconda della versione da cui state eseguendo la migrazione - consultate [questa sezione](#back-up-the-database-and-the-current-installation)).
1. In base alla versione da cui state eseguendo la migrazione, eseguite i seguenti comandi:

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
   >Per il primo comando, non copiate il file **config-default.xml** .

1. Nei file **serverConf.xml** e **config-default.xml** di  Adobe Campaign v7, applicate le configurazioni specifiche  versione precedente di Adobe Campaign. Per il file **serverConf.xml** , usate il file **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** o **Adobe Campaign v6/conf/serverConf.xml.diff** .

   >[!NOTE]
   >
   >Quando riferite le configurazioni da  versione precedente di Adobe Campaign a  Adobe Campaign v7, accertatevi che i percorsi alle directory fisiche portino  Adobe Campaign v7 (e non Neolane v5, Neolane v6 o  Adobe Campaign v6).

1. Ricaricate la configurazione  Adobe Campaign v7 utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

1. Avviare il processo di post-aggiornamento utilizzando il seguente comando:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>Non avviare  servizi Adobe Campaign: è necessario apportare alcune modifiche a IIS.

## Migrazione del server di reindirizzamento (IIS) {#migrating-the-redirection-server--iis-}

In questa fase, il server IIS deve essere arrestato. Fare riferimento all&#39;arresto [del](#service-stop)servizio.

1. Aprite la console di Gestione **** Internet Information Services (IIS).
1. Modificare i binding (porte di ascolto) del sito utilizzato per  versione precedente di Adobe Campaign:

   * Fate clic con il pulsante destro del mouse sul sito utilizzato per  versione precedente di Adobe Campaign e selezionate **[!UICONTROL Edit bindings]**.
   * Per ciascun tipo di porta di ascolto (**[!UICONTROL http]** e/o **[!UICONTROL https]**), selezionate la riga appropriata e fate clic **[!UICONTROL Edit]**.
   * Immettete una porta diversa. Per impostazione predefinita, la porta di ascolto è 80 per http e 443 per https. Verificate che la nuova porta sia disponibile.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >Se il server IIS include diversi siti Web per  Adobe Campaign con una configurazione avanzata (porta condivisa e indirizzi IP diversi), contattare l&#39;amministratore.

1. Create un nuovo sito Web per  Adobe Campaign v7:

   * Fate clic con il pulsante destro del mouse sulla **[!UICONTROL Sites]** cartella e selezionate **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * Inserite il nome del sito, ad esempio **Adobe Campaign v7** .
   * Il percorso di accesso alla directory di base del sito Web non viene utilizzato, ma è necessario immettere il **[!UICONTROL Physical access path]** campo. Immettere il percorso di accesso predefinito di IIS: **C:\inetpub\wwwroot**.
   * Fate clic sul pulsante **[!UICONTROL Connect as...]** come e accertatevi che l&#39; **[!UICONTROL Application user]** opzione sia selezionata.
   * È possibile lasciare i valori predefiniti nei **[!UICONTROL IP address]** campi e **[!UICONTROL Port]** . Se desiderate utilizzare altri valori, accertatevi che l&#39;indirizzo IP e/o la porta siano disponibili.
   * Controlla la **[!UICONTROL Start Web site immediately]** casella.

      ![](assets/_migration_iis_5_7.png)

1. Eseguire lo script **is_neolane_setup.vbs** per configurare automaticamente le risorse utilizzate dal server Adobe Campaign  nella directory virtuale precedentemente creata.

   * Questo file si trova nella directory **`[Adobe Campaign v7]`\conf** , dove **`[Adobe Campaign v7]`** è il percorso di accesso alla directory di installazione di Adobe Campaign . Il comando per l&#39;esecuzione dello script è il seguente (per amministratori):

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * Fare clic **[!UICONTROL OK]** per confermare l&#39;esecuzione dello script.

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Immettete il numero del sito Web creato in precedenza per  Adobe Campaign v7 e fate clic **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Deve comparire un messaggio di conferma:

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * Nella **[!UICONTROL Content view]** scheda, accertatevi che la configurazione del sito Web sia configurata correttamente con  risorse Adobe Campaign:

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >Se la struttura ad albero non viene visualizzata, riavviare IIS.
      >
      >I seguenti passaggi di configurazione IIS sono descritti in [questa sezione](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

## Zone di protezione {#security-zones}

Se state eseguendo la migrazione dalla versione 6.02 o precedente, dovete configurare le aree di protezione prima di avviare i servizi. Per ulteriori informazioni, vedere [Sicurezza](../../migration/using/general-configurations.md#security).

## Riavvio dei servizi {#re-starting-the-services}

Avviate i servizi IIS e  Adobe Campaign su ciascuno dei seguenti server:

1. Server di tracciamento e reindirizzamento.
1. Server di mid-sourcing.
1. Server di marketing.

Prima di passare al passaggio successivo, eseguite un test completo della nuova installazione, accertatevi che non ci siano regressioni e che tutto funzioni seguendo tutte le raccomandazioni nella sezione [Configurazioni](../../migration/using/general-configurations.md) generali.

## Eliminazione e pulizia  versione precedente di Adobe Campaign {#deleting-and-cleansing-adobe-campaign-previous-version}

La procedura dipende dalla versione precedente  Adobe Campaign.

### Adobe Campaign v5 {#adobe-campaign-v5}

Prima di eliminare e cancellare l&#39;installazione  Adobe Campaign v5, è necessario applicare le seguenti raccomandazioni:

* Fate in modo che i team operativi eseguano un controllo completo della nuova installazione.
* Disinstallate  Adobe Campaign v5 solo dopo aver verificato che non è necessario eseguire il rollback.

1. In IIS, eliminate il sito Web **Neolane v5** , quindi il pool di applicazioni **Neolane v5** .
1. Rinominate la cartella **Neolane v5.back** come **Neolane v5**.
1. Disinstallare  Adobe Campaign v5 utilizzando la procedura guidata Aggiungi/rimuovi componenti.

   ![](assets/migration_wizard_2.png)

1. Eliminate il servizio **nlserver5** Windows utilizzando il seguente comando:

   ```
   sc delete nlserver5
   ```

1. Riavviate il server.

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Prima di eliminare e cancellare l&#39;installazione  Adobe Campaign v6.02, è necessario applicare le seguenti raccomandazioni:

* Fate in modo che i team operativi eseguano un controllo completo della nuova installazione.
* Disinstallate  Adobe Campaign v6.02 solo se siete certi che non è necessario eseguire il rollback.

1. In IIS, eliminate il sito Web **Neolane v6** , quindi il pool di applicazioni **Neolane v6** .
1. Rinominate la cartella **Neolane v6.back** come **Neolane v6**.
1. Disinstallare  Adobe Campaign v6.02 utilizzando la procedura guidata Aggiungi/rimuovi componenti.

   ![](assets/migration_wizard_2.png)

1. Riavviate il server.

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

Prima di eliminare e cancellare l&#39;installazione  di Adobe Campaign v6, è necessario applicare le seguenti raccomandazioni:

* Fate in modo che i team operativi eseguano un controllo completo della nuova installazione.
* Disinstallate  Adobe Campaign v6 solo dopo aver verificato che non è necessario eseguire il rollback.

1. In IIS, eliminate il sito Web **Adobe Campaign v6** , quindi il pool di applicazioni **Adobe Campaign v6** .
1. Rinominate la cartella **Adobe Campaign v6.back** come **Adobe Campaign v6**.
1. Disinstallare  Adobe Campaign v6 utilizzando la procedura guidata Aggiungi/rimuovi componenti.

   ![](assets/migration_wizard_2.png)

1. Riavviate il server.

