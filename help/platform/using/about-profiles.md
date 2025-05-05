---
product: campaign
title: Introduzione ai profili
description: Utilizzare i profili in Adobe Campaign
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 17%

---

# Introduzione ai profili{#about-profiles}



I profili sono centralizzati nel database di Adobe Campaign. Esistono molti possibili meccanismi per l’acquisizione di profili e la creazione di questo database: raccolta on-line tramite moduli web, importazione manuale o automatica di file di testo, replica con database aziendali o altri sistemi di informazioni. Con Adobe Campaign, puoi incorporare la cronologia di marketing, le informazioni di acquisto, le preferenze, i dati di gestione delle relazioni con i clienti ed eventuali dati PI rilevanti in una visualizzazione consolidata per analizzare e intraprendere azioni.

&quot;**Profilo**&quot; indica un record di informazioni (ad esempio un record nella tabella nmsRecipient o una tabella esterna contenente un ID cookie, un ID cliente, un identificatore mobile o altre informazioni relative a un canale specifico) che rappresenta un cliente finale, un potenziale cliente o un lead.

In Adobe Campaign, i destinatari sono i profili target predefiniti per l’invio di consegne (e-mail, SMS, ecc). I dati dei destinatari memorizzati nel database consentono di filtrare il target che riceverà una determinata consegna e di aggiungere dati di personalizzazione al contenuto della consegna. Nel database sono presenti altri tipi di profili. Essi sono progettati per diversi utilizzi. Ad esempio, i profili di seed vengono creati per testare le consegne prima che vengano inviate al target finale.

