---
title: Passaggi per creare una query
seo-title: Passaggi per creare una query
description: Passaggi per creare una query
seo-description: null
page-status-flag: never-activated
uuid: 9668f49c-2da7-42c8-8728-8d644c787935
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: d538f489-f1ae-4682-9c21-d0300bd42b26
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 3%

---


# Passaggi per creare una query{#steps-to-create-a-query}

Per creare una query in  Adobe Campaign, procedere come segue:

1. Selezionare la tabella di lavoro. Fare riferimento al [Passaggio 1 - Scegliere una tabella](#step-1---choose-a-table).
1. Selezionare i dati da estrarre. Fare riferimento al [Passaggio 2 - Scegliere i dati da estrarre](#step-2---choose-data-to-extract).
1. Definire la sequenza di ordinamento dei dati. Fare riferimento al [passaggio 3 - Ordinare i dati](#step-3---sort-data).
1. Filtrare i dati. Fare riferimento al [passaggio 4 - Filtrare i dati](#step-4---filter-data).
1. Formattare i dati. Fare riferimento al [passaggio 5 - Formattare i dati](#step-5---format-data).
1. Visualizza il risultato. Fare riferimento al [passaggio 6 - Visualizzare l&#39;anteprima dei dati](#step-6---preview-data).

>[!NOTE]
>
>Tutti questi passaggi sono disponibili nell’editor query generico. Quando una query viene creata in un altro contesto, alcuni passaggi possono essere omessi.\
>L&#39;attività Query viene presentata in [questa sezione](../../workflow/using/query.md).

## Passaggio 1 - Scegliere una tabella {#step-1---choose-a-table}

Selezionare la tabella contenente i dati da eseguire nella **[!UICONTROL Document type]** finestra. Se necessario, filtrare i dati utilizzando il campo filtro o il **[!UICONTROL Filters]** pulsante.

![](assets/query_editor_nveau_21.png)

## Passaggio 2 - Scegliere i dati da estrarre {#step-2---choose-data-to-extract}

Nella **[!UICONTROL Data to extract]** finestra, selezionare i dati da visualizzare: questi campi costituiranno le colonne di output.

Ad esempio, selezionare **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** e **[!UICONTROL City]**. I risultati saranno organizzati in base a questa selezione. Utilizzate le frecce blu a destra della finestra per modificare l&#39;ordine delle colonne.

![](assets/query_editor_nveau_01.png)

È possibile modificare un&#39;espressione inserendo al suo interno una formula o eseguendo un processo su una funzione di aggregazione. A questo scopo, fare clic sul campo **[!UICONTROL Expression]** colonna, quindi selezionare **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

È possibile raggruppare i dati delle colonne di output: a questo scopo, selezionate **[!UICONTROL Yes]** la **[!UICONTROL Group]** colonna della **[!UICONTROL Data to extract]** finestra. Questa funzione genera un risultato intorno all&#39;asse di raggruppamento selezionato. Un esempio di query con raggruppamento è disponibile in [questa sezione](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* La **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** funzione consente di &quot;raggruppare per&quot; e selezionare i raggruppamenti (&quot;avere&quot;). Questa funzione si applica a tutti i campi della colonna di output. Ad esempio, questa opzione consente di raggruppare tutte le scelte di una colonna di output e recuperare un tipo specifico di informazioni, ad esempio i destinatari compresi tra 35 e 50.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/querying-using-grouping-management.md).

* La **[!UICONTROL Remove duplicate rows (DISTINCT)]** funzione consente di deduplicare risultati identici ottenuti nella colonna di output. Ad esempio, se effettui un censimento selezionando i campi Cognome, Nome e E-mail nella colonna di output, quelli con dati identici verranno eliminati, poiché significa che lo stesso contatto è stato immesso più volte nel database: verrà preso in considerazione solo un risultato.

## Passaggio 3 - Ordinare i dati {#step-3---sort-data}

La **[!UICONTROL Sorting]** finestra consente di ordinare il contenuto delle colonne. Utilizzate le frecce per modificare l&#39;ordine delle colonne:

* La **[!UICONTROL Sorting]** colonna consente un ordinamento semplice e dispone il contenuto della colonna da A a Z o in ordine crescente.
* Il contenuto **[!UICONTROL Descending sort]** viene disposto da Z a A e in ordine decrescente. Questo è utile per visualizzare le vendite record, ad esempio: le cifre più alte sono riportate in cima all’elenco.

In questo esempio, i dati vengono ordinati in ordine crescente in base all&#39;età del destinatario.

![](assets/query_editor_nveau_57.png)

## Passaggio 4 - Filtrare i dati {#step-4---filter-data}

L&#39;editor di query consente di filtrare i dati per perfezionare la ricerca.

I filtri offerti dipendono dalla tabella interessata dalla query.

![](assets/query_editor_nveau_09.png)

Una volta selezionato, **[!UICONTROL Filtering conditions]** si accede alla **[!UICONTROL Target elements]** sezione: in questo modo puoi definire come filtrare i dati da raccogliere.

* Per creare un nuovo filtro, selezionare i campi, gli operatori e i valori richiesti per creare la formula da verificare per consentire la selezione dei dati. È possibile combinare diverse condizioni (per ulteriori informazioni, vedere [Definizione delle condizioni](../../platform/using/defining-filter-conditions.md)del filtro).
* Per utilizzare i filtri salvati in precedenza, aprire l&#39;elenco a discesa facendo clic sul **[!UICONTROL Add]** pulsante, fare clic **[!UICONTROL Predefined filter]** e selezionare quello desiderato.

   ![](assets/query_editor_15.png)

* I filtri creati in **[!UICONTROL Generic query editor]** sono disponibili in altre applicazioni di query e viceversa. Per salvare un filtro, fate clic sull’ **[!UICONTROL Save]** icona .

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e l&#39;uso dei filtri, vedere [Opzioni](../../platform/using/filtering-options.md)di filtro.

Come illustrato nell’esempio seguente, per recuperare tutti i destinatari che parlano inglese, selezionate: &quot;lingua del destinatario **uguale** a EN&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>È possibile accedere direttamente a un&#39;opzione digitando la seguente formula nel campo **Valore** : **$(options:OPTION_NAME)**.

Fare clic sulla **[!UICONTROL Preview]** scheda per visualizzare il risultato della condizione di filtro. In questo caso, tutti i destinatari che parlano inglese vengono visualizzati con il proprio nome, nome e indirizzo e-mail.

![](assets/query_editor_nveau_98.png)

Gli utenti che hanno familiarità con SQL Language possono fare clic **[!UICONTROL Generate SQL query]** per visualizzare la query in SQL.

![](assets/query_editor_nveau_99.png)

## Passaggio 5 - Formattare i dati {#step-5---format-data}

Una volta configurati i filtri di restrizione, potrete accedere alla **[!UICONTROL Data formatting]** finestra. Questa finestra consente di ridisporre le colonne di output, trasformare i dati e modificare le lettere maiuscole e minuscole delle etichette delle colonne. Consente inoltre di applicare una formula al risultato finale utilizzando un campo calcolato.

>[!NOTE]
>
>Per ulteriori informazioni sui tipi di campi calcolati, vedere [Creazione di campi](../../platform/using/defining-filter-conditions.md#creating-calculated-fields)calcolati.

Le colonne non selezionate non vengono visualizzate nella finestra di anteprima dei dati.

![](assets/query_editor_nveau_10.png)

La **[!UICONTROL Transformation]** colonna consente di modificare l’etichetta di una colonna in lettere maiuscole o minuscole. Selezionate la colonna e fate clic su nella **[!UICONTROL Transformation]** colonna. Potete scegliere:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Passaggio 6 - Anteprima dei dati {#step-6---preview-data}

La **[!UICONTROL Data preview]** finestra è l&#39;ultimo passaggio. Fare clic **[!UICONTROL Start the preview of the data]** per ottenere il risultato della query. È disponibile in colonne o in formato XML. Fare clic sulla **[!UICONTROL Generated SQL queries]** scheda per visualizzare la query in formato SQL.

In questo esempio, i dati vengono ordinati in ordine crescente in base all&#39;età del destinatario.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Per impostazione predefinita, nella **[!UICONTROL Data preview]** finestra sono visualizzate solo le prime 200 righe. Per modificare questa impostazione, immettete un numero nella **[!UICONTROL Lines to display]** casella e fate clic su **[!UICONTROL Start the preview of the data]**.

