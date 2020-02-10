---
title: Domande frequenti
seo-title: Domande frequenti
description: Domande frequenti su Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# Domande frequenti sugli sviluppatori {#dev-faq}

Come soluzione aperta, Adobe Campaign è pronto per la personalizzazione e lo sviluppo di applicazioni avanzate.

## Cos&#39;è il modello dati Campaign? {#what-is-the-campaign-data-model}

Il modello di dati concettuali del database Adobe Campaign consiste in un insieme di tabelle integrate e nella relativa interazione. La struttura fisica e logica dei dati trasferiti nell&#39;applicazione è descritta in XML. Obbedisce a una grammatica specifica di Adobe Campaign, denominata schema. Per ulteriori informazioni sugli schemi di Adobe Campaign, [consulta questa sezione](../../configuration/using/about-schema-edition.md).

[Fai clic qui per saperne di più sul modello dati](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)di Campaign.

Le best practice sono elencate [in questo articolo](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).

## Come utilizzare gli schemi di Campaign? {#how-to-work-with-campaign-schemas-}

In Adobe Campaign, gli schemi dati vengono utilizzati per:

* Definire il modo in cui gli oggetti dati all&#39;interno dell&#39;applicazione sono legati alle tabelle di database sottostanti.
* Definire collegamenti tra i diversi oggetti dati all&#39;interno dell&#39;applicazione Campaign.
* Definire e descrivere i singoli campi inclusi in ciascun oggetto.

Leggi le [tabelle e gli schemi per iniziare](../../configuration/using/about-schema-edition.md) a utilizzare lo schema dati, estendere e personalizzare Campaign in base alle tue esigenze.

## Come utilizzare una tabella di destinazione personalizzata? {#how-to-use-a-custom-recipient-table-}

Puoi creare e implementare una tabella di destinatari non standard in Campaign per inviare i tuoi messaggi.

[Fai clic qui per saperne di più](../../configuration/using/about-custom-recipient-table.md)

## Quali sono le best practice per definire le query in Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

L&#39;editor di query di Adobe Campaign è uno strumento potente per esplorare i dati e creare segmenti.

Lo strumento di query Adobe Campaign si trova su più livelli del software: per creare una popolazione target, segmentare i clienti, estrarre e filtrare i registri di tracciamento, creare filtri, ecc.

Puoi eseguire query sul database Campaign utilizzando l&#39;editor query generico. **È accessibile tramite** Strumenti > Editor query generico. menu. Consente di estrarre le informazioni memorizzate in un database e organizzare, raggruppare, ordinare ecc. Ad esempio, l’utente può recuperare i destinatari che hanno fatto clic più di n volte sul collegamento di una newsletter in un determinato periodo di tempo. Questo strumento consente di raccogliere, ordinare e visualizzare i risultati in base alle esigenze. Questo strumento combina tutte le possibilità di query di Adobe Campaign. Ad esempio, consente di creare e salvare filtri con restrizioni. Ciò significa che un filtro utente creato nell&#39;editor di query generico può essere utilizzato nella casella Query di un flusso di lavoro di targeting, ecc.

Le query vengono create utilizzando i campi della tabella selezionata o utilizzando una formula. I principi principali per creare una query nel database Campaign sono descritti [in questa pagina](../../platform/using/about-queries-in-campaign.md).

[Fai clic qui](../../workflow/using/query.md) per scoprire l&#39;editor di query Campaign.

## Come posso importare un pacchetto di dati? {#how-can-i-import-a-data-package-}

Adobe Campaign consente di esportare o importare la configurazione della piattaforma e i dati attraverso un sistema di pacchetti. I pacchetti di dati consentono la visualizzazione delle entità del database Adobe Campaign tramite file in formato XML. Ogni entità contenuta in un pacchetto è rappresentata da tutti i suoi dati.

Il principio dei pacchetti di dati è esportare una configurazione di dati e integrarla in un altro sistema Adobe Campaign.

[Fai clic qui](../../platform/using/working-with-data-packages.md) per scoprire come utilizzare i pacchetti di dati per importare ed esportare configurazioni di Campaign.

## Dove posso trovare l&#39;elenco delle API Campaign Classic? {#where-can-i-find-the-list-of-campaign-classic-apis}

Tutte le API Campaign, inclusa la descrizione completa, sono disponibili in questa documentazione [](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)dedicata.
