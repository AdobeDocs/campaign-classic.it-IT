---
title: Importazione ed esportazione di audience
seo-title: Importazione ed esportazione di audience
description: Importazione ed esportazione di audience
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Importing and exporting audiences{#importing-and-exporting-audiences}

## Importazione di un&#39;audience {#importing-an-audience}

Puoi importare audience/segmenti da Audience Manager o dal servizio di base Persone in Adobe Campaign tramite gli elenchi dei destinatari.

1. Vai al nodo **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** in Adobe Campaign Explorer.
1. Nella barra delle azioni, selezionate **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Nella finestra visualizzata, fai clic **[!UICONTROL Select a shared audience]** per passare all&#39;elenco dei tipi di pubblico/segmenti condivisi disponibili dalle altre soluzioni Adobe Experience Cloud.
1. Selezionate un&#39;audience e confermate. Le informazioni del pubblico vengono completate automaticamente.

   Nota: per poter importare un&#39;audience condivisa, devi essere assegnato al **[!UICONTROL Audience library]** prodotto nella console di amministrazione ed essere un amministratore in Audience Manager. Per ulteriori informazioni, consulta la documentazione [di](https://helpx.adobe.com/enterprise/managing/user-guide.html)Admin Console.

   ![](assets/aam_import_audience_3.png)

1. Selezionare l&#39;origine dati AMC dal **[!UICONTROL AMC Data source]** campo per definire il tipo di dati previsto.

   ![](assets/aam_import_audience_2.png)

1. Salva il pubblico.

Il pubblico viene importato tramite un flusso di lavoro tecnico. L&#39;elenco importato contiene elementi che possono essere riconciliati utilizzando l&#39;origine dati AMC. Gli elementi non riconosciuti da Adobe Campaign non vengono importati.

La sincronizzazione del processo di importazione richiede 24-36 ore, quando i segmenti vengono importati direttamente dal servizio di base Persone o da Audience Manager. Dopo questo periodo, potrai trovare e utilizzare la nuova audience in Adobe Campaign.

>[!NOTE]
>
>Se importate audience da Adobe Analytics ad Adobe Campaign, queste audience devono essere condivise per la prima volta in Servizio di base Persone o Audience Manager. Questo processo richiede 12-24 ore, che devono essere aggiunte alla sincronizzazione di 24-36 ore con Campaign.
>
>In questo caso specifico, il periodo di condivisione dell&#39;audience può essere fino a 60 ore. Per ulteriori informazioni sulla condivisione dell&#39;audience di Adobe Analytics nel servizio People Core e nel gestore dell&#39;audience, consulta questa [documentazione](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html).

I dati del pubblico vengono sostituiti completamente ogni volta che vengono sincronizzati. È possibile importare solo i segmenti. I dati granulari, incluse coppie chiave-valore, caratteristiche e regole, non sono supportati.

## Esportazione di un&#39;audience {#exporting-an-audience}

Puoi esportare un&#39;audience da Adobe Campaign a Audience Manager o al servizio di base Persone tramite un flusso di lavoro. I processi per la creazione e l&#39;utilizzo di un flusso di lavoro sono descritti in [questo documento](../../workflow/using/building-a-workflow.md). I tipi di pubblico esportati vengono salvati come segmenti nel servizio di base Persone:

1. Create un nuovo flusso di lavoro di targeting.
1. Utilizzando le diverse attività disponibili, eseguite il targeting di un set di destinatari.
1. Dopo il targeting, trascinate e rilasciate un&#39; **[!UICONTROL Update shared audience]** attività, quindi apritela.

   ![](assets/aam_export_example.png)

1. Definite l&#39;audience da esportare tramite l&#39; **[!UICONTROL Select a shared audience]** opzione. Nella finestra che si apre, potete selezionare un&#39;audience esistente o crearne una nuova.

   Se selezionate un&#39;audience esistente, solo i nuovi record verranno aggiunti all&#39;audience.

   Per esportare l&#39;elenco dei destinatari in una nuova audience, completa il **[!UICONTROL Segment name]** campo e fai clic **[!UICONTROL Create]** prima di selezionare l&#39;audience appena creata.

   Completare l&#39;operazione facendo clic sul simbolo di controllo in alto a destra nella finestra, quindi sul **[!UICONTROL OK]** pulsante.

1. Selezionare l&#39;opzione **[!UICONTROL AMC Data source]** per specificare il tipo di dati previsto. Lo schema viene determinato automaticamente.

   ![](assets/aam_export_audience_activity.png)

1. Salva il pubblico.

L&#39;audience viene quindi esportata. L&#39;attività Salva audience ha due transizioni in uscita. La transizione principale contiene i destinatari esportati correttamente. La transizione aggiuntiva contiene i destinatari che non potevano essere mappati con un ID visitatore o un ID dichiarato.

La sincronizzazione tra Adobe Campaign e il servizio di base Persone richiede 24-36 ore. Dopo questo periodo, potrai trovare il nuovo pubblico nel servizio di base Persone e riutilizzarlo in altre soluzioni Adobe Experience Cloud. Per ulteriori informazioni sull&#39;utilizzo di un&#39;audience condivisa di Adobe Campaign nel servizio di base Adobe People, consulta questa [documentazione](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html).

>[!NOTE]
>
>Per essere riconciliati, i record devono avere un Adobe Experience Cloud ID (&#39;ID visitatore&#39; o &#39;ID dichiarato&#39;). I record che non dispongono di un Adobe Experience Cloud ID vengono ignorati durante l&#39;esportazione e l&#39;importazione dei tipi di pubblico.

