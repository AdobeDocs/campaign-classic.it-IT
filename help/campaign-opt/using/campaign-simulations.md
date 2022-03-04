---
product: campaign
title: Simulazioni delle campagne
description: Guida introduttiva alle simulazioni di Campaign
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1245'
ht-degree: 1%

---

# Simulazioni delle campagne{#campaign-simulations}

![](../../assets/common.svg)

## Informazioni sulle simulazioni {#about-simulations}

L’ottimizzazione per le campagne consente di verificare l’efficienza di un piano di campagna utilizzando delle simulazioni. Questo consente di misurare il potenziale successo di una campagna: ricavi generati, volume target in base alle regole di tipologia applicate, ecc.

La simulazione ti consente di monitorare e confrontare l’impatto delle consegne.

>[!NOTE]
>
>Le consegne preparate in modalità di test non hanno alcun impatto l’una sull’altra, ad esempio durante la valutazione di una campagna di marketing distribuito, o purché le consegne non siano pianificate nel calendario provvisorio.\
>Ciò significa che le regole sulla pressione e sulla capacità sono applicate solo alle consegne in **[!UICONTROL Target estimation and message personalization]** modalità. Consegne **[!UICONTROL Estimation and approval of the provisional target]** e **[!UICONTROL Target evaluation]** non vengono presi in considerazione.\
>La modalità di consegna viene selezionata nella **[!UICONTROL Typology]** sottoscheda delle proprietà di consegna.

![](assets/simu_campaign_select_delivery_mode.png)

## Imposta una simulazione {#setting-up-a-simulation}

### Creare una simulazione {#creating-a-simulation}

Per creare una simulazione, esegui i seguenti passaggi:

1. Apri **[!UICONTROL Campaigns]** fai clic sulla scheda **[!UICONTROL More]** all&#39;interno del **[!UICONTROL Create]** e seleziona la sezione **[!UICONTROL Simulation]** opzione .

   ![](assets/simu_campaign_opti_01.png)

1. Inserisci il modello e il nome della simulazione. Fai clic su **[!UICONTROL Save]** per creare la simulazione.

   ![](assets/simu_campaign_opti_02.png)

1. Fai clic sul pulsante **[!UICONTROL Edit]** per configurarlo.

   ![](assets/simu_campaign_opti_edit.png)

1. In **[!UICONTROL Scope]** specifica le consegne da considerare per questa simulazione. A questo scopo, fai clic sul pulsante **[!UICONTROL Add]** e specifica la modalità di selezione della consegna da considerare.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Puoi selezionare ciascuna consegna una per una oppure ordinarla per campagna, programma o piano.

   >[!NOTE]
   >
   >Se selezioni le consegne tramite un piano, un programma o una campagna, Adobe Campaign può aggiornare automaticamente l’elenco delle consegne da prendere in considerazione ogni volta che viene avviata una simulazione. Per eseguire questa operazione, controlla il **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** opzione .
   >  
   >In caso contrario, le consegne non disponibili nel piano, nel programma o nella campagna al momento della creazione della simulazione non verranno prese in considerazione: le consegne aggiunte in seguito verranno ignorate.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Seleziona gli elementi da includere nell’ambito della simulazione. Se necessario, selezionare più elementi utilizzando i tasti MAIUSC e CTRL.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Fai clic su **[!UICONTROL Finish]** per approvare la selezione.

   Puoi combinare manualmente consegne e consegne selezionate appartenenti a piani, programmi o campagne.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Se necessario, puoi utilizzare una condizione dinamica tramite il **[!UICONTROL Edit the dynamic condition...]** link.

   Fai clic su **[!UICONTROL Save]** per approvare questa configurazione.

   >[!NOTE]
   >
   >Nel calcolo delle simulazioni vengono prese in considerazione solo le consegne il cui obiettivo è stato calcolato (stati: **Target pronto** o **Pronti per la consegna**).

1. In **[!UICONTROL Calculations]** seleziona una dimensione di analisi, ad esempio lo schema destinatario.

   ![](assets/simu_campaign_opti_dimension.png)

