---
product: campaign
title: Lista di controllo per sicurezza e privacy
description: Ulteriori informazioni sugli elementi chiave da verificare in materia di sicurezza e privacy
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 7%

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

* **Scripting**: tentare di evitare istruzioni SQL, utilizzare funzioni con parametri anziché concatenare stringhe, evitare l&#39;inserimento di istruzioni SQL aggiungendo le funzioni SQL da utilizzare al inserisco nell&#39;elenco Consentiti di.

* **Proteggere il modello dati**: utilizzare diritti denominati per limitare le azioni dell&#39;operatore, aggiungere filtri di sistema (sysFilter)

* **Aggiungi captchas nelle applicazioni Web**: scopri come aggiungere captchas nelle pagine di destinazione pubbliche e nelle pagine di abbonamento.

[Maggiori informazioni](../../installation/using/scripting-coding-guidelines.md)

## Rete, database e SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Una cosa molto importante da controllare quando si distribuisce un tipo di architettura on-premise è la configurazione di rete.

È inoltre fondamentale seguire la protezione del motore di database.

[Maggiori informazioni](../../installation/using/network-database.md)


## Configurazione del server

<img src="assets/do-not-localize/icon_server.svg" width="60px">

La configurazione deve essere eseguita su tutti i server. I file di configurazione sono di tipo **serverConf.xml** e **`config-<instance>.xml`**. Di seguito sono riportati gli elementi chiave da verificare:

* **Aree di protezione**: configurare le aree di protezione in modo che tengano conto direttamente degli indirizzi IP dei client di un proxy.

* **Protezione caricamento file**: limita i tipi di file che possono essere caricati nel server Adobe Campaign utilizzando un nuovo attributo uploadAllowList. Può essere utilizzato nel file di configurazione del server.

* **Inoltro**: ottimizzare la configurazione dell&#39;inoltro disattivando le regole di inoltro per moduli/applicazioni non utilizzati.

* **Protezione connessione in uscita** e **Restrizione comando** (lato server)

* Puoi anche aggiungere altre intestazioni HTTP, attivare checkIPConsistent, enableTLS, sessionTimeOutSec, ecc. Per ulteriori informazioni, consultare la [documentazione sulla configurazione del server Campaign](../../installation/using/configuring-campaign-server.md) e la [descrizione del file di configurazione del server](../../installation/using/the-server-configuration-file.md).

[Maggiori informazioni](../../installation/using/server-configuration.md)

## Configurazione server web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Durante la configurazione del server web (Apache/IIS) è necessario seguire diverse best practice:

* Disattiva la versione SSL e le crittografie precedenti
* Rimuovere il metodo TRACE
* Rimuovi il banner
* Limita le dimensioni delle query per impedire il caricamento di file importanti

[Maggiori informazioni](../../installation/using/web-server-configuration.md)
