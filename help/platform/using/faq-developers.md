---
product: campaign
title: Domande comuni
description: Domande frequenti su Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---

# Domande frequenti sugli sviluppatori {#dev-faq}

In quanto soluzione aperta, Adobe Campaign è pronto alla personalizzazione e allo sviluppo di applicazioni avanzate.

## Qual è il modello dati di Campaign? {#what-is-the-campaign-data-model}

Il modello dati concettuale del database di Adobe Campaign è costituito da una serie di tabelle integrate e dalla loro interazione. La struttura fisica e logica dei dati trasferiti nell’applicazione è descritta in XML. Essa obbedisce a una grammatica specifica ad Adobe Campaign, denominata schema. Per ulteriori informazioni sugli schemi di Adobe Campaign, [consulta questa sezione](../../configuration/using/about-schema-edition.md).

[Fai clic qui per ulteriori informazioni sul modello dati di Campaign](https://helpx.adobe.com/it/campaign/kb/acc-datamodel.html).

Le best practice sono elencate [in questo articolo](https://helpx.adobe.com/it/campaign/kb/acc-data-model-best-practices.html).

## Come si utilizzano gli schemi di Campaign? {#how-to-work-with-campaign-schemas-}

In Adobe Campaign, gli schemi di dati vengono utilizzati per:

* Definire il modo in cui gli oggetti dati all’interno dell’applicazione sono legati alle tabelle del database sottostanti.
* Definire i collegamenti tra i diversi oggetti dati all’interno dell’applicazione Campaign.
* Definire e descrivere i singoli campi inclusi in ciascun oggetto.

Consulta le [guide introduttive per le tabelle e gli schemi](../../configuration/using/about-schema-edition.md) per scoprire come utilizzare lo schema dei dati, estendere e personalizzare Campaign in base alle tue esigenze.

## Come si utilizza una tabella dei destinatari personalizzata? {#how-to-use-a-custom-recipient-table-}

Puoi creare e implementare una tabella dei destinatari non standard in Campaign per inviare i tuoi messaggi.

[Fai clic qui per ulteriori informazioni](../../configuration/using/about-custom-recipient-table.md)

## Quali sono le best practice per definire le query in Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

 L’editor di query di Adobe Campaign è uno strumento utile per esplorare i dati e creare segmenti.

Lo strumento di query di Adobe Campaign si trova su più livelli del software: per creare una popolazione target, segmentare i clienti, estrarre e filtrare i log di tracking, creare filtri, ecc.

Puoi eseguire query sul database di Campaign utilizzando l’editor di query generico. Esso è accessibile tramite il menu **Tools > Generic query editor…**. Ti consente di estrarre le informazioni archiviate in un database e organizzarle, raggrupparle, ordinarle, eccetera. Ad esempio, l’utente può recuperare i destinatari che hanno fatto clic più di “n” volte sul collegamento di una newsletter in un determinato periodo di tempo. Questo strumento ti consente di raccogliere, ordinare e visualizzare i risultati in base alle tue esigenze. Questo strumento combina tutte possibilità di query di Adobe Campaign. Ad esempio, ti consente di creare e salvare filtri con restrizioni. Ciò significa che un filtro utente creato nell’editor di query generico può essere utilizzato nella casella di query di un flusso di lavoro di targeting, ecc.

Le query vengono create utilizzando i campi della tabella selezionata o utilizzando una formula. I principi fondamentali per creare una query nel database di Campaign sono descritti [in questa pagina](../../platform/using/about-queries-in-campaign.md).

[Fai clic qui](../../workflow/using/query.md) per scoprire l’editor di query di Campaign.

## Come posso importare un pacchetto di dati? {#how-can-i-import-a-data-package-}

 Adobe Campaign ti consente di esportare o importare la configurazione e i dati della piattaforma attraverso un sistema di pacchetti. I pacchetti di dati consentono la visualizzazione delle entità del database di Adobe Campaign tramite file in formato XML. Ogni entità contenuta in un pacchetto viene rappresentata con tutti i suoi dati.

Il principio dei pacchetti di dati è di esportare una configurazione di dati e integrarla in un altro sistema di Adobe Campaign.

[Fai clic qui](../../platform/using/working-with-data-packages.md) per scoprire come utilizzare i pacchetti di dati per importare ed esportare configurazioni di Campaign.

## Dove posso trovare l’elenco delle API di Campaign Classic? {#where-can-i-find-the-list-of-campaign-classic-apis}

Tutte le API di Campaign, inclusa la loro descrizione completa, sono disponibili in questa [](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)documentazione dedicata.
