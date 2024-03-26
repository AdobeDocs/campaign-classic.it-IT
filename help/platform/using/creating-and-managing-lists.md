---
product: campaign
title: Creazione e gestione di elenchi
description: Scopri come creare e gestire gli elenchi
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Profiles
role: User
level: Beginner
exl-id: 711b84cd-bac8-4f1a-9999-0124fbfc3a01
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 9%

---

# Creare e gestire gli elenchi{#creating-and-managing-lists}



## Che cos&#39;è un elenco? {#about-lists-in-adobe-campaign}

Un elenco è un set statico di profili che possono essere targetizzati nelle azioni di consegna o aggiornati durante le operazioni di importazione o l’esecuzione di un flusso di lavoro. Ad esempio, una popolazione estratta dal database tramite una query può fornire un elenco.

Gli elenchi vengono creati e gestiti tramite **[!UICONTROL Lists]** collegamento in **[!UICONTROL Profiles and targets]** scheda.

![](assets/s_ncs_user_interface_group_link.png)

In Adobe Campaign sono disponibili due tipi di elenchi:

* **[!UICONTROL Group]** type (tipo): The **[!UICONTROL Group]** gli elenchi di tipi appartengono a un **statico** elenco di persone selezionate secondo criteri specifici. L’elenco è simile a un’istantanea di un set di profili. Tieni presente che non viene aggiornato automaticamente nel caso in cui i profili vengano aggiunti al database.

  Per ulteriori informazioni su come creare una **[!UICONTROL Group]** digita elenco, fai riferimento a questo [pagina](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** type (tipo): The **[!UICONTROL List]** gli elenchi di tipo consentono di utilizzare i flussi di lavoro per creare e gestire gli elenchi. Si tratta di elenchi specifici risultanti dalle importazioni di dati, che possono essere aggiornati tramite l’ **[!UICONTROL List update]** attività del flusso di lavoro.

  A differenza della **[!UICONTROL Group]** elenco dei tipi, questo elenco dei tipi può essere aggiornato automaticamente con **[!UICONTROL Scheduler]** attività. Tieni presente che per un esempio su come creare **[!UICONTROL List]** elenchi di tipi, fare riferimento a [questa pagina](../../workflow/using/list-update.md).

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#create-list-video)

## Creare un elenco di profili da un gruppo {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** digita gli elenchi creati tramite **[!UICONTROL Profiles and targets]** il collegamento deve essere basato sulla tabella predefinita del profilo di Adobe Campaign (nms:recipient).

>[!NOTE]
>
>Per creare elenchi contenenti altri tipi di dati, è necessario eseguire un flusso di lavoro. Ad esempio, utilizzando una query nella tabella dei visitatori e aggiornando l’elenco, puoi creare un elenco di visitatori. Per ulteriori informazioni sui flussi di lavoro, consulta [questa sezione](../../workflow/using/about-workflows.md).

Per creare un nuovo **[!UICONTROL Group]** tipo, applica i seguenti passaggi:

1. Fai clic su **[!UICONTROL Create]** e seleziona **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Immettere le informazioni in **[!UICONTROL Edit]** della finestra di creazione dell’elenco.

   * Inserisci il nome dell’elenco in **[!UICONTROL Label]** e, se necessario, modificare il nome interno.
   * Aggiungere una descrizione per l&#39;elenco.
   * Puoi specificare una data di scadenza: una volta raggiunta tale data, l’elenco viene eliminato e rimosso automaticamente.

     ![](assets/list_expiration_date.png)

1. In **[!UICONTROL Content]** , fare clic su **[!UICONTROL Add]** per selezionare i profili appartenenti all’elenco.

   ![](assets/s_ncs_user_add_group.png)

1. Clic **[!UICONTROL Save]** per salvare l&#39;elenco. Viene quindi aggiunto alla panoramica degli elenchi.

Puoi creare nuovi profili direttamente dalla finestra &quot;Aggiungi profili&quot; facendo clic su **[!UICONTROL Create]**. Il profilo verrà aggiunto al database.

![](assets/s_ncs_user_new_recipient_from_group.png)

L’elenco dei profili può essere configurato come gli altri elenchi. Consulta [questa sezione](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Collegare dati a un elenco {#linking-data-to-a-list}

>[!NOTE]
>
>Il collegamento di dati a un elenco può essere eseguito solo con un **[!UICONTROL Group]** elenco dei tipi.

I profili di un set di profili possono essere filtrati e collegati a un elenco. Le azioni di consegna possono quindi essere inviate a questo elenco, per eseguire il targeting dei profili. Per raggruppare i profili:

1. Seleziona i profili e fai clic con il pulsante destro del mouse.
1. Seleziona **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Seleziona l’elenco desiderato o creane uno nuovo utilizzando **[!UICONTROL Create]** , quindi fare clic su **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Fai clic sul pulsante **[!UICONTROL Start]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

Il **[!UICONTROL Recreate the list]** elimina il contenuto precedente dall’elenco. Questa modalità è ottimizzata perché non è necessaria alcuna query per verificare se i profili sono già collegati all’elenco.

Se deselezioni la **[!UICONTROL No trace of this job is saved in the database]** , è possibile selezionare (o creare) la cartella di esecuzione in cui verranno memorizzate le informazioni collegate al processo.

La sezione superiore della finestra consente di monitorare l’esecuzione. Il **[!UICONTROL Stop]** consente di interrompere il processo. I contatti già elaborati verranno collegati all&#39;elenco.

È possibile monitorare il processo tramite **[!UICONTROL Lists]** scheda sui profili interessati da questa operazione:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Puoi modificare l’elenco anche tramite la home page di Adobe Campaign: fai clic sul pulsante **[!UICONTROL Profiles and Targets > Lists]** e selezionare l&#39;elenco corrispondente. Il **[!UICONTROL Content]** mostra i profili collegati a questo elenco.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Rimuovere un profilo da un elenco {#removing-a-profile-from-a-list}

Per rimuovere un profilo da un elenco, puoi:

* Modifica l’elenco, seleziona il profilo in **[!UICONTROL Content]** , quindi fare clic sulla scheda **[!UICONTROL Delete]** icona.

  ![](assets/list_remove_a_recipient.png)

* Modifica il profilo, fai clic su **[!UICONTROL List]** , quindi fare clic sulla scheda **[!UICONTROL Delete]** icona.

  ![](assets/recipient_remove_a_list.png)

## Eliminare un elenco di profili {#deleting-a-list-of-profiles}

È possibile eliminare uno o più elenchi dall&#39;elenco dei gruppi nella struttura Adobe Campaign. A questo scopo, modifica la struttura tramite **[!UICONTROL Advanced > Explorer]** nella home page di Adobe Campaign. Selezionare i gruppi interessati e fare clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Delete]**. Viene visualizzato un messaggio di avviso che richiede di confermare l&#39;eliminazione.

>[!NOTE]
>
>Quando elimini un elenco, i profili presenti nell’elenco non vengono interessati, ma i dati contenuti nel profilo vengono aggiornati.

## Video tutorial {#create-list-video}

### Come creare un elenco di destinatari

Un elenco è un set statico di destinatari che possono essere targetizzati nelle azioni di consegna o aggiornati durante le operazioni di importazione o l’esecuzione di un flusso di lavoro. Un elenco di destinatari è anche detto audience.

Scopri come creare un pubblico configurando un elenco di destinatari da Explorer.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### Come utilizzare un flusso di lavoro per creare un elenco di destinatari {#create-list-in-a-wf-video}

Scopri come creare un flusso di lavoro per eseguire il targeting dei destinatari e come renderlo ricorrente prima di utilizzare l’elenco in un target e-mail.

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

Sono disponibili altri video dimostrativi sui Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
