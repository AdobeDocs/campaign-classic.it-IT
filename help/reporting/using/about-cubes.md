---
product: campaign
title: Informazioni sui cubi
description: Introduzione ai cubi
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# Introduzione ai cubi{#about-cubes}



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
