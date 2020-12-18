---
solution: Campaign Classic
product: campaign
title: Simulazioni delle campagne
description: Simulazioni delle campagne
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 1%

---


# Simulazioni delle campagne{#campaign-simulations}

## Informazioni sulle simulazioni {#about-simulations}

Ottimizzazione campagna consente di verificare l&#39;efficienza di un piano di campagna mediante simulazioni. Questo consente di misurare il potenziale successo di una campagna: ricavi generati, volume di destinazione in base alle regole di tipologia applicate, ecc.

La simulazione consente di monitorare e confrontare l&#39;impatto delle consegne.

>[!NOTE]
>
>Le consegne preparate in modalità di test non hanno alcun impatto l&#39;una sull&#39;altra, ad esempio nel valutare una campagna nel marketing distribuito, o finché le consegne non sono pianificate nel calendario provvisorio.\
>Ciò significa che le regole di pressione e capacità sono applicate solo alle consegne in modalità **[!UICONTROL Target estimation and message personalization]**. Le consegne in **[!UICONTROL Estimation and approval of the provisional target]** e in modalità **[!UICONTROL Target evaluation]** non vengono prese in considerazione.\
>La modalità di consegna viene scelta nella sottoscheda **[!UICONTROL Typology]** delle proprietà di consegna.

![](assets/simu_campaign_select_delivery_mode.png)

## Impostazione di una simulazione {#setting-up-a-simulation}

### Creazione di una simulazione {#creating-a-simulation}

Per creare una simulazione, effettuate le seguenti operazioni:

1. Passare all&#39;universo **[!UICONTROL Campaigns]**, fare clic sul collegamento **[!UICONTROL More]** all&#39;interno della sezione **[!UICONTROL Create]** e selezionare l&#39;opzione **[!UICONTROL Simulation]**.

   ![](assets/simu_campaign_opti_01.png)

1. Inserite il modello e il nome della simulazione. Fate clic su **[!UICONTROL Save]** per creare la simulazione.

   ![](assets/simu_campaign_opti_02.png)

1. Fare clic sulla scheda **[!UICONTROL Edit]** per configurarla.

   ![](assets/simu_campaign_opti_edit.png)

1. Nella scheda **[!UICONTROL Scope]**, specificate le consegne da considerare per la simulazione. A questo scopo, fate clic sul pulsante **[!UICONTROL Add]** e specificate la modalità di selezione della consegna da tenere in considerazione.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Potete selezionare ogni consegna uno per uno oppure ordinarli per campagna, programma o piano.

   >[!NOTE]
   >
   >Se selezioni le consegne tramite un piano, un programma o una campagna,  Adobe Campaign può aggiornare automaticamente l&#39;elenco delle consegne da tenere in considerazione ogni volta che viene avviata una simulazione. A questo scopo, selezionare l&#39;opzione **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]**.
   >  
   >In caso contrario, le consegne non disponibili nel piano, nel programma o nella campagna al momento della creazione della simulazione non verranno prese in considerazione: le consegne aggiunte in seguito verranno ignorate.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Selezionate gli elementi da includere nell’ambito della simulazione. Se necessario, selezionare più elementi utilizzando i tasti MAIUSC e CTRL.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Fare clic su **[!UICONTROL Finish]** per approvare la selezione.

   Puoi combinare manualmente le consegne e le consegne selezionate appartenenti a piani, programmi o campagne.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Se necessario, è possibile utilizzare una condizione dinamica tramite il collegamento **[!UICONTROL Edit the dynamic condition...]**.

   Fare clic su **[!UICONTROL Save]** per approvare la configurazione.

   >[!NOTE]
   >
   >Nel calcolo delle simulazioni si tiene conto solo delle consegne il cui obiettivo è stato calcolato (stati: **Target ready** o **Ready to delivery**).

1. Nella scheda **[!UICONTROL Calculations]**, selezionare una dimensione di analisi, ad esempio lo schema del destinatario.

   ![](assets/simu_campaign_opti_dimension.png)

