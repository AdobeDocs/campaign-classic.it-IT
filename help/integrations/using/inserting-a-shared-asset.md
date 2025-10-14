---
product: campaign
title: Inserimento di una risorsa condivisa
description: Inserimento di una risorsa condivisa
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 1%

---

# Inserimento di una risorsa condivisa{#inserting-a-shared-asset}

Assets condiviso da Adobe Experience Cloud può essere utilizzato nelle e-mail e nelle pagine di destinazione come segue:

1. Crea una nuova e-mail o una nuova pagina di destinazione.

   Se utilizzi risorse dalla libreria di risorse Adobe Experience Manager, utilizza un modello di consegna creato durante la [configurazione dell&#39;integrazione](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Se non disponi di questo modello specifico, assicurati che nella consegna **Proprietà**, la scheda **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]**) sia impostata su **DCE** e che sia fornito l&#39;account esterno AEM che desideri utilizzare per accedere alla libreria di risorse AEM Assets.

1. Nella finestra di modifica, seleziona l’opzione per aggiungere un’immagine:

   * Se si utilizza la [modalità di modifica standard](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html#adding-images){target="_blank"}, selezionare **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * Se utilizzi la [modalità di modifica avanzata](../../web/using/about-campaign-html-editor.md) (DCE), passa a un blocco di immagine e seleziona **[!UICONTROL Select a shared asset]** tramite il menu contestuale.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >Impossibile inserire immagini condivise da Adobe Campaign in [accesso Web](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) quando si utilizza DCE.

1. Nella finestra di selezione visualizzata, seleziona un’immagine, quindi conferma.

   Le immagini disponibili provengono dalla libreria Adobe Experience Cloud o dalla libreria AEM Assets, a seconda di come è configurata la tua istanza di Adobe Campaign. Consulta la sezione [Configurazione dell&#39;accesso ad Assets](../../integrations/using/configuring-access-to-assets.md).

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Se utilizzi l’integrazione con Adobe Target, puoi utilizzare un’immagine condivisa come immagine predefinita. Consulta [questa pagina](../../integrations/using/integrating-with-adobe-target.md).
