---
solution: Campaign Classic
product: campaign
title: Privacy e consenso
description: Ulteriori informazioni su Privacy e Consenso
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Domande frequenti sulla privacy {#privacy-faq}

Di seguito sono riportate alcune delle Domande frequenti sulla privacy e il consenso quando si utilizza  Adobe Campaign.

## Termini chiave {#key-terms}

**Quali sono i termini chiave della Privacy?**

Gli elementi elencati di seguito sono collegati ai termini e concetti chiave relativi a Privacy e Consenso in  Adobe Campaign:

* [Regolamenti sulla gestione della privacy](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Dati personali e personale](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Diritto di accesso e diritto di essere dimenticato](../../platform/using/privacy-management.md#right-access-forgotten)
* [Consenso, mantenimento e ruoli](../../platform/using/privacy-management.md#consent-retention-roles)

## Prontezza delle normative sulla privacy {#privacy-regulations-readiness}

**Qual è  suggerimento di Adobe Campaign di rispettare le più recenti normative sulla privacy?**

 Adobe non fornisce consulenza legale. Devi collaborare con il tuo consulente legale per assicurarti che stiano facendo tutti i passi necessari verso il GDPR, l&#39;CCPA, il PDPA, la LGPD o qualsiasi altra preparazione normativa applicabile.

**Preparazione per le richieste di accesso ed eliminazione dei dati**

* Identificare un processo per ricevere/rispondere alle richieste degli interessati, inclusa la nomina di un punto di contatto per la privacy.

* Rivedete i vari dati cliente memorizzati in  Adobe Campaign e stabilite identificatori univoci (probabilmente ce ne sarà più di uno).

* Determinare un criterio e un processo di convalida/autenticazione per la conferma dell&#39;identità dell&#39;oggetto dati.

* Assicurarsi che la risposta dell&#39;oggetto dati sia di facile comprensione.

**Considera il consenso**

* Elenca e aggiorna, se necessario, tutti i punti di contatto per l’acquisizione dei dati per il GDPR (vale a dire la lingua, il meccanismo per il consenso e i registri di consenso).

* Assicurati che tutte le e-mail di marketing includano i collegamenti per l’annullamento della sottoscrizione.

* Valuta la strategia globale per il marketing delle e-mail per determinare le implementazioni specifiche per le aree geografiche.

**Comprendere i dati**

* Controlla tutte le origini di importazione e acquisizione dei dati in cui i dati scorrono  Adobe Campaign e documenta quali campi vengono utilizzati per le tue attività di marketing.

* Rimuovete eventuali attributi di dati inutilizzati dal database Adobe Campaign .

* Utilizza i dati disponibili in  Adobe Campaign per l&#39;intento che è stato acquisito e offri ai destinatari esperienze personalizzate migliori.

* Rivedete e aggiornate le autorizzazioni di accesso ai dati per garantire che gli utenti di  Adobe Campaign possano sfruttare appieno solo i dati necessari per eseguire le campagne, ma non accedere ad altri dati.

* Assicurati che ciascun utente di  Adobe Campaign disponga dei diritti di accesso appropriati per eseguire le attività richieste, ma non disponga di altri diritti per eseguire altre attività.

## Mantenimento del coinvolgimento degli utenti {#preserve-user-engagement}

**Come possono i Data Controller ottenere il consenso con un impatto minimo sul coinvolgimento degli utenti?**

Nei casi in cui il consenso sarà necessario per determinate attività di marketing, il consenso dei consumatori dovrà essere attivo (ossia nessun silenzio come consenso o caselle pre-controllate), disaggregato e non può essere subordinato all&#39;offerta dei servizi.

Potrebbero addirittura verificarsi casi in cui è necessario aggiornare alcuni assetti per poter continuare a utilizzare i dati in corso di elaborazione.

Invece di considerare questi requisiti di consenso avanzati come un rischio per l&#39;universo commerciabile, gli esperti di marketing potrebbero adottarli come un vero indicatore di coinvolgimento e fedeltà del marchio, oltre alla soddisfazione e alla fiducia dei clienti.

## Gestisci consenso {#manage-consent}

**Come possono i Data Controller gestire il consenso in  Adobe Campaign?**

 Adobe Campaign offre già funzionalità per gestire il consenso a più livelli rispetto a quanto la maggior parte degli esperti di marketing sfrutta tramite campi dati personalizzati o attraverso uno o più servizi.

Gli esperti di marketing devono consultare il proprio consulente legale per informazioni su come procedere e sfruttare le funzionalità già integrate per  Adobe Campaign.

Ad esempio, l&#39;estensione del modello dati in  Adobe Campaign per tenere traccia non solo di chi ha acconsentito, ma anche della marca temporale dell&#39;opt-in, e di un tipo di indicatore che acquisisca l&#39;ambito preciso del consenso.

## Eliminazione dei dati {#data-deletion}

**Quali dati possono essere eliminati dai Data Controller in  Adobe Campaign in risposta a una richiesta del cliente da parte di un Oggetto dati?**

Tutti i dati associati all&#39;oggetto dati verranno eliminati, incluse le tabelle pronte all&#39;uso e personalizzate.

Tecnicamente, tutti i dati collegati all&#39;Oggetto dati con `integrity="own"` verranno eliminati.

In qualità di Data Controller, è possibile personalizzare questa funzione modificando l&#39;integrità dei collegamenti definiti negli schemi di dati (ad esempio, nel caso in cui si disponga di una giustificazione aziendale per non eliminare determinati dati).

**In che modo vengono interessati i rapporti quando i registri di consegna e tracciamento vengono eliminati?**

I report in  Adobe Campaign si basano su indicatori calcolati in base ai dati aggregati ricavati dai log di consegna e tracciamento. Di conseguenza, la rimozione dei singoli file di registro non dovrebbe avere alcun impatto sulle metriche visualizzate nei report.

## Reimportazione di dati {#re-import-data}

**Spesso in  Adobe Campaign, i record vengono caricati da un&#39;origine dati esterna. Devo essere consapevole di poter reimportare i dati in un secondo momento?**

In qualità di Titolare del trattamento dei dati è necessario assicurarsi che, quando si riceve una richiesta di eliminazione, tutti i dati necessari relativi all&#39;Oggetto dati vengano eliminati da tutti i sistemi.

## Accetta di nuovo {#opt-in-again}

**Un oggetto dati, i cui dati sono stati cancellati da  Adobe Campaign, può scegliere di nuovo in un secondo momento?**

È possibile che un soggetto a dati decida nuovamente di partecipare o che venga aggiunto come nuovo destinatario dopo che i suoi dati sono stati cancellati da  Adobe Campaign.

È possibile utilizzare la traccia di controllo per specificare i dettagli relativi all&#39;eliminazione precedente e alla creazione del nuovo destinatario.