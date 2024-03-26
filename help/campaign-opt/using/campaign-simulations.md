---
product: campaign
title: Simulazioni delle campagne
description: Introduzione alle simulazioni di Campaign
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 1%

---

# Simulazioni delle campagne{#campaign-simulations}

## Informazioni sulle simulazioni {#about-simulations}

L’ottimizzazione di Campaign consente di testare l’efficienza di un piano di campagna utilizzando simulazioni. Questo consente di misurare il potenziale successo di una campagna: ricavi generati, volume target in base alle regole di tipologia applicate, ecc.

La simulazione consente di monitorare e confrontare l’impatto delle consegne.

>[!NOTE]
>
>Le consegne preparate in modalità di test non hanno alcun impatto l’una sull’altra, ad esempio durante la valutazione di una campagna nel marketing distribuito o finché le consegne non sono pianificate nel calendario provvisorio.\
>Ciò significa che le regole di pressione e capacità si applicano solo alle consegne in **[!UICONTROL Target estimation and message personalization]** modalità. Consegne in **[!UICONTROL Estimation and approval of the provisional target]** e in **[!UICONTROL Target evaluation]** non vengono prese in considerazione.\
>La modalità di consegna viene scelta in **[!UICONTROL Typology]** scheda secondaria delle proprietà di consegna.

![](assets/simu_campaign_select_delivery_mode.png)

## Impostare una simulazione {#setting-up-a-simulation}

### Creare una simulazione {#creating-a-simulation}

Per creare una simulazione, attieniti alla seguente procedura:

1. Apri **[!UICONTROL Campaigns]** , fare clic sulla scheda **[!UICONTROL More]** collegamento all&#39;interno del **[!UICONTROL Create]** e seleziona la **[!UICONTROL Simulation]** opzione.

   ![](assets/simu_campaign_opti_01.png)

1. Immettere il modello e il nome della simulazione. Clic **[!UICONTROL Save]** per creare la simulazione.

   ![](assets/simu_campaign_opti_02.png)

1. Fai clic su **[!UICONTROL Edit]** per configurarlo.

   ![](assets/simu_campaign_opti_edit.png)

1. In **[!UICONTROL Scope]** , specifica le consegne da considerare per questa simulazione. A questo scopo, fai clic su **[!UICONTROL Add]** e specifica la modalità di selezione della consegna da considerare.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Puoi selezionare ciascuna consegna singolarmente oppure ordinarle per campagna, programma o piano.

   >[!NOTE]
   >
   >Se selezioni le consegne tramite un piano, un programma o una campagna, Adobe Campaign può aggiornare automaticamente l’elenco delle consegne da considerare ogni volta che viene avviata una simulazione. A questo scopo, seleziona la **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** opzione.
   >  
   >In caso contrario, non verranno prese in considerazione le consegne non disponibili nel piano, nel programma o nella campagna al momento della creazione della simulazione: le consegne aggiunte successivamente verranno ignorate.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Selezionare gli elementi da includere nell&#39;ambito di simulazione. Se necessario, selezionare più elementi utilizzando i tasti MAIUSC e CTRL.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Clic **[!UICONTROL Finish]** per approvare la selezione.

   Puoi combinare manualmente le consegne selezionate e le consegne appartenenti a piani, programmi o campagne.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Se necessario, puoi utilizzare una condizione dinamica tramite **[!UICONTROL Edit the dynamic condition...]** collegamento.

   Clic **[!UICONTROL Save]** per approvare questa configurazione.

   >[!NOTE]
   >
   >Nel calcolo delle simulazioni vengono prese in considerazione solo le consegne il cui target è stato calcolato (stati: **Target pronto** o **Pronto per la consegna**).

1. In **[!UICONTROL Calculations]** , seleziona una dimensione di analisi come, ad esempio, lo schema del destinatario.

   ![](assets/simu_campaign_opti_dimension.png)

