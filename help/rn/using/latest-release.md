---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: da35a3050d838cd8e57bf802dc066e32f22f8273
workflow-type: ht
source-wordcount: '2295'
ht-degree: 100%

---

# Ultima versione{#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.3.5 - Build 9368 {#release-7-3-5}

[!BADGE Disponibilità generale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}


_5 dicembre 2023_


### Miglioramenti di sicurezza {#release-7-3-5-security}


* Con Campaign Classic v7.3.5, il processo di autenticazione è stato migliorato e protetto. Gli operatori tecnici ora devono utilizzare Adobe Identity Management System (IMS) per connettersi a Campaign. Scopri come eseguire la migrazione degli account tecnici esistenti in [questa nota tecnica](../../technotes/using/ims-migration.md).

* Inoltre, come parte del tentativo di rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare la modalità di autenticazione dell’utente finale dall’autenticazione nativa di login/password ad Adobe Identity Management System (IMS). Scopri come effettuare la migrazione degli operatori in [questa nota tecnica](../../technotes/using/migrate-users-to-ims.md).

### Patch {#release-7-3-5-patches}

* È stato risolto un problema che si verificava durante l’utilizzo di dati da un database Google Big Query e l’aggiornamento di dati in un database di Oracle: tutte le chiavi erano impostate su `0` nella tabella temporanea del flusso di lavoro. (NEO-65091)
* È stato risolto un problema che causava un errore nell’esecuzione di un flusso di lavoro quando due query su un database Google Big Query venivano combinate in un’attività del flusso di lavoro **Unione**. (NEO-63705)
* È stato risolto un problema che richiedeva all’utente di autenticarsi nuovamente facendo clic sul pulsante `Back` in un rapporto sulla campagna. (NEO-65087)
* È stato corretto un errore nel flusso di lavoro di pulizia del database che si verificava quando una consegna veniva eliminata prima delle relative bozze di consegna. (NEO-48114)
* È stato risolto un problema che si verificava durante la connessione alla console client: gli aggiornamenti recenti sulla verifica TLS causavano un errore di connessione. (NEO-50488)
* È stato risolto un problema relativo all’autenticazione proxy HTTP dopo l’aggiornamento di Campaign alla versione 7.3.1. Le richieste HTTP nei flussi di lavoro di Campaign generavano errori con `error 407 – proxy auth required is returned`. (NEO-49624)
* È stato risolto un errore intermittente con la decrittografia GPG nelle attività del flusso di lavoro **Script**. Il messaggio di errore associato era: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

## Versione 7.3.4 - Build 9364 {#release-7-3-4}

[!BADGE Disponibilità limitata]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità limitata"}


>[!CAUTION]
>
>L’aggiornamento della console client è obbligatorio. Scopri come aggiornare la console client in questa [pagina](../../installation/using/installing-the-client-console.md).
>
>Se stai usando il [Connettore per la gestione delle relazioni con i clienti Microsoft Dynamics - Campaign](../../platform/using/crm-connectors.md), con questa nuova build devi aggiornare sia i server di marketing che quelli di mid-sourcing.

_7 settembre 2023_

### Miglioramenti di sicurezza {#release-7-3-4-security}

* La sicurezza è stata migliorata nelle API IMS. Le informazioni sensibili per il client (ad esempio i token di accesso) sono state rimosse dai parametri URL. Queste credenziali vengono ora inviate nell’intestazione dei dati post o dell’autorizzazione, garantendo un processo di comunicazione più sicuro. (NEO-63045)
* È stata migliorata la sicurezza nelle app web per prevenire gli attacchi DDOS. (NEO-50757)
* È stata migliorata la sicurezza per evitare che i dati PII vengano esposti negli errori dei registri web. (NEO-46827)
* La sicurezza è stata ottimizzata per impedire l’inclusione del token di sicurezza nell’URL della pagina Home di Campaign. (NEO-38519)

### Aggiornamenti della compatibilità  {#release-7-3-4-compat}

* Tomcat è stato aggiornato alla versione 8.5.91
* La libreria libexpat è stata aggiornata alla versione 2.5.0 per migliorare la sicurezza. (NEO-51023)

