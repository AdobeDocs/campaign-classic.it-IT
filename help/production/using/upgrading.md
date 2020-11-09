---
title: Aggiornamento a una nuova build
description: Scopri i passaggi tecnici per effettuare l'aggiornamento a una nuova build
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
translation-type: tm+mt
source-git-commit: 7e56e4f98ffab752f0b86bb8620fb1b4af6a3dca
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---


# Aggiornamento a una nuova build (locale){#upgrading}

Prima di avviare il processo di aggiornamento, determinare e confermare la versione di  Adobe Campaign in fase di aggiornamento e consultare le [Note](../../rn/using/latest-release.md) sulla versione.

>[!IMPORTANT]
>
>È consigliabile eseguire un backup del database in ogni istanza prima di eseguire l&#39;aggiornamento. Per ulteriori informazioni, vedere [Backup](../../production/using/backup.md).\
>Per eseguire un aggiornamento, accertati di disporre della capacità e delle autorizzazioni necessarie per accedere a istanze e registri.

>[!NOTE]
>
>Consultare anche la guida [all&#39;](../../installation/using/general-architecture.md) installazione e l&#39;aggiornamento [della](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html) build.

## Windows {#in-windows}

Per aggiornare  Adobe Campaign in una nuova versione al momento della distribuzione di una nuova build, in Windows dovrebbe essere applicata la seguente procedura:

* [Arrestare i servizi](#shut-down-services),
* [Aggiornare l&#39;applicazione](#upgrade-the-adobe-campaign-server-application)server Adobe Campaign ,
* [Sincronizzare le risorse](#synchronize-resources),
* [Riavviate i servizi](#restart-services).

Per informazioni su come aggiornare la console client, consulta [questa sezione](../../installation/using/client-console-availability-for-windows.md).

### Arrestare i servizi {#shut-down-services}

Per sostituire tutti i file con la nuova versione, è necessario chiudere tutte le istanze del servizio nlserver.

1. Arrestate i seguenti servizi:

   * Servizi Web (IIS):

      **iisreset /stop**

   *  servizio Adobe Campaign: **net stop nlserver6**
   >[!IMPORTANT]
   >
   >È inoltre necessario assicurarsi che il server di reindirizzamento (webmdl) sia arrestato, in modo che il file **nlsrvmod.dll** utilizzato da IIS possa essere sostituito con la nuova versione.

1. Verificare che non siano attive attività eseguendo il comando **nlserver pdump** . Dovrebbe essere visualizzato quanto segue:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   È possibile utilizzare Task Manager di Windows per verificare che tutti i processi siano interrotti.

### Aggiornamento dell&#39;applicazione server Adobe Campaign  {#upgrade-the-adobe-campaign-server-application}

Per eseguire il file di aggiornamento, procedere come segue:

1. Eseguire **setup.exe**.

   Per scaricare questo file, accedete alla  pagina Assistenza Adobe Campaign ( [https://support.neolane.net/](https://support.neolane.net/)) tramite il collegamento **Centro** download.

1. Selezionate la modalità di installazione: scegli **[!UICONTROL Update or repair]**
1. Fai clic su **[!UICONTROL Next]** .
1. Fai clic su **[!UICONTROL Finish]** .

   Il programma di installazione copia quindi i nuovi file.

1. Al termine dell&#39;operazione, fare clic su **[!UICONTROL Finish]** .

### Sincronizzare le risorse {#synchronize-resources}

Utilizzare la riga di comando seguente:

**nlserver config -postupgrade -allinstance**

Questo consente di eseguire le operazioni seguenti:

* Sincronizzare le risorse,
* schemi di aggiornamento,
* aggiornare il database.

>[!NOTE]
>
>Questa operazione deve essere eseguita una sola volta e solo su un server applicazione (**nlserver web**).

Quindi verificate se la sincronizzazione ha generato errori o avvisi. Per ulteriori informazioni, vedere [Risoluzione dei conflitti](#resolving-upgrade-conflicts)di aggiornamento.

### Riavvia servizi {#restart-services}

I servizi da riavviare sono:

* Servizi Web (IIS):

   **iisreset /start**

*  servizio Adobe Campaign: **net start nlserver6**

## Linux {#in-linux}

Per aggiornare  Adobe Campaign in una nuova versione quando viene consegnata una nuova build, la procedura per Linux è la seguente:

* [Ottenere pacchetti](#obtain-updated-packages)aggiornati,
* [Eseguire un aggiornamento](#perform-an-update),
* [Riavviare il server](#reboot-the-web-server)Web.

Per informazioni su come aggiornare la console client, consulta [questa sezione](../../installation/using/client-console-availability-for-linux.md).

>[!NOTE]
>
>Dalla build 8757, la libreria di terze parti non è più necessaria.

### Ottenere pacchetti aggiornati {#obtain-updated-packages}

Iniziate recuperando entrambi i pacchetti aggiornati di  Adobe Campaign: andate alla  pagina Assistenza Adobe Campaign ( [https://support.neolane.net/](https://support.neolane.net/)) tramite il collegamento **Centro** download.

Il file è **nlserver6-v7-XXX.rpm**

### Eseguire un aggiornamento {#perform-an-update}

* Distribuzione basata su RPM (RedHat, SuSe)

   Per installarli, eseguiteli come root:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   dove XXX è la versione del file.

   Il file rpm ha dipendenze su pacchetti che è possibile trovare sulle distribuzioni CentOS/Red Hat. Se non si desidera utilizzare alcune di queste dipendenze, potrebbe essere necessario utilizzare l&#39;opzione &quot;nodeps&quot; di rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* Distribuzione basata su DEB (Debian)

   Per installarli, eseguiteli come root:

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>Le procedure di installazione complete sono descritte in [questa sezione](../../installation/using/installing-campaign-standard-packages.md). Le risorse vengono sincronizzate automaticamente, tuttavia è necessario assicurarsi che non si verifichino errori. Per ulteriori informazioni, vedere [Risoluzione dei conflitti](#resolving-upgrade-conflicts)di aggiornamento.

### Riavviare il server Web {#reboot-the-web-server}

Per rendere applicabile la nuova libreria, è necessario chiudere Apache.

A questo scopo, eseguite il comando seguente:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Lo script potrebbe essere denominato **httpd** invece di **apache**.
>* È NECESSARIO eseguire questo comando fino a ottenere la seguente risposta:

   >
   >   
   Questa operazione è necessaria per consentire ad Apache di applicare la nuova libreria.


Quindi riavviate Apache:

```
/etc/init.d/apache start
```

## Risoluzione dei conflitti di aggiornamento {#resolving-upgrade-conflicts}

Durante la sincronizzazione delle risorse, il comando **postupgrade** consente di rilevare se la sincronizzazione ha generato errori o avvisi.

### Visualizzare il risultato della sincronizzazione {#view-the-synchronization-result}

Esistono due modi per visualizzare il risultato della sincronizzazione:

* Nell&#39;interfaccia della riga di comando, gli errori vengono generati da una tripla freccia **>>** e la sincronizzazione viene arrestata automaticamente. Le avvertenze vengono materializzate da una doppia freccia **>>** e devono essere risolte una volta completata la sincronizzazione. Alla fine del post aggiornamento, nel prompt dei comandi viene visualizzato un riepilogo. Può essere simile al seguente:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Se l&#39;avviso riguarda un conflitto di risorse, è necessario prestare attenzione alla risoluzione del problema.

* Il file di registro **postupgrade_`<server version number>_<time of postupgrade>`.log** contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **`<installation directory>/var/<instance/postupgrade`**. Gli errori e gli avvisi sono indicati dagli attributi di errore e avviso.

### Risoluzione dei conflitti {#resolving-conflicts}

Per risolvere i conflitti, eseguire il seguente processo:

1. Nella struttura  Adobe Campaign, andate a **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selezionare il conflitto da risolvere nell&#39;elenco.

Esistono tre modi per risolvere un conflitto:

* **[!UICONTROL Declare as resolved]** : richiede l&#39;intervento preventivo dell&#39;utente.
* **[!UICONTROL Accept the new version]** : consigliato se le risorse fornite con  Adobe Campaign non sono state modificate dall&#39;utente.
* **[!UICONTROL Keep the current version]** : indica che l&#39;aggiornamento viene rifiutato.

   >[!IMPORTANT]
   >
   >Se si seleziona questa modalità di risoluzione, è possibile che non si ottengano correzioni nella nuova versione.

Se avete scelto di risolvere il conflitto manualmente, procedete come segue:

1. Nella sezione inferiore della finestra, cercare la stringa del **_conflitto_** per individuare le entità con conflitti. L&#39;entità installata con la nuova versione contiene il **nuovo** argomento, l&#39;entità che corrisponde alla versione precedente contiene l&#39; **argomento cus** .

   ![](assets/s_ncs_production_conflict002.png)

1. Eliminate la versione che non desiderate mantenere. Eliminate la stringa **_conflitto_argomento_** dell&#39;entità da mantenere.

   ![](assets/s_ncs_production_conflict003.png)

1. Vai al conflitto risolto. Fate clic sull&#39; **[!UICONTROL Actions]** icona e selezionate **[!UICONTROL Declare as resolved]** .
1. Salvare le modifiche: il conflitto ora è risolto.

### Best practice {#best-practices}

Un errore di aggiornamento potrebbe essere collegato alla configurazione del database. Verificate che le configurazioni eseguite dall&#39;amministratore tecnico e dall&#39;amministratore del database siano compatibili.

Ad esempio, un database unicode non deve solo autorizzare la memorizzazione di dati LATIN1, ecc.

## Avvisa le console client dell’aggiornamento disponibile {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Nel computer in cui è installato (**server Web**)  server applicazioni Adobe Campaign, scaricate e copiate il file

**setup-client-6.XXXX.exe**

in **[percorso dell&#39;applicazione]**datakitnlunjsp

Alla successiva connessione delle console client, una finestra informerà gli utenti della disponibilità di un aggiornamento e offrirà loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Verificare che l&#39;utente IIS_XPG disponga dei diritti di lettura appropriati per questo file di installazione e consultare la guida [all&#39;](../../installation/using/general-architecture.md) installazione per ulteriori informazioni.

### Linux {#in-linux-1}

Nel computer in cui è installato  server applicazioni Adobe Campaign (**server Web**), recuperate il pacchetto seguente:

**setup-client-6.XXXX.exe**

e copiarlo, salvandolo come **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Alla successiva connessione delle console client, una finestra informerà gli utenti della disponibilità di un aggiornamento e offrirà loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Accertatevi che l&#39;utente Apache disponga dei diritti di lettura appropriati per questo file di installazione e fate riferimento alla guida [all&#39;](../../installation/using/general-architecture.md) installazione per ulteriori informazioni.