1. È quindi possibile aggiungere espressioni.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Impostazioni di esecuzione {#execution-settings}

Il **[!UICONTROL General]** scheda della simulazione consente di immettere le impostazioni di esecuzione:

* Il **[!UICONTROL Schedule execution for down-time]** L&#39;opzione posticipa l&#39;avvio della simulazione a un periodo di tempo meno occupato, in base al livello di priorità scelto. Le simulazioni utilizzano risorse di database significative. Per questo motivo, ad esempio, è necessario pianificare l&#39;esecuzione di simulazioni non urgenti di notte.
* Il **[!UICONTROL Priority]** è il livello applicato alla simulazione per ritardarne l’attivazione.
* **[!UICONTROL Save SQL queries in the log]**. I registri SQL consentono di diagnosticare una simulazione se termina con errori. Possono anche aiutarti a scoprire perché una simulazione è troppo lenta. Questi messaggi saranno visibili dopo la simulazione nella **[!UICONTROL SQL logs]** scheda secondaria della scheda **[!UICONTROL Audit]** scheda.

## Eseguire una simulazione {#executing-a-simulation}

### Avvia una simulazione {#starting-a-simulation}

Una volta definito l’ambito di simulazione, puoi eseguirlo.

A questo scopo, apri il dashboard di simulazione e fai clic su **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

Al termine dell’esecuzione, apri la simulazione e fai clic su **[!UICONTROL Results]** per visualizzare i target calcolati per ciascuna consegna.

![](assets/simu_campaign_opti_results.png)

1. Il **[!UICONTROL Deliveries]** nella scheda secondaria sono elencate tutte le consegne prese in considerazione dalla simulazione. Mostra due conteggi:

   * Il **[!UICONTROL Initial count]** è il target calcolato durante la stima nella consegna.
   * Il **[!UICONTROL Final count]** è il numero di destinatari conteggiati dopo la simulazione.

     La differenza tra i conteggi iniziali e finali riflette l’applicazione delle varie regole o filtri configurati prima della simulazione.

     Per ulteriori informazioni su questo calcolo, modifica **[!UICONTROL Exclusions]** scheda secondaria.

1. Il **[!UICONTROL Exclusions]** scheda secondaria consente di visualizzare il raggruppamento di esclusione.

   ![](assets/simu_campaign_opti_14.png)

1. Il **[!UICONTROL Alerts]** scheda secondaria raggruppa tutti i messaggi di avviso generati durante la simulazione. I messaggi di avviso possono essere inviati in caso di sovraccarico di capacità (ad esempio, se il numero di destinatari supera la capacità impostata).
1. Il **[!UICONTROL Exploration of the exclusions]** scheda secondaria consente di creare una tabella di analisi dei risultati. L’utente deve indicare le variabili negli assi delle ascisse/ordinate.

   Per un esempio di creazione di tabelle di analisi, fare riferimento alla fine di [Esplorazione dei risultati](#exploring-results).

### Visualizza risultati {#viewing-results}

#### Audit {#audit}

Il **[!UICONTROL Audit]** Questa scheda ti consente di monitorare l’esecuzione della simulazione. Il **[!UICONTROL SQL Logs]** scheda secondaria è utile per gli utenti esperti. Elenca i registri di esecuzione in formato SQL. Questi registri vengono visualizzati solo se **[!UICONTROL Save SQL queries in the log]** è stata selezionata in **[!UICONTROL General]** prima dell’esecuzione della simulazione.

![](assets/simu_campaign_opti_11.png)

#### Esplora i risultati {#exploring-results}

Il **[!UICONTROL Exploration of the exclusions]** scheda secondaria consente di analizzare i dati risultanti da una simulazione.

L’analisi descrittiva è descritta in [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Risultati di una simulazione {#results-of-a-simulation}

Gli indicatori nel **[!UICONTROL Log]** e **[!UICONTROL Results]** Le schede forniscono una prima panoramica dei risultati della simulazione. Per una visualizzazione più dettagliata dei risultati, aprire **[!UICONTROL Reports]** scheda.

### Rapporti {#reports}

Per analizzare il risultato di una simulazione, modificane i rapporti: mostrano esclusioni e cause.

Per impostazione predefinita, vengono forniti i seguenti rapporti:

* **[!UICONTROL Detail of simulation exclusions]** : questo rapporto fornisce un grafico dettagliato delle cause di esclusione per tutte le consegne interessate.
* **[!UICONTROL Simulation summary]** : questo rapporto mostra le popolazioni escluse dalla simulazione in tutte le varie consegne.
* **[!UICONTROL Summary of exclusions linked to the simulation]** : questo rapporto mostra un grafico delle esclusioni causate dalla simulazione insieme alla regola di tipologia applicata e un grafico che mostra il rapporto di esclusione per regola.

>[!NOTE]
>
>Puoi creare nuovi rapporti e aggiungerli a quelli offerti. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Per accedere ai rapporti, fai clic su **[!UICONTROL Reports]** collegamento della simulazione target tramite la relativa dashboard.

![](assets/campaign_opt_reporting_edit_from_board.png)

È inoltre possibile modificare i rapporti utilizzando **[!UICONTROL Reports]** accessibile dal dashboard di simulazione.

### Confrontare simulazioni {#comparing-simulations-}

Ogni volta che viene eseguita una simulazione, il risultato sostituisce qualsiasi risultato precedente: non è possibile visualizzare e confrontare i risultati da un’esecuzione all’altra.

Per confrontare i risultati, devi utilizzare i rapporti. In effetti, Adobe Campaign ti consente di salvare una cronologia del rapporto per visualizzarla nuovamente in un secondo momento. Questa cronologia viene salvata durante il ciclo di vita delle simulazioni.

**Esempio:**

1. Creare una simulazione su una consegna in base alla tipologia **A** viene applicato a.
1. In **[!UICONTROL Reports]** , modifica uno dei rapporti disponibili, ad esempio **[!UICONTROL Detail of simulation exclusions]** ad esempio.
1. Nella sezione in alto a destra del rapporto, fai clic sull’icona per creare una nuova cronologia.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Chiudere la simulazione e modificare la configurazione della tipologia **A**.
1. Esegui nuovamente la simulazione e confronta il risultato con quello visualizzato nel rapporto per il quale è stata creata una cronologia.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Puoi salvare tutte le cronologie dei rapporti necessarie.

### Assi di reporting {#reporting-axes}

Il **[!UICONTROL Calculations]** consente di definire gli assi di reporting sul target. Questi assi verranno utilizzati durante l&#39;analisi dei risultati (fare riferimento a [Esplorazione dei risultati](#exploring-results)).

>[!NOTE]
>
>È consigliabile definire gli assi di calcolo nei modelli di simulazione anziché singolarmente per ogni simulazione.\
>I modelli di simulazione vengono salvati in **[!UICONTROL Resources > Templates > Simulation templates]** della struttura Adobe Campaign.

**Esempio:**

Nell’esempio seguente, vogliamo creare un asse di reporting aggiuntivo basato sullo stato dei destinatari (&quot;Cliente&quot;, &quot;Potenziale&quot; o nessuno).

1. Per definire un asse di reporting, selezionare la tabella contenente le informazioni da elaborare nel **[!UICONTROL Analysis dimension]** campo. Queste informazioni sono obbligatorie.
1. In questo caso, desideri selezionare il campo Segmento della tabella dei destinatari.

   ![](assets/simu_campaign_opti_09.png)

1. Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Generate target overlap statistics]** consente di recuperare tutte le statistiche di sovrapposizione nel rapporto di simulazione. Le sovrapposizioni sono destinatari di almeno due consegne nell’ambito di una simulazione.

     >[!IMPORTANT]
     >
     >Selezionando questa opzione si aumenta notevolmente il tempo di esecuzione della simulazione.

   * **[!UICONTROL Keep the simulation work table]** consente di conservare le tracce della simulazione.

     >[!IMPORTANT]
     >
     >Il salvataggio automatico di queste tabelle richiede una capacità di archiviazione significativa: assicurati che il database sia sufficientemente grande.

Quando vengono visualizzati i risultati della simulazione, le informazioni sull’espressione selezionata vengono visualizzate nel **[!UICONTROL Overlaps]** scheda secondaria.

Le sovrapposizioni del target di consegna indicano i destinatari target in almeno due consegne di una simulazione.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Questa scheda secondaria viene visualizzata solo se **[!UICONTROL Generate target recovery statistics]** l&#39;opzione è stata abilitata.

Le informazioni sugli assi di reporting possono essere elaborate nei rapporti di analisi di esclusione creati in **[!UICONTROL Exploring exclusions]** scheda secondaria. Per ulteriori informazioni, consulta [Esplorazione dei risultati](#exploring-results).
