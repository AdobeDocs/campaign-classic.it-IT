---
solution: Campaign Classic
product: campaign
title: Importazione ed esportazione di pubblici
description: Importazione ed esportazione di pubblici
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 4%

---


# Importazione ed esportazione di pubblici{#importing-and-exporting-audiences}

## Importazione di un&#39;audience {#importing-an-audience}

Puoi importare audience/segmenti da Audience Manager o dal servizio di base Persone in  Adobe Campaign tramite gli elenchi dei destinatari.

1. Andate al nodo **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** nell&#39; di Adobe Campaign Explorer.
1. Nella barra delle azioni, selezionare **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Nella finestra visualizzata, fate clic su **[!UICONTROL Select a shared audience]** per passare all&#39;elenco dei tipi di pubblico/segmenti condivisi disponibili dalle altre soluzioni Adobe Experience Cloud.
1. Selezionate un&#39;audience e confermate. Le informazioni del pubblico vengono completate automaticamente.

   Per poter importare un&#39;audience condivisa, è necessario che ti sia assegnato il prodotto **[!UICONTROL Audience library]** nella console di amministrazione ed essere un amministratore nel  Audience Manager. Per ulteriori informazioni, consulta la documentazione di [Admin Console](https://helpx.adobe.com/it/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selezionare l&#39;origine dati AMC dal campo **[!UICONTROL AMC Data source]** per definire il tipo di dati previsto.

   ![](assets/aam_import_audience_2.png)

1. Salva il pubblico.

L&#39;audience viene importata tramite un flusso di lavoro tecnico. L&#39;elenco importato contiene elementi che possono essere riconciliati utilizzando l&#39;origine dati AMC. Gli elementi non riconosciuti da  Adobe Campaign non vengono importati.

La sincronizzazione del processo di importazione richiede 24-36 ore, quando i segmenti vengono importati direttamente dal servizio di base Persone o  Audience Manager. Dopo questo periodo, potrete trovare e utilizzare la nuova audience in  Adobe Campaign.

>[!NOTE]
>
>Se importate audience da  Adobe Analytics a  Adobe Campaign, queste devono prima essere condivise in Servizio core Persone o  Audience Manager. Questo processo richiede 12-24 ore, che devono essere aggiunte alla sincronizzazione di 24-36 ore con Campaign.
>
>In questo caso specifico, il periodo di condivisione dell&#39;audience può essere fino a 60 ore. Per ulteriori informazioni  condivisione dell&#39;audience Adobe Analytics nel servizio di base Persone e in Audience Manager, consultare la [documentazione](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

I dati del pubblico vengono sostituiti completamente ogni volta che vengono sincronizzati. È possibile importare solo i segmenti. I dati granulari, incluse coppie chiave-valore, caratteristiche e regole, non sono supportati.

## Esportazione di un&#39;audience {#exporting-an-audience}

Puoi esportare un&#39;audience da  Adobe Campaign a Audience Manager o al servizio di base Persone tramite un flusso di lavoro. I processi per la creazione e l&#39;utilizzo di un flusso di lavoro sono descritti in [questo documento](../../workflow/using/building-a-workflow.md). I tipi di pubblico esportati vengono salvati come segmenti nel servizio di base Persone:

1. Create un nuovo flusso di lavoro di targeting.
1. Utilizzando le diverse attività disponibili, eseguite il targeting di un set di destinatari.
1. Dopo il targeting, trascinate e rilasciate un&#39;attività **[!UICONTROL Update shared audience]**, quindi apritela.

   ![](assets/aam_export_example.png)

1. Definite l&#39;audience da esportare tramite l&#39;opzione **[!UICONTROL Select a shared audience]**. Nella finestra che si apre, potete selezionare un&#39;audience esistente o crearne una nuova.

   Se selezionate un&#39;audience esistente, solo i nuovi record verranno aggiunti all&#39;audience.

   Per esportare l&#39;elenco dei destinatari in una nuova audience, completa il campo **[!UICONTROL Segment name]**, quindi fai clic su **[!UICONTROL Create]** prima di selezionare l&#39;audience appena creata.

   Completare l&#39;operazione facendo clic sul simbolo di spunta in alto a destra nella finestra, quindi sul pulsante **[!UICONTROL OK]**.

1. Selezionare **[!UICONTROL AMC Data source]** per specificare il tipo di dati previsto. Lo schema viene determinato automaticamente.

   ![](assets/aam_export_audience_activity.png)

1. Salva il pubblico.

L&#39;audience viene quindi esportata. L&#39;attività Salva audience ha due transizioni in uscita. La transizione principale contiene i destinatari esportati correttamente. La transizione aggiuntiva contiene i destinatari che non potevano essere mappati con un ID visitatore o un ID dichiarato.

La sincronizzazione tra  servizio di base Adobe Campaign e Persone richiede 24-36 ore. Dopo questo periodo, potrai trovare la nuova audience nel servizio di base Persone e riutilizzarla in altre soluzioni Adobe Experience Cloud. Per ulteriori informazioni sull&#39;utilizzo di un&#39;audience condivisa  Adobe Campaign nel servizio di base Persone del Adobe, consultare la [documentazione](https://docs.adobe.com/content/help/en/core-services/interface/audiences/t-audience-create.html).

>[!NOTE]
>
>Per essere riconciliati, i record devono avere un Adobe Experience Cloud ID (&#39;ID visitatore&#39; o &#39;ID dichiarato&#39;). I record che non dispongono di un Adobe Experience Cloud ID vengono ignorati durante l&#39;esportazione e l&#39;importazione dei tipi di pubblico.

