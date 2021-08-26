---
product: campaign
title: Aggiornamento a una nuova build
description: Scopri i passaggi tecnici per l’aggiornamento a una nuova build
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 3%

---

# Aggiornamento a una nuova build (on-premise){#upgrading}

![](../../assets/v7-only.svg)

Prima di avviare il processo di aggiornamento, determina e conferma quale versione di Adobe Campaign deve essere aggiornata a e consulta le [Note sulla versione](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe consiglia vivamente di eseguire un backup del database su ogni istanza prima dell&#39;aggiornamento. Per ulteriori informazioni, consulta [questa sezione](../../production/using/backup.md).
>* Per eseguire un aggiornamento, assicurati di disporre della capacità e delle autorizzazioni per accedere alle istanze e ai registri.
>* Leggi [questa sezione](../../installation/using/general-architecture.md) e il capitolo [build upgrade](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html) prima di iniziare.

>


## Windows {#in-windows}

In un ambiente Windows, segui i passaggi seguenti per aggiornare Adobe Campaign a una nuova build:

* [Servizi](#shut-down-services) di arresto,
* [Aggiornare l&#39;application server](#upgrade-the-adobe-campaign-server-application),
* [Sincronizzare le risorse](#synchronize-resources),
* [Riavvia i servizi](#restart-services).

Per informazioni su come aggiornare la console client, consulta [questa sezione](../../installation/using/client-console-availability-for-windows.md).

### Servizi di arresto {#shut-down-services}

Per sostituire tutti i file con la nuova versione, è necessario arrestare tutte le istanze del servizio nlserver.

1. Spegni i seguenti servizi:

   * Servizi Web (IIS):

      **iisreset /stop**

   * Servizio Adobe Campaign: **net stop nlserver6**
   >[!IMPORTANT]
   >
   >È inoltre necessario assicurarsi che il server di reindirizzamento (webmdl) sia arrestato, in modo che il file **nlsrvmod.dll** utilizzato da IIS possa essere sostituito con la nuova versione.

1. Verificare che nessuna attività sia attiva eseguendo il comando **nlserver pdump**. Dovrebbe comparire quanto segue:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   È possibile utilizzare Gestione attività di Windows per assicurarsi che tutti i processi siano interrotti.

### Aggiornare l’applicazione server Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Per eseguire il file di aggiornamento, procedi come segue:

1. Eseguire **setup.exe**.

   Per scaricare questo file, connettiti al [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) utilizzando le tue credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it?lang=en).

1. Seleziona la modalità di installazione: scegli **[!UICONTROL Update or repair]**
1. Fai clic su **[!UICONTROL Next]** .
1. Fai clic su **[!UICONTROL Finish]** .

   Il programma di installazione copia quindi i nuovi file.

1. Al termine dell’operazione, fai clic su **[!UICONTROL Finish]** .

### Sincronizzare le risorse {#synchronize-resources}

Utilizzare la seguente riga di comando:

**nlserver config -postupgrade -allinstances**

In questo modo potrai eseguire le seguenti operazioni:

* Sincronizzare le risorse
* Aggiorna schemi
* aggiornare il database

>[!NOTE]
>
>Questa operazione deve essere eseguita una sola volta e solo su un server applicativo (**nlserver web**).

Quindi controlla se la sincronizzazione ha generato errori o avvisi. Per ulteriori informazioni, consulta [Risoluzione dei conflitti di aggiornamento](#resolving-upgrade-conflicts).

### Riavvia i servizi {#restart-services}

I servizi da riavviare sono i seguenti:

* Servizi Web (IIS):

   **iisreset /start**

* Servizio Adobe Campaign: **net start nlserver6**

## Linux {#in-linux}

In un ambiente Linux, segui i passaggi seguenti per aggiornare Adobe Campaign a una nuova build:

* [Scarica i pacchetti](#obtain-updated-packages) aggiornati,
* [Esegui l&#39;aggiornamento](#perform-an-update),
* [Riavviare il server](#reboot-the-web-server) web.

[Ulteriori informazioni sulla disponibilità](../../installation/using/client-console-availability-for-windows.md) della console client.

>[!NOTE]
>
>Dalla build 8757, la libreria di terze parti non è più necessaria.

### Ottieni pacchetti aggiornati {#obtain-updated-packages}

Inizia recuperando entrambi i pacchetti aggiornati di Adobe Campaign: connettersi al [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) utilizzando le credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

Il file è **nlserver6-v7-XXX.rpm**

### Eseguire un aggiornamento {#perform-an-update}

* Distribuzione basata su RPM (RedHat, SuSe)

   Per installarli, esegui come root:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   Dove XXX è la versione del file.

   Il file rpm ha dipendenze da pacchetti che è possibile trovare sulle distribuzioni CentOS/Red Hat. Se non si desidera utilizzare alcune di queste dipendenze, potrebbe essere necessario utilizzare l&#39;opzione &quot;nodeps&quot; di rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* Distribuzione basata su DEB (Debian)

   Per installarli, esegui come root:

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>Le procedure di installazione complete sono descritte in [questa sezione](../../installation/using/installing-campaign-standard-packages.md). Le risorse vengono sincronizzate automaticamente, tuttavia è necessario assicurarsi che non si siano verificati errori. Per ulteriori informazioni, consulta [Risolvere i conflitti di aggiornamento](#resolving-upgrade-conflicts).

### Riavviare il server web {#reboot-the-web-server}

Per rendere applicabile la nuova libreria, è necessario arrestare Apache.

A questo scopo, esegui il seguente comando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Lo script potrebbe essere denominato **httpd** invece di **apache**.
>* È NECESSARIO eseguire questo comando finché non si ottiene la seguente risposta:

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

* Nell&#39;interfaccia a riga di comando, gli errori vengono materializzati da una tripla freccia **>>>** e la sincronizzazione viene arrestata automaticamente. Gli avvisi vengono materializzati da una doppia freccia **>>** e devono essere risolti una volta completata la sincronizzazione. Al termine del post aggiornamento, nel prompt dei comandi viene visualizzato un riepilogo. Può essere così:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Se l’avviso riguarda un conflitto di risorse, è necessario prestare attenzione a risolverlo.

* Il file di registro **postupgrade_`<server version number>_<time of postupgrade>`.log** contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **`<installation directory>/var/<instance/postupgrade`**. Gli errori e gli avvisi sono indicati dagli attributi di errore e avviso.

### Risolvere i conflitti {#resolving-conflicts}

Per risolvere i conflitti, applicare il seguente processo:

1. Nella struttura di Adobe Campaign, vai a **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selezionare il conflitto da risolvere nell&#39;elenco.

Esistono tre modi per risolvere un conflitto:

* **[!UICONTROL Declare as resolved]** : richiede prima l&#39;intervento dell&#39;utente.
* **[!UICONTROL Accept the new version]** : consigliato se l’utente non ha modificato le risorse fornite con Adobe Campaign.
* **[!UICONTROL Keep the current version]** : significa che l&#39;aggiornamento viene rifiutato.

   >[!IMPORTANT]
   >
   >Se si seleziona questa modalità di risoluzione, è possibile che non si tratti di correzioni nella nuova versione.

Se si sceglie di risolvere il conflitto manualmente, procedere come segue:

1. Nella sezione inferiore della finestra, cerca la stringa **_Conflitto_** per individuare le entità con conflitti. L&#39;entità installata con la nuova versione contiene l&#39;argomento **new**, l&#39;entità che corrisponde alla versione precedente contiene l&#39;argomento **cus**.

   ![](assets/s_ncs_production_conflict002.png)

1. Elimina la versione che non desideri mantenere. Elimina la stringa **_conflittuale_** dell&#39;entità che stai mantenendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vai al conflitto che hai risolto. Fai clic sull’icona **[!UICONTROL Actions]** e seleziona **[!UICONTROL Declare as resolved]** .
1. Salva le modifiche: il conflitto è ora risolto.

### Best practice {#best-practices}

È possibile collegare un errore di aggiornamento alla configurazione del database. Assicurati che le configurazioni eseguite dall’amministratore tecnico e dall’amministratore del database siano compatibili.

Ad esempio, un database unicode non deve solo autorizzare l’archiviazione di dati LATIN1, ecc.

## Avvisa le console client dell’aggiornamento disponibile {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Sul computer in cui è installato l&#39;application server di Adobe Campaign (**nlserver web**), scarica e copia il file **setup-client-6.XXXX.exe** i **[percorso dell&#39;applicazione]/datakit/nl/eng/jsp**.

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Assicurati che l&#39;utente IIS_XPG disponga dei diritti di lettura appropriati per questo file di installazione e fai riferimento alla [guida all&#39;installazione](../../installation/using/general-architecture.md) per ulteriori informazioni.

### Linux {#in-linux-1}

Sul computer in cui è installato l&#39;application server Adobe Campaign (**nlserver web**), recupera il pacchetto **setup-client-6.XXXX.exe** e lo copia, salvandolo come **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Assicurati che l&#39;utente Apache disponga dei diritti di lettura appropriati per questo file di installazione e fai riferimento alla [guida all&#39;installazione](../../installation/using/general-architecture.md) per ulteriori informazioni.