1. Potete quindi aggiungere espressioni.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Impostazioni di esecuzione {#execution-settings}

La scheda **[!UICONTROL General]** della simulazione consente di immettere le impostazioni di esecuzione:

* L&#39;opzione **[!UICONTROL Schedule execution for down-time]** trasferisce l&#39;avvio della simulazione a un periodo di tempo meno occupato, in base al livello di priorità scelto. Le simulazioni utilizzano notevoli risorse di database, ecco perché le simulazioni non urgenti dovrebbero essere programmate per essere eseguite di notte, ad esempio.
* **[!UICONTROL Priority]** è il livello applicato alla simulazione per ritardarne l&#39;attivazione.
* **[!UICONTROL Save SQL queries in the log]**. I registri SQL consentono di diagnosticare una simulazione se termina con errori. Possono anche aiutarvi a scoprire perché una simulazione è troppo lenta. Questi messaggi saranno visibili dopo la simulazione nella sottoscheda **[!UICONTROL SQL logs]** della scheda **[!UICONTROL Audit]**.

## Esecuzione di una simulazione {#executing-a-simulation}

### Avvio di una simulazione {#starting-a-simulation}

Una volta definito l’ambito di simulazione, potete eseguirlo.

A questo scopo, aprite il dashboard di simulazione e fate clic su **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

Al termine dell&#39;esecuzione, aprite la simulazione e fate clic sulla scheda **[!UICONTROL Results]** per visualizzare le destinazioni calcolate per ogni consegna.

![](assets/simu_campaign_opti_results.png)

1. Nella sottoscheda **[!UICONTROL Deliveries]** sono elencate tutte le consegne prese in considerazione dalla simulazione. Vengono visualizzati due conteggi:

   * Il **[!UICONTROL Initial count]** è il target calcolato durante la stima nella consegna.
   * **[!UICONTROL Final count]** indica il numero di destinatari contati dopo la simulazione.

      La differenza tra il conteggio iniziale e quello finale riflette l&#39;applicazione delle varie regole o filtri configurati prima della simulazione.

      Per ulteriori informazioni su questo calcolo, modificare la sottoscheda **[!UICONTROL Exclusions]**.

1. La sottoscheda **[!UICONTROL Exclusions]** consente di visualizzare l&#39;interruzione di esclusione.

   ![](assets/simu_campaign_opti_14.png)

1. Nella sottoscheda **[!UICONTROL Alerts]** vengono raggruppati tutti i messaggi di avviso generati durante la simulazione. I messaggi di avviso possono essere inviati in caso di sovraccarico di capacità (ad esempio, se il numero di destinatari supera la capacità impostata).
1. La sottoscheda **[!UICONTROL Exploration of the exclusions]** consente di creare una tabella di analisi dei risultati. L&#39;utente deve indicare le variabili negli assi abscissa/ordinata.

   Per un esempio di creazione di tabelle di analisi, fare riferimento alla fine di [Risultati di esplorazione](#exploring-results).

### Visualizzazione dei risultati {#viewing-results}

#### Audit {#audit}

La scheda **[!UICONTROL Audit]** consente di monitorare l&#39;esecuzione della simulazione. La sottoscheda **[!UICONTROL SQL Logs]** è utile per gli utenti esperti. Elenca i registri di esecuzione in formato SQL. Questi registri vengono visualizzati solo se l&#39;opzione **[!UICONTROL Save SQL queries in the log]** è stata selezionata nella scheda **[!UICONTROL General]** prima dell&#39;esecuzione della simulazione.

![](assets/simu_campaign_opti_11.png)

#### Esplorazione dei risultati {#exploring-results}

La scheda secondaria **[!UICONTROL Exploration of the exclusions]** consente di analizzare i dati risultanti da una simulazione.

L&#39;analisi descrittiva è dettagliata in [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Risultati di una simulazione {#results-of-a-simulation}

Gli indicatori nelle schede **[!UICONTROL Log]** e **[!UICONTROL Results]** forniscono una prima panoramica dei risultati della simulazione. Per una visualizzazione più dettagliata dei risultati, aprite la scheda **[!UICONTROL Reports]**.

### Rapporti {#reports}

Per analizzare il risultato di una simulazione, modificatene i rapporti: mostrano esclusioni e cause.

Per impostazione predefinita, vengono forniti i seguenti rapporti:

* **[!UICONTROL Detail of simulation exclusions]** : la relazione fornisce un grafico dettagliato delle cause di esclusione per tutte le consegne interessate.
* **[!UICONTROL Simulation summary]** : questa relazione mostra le popolazioni escluse dalla simulazione per tutta la durata delle varie consegne.
* **[!UICONTROL Summary of exclusions linked to the simulation]** : questo rapporto mostra un grafico delle esclusioni causate dalla simulazione insieme alla regola di tipologia applicata e un grafico che mostra il rapporto di esclusione per regola.

>[!NOTE]
>
>Puoi creare nuovi rapporti e aggiungerli a quelli offerti. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Per accedere ai rapporti, fate clic sul collegamento **[!UICONTROL Reports]** della simulazione di destinazione tramite il relativo dashboard.

![](assets/campaign_opt_reporting_edit_from_board.png)

Potete anche modificare i rapporti utilizzando il collegamento **[!UICONTROL Reports]** accessibile dal dashboard di simulazione.

### Confronto delle simulazioni {#comparing-simulations-}

Ogni volta che viene eseguita una simulazione, il risultato sostituisce eventuali risultati precedenti: non è possibile visualizzare e confrontare i risultati di un&#39;esecuzione a un&#39;altra.

Per confrontare i risultati, è necessario utilizzare i rapporti. In effetti,  Adobe Campaign consente di salvare una cronologia dei report per visualizzarla nuovamente in un secondo momento. Questa storia viene salvata durante tutto il ciclo di vita delle simulazioni.

**Esempio:**

1. Create una simulazione su una consegna a cui viene applicata la tipologia **A**.
1. Nella scheda **[!UICONTROL Reports]**, modificare uno dei rapporti disponibili, ad esempio **[!UICONTROL Detail of simulation exclusions]**.
1. Nella sezione in alto a destra del rapporto, fai clic sull&#39;icona per creare una nuova cronologia.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Chiudere la simulazione e modificare la configurazione della tipologia **A**.
1. Eseguire di nuovo la simulazione e confrontare il risultato con quello visualizzato nel report per il quale è stata creata una cronologia.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Puoi salvare tutte le cronologie dei report necessarie.

### Assi di reporting {#reporting-axes}

La scheda **[!UICONTROL Calculations]** consente di definire gli assi di reporting sulla destinazione. Questi assi verranno utilizzati durante l&#39;analisi dei risultati (fare riferimento a [Risultati di esplorazione](#exploring-results)).

>[!NOTE]
>
>È consigliabile definire gli assi di calcolo nei modelli di simulazione anziché singolarmente per ogni simulazione.\
>I modelli di simulazione vengono salvati nel nodo **[!UICONTROL Resources > Templates > Simulation templates]** della struttura di Adobe Campaign .

**Esempio:**

Nell&#39;esempio seguente, vogliamo creare un asse di reporting aggiuntivo in base allo stato dei destinatari (&quot;Cliente&quot;, &quot;Prospettiva&quot; o nessuno).

1. Per definire un asse di reporting, selezionare la tabella che contiene le informazioni da elaborare nel campo **[!UICONTROL Analysis dimension]**. Queste informazioni sono obbligatorie.
1. Qui si desidera selezionare il campo Segmento della tabella dei destinatari.

   ![](assets/simu_campaign_opti_09.png)

1. Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Generate target overlap statistics]** consente di recuperare tutte le statistiche di sovrapposizione nel rapporto di simulazione. Le sovrapposizioni sono destinatari mirati in almeno due consegne all&#39;interno di una simulazione.

      >[!IMPORTANT]
      >
      >Selezionando questa opzione si aumenta notevolmente il tempo di esecuzione della simulazione.

   * **[!UICONTROL Keep the simulation work table]** consente di mantenere tracce di simulazione.

      >[!IMPORTANT]
      >
      >Il salvataggio automatico di queste tabelle richiede una notevole capacità di storage: assicurarsi che il database sia sufficientemente grande.

Quando i risultati della simulazione vengono visualizzati, le informazioni sull&#39;espressione selezionata vengono visualizzate nella sottoscheda **[!UICONTROL Overlaps]**.

Le sovrapposizioni delle destinazioni di consegna indicano i destinatari con targeting in almeno due consegne di una simulazione.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Questa sottoscheda viene visualizzata solo se l&#39;opzione **[!UICONTROL Generate target recovery statistics]** è stata abilitata.

Le informazioni sugli assi di reporting possono essere elaborate nei report di analisi dell&#39;esclusione creati nella sottoscheda **[!UICONTROL Exploring exclusions]**. Per ulteriori informazioni, vedere [Risultati di esplorazione](#exploring-results).
