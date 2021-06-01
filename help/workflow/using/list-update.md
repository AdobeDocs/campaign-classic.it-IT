---
product: campaign
title: Aggiornare un elenco
description: Aggiornare un elenco
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 2%

---

# Aggiornare un elenco{#list-update}

Un&#39;attività **Aggiornamento elenco** memorizza la popolazione specificata nella transizione in un elenco di destinatari.

![](assets/s_user_segmentation_update_group.png)

L’elenco può essere selezionato dall’elenco dei gruppi esistenti.

Può essere creato anche utilizzando le opzioni **[!UICONTROL Create the list if necessary (Computed name)]** e **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** . Queste opzioni consentono di selezionare l’etichetta scelta per creare un elenco e successivamente la cartella in cui verrà salvato. L’etichetta può anche essere generata automaticamente inserendo campi dinamici o uno script. I diversi campi dinamici sono disponibili nel menu a comparsa a destra dell’etichetta.

![](assets/s_user_segmentation_update_list_calc.png)

Se l’elenco esiste già, i destinatari verranno aggiunti al contenuto esistente, a meno che tu non selezioni l’opzione **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** . In questo caso, il contenuto dell’elenco viene eliminato prima dell’aggiornamento.

Se desideri che l’elenco creato o aggiornato utilizzi una tabella diversa dalla tabella dei destinatari, seleziona l’opzione **[!UICONTROL Create or use a list with its own table]** .

Per utilizzare l’opzione , le tabelle specifiche in questione devono essere state configurate nell’istanza di Adobe Campaign.

In genere, il salvataggio di una destinazione in un elenco segna la fine di un flusso di lavoro. Per impostazione predefinita, l’attività **[!UICONTROL List update]** non dispone pertanto di una transizione in uscita. Seleziona l’opzione **[!UICONTROL Generate an outbound transition]** per aggiungerne una.

![](assets/do-not-localize/how-to-video.png) [Scopri come creare un elenco di destinatari da Esplora risorse nel video](#video)

## Esempio: Aggiornamento elenco {#example--list-update}

Nell&#39;esempio seguente, l&#39;attività di aggiornamento elenco segue una query che prende di mira gli uomini che hanno più di 30 anni di vita in Francia. L’elenco verrà creato inizialmente dai risultati della query. Viene quindi aggiornato ogni volta che viene avviato dal flusso di lavoro. Ad esempio, può essere utilizzato regolarmente per offerte promozionali mirate per le campagne.

1. Aggiungi un **[!UICONTROL list update activity]** direttamente dopo una query, quindi aprila per modificarla.

   Per ulteriori informazioni sulla creazione di una query in un flusso di lavoro, consulta [Query](../../workflow/using/query.md).

1. Puoi selezionare un’etichetta per l’attività.
1. Seleziona l’opzione **[!UICONTROL Create the list if necessary (Calculated name)]** per mostrare che l’elenco verrà creato dopo l’esecuzione del primo flusso di lavoro, quindi aggiornato con le esecuzioni seguenti.
1. Selezionare la cartella in cui salvare l’elenco.
1. Inserisci un’etichetta per l’elenco. È possibile inserire campi dinamici per generare automaticamente il nome dall’elenco. In questo esempio, l’elenco ha lo stesso nome della query per identificare facilmente il suo contenuto.
1. Lascia selezionata l’opzione **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** per eliminare i destinatari che non corrispondono ai criteri di targeting e per inserire quelli nuovi nell’elenco.
1. Lascia selezionata anche l’opzione **[!UICONTROL Create or use a list with its own table]** .
1. Lascia deselezionata l’opzione **[!UICONTROL Generate an outbound transition]** .
1. Fai clic su **[!UICONTROL Ok]**, quindi avvia il flusso di lavoro.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   L’elenco dei destinatari corrispondenti viene quindi creato o aggiornato.

## Parametri di input {#input-parameters}

* tableName
* schema

Identifica la popolazione da salvare nel gruppo.

## Parametri di output {#output-parameters}

* groupId: Identificatore del gruppo.

## Video tutorial {#video}

Questo video mostra come creare un elenco di destinatari da Esplora risorse.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
