---
product: campaign
title: Creazione e gestione di elenchi
description: Scopri come creare e gestire gli elenchi
feature: Profili
role: User
level: Beginner
exl-id: 711b84cd-bac8-4f1a-9999-0124fbfc3a01
source-git-commit: 6c28e6cd78ce7a8ee5c0dc7e671de780787b9f57
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 9%

---

# Creare e gestire gli elenchi{#creating-and-managing-lists}

## Cos&#39;è una lista? {#about-lists-in-adobe-campaign}

Un elenco è un set statico di profili che possono essere oggetto di targeting nelle azioni di consegna o aggiornati durante le operazioni di importazione o l’esecuzione di un flusso di lavoro. Ad esempio, una popolazione estratta dal database tramite una query può fornire un elenco.

Gli elenchi vengono creati e gestiti tramite il collegamento **[!UICONTROL Lists]** nella scheda **[!UICONTROL Profiles and targets]** .

![](assets/s_ncs_user_interface_group_link.png)

In Adobe Campaign sono disponibili due tipi di elenchi:

* **[!UICONTROL Group]** tipo: Gli elenchi di  **[!UICONTROL Group]** tipi appartengono a un elenco  **** statico di persone selezionate in base a criteri specifici. L’elenco è simile a un’istantanea di un set di profili. Nota che non viene aggiornato automaticamente in caso di aggiunta di profili al database.

   Per ulteriori informazioni su come creare un elenco di tipi **[!UICONTROL Group]**, consulta questa [pagina](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** tipo: Gli elenchi di  **[!UICONTROL List]** tipi consentono di utilizzare i flussi di lavoro per creare e gestire gli elenchi. Si tratta di elenchi specifici risultanti dalle importazioni di dati, che possono essere aggiornati tramite l’attività dedicata del flusso di lavoro **[!UICONTROL List update]** .

   A differenza dell’elenco dei tipi **[!UICONTROL Group]**, questo elenco può essere aggiornato automaticamente con un’attività **[!UICONTROL Scheduler]**. Nota che per un esempio su come creare elenchi di tipi **[!UICONTROL List]**, fare riferimento a [questa pagina](../../workflow/using/list-update.md).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#create-list-video)

## Creare un elenco di profili da un gruppo {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** gli elenchi di tipi creati tramite il  **[!UICONTROL Profiles and targets]** collegamento devono essere basati sulla tabella di profilo Adobe Campaign predefinita (nms:recipient).

>[!NOTE]
>
>Per creare elenchi contenenti altri tipi di dati, è necessario eseguire un flusso di lavoro. Ad esempio, utilizzando una query sulla tabella dei visitatori e aggiornando l’elenco, puoi creare un elenco di visitatori. Per ulteriori informazioni sui flussi di lavoro, consulta [questa sezione](../../workflow/using/about-workflows.md).

Per creare un nuovo elenco di tipi **[!UICONTROL Group]**, effettua le seguenti operazioni:

1. Fai clic sul pulsante **[!UICONTROL Create]** e seleziona **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Immetti le informazioni nella scheda **[!UICONTROL Edit]** della finestra di creazione dell’elenco.

   * Immetti il nome dell’elenco nel campo **[!UICONTROL Label]** e, se necessario, modifica il nome interno.
   * Aggiungi una descrizione per questo elenco.
   * Puoi specificare una data di scadenza: una volta raggiunta tale data, l’elenco viene eliminato e eliminato automaticamente.

      ![](assets/list_expiration_date.png)

1. Nella scheda **[!UICONTROL Content]** , fai clic su **[!UICONTROL Add]** per selezionare i profili appartenenti all’elenco.

   ![](assets/s_ncs_user_add_group.png)

1. Fai clic su **[!UICONTROL Save]** per salvare l’elenco. Viene quindi aggiunto alla panoramica degli elenchi.

Puoi creare nuovi profili direttamente dalla finestra &quot;aggiungi profili&quot; facendo clic su **[!UICONTROL Create]**. Il profilo verrà aggiunto al database.

![](assets/s_ncs_user_new_recipient_from_group.png)

L’elenco dei profili può essere configurato come altri elenchi. Vedi [questa sezione](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Collegamento di dati a un elenco {#linking-data-to-a-list}

>[!NOTE]
>
>Il collegamento dei dati a un elenco può essere eseguito solo con un elenco di tipi **[!UICONTROL Group]**.

I profili di un set di profili possono essere filtrati e collegati a un elenco. Le azioni di consegna possono quindi essere inviate a questo elenco, per eseguire il targeting dei profili. Per raggruppare i profili:

1. Seleziona i profili e fai clic con il pulsante destro del mouse.
1. Seleziona **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Seleziona l’elenco desiderato o crea un nuovo elenco utilizzando il pulsante **[!UICONTROL Create]** , quindi fai clic su **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Fai clic sul pulsante **[!UICONTROL Start]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

L’opzione **[!UICONTROL Recreate the list]** elimina il contenuto precedente dall’elenco. Questa modalità è ottimizzata in quanto non è necessaria alcuna query per verificare se i profili sono già collegati all’elenco.

Deselezionando l’opzione **[!UICONTROL No trace of this job is saved in the database]**, puoi selezionare (o creare) la cartella di esecuzione in cui verranno memorizzate le informazioni collegate al processo.

La sezione superiore della finestra consente di monitorare l’esecuzione. Il pulsante **[!UICONTROL Stop]** ti consente di interrompere il processo. I contatti già elaborati verranno collegati all&#39;elenco.

Puoi monitorare il processo tramite la scheda **[!UICONTROL Lists]** sui profili interessati da questa operazione:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Puoi anche modificare l’elenco tramite la home page di Adobe Campaign: fare clic sul menu **[!UICONTROL Profiles and Targets > Lists]** e selezionare l&#39;elenco interessato. La scheda **[!UICONTROL Content]** mostra i profili collegati a questo elenco.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Rimuovere un profilo da un elenco {#removing-a-profile-from-a-list}

Per rimuovere un profilo da un elenco, puoi:

* Modifica l’elenco, seleziona il profilo nella scheda **[!UICONTROL Content]** , quindi fai clic sull’icona **[!UICONTROL Delete]** .

   ![](assets/list_remove_a_recipient.png)

* Modifica il profilo, fai clic sulla scheda **[!UICONTROL List]** , quindi fai clic sull’icona **[!UICONTROL Delete]** .

   ![](assets/recipient_remove_a_list.png)

## Eliminare un elenco di profili {#deleting-a-list-of-profiles}

È possibile eliminare uno o più elenchi dall’elenco dei gruppi nella struttura di Adobe Campaign. A questo scopo, modifica la struttura tramite il collegamento **[!UICONTROL Advanced > Explorer]** nella home page di Adobe Campaign. Selezionare il gruppo o i gruppi interessati e fare clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Delete]**. Un messaggio di avviso richiede di confermare l’eliminazione.

>[!NOTE]
>
>Quando elimini un elenco, i profili presenti nell’elenco non vengono interessati ma i dati nel relativo profilo vengono aggiornati.

## Video tutorial {#create-list-video}

### Creare un elenco di destinatari

Un elenco è un set statico di destinatari che possono essere targetizzati nelle azioni di consegna o aggiornati durante le operazioni di importazione o l’esecuzione di un flusso di lavoro. Un elenco di destinatari è anche detto audience.

Scopri come creare un pubblico configurando un elenco di destinatari da Esplora risorse.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### Utilizzare un flusso di lavoro per creare un elenco di destinatari {#create-list-in-a-wf-video}

Scopri come creare un flusso di lavoro per eseguire il targeting dei destinatari e come renderlo ricorrente prima di utilizzare l’elenco in una destinazione e-mail.

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
