---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: ht
source-wordcount: '352'
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

* Ora, quando un modulo web è in stato di **Pubblicazione in sospeso**, non diventa automaticamente disponibile. Per evitare problemi di sicurezza, è necessario pubblicarlo prima che sia **Online** e accessibile tramite l’URL del modulo web in un browser web. [Ulteriori informazioni](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Patch {#release-7-3-5-patches}

* È stato risolto un problema che si verificava durante l’utilizzo di dati da un database Google Big Query e l’aggiornamento di dati in un database di Oracle: tutte le chiavi erano impostate su `0` nella tabella temporanea del flusso di lavoro. (NEO-65091)
* È stato risolto un problema che causava un errore nell’esecuzione di un flusso di lavoro quando due query su un database Google Big Query venivano combinate in un’attività del flusso di lavoro **Unione**. (NEO-63705)
* È stato risolto un problema che richiedeva all’utente di autenticarsi nuovamente facendo clic sul pulsante `Back` in un rapporto sulla campagna. (NEO-65087)
* È stato corretto un errore nel flusso di lavoro di pulizia del database che si verificava quando una consegna veniva eliminata prima delle relative bozze di consegna. (NEO-48114)
* È stato risolto un problema che si verificava durante la connessione alla console client: gli aggiornamenti recenti sulla verifica TLS causavano un errore di connessione. (NEO-50488)
* È stato risolto un problema relativo all’autenticazione proxy HTTP dopo l’aggiornamento di Campaign alla versione 7.3.1. Le richieste HTTP nei flussi di lavoro di Campaign generavano errori con `error 407 – proxy auth required is returned`. (NEO-49624)
* È stato risolto un errore intermittente con la decrittografia GPG nelle attività del flusso di lavoro **Script**. Il messaggio di errore associato era: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

