---
title: I cubi
seo-title: I cubi
description: I cubi
seo-description: null
page-status-flag: never-activated
uuid: 429bd5e9-288a-4c71-9b01-c4c5690f5abe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 42db3be8-ee02-4158-adcd-846420a32460
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# I cubi{#about-cubes}

L&#39;esplorazione dei dati nel database viene offerta tramite il modulo **Marketing Analytics** . Consente di analizzare e misurare i dati, calcolare le statistiche, semplificare e ottimizzare la creazione e il calcolo dei rapporti. Inoltre, Marketing Analytics consente di creare report e generare popolazioni target. Una volta identificati, questi vengono memorizzati in elenchi che possono essere utilizzati in Adobe Campaign (targeting, segmentazione, ecc.).

I cubi vengono utilizzati per generare alcuni rapporti incorporati, inclusi i rapporti sulla consegna (tracciamento della consegna, clic, aperture ecc.). I report basati su cubi possono essere utilizzati come standard solo per volumi di dati inferiori a 5 milioni di linee di fatto.

È possibile ampliare le capacità di esplorazione e analisi del database e semplificare la configurazione di rapporti e tabelle da parte degli utenti finali: è sufficiente selezionare un cubo esistente (completamente configurato) al momento della creazione del rapporto o della tabella per elaborare calcoli, misure e statistiche.

Una volta creati e configurati, i cubi vengono utilizzati nelle caselle di query dei report e nelle applicazioni Web. Possono essere utilizzati e modificati all&#39;interno di tabelle pivot.

>[!CAUTION]
>
>**Marketing Analytics** è un modulo di Adobe Campaign. Deve essere installato nell’istanza in uso in modo da poter utilizzare le funzionalità descritte di seguito.

Con il modulo Marketing Analytics, Campaign consente di:

1. Crea cubi in vista di:

   * aggregare i dati e memorizzarli in una tabella di lavoro per precalcolare gli indicatori in base alle esigenze degli utenti,
   * ridurre il volume dei dati coinvolti nei vari calcoli utilizzati per i rapporti e le query, ottimizzando in modo significativo i tempi di calcolo degli indicatori,
   * semplificare l&#39;accesso ai dati, consentendo agli utenti di manipolare i dati (preaggregati o meno) in base a diverse dimensioni.
   Per ulteriori informazioni, vedere [Creazione di indicatori](../../reporting/using/creating-indicators.md).

1. Creare tabelle pivot in vista di:

   * esplorazione di dati calcolati, misure configurate,
   * la selezione dei dati da visualizzare e la relativa modalità di visualizzazione,
   * personalizzare le misure e gli indicatori utilizzati,
   * strumenti di analisi interattiva per gli utenti con background non tecnico.
   Per ulteriori informazioni, vedere [Uso dei cubi per esplorare i dati](../../reporting/using/using-cubes-to-explore-data.md).

1. Crea una query utilizzando i dati calcolati e aggregati in un cubo.
1. Identificare le popolazioni e farvi riferimento negli elenchi.

## Terminologia {#terminology}

Quando si utilizzano i cubi, è necessario conoscere i seguenti concetti:

* Cube

   Un cubo è una rappresentazione di informazioni multidimensionali: fornisce agli utenti finali strutture progettate per l&#39;analisi interattiva dei dati.

* Tabella/schema dei fatti

   La tabella dei fatti (o schema dei fatti) contiene i dati grezzi o elementari sui quali verranno basate le analisi. Si tratta principalmente di grandi tabelle di volumi (eventualmente con tabelle collegate) con calcoli potenzialmente lunghi.

   Ad esempio, una tabella di fatti può essere: la tabella di trasmissione, la tabella di acquisto, ecc.

* Dimensione

   Le dimensioni consentono di segmentare i dati in gruppi: una volta create, le dimensioni fungono da assi di analisi. Nella maggior parte dei casi, per una data dimensione, verranno definiti più livelli. Ad esempio, per una dimensione temporale, i livelli saranno mesi, giorni, ore, minuti, ecc. Questo insieme di livelli rappresenta la gerarchia delle dimensioni e consente l&#39;analisi dei dati a vari livelli.

* Binding

   Per alcuni campi è possibile definire il binding con i valori dei gruppi e semplificare la lettura delle informazioni. Il binning viene applicato ai livelli

   È consigliabile definire il binning quando esiste la possibilità di molti valori diversi.

* Misura

   Le misure più frequenti sono somma, media, massima, minima, deviazione standard, ecc.

   Le misure possono essere calcolate: ad esempio, il tasso di accettazione di un&#39;offerta è il rapporto tra il numero di volte in cui è stata presentata rispetto al numero di volte in cui è stata accettata.

## Area di lavoro Cubo {#cube-workspace}

I cubi sono memorizzati nel **[!UICONTROL Administration > Configuration > Cubes]** nodo.

![](assets/s_advuser_cube_node.png)

I principali contesti di utilizzo per i cubi sono i seguenti:

* Le esportazioni di dati possono essere effettuate direttamente in un report, progettato nell&#39; **[!UICONTROL Reports]** universo della piattaforma Adobe Campaign.

   A tal fine, creare un nuovo rapporto e selezionare il cubo da utilizzare.

   ![](assets/cube_create_new.png)

   I cubi vengono visualizzati come modelli in base ai quali vengono creati i rapporti. Dopo aver scelto un modello, fate clic **[!UICONTROL Create]** per configurare e visualizzare il rapporto corrispondente.

   È possibile adattare le misure, modificare la modalità di visualizzazione o configurare la tabella, quindi visualizzare il rapporto utilizzando il pulsante principale.

   ![](assets/cube_display_new.png)

* È inoltre possibile fare riferimento a un cubo nella **[!UICONTROL Query]** casella di un rapporto per utilizzarne gli indicatori, come illustrato di seguito:

   ![](assets/s_advuser_query_using_a_cube.png)

* È inoltre possibile inserire una tabella pivot basata su un cubo in qualsiasi pagina di un rapporto. A tal fine, fare riferimento al cubo da utilizzare nella **[!UICONTROL Data]** scheda della tabella pivot sulla pagina interessata.

   ![](assets/s_advuser_cube_in_report.png)

   Per ulteriori informazioni, vedere [Esplorazione dei dati in un rapporto](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).

