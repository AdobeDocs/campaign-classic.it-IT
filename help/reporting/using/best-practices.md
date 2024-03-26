---
product: campaign
title: Best practice per il reporting
description: Best practice per la generazione di rapporti sulle campagne
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 5%

---

# Best practice per la generazione di rapporti{#best-practices-reporting}



## Analizzare le proprie esigenze{#analyzing-needs}

L’utilizzo di uno strumento di reporting dipende dal volume di dati da manipolare, dalla loro complessità e dal tipo di reporting da impostare.

Per ottimizzare la creazione, l’utilizzo e la durata di un rapporto, è necessario esaminare attentamente le esigenze che si desidera soddisfare. Questa prima analisi ti consentirà di identificare il tipo di rapporto da creare e la modalità di creazione migliore. Per creare il rapporto, effettua le seguenti operazioni:

1. Identificare la necessità

   Il primo passo è identificare chiaramente la necessità: cosa mostrare nel rapporto e qual è il suo obiettivo (monitoraggio, analisi, esportazione dei dati, ecc.).

   Adobe Campaign offre un’ampia gamma di capacità di reporting. È importante analizzare la necessità di identificare le funzionalità più adatte.

   Ad esempio, puoi:

   * Esplora i dati nel database e definisci le misurazioni. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/ac-cubes.md)
   * Aggiungere indicatori a un rapporto esistente. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)
   * Visualizzare i dati nel database. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/about-descriptive-analysis.md)
   * Crea un nuovo rapporto di consegna. Ulteriori informazioni [in questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Esportare dati dal database di Adobe Campaign (tramite un flusso di lavoro, fare riferimento a [questa sezione](../../workflow/using/about-workflows.md)
   * Creare una tabella pivot. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Esplora i dati aggregati. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/ac-cubes.md)
   * Utilizza una procedura guidata per analizzare i dati. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/about-descriptive-analysis.md)
   * Analizzare grandi volumi di dati. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)

1. Identificare la popolazione target

   Quindi devi scoprire il target del rapporto che desideri creare, conoscere il tipo di pubblico che lo visualizzerà e la modalità di visualizzazione del rapporto (in un browser, in Adobe Campaign, per un oggetto specifico, per l’intera piattaforma, ecc.).

   Puoi anche creare rapporti per:

   * Tutti gli operatori Adobe Campaign,
   * Operatori con il diritto di accedere solo a una campagna di marketing,
   * un operatore unico per uso temporaneo,
   * Tutti gli operatori in Accesso web, ecc.

   Queste considerazioni devono anche tenere conto delle questioni legate ai diritti di accesso e alla sicurezza.

1. Definire il contenuto

   Poi devi scoprire quale tipo di dati desideri visualizzare: indicatori di consegna, rapporti sui profili del database, ecc.

   È inoltre necessario conoscere la natura di questi dati (semplici, risultanti da un calcolo, significativi, ecc.), la loro posizione (in Adobe Campaign, in un sistema di terze parti), la frequenza di aggiornamento per definire la periodicità del calcolo (giornaliera, settimanale, al volo) e il loro volume.

   I problemi relativi ai volumi di dati e agli aggiornamenti devono essere esaminati attentamente per evitare problemi di visualizzazione dei rapporti, soprattutto in termini di tempo. Si consiglia pertanto di creare aggregati per precalcolare alcuni dati al di fuori del rapporto. Le tabelle che contengono i registri di tracciamento e consegna possono includere milioni di record: ciò significa che i dati devono essere aggregati tramite un flusso di lavoro per essere utilizzati in un rapporto.

## Ottimizzare la progettazione dei rapporti{#optimizing-report-creation}

### Volume dati {#data-volume}

Per garantire prestazioni ottimali, il volume dei dati manipolati non deve essere troppo grande.

Segnatamente:

* Il tempo di calcolo per un report non deve mai superare i 5 minuti.

  Analogamente, durante la fase di progettazione, con un piccolo volume di dati, se il calcolo del rapporto supera i 60 secondi, è necessario modificare i metodi di calcolo.

* Quando si utilizza il modulo Marketing Analytics, i dati di reporting non devono superare i 10 milioni di righe.

Consigliamo inoltre di calcolare gli aggregati di notte e di utilizzarli direttamente nei rapporti. Questi aggregati devono essere creati tramite flussi di lavoro di gestione dati dedicati (query SQL).

È inoltre possibile calcolare i rapporti durante la notte e creare automaticamente una cronologia che possa essere visualizzata in qualsiasi momento senza sovraccaricare il database.

### Query {#queries}

È consigliabile utilizzare le query SQL quando possibile ed evitare la post-elaborazione JavaScript. Se necessario, utilizza un’attività Script in un flusso di lavoro ed elimina i dati utilizzati per il calcolo. Puoi anche utilizzare i dati archiviati per accelerare i tempi di elaborazione.

In questo caso, è necessario utilizzare la sintassi seguente:

```
if(string(ctx@_historyId)!==""))
```

Le query che consentono di raccogliere i dati visualizzati nei report non devono essere troppo complesse, soprattutto se applicate a tutti i dati del database. Per migliorare le prestazioni, può essere utile filtrare i dati prima di eseguire queste query: questo significa che il calcolo riguarderà solo una parte dei dati.

### Prestazioni {#performances}

I consigli di cui sopra consentono di ottimizzare il calcolo del rapporto.

Inoltre, Adobe Campaign consiglia di apportare i seguenti miglioramenti:

* Lavorare sul modello dati: i campi indicizzati devono essere utilizzati principalmente per migliorare le formule di calcolo.

  Per trovare rapidamente un campo indicizzato, osserva il nome della colonna nell’interfaccia di Adobe Campaign: se il campo è indicizzato, la freccia di ordinamento è sottolineata in rosso.

  Per ulteriori informazioni sugli indici, consulta [questa sezione](../../configuration/using/data-model-best-practices.md#indexes).

* Assicurati che il rapporto sia scalabile: il volume dei dati potrebbe aumentare in modo significativo nel tempo.

  Analogamente, il volume dei dati manipolati durante le fasi di prova può differire dal volume effettivo dei dati in produzione. Ecco perché le fasi di test sono importanti.

  Infine, i ritardi di eliminazione dei dati devono essere noti e adattati quando necessario per una facile manipolazione dei dati.

  Per ulteriori informazioni sulla pulizia e la conservazione dei dati, consulta [questa sezione](../../configuration/using/data-model-best-practices.md#data-retention).

### Esportazione dei rapporti {#exporting-reports}

Recommendations specifico per l’esportazione dei rapporti è descritto in [questa sezione](../../reporting/using/actions-on-reports.md#exporting-a-report).
