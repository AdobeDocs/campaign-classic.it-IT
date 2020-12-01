---
solution: Campaign Classic
product: campaign
title: Creazione e gestione di elenchi
description: Scopri come creare e gestire gli elenchi
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 8%

---


# Creazione e gestione di elenchi{#creating-and-managing-lists}

## Informazioni sugli elenchi in  Adobe Campaign {#about-lists-in-adobe-campaign}

Un elenco è un set statico di profili che possono essere mirati nelle azioni di consegna o aggiornati durante le operazioni di importazione o durante l&#39;esecuzione del flusso di lavoro. Ad esempio, una popolazione estratta dal database tramite una query può fornire un elenco.

Gli elenchi vengono creati e gestiti tramite il **[!UICONTROL Lists]** collegamento presente nella **[!UICONTROL Profiles and targets]** scheda.

![](assets/s_ncs_user_interface_group_link.png)

In  Adobe Campaign sono disponibili due tipi di elenchi:

* **[!UICONTROL Group]** type: Gli elenchi di **[!UICONTROL Group]** tipi appartengono a un elenco **statico** di persone selezionate in base a criteri specifici. L’elenco è simile a un’istantanea di un set di profili. Nota che non viene aggiornato automaticamente in caso di aggiunta di profili al database.

   For more information on how to create a **[!UICONTROL Group]** type list, refer to this [page](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** type: Gli elenchi dei **[!UICONTROL List]** tipi consentono di utilizzare i flussi di lavoro per creare e gestire gli elenchi. Si tratta di elenchi specifici risultanti dalle importazioni di dati, che possono essere aggiornati tramite l&#39;attività dedicata al **[!UICONTROL List update]** flusso di lavoro.

   A differenza dell&#39;elenco dei **[!UICONTROL Group]** tipi, questo elenco di tipi può essere aggiornato automaticamente con un&#39; **[!UICONTROL Scheduler]** attività. Si noti che per un esempio su come creare elenchi di **[!UICONTROL List]** tipi, fare riferimento a [questa pagina](../../workflow/using/list-update.md).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#create-list-video)

## Creazione di un elenco di profili da un gruppo {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** gli elenchi di tipi creati tramite il **[!UICONTROL Profiles and targets]** collegamento devono essere basati sulla tabella di profilo Adobe Campaign  predefinita (nms:destinatario).

>[!NOTE]
>
>Per creare elenchi contenenti altri tipi di dati, è necessario eseguire un flusso di lavoro. Ad esempio, utilizzando una query sulla tabella dei visitatori e aggiornando l&#39;elenco, potete creare un elenco di visitatori. For more information on workflows, refer to [this section](../../workflow/using/about-workflows.md).

Per creare un nuovo elenco di **[!UICONTROL Group]** tipi, procedere come segue:

1. Click the **[!UICONTROL Create]** button and select **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Immettete le informazioni nella **[!UICONTROL Edit]** scheda della finestra di creazione dell’elenco.

   * Immettete il nome dell’elenco nel **[!UICONTROL Label]** campo e, se necessario, modificate il nome interno.
   * Aggiungi una descrizione per l&#39;elenco.
   * Puoi specificare una data di scadenza: una volta raggiunta tale data, l&#39;elenco viene eliminato e eliminato automaticamente.

      ![](assets/list_expiration_date.png)

1. Nella **[!UICONTROL Content]** scheda, fare clic **[!UICONTROL Add]** per selezionare i profili che appartengono all&#39;elenco.

   ![](assets/s_ncs_user_add_group.png)

1. Click **[!UICONTROL Save]** to save the list. Viene quindi aggiunta alla panoramica degli elenchi.

Potete creare nuovi profili direttamente dalla finestra &#39;aggiungi profili&#39; facendo clic su **[!UICONTROL Create]**. Il profilo verrà aggiunto al database.

![](assets/s_ncs_user_new_recipient_from_group.png)

L&#39;elenco dei profili può essere configurato come altri elenchi. Consultate [Configurazione degli elenchi](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Collegamento di dati a un elenco {#linking-data-to-a-list}

>[!NOTE]
>
>Il collegamento dei dati a un elenco può essere eseguito solo con un elenco di **[!UICONTROL Group]** tipi.

I profili di un set di profili possono essere filtrati e collegati a un elenco. Le azioni di consegna possono quindi essere inviate a questo elenco, ai profili di destinazione. Per raggruppare i profili:

1. Selezionate i profili e fate clic con il pulsante destro del mouse.
1. Seleziona **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Selezionate l’elenco desiderato o create un nuovo elenco utilizzando il **[!UICONTROL Create]** pulsante, quindi fate clic su **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Fai clic sul pulsante **[!UICONTROL Start]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

L&#39; **[!UICONTROL Recreate the list]** opzione elimina il contenuto precedente dall&#39;elenco. Questa modalità è ottimizzata perché non è necessaria alcuna query per verificare se i profili sono già collegati all&#39;elenco.

Se deselezionate l’ **[!UICONTROL No trace of this job is saved in the database]** opzione, potete selezionare (o creare) la cartella di esecuzione in cui verranno memorizzate le informazioni collegate al processo.

La sezione superiore della finestra consente di monitorare l&#39;esecuzione. Il **[!UICONTROL Stop]** pulsante consente di interrompere il processo. I contatti già elaborati verranno collegati all&#39;elenco.

È possibile monitorare il processo tramite la **[!UICONTROL Lists]** scheda sui profili interessati dall&#39;operazione:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Potete anche modificare l’elenco tramite la home page di  Adobe Campaign: fare clic sul **[!UICONTROL Profiles and Targets > Lists]** menu e selezionare l&#39;elenco interessato. La **[!UICONTROL Content]** scheda mostra i profili collegati a questo elenco.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Rimozione di un profilo da un elenco {#removing-a-profile-from-a-list}

Per rimuovere un profilo da un elenco, potete:

* Modificate l&#39;elenco, selezionate il profilo nella **[!UICONTROL Content]** scheda, quindi fate clic sull&#39; **[!UICONTROL Delete]** icona.

   ![](assets/list_remove_a_recipient.png)

* Modificate il profilo, fate clic sulla **[!UICONTROL List]** scheda, quindi fate clic sull&#39; **[!UICONTROL Delete]** icona.

   ![](assets/recipient_remove_a_list.png)

## Eliminazione di un elenco di profili {#deleting-a-list-of-profiles}

È possibile eliminare uno o più elenchi dall&#39;elenco dei gruppi nella struttura  Adobe Campaign. A questo scopo, modificate la struttura ad albero tramite il **[!UICONTROL Advanced > Explorer]** collegamento presente nella home page di  Adobe Campaign. Selezionare i gruppi interessati e fare clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Delete]**. Un messaggio di avviso richiede di confermare l’eliminazione.

>[!NOTE]
>
>Quando eliminate un elenco, i profili presenti nell’elenco non vengono modificati, ma i dati nel relativo profilo vengono aggiornati.

## Video di esercitazione {#create-list-video}

### Come creare un elenco di destinatari

Un elenco è un set statico di destinatari che possono essere targetizzati nelle azioni di consegna o aggiornati durante le operazioni di importazione o l’esecuzione di un flusso di lavoro. Un elenco di destinatari è anche detto audience.

Scopri come creare un pubblico configurando un elenco di destinatari da Esplora risorse.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### How to create a list of recipients with a workflow {#create-list-in-a-wf-video}

Scoprite come creare un flusso di lavoro per indirizzare i destinatari e come renderlo ricorrente prima di utilizzare l&#39;elenco in una destinazione e-mail.

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

Ulteriori video Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).