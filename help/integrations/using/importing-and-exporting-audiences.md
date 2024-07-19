---
product: campaign
title: Importazione ed esportazione di tipi di pubblico
description: Importazione ed esportazione di tipi di pubblico
feature: Audiences
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 1%

---


# Importazione ed esportazione di tipi di pubblico{#importing-and-exporting-audiences}



## Importazione di un pubblico {#importing-an-audience}

Puoi importare tipi di pubblico/segmenti da Audience Manager ad Adobe Campaign tramite gli elenchi dei destinatari.

1. Vai al nodo **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** in Adobe Campaign Explorer.
1. Nella barra delle azioni, selezionare **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Nella finestra visualizzata, fai clic su **[!UICONTROL Select a shared audience]** per passare all&#39;elenco dei tipi di pubblico/segmenti condivisi disponibili dalle altre soluzioni Adobe Experience Cloud.
1. Seleziona un pubblico e conferma. Le informazioni del pubblico vengono completate automaticamente.

   Per importare un pubblico condiviso, è necessario disporre del prodotto **[!UICONTROL Audience library]** in Admin Console e, ad Audience Manager, essere un amministratore. Per ulteriori informazioni, consulta la [documentazione di Admin Console](https://helpx.adobe.com/it/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selezionare l&#39;origine dati AMC dal campo **[!UICONTROL AMC Data source]** per definire il tipo di dati previsto.

   ![](assets/aam_import_audience_2.png)

1. Salva il pubblico.

Il pubblico viene importato tramite un flusso di lavoro tecnico. L&#39;elenco importato contiene elementi che è possibile riconciliare utilizzando l&#39;origine dati AMC. Gli elementi non riconosciuti da Adobe Campaign non vengono importati.

La sincronizzazione del processo di importazione richiede 24-36 ore, quando i segmenti vengono importati direttamente da Audience Manager. Dopo questo periodo, potrai trovare e utilizzare il nuovo pubblico in Adobe Campaign.

>[!NOTE]
>
>Se importi tipi di pubblico da Adobe Analytics ad Adobe Campaign, questi devono essere condivisi in Audience Manager. Questo processo richiede 12-24 ore, che devono essere aggiunte alla sincronizzazione di 24-36 ore con Campaign.
>
>In questo caso specifico, l’arco temporale di condivisione del pubblico può essere fino a 60 ore. Per ulteriori informazioni sulla condivisione del pubblico di Adobe Analytics in Audience Manager, consulta la [documentazione di Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html){target="_blank"}.

I dati del pubblico vengono completamente sostituiti ogni volta che vengono sincronizzati. È possibile importare solo i segmenti. I dati granulari, comprese coppie chiave-valore, caratteristiche e regole, non sono supportati.

## Esportazione di un pubblico {#exporting-an-audience}

Puoi esportare un pubblico da Adobe Campaign ad Audience Manager utilizzando un flusso di lavoro. I processi per la creazione e l&#39;utilizzo di un flusso di lavoro sono descritti in [questo documento](../../workflow/using/building-a-workflow.md). I tipi di pubblico esportati vengono salvati come segmenti:

1. Crea un nuovo flusso di lavoro di targeting.
1. Utilizzando le diverse attività disponibili, esegui il targeting per un set di destinatari.
1. Dopo il targeting, trascina e rilascia un&#39;attività **[!UICONTROL Update shared audience]**, quindi aprila.

   ![](assets/aam_export_example.png)

1. Definire il pubblico da esportare tramite l&#39;opzione **[!UICONTROL Select a shared audience]**. Nella finestra visualizzata, puoi selezionare un pubblico esistente o crearne uno nuovo.

   Se selezioni un pubblico esistente, al pubblico verranno aggiunti solo i nuovi record.

   Per esportare l&#39;elenco dei destinatari in un nuovo pubblico, completare il campo **[!UICONTROL Segment name]**, quindi fare clic su **[!UICONTROL Create]** prima di selezionare il nuovo pubblico creato.

   Completare l&#39;operazione facendo clic sul simbolo di spunta in alto a destra della finestra, quindi sul pulsante **[!UICONTROL OK]**.

1. Selezionare **[!UICONTROL AMC Data source]** per specificare il tipo di dati previsto. Lo schema viene determinato automaticamente.

   ![](assets/aam_export_audience_activity.png)

1. Salva il pubblico.

Il pubblico viene quindi esportato. L’attività Save audience dispone di due transizioni in uscita. La transizione principale contiene i destinatari esportati correttamente. La transizione aggiuntiva contiene i destinatari che non potevano essere mappati con un ID visitatore o un ID dichiarato.

La sincronizzazione tra le soluzioni richiede 24-36 ore. Dopo questo periodo, potrai trovare il nuovo pubblico e riutilizzarlo in altre soluzioni Adobe Experience Cloud. Per ulteriori informazioni sull&#39;utilizzo di un pubblico condiviso di Adobe Campaign, consulta questa [documentazione](https://experienceleague.adobe.com/en/docs/core-services/interface/services/audiences/create){target="_blank"}.

>[!NOTE]
>
>Per la riconciliazione, i record devono avere un Adobe Experience Cloud ID (&quot;ID visitatore&quot; o &quot;ID dichiarato&quot;). I record che non hanno un Adobe Experience Cloud ID vengono ignorati durante l’esportazione e l’importazione di tipi di pubblico.
