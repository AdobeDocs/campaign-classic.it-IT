---
title: Creazione di un elenco di profili con un flusso di lavoro
seo-title: Creazione di un elenco di profili con un flusso di lavoro
description: Creazione di un elenco di profili con un flusso di lavoro
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 19%

---


# Creazione di un elenco di profili con un flusso di lavoro{#creating-a-profile-list-with-a-workflow}

Per creare un elenco di **[!UICONTROL List]** tipi basato sulla nuova tabella destinatari, è necessario creare un flusso di lavoro di targeting che genererà l&#39;elenco. Per ulteriori informazioni sugli elenchi in Campaign, consulta [questa sezione](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Passate al **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nodo dell&#39;esploratore.
1. Create un nuovo flusso di lavoro di targeting.
1. Inserite un&#39;attività **Query** seguita da un&#39;attività di aggiornamento **** Elenco.

   ![](assets/mapping_create_list_workflow01.png)

1. Fate doppio clic sull&#39;attività **Query** , quindi fate clic **[!UICONTROL Edit the query]** per scegliere una dimensione di targeting basata sullo schema della nuova tabella destinatari (nel nostro esempio: **Individuale**). Fate clic **[!UICONTROL Finish]** per confermare.

   ![](assets/mapping_create_list_workflow03.png)

1. Fate doppio clic sull&#39;attività di aggiornamento **** Elenco, quindi fate clic sul **[!UICONTROL Create the list if necessary (Computed name)]** pulsante di scelta.

   ![](assets/mapping_create_list_workflow02.png)

1. Selezionate la cartella di creazione per il nuovo elenco.
1. Eseguire il flusso di lavoro per creare l&#39;elenco.
1. Visualizzare il risultato nel nodo della struttura ad albero selezionato durante l&#39; **[!UICONTROL List update]** attività.

   Il dashboard specifica lo schema su cui si basa l&#39;elenco, come illustrato di seguito:

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>Potete anche fare riferimento a [Creazione di un elenco di video dei destinatari](https://docs.adobe.com/content/help/it-IT/campaign-classic-learn/tutorials/getting-started/creating-a-list-of-recipients.html) .

