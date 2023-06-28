---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: f2dc0947a3b1ed17cbc3d88176e7921e80ca1bb5
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 99%

---

# Ultima versione{#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.3.3 - Build 9359 {#release-7-3-3}

[!BADGE Disponibilità generale]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}

>[!CAUTION]
>
>L’aggiornamento della console client è obbligatorio. Scopri come aggiornare la console client in questa [pagina](../../installation/using/installing-the-client-console.md).

_20 marzo 2023_

**Miglioramento della sicurezza**

* Per migliorare la sicurezza, Tomcat è stato aggiornato dalla versione 8.5.81 alla versione 8.5.85. (NEO-56936)

**Miglioramenti**

* Il flusso di lavoro Fatturazione è stato migliorato per ottimizzarne le prestazioni. (NEO-47658)
* Il flusso di lavoro di tracciamento è stato migliorato per ottimizzarne le prestazioni in caso di consegne di dimensioni elevate. (NEO-45064)
* La gestione del tracciamento è stata migliorata per risolvere possibili problemi relativi ai parametri dinamici negli URL. La gestione del tracciamento v3 ora gestisce gli URL di tipo AJAX (con parametri dopo il simbolo “#”) e impedisce agli strumenti di terze parti di modificare gli URL di tracciamento. Per applicare questa modifica, contatta Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Patch**

* È stato risolto un problema che poteva impedire all’istanza di controllo (contesto Messaggistica transazionale) di inviare notifiche push iOS in stato di bozza. (NEO-54713)
* È stato risolto un problema che poteva impedire lo scorrimento nella scheda **Modifica** dell’editor di contenuti digitali (DCE). (NEO-54474)
* È stato risolto un problema che si verificava quando due attività di arricchimento utilizzavano lo stesso identificatore di nome nel collegamento, e questo faceva sì che la seconda utilizzasse i collegamenti della prima. (NEO-48851)

## Versione 7.3.2 - Build 9356 {#release-7-3-2}

[!BADGE Disponibilità limitata]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità limitata"}

_21 novembre 2022_

>[!CAUTION]
>
>L’aggiornamento della console client è obbligatorio. Scopri come aggiornare la console client in questa [pagina](../../installation/using/installing-the-client-console.md).

**Aggiornamenti della compatibilità**

* Adobe Campaign è ora compatibile con PostgreSQL 14. Per ulteriori informazioni, consulta questa [nota tecnica](../../technotes/using/tech-stack-upgrade.md).

* Dopo la fine del ciclo di vita di Microsoft Internet Explorer 11, il motore di rendering HTML per le dashboard nella console client utilizza ora Edge Chromium. (NEO-20741)

Ulteriori informazioni nella [matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Miglioramenti**

* Il connettore Google BigQuery ora supporta completamente i campi booleani. (NEO-49181)
* Ora è possibile configurare la durata di validità dei cookie IMS nella sezione `Configuration for the redirection service` del file serverConf.xml. Questo vale per i seguenti cookie: `uuid230`, `nllastdelid` e `AMCV_` (NEO-42541)
* Nella richiesta “r/test” ora l’IP può essere nascosto impostando `showSourceIP` su false nel nodo di reindirizzamento del file serverConf.xml. [Maggiori informazioni](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Funzioni obsolete**

* Il Social Marketing con Facebook è ora obsoleto. Per pubblicare sui social media o lavorare con Adobe per creare un canale personalizzato, è possibile utilizzare Twitter.
* Il connettore ACS (offerta Prime) è ora obsoleto. È possibile utilizzare le funzionalità di esportazione/importazione di Campaign per estrarre e inserire dati in entrambi i prodotti.

Ulteriori informazioni sono disponibili nella pagina [Funzioni obsolete e rimosse](deprecated-features.md).

**Altre modifiche**

* I registri web sono stati migliorati: gli avvisi `logonEscalation` vengono ora visualizzati solo per gli utenti con privilegi di amministratore. (NEO-47167)
* Per evitare errori, il flusso di lavoro **Raccolta dati per il servizio Heatmap** (collectDataHeatMapService) ora viene interrotto per impostazione predefinita. (NEO-33959)
* Sono stati implementati diversi miglioramenti per ottimizzare l’utilizzo della CPU per il dashboard delle campagne. (NEO-46417)
* Per evitare arresti anomali, è stato rimosso il metodo JS loadLibraryDebug. (NEO-46968)
* I riferimenti rimanenti alla libreria log4j sono stati rimossi dall’installazione di Campaign su Windows. (NEO-44851)

**Patch**

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
