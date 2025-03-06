---
product: campaign
title: Aggiornare un elenco
description: Aggiornare un elenco
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 3%

---

# Aggiornare un elenco{#list-update}



Un&#39;attività **List update** memorizza la popolazione specificata nella transizione in un elenco di destinatari.

![](assets/s_user_segmentation_update_group.png)

L’elenco può essere selezionato dall’elenco dei gruppi esistenti.

Può essere creato anche utilizzando le opzioni **[!UICONTROL Create the list if necessary (Computed name)]** e **[!UICONTROL Create the list if necessary (Computed Folder and Name)]**. Queste opzioni consentono di selezionare l&#39;etichetta desiderata per creare un elenco e, successivamente, la cartella in cui verrà salvato. L’etichetta può anche essere generata automaticamente inserendo campi dinamici o uno script. I diversi campi dinamici sono disponibili nel menu a comparsa a destra dell’etichetta.

![](assets/s_user_segmentation_update_list_calc.png)

Se l&#39;elenco esiste già, i destinatari verranno aggiunti al contenuto esistente, a meno che non si selezioni l&#39;opzione **[!UICONTROL Purge the list if it exists (otherwise add to the list)]**. In questo caso, il contenuto dell’elenco viene eliminato prima dell’aggiornamento.

Se si desidera che l&#39;elenco creato o aggiornato utilizzi una tabella diversa da quella dei destinatari, selezionare l&#39;opzione **[!UICONTROL Create or use a list with its own table]**.

Per utilizzare l’opzione, le tabelle specifiche in questione devono essere state configurate nell’istanza di Adobe Campaign.

In genere, il salvataggio di una destinazione in un elenco indica la fine di un flusso di lavoro. Per impostazione predefinita, l&#39;attività **[!UICONTROL List update]** non ha quindi una transizione in uscita. Selezionare l&#39;opzione **[!UICONTROL Generate an outbound transition]** per aggiungerne una.

![](assets/do-not-localize/how-to-video.png) [Scopri come creare un elenco di destinatari da Esplora risorse nel video](#video)

## Esempio: aggiornamento elenco {#example--list-update}

Nell’esempio seguente, l’attività di aggiornamento dell’elenco segue una query che esegue il targeting degli uomini oltre i 30 anni che vivono in Francia. L’elenco verrà creato inizialmente dai risultati della query. Verrà quindi aggiornato ogni volta che viene avviato dal flusso di lavoro. Ad esempio, può essere utilizzato regolarmente per offerte promozionali mirate a campagne.

1. Aggiungi **[!UICONTROL list update activity]** direttamente dopo una query, quindi aprila per modificarla.

   Per ulteriori informazioni sulla creazione di una query in un flusso di lavoro, consulta [Query](query.md).

1. Puoi selezionare un’etichetta per l’attività.
1. Selezionare l&#39;opzione **[!UICONTROL Create the list if necessary (Calculated name)]** per indicare che l&#39;elenco verrà creato una volta eseguito il primo flusso di lavoro, quindi aggiornato con le esecuzioni seguenti.
1. Selezionare la cartella in cui salvare l&#39;elenco.
1. Immettere un&#39;etichetta per l&#39;elenco. Puoi inserire campi dinamici per generare automaticamente il nome dall’elenco. In questo esempio, l’elenco ha lo stesso nome della query per identificarne facilmente il contenuto.
1. Lascia selezionata l&#39;opzione **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** per eliminare i destinatari che non corrispondono ai criteri di targeting e inserire i nuovi destinatari nell&#39;elenco.
1. Lascia selezionata anche l&#39;opzione **[!UICONTROL Create or use a list with its own table]**.
1. Lascia deselezionata l&#39;opzione **[!UICONTROL Generate an outbound transition]**.
1. Fai clic su **[!UICONTROL Ok]**, quindi avvia il flusso di lavoro.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   Viene quindi creato o aggiornato l’elenco dei destinatari corrispondenti.

## Parametri di input {#input-parameters}

* tableName
* schema

Identifica la popolazione da salvare nel gruppo.

## Parametri di output {#output-parameters}

* groupId: identificatore del gruppo.

## Video tutorial {#video}

Questo video mostra come creare un elenco di destinatari da Explorer.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

Ulteriori video dimostrativi di Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
