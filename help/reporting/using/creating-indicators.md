---
product: campaign
title: Creare indicatori
description: Creare indicatori
feature: Reporting
hide: true
hidefromtoc: true
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 2%

---

# Creare indicatori{#creating-indicators}



Per rendere funzionale un cubo, è necessario identificare le dimensioni e le misure rilevanti e crearle nel cubo.

Per creare un cubo, attenersi alla procedura descritta di seguito.

1. Selezionare la tabella di lavoro. Fai riferimento a [Seleziona la tabella di lavoro](#selecting-the-work-table).
1. Definite le quote. Fai riferimento a [Definire le dimensioni](#defining-dimensions).
1. Definire le misure. Fai riferimento a [Creare indicatori](#building-indicators).
1. Creare aggregati (facoltativo). Fai riferimento a [Calcolare e utilizzare gli aggregati](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

In questo esempio viene illustrato come creare rapidamente un cubo semplice in un report per esportare le relative misure.

I passaggi di implementazione sono descritti di seguito. Opzioni e descrizioni dettagliate sono disponibili nelle altre sezioni di questo capitolo.

## Seleziona la tabella di lavoro {#selecting-the-work-table}

Per creare un cubo, fare clic su **[!UICONTROL New]** sopra l&#39;elenco dei cubi.

![](assets/s_advuser_cube_create.png)

Seleziona lo schema dei fatti, ovvero lo schema che contiene gli elementi che desideri esplorare. In questo esempio, selezioneremo il **Destinatario** tabella.

![](assets/s_advuser_cube_wz_02.png)

Clic **[!UICONTROL Save]** per creare il cubo: verrà visualizzato nell&#39;elenco dei cubi e potrà essere configurato utilizzando le schede appropriate.

Fai clic su **[!UICONTROL Filter the source data...]** collegamento per applicare i calcoli del cubo a una selezione di dati nel database.

![](assets/s_advuser_cube_wz_03.png)

## Definire le dimensioni {#defining-dimensions}

I Dimension coincidono con gli assi di analisi definiti per ciascun cubo in base al relativo schema fact. Queste sono le dimensioni analizzate nell’analisi, ad esempio il tempo (anno, mese, data...), una classificazione di prodotti o contratti (famiglia, riferimento, ecc.), un segmento di popolazione (per città, fascia di età, stato, ecc.).

Questi assi di analisi sono definiti nel **[!UICONTROL Dimension]** del cubo.

Fai clic su **[!UICONTROL Add]** per creare una nuova dimensione, quindi nella **[!UICONTROL Expression field]**, fare clic su **[!UICONTROL Edit expression]** per selezionare il campo che contiene i dati interessati.

![](assets/s_advuser_cube_wz_04.png)

* Per iniziare, seleziona il destinatario **Età**. Per questo campo, puoi definire il binning per raggruppare le pagine e semplificare la lettura delle informazioni. È consigliabile utilizzare il binning quando è probabile che siano presenti più valori separati.

   A questo scopo, seleziona la **[!UICONTROL Enable binning]** opzione. Le modalità di binning sono descritte in [Binning dati](../../reporting/using/concepts-and-methodology.md#data-binning).

   ![](assets/s_advuser_cube_wz_05.png)

* Aggiungi un **Data** dimensione del tipo. In questo caso, vogliamo visualizzare le date di creazione del profilo del destinatario

   A questo scopo, fai clic su **[!UICONTROL Add]** e seleziona la **[!UICONTROL Creation date]** nella tabella dei destinatari.

   ![](assets/s_advuser_cube_wz_06.png)

   È possibile selezionare la modalità di visualizzazione della data. A questo scopo, seleziona la gerarchia da utilizzare e i livelli da generare:

   ![](assets/s_advuser_cube_wz_07.png)

   Nel nostro esempio, vogliamo visualizzare solo anni, mesi e giorni, poiché non è possibile lavorare con settimane e semestri/mesi contemporaneamente: questi livelli non sono compatibili.

* Crea un’altra dimensione per analizzare i dati relativi alla città del destinatario

   A questo scopo, aggiungi una nuova dimensione e seleziona la città nel **[!UICONTROL Location]** nodo dello schema del destinatario.

   ![](assets/s_advuser_cube_wz_08.png)

   È possibile abilitare il binning per semplificare la lettura delle informazioni e collegare i valori a un&#39;enumerazione.

   ![](assets/s_advuser_cube_wz_09.png)

   Seleziona l’enumerazione dall’elenco a discesa

   ![](assets/s_advuser_cube_wz_10.png)

   Verranno visualizzati solo i valori nell’enumerazione. Gli altri saranno raggruppati sotto l’etichetta definita nella **[!UICONTROL Label of the other values]** campo.

   Per ulteriori informazioni, consulta [Gestione dinamica dei contenitori](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins).

## Creare indicatori {#building-indicators}

Una volta definite le dimensioni, è necessario specificare una modalità di calcolo per i valori da visualizzare nelle celle. A questo scopo, crea gli indicatori corrispondenti nel **[!UICONTROL Measures]** scheda: crea tutte le misure presenti nelle colonne da visualizzare nel rapporto che utilizzerà il cubo.

A questo scopo, esegui i seguenti passaggi:

1. Fai clic sul pulsante **[!UICONTROL Add]**.
1. Selezionare il tipo di misura e la formula da applicare. Qui vogliamo contare il numero di donne tra i destinatari.

   La nostra misura si basa sullo schema dei fatti e utilizza **[!UICONTROL Count]** operatore.

   ![](assets/s_advuser_cube_wz_11.png)

   Il **[!UICONTROL Filter the measure data...]** consente di selezionare solo donne. Per ulteriori informazioni sulla definizione delle misure e delle opzioni disponibili, consulta [Definire le misure](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. Immettere l&#39;etichetta della misura e salvarla.

   ![](assets/s_advuser_cube_wz_13.png)

1. Salvare il cubo.

## Creare un rapporto basato su un cubo {#creating-a-report-based-on-a-cube}

Una volta configurato, il cubo può essere utilizzato come modello per la creazione di un nuovo report.

Per eseguire questa operazione:

1. Fai clic su **[!UICONTROL Create]** pulsante della **[!UICONTROL Reports]** e selezionare il cubo appena creato.

   ![](assets/s_advuser_cube_wz_14.png)

1. Fai clic su **[!UICONTROL Create]** pulsante per confermare: questo pulsante ti porterà alla pagina configurazione e visualizzazione del rapporto.

   Per impostazione predefinita, le prime due dimensioni disponibili sono offerte in linee e colonne, ma nella tabella non viene visualizzato alcun valore. Per generare la tabella, fai clic sull’icona principale:

   ![](assets/s_advuser_cube_wz_15.png)

1. Potete cambiare gli assi della quota, eliminarli, aggiungere nuove misure e così via. Le operazioni possibili sono descritte in [questa pagina](../../reporting/using/using-cubes-to-explore-data.md).

   A questo scopo, utilizza le icone appropriate.

   ![](assets/s_advuser_cube_wz_16.png)
