---
solution: Campaign Classic
product: campaign
title: Workflow HeatMap
description: Monitorare i flussi di lavoro di Campaign con Workflow HeatMap
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: f1016ddf-0c87-4611-a878-d01f3684935f
translation-type: tm+mt
source-git-commit: 5b1c4426a0d59861aa61a7e53154b9adfda31d71
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 4%

---

# Workflow HeatMap {#workflow-heatmap}

Adobe Campaign Workflow HeatMap è costituito da una rappresentazione grafica codificata per colori di tutti i flussi di lavoro attualmente in esecuzione. È disponibile solo per gli amministratori delle istanze.

In [questa pagina](../../production/using/monitoring-guidelines.md) sono descritti metodi aggiuntivi per monitorare i diversi processi di Campaign.

## Informazioni sul Workflow HeatMap {#about-the-workflow-heatmap}

Fornendo una rapida panoramica sul numero di flussi di lavoro simultanei, Workflow HeatMap consente agli amministratori della piattaforma Adobe Campaign di monitorare il carico sull’istanza e pianificare i flussi di lavoro di conseguenza.

Più precisamente, consente agli amministratori di piattaforma di:

* Visualizzare e comprendere i flussi di lavoro simultanei
* Filtrare i flussi di lavoro per durata per vedere quali potrebbero presentare problemi
* Filtrare le attività per durata per vedere quali attività possono incontrare problemi
* Trovare facilmente singoli flussi di lavoro e le attività correlate ad essi (con la relativa durata)
* Ricercare per tipo di flusso di lavoro ([flussi di lavoro tecnici](../../workflow/using/building-a-workflow.md#technical-workflows) o [flussi di lavoro di campagne](../../workflow/using/building-a-workflow.md#campaign-workflows))
* Cercare un flusso di lavoro specifico da analizzare

>[!NOTE]
>
>Oltre alla **Workflow Heatmap**, puoi creare un flusso di lavoro che ti consenta di monitorare lo stato di un set di flussi di lavoro e inviare messaggi ricorrenti alle autorità di vigilanza. Per ulteriori informazioni, consulta la sezione [dedicata](../../workflow/using/supervising-workflows.md).

L&#39;utilizzo di Workflow HeatMap richiede una buona comprensione dei seguenti concetti: [Flussi di lavoro](../../workflow/using/about-workflows.md), [Attività](../../workflow/using/about-activities.md) e [Best practice per i flussi di lavoro](../../workflow/using/workflow-best-practices.md).

<!--The Workflow HeatMap is available by default in Adobe Campaign starting 18.10 release. If you have a build between 8700 and 8977 (18.10), you can also benefit from this capability. To request the corresponding package, contact the [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) and follow the instructions from [this page](https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html) to understand how to install it.-->

## Utilizzo di HeatMap {#using-the-heatmap}

>[!NOTE]
>
>Solo gli utenti con diritti di amministrazione possono accedere alla Workflow HeatMap di Campaign.

1. Vai a **[!UICONTROL Monitoring]** e fai clic sul collegamento **[!UICONTROL Workflow HeatMap]** per visualizzare la pagina **[!UICONTROL Campaign Workflow HeatMap]**.

   ![](assets/wkf_monitoring_path.png)

1. Fai clic sul calendario per selezionare un giorno.

   Per impostazione predefinita, la pagina mostra l’attività del flusso di lavoro per il giorno corrente. Puoi modificarlo e selezionare qualsiasi giorno nel passato.

   >[!NOTE]
   >
   >Sono visibili solo i flussi di lavoro che non sono stati eliminati dal flusso di lavoro **[!UICONTROL Database cleanup]** . Per ulteriori informazioni sul flusso di lavoro di pulizia del database, consulta [questa sezione](../../production/using/database-cleanup-workflow.md).\
   >Per impostazione predefinita, il fuso orario Workflow HeatMap è quello definito per l&#39;utente amministratore corrente. Ad esempio, puoi modificarla se non ti trovi nella stessa area degli utenti di marketing con cui stai lavorando.

1. Fai clic sul pulsante **[!UICONTROL Filters]**.

   ![](assets/wkf_monitoring_filters.png)

1. Utilizzare il cursore per impostare la durata minima da 0 a 1 ora. Questo consente di cercare solo i flussi di lavoro in esecuzione per più di un certo numero di secondi o minuti.

   ![](assets/wkf_monitoring_filters_duration.png)

1. Puoi anche scegliere un flusso di lavoro specifico dall’elenco **[!UICONTROL Workflows]**.

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >Viene applicato il filtro **[!UICONTROL Min duration]** . Se non riesci a trovare un flusso di lavoro specifico, reimposta la durata minima su 0 in modo che tutti i flussi di lavoro siano visualizzati nell’elenco.

1. Puoi anche filtrare il **[!UICONTROL Workflow type]** :

   * **[!UICONTROL Technical]** : Vengono visualizzati solo  [flussi di ](../../workflow/using/building-a-workflow.md#technical-workflows) lavoro preconfigurati e flussi di  [lavoro ](../../workflow/using/targeting-data.md#data-management) di gestione dei dati.
   * **[!UICONTROL Marketing]** : Vengono visualizzati solo i flussi di lavoro collegati a una campagna di marketing, noti come flussi di lavoro per  [campagne](../../workflow/using/building-a-workflow.md#campaign-workflows).

1. Per cercare un flusso di lavoro specifico per nome, puoi anche utilizzare il campo **[!UICONTROL Workflow name filter]** .

   ![](assets/wkf_monitoring_filters_name.png)

1. Se hai modificato alcuni flussi di lavoro nel periodo di tempo tra , fai clic sul pulsante **[!UICONTROL Reload data]** per aggiornare i dati visualizzati nella griglia.

## Lettura della mappa di calore {#reading-the-heatmap}

La Workflow HeatMap di Campaign è una griglia leggibile in modo naturale dall’alto a sinistra verso il basso a destra, che consente di trovare le &quot;aree calde&quot; con una gamma di colori da verde a rosso.

* Le celle rosse più scure corrispondono a periodi in cui un numero elevato di flussi di lavoro vengono eseguiti contemporaneamente.
* Le celle grigie corrispondono a periodi in cui non è in esecuzione alcun flusso di lavoro.

Per scoprire come applicare il codice colore e come navigare nella mappa di calore, fai clic sul pulsante **[!UICONTROL Help]** .

![](assets/wkf_monitoring_legend.png)

Ogni riga rappresenta un’ora del giorno e ogni cella rappresenta 5 minuti di quell’ora.

La griglia mostra tutti i flussi di lavoro in esecuzione contemporaneamente per ciascuno di questi periodi di 5 minuti.

Nell’esempio seguente, tra le 8 e le 8:05, sono in esecuzione tre flussi di lavoro (indipendentemente dalla loro durata individuale):

![](assets/wkf_monitoring_ex_8am.png)

1. Fai clic su una cella colorata per visualizzare i dettagli di tutti i flussi di lavoro simultanei in esecuzione durante questo periodo.

   ![](assets/wkf_monitoring_details.png)

   Per ogni flusso di lavoro, vengono elencate tutte le attività che contengono, con la relativa durata.

1. Fai clic sull’ID o sul nome del flusso di lavoro per aprire direttamente un flusso di lavoro.
1. Per tornare alla visualizzazione **[!UICONTROL Campaign Workflow HeatMap]**, fai clic sul pulsante **[!UICONTROL Home]** .

## Casi di utilizzo: utilizzo di HeatMap per eseguire azioni {#use-cases--using-the-heatmap-to-take-actions}

Esistono due casi principali in cui la Workflow HeatMap di Campaign può essere utile.

### Riduzione del numero di flussi di lavoro simultanei {#reducing-the-number-of-concurrent-workflows}

In qualità di amministratore di Campaign, Workflow HeatMap può aiutarti a comprendere il carico sull’istanza e a pianificare i flussi di lavoro esistenti o nuovi in momenti opportuni.

1. Dalla visualizzazione **[!UICONTROL Campaign Workflow HeatMap]**, fai clic sul pulsante **[!UICONTROL Filters]** .
1. Imposta la durata a pochi secondi o qualche minuto.
1. Escludi i flussi di lavoro più brevi che non sono significativi aumentando il filtro della durata.

   ![](assets/wkf_monitoring_short_duration.png)

1. Esplorare i risultati per comprendere il carico sull&#39;istanza e intraprendere le azioni appropriate:

   * Se si verificano problemi di prestazioni e se una o più celle rosse sono visualizzate nella griglia, è consigliabile modificare i tempi di avvio di diversi flussi di lavoro. Chiedi agli utenti di marketing di spostare manualmente i flussi di lavoro da periodi di attività (&quot;hot&quot;) a intervalli di tempo più disponibili. Questo dovrebbe mantenere un livello di attività stabile durante il giorno.
   * Per evitare picchi ed evitare che l’istanza si sovraccarichi, osserva HeatMap prima di pianificare i nuovi flussi di lavoro e scegli il momento migliore. Per avviare nuovi flussi di lavoro, prendi in considerazione intervalli di tempo corrispondenti a celle grigie o verdi nella griglia.

### Ricerca di flussi di lavoro a lungo termine che influiscono sulle prestazioni {#finding-long-running-workflows-that-impact-performance}

In qualità di amministratore di Campaign, Workflow HeatMap ti consente di trovare i flussi di lavoro più lunghi che possono rallentare l’attività.

1. Dalla visualizzazione **[!UICONTROL Campaign Workflow HeatMap]**, fai clic sul pulsante **[!UICONTROL Filters]** .
1. Imposta la durata su 1 ora.

   ![](assets/wkf_monitoring_long_duration.png)

1. Includi più risultati diminuendo il filtro **[!UICONTROL Min duration]** .
1. Esplora i risultati per trovare i flussi di lavoro più lunghi, che possono potenzialmente avere un maggiore impatto sulle risorse del server e del database (CPU, RAM, rete, IOPS e così via).
1. Adottare le misure appropriate:

   * Consigliamo agli utenti di marketing di suddividere i flussi di lavoro più lunghi per ridurre i tempi di elaborazione.
   * Avvia un’analisi più approfondita su flussi di lavoro specifici e attività specifiche (come JavaScript, importazione, esportazione e così via) per isolare i problemi e risolverli più facilmente.

## Esempio: Utilizzo di HeatMap per migliorare la pianificazione del flusso di lavoro {#example--using-the-heatmap-to-improve-workflow-planning}

L’esempio seguente mostra come la pianificazione può essere più efficiente e come le prestazioni possono essere migliorate quando si utilizza Adobe Campaign Workflow HeatMap.

In questo caso, molti utenti si lamentano delle prestazioni del flusso di lavoro. È necessario controllare cosa rallenta l&#39;attività e come risolvere il problema.

1. Vai a **[!UICONTROL Monitoring]** e fai clic sul collegamento **[!UICONTROL Workflows]** per visualizzare la pagina **[!UICONTROL Campaign Workflow HeatMap]**.
1. Imposta il filtro **[!UICONTROL Min duration]** su 5 minuti.
1. Imposta il filtro **[!UICONTROL Workflow type]** su **[!UICONTROL Marketing]** .
1. Dalla griglia di HeatMap, osservate quanto segue:

   ![](assets/wkf_monitoring_without.png)

   * 50 flussi di lavoro per campagne di lunga durata (più di 5 minuti) sono in esecuzione alle 10.
   * La maggior parte di essi dispone di uno stato in sospeso (per impostazione predefinita, il limite di concorrenza è impostato su 20).
   * I flussi di lavoro in sospeso devono essere riavviati manualmente ogni giorno.
   * Le prestazioni sono basse.

1. Invece di avere cinquanta flussi di lavoro a partire dalle 10, distribuisci gli orari di avvio dei flussi di lavoro in modo uniforme per il resto della giornata.
1. Torna alla pagina **[!UICONTROL Campaign Workflow HeatMap]** e fai clic sul pulsante **[!UICONTROL Reload data]** .
1. Osserva quanto segue:

   ![](assets/wkf_monitoring_with.png)

   * Alle 10 di mattina sono ancora in esecuzione solo diciotto flussi di lavoro per campagne di lunga durata.
   * Nessun altro flusso di lavoro è in sospeso (il limite di concorrenza è ancora impostato su 20).
   * Gli orari di avvio del flusso di lavoro sono distribuiti in modo uniforme durante l&#39;intera giornata.
   * Nessun altro utente si lamenta di problemi di prestazioni.