1. È quindi possibile aggiungere espressioni.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Impostazioni di esecuzione {#execution-settings}

La **[!UICONTROL General]** la scheda della simulazione ti consente di inserire le impostazioni di esecuzione:

* La **[!UICONTROL Schedule execution for down-time]** l’opzione differisce il lancio della simulazione in un periodo di tempo meno occupato, in base al livello di priorità scelto. Le simulazioni utilizzano risorse di database significative, ecco perché le simulazioni non urgenti dovrebbero essere programmate per essere eseguite di notte, ad esempio.
* La **[!UICONTROL Priority]** è il livello applicato alla simulazione per ritardare l’attivazione.
* **[!UICONTROL Save SQL queries in the log]**. I registri SQL consentono di diagnosticare una simulazione se termina con errori. Possono anche aiutarti a scoprire perché una simulazione è troppo lenta. Questi messaggi saranno visibili dopo la simulazione nel **[!UICONTROL SQL logs]** sottoscheda della **[!UICONTROL Audit]** scheda .

## Eseguire una simulazione {#executing-a-simulation}

### Avvia una simulazione {#starting-a-simulation}

Una volta definito l’ambito di simulazione, puoi eseguirlo.

A questo scopo, apri il dashboard di simulazione e fai clic su **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

Al termine dell’esecuzione, apri la simulazione e fai clic sul pulsante **[!UICONTROL Results]** per visualizzare le destinazioni calcolate per ogni consegna.

![](assets/simu_campaign_opti_results.png)

1. La **[!UICONTROL Deliveries]** nella sottoscheda vengono elencate tutte le consegne prese in considerazione dalla simulazione. Mostra due conteggi:

   * La **[!UICONTROL Initial count]** è l’obiettivo calcolato durante la stima nella consegna.
   * La **[!UICONTROL Final count]** è il numero di destinatari conteggiati dopo la simulazione.

      La differenza tra il conteggio iniziale e finale riflette l’applicazione delle varie regole o filtri configurati prima della simulazione.

      Per ulteriori informazioni su questo calcolo, modifica il **[!UICONTROL Exclusions]** sottoscheda .

1. La **[!UICONTROL Exclusions]** la sottoscheda ti consente di visualizzare la suddivisione di esclusione.

   ![](assets/simu_campaign_opti_14.png)

1. La **[!UICONTROL Alerts]** la sottoscheda raggruppa tutti i messaggi di avviso generati durante la simulazione. I messaggi di avviso possono essere inviati in caso di sovraccarico di capacità (ad esempio se il numero di destinatari interessati supera la capacità impostata).
1. La **[!UICONTROL Exploration of the exclusions]** la sottoscheda ti consente di creare una tabella di analisi dei risultati. L’utente deve indicare le variabili negli assi abscissa/ordinata.

   Per un esempio di creazione di tabelle di analisi, fai riferimento alla fine di [Esplorazione dei risultati](#exploring-results).

### Visualizza risultati {#viewing-results}

#### Audit {#audit}

La **[!UICONTROL Audit]** consente di monitorare l’esecuzione della simulazione. La **[!UICONTROL SQL Logs]** la sottoscheda è utile per gli utenti esperti. Elenca i registri di esecuzione in formato SQL. Questi registri vengono visualizzati solo se **[!UICONTROL Save SQL queries in the log]** è stata selezionata nella **[!UICONTROL General]** prima dell’esecuzione della simulazione.

![](assets/simu_campaign_opti_11.png)

#### Esplorare i risultati {#exploring-results}

La **[!UICONTROL Exploration of the exclusions]** la sottoscheda ti consente di analizzare i dati risultanti da una simulazione.

L&#39;analisi descrittiva è dettagliata in [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Risultati di una simulazione {#results-of-a-simulation}

Gli indicatori **[!UICONTROL Log]** e **[!UICONTROL Results]** le schede forniscono una prima panoramica dei risultati della simulazione. Per una visualizzazione più dettagliata dei risultati, apri la **[!UICONTROL Reports]** scheda .

### Rapporti {#reports}

Per analizzare il risultato di una simulazione, modifica i relativi rapporti: mostrano esclusioni e cause.

Per impostazione predefinita vengono forniti i seguenti rapporti:

* **[!UICONTROL Detail of simulation exclusions]** : il presente rapporto fornisce un grafico dettagliato delle cause di esclusione per tutte le consegne interessate.
* **[!UICONTROL Simulation summary]** : questa relazione mostra le popolazioni escluse dalla simulazione durante le varie consegne.
* **[!UICONTROL Summary of exclusions linked to the simulation]** : questo rapporto mostra un grafico delle esclusioni causate dalla simulazione insieme alla regola di tipologia applicata e un grafico che mostra il rapporto di esclusione per regola.

>[!NOTE]
>
>Puoi creare nuovi report e aggiungerli a quelli offerti. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Per accedere ai rapporti, fai clic sul pulsante **[!UICONTROL Reports]** collegamento della simulazione mirata tramite il relativo dashboard.

![](assets/campaign_opt_reporting_edit_from_board.png)

È inoltre possibile modificare i rapporti utilizzando **[!UICONTROL Reports]** collegamento accessibile dal dashboard di simulazione.

### Confrontare le simulazioni {#comparing-simulations-}

Ogni volta che viene eseguita una simulazione, il risultato sostituisce eventuali risultati precedenti: non è possibile visualizzare e confrontare i risultati di un’esecuzione con quelli di un’altra.

Per confrontare i risultati, è necessario utilizzare i rapporti. Adobe Campaign consente infatti di salvare una cronologia dei rapporti per visualizzarla nuovamente in un secondo momento. Questa storia viene salvata durante tutto il ciclo di vita delle simulazioni.

**Esempio:**

1. Creare una simulazione su una consegna che utilizza una tipologia **A** viene applicato a .
1. In **[!UICONTROL Reports]** modificare uno dei rapporti disponibili, ad esempio **[!UICONTROL Detail of simulation exclusions]** ad esempio.
1. Nella sezione in alto a destra del rapporto, fai clic sull’icona per creare una nuova cronologia.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Chiudi la simulazione e modifica la configurazione della tipologia **A**.
1. Esegui nuovamente la simulazione e confronta il risultato con quello visualizzato nel rapporto per il quale è stata creata una cronologia.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Puoi salvare tutte le cronologie dei rapporti necessarie.

### Assi di reporting {#reporting-axes}

La **[!UICONTROL Calculations]** consente di definire gli assi di reporting sul target. Questi assi verranno utilizzati durante l&#39;analisi dei risultati (fare riferimento a [Esplorazione dei risultati](#exploring-results)).

>[!NOTE]
>
>È consigliabile definire gli assi di calcolo nei modelli di simulazione anziché singolarmente per ogni simulazione.\
>I modelli di simulazione vengono salvati in **[!UICONTROL Resources > Templates > Simulation templates]** nodo della struttura Adobe Campaign.

**Esempio:**

Nell’esempio seguente, vogliamo creare un asse di reporting aggiuntivo in base allo stato dei destinatari (&quot;Cliente&quot;, &quot;Prospettiva&quot; o Nessuno).

1. Per definire un asse di reporting, selezionare la tabella contenente le informazioni da elaborare nel **[!UICONTROL Analysis dimension]** campo . Queste informazioni sono obbligatorie.
1. In questo caso, vogliamo selezionare il campo Segmento della tabella dei destinatari.

   ![](assets/simu_campaign_opti_09.png)

1. Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Generate target overlap statistics]** consente di recuperare tutte le statistiche di sovrapposizione nel rapporto di simulazione. Le sovrapposizioni sono destinatari interessati da almeno due consegne all’interno di una simulazione.

      >[!IMPORTANT]
      >
      >Selezionando questa opzione si aumenta notevolmente il tempo di esecuzione della simulazione.

   * **[!UICONTROL Keep the simulation work table]** consente di mantenere tracce di simulazione.

      >[!IMPORTANT]
      >
      >Il salvataggio automatico di queste tabelle richiede una notevole capacità di storage: assicurati che il database sia sufficientemente grande.

Quando vengono visualizzati i risultati della simulazione, le informazioni sull’espressione selezionata vengono visualizzate nella sezione **[!UICONTROL Overlaps]** sottoscheda .

Le sovrapposizioni di target di consegna indicano i destinatari target in almeno due consegne di una simulazione.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Questa sottoscheda viene visualizzata solo se **[!UICONTROL Generate target recovery statistics]** è stata abilitata.

Le informazioni sugli assi di reporting possono essere elaborate nei rapporti di analisi dell’esclusione creati nella **[!UICONTROL Exploring exclusions]** sottoscheda . Per ulteriori informazioni, consulta [Esplorazione dei risultati](#exploring-results).
