---
product: campaign
title: Best practice per il reporting
description: Best practice per la generazione di rapporti sulle campagne
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---

# Best practice per la generazione di rapporti{#best-practices-reporting}

![](../../assets/common.svg)

## Analisi delle esigenze{#analyzing-needs}

L’utilizzo di uno strumento di reporting dipende dal volume di dati da manipolare, dalla sua complessità e dal tipo di reporting da configurare.

Per ottimizzare la creazione, l’utilizzo e la durata di un rapporto, è necessario esaminare attentamente le esigenze che si desidera soddisfare. Questa prima analisi ti consente di identificare il tipo di rapporto da creare e la modalità di creazione migliore. Per creare il rapporto, effettua le seguenti operazioni:

1. Identificare la necessità

   Il primo passo è quello di identificare chiaramente la necessità: cosa desideri mostrare nel tuo rapporto e quale sia il suo obiettivo (monitoraggio, analisi, esportazione di dati, ecc.).

   Adobe Campaign offre una vasta gamma di capacità di reporting. È importante analizzare la necessità di identificare la funzionalità più adatta.

   Ad esempio, puoi:

   * Esplora i dati nel database e definisci le misurazioni. Ulteriori informazioni [in questa sezione](../../reporting/using/about-cubes.md)
   * Aggiungi indicatori a un rapporto esistente. Ulteriori informazioni [in questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)
   * Visualizza i dati nel database. Ulteriori informazioni [in questa sezione](../../reporting/using/about-descriptive-analysis.md)
   * Crea un nuovo rapporto di consegna. Ulteriori informazioni [in questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Esporta dati dal database di Adobe Campaign (tramite un flusso di lavoro, fai riferimento a [questa sezione](../../workflow/using/about-workflows.md)
   * Creare una tabella pivot. Ulteriori informazioni [in questa sezione](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Esplorare i dati aggregati. Ulteriori informazioni [in questa sezione](../../reporting/using/about-cubes.md)
   * Utilizza una procedura guidata per analizzare i dati. Ulteriori informazioni [in questa sezione](../../reporting/using/about-descriptive-analysis.md)
   * Analizzare grandi volumi di dati. Ulteriori informazioni [in questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)

1. Identificare la popolazione target

   Quindi devi scoprire di chi sarà il target del rapporto che desideri creare, sapere il tipo di pubblico che lo visualizzerà e la modalità di visualizzazione del rapporto (in un browser, in Adobe Campaign, per un oggetto specifico, per l’intera piattaforma, ecc.).

   Puoi anche creare rapporti per:

   * Tutti gli operatori Adobe Campaign,
   * Operatori con diritti di accesso solo a una campagna di marketing,
   * un unico operatore per uso temporaneo,
   * Tutti gli operatori in accesso Web, ecc.

   Tali considerazioni devono anche tener conto delle questioni connesse ai diritti di accesso e alla sicurezza.

1. Definire il contenuto

   Quindi devi scoprire quale tipo di dati desideri visualizzare: indicatori di consegna, rapporti sui profili del database, ecc.

   È inoltre necessario conoscere la natura di questi dati (semplici, derivanti da un calcolo, significativi, ecc.), la sua posizione (in Adobe Campaign, in un sistema di terze parti), la sua frequenza di aggiornamento per definire la periodicità di calcolo (giornaliera, settimanale, on-the-fly), nonché il suo volume.

   I problemi relativi ai volumi di dati e agli aggiornamenti devono essere esaminati attentamente per evitare problemi di visualizzazione dei rapporti, soprattutto in termini di tempo. Consigliamo quindi di creare aggregati per precalcolare alcuni dati al di fuori del rapporto. Le tabelle che contengono i registri di tracciamento e consegna possono includere milioni di record: ciò significa che i dati devono essere aggregati tramite un flusso di lavoro da utilizzare in un rapporto.

## Ottimizzazione della creazione dei rapporti{#optimizing-report-creation}

### Volume dei dati {#data-volume}

Per garantire prestazioni ottimali, il volume dei dati manipolati non deve essere troppo grande.

Vale a dire:

* Il tempo di calcolo per un rapporto non deve mai superare i 5 minuti.

   Analogamente, durante la fase di progettazione, con un volume ridotto di dati, se il calcolo del report supera i 60 secondi, è necessario modificare i metodi di calcolo.

* Quando si utilizza il modulo Marketing Analytics, i dati di reporting non devono superare 10 milioni di righe.

Consigliamo inoltre di calcolare gli aggregati di notte e di utilizzare questi dati aggregati direttamente nei rapporti. Questi aggregati devono essere creati tramite flussi di lavoro dedicati per la gestione dei dati (query SQL).

È inoltre possibile calcolare i rapporti durante la notte e creare automaticamente una cronologia che può essere visualizzata in qualsiasi momento senza sovraccaricare il database.

### Query {#queries}

È consigliabile utilizzare le query SQL quando possibile ed evitare la post-elaborazione JavaScript. Se necessario, utilizza un’attività Script in un flusso di lavoro ed elimina i dati utilizzati per il calcolo. Puoi inoltre utilizzare i dati archiviati per accelerare il tempo di elaborazione.

In questo caso, è necessario utilizzare la sintassi seguente:

```
if(string(ctx@_historyId)!==""))
```

Le query che consentono di raccogliere i dati visualizzati nei rapporti non devono essere troppo complesse, specialmente se applicate a tutti i dati nel database. Per migliorare le prestazioni, può essere utile filtrare i dati prima di eseguire queste query: ciò significa che il calcolo riguarderà solo una parte dei dati.

### Prestazioni {#performances}

Le raccomandazioni di cui sopra consentono di ottimizzare il calcolo del rapporto.

Inoltre, Adobe Campaign consiglia i seguenti miglioramenti:

* Utilizza il modello dati: i campi indicizzati devono essere utilizzati principalmente per migliorare le formule di calcolo.

   Per trovare rapidamente un campo indicizzato, osserva il nome della colonna nell’interfaccia di Adobe Campaign: la freccia di ordinamento è evidenziata in rosso se il campo è indicizzato.

   Per ulteriori informazioni sugli indici, consulta [questa sezione](../../configuration/using/data-model-best-practices.md#indexes).

* Assicurati che il rapporto sia scalabile: il volume dei dati può aumentare notevolmente nel tempo.

   Analogamente, il volume dei dati manipolati durante le fasi di prova può differire dal volume effettivo dei dati in produzione. Ecco perché le fasi di prova sono importanti.

   Infine, i ritardi nell&#39;eliminazione dei dati devono essere noti e adattati quando necessario per una facile manipolazione dei dati.

   Per ulteriori informazioni sulla pulizia e la conservazione dei dati, consulta [questa sezione](../../configuration/using/data-model-best-practices.md#data-retention).

### Esportazione dei rapporti {#exporting-reports}

Recommendations specifico per l’esportazione dei rapporti è descritto in [questa sezione](../../reporting/using/actions-on-reports.md#exporting-a-report).
