---
product: campaign
title: Utilizzare gli aggregati
description: Scopri come utilizzare gli aggregati
feature: Workflows
exl-id: 12b173e9-5068-4d45-9e1e-2aecc9866e9c
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---

# Utilizzare gli aggregati{#using-aggregates}

![](../../assets/common.svg)

Questo caso d’uso descrive come identificare automaticamente gli ultimi destinatari aggiunti al database.

Utilizzando il processo seguente, la data di creazione dei destinatari nel database viene confrontata con l’ultima data nota in cui un destinatario è stato creato utilizzando un aggregato. Verranno selezionati anche tutti i destinatari creati lo stesso giorno.

Per eseguire un **Data creazione = max (data creazione)** digita il filtro per i destinatari, devi eseguire un flusso di lavoro per seguire questi passaggi:

1. Recupera i destinatari del database utilizzando una query di base. Per ulteriori informazioni su questo passaggio, consulta [Creazione di una query](query.md#creating-a-query).
1. Calcola l’ultima data nota in cui è stato creato un destinatario utilizzando il risultato generato dalla **max (data di creazione)** funzione di aggregazione.
1. Collega ogni destinatario alla funzione di aggregazione e genera lo stesso schema.
1. Filtrare i destinatari utilizzando l’aggregato tramite lo schema modificato.

![](assets/datamanagement_usecase_1.png)

## Passaggio 1: Calcolo del risultato aggregato {#step-1--calculating-the-aggregate-result}

1. Crea una query. In questo caso, l’obiettivo è quello di calcolare l’ultima data di creazione nota tra tutti i destinatari del database. La query non contiene pertanto un filtro.
1. Seleziona **[!UICONTROL Add data]**.
1. Nelle finestre aperte, seleziona **[!UICONTROL Data linked to the filtering dimension]** then **[!UICONTROL Filtering dimension data]**.
1. In **[!UICONTROL Data to add]** aggiungi una colonna che calcola il valore massimo per **Data creazione** nella tabella dei destinatari. Puoi utilizzare l’editor di espressioni o immettere **max(@created)** direttamente in un campo nel **[!UICONTROL Expression]** colonna. Quindi fai clic sul pulsante **[!UICONTROL Finish]** pulsante .

   ![](assets/datamanagement_usecase_2.png)

1. Fai clic su **[!UICONTROL Edit additional data]**, quindi su **[!UICONTROL Advanced parameters...]**. Seleziona l’opzione **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]**.

   Questa opzione assicura che tutti i destinatari non vengano visualizzati come risultato e che i dati aggiunti esplicitamente non vengano conservati. In questo caso, si riferisce all’ultima data di creazione di un destinatario.

   Lascia selezionata l’opzione **[!UICONTROL Remove duplicate rows (DISTINCT)]**.

## Passaggio 2: Collegamento dei destinatari e del risultato della funzione di aggregazione {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Per collegare la query relativa ai destinatari alla query che esegue il calcolo della funzione di aggregazione, è necessario utilizzare un’attività di modifica dello schema.

1. Definisci la query per i destinatari come set principale.
1. In **[!UICONTROL Links]** , aggiungi un nuovo collegamento e inserisci le informazioni nella finestra che si apre come segue:

   * Selezionare lo schema temporaneo relativo all&#39;aggregato. I dati per questo schema verranno aggiunti ai membri del set principale.
   * Seleziona **[!UICONTROL Use a simple join]** per collegare il risultato aggregato a ogni destinatario del set principale.
   * Infine, specifica che il collegamento è un **[!UICONTROL Type 11 simple link]**.

   ![](assets/datamanagement_usecase_3.png)

Il risultato dell’aggregazione è quindi collegato a ogni destinatario.

## Passaggio 3: Filtrare i destinatari utilizzando l’aggregato . {#step-3--filtering-recipients-using-the-aggregate-}

Una volta stabilito il collegamento, il risultato aggregato e i destinatari fanno parte dello stesso schema temporaneo. È quindi possibile creare un filtro sullo schema per confrontare la data di creazione dei destinatari e l’ultima data di creazione nota, rappresentata dalla funzione di aggregazione. Questo filtro viene eseguito utilizzando un’attività di suddivisione.

1. In **[!UICONTROL General]** scheda , seleziona **Destinatari** come dimensione di targeting e **Modifica schema** come dimensione di filtro (per filtrare l’attività schema di transizione in entrata).
1. In **[!UICONTROL subsets]** scheda , seleziona **[!UICONTROL Add a filtering condition on the inbound population]** quindi fai clic su **[!UICONTROL Edit...]**.
1. Utilizzando l’editor espressioni, aggiungi un criterio di uguaglianza tra la data di creazione dei destinatari e la data di creazione calcolata dall’aggregato.

   I campi del tipo di data nel database vengono generalmente salvati in millisecondi. È pertanto necessario estenderle per l’intero giorno per evitare di recuperare i destinatari creati solo con lo stesso millisecondi.

   Per eseguire questa operazione, utilizza la variabile **ToDate** , disponibile nell’editor di espressioni, che converte date e ore in date semplici.

   Le espressioni da utilizzare per i criteri sono pertanto:

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`, dove expr#### fa riferimento all’aggregato specificato nella query della funzione di aggregazione.

   ![](assets/datamanagement_usecase_4.png)

Il risultato dell’attività di suddivisione si riferisce quindi ai destinatari creati lo stesso giorno dell’ultima data di creazione nota.

Puoi quindi aggiungere altre attività, ad esempio un aggiornamento dell’elenco o una consegna per arricchire il flusso di lavoro.
