---
title: HeatMap flusso di lavoro
seo-title: HeatMap flusso di lavoro
description: HeatMap flusso di lavoro
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ea6488686d19b020e55839afee97e71a13ce2e33
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 0%

---


# HeatMap flusso di lavoro {#workflow-heatmap}

La  Workflow HeatMap consiste in una rappresentazione grafica con colori diversi per tutti i flussi di lavoro attualmente in esecuzione. È disponibile solo per gli amministratori di istanza.

In [questa pagina](../../production/using/monitoring-guidelines.md)sono disponibili altri metodi per monitorare i diversi processi di Campaign.

## Informazioni sulla mappa di calore del flusso di lavoro {#about-the-workflow-heatmap}

Fornendo una rapida panoramica sul numero di flussi di lavoro simultanei, Workflow HeatMap consente agli amministratori della piattaforma di  Adobe Campaign di monitorare il carico sull&#39;istanza e pianificare i flussi di lavoro di conseguenza.

Più precisamente, consente agli amministratori di piattaforma di:

* Visualizzare e comprendere flussi di lavoro simultanei
* Filtrare i flussi di lavoro per durata per vedere quali flussi di lavoro potrebbero incontrare problemi
* Filtrare le attività per durata per vedere quali attività possono incontrare problemi
* Trova facilmente flussi di lavoro singoli e tutte le attività correlate (con la loro durata)
* Ricerca per tipo di flusso di lavoro (flussi di lavoro[](../../workflow/using/building-a-workflow.md#technical-workflows) tecnici o flussi di lavoro [di](../../workflow/using/building-a-workflow.md#campaign-workflows)campagna)
* Cercare un flusso di lavoro specifico da analizzare

>[!NOTE]
>
>Oltre alla Heatmap del **flusso di lavoro**, puoi creare un flusso di lavoro che ti consenta di monitorare lo stato di un set di flussi di lavoro e inviare messaggi ricorrenti alle autorità di vigilanza. For more on this, refer to the [dedicated section](../../workflow/using/supervising-workflows.md).

L’utilizzo di HeatMap del flusso di lavoro richiede una buona comprensione dei seguenti concetti: [Best practice](../../workflow/using/about-workflows.md)per flussi di lavoro, [attività](../../workflow/using/about-activities.md) e [flussi di lavoro](../../workflow/using/workflow-best-practices.md).

Il HeatMap del flusso di lavoro è disponibile per impostazione predefinita in  Adobe Campaign a partire dalla release 18.10. Se disponete di una build compresa tra 8700 e 8977 (18.10), potete anche beneficiare di questa funzionalità. Per richiedere il pacchetto corrispondente, contattate l&#39;Assistenza [clienti](https://support.neolane.net/) Adobe e seguite le istruzioni fornite in [questa pagina](https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html) per apprendere come installarlo.

Quando accedete per la prima volta a Workfklow HeatMap, viene visualizzata la finestra a comparsa seguente. L&#39;accordo consente il trasferimento e lo stoccaggio negli Stati Uniti, consentendo  Adobe Campaign di:

* monitorare le istanze per esaminare eventuali problemi di prestazioni.
* raccogliere i dati per il rilevamento delle anomalie.

Il trasferimento dei dati è disponibile solo per gli utenti che si connettono a  Adobe Campaign utilizzando il proprio Adobe ID .

![](assets/wf_monitoring_agreement.png)

Sono disponibili tre opzioni:

* **[!UICONTROL Accept]** : Accettando questo contratto, autorizzi  Adobe Campaign a raccogliere i tuoi dati e a trasferirli negli Stati Uniti per essere in grado di aiutarti in caso di rilevamento di anomalie.
* **[!UICONTROL Refuse]** : Rifiutando l&#39;accordo, i dati non verranno trasferiti ma puoi comunque utilizzare Workflow Heatmap.
* **[!UICONTROL Do not show this message again]** : Facendo clic su **[!UICONTROL Do not show this message again]** , la finestra a comparsa si interrompe quando si accede a Workflow Heatmap ma è ancora disponibile dal **[!UICONTROL Term of use]** pulsante.

Questa scelta non è finale, è sempre possibile modificarla facendo clic sul **[!UICONTROL Term of use]** pulsante.

## Utilizzo di HeatMap {#using-the-heatmap}

>[!NOTE]
>
>Solo gli utenti con diritti di amministrazione possono accedere alla mappa di calore del flusso di lavoro della campagna.

1. Passate a **[!UICONTROL Monitoring]** e fate clic sul **[!UICONTROL Workflow HeatMap]** collegamento per visualizzare la **[!UICONTROL Campaign Workflow HeatMap]** pagina.

   ![](assets/wkf_monitoring_path.png)

1. Fate clic sul calendario per selezionare un giorno.

   Per impostazione predefinita, la pagina mostra l’attività del flusso di lavoro per il giorno corrente. Potete modificarlo e selezionare qualsiasi giorno del passato.

   >[!NOTE]
   >
   >Sono visibili solo i flussi di lavoro che non sono stati eliminati dal **[!UICONTROL Database cleanup]** flusso di lavoro. Per ulteriori informazioni sul flusso di lavoro di pulizia del database, consultare [questa sezione](../../production/using/database-cleanup-workflow.md).\
   >Per impostazione predefinita, il fuso orario Workflow HeatMap è quello definito per l’utente amministratore corrente. Ad esempio, puoi modificarlo se non ti trovi nella stessa area degli utenti di marketing con cui stai lavorando.

1. Fai clic sul pulsante **[!UICONTROL Filters]**. 

   ![](assets/wkf_monitoring_filters.png)

1. Usate il cursore per impostare la durata minima da 0 a 1 ora. Questo consente di cercare solo i flussi di lavoro in esecuzione per più di un certo numero di secondi o minuti.

   ![](assets/wkf_monitoring_filters_duration.png)

1. Potete anche scegliere un flusso di lavoro specifico dall’ **[!UICONTROL Workflows]** elenco.

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >Il **[!UICONTROL Min duration]** filtro viene applicato. Se non trovate un flusso di lavoro specifico, reimpostate la durata minima su 0 in modo che tutti i flussi di lavoro siano visualizzati nell’elenco.

1. Potete anche filtrare su **[!UICONTROL Workflow type]** :

   * **[!UICONTROL Technical]** : Vengono visualizzati solo i flussi [di lavoro](../../workflow/using/building-a-workflow.md#technical-workflows) tecnici e di gestione [dei dati](../../workflow/using/targeting-data.md#data-management) .
   * **[!UICONTROL Marketing]** : Vengono visualizzati solo i flussi di lavoro collegati a una campagna di marketing, noti come flussi di lavoro [di](../../workflow/using/building-a-workflow.md#campaign-workflows)campagna.

1. Per eseguire ricerche in un flusso di lavoro specifico in base al nome, potete anche utilizzare il **[!UICONTROL Workflow name filter]** campo.

   ![](assets/wkf_monitoring_filters_name.png)

1. Se hai modificato alcuni flussi di lavoro nel periodo compreso, fai clic sul **[!UICONTROL Reload data]** pulsante per aggiornare i dati visualizzati nella griglia.

## Lettura della mappa di calore {#reading-the-heatmap}

La Campaign Workflow HeatMap è una griglia leggibile in modo naturale dall&#39;alto a sinistra verso il basso a destra, che consente di individuare le &quot;aree sensibili&quot; con un intervallo di colori da verde a rosso.

* Le celle rosse più scure corrispondono a periodi in cui un elevato numero di flussi di lavoro vengono eseguiti contemporaneamente.
* Le celle grigie corrispondono ai punti in cui non è in esecuzione alcun flusso di lavoro.

Per informazioni sull’applicazione del codice colore e su come navigare nella mappa di calore, fate clic sul **[!UICONTROL Help]** pulsante .

![](assets/wkf_monitoring_legend.png)

Ogni riga rappresenta un&#39;ora del giorno e ogni cella rappresenta 5 minuti di quell&#39;ora.

La griglia mostra tutti i flussi di lavoro in esecuzione contemporaneamente per ciascuno di questi periodi di 5 minuti.

Nell&#39;esempio seguente, tra le 8 e le 8:05 del mattino, sono in esecuzione tre flussi di lavoro (indipendentemente dalla durata individuale):

![](assets/wkf_monitoring_ex_8am.png)

1. Fai clic su una cella colorata per visualizzare i dettagli di tutti i flussi di lavoro simultanei in esecuzione in questo periodo.

   ![](assets/wkf_monitoring_details.png)

   Per ciascun flusso di lavoro, vengono elencate tutte le attività che contengono, con la relativa durata.

1. Fate clic sull’ID o sul nome del flusso di lavoro per aprire direttamente un flusso di lavoro.
1. Per tornare alla **[!UICONTROL Campaign Workflow HeatMap]** visualizzazione, fare clic sul **[!UICONTROL Home]** pulsante.

## Casi di utilizzo: utilizzo di HeatMap per eseguire azioni {#use-cases--using-the-heatmap-to-take-actions}

Esistono due casi principali in cui la mappa del calore del flusso di lavoro della campagna può essere utile.

### Riduzione del numero di flussi di lavoro simultanei {#reducing-the-number-of-concurrent-workflows}

In qualità di amministratore di Campaign, Workflow HeatMap può aiutarti a comprendere il carico sull&#39;istanza e a pianificare flussi di lavoro esistenti o nuovi in momenti opportuni.

1. Dalla **[!UICONTROL Campaign Workflow HeatMap]** vista, fare clic sul **[!UICONTROL Filters]** pulsante.
1. Impostate la durata su alcuni secondi o su alcuni minuti.
1. Escludete i flussi di lavoro più brevi che non sono significativi aumentando il filtro della durata.

   ![](assets/wkf_monitoring_short_duration.png)

1. Esplorate i risultati per comprendere il carico sull&#39;istanza ed eseguite le azioni appropriate:

   * Se si verificano problemi di prestazioni e se una o più celle rosse vengono visualizzate nella griglia, è consigliabile modificare i tempi di inizio di diversi flussi di lavoro. Chiedi agli utenti di marketing di spostare manualmente i flussi di lavoro dai periodi occupati (&quot;hot&quot;) a più orari disponibili. Ciò dovrebbe mantenere un livello stabile di attività durante tutto il giorno.
   * Per evitare picchi e impedire che l’istanza venga sovraccaricata, controllate HeatMap prima di pianificare nuovi flussi di lavoro e scegliete il momento migliore. Considerare gli slot temporali corrispondenti alle celle grigie o verdi nella griglia per avviare nuovi flussi di lavoro.

### Ricerca di flussi di lavoro a lungo termine che influiscono sulle prestazioni {#finding-long-running-workflows-that-impact-performance}

Come amministratore di Campaign, Workflow HeatMap ti aiuta a trovare i flussi di lavoro più lunghi che possono rallentare l&#39;attività.

1. Dalla **[!UICONTROL Campaign Workflow HeatMap]** vista, fare clic sul **[!UICONTROL Filters]** pulsante.
1. Impostate la durata su 1 ora.

   ![](assets/wkf_monitoring_long_duration.png)

1. Includete più risultati diminuendo il **[!UICONTROL Min duration]** filtro.
1. Esplorate i risultati per individuare i flussi di lavoro più lunghi, che possono avere un impatto maggiore sulle risorse del server e del database (CPU, RAM, rete, IOPS e così via).
1. Adottare le misure appropriate:

   * Consiglia agli utenti di marketing di suddividere i flussi di lavoro più lunghi per ridurre il tempo di elaborazione.
   * Avviate un&#39;analisi più approfondita su flussi di lavoro specifici e attività specifiche (come JavaScript, importazione, esportazione e così via) per isolare i problemi e risolverli più facilmente.

## Esempio: Utilizzo di HeatMap per migliorare la pianificazione del flusso di lavoro {#example--using-the-heatmap-to-improve-workflow-planning}

L’esempio seguente mostra come la pianificazione possa essere più efficiente e come migliorare le prestazioni quando si utilizza la mappa calore del flusso di lavoro del Adobe Campaign .

In questo caso, molti utenti si lamentano delle prestazioni del flusso di lavoro. È necessario verificare cosa rallenta l&#39;attività e come risolvere il problema.

1. Passate a **[!UICONTROL Monitoring]** e fate clic sul **[!UICONTROL Workflows]** collegamento per visualizzare la **[!UICONTROL Campaign Workflow HeatMap]** pagina.
1. Impostate il **[!UICONTROL Min duration]** filtro su 5 minuti.
1. Impostate il **[!UICONTROL Workflow type]** filtro su **[!UICONTROL Marketing]** .
1. Dalla griglia HeatMap, osservate quanto segue:

   ![](assets/wkf_monitoring_without.png)

   * Alle 10 di mattina sono in esecuzione 50 flussi di lavoro di campagna di lunga durata (più di 5 minuti).
   * La maggior parte di essi dispone di uno stato in sospeso (per impostazione predefinita, il limite di concorrenza è impostato su 20).
   * I flussi di lavoro in sospeso devono essere riavviati manualmente ogni giorno.
   * Le prestazioni sono basse.

1. Invece di avere cinquanta flussi di lavoro a partire dalle 10, distribuisci gli orari di inizio dei flussi di lavoro in modo uniforme per tutto il resto della giornata.
1. Tornate alla **[!UICONTROL Campaign Workflow HeatMap]** pagina e fate clic sul **[!UICONTROL Reload data]** pulsante.
1. Osservate ora quanto segue:

   ![](assets/wkf_monitoring_with.png)

   * Solo diciotto flussi di lavoro per campagne di lunga durata sono ancora in esecuzione alle 10 di mattina.
   * Nessun flusso di lavoro in sospeso (il limite di concorrenza è ancora impostato su 20).
   * Gli orari di inizio dei flussi di lavoro vengono distribuiti in modo uniforme durante l&#39;intera giornata.
   * Nessun altro utente si lamenta dei problemi di prestazioni.
