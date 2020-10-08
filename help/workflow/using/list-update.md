---
title: Aggiornamento elenco
seo-title: Aggiornamento elenco
description: Aggiornamento elenco
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 1%

---


# Aggiornamento elenco{#list-update}

Un&#39;attività di aggiornamento **** elenco memorizza la popolazione specificata nella transizione in un elenco di destinatari.

![](assets/s_user_segmentation_update_group.png)

L’elenco può essere selezionato dall’elenco dei gruppi esistenti.

Può essere anche creato utilizzando le opzioni **[!UICONTROL Create the list if necessary (Computed name)]** e **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** . Queste opzioni consentono di selezionare l&#39;etichetta desiderata per creare un elenco e, successivamente, la cartella in cui verrà salvato. L&#39;etichetta può essere generata automaticamente anche inserendo campi dinamici o inserendo uno script. I diversi campi dinamici sono disponibili nel menu a comparsa a destra dell&#39;etichetta.

![](assets/s_user_segmentation_update_list_calc.png)

Se l’elenco esiste già, i destinatari verranno aggiunti al contenuto esistente, a meno che non si selezioni l’ **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** opzione. In questo caso, il contenuto dell&#39;elenco viene eliminato prima dell&#39;aggiornamento.

Se si desidera che l&#39;elenco creato o aggiornato utilizzi una tabella diversa da quella del destinatario, selezionare l&#39; **[!UICONTROL Create or use a list with its own table]** opzione.

Per utilizzare l&#39;opzione, le tabelle specifiche in questione devono essere state configurate nell&#39;istanza di Adobe Campaign .

In genere, il salvataggio di una destinazione in un elenco indica la fine di un flusso di lavoro. Per impostazione predefinita, l&#39; **[!UICONTROL List update]** attività non ha pertanto una transizione in uscita. Selezionare l&#39; **[!UICONTROL Generate an outbound transition]** opzione per aggiungerne una.

## Esempio: Aggiornamento elenco {#example--list-update}

Nell&#39;esempio seguente, l&#39;attività di aggiornamento dell&#39;elenco segue una query che riguarda gli uomini che vivono in Francia oltre 30 anni. L&#39;elenco verrà creato inizialmente dai risultati della query. Viene quindi aggiornato ogni volta che viene avviato dal flusso di lavoro. Ad esempio, può essere utilizzato regolarmente per offerte promozionali mirate per le campagne.

1. Aggiungete un oggetto **[!UICONTROL list update activity]** direttamente dopo una query, quindi apritelo per modificarlo.

   Per ulteriori informazioni sulla creazione di una query in un flusso di lavoro, vedere [Query](../../workflow/using/query.md).

1. Potete selezionare un&#39;etichetta per l&#39;attività.
1. Selezionate l’ **[!UICONTROL Create the list if necessary (Calculated name)]** opzione per mostrare che l’elenco verrà creato dopo l’esecuzione del primo flusso di lavoro, quindi aggiornato con le seguenti esecuzioni.
1. Selezionare la cartella in cui salvare l&#39;elenco.
1. Immettere un&#39;etichetta per l&#39;elenco. È possibile inserire campi dinamici per generare automaticamente il nome dall&#39;elenco. In questo esempio, l&#39;elenco ha lo stesso nome della query per identificare facilmente il suo contenuto.
1. Lasciate l&#39; **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** opzione selezionata per eliminare i destinatari che non corrispondono ai criteri di targeting e per inserire quelli nuovi nell&#39;elenco.
1. Also leave the **[!UICONTROL Create or use a list with its own table]** option checked.
1. Leave the **[!UICONTROL Generate an outbound transition]** option unchecked.
1. Click **[!UICONTROL Ok]** then start the workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   L&#39;elenco dei destinatari corrispondenti viene quindi creato o aggiornato.

Per ulteriori informazioni, consultate [Creazione di un elenco di video dei destinatari](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/profile-management/creating-a-list-of-recipients.html) .

## Parametri di input {#input-parameters}

* tableName
* schema

Identifica la popolazione da salvare nel gruppo.

## Parametri di output {#output-parameters}

* groupId: Identificatore gruppo.
