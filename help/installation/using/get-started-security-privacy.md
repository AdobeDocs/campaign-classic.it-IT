---
product: campaign
title: Lista di controllo per sicurezza e privacy
description: Ulteriori informazioni sugli elementi chiave da verificare in materia di sicurezza e privacy
feature: Installation, Privacy, Access Management, Privacy Tools
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 8%

---

# Lista di controllo per sicurezza e privacy{#get-started-security-privacy}



Questa sezione ti presenterà gli elementi chiave da verificare in materia di sicurezza e privacy. Alcune configurazioni possono essere eseguite solo da clienti on-premise.

## Privacy

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

La configurazione e l’irrigidimento della privacy sono un elemento chiave dell’ottimizzazione della sicurezza. Di seguito sono riportate alcune best practice da seguire relative alla privacy:

* Protect le informazioni personali dei clienti utilizzando HTTPS anziché HTTP
* Utilizza la restrizione della visualizzazione PII per proteggere la privacy e impedire l’utilizzo improprio dei dati.
* Verificare che le password crittografate siano soggette a restrizioni.
* Protect le pagine che potrebbero contenere informazioni personali come pagine mirror, applicazioni web, ecc.

[Maggiori informazioni](../../installation/using/privacy.md)

## Gestione degli accessi

<img src="assets/do-not-localize/icon_access.svg" width="60px">

La gestione degli accessi è una parte importante della protezione avanzata. Di seguito sono riportate alcune delle best practice principali:

* Creare un numero sufficiente di gruppi di sicurezza
* Verifica che ogni operatore disponga dei diritti di accesso appropriati
* Evita di utilizzare l’operatore admin ed evita di avere troppi operatori nel gruppo admin

[Maggiori informazioni](../../installation/using/access-management.md)

## Linee guida per scripting e codifica

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Durante lo sviluppo in Adobe Campaign (flussi di lavoro, JavaScript, JSSP, ecc.), segui sempre le seguenti linee guida:

* **Scripting**: prova ad evitare le istruzioni SQL, utilizza funzioni con parametri invece della concatenazione di stringhe, evita SQL injection aggiungendo le funzioni SQL da utilizzare al inserisco nell&#39;elenco Consentiti di.

* **Proteggere il modello dati**: utilizzare diritti denominati per limitare le azioni dell’operatore, aggiungere filtri di sistema (sysFilter)

* **Aggiungere captchas nelle applicazioni web**: scopri come aggiungere i captcha nelle pagine di destinazione e nelle pagine di abbonamento pubbliche.

[Maggiori informazioni](../../installation/using/scripting-coding-guidelines.md)

## Rete, database e SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Una cosa molto importante da controllare quando si distribuisce un tipo di architettura on-premise è la configurazione di rete.

È inoltre fondamentale seguire la protezione del motore di database.

[Maggiori informazioni](../../installation/using/network-database.md)

>[!CAUTION]
>
>A partire dal 14 luglio 2021, i sistemi client che non supportano il protocollo TLS 1.2 perderanno l’accesso a tutti i prodotti e servizi Adobe. Assicurati che tutti i sistemi utente e client siano conformi a TLS 1.2 prima di questa data. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/multi/eol-tls-support.html)

## Configurazione del server

<img src="assets/do-not-localize/icon_server.svg" width="60px">

La configurazione deve essere eseguita su tutti i server. I file di configurazione sono di tipo **serverConf.xml** e **`config-<instance>.xml`**. Di seguito sono riportati gli elementi chiave da verificare:

* **Aree di protezione**: configura le aree di sicurezza in modo che tengano direttamente conto degli indirizzi IP dei client di un proxy.

* **Protezione caricamento file**: limita i tipi di file che possono essere caricati sul server Adobe Campaign utilizzando un nuovo attributo uploadAllowList. Può essere utilizzato nel file di configurazione del server.

* **Inoltro**: regola accuratamente la configurazione dell’inoltro disattivando le regole di inoltro per moduli/applicazioni non utilizzati.

* **Protezione delle connessioni in uscita** e **Restrizione comando** (lato server)

* Puoi anche aggiungere altre intestazioni HTTP, attivare checkIPConsistent, enableTLS, sessionTimeOutSec, ecc. Consulta la sezione [Documentazione sulla configurazione del server Campaign](../../installation/using/configuring-campaign-server.md) e [Descrizione del file di configurazione del server](../../installation/using/the-server-configuration-file.md) per ulteriori informazioni.

[Maggiori informazioni](../../installation/using/server-configuration.md)

## Configurazione server web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Durante la configurazione del server web (Apache/IIS) è necessario seguire diverse best practice:

* Disattiva la versione SSL e le crittografie precedenti
* Rimuovere il metodo TRACE
* Rimuovi il banner
* Limita le dimensioni delle query per impedire il caricamento di file importanti

[Maggiori informazioni](../../installation/using/web-server-configuration.md)
