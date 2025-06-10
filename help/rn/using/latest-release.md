---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: ht
source-wordcount: '903'
ht-degree: 100%

---

# Ultima versione {#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign Classic v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.4.2  {#release-7-4-2}

### Build 9391 {#build-9391}

[!BADGE Disponibilità limitata]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità limitata"}

_12 maggio 2025_

Questa build include le seguenti correzioni:

* È stato risolto un problema di post-aggiornamento riscontrato nelle configurazioni diverse da Oracle. (NEO-87012)
* È stato risolto un problema di back-end TLS/HTTPS che interessava sia la console client che il server. (NEO-87432)

### Build 9390 {#build-9390}

[!BADGE Disponibilità generale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}

_2 aprile 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**Miglioramenti della sicurezza**

Questa versione include molte correzioni di sicurezza.

La connessione con le soluzioni e le app Adobe tramite l’account esterno di **[!UICONTROL Adobe Experience Cloud]** è stata aggiornata per rafforzare la sicurezza.

**Correzioni principali**

Questa versione include le seguenti correzioni principali:

* Connessione TLS/SMPP: sono stati risolti dei problemi di stabilità SMPP

* Correzioni di Google BigQuery:

   * Sono state corrette le regressioni sui tipi di dati BOOLEANI
   * Sono stati risolti i problemi relativi alle impostazioni proxy
   * Sono state corrette le regressioni sui tipi di dati DATAORA
   * È stato risolto il problema relativo alla stabilità del caricamento in blocco
   * Sono stati migliorati i test interni sulle versioni ODBC
   * È stato risolto un problema relativo ai caratteri speciali nella stringa di connessione
   * È stati rimosso il timeout predefinito (5 min) nelle query Google BigQuery

* Mail Transfer Agent (MTA): è stato risolto elemento secondario MTA orfano bloccato nello stato **[!UICONTROL Start pending]**.


**Altre correzioni**

In questa versione sono stati risolti anche i seguenti problemi:

* È stato risolto un problema a causa del quale l’attività **Caricamento dati (file)** non riusciva a caricare i file nel server<!--after an upgrade to version 8.3.8-->. Ora gli utenti possono caricare correttamente i file senza riscontrare errori di blocco dell’avanzamento o della console. (NEO-47269)

* Sono stati risolti gli errori di segmentazione (fault) in Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Questa correzione impedisce la generazione di file di base e garantisce un funzionamento stabile del server. (NEO-59059)

* È stato risolto un problema di connettività con il database Google BigQuery <!--after upgrading to version 7.3.3 build 9359-->. Gli utenti possono ora testare correttamente le connessioni utilizzando l’account esterno GCP. (NEO-62455)

* È stata migliorata la compatibilità per gli aggiornamenti delle colonne Booleano e Data e ora nelle tabelle di Google BigQuery tramite Federated Data Access (FDA). Questa correzione garantisce la corretta gestione dei tipi di dati durante le operazioni di inserimento/aggiornamento. (NEO-65774)

* È stata risolta una vulnerabilità di inserimento di risorse che consentiva agli hacker di inserire elementi HTML negli endpoint e-mail. Questo miglioramento della sicurezza impedisce l’accesso non autorizzato e i tentativi di phishing. (NEO-66462)

* Sono stati risolti degli errori intermittenti durante l’inserimento di dati nelle tabelle di Google BigQuery a causa di problemi di contenuto HTTP o di codifica dei trasferimenti. Questa correzione assicura flussi di lavoro stabili per il caricamento dei dati. (NEO-66989)

* È stata risolta una vulnerabilità di attraversamento percorso nel metodo `File.list()` all’interno dei flussi di lavoro. Questo miglioramento della sicurezza impedisce l’accesso non autorizzato alla directory e protegge i file sensibili. (NEO-77898)

* È stato risolto un problema a causa del quale i registri di consegna SMS non venivano aggiornati correttamente allo stato “ricevuto su dispositivo mobile”. Questo miglioramento garantisce un reporting accurato sulla consegna. (NEO-78843)

* Sono stati risolti gli errori di accesso in Adobe Campaign Classic durante l’utilizzo di Azure Federated Data Access (FDA). Gli utenti ora possono accedere correttamente tramite la console client. (NEO-79373)

* È stato risolto un arresto anomalo nei flussi di lavoro causato dal metodo `CCurlAzureBlobStorage::UploadStream()`. Questo miglioramento garantisce un’esecuzione stabile del flusso di lavoro. (NEO-79598)

