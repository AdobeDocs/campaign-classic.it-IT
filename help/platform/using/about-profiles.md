---
title: Informazioni sui profili
seo-title: Informazioni sui profili
description: Informazioni sui profili
seo-description: null
page-status-flag: never-activated
uuid: 9a3fcb58-a356-4eee-bc26-c64825de5f99
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 5addada8-0185-488f-9825-83f60981c139
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 16%

---


# Informazioni sui profili{#about-profiles}

I profili (clienti, potenziali clienti, abbonati a newsletter, ecc.) sono centralizzati nel database di Adobe Campaign. Esistono molti possibili meccanismi per l’acquisizione di profili e la creazione di questo database: raccolta on-line tramite moduli web, importazione manuale o automatica di file di testo, replica con database aziendali o altri sistemi di informazioni. Con  Adobe Campaign, puoi includere la cronologia di marketing, le informazioni sugli acquisti, le preferenze, i dati CRM ed eventuali dati PI pertinenti in una vista consolidata per analizzare e intervenire.

In Adobe Campaign, i destinatari sono i profili predefiniti oggetto di targeting per l’invio di consegne (e-mail, SMS, ecc.). Grazie ai dati sui destinatari archiviati nel database, potrai filtrare il target che riceverà una determinata consegna e aggiungere dati di personalizzazione nei contenuti della consegna. Nel database sono presenti altri tipi di profili. Essi sono progettati per diversi utilizzi. Ad esempio, i profili di seed vengono creati per testare le consegne prima che vengano inviate al target finale.

