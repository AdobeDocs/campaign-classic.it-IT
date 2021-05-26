---
solution: Campaign Classic
product: campaign
title: Importazione ed esportazione di pubblici
description: Importazione ed esportazione di pubblici
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 4%

---

# Importazione ed esportazione di pubblici{#importing-and-exporting-audiences}

## Importazione di un pubblico {#importing-an-audience}

Puoi importare tipi di pubblico/segmenti da Audience Manager o dal servizio core Persone in Adobe Campaign tramite gli elenchi dei destinatari.

1. Passa al nodo **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** nell’explorer di Adobe Campaign.
1. Nella barra delle azioni, seleziona **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Nella finestra visualizzata, fai clic su **[!UICONTROL Select a shared audience]** per passare all’elenco dei tipi di pubblico/segmenti condivisi disponibili dalle altre soluzioni Adobe Experience Cloud.
1. Seleziona un pubblico e conferma. Le informazioni sul pubblico vengono completate automaticamente.

   Per poter importare il pubblico condiviso, devi assegnare il prodotto **[!UICONTROL Audience library]** in Admin Console ed essere un amministratore in Audience Manager. Per ulteriori informazioni, consulta la documentazione di [Admin Console](https://helpx.adobe.com/it/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Seleziona l’origine dati AMC dal campo **[!UICONTROL AMC Data source]** per definire il tipo di dati previsto.

   ![](assets/aam_import_audience_2.png)

1. Salva il pubblico.

Il pubblico viene importato tramite un flusso di lavoro tecnico. L’elenco importato contiene elementi che possono essere riconciliati utilizzando l’origine dati AMC. Gli elementi non riconosciuti da Adobe Campaign non vengono importati.

La sincronizzazione del processo di importazione richiede 24-36 ore, quando i segmenti vengono importati direttamente dal servizio core Persone o da Audience Manager. Dopo questo periodo, potrai trovare e utilizzare il nuovo pubblico in Adobe Campaign.

>[!NOTE]
>
>Se importi dei tipi di pubblico da Adobe Analytics ad Adobe Campaign, questi devono prima essere condivisi in Servizio core Persone o in Audience Manager. Questo processo richiede 12-24 ore, che devono essere aggiunte alla sincronizzazione di 24-36 ore con Campaign.
>
>In questo caso specifico, il tempo di condivisione del pubblico può essere fino a 60 ore. Per ulteriori informazioni sulla condivisione del pubblico di Adobe Analytics nel servizio core Persone e in Audience Manager, consulta la [documentazione di Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

I dati del pubblico vengono completamente sostituiti ogni volta che viene sincronizzato. È possibile importare solo i segmenti. I dati granulari tra cui coppie chiave-valore, caratteristiche e regole non sono supportati.

## Esportazione di un pubblico {#exporting-an-audience}

Puoi esportare un pubblico da Adobe Campaign a Audience Manager o al servizio core Persone utilizzando un flusso di lavoro. I processi per la creazione e l&#39;utilizzo di un flusso di lavoro sono descritti in [questo documento](../../workflow/using/building-a-workflow.md). I tipi di pubblico esportati vengono salvati come segmenti nel servizio core Persone:

1. Crea un nuovo flusso di lavoro di targeting.
1. Utilizzando le diverse attività disponibili, esegui il targeting di un set di destinatari.
1. Dopo il targeting, trascina e rilascia un’attività **[!UICONTROL Update shared audience]**, quindi aprila.

   ![](assets/aam_export_example.png)

1. Definisci il pubblico da esportare tramite l’opzione **[!UICONTROL Select a shared audience]** . Nella finestra visualizzata, puoi selezionare un pubblico esistente o crearne uno nuovo.

   Se selezioni un pubblico esistente, verranno aggiunti al pubblico solo i nuovi record.

   Per esportare l’elenco dei destinatari in un nuovo pubblico, completa il campo **[!UICONTROL Segment name]** , quindi fai clic su **[!UICONTROL Create]** prima di selezionare il pubblico appena creato.

   Completare l&#39;operazione facendo clic sul simbolo di spunta in alto a destra nella finestra, quindi sul pulsante **[!UICONTROL OK]**.

1. Seleziona il **[!UICONTROL AMC Data source]** per specificare il tipo di dati previsto. Lo schema viene determinato automaticamente.

   ![](assets/aam_export_audience_activity.png)

1. Salva il pubblico.

Il pubblico viene quindi esportato. L’attività Save audience dispone di due transizioni in uscita. La transizione principale contiene i destinatari che sono stati esportati correttamente. La transizione aggiuntiva contiene i destinatari che non potevano essere stati mappati con un ID visitatore o un ID dichiarato.

La sincronizzazione tra Adobe Campaign e il servizio core People richiede 24-36 ore. Dopo questo periodo, potrai trovare il nuovo pubblico nel servizio core Persone e riutilizzarlo in altre soluzioni Adobe Experience Cloud. Per ulteriori informazioni sull&#39;utilizzo di un pubblico condiviso di Adobe Campaign nel servizio core Persone di Adobe, consulta questa [documentazione](https://docs.adobe.com/content/help/en/core-services/interface/audiences/t-audience-create.html).

>[!NOTE]
>
>Per essere riconciliati, i record devono avere un Adobe Experience Cloud ID (&quot;ID visitatore&quot; o &quot;ID dichiarato&quot;). I record privi di un ID Adobe Experience Cloud vengono ignorati durante l’esportazione e l’importazione di tipi di pubblico.
