---
solution: Campaign Classic
product: campaign
title: Utilizzo dei cubi per esplorare i dati
description: Utilizzo dei cubi per esplorare i dati
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 2%

---


# Utilizzo dei cubi per esplorare i dati{#using-cubes-to-explore-data}

Marketing Analytics semplifica la creazione di report e l&#39;identificazione e la selezione dei dati dal database tramite cubi. Questo consente di:

* Creare rapporti basati su cubi. Il processo è illustrato di seguito: [Esplorazione dei dati in un report](#exploring-the-data-in-a-report).
* Raccogliere i dati nel database e raggrupparli in elenchi, ad esempio per identificare e generare target e consegne. Per ulteriori informazioni, vedere [Creazione di una popolazione](#building-a-target-population)target.
* Inserire una tabella pivot in un rapporto, fare riferimento a un cubo esistente al suo interno. Per ulteriori informazioni, vedere [Inserimento di una tabella pivot in un rapporto](#inserting-a-pivot-table-into-a-report).

>[!NOTE]
>
>Marketing Analytics è necessario per creare o modificare i cubi. For more on this, refer to [About cubes](../../reporting/using/about-cubes.md).

## Esplorazione dei dati in un rapporto {#exploring-the-data-in-a-report}

### Passaggio 1 - Creazione di un report basato su un cubo {#step-1---creating-a-report-based-on-a-cube}

Per creare un rapporto basato su un cubo, fare clic sul **[!UICONTROL Create]** pulsante nell&#39; **[!UICONTROL Reports]** universo e selezionare il cubo che si desidera utilizzare.

Il processo è illustrato di seguito: [Creazione di un rapporto basato su un cubo](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube).

### Passaggio 2 - Selezione di linee e colonne {#step-2---selecting-lines-and-columns}

La visualizzazione predefinita mostra le prime due dimensioni del cubo (età e città, in questo caso).

I **[!UICONTROL Add]** pulsanti di ciascun asse consentono di aggiungere dimensioni.

![](assets/s_advuser_cube_in_report_03.png)

1. Selezionare le dimensioni da visualizzare nelle righe e nelle colonne della tabella. A questo scopo, trascinate e rilasciate le dimensioni disponibili come illustrato di seguito:
1. Selezionare dall&#39;elenco le dimensioni da aggiungere alla tabella:

   ![](assets/s_advuser_cube_in_report_04.png)

1. Selezionate quindi i parametri di questa dimensione.

   ![](assets/s_advuser_cube_in_report_04b.png)

   I parametri dipendono dal tipo di dati della dimensione selezionata.

   Ad esempio, per le date, possono essere disponibili diversi livelli. For more on this, refer to [Displaying measures](../../reporting/using/concepts-and-methodology.md#displaying-measures).

   In questo caso sono disponibili le seguenti opzioni:

   ![](assets/s_advuser_cube_in_report_config2.png)

   Potete effettuare le seguenti operazioni:

   * Espandi dati durante il caricamento: i valori verranno visualizzati per impostazione predefinita ogni volta che il rapporto viene aggiornato (valore predefinito: no).
   * Visualizza il totale alla fine della riga: quando i dati vengono visualizzati in colonne, un&#39;opzione aggiuntiva consente di visualizzare il totale alla fine della riga: alla tabella viene aggiunta una colonna (valore predefinito: sì).
   * Applicare un ordinamento: i valori della colonna possono essere ordinati in base al valore, all&#39;etichetta o alla misura (valore predefinito: per valore).
   * Visualizza i valori in ordine crescente (a-z, 0-9) o decrescente (z-a, 9-0).
   * Modificare il numero di colonne da visualizzare al caricamento (per impostazione predefinita: 200).

1. Fate clic **[!UICONTROL Ok]** per confermare: la dimensione viene aggiunta alle dimensioni esistenti.

   Il banner giallo sopra la tabella indica che sono state apportate delle modifiche: fare clic sul **[!UICONTROL Save]** pulsante per salvarli.

   ![](assets/s_advuser_cube_in_report_04c.png)

### Passaggio 3 - Configurazione delle misure da visualizzare {#step-3---configuring-the-measures-to-display}

Una volta inserite le righe e le colonne, indicate le misure da visualizzare e la relativa modalità di visualizzazione.

Per impostazione predefinita, viene visualizzata una sola misura. Per aggiungere o configurare misure:

1. Fai clic sul pulsante **[!UICONTROL Measures]**.

   ![](assets/s_advuser_cube_in_report_05.png)

1. Il **[!UICONTROL Use a measure]** pulsante consente di selezionare una delle misure esistenti.

   ![](assets/s_advuser_cube_in_report_08.png)

   Selezionare le informazioni da visualizzare e il tipo di formattazione. L&#39;elenco delle opzioni dipende dal tipo di misura configurato.

   ![](assets/s_advuser_cube_in_report_09.png)

   La configurazione complessiva delle misure è disponibile anche tramite l’ **[!UICONTROL Edit the configuration of the pivot table]** icona nell’intestazione.

   ![](assets/s_advuser_cube_in_report_config_02.png)

   È quindi possibile scegliere se visualizzare o meno le etichette delle misure. Per ulteriori informazioni, vedere [Configurazione della visualizzazione](../../reporting/using/concepts-and-methodology.md#configuring-the-display).

1. È possibile creare nuove misure utilizzando quelle esistenti. A tale scopo, fare clic **[!UICONTROL Create a measure]** e configurarlo.

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   Sono disponibili i seguenti tipi di misure:

   * Combinazione di misure: questo tipo di misura consente di creare la nuova misura utilizzando quelle esistenti:

      Gli operatori disponibili sono: somma, differenza, moltiplicazione e tasso.

   * Proporzione: questo tipo di misura consente di calcolare il numero di record misurati per una data dimensione. È possibile calcolare la proporzionalità in base a una dimensione o sub-dimensione.
   * Variazione: questa misura consente di calcolare la variazione dei valori di un livello.
   * Deviazione standard: questo tipo di misura consente di calcolare le deviazioni all&#39;interno di ciascun gruppo di celle rispetto alla media dei valori. Ad esempio, puoi confrontare il volume di acquisto per tutti i segmenti esistenti.

   La misura creata viene aggiunta al report.

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   Dopo aver creato una misura, potete modificarla e, se necessario, modificarne la configurazione. Per eseguire questa operazione, fare clic sul **[!UICONTROL Measures]** pulsante, quindi passare alla scheda della misura da modificare.

   Quindi fate clic **[!UICONTROL Edit the dynamic measure]** per accedere al menu delle impostazioni.

## Creazione di una popolazione bersaglio {#building-a-target-population}

La creazione di report tramite cubi consente di raccogliere i dati dalla tabella e salvarli in un elenco.

A questo scopo, aggiungeteli a un carrello ed elaboratene il contenuto.

Per raggruppare una popolazione in un elenco, procedere come segue:

1. Fare clic sulle celle contenenti la popolazione da raccogliere per selezionarle, quindi fare clic sull&#39; **[!UICONTROL Add to cart]** icona.

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   Per questo numero di volte necessario per raccogliere i vari profili

1. Fate clic sul **[!UICONTROL Show cart]** pulsante per visualizzarne il contenuto prima di eseguire l’esportazione.

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. Il **[!UICONTROL Export]** pulsante consente di raggruppare gli elementi del carrello in un elenco.

   È necessario specificare il nome dell&#39;elenco e il tipo di esportazione da eseguire.

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   Fate clic **[!UICONTROL Start]** per eseguire l&#39;esportazione.

1. Una volta completata l&#39;esportazione, un messaggio conferma l&#39;esecuzione e il numero di record elaborati.

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   È possibile salvare il contenuto del carrello o svuotarlo.

   L&#39;elenco è accessibile attraverso l&#39; **[!UICONTROL Profiles and targets]** universo.

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## Inserimento di una tabella pivot in un report {#inserting-a-pivot-table-into-a-report}

Per creare una tabella ed esplorare i dati contenuti in un cubo, procedere come segue:

1. Crea un nuovo rapporto con una singola pagina e inserisci una tabella pivot al suo interno. Per ulteriori informazioni, consulta [questa pagina](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table).

   ![](assets/s_advuser_cube_in_report_01.png)

1. Nella **[!UICONTROL Data]** scheda della pagina, selezionare un cubo per elaborare le dimensioni che contiene e visualizzare le misure calcolate.

   ![](assets/s_advuser_cube_in_report_02.png)

   Questo consente di creare il rapporto da visualizzare. Per ulteriori informazioni, vedere [Passaggio 2 - Selezione di righe e colonne](#step-2---selecting-lines-and-columns).

