---
product: campaign
title: Domande frequenti privacy e consenso
description: Domande frequenti privacy e consenso
feature: Privacy, Privacy Tools
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: ce2c90cd-46d9-4365-8013-5c1273b6c176
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 98%

---

# Domande frequenti sulla privacy {#privacy-faq}



Di seguito sono riportate alcune delle domande frequenti sulla privacy e sul consenso relative all’utilizzo di Adobe Campaign.

## Termini chiave {#key-terms}

### Quali sono i termini chiave della privacy?

Gli elementi elencati di seguito rimandano ai termini e ai concetti chiave relativi alla privacy e al consenso in Adobe Campaign:

* [Normative sulla gestione della privacy](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Dati personali e utenti tipo](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Diritto di accesso e diritto all’oblio](../../platform/using/privacy-management.md#right-access-forgotten)
* [Consenso, conservazione e ruoli](../../platform/using/privacy-management.md#consent-retention-roles)

## Conformità alle normative sulla privacy {#privacy-regulations-readiness}

### Cosa suggerisce Adobe Campaign in merito al rispetto delle normative sulla privacy più recenti?

 Adobe non fornisce consulenza legale. Collabora con il tuo reparto legale per assicurarti che vengano eseguiti tutti i passaggi per garantire il rispetto di GDPR, CCPA, PDPA, LGPD o di qualsiasi altra normativa applicabile.

**Prepararsi per le richieste di accesso ed eliminazione dei dati**

* Identifica un processo per ricevere/rispondere alle richieste degli interessati, inclusa la nomina di un punto di contatto per la privacy.

* Esamina i vari dati dei clienti memorizzati in Adobe Campaign e determina identificatori univoci (probabilmente ce ne sarà più di uno).

* Determina un criterio e un processo di convalida/autenticazione per confermare l’identità dell’interessato.

* Assicurati che la risposta dell’interessato sia chiara e comprensibile.

**Considerare il consenso**

* Elenca e aggiorna, secondo necessità, tutti i punti di contatto per l’acquisizione dei dati per il GDPR (ovvero la lingua, il meccanismo per il consenso e i registri dei consensi).

* Assicurati che tutte le e-mail di marketing includano i collegamenti per annullare l’abbonamento.

* Valuta la strategia globale per l’e-mail marketing per determinare le implementazioni specifiche per le aree geografiche.

**Comprendere i dati**

* Controlla tutte le origini di importazione e acquisizione dei dati da cui i dati fluiscono in Adobe Campaign e documenta quali campi vengono utilizzati per le attività di marketing.

* Rimuovi eventuali attributi di dati inutilizzati dal database Adobe Campaign.

* Utilizza i dati disponibili in Adobe Campaign con l’intento per cui sono stati acquisiti e offri ai destinatari esperienze personalizzate migliorate.

* Esamina e aggiorna le autorizzazioni di accesso ai dati per garantire che gli utenti di Adobe Campaign possano sfruttare pienamente solo i dati necessari per eseguire le campagne, ma non accedere ad altri dati non correlati.

* Assicurati che ciascun utente di Adobe Campaign disponga dei diritti di accesso appropriati per eseguire le attività richieste, ma non disponga dei diritti per eseguire altre attività non correlate.

## Mantenere il coinvolgimento degli utenti {#preserve-user-engagement}

### In che modo i titolari del trattamento possono ottenere il consenso con un impatto minimo sul coinvolgimento degli utenti?

Nei casi in cui si necessita il consenso per determinate attività di marketing, il consenso dei consumatori deve essere attivo (ovvero non può essere espresso in forma di silenzio-assenso o tramite caselle pre-selezionate), disaggregato e non può essere subordinato all’offerta dei servizi.

Possono verificarsi casi in cui è necessario aggiornare alcuni consensi per poter continuare a utilizzare i dati.

Gli addetti al marketing devono accettare questi requisiti di consenso avanzati come un vero indicatore di brand engagement e fedeltà, oltre che di soddisfazione e fiducia dei clienti.

## Gestire il consenso {#manage-consent}

### In che modo i titolari del trattamento gestiscono il consenso in Adobe Campaign?

 Adobe Campaign offre già funzionalità per gestire il consenso a più livelli rispetto a quanto sfruttato dalla maggior parte degli esperti di marketing tramite campi dati personalizzati o attraverso uno o più servizi.

Gli esperti di marketing devono consultare il proprio reparto legale per informazioni su come procedere e sfruttare le funzionalità già integrate in Adobe Campaign.

Ad esempio, estendere il modello dati in Adobe Campaign per monitorare non solo i consensi ricevuti, ma anche la marca temporale del consenso, e un tipo di indicatore che acquisisce l’ambito preciso del consenso.

## Eliminazione dei dati {#data-deletion}

### Quali dati possono essere eliminati dai titolari del trattamento in Adobe Campaign in risposta a una richiesta da parte del cliente interessato?

Tutti i dati associati all’interessato verranno eliminati, incluse le tabelle pronte all’uso e personalizzate.

Tecnicamente, tutti i dati collegati all’interessato con `integrity="own"` verranno eliminati.

In qualità di titolare del trattamento, è possibile personalizzare questo passaggio modificando l’integrità dei collegamenti definiti negli schemi di dati (ad esempio, nel caso in cui si disponga di una giustificazione aziendale per non eliminare determinati dati).

### Che effetto ha sui rapporti l’eliminazione dei registri di consegna e di tracciamento?

I rapporti in Adobe Campaign si basano su indicatori calcolati in base ai dati aggregati ricavati dai registri di consegna e di tracciamento. Di conseguenza, la rimozione dei singoli registri non dovrebbe avere alcun effetto sulle metriche visualizzate nei rapporti.

## Reimportare i dati {#re-import-data}

### Devo prendere in considerazione una possibile reimportazione dei dati in un secondo momento?

Spesso in Adobe Campaign i record vengono caricati da un’origine dati esterna.

In qualità di titolare del trattamento assicurati che, quando ricevi una richiesta di eliminazione, tutti i dati necessari relativi all’interessato vengano eliminati da tutti i sistemi.

## Fornire nuovamente il consenso {#opt-in-again}

### Un interessato i cui dati sono stati eliminati da Adobe Campaign può fornire di nuovo il consenso in un secondo momento?

È possibile che un interessato decida di fornire nuovamente il consenso o che venga aggiunto come nuovo destinatario dopo che i suoi dati sono stati eliminati da Adobe Campaign.

Puoi utilizzare l’audit trail, che illustra quando è avvenuta l’eliminazione precedente e quando è stato creato il nuovo destinatario.