### Miglioramenti {#release-7-3-4-improvements}

* Il parametro MaxWorkingSetMb nel file di configurazione del server (serverConf.xml) è stato modificato per ottimizzare l’allocazione della memoria per le consegne. (NEO-49204)
* L’account esterno BigQuery è stato migliorato con nuove opzioni utilizzate per configurare l’SDK GCloud. (NEO-63879) [Ulteriori informazioni](../../installation/using/configure-fda-google-big-query.md#google-external)
* È stata aggiunta una nuova sezione `cusHeader` nel file di configurazione del server (serverConf.xml). Questa consente di aggiungere intestazioni personalizzate durante il caricamento di un file da un server esterno. (NEO-58339) [Ulteriori informazioni](../../installation/using/the-server-configuration-file.md#cusheaders).
* La gestione del registro di tracciamento è stata migliorata per evitare ID negativi per lastMsgId. È stato modificato da int32 a int64. (NEO-52290)
* Il flusso di lavoro di mid-sourcing (statistiche di consegna) è stato aggiunto come preconfigurato. Questo nuovo flusso di lavoro sincronizza i dati statistici di consegna (nms:deliveryStat) dall’istanza mid a quella di marketing. (NEO-36802)

### Patch {#release-7-3-4-patches}

* È stato risolto un problema che poteva verificarsi quando una richiesta di servizio veniva effettuata prima dell’accesso IMS, se l’autenticazione della chiamata della richiesta di servizio utilizzava un token di servizio. (NEO-64903)
* È stato risolto un problema di regressione che poteva causare problemi di scorrimento durante l’utilizzo di Digital Content Editor. (NEO-64671, NEO-59256)
* È stato risolto un problema di regressione che si verificava quando si incollava contenuto da Excel a Digital Content Editor. (NEO-63287)
* È stato risolto un problema che poteva impedire la corretta visualizzazione delle applicazioni web in modalità di compatibilità v5. (NEO-63174)
* È stato risolto un problema che impediva agli operatori non amministratori di inviare consegne webAnalytics. (NEO-62750)
* È stato risolto un problema che impediva ai browser di aggiungere spazi aggiuntivi durante l’utilizzo di contenuto condizionale in una consegna. (NEO-62132)
* È stato risolto un problema di regressione che impediva il corretto funzionamento del calcolo del contatto attivo nel flusso di lavoro Fatturazione quando si utilizzavano schemi di destinazione associati a più schemi di registro. (NEO-61468)
* È stato risolto un problema che poteva causare un errore e impedire lo scorrimento durante la modifica del contenuto di una consegna. (NEO-61364)
* È stato risolto un problema che causava l’apertura di una finestra a comparsa quando si faceva clic su un’immagine nell’editor dei contenuti e-mail. (NEO-60752)
* È stato risolto un problema che poteva causare la codifica errata in diversi browser dei caratteri speciali nel contenuto HTML di una consegna. (NEO-60081)
* È stato risolto un problema di sincronizzazione che poteva verificarsi durante l’utilizzo dell’attività del flusso di lavoro inSMS. (NEO-59544)
* È stato risolto un problema che si verificava con l’utilizzo del connettore Big Query con campi timestamp o datetime. (NEO-59502, NEO-49768)
* È stato risolto un problema che impediva l’utilizzo dei rapporti sulle consegne cumulativi. (NEO-59211)
* È stato risolto un problema che poteva causare errori durante la condivisione dei tipi di pubblico con il servizio core People. (NEO-58637)
* È stato risolto un problema che si verificava durante la visualizzazione della pagina mirror di una consegna. (NEO-58325)
* È stato risolto un problema che impediva il funzionamento dell’espressione XtkLibrary.Right() xtk. (NEO-57870)
* È stato risolto un problema che causava la modifica dell’attributo di stile del tag del corpo se si caricava un’immagine dal Digital Content Editor. (NEO-57697)
* È stato risolto un problema relativo ai caratteri speciali durante l’esecuzione di esportazioni batch con l’attività del connettore di gestione delle relazioni con i clienti. (NEO-54300)
* È stato risolto un problema che impediva il funzionamento del caricamento in blocco con i tipi di dati “stringa” quando si utilizzava un’attività di caricamento dati e il connettore Big Query. (NEO-53748)
* È stato risolto un problema relativo alla chiave della cache che poteva causare problemi di rendering delle offerte. (NEO-51516, NEO-49995)
* È stato risolto un problema che poteva causare un errore di convalida durante l’invio di una consegna direct mail utilizzando targetMapping con approvazioni. (NEO-50758)
* È stato risolto un problema di gestione delle query che poteva influire sulle prestazioni di consegna. (NEO-49991)
* È stato risolto un problema che si verificava durante l’utilizzo di account esterni nelle attività di consegna del flusso di lavoro della campagna e che poteva causare problemi di configurazione dell’account esterno. (NEO-49959)
* È stato risolto un problema di prestazioni che si verificava durante l’invio di notifiche push. (NEO-49953)
È stato risolto un problema che poteva causare la visualizzazione errata dei caratteri giapponesi durante l’esportazione dei rapporti (NEO-49308).
* È stato risolto un problema che causava la visualizzazione di troppi dettagli sull’errore nel rapporto di errore Tomcat. (NEO-49029)
* È stato risolto un problema che poteva causare un errore di consegna se si utilizzava un numero elevato di offerte. (NEO-48807)
* È stato risolto un problema che poteva impedire il corretto funzionamento dell’attività del flusso di lavoro **Aggiorna dati**. (NEO-48140)
* È stato risolto un problema che poteva impedire la sincronizzazione dei dati di tracciamento dei clic per le consegne tramite un account esterno diverso dall’e-mail.(NEO-47277)
* È stato risolto un problema che poteva impedire la sincronizzazione dei registri di tracciamento in tempo reale nell’istanza marketing del Centro messaggi. (NEO-42540)
* È stato risolto un problema che impediva la visualizzazione del prefisso dell’area di lavoro nella finestra di individuazione di uno schema, per le tabelle del database Snowflake. (NEO-40297)
* È stato risolto un problema che impediva il funzionamento dei tag `<img-amp>` nel contenuto e-mail. (NEO-38685)
* È stato risolto un problema che poteva causare un errore nel flusso di lavoro di archiviazione del Centro messaggi in caso di utilizzo di un inoltro HTTP. (NEO-33783)
* È stato risolto un problema che poteva causare errori nel nome e nelle dimensioni del font nell’editor del contenuto dell’e-mail. (NEO-61342)

## Versione 7.3.3 - Build 9359 {#release-7-3-3}

[!BADGE Disponibilità limitata]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità limitata"}

>[!AVAILABILITY]
>
>Per questa versione è disponibile un aggiornamento specifico della patch di Campaign v7.3.3.IMS, se non è stata applicata alcuna altra patch all’ambiente. Questa porta negli ambienti v7.3.3 esistenti [gli aggiornamenti di sicurezza di Adobe Identity Management System (IMS) in arrivo con la versione v7.3.5](#release-7-3-5-security).


_20 marzo 2023_


### Miglioramento di sicurezza {#release-7-3-3-security}

* Per migliorare la sicurezza, Tomcat è stato aggiornato dalla versione 8.5.81 alla versione 8.5.85. (NEO-56936)



### Miglioramenti {#release-7-3-3-improvements}

* Il flusso di lavoro Fatturazione è stato migliorato per ottimizzarne le prestazioni. (NEO-47658)
* Il flusso di lavoro di tracciamento è stato migliorato per ottimizzarne le prestazioni in caso di consegne di dimensioni elevate. (NEO-45064)
* La gestione del tracciamento è stata migliorata per risolvere possibili problemi relativi ai parametri dinamici negli URL. La gestione del tracciamento v3 ora gestisce gli URL di tipo AJAX (con parametri dopo il simbolo “#”) e impedisce agli strumenti di terze parti di modificare gli URL di tracciamento. Per applicare questa modifica, contatta Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>L’aggiornamento della console client è obbligatorio. Scopri come aggiornare la console client in questa [pagina](../../installation/using/installing-the-client-console.md).

### Patch {#release-7-3-3-patches}

* È stato risolto un problema che poteva impedire all’istanza di controllo (contesto Messaggistica transazionale) di inviare notifiche push iOS in stato di bozza. (NEO-54713)
* È stato risolto un problema che poteva impedire lo scorrimento nella scheda **Modifica** dell’editor di contenuti digitali (DCE). (NEO-54474)
* È stato risolto un problema che si verificava quando due attività di arricchimento utilizzavano lo stesso identificatore di nome nel collegamento, e questo faceva sì che la seconda utilizzasse i collegamenti della prima. (NEO-48851)

## Versione 7.3.2 - Build 9356 {#release-7-3-2}

[!BADGE Disponibilità limitata]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità limitata"}


>[!AVAILABILITY]
>
>Per questa versione è disponibile un aggiornamento specifico della patch di Campaign v7.3.2.IMS, se non è stata applicata alcuna altra patch all’ambiente. Questa porta negli ambienti v7.3.3 esistenti [gli aggiornamenti di sicurezza di Adobe Identity Management System (IMS) in arrivo con la versione v7.3.5](#release-7-3-5-security).

_21 novembre 2022_

### Aggiornamenti della compatibilità {#release-7-3-2-compat}

* Adobe Campaign è ora compatibile con PostgreSQL 14. Per ulteriori informazioni, consulta questa [nota tecnica](../../technotes/using/tech-stack-upgrade.md).

* Dopo la fine del ciclo di vita di Microsoft Internet Explorer 11, il motore di rendering HTML per le dashboard nella console client utilizza ora Edge Chromium. (NEO-20741)

Ulteriori informazioni nella [matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

>[!CAUTION]
>
>L’aggiornamento della console client è obbligatorio. Scopri come aggiornare la console client in questa [pagina](../../installation/using/installing-the-client-console.md).

### Miglioramenti {#release-7-3-2-improvements}

* Il connettore Google BigQuery ora supporta completamente i campi booleani. (NEO-49181)
* Ora è possibile configurare la durata di validità dei cookie IMS nella sezione `Configuration for the redirection service` del file serverConf.xml. Questo vale per i seguenti cookie: `uuid230`, `nllastdelid` e `AMCV_` (NEO-42541)
* Nella richiesta “r/test” ora l’IP può essere nascosto impostando `showSourceIP` su false nel nodo di reindirizzamento del file serverConf.xml. [Maggiori informazioni](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

### Funzioni obsolete  {#release-7-3-2-deprecated}

* Il Social Marketing con Facebook è ora obsoleto. Per pubblicare sui social media o lavorare con Adobe per creare un canale personalizzato, è possibile utilizzare l’integrazione con X (precedentemente noto come Twitter).
* Il connettore ACS (offerta Prime) è ora obsoleto. È possibile utilizzare le funzionalità di esportazione/importazione di Campaign per estrarre e inserire dati in entrambi i prodotti.

Ulteriori informazioni sono disponibili nella pagina [Funzioni obsolete e rimosse](deprecated-features.md).

### Altre modifiche  {#release-7-3-2-other}

* I registri web sono stati migliorati: gli avvisi `logonEscalation` vengono ora visualizzati solo per gli utenti con privilegi di amministratore. (NEO-47167)
* Per evitare errori, il flusso di lavoro **Raccolta dati per il servizio Heatmap** (collectDataHeatMapService) ora viene interrotto per impostazione predefinita. (NEO-33959)
* Sono stati implementati diversi miglioramenti per ottimizzare l’utilizzo della CPU per il dashboard delle campagne. (NEO-46417)
* Per evitare arresti anomali, è stato rimosso il metodo JS loadLibraryDebug. (NEO-46968)
* I riferimenti rimanenti alla libreria log4j sono stati rimossi dall’installazione di Campaign su Windows. (NEO-44851)

### Patch {#release-7-3-2-patches}

* È stato risolto un problema che impediva l’utilizzo dell’opzione **Unisci righe selezionate** del flusso di lavoro. (NEO-48488)
* È stato risolto un problema che impediva l’aggiornamento corretto dell’indicatore di consegna **riuscita** quando si utilizzava l’MTA avanzato di Adobe Campaign. (NEO-50462)
* È stato risolto un problema che impediva la riapprovazione durante la reimpostazione dell’approvazione del contenuto in una consegna e-mail. (NEO-44259)
* È stato risolto un problema che poteva impedire la visualizzazione del pulsante **Approvazione della consegna**. (NEO-47547)
* È stato risolto un problema di prestazioni nella scheda HTML di una consegna che poteva verificarsi in caso di un codice HTML di grandi dimensioni. (NEO-47440)
* È stato risolto un problema che interessava gli aggiornamenti dello stato del registro di consegna sull’istanza MID quando l’opzione `FeatureFlag_GZIP_Compression` era abilitata. (NEO-49183)
* È stato risolto un problema che impediva l’invio di notifiche di app mobili iOS da un’istanza di esecuzione durante l’utilizzo dell’autenticazione basata sui token. (NEO-45961)
* È stato risolto un problema relativo al flusso di lavoro **Aggiorna per il recapito messaggi** (deliverabilityUpdate) che si bloccava quando erano presenti troppi broadLog da sincronizzare. (NEO-48287)
* È stato risolto un problema relativo al tipo di evento che bloccava il flusso di lavoro **Sincronizzazione del Centro messaggi** (mcSynch).
* È stato risolto un problema che poteva causare un errore durante l’aggiunta dell’indicatore **Destinatari che hanno aperto** (estimatedRecipientOpen) nei dati aggiuntivi di un’attività del flusso di lavoro **Query**. (NEO-46665)
* È stato risolto un problema relativo al flusso di lavoro **Fatturazione** non riuscito quando i pacchetti Controllo ed Esecuzione del Centro messaggi erano installati nella stessa istanza. (NEO-47674)
* È stato risolto un problema relativo al flusso di lavoro **Fatturazione** non riuscito quando le tabelle con la chiave primaria erano definite come stringa invece di un numero intero. (NEO-46254)
* È stato risolto un problema relativo ai filtri heatmap con il nome del flusso di lavoroa troppo lungo. (NEO-46301)
* È stato risolto un problema introdotto nella versione 7.3.1 sul connettore Snowflake FDA che causava la perdita di record durante l’utilizzo di “unione semplice a 0 o a 1 cardinalità” durante l’arricchimento. (NEO-48737)
* È stato risolto un problema relativo al connettore Snowflake FFDA durante l’utilizzo del parametro di ordinamento in un’attività del flusso di lavoro di **Divisione**. (NEO-45899)
* È stato risolto un problema che poteva impedire agli utenti di salvare la configurazione dell’account esterno. L’account esterno viene ora salvato automaticamente dopo il test di connessione, per i connettori con funzionalità parser (Snowflake e Google BigQuery). (NEO-47636)
* È stato risolto un problema che impediva l’inserimento di un tipo di dati Ora in un’attività del flusso di lavoro **Aggiornamento dei dati** in MSSQL. (NEO-47763)
* È stato risolto un problema che causava l’arresto anomalo del processo MTA quando il fuso orario del motore non era impostato (specifico per MSSQL). (NEO-46619)
* È stato risolto un problema relativo all’importazione di file HTML quando i nodi immagine (img) contenevano URL con campi di personalizzazione. (NEO-48396)
* È stato corretto un errore HTTP 500 durante il tentativo di connessione a un’istanza in cui il nodo `limit` non era configurato nel file serverConf.xml.
* È stato risolto un problema che poteva causare un errore di “Mancata corrispondenza del set di caratteri” durante l’utilizzo di alcune funzioni come `to_nclob` con un database unicode di Oracle in cui NChar non veniva abilitato. (NEO-49361)
* È stato risolto un problema che causava un errore quando un utente con diritti di accesso in lettura nella cartella nmsDeliveryMapping tentava di eseguire una campagna o un flusso di lavoro. (NEO-48230)
* È stato risolto un problema che impediva l’utilizzo della funzione `JSPContext.sqlExecWithOneParam`. (NEO-50066)
* Sono stati corretti diversi errori di reindirizzamento. (NEO-50030)
