---
product: campaign
title: Informazioni sui cubi
description: Introduzione ai cubi
feature: Reporting, Monitoring
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
hide: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%
---
# Introduzione ai cubi{#about-cubes}



## Terminologia {#terminology}

Di seguito sono elencati i termini specifici per l&#39;utilizzo dei cubi.

* **Cubo** - Un cubo è una rappresentazione di informazioni multidimensionali: fornisce agli utenti finali strutture progettate per l&#39;analisi dei dati interattivi.

* **Tabella/schema fatti** - La tabella dei fatti (o schema dei fatti) contiene i dati non elaborati o elementari su cui verranno basate le analisi. Si tratta principalmente di tabelle di volumi di grandi dimensioni (eventualmente con tabelle collegate) con calcoli potenzialmente lunghi. Ad esempio, una fact table può essere: la tabella broadlog, la tabella purchase e così via.

* **Dimension** - Le dimensioni consentono di segmentare i dati in gruppi: una volta create, le dimensioni fungono da assi di analisi. Nella maggior parte dei casi, per una determinata dimensione, vengono definiti diversi livelli. Ad esempio, per una dimensione temporale, i livelli saranno mesi, giorni, ore, minuti e così via. Questo set di livelli rappresenta la gerarchia delle dimensioni e abilita vari livelli di analisi dei dati.

* **Binning** - Per alcuni campi è possibile definire il binning per raggruppare i valori e semplificare la lettura delle informazioni. Binning applicato ai livelli. Si consiglia di definire il binning quando esiste la possibilità di molti valori diversi.

* **Misura** - Le misure più frequenti sono somma, media, massima, minima, deviazione standard e così via. Le misure possono essere calcolate: ad esempio, il tasso di accettazione di un’offerta è il rapporto tra il numero di volte in cui è stata presentata e il numero di volte in cui è stata accettata.

## Area di lavoro del cubo {#cube-workspace}

I cubi sono archiviati nel nodo **[!UICONTROL Administration > Configuration > Cubes]**.

![](assets/s_advuser_cube_node.png)

I principali contesti di utilizzo dei cubi sono i seguenti:

* Le esportazioni di dati possono essere eseguite direttamente in un rapporto, progettato nella scheda **[!UICONTROL Reports]** della piattaforma Adobe Campaign.

  A questo scopo, crea un nuovo rapporto e seleziona il cubo da utilizzare.

  ![](assets/cube_create_new.png)

  I cubi vengono visualizzati come modelli in base ai rapporti creati. Dopo aver scelto un modello, fare clic su **[!UICONTROL Create]** per configurare e visualizzare il report corrispondente.

  Puoi adattare le misure, modificare la modalità di visualizzazione o configurare la tabella, quindi visualizzare il rapporto utilizzando il pulsante principale.

  ![](assets/cube_display_new.png)

* È inoltre possibile fare riferimento a un cubo nella casella **[!UICONTROL Query]** di un report per utilizzare i relativi indicatori, come illustrato di seguito:

  ![](assets/s_advuser_query_using_a_cube.png)

* È inoltre possibile inserire una tabella pivot basata su un cubo in qualsiasi pagina di un report. A tale scopo, fare riferimento al cubo da utilizzare nella scheda **[!UICONTROL Data]** della tabella pivot sulla pagina interessata.

  ![](assets/s_advuser_cube_in_report.png)

  Per ulteriori informazioni, consulta [Esplorare i dati in un report](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
