---
product: campaign
title: Aggiornamento a una nuova build
description: Scopri i passaggi tecnici per l’aggiornamento a una nuova build
feature: Monitoring, Upgrade
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: e5468f2aa5dc18c2b24c3e80e416e423ad0e13c9
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 2%

---

# Aggiornamento a una nuova build (on-premise){#upgrading}

Prima di avviare il processo di aggiornamento, determinare e confermare a quale versione di Adobe Campaign verrà effettuato l&#39;aggiornamento e consultare le [Note sulla versione](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* L’Adobe consiglia vivamente di eseguire un backup del database su ogni istanza prima di eseguire l’aggiornamento. Per ulteriori informazioni, consulta [questa sezione](../../production/using/backup.md).
>* Per eseguire un aggiornamento, assicurati di disporre delle capacità e delle autorizzazioni necessarie per accedere alle istanze e ai registri.
>* Prima di iniziare, leggi [questa sezione](../../installation/using/general-architecture.md) e il capitolo [aggiornamento build](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html).
>

## Windows {#in-windows}

In un ambiente Windows, eseguire la procedura seguente per aggiornare Adobe Campaign a una nuova build:

* [Arresta i servizi](#shut-down-services),
* [Aggiornare il server applicazioni](#upgrade-the-adobe-campaign-server-application),
* [Sincronizza risorse](#synchronize-resources),
* [Riavvia servizi](#restart-services).

Per informazioni su come aggiornare la console client, consultare [questa sezione](../../installation/using/client-console-availability-for-windows.md).

### Arresta servizi {#shut-down-services}

Per sostituire tutti i file con la nuova versione, è necessario arrestare tutte le istanze del servizio nlserver.

1. Arrestare i servizi seguenti:

   * Servizi Web (IIS):

     **iisreset /stop**

   * Servizio Adobe Campaign: **net stop nlserver6**

   >[!IMPORTANT]
   >
   >È inoltre necessario assicurarsi che il server di reindirizzamento (webmdl) sia arrestato, in modo che il file **nlsrvmod.dll** utilizzato da IIS possa essere sostituito con la nuova versione.

1. Verificare che nessuna attività sia attiva eseguendo il comando **nlserver pdump**. Dovrebbero sorgere i seguenti problemi:

   ```sql
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   È possibile utilizzare Gestione attività di Windows per assicurarsi che tutti i processi siano interrotti.

### Aggiornare l’applicazione server Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Per eseguire il file di aggiornamento, attenersi alla seguente procedura:

1. Eseguire **setup.exe**.

   Per scaricare questo file, connettiti al [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) utilizzando le credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).

1. Selezionare la modalità di installazione: scegliere **[!UICONTROL Update or repair]**
1. Fare clic su **[!UICONTROL Next]**.
1. Fare clic su **[!UICONTROL Finish]**.

   Il programma di installazione copia quindi i nuovi file.

1. Al termine dell&#39;operazione, fare clic su **[!UICONTROL Finish]**.

### Sincronizzare le risorse {#synchronize-resources}

Utilizza la seguente riga di comando:

**nlserver config -postupgrade -allinstances**

Ciò ti consentirà di eseguire le seguenti operazioni:

* Sincronizzare le risorse
* Aggiornare schemi
* aggiornare il database

>[!NOTE]
>
>Questa operazione deve essere eseguita una sola volta e solo su un server applicazioni (**nlserver web**).

Verificare quindi se la sincronizzazione ha generato errori o avvisi. Per ulteriori informazioni, consulta [Risoluzione dei conflitti di aggiornamento](#resolving-upgrade-conflicts).

### Riavvia servizi {#restart-services}

I servizi da riavviare sono:

* Servizi Web (IIS):

  **iisreset /start**

* Servizio Adobe Campaign: **net start nlserver6**

## Linux {#in-linux}

In un ambiente Linux, segui i passaggi seguenti per aggiornare Adobe Campaign a una nuova build:

* [Scarica i pacchetti aggiornati](#obtain-updated-packages),
* [Esegui l&#39;aggiornamento](#perform-an-update),
* [Riavviare il server Web](#reboot-the-web-server).

[Ulteriori informazioni sulla disponibilità della console client](../../installation/using/client-console-availability-for-windows.md).

### Installare i pacchetti aggiornati {#obtain-updated-packages}

Inizia recuperando entrambi i pacchetti aggiornati di Adobe Campaign: connettiti al [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) utilizzando le credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).

Il file è **nlserver6-v7-XXX.rpm**

>[!AVAILABILITY]
>
>A partire dalla versione 7.4.1, le librerie XML per i pacchetti RPM Linux non sono più incluse in Campaign. È necessario installare queste librerie.
> 

Quindi puoi installare i pacchetti richiesti, come descritto di seguito:

* Distribuzione basata su RPM (RedHat, SuSe)

  Se il pacchetto `epel-release` non è installato, installarlo. Per eseguire questa operazione, immetti il seguente comando, come root:

  ```
  yum install epel-release
  ```

  Per installare il pacchetto Campaign, esegui come root:

  ```
  yum update ./nlserver6-v7-XXXX.rpm
  ```

  Prima di confermare l’aggiornamento, accertati che l’output sia simile al seguente:

  ```
  ==================================================================================================== 
  Package                         Architecture  Version                    Repository           Size 
  ==================================================================================================== 
  Upgrading: 
  nlserver6-v7                    x86_64        XXXX.0.0-1                 @commandline         63 M
  ```

  >[!IMPORTANT]
  >
  >Se leggi `Removing:` invece di `Upgrading:`, annulla il comando. Probabilmente ci sono alcuni errori (elencati sopra) che spiegano la rimozione. In tal caso, correggere tali errori aggiornando/installando le dipendenze mancanti elencate e quindi provare a eseguire di nuovo il comando.

  Il file rpm dipende dai pacchetti che si trovano nelle distribuzioni CentOS/Red Hat. Se non si desidera utilizzare alcune di queste dipendenze, potrebbe essere necessario utilizzare l&#39;opzione &quot;nodeps&quot; di rpm:

  ```
  rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
  ```

  Si noti che la maggior parte delle dipendenze è obbligatoria e `nlserver` non può essere avviata se non è installata. L&#39;unica eccezione è openjdk; se necessario, è possibile installare un altro JDK.

* Distribuzione basata su DEB (Debian)

  Per installarli, esegui come root:

  ```
  apt install ./nlserver6-v7-XXXX-amd64_debX.deb
  ```

>[!NOTE]
>
>Le procedure di installazione complete sono descritte in [questa sezione](../../installation/using/installing-packages-with-linux.md). Le risorse vengono sincronizzate automaticamente, tuttavia è necessario assicurarsi che non si siano verificati errori. Per ulteriori informazioni, consulta [Risolvere i conflitti di aggiornamento](#resolving-upgrade-conflicts).
>

### Riavviare il server Web {#reboot-the-web-server}

Per rendere applicabile la nuova libreria, devi chiudere Apache.

A questo scopo, esegui il seguente comando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Lo script potrebbe essere denominato **httpd** anziché **apache**.
>* È NECESSARIO eseguire questo comando fino a ottenere la seguente risposta:
>
>   Questa operazione è necessaria per consentire ad Apache di applicare la nuova libreria.

Quindi riavvia Apache:

```
/etc/init.d/apache start
```

## Risolvere i conflitti di aggiornamento {#resolving-upgrade-conflicts}

Durante la sincronizzazione delle risorse, il comando **postupgrade** consente di rilevare se la sincronizzazione ha generato errori o avvisi.

### Visualizza il risultato della sincronizzazione {#view-the-synchronization-result}

Esistono due modi per visualizzare il risultato della sincronizzazione:

* Nell&#39;interfaccia della riga di comando, gli errori vengono materializzati da una tripla freccia **>>>** e la sincronizzazione viene interrotta automaticamente. Gli avvisi vengono materializzati da una doppia freccia **>>** e devono essere risolti al termine della sincronizzazione. Al termine del post-aggiornamento, al prompt dei comandi viene visualizzato un riepilogo. Può essere simile al seguente:

  ```
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Se l’avviso riguarda un conflitto di risorse, è necessario l’attenzione dell’utente per risolverlo.

* Il file di log **postupgrade_`<server version number>_<time of postupgrade>`.log** contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **`<installation directory>/var/<instance/postupgrade`**. Gli errori e gli avvisi sono indicati dagli attributi di errore e di avviso.

### Risolvi conflitti {#resolving-conflicts}

Per risolvere i conflitti, attenersi alla seguente procedura:

1. Nella struttura Adobe Campaign, vai a **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selezionare il conflitto che si desidera risolvere nell&#39;elenco.

Esistono tre modi per risolvere un conflitto:

* **[!UICONTROL Declare as resolved]** : richiede l&#39;intervento anticipato dell&#39;utente.
* **[!UICONTROL Accept the new version]** : consigliato se le risorse fornite con Adobe Campaign non sono state modificate dall&#39;utente.
* **[!UICONTROL Keep the current version]** : indica che l&#39;aggiornamento è stato rifiutato.

  >[!IMPORTANT]
  >
  >Se si seleziona questa modalità di risoluzione, è possibile che non si ottengano correzioni nella nuova versione.

Se si è scelto di risolvere il conflitto manualmente, procedere come segue:

1. Nella sezione inferiore della finestra, cerca la stringa **_conflitto_** per individuare le entità con conflitti. L&#39;entità installata con la nuova versione contiene l&#39;argomento **new**. L&#39;entità che corrisponde alla versione precedente contiene l&#39;argomento **cus**.

   ![](assets/s_ncs_production_conflict002.png)

1. Elimina la versione che non desideri mantenere. Eliminare la stringa **_conflitto_argomento_** dell&#39;entità che si desidera mantenere.

   ![](assets/s_ncs_production_conflict003.png)

1. Passare al conflitto risolto. Fare clic sull&#39;icona **[!UICONTROL Actions]** e selezionare **[!UICONTROL Declare as resolved]**.
1. Salva le modifiche: il conflitto è stato risolto.

### Best practice {#best-practices}

Un errore di aggiornamento potrebbe essere collegato alla configurazione del database. Verificare che le configurazioni eseguite dall&#39;amministratore tecnico e dall&#39;amministratore del database siano compatibili.

Ad esempio, un database unicode deve autorizzare non solo l’archiviazione di dati LATIN1, ecc.

## Avvisa le console client dell&#39;aggiornamento disponibile {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Nel computer in cui è installato il server applicazioni Adobe Campaign (**nlserver web**), scaricare e copiare il file **setup-client-6.XXXX.exe** i n **[percorso dell&#39;applicazione]/datakit/nl/eng/jsp**.

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Verificare che l&#39;utente IIS_XPG disponga dei diritti di lettura appropriati per questo file di installazione e fare riferimento alla [guida all&#39;installazione](../../installation/using/general-architecture.md) per ulteriori informazioni.

### Linux {#in-linux-1}

Nel computer in cui è installato il server applicazioni Adobe Campaign (**nlserver web**), recuperare il pacchetto **setup-client-6.XXXX.exe** e copiarlo, salvandolo come **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Assicurarsi che l&#39;utente Apache disponga dei diritti di lettura appropriati per questo file di installazione e fare riferimento alla [guida all&#39;installazione](../../installation/using/general-architecture.md) per ulteriori informazioni.
