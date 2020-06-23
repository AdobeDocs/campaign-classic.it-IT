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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 972dce4b8429bb5b56fdf32b237384155bcc417a
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 1%

---


# Informazioni sui profili{#about-profiles}

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

Il **[!UICONTROL Profiles and targets]** collegamento consente di visualizzare i destinatari memorizzati nel database  Adobe Campaign. Puoi creare un nuovo destinatario, modificare un destinatario esistente e accedere al suo profilo. For more on this, refer to [this page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Consente inoltre di accedere a:

* elenchi; consultate [Creazione e gestione di elenchi](../../platform/using/creating-and-managing-lists.md),
* servizi di abbonamento; fare riferimento a [questa pagina](../../delivery/using/managing-subscriptions.md),
* applicazioni web; fare riferimento a [questa pagina](../../web/using/about-web-applications.md),
* importazioni ed esportazioni (posti di lavoro); fare riferimento alle importazioni e alle esportazioni [](../../platform/using/generic-imports-and-exports.md)generiche,
* flussi di lavoro di targeting; fare riferimento a [questa pagina](../../workflow/using/building-a-workflow.md#implementation-steps-).

La pagina dei destinatari consente di eseguire operazioni frequenti sui profili: modifiche, aggiornamenti, aggiunta, eliminazione, ordinamento.

Per manipolazioni di profilo più avanzate, è necessario modificare la struttura  Adobi Campaign. A questo scopo, fate clic sul **[!UICONTROL Explorer]** collegamento nella home page del Adobe Campaign .

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
>È inoltre possibile visualizzare una visualizzazione avanzata di questo elenco dalla struttura  Adobi Campaign facendo clic sul **[!UICONTROL Profiles and targets > Recipients]** collegamento. La visualizzazione elenco può essere configurata in base alle proprie esigenze. È possibile aggiungere o eliminare colonne, definire l&#39;ordine delle colonne, ordinare i dati e così via. La configurazione della visualizzazione dell&#39;elenco è descritta in [Utilizzo  utilità di esplorazione](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)Adobi Campaign.
>
>Puoi anche definire le visualizzazioni dei destinatari. Per ulteriori informazioni su questa funzionalità, consultare [Cartelle e viste](../../platform/using/access-management.md#folders-and-views).

## Profili attivi {#active-profiles}

I profili attivi sono i profili conteggiati a scopo di fatturazione.

Per &quot;**profilo**&quot; si intende una registrazione di informazioni (ad esempio: un record nella tabella nmsRecipient o una tabella esterna contenente un ID cookie, un ID cliente, un identificatore mobile o altre informazioni pertinenti a un canale specifico) che rappresenta un cliente finale, un potenziale o un lead.

La fatturazione riguarda solo i profili **attivi**. Un profilo è considerato attivo se è stato eseguito il targeting o comunicato con il profilo negli ultimi 12 mesi tramite qualsiasi canale.

I profili esclusi durante la preparazione della consegna (regole di tipologia, quarantena) non vengono presi in considerazione. Un profilo di destinazione per più consegne verrà conteggiato una sola volta.

>[!NOTE]
>
>I canali Facebook e Twitter non vengono presi in considerazione.

Potete avere una panoramica del **[!UICONTROL Number of active profiles]** menu Campaign Standard **[!UICONTROL Administration > Campaign Management > Customer metrics]** . Il conteggio effettivo viene eseguito dal flusso di lavoro **[!UICONTROL Number of active billing profiles]****[!UICONTROL billingActiveContactCount]**( [)](../../workflow/using/deliveries.md)tecnico, che viene eseguito ogni giorno e aggiunge i nuovi dati al rapporto esistente per il periodo corrente nel **[!UICONTROL Customer metrics]** menu. Ogni periodo dura 12 mesi.

Se siete ospitati su AWS e utilizzate Campaign Classic dalla build 8931, potete anche monitorare il numero di profili attivi utilizzati sulle istanze direttamente dal Pannello di controllo. Per ulteriori informazioni, consulta la documentazione [del Pannello di](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html)controllo.