![](assets/do-not-localize/how-to-video.png) [Comprendere il concetto di profili nei video](#create-profiles-video)

## Tipi di profilo {#profile-types}

 Adobe Campaign consente di gestire i profili per l’intero ciclo di vita: creazione, importazione, targeting, tracciamento delle azioni, aggiornamenti ecc.

Ogni profilo corrisponde a una voce del database. Contengono tutte le informazioni necessarie per il targeting, le persone idonee e il tracciamento.

I profili possono essere identificati in base allo spazio di archiviazione. Ciò significa che un profilo può corrispondere: un destinatario, un visitatore, un operatore, un utente iscritto, un potenziale, ecc.

## Profili destinatario {#recipient-profiles}

I destinatari della distribuzione vengono memorizzati nel database come profili contenenti le informazioni ad essi collegate: cognome, nome, indirizzo, iscrizioni, consegne, ecc. Quando create le campagne, potete definire il target delle consegne per una selezione dei profili nella base in base a criteri semplici o avanzati.

Potete anche creare campagne mirate ai destinatari i cui profili sono memorizzati non nel database, ma nei file. Tali consegne sono note come consegne &quot;esterne&quot;. Per ulteriori informazioni su questo tipo di consegna, consulta [questa pagina](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

I metodi principali per creare i profili dei destinatari sono i seguenti:

* ingresso diretto nelle schermate dell&#39;interfaccia grafica,
* importazione di elenchi destinatari,
* raccolta on-line tramite moduli Web.

>[!NOTE]
>
>Per informazioni sulle modalità di importazione di file e moduli Web, fare riferimento a Importazione ed esportazione [generica](../../platform/using/generic-imports-and-exports.md).

## Profili e destinazioni {#profiles-and-targets}

Il **[!UICONTROL Profiles and targets]** collegamento consente di visualizzare i destinatari memorizzati  database Adobe Campaign. Puoi creare un nuovo destinatario, modificare un destinatario esistente e accedere al suo profilo. Per ulteriori informazioni, consulta [questa pagina](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Consente inoltre di accedere a:

* elenchi; consultate [Creazione e gestione di elenchi](../../platform/using/creating-and-managing-lists.md),
* servizi di abbonamento; fare riferimento a [questa pagina](../../delivery/using/managing-subscriptions.md),
* applicazioni web; fare riferimento a [questa pagina](../../web/using/about-web-applications.md),
* importazioni ed esportazioni (posti di lavoro); fare riferimento alle importazioni e alle esportazioni [](../../platform/using/generic-imports-and-exports.md)generiche,
* flussi di lavoro di targeting; fare riferimento a [questa pagina](../../workflow/using/building-a-workflow.md#implementation-steps-).

La pagina dei destinatari consente di eseguire operazioni frequenti sui profili: modifiche, aggiornamenti, aggiunta, eliminazione, ordinamento.

Per manipolazioni di profilo più avanzate, è necessario modificare la struttura  di Adobe Campaign. A tal fine, fate clic sul **[!UICONTROL Explorer]** collegamento nella home page di  Adobe Campaign.

Per impostazione predefinita, i destinatari sono memorizzati nel **[!UICONTROL Profiles and Targets > Recipients]** nodo della struttura ad albero. Puoi creare i destinatari da questa vista, nonché:

* ordinare e filtrare i profili della banca dati; consultate [Opzioni](../../platform/using/filtering-options.md)di filtro,
* spostare, copiare o eliminare profili dal database; vedere [Gestione dei profili](../../platform/using/managing-profiles.md),
* profili di aggiornamento; vedere [Aggiornamento dei dati](../../platform/using/updating-data.md),
* i destinatari delle esportazioni; consultate [Esportazione e importazione di profili](../../platform/using/exporting-and-importing-profiles.md),
* creare gruppi di destinatari; consultate [Creazione e gestione di elenchi](../../platform/using/creating-and-managing-lists.md).

Per accedere a funzionalità e configurazioni avanzate, fai clic sull’ **[!UICONTROL Explorer]** icona .

![](assets/d_ncs_user_interface01.png)

Il layout generale di  Adobe Campaign Explorer viene presentato in [Utilizzo  Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>È inoltre possibile visualizzare una visualizzazione avanzata di questo elenco dalla struttura  Adobe Campaign facendo clic sul **[!UICONTROL Profiles and targets > Recipients]** collegamento. La visualizzazione elenco può essere configurata in base alle proprie esigenze. È possibile aggiungere o eliminare colonne, definire l&#39;ordine delle colonne, ordinare i dati e così via. La configurazione della visualizzazione dell&#39;elenco è descritta in [Utilizzo  Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).
>
>Puoi anche definire le visualizzazioni dei destinatari. Per ulteriori informazioni su questa funzionalità, consultare [Cartelle e viste](../../platform/using/access-management.md#folders-and-views).

## Profili attivi {#active-profiles}

I profili attivi sono i profili conteggiati a scopo di fatturazione.

>[!NOTE]
>
>Se siete ospitati su AWS e utilizzate Campaign Classic dalla build 8931, potete anche monitorare il numero di profili attivi utilizzati sulle istanze direttamente dal Pannello di controllo Campaign. For more on this, refer to the [Control Panel documentation](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
>
>Il conteggio dei profili attivi è disponibile solo per le istanze **di** Marketing. Non è disponibile per le istanze di esecuzione, ovvero per le istanze MID (mid-sourcing) e RT (Message Center / Real-time messaging).

“**Profile**” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead.

La fatturazione riguarda solo i profili **attivi**. Un profilo è considerato attivo se è stato eseguito il targeting o comunicato con il profilo negli ultimi 12 mesi tramite qualsiasi canale.

I profili esclusi durante la preparazione della consegna (regole di tipologia, quarantena) non vengono presi in considerazione. Un profilo di destinazione per più consegne verrà conteggiato una sola volta.

>[!NOTE]
>
>I canali Facebook e Twitter non vengono presi in considerazione.

Potete avere una panoramica del **[!UICONTROL Number of active profiles]** menu Campaign Standard **[!UICONTROL Administration > Campaign Management > Customer metrics]** . Il conteggio effettivo viene eseguito dal flusso di lavoro **[!UICONTROL Number of active billing profiles]****[!UICONTROL billingActiveContactCount]**( [)](../../workflow/using/deliveries.md)tecnico, che viene eseguito ogni giorno e aggiunge i nuovi dati al rapporto esistente per il periodo corrente nel **[!UICONTROL Customer metrics]** menu. Ogni periodo dura 12 mesi.

## Come creare e gestire i profili {#create-profiles-video}

Scopri come accedere ai dati del profilo, ordinare e filtrare i profili e come creare e gestire manualmente i profili.

Questo video spiega anche la conformità di Adobe Campaign Classic alle normative generali sulla protezione dei dati.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

**Vedi anche**

* [Gestione della privacy in Campaign](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html)

* [Definire la popolazione di destinazione](../../delivery/using/define-the-right-audience.md)

* [Creazione di query e dati di segmento nei flussi di lavoro](../../workflow/using/targeting-data.md)

* [Seleziona mapping di destinazione](../../delivery/using/selecting-a-target-mapping.md)

* [Definizione dell&#39;audience - procedure ottimali](../../delivery/using/define-the-right-audience.md)
