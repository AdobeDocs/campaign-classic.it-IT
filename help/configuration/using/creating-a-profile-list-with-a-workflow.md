---
product: campaign
title: Creazione di un elenco di profili con un flusso di lavoro
description: Scopri come creare un elenco di profili in un flusso di lavoro
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 11%

---

# Creazione di un elenco di profili con un flusso di lavoro{#creating-a-profile-list-with-a-workflow}


Per creare un **[!UICONTROL List]** digita elenco in base alla nuova tabella dei destinatari; devi creare un flusso di lavoro di targeting che genererà l’elenco.

Per ulteriori informazioni sugli elenchi in Campaign, consulta [questa sezione](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Per creare un flusso di lavoro di targeting e aggiornare i destinatari in una tabella dei destinatari personalizzata, effettua le seguenti operazioni:

1. Vai a **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nodo dell&#39;explorer.
1. Crea un nuovo flusso di lavoro di targeting.
1. Inserisci un **Query** attività seguita da **Aggiornamento elenco** attività.

   ![](assets/mapping_create_list_workflow01.png)

1. Fai doppio clic su **Query** attività, quindi fai clic su **[!UICONTROL Edit the query]** per scegliere una dimensione di targeting basata sullo schema della nuova tabella dei destinatari (nel nostro esempio: **Individuale**). Fai clic su **[!UICONTROL Finish]** per confermare.

   ![](assets/mapping_create_list_workflow03.png)

1. Fai doppio clic su **Aggiornamento elenco** attività, quindi seleziona la **[!UICONTROL Create the list if necessary (Computed name)]** pulsante di opzione.

   ![](assets/mapping_create_list_workflow02.png)

1. Selezionare la cartella di creazione per il nuovo elenco.
1. Esegui il flusso di lavoro per creare l’elenco.
1. Visualizza il risultato nel nodo della struttura selezionata durante la **[!UICONTROL List update]** attività.

   Il dashboard specifica lo schema su cui si basa l’elenco, come illustrato di seguito:

   ![](assets/mapping_list_view.png)
