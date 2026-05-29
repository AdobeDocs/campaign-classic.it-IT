---
product: campaign
title: Creazione di un elenco di profili con un flusso di lavoro
description: Scopri come creare un elenco di profili in un flusso di lavoro
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
TQID: https://experienceleague.adobe.com/km2D2qnUAdgDCauLUYcWSC-J567twPEyvaZBsLDAOKA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 11%

---

# Creazione di un elenco di profili con un flusso di lavoro{#creating-a-profile-list-with-a-workflow}


Per creare un elenco di tipi **[!UICONTROL List]** basato sulla nuova tabella dei destinatari, è necessario creare un flusso di lavoro di targeting che genererà l&#39;elenco.

Per ulteriori informazioni sugli elenchi in Campaign, consulta [questa sezione](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Guarda un video su questa funzione](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Per creare un flusso di lavoro di targeting e aggiornare i destinatari in una tabella dei destinatari personalizzata, effettua le seguenti operazioni:

1. Vai al nodo **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** dell&#39;Explorer.
1. Crea un nuovo flusso di lavoro di targeting.
1. Inserisci un&#39;attività **Query** seguita da un&#39;attività **List update**.

   ![](assets/mapping_create_list_workflow01.png)

1. Fai doppio clic sull&#39;attività **Query**, quindi fai clic su **[!UICONTROL Edit the query]** per scegliere una dimensione di targeting basata sullo schema della nuova tabella dei destinatari (nel nostro esempio: **Individual**). Fai clic su **[!UICONTROL Finish]** per confermare.

   ![](assets/mapping_create_list_workflow03.png)

1. Fare doppio clic sull&#39;attività **Aggiornamento elenco**, quindi selezionare il pulsante di opzione **[!UICONTROL Create the list if necessary (Computed name)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Selezionare la cartella di creazione per il nuovo elenco.
1. Esegui il flusso di lavoro per creare l’elenco.
1. Visualizzare il risultato nel nodo della struttura selezionata durante l&#39;attività **[!UICONTROL List update]**.

   Il dashboard specifica lo schema su cui si basa l’elenco, come illustrato di seguito:

   ![](assets/mapping_list_view.png)