* Sono stati attivati due flag di compilazione critici (`ControlFlowGuard` e `StackProtection`) in Windows per migliorare la sicurezza del prodotto e ridurre i rischi di sfruttamento. (NEO-80145)

* È stato risolto un problema a causa del quale gli stati degli eventi venivano inviati in modo errato quando il broadLog si trovava in uno stato di errore. Questo miglioramento garantisce un reporting accurato degli eventi. (NEO-80245)

* L’aggiornamento di POP3 OAuth e il token di accesso ora vengono salvati nel database e l’errore `Authentication failure: unknown user name or bad password` non viene più visualizzato dopo la scadenza del token di aggiornamento. (NEO-80683)

* L’opzione `XApiKey` è ora utilizzata come valore per l’ID client per la connessione ad Adobe Analytics anziché utilizzare l’ID client dell’account esterno Marketing Cloud (MAC). (NEO-80434)

* È stato risolto un problema a causa del quale gli utenti inMail riscontravano errori di autenticazione dovuti alla scadenza del token. Gli utenti possono ora verificare la connessione e riavviare il server per risolvere problemi simili. (NEO-80683)

* È stata migliorata la funzionalità API di analisi garantendo che tutte le chiamate di analisi utilizzino una chiave API coerente (Campaign1) per l’autenticazione, anche durante il passaggio a un ID client casuale. Questo assicura un tracciamento fluido delle analisi. (NEO-80434)

* È stato migliorato il connettore Federated Data Access (FDA) di BigQuery, consentendo agli utenti di regolare il periodo di timeout per le query. Questo miglioramento impedisce gli errori di timeout durante query con tempi di esecuzione lunghi. (NEO-81222)

* Il processo di aggiornamento della versione di Campaign <!--7.4.1--> è stato aggiornato per includere le dipendenze richieste. Questo miglioramento semplifica il processo di aggiornamento per gli utenti. (NEO-81433)

* È stato risolto un problema di arresto anomalo della console che si verificava con l’utilizzo di un flusso di lavoro secondario in combinazione con un campo `enum`. Questo miglioramento garantisce un’esecuzione stabile del flusso di lavoro. (NEO-81864)

* È stato risolto un problema a causa del quale i processi secondari MTA risultavano bloccati, bloccando gli slot di consegna. Questa correzione assicura operazioni di consegna fluida delle comunicazioni push e WhatsApp. (NEO-82351)

* È stato risolto un problema che causava il blocco delle consegne nella personalizzazione in sospeso a causa di attività di consegna messe in pausa. Questo miglioramento garantisce l’esecuzione corretta della consegna. (NEO-82781)

* È stata migliorata la funzionalità di accesso IMS sfruttando l’endpoint CampaignIO per l’autenticazione. Questo miglioramento semplifica il processo di accesso. (NEO-82838)

* Sono stati rivisti gli errori di timeout di Federated Data Access (FDA) di Google BigQuery per garantire la stabilità dell’esecuzione delle query dopo l’implementazione della correzione rapida. (NEO-82923)

* È stato risolto un problema di spazio durante il caricamento di volumi di dati di grandi dimensioni nelle tabelle Teradata. Questo miglioramento garantisce la stabilità delle operazioni di caricamento dei dati. (NEO-83252)

* È stato risolto un problema per cui le query GCP non riuscivano a causa di confronti di data e marca temporale non corrispondenti <!--after upgrading to version 9383-->. Questo miglioramento garantisce la compatibilità delle query. (NEO-83826)

* Sono stati risolti gli errori di consegna causati dalla ripresa delle attività di consegna messe in pausa. Questa correzione garantisce l’esecuzione corretta della consegna. (NEO-83809)

* Sono stati risolti gli errori di autenticazione con il connettore Federated Data Access (FDA) di Snowflake durante l’utilizzo dell’autenticazione con chiave privata. Questo miglioramento garantisce connessioni corrette al database. (NEO-84024)

* Sono state implementate modifiche di watchdog per risolvere il blocco degli slot secondari MTA causato da processi bloccati. Questo miglioramento garantisce operazioni di consegna fluide. (NEO-84553)

* Controlli di attesa Javascript incrementati per risolvere il blocco degli slot secondari MTA causato da processi in stato operativo. Questa correzione garantisce la stabilità delle operazioni di consegna. (NEO-85150)

