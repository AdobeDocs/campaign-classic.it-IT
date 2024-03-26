---
product: campaign
title: Aggiornare un elenco
description: Aggiornare un elenco
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 3%

---

# Aggiornare un elenco{#list-update}



A **Aggiornamento elenco** l’attività memorizza la popolazione specificata nella transizione in un elenco di destinatari.

![](assets/s_user_segmentation_update_group.png)

L’elenco può essere selezionato dall’elenco dei gruppi esistenti.

Può essere creato anche utilizzando **[!UICONTROL Create the list if necessary (Computed name)]** e **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** opzioni. Queste opzioni consentono di selezionare l&#39;etichetta desiderata per creare un elenco e, successivamente, la cartella in cui verrà salvato. L’etichetta può anche essere generata automaticamente inserendo campi dinamici o uno script. I diversi campi dinamici sono disponibili nel menu a comparsa a destra dell’etichetta.

![](assets/s_user_segmentation_update_list_calc.png)

Se l’elenco esiste già, i destinatari verranno aggiunti al contenuto esistente, a meno che tu non controlli **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** opzione. In questo caso, il contenuto dell’elenco viene eliminato prima dell’aggiornamento.

Se desideri che l’elenco creato o aggiornato utilizzi una tabella diversa da quella dei destinatari, seleziona la **[!UICONTROL Create or use a list with its own table]** opzione.

Per utilizzare l’opzione, le tabelle specifiche in questione devono essere state configurate nell’istanza di Adobe Campaign.

In genere, il salvataggio di una destinazione in un elenco indica la fine di un flusso di lavoro. Per impostazione predefinita, il **[!UICONTROL List update]** L’attività non dispone pertanto di una transizione in uscita. Controlla la **[!UICONTROL Generate an outbound transition]** per aggiungerne una.

![](assets/do-not-localize/how-to-video.png) [Scopri come creare un elenco di destinatari da Esplora risorse nel video](#video)

## Esempio: aggiornamento elenco {#example--list-update}

Nell’esempio seguente, l’attività di aggiornamento dell’elenco segue una query che esegue il targeting degli uomini oltre i 30 anni che vivono in Francia. L’elenco verrà creato inizialmente dai risultati della query. Verrà quindi aggiornato ogni volta che viene avviato dal flusso di lavoro. Ad esempio, può essere utilizzato regolarmente per offerte promozionali mirate a campagne.

1. Aggiungi un **[!UICONTROL list update activity]** direttamente dopo una query, quindi aprila per modificarla.

   Per ulteriori informazioni sulla creazione di una query in un flusso di lavoro, consulta [Query](query.md).

1. Puoi selezionare un’etichetta per l’attività.
1. Seleziona la **[!UICONTROL Create the list if necessary (Calculated name)]** per mostrare che l’elenco verrà creato una volta eseguito il primo flusso di lavoro, quindi aggiornato con le esecuzioni seguenti.
1. Selezionare la cartella in cui salvare l&#39;elenco.
1. Immettere un&#39;etichetta per l&#39;elenco. Puoi inserire campi dinamici per generare automaticamente il nome dall’elenco. In questo esempio, l’elenco ha lo stesso nome della query per identificarne facilmente il contenuto.
1. Lascia **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** opzione selezionata per eliminare i destinatari che non corrispondono ai criteri di targeting e inserire i nuovi destinatari nell’elenco.
1. Lascia anche **[!UICONTROL Create or use a list with its own table]** opzione selezionata.
1. Lascia **[!UICONTROL Generate an outbound transition]** deselezionata.
1. Clic **[!UICONTROL Ok]** quindi avvia il workflow.

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

Sono disponibili altri video dimostrativi sui Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
