---
title: Utilizzo di aggregati
seo-title: Utilizzo di aggregati
description: Utilizzo di aggregati
seo-description: null
page-status-flag: never-activated
uuid: 70556745-56b2-4f22-bbc5-7f8106fb0d4a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9ca649b4-2226-4cfe-bae1-4632c421975b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 2%

---


# Utilizzo di aggregati{#using-aggregates}

Questo caso d’uso descrive come identificare automaticamente gli ultimi destinatari aggiunti al database.

Utilizzando la procedura seguente, la data di creazione dei destinatari nel database viene confrontata con l&#39;ultima data nota in cui un destinatario è stato creato utilizzando un aggregato. Vengono selezionati anche tutti i destinatari creati lo stesso giorno.

Per eseguire un filtro di tipo Data **creazione = data max (data creazione)** sui destinatari, è necessario eseguire un flusso di lavoro per eseguire la procedura seguente:

1. Recuperare i destinatari del database utilizzando una query di base. Per ulteriori informazioni su questo passaggio, vedere [Creazione di una query](../../workflow/using/query.md#creating-a-query).
1. Calcola l&#39;ultima data nota in cui è stato creato un destinatario utilizzando il risultato generato dalla funzione di aggregazione **massima (data di creazione)** .
1. Collega ciascun destinatario alla funzione di aggregazione e crea lo stesso schema.
1. Filtrare i destinatari utilizzando l&#39;aggregazione tramite lo schema modificato.

![](assets/datamanagement_usecase_1.png)

## Passaggio 1: Calcolo del risultato aggregato {#step-1--calculating-the-aggregate-result}

1. Creare una query. Qui l&#39;obiettivo è calcolare l&#39;ultima data di creazione nota di tutti i destinatari nel database. La query non contiene pertanto un filtro.
1. Seleziona **[!UICONTROL Add data]**.
1. Nelle finestre che si aprono, selezionare **[!UICONTROL Data linked to the filtering dimension]** quindi **[!UICONTROL Filtering dimension data]**.
1. Nella **[!UICONTROL Data to add]** finestra, aggiungere una colonna che calcola il valore massimo per il campo Data **** creazione nella tabella dei destinatari. È possibile utilizzare l&#39;editor di espressioni o immettere **max(@created)** direttamente in un campo della **[!UICONTROL Expression]** colonna. Then click the **[!UICONTROL Finish]** button.

   ![](assets/datamanagement_usecase_2.png)

1. Fai clic su **[!UICONTROL Edit additional data]**, quindi su **[!UICONTROL Advanced parameters...]**. Seleziona l’opzione **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]**.

   Questa opzione assicura che tutti i destinatari non vengano visualizzati come risultato e che i dati aggiunti in modo esplicito non vengano conservati. In questo caso, si riferisce all&#39;ultima data in cui è stato creato un destinatario.

   Lascia selezionata l’opzione **[!UICONTROL Remove duplicate rows (DISTINCT)]**.

## Passaggio 2: Collegamento dei destinatari e del risultato della funzione di aggregazione {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Per collegare la query relativa ai destinatari alla query che esegue il calcolo della funzione di aggregazione, è necessario utilizzare un&#39;attività di modifica dello schema.

1. Definire la query per i destinatari come set principale.
1. Nella **[!UICONTROL Links]** scheda, aggiungi un nuovo collegamento e immetti le informazioni nella finestra che si apre come segue:

   * Selezionare lo schema temporaneo relativo all&#39;aggregazione. I dati per questo schema verranno aggiunti ai membri del set principale.
   * Selezionate **[!UICONTROL Use a simple join]** per collegare il risultato aggregato a ogni destinatario del set principale.
   * Infine, specificate che il collegamento è un **[!UICONTROL Type 11 simple link]**.

   ![](assets/datamanagement_usecase_3.png)

Il risultato dell&#39;aggregazione è quindi collegato a ogni destinatario.

## Passaggio 3: Applicazione di filtri ai destinatari tramite l’aggregazione. {#step-3--filtering-recipients-using-the-aggregate-}

Una volta stabilito il collegamento, il risultato dell&#39;aggregazione e i destinatari fanno parte dello stesso schema temporaneo. È quindi possibile creare un filtro sullo schema per confrontare la data di creazione dei destinatari e l&#39;ultima data di creazione nota, rappresentata dalla funzione di aggregazione. Questo filtro viene eseguito utilizzando un&#39;attività divisa.

1. Nella **[!UICONTROL General]** scheda, selezionare **Destinatari** come dimensione di targeting e **Modifica schema** come dimensione di filtro (per filtrare l&#39;attività dello schema di transizione in entrata).
1. Nella **[!UICONTROL subsets]** scheda, selezionare **[!UICONTROL Add a filtering condition on the inbound population]** quindi fare clic su **[!UICONTROL Edit...]**.
1. Utilizzando l&#39;editor di espressioni, aggiungete un criterio di uguaglianza tra la data di creazione dei destinatari e la data di creazione calcolata dall&#39;aggregazione.

   I campi del tipo di data nel database vengono generalmente salvati in millisecondi. È pertanto necessario estendere tali valori per l&#39;intera giornata per evitare di recuperare i destinatari creati solo con lo stesso millisecondo.

   A tal fine, utilizzare la funzione **ToDate** , disponibile nell&#39;editor di espressioni, che converte date e ore in date semplici.

   Le espressioni da utilizzare per i criteri sono pertanto:

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`, dove expr##### fa riferimento all&#39;aggregazione specificata nella query della funzione di aggregazione.

   ![](assets/datamanagement_usecase_4.png)

Il risultato della divisione dell&#39;attività è quindi relativo ai destinatari creati lo stesso giorno dell&#39;ultima data di creazione nota.

Potete quindi aggiungere altre attività, ad esempio un aggiornamento dell&#39;elenco o una distribuzione per arricchire il flusso di lavoro.
