---
product: campaign
title: Passaggi per creare una query
description: Passaggi per creare una query
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# Passaggi per creare una query{#steps-to-create-a-query}

![](../../assets/common.svg)

I passaggi per creare una query in Adobe Campaign sono i seguenti:

1. Selezionare la tabella di lavoro. Fare riferimento a [Passaggio 1 - Scegliere una tabella](#step-1---choose-a-table).
1. Seleziona i dati da estrarre. Fare riferimento a [Passaggio 2 - Scegliere i dati da estrarre](#step-2---choose-data-to-extract).
1. Definire la sequenza di ordinamento dei dati. Fare riferimento a [Passaggio 3 - Ordinare i dati](#step-3---sort-data).
1. Filtrare i dati. Fare riferimento a [Passaggio 4 - Filtrare i dati](#step-4---filter-data).
1. Formatta i dati. Fare riferimento a [Passaggio 5 - Formattare i dati](#step-5---format-data).
1. Visualizza il risultato. Fare riferimento a [Passaggio 6 - Anteprima dati](#step-6---preview-data).

>[!NOTE]
>
>Tutti questi passaggi sono disponibili nell’editor di query generico. Quando una query viene creata in un altro contesto, alcuni passaggi possono essere omessi.\
>L’attività Query è presentata in [questa sezione](../../workflow/using/query.md).

## Passaggio 1: scegliere una tabella {#step-1---choose-a-table}

Selezionare la tabella contenente i dati da eseguire nella finestra **[!UICONTROL Document type]**. Se necessario, filtra i dati utilizzando il campo filtro o il pulsante **[!UICONTROL Filters]** .

![](assets/query_editor_nveau_21.png)

## Passaggio 2: scegliere i dati da estrarre {#step-2---choose-data-to-extract}

Nella finestra **[!UICONTROL Data to extract]**, seleziona i dati da visualizzare: questi campi costituiranno le colonne di output.

Ad esempio, selezionare **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** e **[!UICONTROL City]**. I risultati saranno organizzati in base a questa selezione. Utilizza le frecce blu a destra della finestra per modificare l’ordine delle colonne.

![](assets/query_editor_nveau_01.png)

È possibile modificare un&#39;espressione inserendo una formula o eseguendo un processo su una funzione di aggregazione. A questo scopo, fai clic sul campo della colonna **[!UICONTROL Expression]** , quindi seleziona **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

È possibile raggruppare i dati della colonna di output: a questo scopo, seleziona **[!UICONTROL Yes]** nella colonna **[!UICONTROL Group]** della finestra **[!UICONTROL Data to extract]**. Questa funzione genera un risultato intorno all&#39;asse di raggruppamento selezionato. Un esempio di query con raggruppamento è disponibile in [questa sezione](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* La funzione **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** ti consente di &quot;raggruppare per&quot; e selezionare il raggruppamento (&quot;avere&quot;). Questa funzione si applica a tutti i campi della colonna di output. Ad esempio, questa opzione ti consente di raggruppare tutte le scelte di una colonna di output e recuperare un tipo specifico di informazioni, ad esempio i destinatari compresi tra 35 e 50.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/querying-using-grouping-management.md).

* La funzione **[!UICONTROL Remove duplicate rows (DISTINCT)]** consente di deduplicare risultati identici ottenuti nella colonna di output. Ad esempio, se scegli un censimento selezionando i campi Cognome, Nome e E-mail nella colonna di output, quelli con dati identici verranno eliminati, poiché significa che lo stesso contatto è stato inserito più volte nel database: verrà preso in considerazione un solo risultato.

## Passaggio 3 - Ordinare i dati {#step-3---sort-data}

La finestra **[!UICONTROL Sorting]** ti consente di ordinare il contenuto delle colonne. Utilizza le frecce per modificare l’ordine delle colonne:

* La colonna **[!UICONTROL Sorting]** consente un ordinamento semplice e dispone il contenuto delle colonne da A a Z o in ordine crescente.
* Il **[!UICONTROL Descending sort]** organizza il contenuto da Z a A in ordine decrescente. Questo è utile per visualizzare le vendite record, ad esempio: le cifre più alte sono riportate in cima all’elenco.

In questo esempio, i dati vengono ordinati in ordine crescente in base all’età del destinatario.

![](assets/query_editor_nveau_57.png)

## Passaggio 4: filtrare i dati {#step-4---filter-data}

L’editor delle query ti consente di filtrare i dati per perfezionare la ricerca.

I filtri offerti dipendono dalla tabella di cui si occupa la query.

![](assets/query_editor_nveau_09.png)

Dopo aver selezionato **[!UICONTROL Filtering conditions]** accedi alla sezione **[!UICONTROL Target elements]** : questo ti consente di definire come filtrare i dati da raccogliere.

* Per creare un nuovo filtro, selezionare i campi, gli operatori e i valori necessari per la creazione della formula da verificare per la selezione dei dati. È possibile combinare diverse condizioni (per ulteriori informazioni, consulta [Definizione delle condizioni del filtro](../../platform/using/defining-filter-conditions.md)).
* Per utilizzare i filtri salvati in precedenza, apri l’elenco a discesa facendo clic sul pulsante **[!UICONTROL Add]** , fai clic su **[!UICONTROL Predefined filter]** e seleziona quello desiderato.

   ![](assets/query_editor_15.png)

* I filtri creati in **[!UICONTROL Generic query editor]** sono disponibili in altre applicazioni di query e viceversa. Per salvare un filtro, fai clic sull’icona **[!UICONTROL Save]** .

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e l’utilizzo dei filtri, consulta [Opzioni di filtro](../../platform/using/filtering-options.md).

Come mostrato nell’esempio seguente, per recuperare tutti i destinatari di lingua inglese, seleziona: &quot;lingua del destinatario **uguale a** IT&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>Puoi accedere direttamente a un&#39;opzione digitando la seguente formula nel campo **Valore** : **$(options:OPTION_NAME)**.

Fai clic sulla scheda **[!UICONTROL Preview]** per visualizzare il risultato della condizione di filtro. In questo caso, tutti i destinatari che parlano inglese vengono visualizzati con il loro nome, nome e indirizzo e-mail.

![](assets/query_editor_nveau_98.png)

Gli utenti che hanno familiarità con SQL Language possono fare clic su **[!UICONTROL Generate SQL query]** per visualizzare la query in SQL.

![](assets/query_editor_nveau_99.png)

## Passaggio 5: formattare i dati {#step-5---format-data}

Dopo aver configurato i filtri di restrizione, potrai accedere alla finestra **[!UICONTROL Data formatting]**. Questa finestra consente di ridisporre le colonne di output, trasformare i dati e modificare le lettere maiuscole e minuscole delle etichette delle colonne. Consente inoltre di applicare una formula al risultato finale utilizzando un campo calcolato.

>[!NOTE]
>
>Per ulteriori informazioni sui tipi di campi calcolati, consulta [Creazione di campi calcolati](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Le colonne non selezionate non vengono visualizzate nella finestra di anteprima dati.

![](assets/query_editor_nveau_10.png)

La colonna **[!UICONTROL Transformation]** consente di modificare l’etichetta di una colonna in lettere maiuscole o minuscole. Seleziona la colonna e fai clic su nella colonna **[!UICONTROL Transformation]** . Puoi scegliere:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Passaggio 6 - Anteprima dei dati {#step-6---preview-data}

La finestra **[!UICONTROL Data preview]** è l&#39;ultima fase. Fai clic su **[!UICONTROL Start the preview of the data]** per ottenere il risultato della query. È disponibile in colonne o in formato XML. Fare clic sulla scheda **[!UICONTROL Generated SQL queries]** per visualizzare la query in formato SQL.

In questo esempio, i dati vengono ordinati in ordine crescente in base all’età del destinatario.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Per impostazione predefinita, nella finestra **[!UICONTROL Data preview]** vengono visualizzate solo le prime 200 righe. Per modificare questa impostazione, immettere un numero nella casella **[!UICONTROL Lines to display]** e fare clic su **[!UICONTROL Start the preview of the data]**.
