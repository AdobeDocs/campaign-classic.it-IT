---
solution: Campaign Classic
product: campaign
title: Best practice per il reporting
description: Best practice per la segnalazione delle campagne
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---


# Best practice di reporting{#best-practices-reporting}

## Analisi delle esigenze{#analyzing-needs}

L’utilizzo di uno strumento di reporting dipende dal volume di dati da manipolare, dalla sua complessità e dal tipo di rapporto da impostare.

Per ottimizzare la creazione, l&#39;utilizzo e la durata di un rapporto, è necessario esaminare attentamente le esigenze che si desidera soddisfare. Questa prima analisi consente di identificare il tipo di rapporto da creare e la migliore modalità di creazione. Per creare il rapporto, effettua i seguenti passaggi:

1. Identificare la necessità

   Il primo passo è identificare chiaramente la necessità: ciò che desideri mostrare nel tuo rapporto e qual è il suo obiettivo (monitoraggio, analisi, esportazione di dati, ecc.).

    Adobe Campaign offre un&#39;ampia gamma di capacità di reporting. È importante analizzare la necessità di identificare le funzionalità più adatte.

   Ad esempio, potete:

   * Esplorare i dati nel database e definire le misure. Ulteriori informazioni [in questa sezione](../../reporting/using/about-cubes.md)
   * Aggiungere indicatori a un report esistente. Ulteriori informazioni [in questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)
   * Visualizzare i dati nel database. Ulteriori informazioni [in questa sezione](../../reporting/using/about-descriptive-analysis.md)
   * Crea un nuovo rapporto sulla consegna. Ulteriori informazioni [in questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Esportare dati dal database Adobe Campaign  (tramite un flusso di lavoro, fare riferimento a [questa sezione)](../../workflow/using/about-workflows.md)
   * Creare una tabella pivot. Ulteriori informazioni [in questa sezione](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Esplora i dati aggregati. Ulteriori informazioni [in questa sezione](../../reporting/using/about-cubes.md)
   * Utilizza una procedura guidata per analizzare i dati. Ulteriori informazioni [in questa sezione](../../reporting/using/about-descriptive-analysis.md)
   * Analizzare grandi volumi di dati. Ulteriori informazioni [in questa sezione](../../reporting/using/about-reports-creation-in-campaign.md)

1. Identificare la popolazione di destinazione

   Quindi devi scoprire chi sarà il destinatario del rapporto che desideri creare, sapere il tipo di pubblico che lo visualizzerà e la modalità di visualizzazione del rapporto (in un browser, in  Adobe Campaign, per un oggetto specifico, per l&#39;intera piattaforma, ecc.).

   Potete anche creare rapporti per:

   * Tutti  operatori Adobe Campaign,
   * Operatori con diritti di accesso esclusivamente a una campagna di marketing,
   * un unico operatore per uso temporaneo,
   * Tutti gli operatori in accesso Web, ecc.

   Tali considerazioni devono anche tener conto delle questioni connesse ai diritti di accesso e alla sicurezza.

1. Definire il contenuto

   È quindi necessario individuare il tipo di dati da visualizzare: indicatori di consegna, rapporti sui profili del database, ecc.

   È inoltre necessario conoscere la natura di questi dati (semplici, risultanti da un calcolo, significativi, ecc.), la sua posizione (in  Adobe Campaign, in un sistema di terze parti), la sua frequenza di aggiornamento per definire la periodicità di calcolo (giornaliera, settimanale, on-the-fly), così come il suo volume.

   I problemi legati ai volumi di dati e agli aggiornamenti devono essere esaminati attentamente per evitare problemi di visualizzazione dei report, soprattutto in termini di tempo. È pertanto consigliabile creare aggregati per precalcolare alcuni dati al di fuori del rapporto. Le tabelle che contengono i registri di monitoraggio e consegna possono includere milioni di record: ciò significa che i dati devono essere aggregati tramite un flusso di lavoro da utilizzare in un report.

## Ottimizzazione della creazione dei report{#optimizing-report-creation}

### Volume dei dati {#data-volume}

Per garantire prestazioni ottimali, il volume dei dati manipolati non deve essere troppo grande.

In particolare:

* Il tempo di calcolo per un rapporto non deve mai superare i 5 minuti.

   Analogamente, durante la fase di progettazione, con un volume ridotto di dati, se il calcolo del report supera i 60 secondi, è necessario modificare i metodi di calcolo.

* Quando si utilizza il modulo Marketing Analytics, i dati di reporting non devono superare 10 milioni di righe.

È inoltre consigliabile calcolare gli aggregati di notte e utilizzare questi dati aggregati direttamente nei report. Questi aggregati devono essere creati tramite flussi di lavoro dedicati per la gestione dei dati (query SQL).

È inoltre possibile calcolare i rapporti durante la notte e creare automaticamente una cronologia che possa essere visualizzata in qualsiasi momento senza sovraccaricare il database.

### Query {#queries}

È consigliabile utilizzare le query SQL quando possibile ed evitare la post-elaborazione JavaScript. Se necessario, utilizzare un&#39;attività Script in un flusso di lavoro ed eliminare i dati utilizzati per il calcolo. È inoltre possibile utilizzare i dati archiviati per accelerare il tempo di elaborazione.

In questo caso, deve essere utilizzata la sintassi seguente:

```
if(string(ctx@_historyId)!==""))
```

Le query che consentono di raccogliere i dati visualizzati nei rapporti non devono essere troppo complesse, specialmente se applicate a tutti i dati nel database. Per migliorare le prestazioni, può essere utile filtrare i dati prima di eseguire queste query: ciò significa che il calcolo riguarda solo una parte dei dati.

### Prestazioni {#performances}

Le raccomandazioni di cui sopra consentono di ottimizzare il calcolo dei report.

Inoltre,  Adobe Campaign consiglia i seguenti miglioramenti:

* Utilizza il modello dati: i campi indicizzati devono essere utilizzati principalmente per migliorare le formule di calcolo.

   Per trovare rapidamente un campo indicizzato, osservare il nome della colonna nell’interfaccia Adobe Campaign : la freccia di ordinamento è sottolineata in rosso se il campo è indicizzato.

   For more on indexes, refer to [this section](../../configuration/using/data-model-best-practices.md#indexes).

* Assicurati che il rapporto sia scalabile: il volume dei dati può aumentare notevolmente nel tempo.

   Analogamente, il volume dei dati manipolati durante le fasi di prova può differire dal volume effettivo dei dati in produzione. Ecco perché le fasi di prova sono importanti.

   Infine, i ritardi nella rimozione dei dati devono essere noti e adattati quando necessario per una facile manipolazione dei dati.

   Per ulteriori informazioni sulla pulizia e la conservazione dei dati, consulta [questa sezione](../../configuration/using/data-model-best-practices.md#data-retention).

### Esportazione dei rapporti {#exporting-reports}

Recommendations specifico per l’esportazione dei rapporti è descritto in [questa sezione](../../reporting/using/actions-on-reports.md#exporting-a-report).
