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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 1%

---

# Aggiornamento a una nuova build (on-premise){#upgrading}



Prima di avviare il processo di aggiornamento, determinare e confermare la versione di Adobe Campaign da aggiornare e consultare [Note sulla versione](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* L’Adobe consiglia vivamente di eseguire un backup del database su ogni istanza prima di eseguire l’aggiornamento. Per ulteriori informazioni, consulta [questa sezione](../../production/using/backup.md).
>* Per eseguire un aggiornamento, assicurati di disporre delle capacità e delle autorizzazioni necessarie per accedere alle istanze e ai registri.
>* Leggete [questa sezione](../../installation/using/general-architecture.md) e [aggiornamento della build](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html) prima di iniziare.
>

## Windows {#in-windows}

In un ambiente Windows, eseguire la procedura seguente per aggiornare Adobe Campaign a una nuova build:

* [Arresta servizi](#shut-down-services),
* [Aggiornare il server applicazioni](#upgrade-the-adobe-campaign-server-application),
* [Sincronizzare le risorse](#synchronize-resources),
* [Riavvia servizi](#restart-services).

Per informazioni su come aggiornare la console client, consulta [questa sezione](../../installation/using/client-console-availability-for-windows.md).

### Arresta servizi {#shut-down-services}

Per sostituire tutti i file con la nuova versione, è necessario arrestare tutte le istanze del servizio nlserver.

1. Arrestare i servizi seguenti:

   * Servizi Web (IIS):

     **iisreset /stop**

   * Servizio Adobe Campaign: **net stop nlserver6**

   >[!IMPORTANT]
   >
   >È inoltre necessario assicurarsi che il server di reindirizzamento (webmdl) sia arrestato, in modo che **nlsrvmod.dll** Il file utilizzato da IIS può essere sostituito con la nuova versione.

1. Verificare che non vi siano attività attive eseguendo il comando **nlserver pdump** comando. Dovrebbero sorgere i seguenti problemi:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   È possibile utilizzare Gestione attività di Windows per assicurarsi che tutti i processi siano interrotti.

### Aggiornare l’applicazione server Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Per eseguire il file di aggiornamento, attenersi alla seguente procedura:

1. Esegui **setup.exe**.

   Per scaricare questo file, connettiti a [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) utilizzando le credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).

1. Selezionare la modalità di installazione: scegli **[!UICONTROL Update or repair]**
1. Clic **[!UICONTROL Next]** .
1. Clic **[!UICONTROL Finish]** .

   Il programma di installazione copia quindi i nuovi file.

1. Al termine dell’operazione, fai clic su **[!UICONTROL Finish]** .

### Sincronizzare le risorse {#synchronize-resources}

Utilizza la seguente riga di comando:

**nlserver config -postupgrade -allinstances**

Ciò ti consentirà di eseguire le seguenti operazioni:

* Sincronizzare le risorse
* Aggiornare schemi
* aggiornare il database

>[!NOTE]
>
>Questa operazione deve essere eseguita una sola volta e solo su un (**nlserver web**) server applicazioni.

Verificare quindi se la sincronizzazione ha generato errori o avvisi. Per ulteriori informazioni, consulta [Risoluzione dei conflitti di aggiornamento](#resolving-upgrade-conflicts).

### Riavvia servizi {#restart-services}

I servizi da riavviare sono:

* Servizi Web (IIS):

  **iisreset /start**

* Servizio Adobe Campaign: **net start nlserver6**

## Linux {#in-linux}

In un ambiente Linux, segui i passaggi seguenti per aggiornare Adobe Campaign a una nuova build:

* [Scaricare i pacchetti aggiornati](#obtain-updated-packages),
* [Eseguire l’aggiornamento](#perform-an-update),
* [Riavviare il server Web](#reboot-the-web-server).

[Ulteriori informazioni sulla disponibilità della console client](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>A partire dalla build 8757, la libreria di terze parti non è più necessaria.

### Ottenere i pacchetti aggiornati {#obtain-updated-packages}

Per iniziare, recupera entrambi i pacchetti aggiornati di Adobe Campaign: connettiti a [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) utilizzando le credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).

Il file è **nlserver6-v7-XXX.rpm**

### Eseguire un aggiornamento {#perform-an-update}

* Distribuzione basata su RPM (RedHat, SuSe)

  Per installarli, esegui come root:

  ```
  $rpm -Uvh nlserver6-v7-XXXX.rpm
  ```

  Dove XXX è la versione del file.

  Il file rpm dipende dai pacchetti che si trovano nelle distribuzioni CentOS/Red Hat. Se non si desidera utilizzare alcune di queste dipendenze, potrebbe essere necessario utilizzare l&#39;opzione &quot;nodeps&quot; di rpm:

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
>Le procedure complete di installazione sono descritte in [questa sezione](../../installation/using/installing-campaign-standard-packages.md). Le risorse vengono sincronizzate automaticamente, tuttavia è necessario assicurarsi che non si siano verificati errori. Per ulteriori informazioni, consulta [Risolvere i conflitti di aggiornamento](#resolving-upgrade-conflicts).

### Riavviare il server Web {#reboot-the-web-server}

Per rendere applicabile la nuova libreria, devi chiudere Apache.

A questo scopo, esegui il seguente comando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Il tuo script potrebbe essere chiamato **httpd** invece di **apache**.
>* È NECESSARIO eseguire questo comando fino a ottenere la seguente risposta:
>
>   Questa operazione è necessaria per consentire ad Apache di applicare la nuova libreria.

Quindi riavvia Apache:

```
/etc/init.d/apache start
```

## Risolvere i conflitti di aggiornamento {#resolving-upgrade-conflicts}

Durante la sincronizzazione delle risorse, il **post-aggiornamento** consente di rilevare se la sincronizzazione ha generato errori o avvisi.

### Visualizza il risultato della sincronizzazione {#view-the-synchronization-result}

Esistono due modi per visualizzare il risultato della sincronizzazione:

* Nell&#39;interfaccia della riga di comando, gli errori vengono materializzati da una tripla freccia **>>>** e la sincronizzazione viene interrotta automaticamente. Gli avvisi vengono materializzati da una doppia freccia **>>** e devono essere risolti al termine della sincronizzazione. Al termine del post-aggiornamento, al prompt dei comandi viene visualizzato un riepilogo. Può essere simile al seguente:

  ```
  2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
  2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Se l’avviso riguarda un conflitto di risorse, è necessario l’attenzione dell’utente per risolverlo.

* Il **postupgrade_`<server version number>_<time of postupgrade>`.log** il file di registro contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **`<installation directory>/var/<instance/postupgrade`**. Gli errori e gli avvisi sono indicati dagli attributi di errore e di avviso.

### Risolvi conflitti {#resolving-conflicts}

Per risolvere i conflitti, attenersi alla seguente procedura:

1. Nella struttura Adobe Campaign, vai a **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selezionare il conflitto che si desidera risolvere nell&#39;elenco.

Esistono tre modi per risolvere un conflitto:

* **[!UICONTROL Declare as resolved]** : richiede l’intervento anticipato dell’utente.
* **[!UICONTROL Accept the new version]** : consigliato se le risorse fornite con Adobe Campaign non sono state modificate dall’utente.
* **[!UICONTROL Keep the current version]** : indica che l’aggiornamento viene rifiutato.

  >[!IMPORTANT]
  >
  >Se si seleziona questa modalità di risoluzione, è possibile che non si ottengano correzioni nella nuova versione.

Se si è scelto di risolvere il conflitto manualmente, procedere come segue:

1. Nella sezione inferiore della finestra, cercare **_conflitto_** stringa per individuare le entità con conflitti. L’entità installata con la nuova versione contiene **nuovo** , l&#39;entità che corrisponde alla versione precedente contiene **cus** argomento.

   ![](assets/s_ncs_production_conflict002.png)

1. Elimina la versione che non desideri mantenere. Elimina **_argomento_conflitto_** stringa dell’entità che stai mantenendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Passare al conflitto risolto. Fai clic su **[!UICONTROL Actions]** e seleziona **[!UICONTROL Declare as resolved]** .
1. Salva le modifiche: il conflitto è stato risolto.

### Best practice {#best-practices}

Un errore di aggiornamento potrebbe essere collegato alla configurazione del database. Verificare che le configurazioni eseguite dall&#39;amministratore tecnico e dall&#39;amministratore del database siano compatibili.

Ad esempio, un database unicode deve autorizzare non solo l’archiviazione di dati LATIN1, ecc.

## Avvisa le console client dell&#39;aggiornamento disponibile {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Nel computer in cui è installato il server applicazioni di Adobe Campaign (**nlserver web**), scarica e copia il file  **setup-client-6.XXXX.exe** i n **[percorso dell’applicazione]/datakit/nl/eng/jsp**.

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Verificare che l&#39;utente IIS_XPG disponga dei diritti di lettura appropriati per il file di installazione e fare riferimento al [guida all’installazione](../../installation/using/general-architecture.md) per ulteriori informazioni.

### Linux {#in-linux-1}

Nel computer in cui è installato il server applicazioni Adobe Campaign (**nlserver web**) è installato, recuperare  **setup-client-6.XXXX.exe** creare un pacchetto e copiarlo, salvandolo come **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

>[!NOTE]
>
>Assicurati che l’utente Apache disponga dei diritti di lettura appropriati per questo file di installazione e fai riferimento a [guida all’installazione](../../installation/using/general-architecture.md) per ulteriori informazioni.
