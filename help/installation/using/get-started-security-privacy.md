---
product: campaign
title: Lista di controllo per sicurezza e privacy
description: Ulteriori informazioni sugli elementi chiave da verificare in materia di sicurezza e privacy.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 6%

---

# Lista di controllo per sicurezza e privacy{#get-started-security-privacy}

![](../../assets/v7-only.svg)

Questa sezione ti presenta gli elementi chiave da verificare in materia di sicurezza e privacy. Alcune configurazioni possono essere eseguite solo dai clienti on-premise.

## Privacy

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

La configurazione e l’indurimento della privacy è un elemento chiave dell’ottimizzazione della sicurezza. Seguono alcune best practice per quanto riguarda la privacy:

* Protect dei dati PII del cliente utilizzando HTTPS invece di HTTP
* Utilizza le restrizioni alla visualizzazione PII per proteggere la privacy e impedire l’utilizzo improprio dei dati.
* Assicurati che le password crittografate siano limitate.
* Protect le pagine che possono contenere informazioni personali come pagine mirror, applicazioni web, ecc.

[Ulteriori informazioni](../../installation/using/privacy.md)

## Gestione degli accessi

<img src="assets/do-not-localize/icon_access.svg" width="60px">

La gestione degli accessi è una parte importante dell&#39;irrigidimento della sicurezza. Di seguito sono riportate alcune delle best practice principali:

* Creare un numero sufficiente di gruppi di sicurezza
* Verificare che ogni operatore disponga dei diritti di accesso appropriati
* Evita di utilizzare l&#39;operatore amministratore ed evita di avere troppi operatori nel gruppo di amministrazione

[Ulteriori informazioni](../../installation/using/access-management.md)

## Linee guida per scripting e codifica

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Nello sviluppo in Adobe Campaign (flussi di lavoro, JavaScript, JSSP, ecc.), segui sempre le seguenti linee guida:

* **Scripting**: cercare di evitare istruzioni SQL, utilizzare funzioni parametrizzate invece della concatenazione di stringhe, evitare l&#39;iniezione di SQL aggiungendo le funzioni SQL da utilizzare all&#39;inserire nell&#39;elenco Consentiti.

* **Proteggere il modello** dati: utilizzare diritti denominati per limitare le azioni dell’operatore, aggiungere filtri di sistema (sysFilter)

* **Aggiungi i sottotitoli nelle applicazioni** web: scopri come aggiungere i sottotitoli nelle pagine di destinazione e nelle pagine di abbonamento pubbliche.

[Ulteriori informazioni](../../installation/using/scripting-coding-guidelines.md)

## Rete, database e SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Una cosa molto importante da verificare quando si implementa un tipo di architettura on-premise è la configurazione di rete.

È inoltre fondamentale che tu segua la tua sicurezza del motore di database.

[Ulteriori informazioni](../../installation/using/network-database.md)

>[!CAUTION]
>
>A partire dal 14 luglio 2021, tutti i sistemi client che non supportano il protocollo TLS 1.2 perderanno l’accesso a tutti i prodotti e i servizi di Adobe. Assicurati che tutti i sistemi utente e client siano conformi a TLS 1.2 prima di questa data. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/multi/eol-tls-support.html)

## Configurazione del server

<img src="assets/do-not-localize/icon_server.svg" width="60px">

La configurazione deve essere eseguita su tutti i server. I file di configurazione sono di tipo **serverConf.xml** e **`config-<instance>.xml`**. Ecco gli elementi chiave da verificare:

* **Zone** di sicurezza: Configura le aree di protezione in modo che tengano direttamente conto degli indirizzi IP dei client di un proxy.

* **Protezione** caricamento file: limita i tipi di file che possono essere caricati sul server Adobe Campaign utilizzando un nuovo attributo uploadAllowList . Può essere utilizzato nel file di configurazione del server.

* **Relè**: ottimizza la configurazione del relay disattivando le regole del relay per moduli/applicazioni non utilizzati.

* **Protezione della connessione in uscita** e restrizione  **dei comandi**  (lato server)

* Puoi anche aggiungere intestazioni HTTP aggiuntive, attivare checkIPConsistent, enableTLS, sessionTimeOutSec, ecc. Per ulteriori informazioni, consulta la [documentazione sulla configurazione del server Campaign](../../installation/using/configuring-campaign-server.md) e la [descrizione del file di configurazione del server](../../installation/using/the-server-configuration-file.md) .

[Ulteriori informazioni](../../installation/using/server-configuration.md)

## Configurazione server web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Seguono diverse best practice per configurare il server web (Apache/IIS):

* Disattiva la versione e i codici SSL precedenti
* Rimuovere il metodo TRACE
* Rimuovi il banner
* Limita le dimensioni della query per impedire il caricamento di file importanti

[Ulteriori informazioni](../../installation/using/web-server-configuration.md)
