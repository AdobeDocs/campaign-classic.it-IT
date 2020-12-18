---
solution: Campaign Classic
product: campaign
title: Passaggi per creare una query
description: Passaggi per creare una query
audience: platform
content-type: reference
topic-tags: creating-queries
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---


# Passaggi per creare una query{#steps-to-create-a-query}

Per creare una query in  Adobe Campaign, procedere come segue:

1. Selezionare la tabella di lavoro. Fare riferimento a [Passaggio 1 - Scegliere una tabella](#step-1---choose-a-table).
1. Selezionare i dati da estrarre. Fare riferimento a [Passaggio 2 - Scegliere i dati da estrarre](#step-2---choose-data-to-extract).
1. Definire la sequenza di ordinamento dei dati. Fare riferimento a [Passaggio 3 - Ordinare i dati](#step-3---sort-data).
1. Filtrare i dati. Fare riferimento a [Passaggio 4 - Filtra dati](#step-4---filter-data).
1. Formattare i dati. Fare riferimento a [Passaggio 5 - Formato dati](#step-5---format-data).
1. Visualizza il risultato. Fare riferimento a [Passaggio 6 - Anteprima dati](#step-6---preview-data).

>[!NOTE]
>
>Tutti questi passaggi sono disponibili nell’editor query generico. Quando una query viene creata in un altro contesto, alcuni passaggi possono essere omessi.\
>L&#39;attività Query è presentata in [questa sezione](../../workflow/using/query.md).

## Passaggio 1 - Scegliere una tabella {#step-1---choose-a-table}

Selezionare la tabella contenente i dati da eseguire nella finestra **[!UICONTROL Document type]**. Se necessario, filtrare i dati utilizzando il campo del filtro o il pulsante **[!UICONTROL Filters]**.

![](assets/query_editor_nveau_21.png)

## Passaggio 2 - Scegliere i dati da estrarre {#step-2---choose-data-to-extract}

Nella finestra **[!UICONTROL Data to extract]**, selezionare i dati da visualizzare: questi campi costituiranno le colonne di output.

Ad esempio, selezionare **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** e **[!UICONTROL City]**. I risultati saranno organizzati in base a questa selezione. Utilizzate le frecce blu a destra della finestra per modificare l&#39;ordine delle colonne.

![](assets/query_editor_nveau_01.png)

È possibile modificare un&#39;espressione inserendo al suo interno una formula o eseguendo un processo su una funzione di aggregazione. A tal fine, fare clic sul campo della colonna **[!UICONTROL Expression]**, quindi selezionare **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

È possibile raggruppare i dati delle colonne di output: a tal fine, selezionare **[!UICONTROL Yes]** nella colonna **[!UICONTROL Group]** della finestra **[!UICONTROL Data to extract]**. Questa funzione genera un risultato intorno all&#39;asse di raggruppamento selezionato. Un esempio di query con raggruppamento è disponibile in [questa sezione](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* La funzione **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** consente di &quot;raggruppare per&quot; e selezionare il gruppo raggruppato (&quot;avere&quot;). Questa funzione si applica a tutti i campi della colonna di output. Ad esempio, questa opzione consente di raggruppare tutte le scelte di una colonna di output e recuperare un tipo specifico di informazioni, ad esempio i destinatari compresi tra 35 e 50.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/querying-using-grouping-management.md).

* La funzione **[!UICONTROL Remove duplicate rows (DISTINCT)]** consente di deduplicare risultati identici ottenuti nella colonna di output. Ad esempio, se effettui un censimento selezionando i campi Cognome, Nome e E-mail nella colonna di output, quelli con dati identici verranno eliminati, poiché significa che lo stesso contatto è stato immesso più volte nel database: verrà preso in considerazione solo un risultato.

## Passaggio 3 - Ordinare i dati {#step-3---sort-data}

La finestra **[!UICONTROL Sorting]** consente di ordinare il contenuto delle colonne. Utilizzate le frecce per modificare l&#39;ordine delle colonne:

* La colonna **[!UICONTROL Sorting]** consente un ordinamento semplice e dispone il contenuto delle colonne da A a Z o in ordine crescente.
* Il **[!UICONTROL Descending sort]** dispone il contenuto da Z a A in ordine decrescente. Questo è utile per visualizzare le vendite record, ad esempio: le cifre più alte sono riportate in cima all’elenco.

In questo esempio, i dati vengono ordinati in ordine crescente in base all&#39;età del destinatario.

![](assets/query_editor_nveau_57.png)

## Passaggio 4 - Filtrare i dati {#step-4---filter-data}

L&#39;editor di query consente di filtrare i dati per perfezionare la ricerca.

I filtri offerti dipendono dalla tabella interessata dalla query.

![](assets/query_editor_nveau_09.png)

Dopo aver selezionato **[!UICONTROL Filtering conditions]** si accede alla sezione **[!UICONTROL Target elements]**: in questo modo puoi definire come filtrare i dati da raccogliere.

* Per creare un nuovo filtro, selezionare i campi, gli operatori e i valori richiesti per creare la formula da verificare per consentire la selezione dei dati. È possibile combinare diverse condizioni (per ulteriori informazioni, vedere [Definizione delle condizioni del filtro](../../platform/using/defining-filter-conditions.md)).
* Per utilizzare i filtri salvati in precedenza, aprire l&#39;elenco a discesa facendo clic sul pulsante **[!UICONTROL Add]**, fare clic su **[!UICONTROL Predefined filter]** e selezionare quello desiderato.

   ![](assets/query_editor_15.png)

* I filtri creati in **[!UICONTROL Generic query editor]** sono disponibili in altre applicazioni di query e viceversa. Per salvare un filtro, fate clic sull&#39;icona **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e l&#39;uso dei filtri, vedere [Opzioni di filtro](../../platform/using/filtering-options.md).

Come illustrato nell’esempio seguente, per recuperare tutti i destinatari che parlano inglese, selezionate: &quot;lingua del destinatario **uguale a** EN&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>È possibile accedere direttamente a un&#39;opzione digitando la seguente formula nel campo **Value**: **$(opzioni:OPTION_NAME)**.

Fare clic sulla scheda **[!UICONTROL Preview]** per visualizzare il risultato della condizione di filtro. In questo caso, tutti i destinatari che parlano inglese vengono visualizzati con il proprio nome, nome e indirizzo e-mail.

![](assets/query_editor_nveau_98.png)

Gli utenti che hanno familiarità con SQL Language possono fare clic su **[!UICONTROL Generate SQL query]** per visualizzare la query in SQL.

![](assets/query_editor_nveau_99.png)

## Passaggio 5 - Formato dei dati {#step-5---format-data}

Una volta configurati i filtri di restrizione, potrete accedere alla finestra **[!UICONTROL Data formatting]**. Questa finestra consente di ridisporre le colonne di output, trasformare i dati e modificare le lettere maiuscole e minuscole delle etichette delle colonne. Consente inoltre di applicare una formula al risultato finale utilizzando un campo calcolato.

>[!NOTE]
>
>Per ulteriori informazioni sui tipi di campi calcolati, vedere [Creazione di campi calcolati](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Le colonne non selezionate non vengono visualizzate nella finestra di anteprima dei dati.

![](assets/query_editor_nveau_10.png)

La colonna **[!UICONTROL Transformation]** consente di modificare l&#39;etichetta di una colonna in lettere maiuscole o minuscole. Selezionare la colonna e fare clic sulla colonna **[!UICONTROL Transformation]**. Potete scegliere:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Passaggio 6 - Anteprima dei dati {#step-6---preview-data}

La finestra **[!UICONTROL Data preview]** è l&#39;ultimo passaggio. Fare clic su **[!UICONTROL Start the preview of the data]** per ottenere il risultato della query. È disponibile in colonne o in formato XML. Fare clic sulla scheda **[!UICONTROL Generated SQL queries]** per visualizzare la query in formato SQL.

In questo esempio, i dati vengono ordinati in ordine crescente in base all&#39;età del destinatario.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Per impostazione predefinita, nella finestra **[!UICONTROL Data preview]** sono visualizzate solo le prime 200 righe. Per modificare questa impostazione, immettere un numero nella casella **[!UICONTROL Lines to display]** e fare clic su **[!UICONTROL Start the preview of the data]**.

