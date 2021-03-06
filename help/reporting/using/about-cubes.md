---
product: campaign
title: Introduzione ai cubi
description: Introduzione ai cubi
feature: Reporting
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 11%

---

# Introduzione ai cubi{#about-cubes}

![](../../assets/common.svg)

L&#39;esplorazione dei dati nel database viene offerta tramite il **Analisi di marketing** modulo . Consente di analizzare e misurare i dati, calcolare le statistiche, semplificare e ottimizzare la creazione e il calcolo dei rapporti. Inoltre, Marketing Analytics consente di creare report e generare popolazioni target. Una volta identificati, vengono memorizzati in elenchi che possono essere utilizzati in Adobe Campaign (targeting, segmentazione, ecc.).

I cubi vengono utilizzati per generare alcuni rapporti incorporati, inclusi i rapporti di consegna (tracciamento consegna, clic, aperture, ecc.). I report basati su cubi possono essere utilizzati come standard solo per volumi di dati inferiori a 5 milioni di linee di fatto.

Puoi estendere le capacità di esplorazione e di analisi del database e semplificare la configurazione di report e tabelle da parte degli utenti finali: tutto ciò che devono fare è selezionare un cubo esistente (completamente configurato) durante la creazione del report o della tabella per elaborare calcoli, misure e statistiche.

Una volta creati e configurati, i cubi vengono utilizzati nelle caselle di query dei report e nelle applicazioni web. Possono essere utilizzati e manipolati all’interno di tabelle pivot.

>[!CAUTION]
>
>**Analisi di marketing** è un modulo Adobe Campaign. Deve essere installato nell’istanza in modo da poter utilizzare le funzionalità descritte di seguito.

Utilizza il modulo Campaign Marketing Analytics per:

1. Creazione di cubi

   * aggregare e memorizzare i dati in una tabella di lavoro per precalcolare gli indicatori in base alle esigenze degli utenti,
   * ridurre il volume dei dati coinvolti nei vari calcoli utilizzati per i rapporti e le query, ottimizzando in modo significativo i tempi di calcolo degli indicatori,
   * semplifica l’accesso ai dati, consente agli utenti di manipolare i dati (preaggregati o meno) a seconda delle varie dimensioni.

   Per ulteriori informazioni, consulta [Creare indicatori](../../reporting/using/creating-indicators.md).

1. Creare tabelle pivot

   * esplorare dati calcolati, misure configurate,
   * selezionare i dati da visualizzare e la relativa modalità di visualizzazione,
   * personalizzare le misure e gli indicatori utilizzati,
   * offrono strumenti di analisi interattivi agli utenti con background non tecnico.

   Per ulteriori informazioni, consulta [Utilizzare i cubi per esplorare i dati](../../reporting/using/using-cubes-to-explore-data.md).

1. Crea una query utilizzando dati calcolati e aggregati in un cubo.
1. Identificare le popolazioni e farvi riferimento negli elenchi.

## Terminologia {#terminology}

Di seguito sono elencati i termini specifici quando si lavora con i cubi.

* **Cubo** - Un cubo è una rappresentazione di informazioni multidimensionali: fornisce agli utenti finali strutture progettate per l’analisi interattiva dei dati.

* **Tabella/schema dei fatti** - La tabella dei fatti (o schema dei fatti) contiene i dati grezzi o elementari su cui verranno basate le analisi. Si tratta principalmente di grandi tabelle di volumi (eventualmente con tabelle collegate) con calcoli potenzialmente lunghi. Ad esempio, una tabella dei fatti può essere: la tabella del registro di trasmissione, la tabella degli acquisti, ecc.

* **Dimension** - I Dimension ti consentono di segmentare i dati in gruppi: una volta create, le quote fungono da assi di analisi. Nella maggior parte dei casi, per una data dimensione, verranno definiti diversi livelli. Ad esempio, per una dimensione temporale, i livelli saranno mesi, giorni, ore, minuti, ecc. Questo insieme di livelli rappresenta la gerarchia delle dimensioni e consente diversi livelli di analisi dei dati.

* **Binning** - Per alcuni campi è possibile definire il binding ai valori dei gruppi e semplificare la lettura delle informazioni. Il binding viene applicato ai livelli. È consigliabile definire il binding quando è presente una possibilità di valori diversi.

* **Misura** - Le misure più frequenti sono la somma, la media, il massimo, il minimo, la deviazione standard, ecc. Le misure possono essere calcolate: ad esempio, il tasso di accettazione di un&#39;offerta è il rapporto tra il numero di volte in cui è stata presentata rispetto al numero di volte in cui è stata accettata.

## Area di lavoro dei cubi {#cube-workspace}

I cubi vengono memorizzati nel **[!UICONTROL Administration > Configuration > Cubes]** nodo.

![](assets/s_advuser_cube_node.png)

I principali contesti d&#39;uso per i cubi sono i seguenti:

* Le esportazioni di dati possono essere effettuate direttamente in un rapporto, progettato nel **[!UICONTROL Reports]** della piattaforma Adobe Campaign.

   A questo scopo, crea un nuovo report e seleziona il cubo che desideri utilizzare.

   ![](assets/cube_create_new.png)

   I cubi vengono visualizzati come modelli in base ai quali vengono creati i rapporti. Dopo aver scelto un modello, fai clic su **[!UICONTROL Create]** per configurare e visualizzare il rapporto corrispondente.

   È possibile adattare le misure, modificare la modalità di visualizzazione o configurare la tabella, quindi visualizzare il rapporto utilizzando il pulsante principale.

   ![](assets/cube_display_new.png)

* È inoltre possibile fare riferimento a un cubo nel **[!UICONTROL Query]** casella di un rapporto per utilizzare i relativi indicatori, come mostrato di seguito:

   ![](assets/s_advuser_query_using_a_cube.png)

* È inoltre possibile inserire una tabella pivot basata su un cubo in qualsiasi pagina di un report. A questo scopo, fai riferimento al cubo da utilizzare nel **[!UICONTROL Data]** scheda della tabella pivot sulla pagina interessata.

   ![](assets/s_advuser_cube_in_report.png)

   Per ulteriori informazioni, consulta [Esplorare i dati in un rapporto](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
