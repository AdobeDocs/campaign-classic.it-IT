---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 630a62c5e5c9782c5c55fdebd651493a2d68fc54
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 16%

---

# Ultima versione{#latest-release}

![](../../assets/v7-only.svg)

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni apportati al **versione più recente di Campaign Classic v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Versione 7.2.1 - Build 9346 {#release-7-2-1}

_10 gennaio 2022_

**Miglioramento della sicurezza**

Diversi miglioramenti di sicurezza sono stati apportati agli account FDA:

* I driver ODBC sono ora installati direttamente con Adobe Campaign Third Party. Per installare questi driver non sono più necessari passaggi manuali.
* Quando configuri il tuo account esterno FDA, ora puoi accedere al tuo account di Snowflake utilizzando l’autenticazione con coppia di chiavi per una maggiore sicurezza di autenticazione. [Maggiori informazioni](../../installation/using/configure-fda-snowflake.md)
* Quando configuri il tuo account esterno FDA, ora puoi accedere al tuo account Azure synapse Analytics utilizzando l’identità gestita assegnata dal sistema. [Maggiori informazioni](../../installation/using/configure-fda-synapse.md#azure-external)
* Tutti i riferimenti alla libreria log4j sono stati rimossi da Campaign per garantire la sicurezza ottimale.

**Miglioramenti**

* Connettore Microsoft Dynamics CRM 365

   Sono state applicate correzioni critiche relative all’API web di Microsoft Dynamics Connector:

   * È stato risolto un problema, durante un&#39;importazione attivata da un flusso di lavoro, che causava il salvataggio dei valori null dei campi di tipo stringa come Null invece di valori vuoti.
   * È stato risolto un problema che causava il seguente errore per l’importazione o l’esportazione di dati tramite chiamate API web: &quot;URI non valido: Lo schema URI è troppo lungo&quot;.
   * Sono stati risolti diversi problemi durante l’importazione, da Microsoft Dynamics 365, di dati contenenti campi di ricerca.

* Connettore FDA BigQuery Google

   * Il connettore FDA Google BigQuery è ora disponibile per le distribuzioni in hosting. [Maggiori informazioni](../../installation/using/configure-fda-google-big-query.md)
   * È stato aggiunto il supporto per abilitare le connessioni a un server proxy per il connettore FDA BigQuery Google. Le opzioni proxy richieste possono essere impostate tramite il campo Opzioni nella configurazione dell’account esterno. [Leggi tutto](../../installation/using/configure-fda-google-big-query.md#google-external)

**Altre modifiche**

* In seguito alla loro deprecazione, le attività di azione Microsoft CRM, Salesforce, Oracle CRM On Demand sono state rimosse dall&#39;interfaccia. Per configurare la sincronizzazione dati tra Adobe Campaign e un sistema CRM, puoi utilizzare l’attività del connettore CRM. [Maggiori informazioni](../../workflow/using/crm-connector.md)
* La **[!UICONTROL Encrypted identifier]** è stato aggiunto allo schema visitatore (nms:visitor). Questo campo viene calcolato e deve essere utilizzato per le applicazioni web. Questo si applica quando il canale Line è configurato sull&#39;istanza di mid-sourcing.
* È ora possibile utilizzare le origini dati CRM con **Modificare l’origine dati** attività.
* È stata aggiunta una nuova opzione nel **Gestione degli errori** proprietà delle attività del flusso di lavoro: La **Interrompi in caso di errore** arresta automaticamente il flusso di lavoro. Non potrai riavviarlo successivamente (NEO-29661). [Maggiori informazioni](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Viene ora utilizzata una sequenza dedicata per generare le chiavi primarie per la tabella nmsGroup, che viene utilizzata per creare gruppi statistici di destinatari. In precedenza veniva utilizzata la sequenza xtknownId . (NEO-30832)
* È stato aggiunto il supporto per le operazioni di aggiornamento batch tramite l’attività del connettore di gestione delle relazioni con i clienti.
* Prestazioni migliorate per i tempi di elaborazione della messaggistica transazionale. (NEO-40370)

**Patch**

* È stato risolto un problema che si verificava durante la creazione di una consegna e che causava un errore in **Immagini** della scheda **Tracciamento e immagini** finestra. Ciò si verificava quando si utilizzava una configurazione proxy automatica. (NEO-33260)
* È stato risolto un problema che poteva impedire il caricamento di un file su un server Debian 10 (HTTPS) in modalità sincrona.
* È stato risolto un problema che poteva impedire i record della tabella delle statistiche delle consegne (`nmsDeliveryLogStats`) dall’eliminazione dall’istanza di mid-sourcing durante la pulizia del database dopo l’eliminazione delle consegne correlate. (NEO-31034)
* È stato risolto un problema che impediva l’invio di notifiche di app mobili su iOS durante l’utilizzo dell’autenticazione basata sui token (NEO-38640).
* È stato risolto un problema che poteva causare la visualizzazione di messaggi di errore script durante il tentativo di creazione e configurazione di rapporti (NEO-38393).
* È stato risolto un problema che poteva causare un errore del flusso di lavoro di tracciamento in Oracle a causa di elevati volumi di indicatori di consegna aggiornati simultaneamente (NEO-39653).
* È stato risolto un problema che poteva impedire l’invio di una consegna a causa di un errore che si verificava durante l’esecuzione di una tipologia di controllo (NEO-39833).
* È stato risolto un problema nelle pagine di destinazione che poteva impedire la corretta visualizzazione dei caratteri speciali nelle pagine HTML delle risposte ai sondaggi online (NEO-39438).
* È stato risolto un problema che poteva impedire il funzionamento della console Campaign Classic facendo clic con il pulsante destro del mouse su una delle cartelle nella scheda Esplora risorse (NEO-38884).
* È stato corretto un errore che si verificava quando si utilizzava un modello di consegna creato in precedenza collegato a un account Web Analytics in una nuova consegna in cui la configurazione di Web Analytics era mancante. (NEO-28666)
* È stato risolto un problema che poteva impedire la visualizzazione in anteprima delle consegne mobili collegate a un flusso di lavoro.
* È stato corretto un errore che impediva il reindirizzamento degli URL di tracciamento personalizzati quando era abilitato il meccanismo di firma URL per i collegamenti di tracciamento.
* È stato risolto un problema che poteva causare errori di post aggiornamento a causa di un problema di gestione dell&#39;indice.
* È stato corretto un errore che si verificava durante l’utilizzo dei tipi di dati dei campi di ricerca con Microsoft Dynamics CRM in **Importa** o **Esporta** attività del flusso di lavoro.
* È stato risolto un problema che poteva impedire l’accesso alla console a causa di un problema di configurazione proxy. (NEO-38388)
* È stato risolto un problema di regressione che impediva il funzionamento corretto della funzionalità **Purge folder** (Svuota cartella). (NEO-37459)
* È stato risolto un problema che causava un errore di richiesta errato quando si utilizzavano campi di dati xml con l’account Microsoft Dynamics CRM se il codice xml di riferimento conteneva virgolette doppie.
* È stato risolto un problema che causava la registrazione errata dei problemi di timeout: questi non venivano registrati come errori di rete, ma come problemi di interruzione dello script. Questo problema si verificava nel caso di richieste HTTP incluse nelle attività JavaScript. (NEO-38079)
* È stato risolto un problema a causa del quale venivano restituiti risultati errati nell’esecuzione delle funzioni Amazon Redshift HoursDiff e MinutesDiff durante il tentativo di estrarre il componente “time”.(NEO-31673)
* È stato risolto un problema che impediva la **Clic a caldo** dal caricamento per le consegne a partire dalla build 9182. (NEO-28900)
* È stato corretto un errore che sostituiva il simbolo &amp; in un URL con il riferimento all’entità carattere (`&amp;`) impedisce agli utenti di accedere all’URL collegato a un codice QR. (NEO-28621)
* È stato risolto un problema che creava un nuovo account esterno ogni volta che un utente creava un nuovo flusso di lavoro della campagna e un’attività di consegna collegata a un account Web Analytics. Ciò è stato causato da un ID mancante nell&#39;oggetto di consegna webAnalyticsAccount. (NEO-39691)
* È stato risolto un problema che poteva impedire il funzionamento dell’attività del flusso di lavoro **Read list** (Leggi elenco) se l’elenco era stato identificato nel database con un ID negativo. (NEO-39607)
* È stato risolto un problema con il quale poteva causare il **Mid-sourcing (registri di consegna)** flusso di lavoro per il mancato funzionamento. (NEO-39662)
* È stato risolto un problema che poteva impedire la visualizzazione in anteprima delle consegne e-mail collegate a un flusso di lavoro. (NEO-37840)
* È stato risolto un problema che poteva causare l’eliminazione da parte del flusso di lavoro di pulizia del database di tabelle valide contenenti valori di elenco. (NEO-34911)
* È stato risolto un problema che poteva causare l’arresto anomalo del flusso di lavoro di fatturazione sulle istanze di marketing.
