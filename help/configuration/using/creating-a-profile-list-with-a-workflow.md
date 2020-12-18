---
solution: Campaign Classic
product: campaign
title: Creazione di un elenco di profili con un flusso di lavoro
description: Scopri come creare un elenco di profili in un flusso di lavoro
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---


# Creazione di un elenco di profili con un flusso di lavoro{#creating-a-profile-list-with-a-workflow}

Per creare un elenco di tipi **[!UICONTROL List]** basato sulla nuova tabella destinatari, è necessario creare un flusso di lavoro di targeting che genererà l&#39;elenco.

Per ulteriori informazioni sugli elenchi in Campaign, consultare [questa sezione](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Per creare un flusso di lavoro di targeting e aggiornare i destinatari in una tabella di destinatari personalizzata, effettua le operazioni seguenti:

1. Passate al nodo **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** dell&#39;esploratore.
1. Create un nuovo flusso di lavoro di targeting.
1. Inserire un&#39;attività **Query** seguita da un&#39;attività **Aggiornamento elenco**.

   ![](assets/mapping_create_list_workflow01.png)

1. Fare doppio clic sull&#39;attività **Query**, quindi fare clic su **[!UICONTROL Edit the query]** per scegliere una dimensione di targeting basata sullo schema della nuova tabella destinatari (nel nostro esempio: **Singolo**). Fare clic su **[!UICONTROL Finish]** per confermare.

   ![](assets/mapping_create_list_workflow03.png)

1. Fare doppio clic sull&#39;attività **Aggiornamento elenco**, quindi selezionare il pulsante di scelta **[!UICONTROL Create the list if necessary (Computed name)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Selezionate la cartella di creazione per il nuovo elenco.
1. Eseguire il flusso di lavoro per creare l&#39;elenco.
1. Visualizzare il risultato nel nodo della struttura ad albero selezionato durante l&#39;attività **[!UICONTROL List update]**.

   Il dashboard specifica lo schema su cui si basa l&#39;elenco, come illustrato di seguito:

   ![](assets/mapping_list_view.png)