![](assets/do-not-localize/how-to-video.png) [Comprendere il concetto di profili nel video](#create-profiles-video)

## Tipi di profilo {#profile-types}

Adobe Campaign consente di gestire i profili durante l’intero ciclo di vita: creazione, importazione, targeting, tracciamento delle azioni, aggiornamenti, ecc.

Ogni profilo corrisponde a una voce del database. Contengono tutte le informazioni necessarie per il targeting, la qualifica e il tracciamento dei singoli utenti.

I profili possono essere identificati in base allo spazio di archiviazione. Ciò significa che un profilo può corrispondere a: un destinatario, un visitatore, un operatore, un abbonato, un potenziale cliente, ecc.

## Profili dei destinatari {#recipient-profiles}

I destinatari della consegna vengono memorizzati nel database come profili contenenti le informazioni ad essi collegate: cognome, nome, indirizzo, abbonamenti, consegne, ecc. Quando crei delle campagne, puoi definire il target delle consegne per una selezione di profili nella base in base a criteri semplici o avanzati.

Puoi anche creare campagne destinate a destinatari i cui profili sono memorizzati non nel database, ma in file. Queste sono note come consegne &quot;esterne&quot;. Per ulteriori informazioni su questo tipo di consegna, consulta [questa pagina](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

I metodi principali per la creazione dei profili dei destinatari sono i seguenti:

* ingresso diretto nelle schermate dell’interfaccia grafica,
* importazione di elenchi di destinatari,
* raccolta in linea tramite moduli web.

>[!NOTE]
>
>Per informazioni sull&#39;importazione di file e moduli Web, vedere [Importazioni ed esportazioni generiche](../../platform/using/get-started-data-import-export.md).

## Profili e destinazioni {#profiles-and-targets}

Il collegamento **[!UICONTROL Profiles and targets]** consente di visualizzare i destinatari memorizzati nel database di Adobe Campaign. Puoi creare un nuovo destinatario, modificarne uno esistente e accedere al suo profilo. Per ulteriori informazioni, consulta [questa pagina](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Consente inoltre di accedere a:

* elenchi - [Ulteriori informazioni](../../platform/using/creating-and-managing-lists.md)
* servizi di abbonamento - [Ulteriori informazioni](../../delivery/using/managing-subscriptions.md)
* applicazioni Web - [Ulteriori informazioni](../../web/using/about-web-applications.md)
* importazioni ed esportazioni (processi) - [Ulteriori informazioni](../../platform/using/about-generic-imports-exports.md)
* flussi di lavoro di targeting - [Ulteriori informazioni](../../workflow/using/building-a-workflow.md#implementation-steps-)

La pagina dei destinatari consente di eseguire operazioni frequenti sui profili: modifiche, aggiornamenti, aggiunte, eliminazioni, ordinamenti.

Per manipolazioni di profilo più avanzate, devi modificare la struttura di Adobe Campaign. A tale scopo, fare clic sul collegamento **[!UICONTROL Explorer]** nella home page di Adobe Campaign.

Per impostazione predefinita, i destinatari sono archiviati nel nodo **[!UICONTROL Profiles and Targets > Recipients]** della struttura. Puoi creare i destinatari da questa vista, nonché:

* ordinare e filtrare i profili del database - [Ulteriori informazioni](../../platform/using/filtering-options.md)
* sposta, copia o elimina profili dal database - [Ulteriori informazioni](../../platform/using/managing-profiles.md),
* aggiorna profili - [Ulteriori informazioni](../../platform/using/updating-data.md)
* esporta destinatari - [Ulteriori informazioni](../../platform/using/exporting-and-importing-profiles.md)
* crea gruppi di destinatari - [Ulteriori informazioni](../../platform/using/creating-and-managing-lists.md)

Per accedere a configurazioni e funzionalità avanzate, è necessario fare clic sull&#39;icona **[!UICONTROL Explorer]**.

![](assets/d_ncs_user_interface01.png)

Il layout generale di Adobe Campaign Explorer è presentato in [questa pagina](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>È inoltre possibile visualizzare una visualizzazione avanzata dell&#39;elenco dalla struttura Adobe Campaign facendo clic sul collegamento **[!UICONTROL Profiles and targets > Recipients]**. È possibile configurare la visualizzazione dell&#39;elenco in base alle proprie esigenze. Puoi aggiungere o eliminare colonne, definire l’ordine delle colonne, ordinare i dati e così via. La configurazione della visualizzazione dell&#39;elenco è descritta in [questa pagina](../../platform/using/adobe-campaign-ui-lists.md).
>
>Puoi anche definire le visualizzazioni dei destinatari. Per ulteriori informazioni su questa funzionalità, consultare [questa sezione](../../platform/using/access-management-folders.md).

## Profili attivi {#active-profiles}

Un profilo attivo è un profilo con cui il cliente ha tentato di comunicare negli ultimi 12 mesi tramite qualsiasi canale.

In base al contratto, a ciascuna istanza di Campaign viene fornito un numero specifico di profili attivi conteggiati a scopo di fatturazione. Fai riferimento al contratto più recente per informazioni sul numero di profili attivi acquistati. Ulteriori informazioni sono disponibili nella [descrizione del prodotto Adobe Campaign](https://helpx.adobe.com/it/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Puoi monitorare il numero di profili attivi nell’istanza direttamente dal Pannello di controllo Campaign Campaign. Per ulteriori informazioni, consulta la [documentazione del Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=it){target="_blank"}.

Si applicano le seguenti protezioni e limitazioni:

* Un profilo che è stato oggetto di targeting per diverse consegne viene conteggiato una sola volta.
* I profili target nel contesto di Social marketing su X (Twitter) o Facebook non vengono considerati come profili attivi.
* Il numero di profili attivi è disponibile solo per **istanze Marketing**. Non è disponibile per le istanze di esecuzione, ovvero per le istanze MID (mid sourcing) e RT (Message Center / Real-time messaging [Centro messaggi/Messaggistica in tempo reale]).
* Il conteggio si basa sulla chiave primaria del destinatario. Di conseguenza, se un profilo è presente in due diverse tabelle dei destinatari, può essere conteggiato due volte come profilo attivo.


## Video tutorial {#create-profiles-video}

Scopri come accedere ai dati, ordinare e filtrare i profili e come crearli e gestirli manualmente.

Questo video illustra inoltre la conformità di Adobe Campaign Classic con le normative generali sulla protezione dei dati.

>[!VIDEO](https://video.tv.adobe.com/v/326756?quality=12&captions=ita)

Ulteriori video dimostrativi di Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).

**Vedi anche**

* [Gestione della privacy in Campaign](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html)

* [Creare query e dati dei segmenti nei flussi di lavoro](../../workflow/using/targeting-data.md)

* [Seleziona mappatura target](../../delivery/using/steps-defining-the-target-population.md#select-a-target-mapping)
