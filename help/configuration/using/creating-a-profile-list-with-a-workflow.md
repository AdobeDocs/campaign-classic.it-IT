---
product: campaign
title: Creazione di un elenco di profili con un flusso di lavoro
description: Scopri come creare un elenco di profili in un flusso di lavoro
feature: Workflows
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---

# Creazione di un elenco di profili con un flusso di lavoro{#creating-a-profile-list-with-a-workflow}

![](../../assets/common.svg)

Per creare una **[!UICONTROL List]** digita elenco in base alla nuova tabella dei destinatari, devi creare un flusso di lavoro di targeting che genererà l’elenco.

Per ulteriori informazioni sugli elenchi in Campaign, consulta [questa sezione](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Per creare un flusso di lavoro di targeting e aggiornare i destinatari in una tabella dei destinatari personalizzata, segui i passaggi seguenti:

1. Vai a **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nodo dell&#39;esploratore.
1. Crea un nuovo flusso di lavoro di targeting.
1. Posiziona un **Query** attività seguita da un **Aggiornamento elenco** attività.

   ![](assets/mapping_create_list_workflow01.png)

1. Fai doppio clic sul pulsante **Query** attività, quindi fai clic su **[!UICONTROL Edit the query]** per scegliere una dimensione di targeting basata sullo schema della nuova tabella dei destinatari (nel nostro esempio: **Individuale**). Fai clic su **[!UICONTROL Finish]** per confermare.

   ![](assets/mapping_create_list_workflow03.png)

1. Fai doppio clic sul pulsante **Aggiornamento elenco** , quindi seleziona la **[!UICONTROL Create the list if necessary (Computed name)]** pulsante di scelta.

   ![](assets/mapping_create_list_workflow02.png)

1. Selezionare la cartella di creazione del nuovo elenco.
1. Esegui il flusso di lavoro per creare l’elenco.
1. Visualizza il risultato nel nodo della struttura selezionata durante il **[!UICONTROL List update]** attività.

   Il dashboard specifica lo schema su cui si basa l&#39;elenco, come illustrato di seguito:

   ![](assets/mapping_list_view.png)
