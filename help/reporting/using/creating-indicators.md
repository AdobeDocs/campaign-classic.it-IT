---
title: Creazione di indicatori
seo-title: Creazione di indicatori
description: Creazione di indicatori
seo-description: null
page-status-flag: never-activated
uuid: 3caaba6b-b6c8-4b64-b123-d7098e9ddc7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: a5fc6c78-b4fb-41fd-a072-7be4ece3c554
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 1%

---


# Creazione di indicatori{#creating-indicators}

Per rendere funzionale un cubo, è necessario identificare le dimensioni e le misure rilevanti e crearle nel cubo.

Per creare un cubo, effettua i seguenti passaggi:

1. Selezionare la tabella di lavoro. Fare riferimento a [Selezione della tabella](#selecting-the-work-table)di lavoro.
1. Definite le dimensioni. Fare riferimento a [Definizione delle dimensioni](#defining-dimensions).
1. Definite le misure. Fare riferimento agli indicatori [di](#building-indicators)generazione.
1. Creare aggregati (facoltativo). Fare riferimento a [Calcolo e utilizzo degli aggregati](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

In questo esempio viene illustrato come creare rapidamente un cubo semplice in un rapporto per esportare le relative misure.

Le fasi di implementazione sono descritte di seguito. Le opzioni e le descrizioni esaustive sono disponibili nelle altre sezioni di questo capitolo.

## Selezione della tabella di lavoro {#selecting-the-work-table}

Per creare un cubo, fate clic sul **[!UICONTROL New]** pulsante sopra l’elenco dei cubi.

![](assets/s_advuser_cube_create.png)

Selezionare lo schema dei fatti, ovvero lo schema che contiene gli elementi da esplorare. In questo esempio, selezioneremo la tabella **Destinatario** .

![](assets/s_advuser_cube_wz_02.png)

Fate clic **[!UICONTROL Save]** per creare il cubo: verrà visualizzato nell’elenco dei cubi e potrebbe essere configurato utilizzando le schede appropriate.

Fai clic sul **[!UICONTROL Filter the source data...]** collegamento per applicare i calcoli di questo Cubo a una selezione di dati nel database.

![](assets/s_advuser_cube_wz_03.png)

## Definizione delle dimensioni {#defining-dimensions}

Gli Dimension coincidono con gli assi di analisi definiti per ciascun cubo in base al relativo schema di fatti. Queste sono le dimensioni esaminate nell&#39;analisi, come l&#39;ora (anno, mese, data...), una classificazione di prodotti o contratti (famiglia, riferimento, ecc.), un segmento di popolazione (per città, gruppo di età, stato, ecc.).

Questi assi di analisi sono definiti nella **[!UICONTROL Dimension]** scheda del cubo.

Fai clic sul **[!UICONTROL Add]** pulsante per creare una nuova dimensione, quindi fai clic sull&#39;icona **[!UICONTROL Expression field]**, **[!UICONTROL Edit expression]** per selezionare il campo che contiene i dati in questione.

![](assets/s_advuser_cube_wz_04.png)

* Per iniziare, seleziona l&#39; **età** del destinatario. Per questo campo è possibile definire il binding con le pagine di gruppo e semplificare la lettura delle informazioni. È consigliabile utilizzare il binning quando esiste la probabilità di diversi valori separati.

   Per eseguire questa operazione, selezionare l&#39; **[!UICONTROL Enable binning]** opzione. Le modalità di binding sono descritte in [Binding](../../reporting/using/concepts-and-methodology.md#data-binning)dei dati.

   ![](assets/s_advuser_cube_wz_05.png)

* Aggiungi una dimensione di tipo **Data** . Qui, vogliamo visualizzare le date di creazione del profilo del destinatario

   A tal fine, fare clic **[!UICONTROL Add]** e selezionare il **[!UICONTROL Creation date]** campo nella tabella dei destinatari.

   ![](assets/s_advuser_cube_wz_06.png)

   È possibile selezionare la modalità di visualizzazione della data. A questo scopo, selezionate la gerarchia da utilizzare e i livelli da generare:

   ![](assets/s_advuser_cube_wz_07.png)

   Nel nostro esempio, vogliamo visualizzare solo anni, mesi e giorni, dal momento che non è possibile lavorare con settimane e semestri/mesi contemporaneamente: questi livelli non sono compatibili.

* Crea un&#39;altra dimensione per analizzare i dati relativi alla città del destinatario

   A tal fine, aggiungere una nuova dimensione e selezionare la città nel **[!UICONTROL Location]** nodo dello schema destinatario.

   ![](assets/s_advuser_cube_wz_08.png)

   È possibile abilitare il binding per semplificare la lettura delle informazioni e collegare i valori a un&#39;enumerazione.

   ![](assets/s_advuser_cube_wz_09.png)

   Seleziona l&#39;enumerazione dall&#39;elenco a discesa

   ![](assets/s_advuser_cube_wz_10.png)

   Vengono visualizzati solo i valori nell&#39;enumerazione. Gli altri verranno raggruppati sotto l&#39;etichetta definita nel **[!UICONTROL Label of the other values]** campo.

   Per ulteriori informazioni, vedere Gestione [dinamica dei](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)contenitori.

## Indicatori di costruzione {#building-indicators}

Una volta definite le dimensioni, è necessario specificare una modalità di calcolo per i valori da visualizzare nelle celle. A tal fine, creare gli indicatori corrispondenti nella **[!UICONTROL Measures]** scheda: crea nel rapporto tutte le misure possibili quante colonne verranno visualizzate.

A questo scopo, eseguire i seguenti passaggi:

1. Fai clic sul pulsante **[!UICONTROL Add]**.
1. Selezionare il tipo di misura e la formula da applicare. Qui vogliamo contare il numero di donne tra i beneficiari.

   La misura è basata sullo schema dei fatti e utilizza l&#39; **[!UICONTROL Count]** operatore.

   ![](assets/s_advuser_cube_wz_11.png)

   Il **[!UICONTROL Filter the measure data...]** collegamento consente di selezionare solo donne. Per ulteriori informazioni sulla definizione delle misure e delle opzioni disponibili, vedere [Definizione delle misure](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. Immettete l’etichetta della misura e salvatela.

   ![](assets/s_advuser_cube_wz_13.png)

1. Salva il cubo.

## Creazione di un rapporto basato su un cubo {#creating-a-report-based-on-a-cube}

Una volta configurato, il cubo può essere utilizzato come modello per creare un nuovo rapporto.

Per eseguire questa operazione:

1. Fare clic sul **[!UICONTROL Create]** pulsante dell&#39; **[!UICONTROL Reports]** universo e selezionare il cubo appena creato.

   ![](assets/s_advuser_cube_wz_14.png)

1. Fate clic sul **[!UICONTROL Create]** pulsante per confermare: questo ti porterà alla configurazione del report e alla pagina di visualizzazione.

   Per impostazione predefinita, le prime due dimensioni disponibili sono offerte in righe e colonne, ma nella tabella non viene visualizzato alcun valore. Per generare la tabella, fare clic sull’icona principale:

   ![](assets/s_advuser_cube_wz_15.png)

1. Potete cambiare gli assi della quota, eliminarli, aggiungere nuove misure, ecc. Le possibili operazioni sono descritte qui di seguito: [Utilizzo dei cubi per esplorare i dati](../../reporting/using/using-cubes-to-explore-data.md).

   A tal fine, utilizzate le icone appropriate.

   ![](assets/s_advuser_cube_wz_16.png)

