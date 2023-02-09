---
product: campaign
title: Ciclo di vita dei dati
description: Ulteriori informazioni sul ciclo di vita dei dati nei flussi di lavoro
feature: Workflows, Data Management
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 5%

---

# Ciclo di vita dei dati {#data-life-cycle}

![](../../assets/v7-only.svg)

## Tabella di lavoro {#work-table}

Nei flussi di lavoro, i dati trasportati da un’attività all’altra vengono memorizzati in una tabella di lavoro temporanea.

Questi dati possono essere visualizzati e analizzati facendo clic con il pulsante destro del mouse sulla transizione appropriata.

![](assets/wf-right-click-analyze.png)

A questo scopo, seleziona il menu corrispondente:

* Visualizzazione del target

   In questo menu vengono visualizzati i dati disponibili sulla popolazione target e la struttura della tabella di lavoro (**[!UICONTROL Schema]** ).

   ![](assets/wf-right-click-display.png)

   Per ulteriori informazioni, consulta [Tabelle di lavoro e schema del flusso di lavoro](monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Analisi del target

   Questo menu ti consente di accedere alla procedura guidata di analisi descrittiva che ti consente di produrre statistiche e rapporti sui dati della transizione.

   Per ulteriori informazioni, consulta questa [sezione](../../reporting/using/using-the-descriptive-analysis-wizard.md).

I dati di destinazione vengono eliminati durante l’esecuzione del flusso di lavoro. È accessibile solo l’ultima tabella di lavoro. È possibile configurare il flusso di lavoro in modo che tutte le tabelle di lavoro rimangano accessibili: controlla **[!UICONTROL Keep the result of interim populations between two executions]** nelle proprietà del flusso di lavoro.

Tuttavia, ti consigliamo di evitare di attivare questa opzione in caso di quantità significative di dati.

![](assets/wf-purge-data-option.png)

## Targeting dei dati {#target-data}

I dati memorizzati nella tabella di lavoro del flusso di lavoro sono accessibili nei campi di personalizzazione.

Ciò ti consente di utilizzare i dati raccolti tramite un elenco o in base alle risposte a un sondaggio in una consegna. A questo scopo, utilizza la sintassi seguente:

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** Gli elementi di personalizzazione di tipo (targetData) non sono disponibili per i flussi di lavoro di targeting. Il target di consegna deve essere generato nel flusso di lavoro e specificato nella transizione in entrata della consegna.

Se desideri creare bozze di consegna, il target della bozza deve essere generato in base alla variabile **[!UICONTROL Address substitution]** in modo che i dati di personalizzazione possano essere immessi. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

Nell’esempio seguente, raccoglieremo un elenco di informazioni sui clienti da utilizzare in un’e-mail personalizzata.

Applica i seguenti passaggi:

1. Crea un flusso di lavoro per raccogliere le informazioni, riconcilialo con i dati già presenti nel database, quindi avvia una consegna.

   ![](assets/wf-targetdata-sample-1.png)

   Nel nostro esempio, il contenuto del file è il seguente:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Per caricare il file, effettua le seguenti operazioni:

   ![](assets/wf-targetdata-sample-2.png)

1. Configura le **[!UICONTROL Enrichment]** digita attività per riconciliare i dati raccolti con quelli già presenti nel database Adobe Campaign.

   In questo caso, la chiave di riconciliazione è il numero di account:

   ![](assets/wf-targetdata-sample-3.png)

1. Quindi configura la **[!UICONTROL Delivery]**: viene creato in base a un modello e i destinatari sono specificati dalla transizione in entrata.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Per personalizzare la consegna possono essere utilizzati solo i dati contenuti nella transizione. **targetData** i campi di personalizzazione del tipo sono disponibili solo per la popolazione in entrata del **[!UICONTROL Delivery]** attività.

1. Nel modello di consegna, utilizza i campi raccolti nel flusso di lavoro.

   A questo scopo, inserisci **[!UICONTROL Target extension]** digitare campi di personalizzazione.

   ![](assets/wf-targetdata-sample-5.png)

   In questo caso, vogliamo inserire il genere musicale e il tipo di supporto preferiti dal cliente (CD o DVD) come indicato nel file raccolto dal flusso di lavoro.

   In più, aggiungeremo un coupon per i titolari di carte fedeltà, vale a dire i destinatari per i quali il valore &quot;Carta&quot; è uguale a 1.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** I dati di tipo (targetData) vengono inseriti nelle consegne utilizzando le stesse caratteristiche di tutti i campi di personalizzazione. Possono anche essere utilizzati nell&#39;oggetto, nelle etichette di collegamento o nei link stessi.

   I messaggi indirizzati ai destinatari raccolti conterranno i seguenti dati:

   ![](assets/wf-targetdata-sample-7.png)
