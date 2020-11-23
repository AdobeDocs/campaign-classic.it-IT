---
solution: Campaign Classic
product: campaign
title: Inserimento di una risorsa condivisa
description: Inserimento di una risorsa condivisa
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---


# Inserimento di una risorsa condivisa{#inserting-a-shared-asset}

Le risorse condivise da Adobe Experience Cloud possono essere utilizzate nelle e-mail e nelle pagine di destinazione come segue:

1. Create un nuovo messaggio e-mail o una nuova pagina di destinazione.

   Se utilizzate risorse dalla libreria delle risorse di Adobe Experience Manager, utilizzate un modello di consegna creato al momento della [configurazione dell&#39;integrazione](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Se non si dispone di questo modello specifico, assicurarsi che in **Proprietà** consegna, la **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** scheda) sia impostata su **DCE** e che sia fornito l&#39;account esterno AEM che si desidera utilizzare per accedere alla  libreria delle risorse AEM Assets.

1. Nella finestra di modifica, selezionate l’opzione per aggiungere un’immagine:

   * Se utilizzate la modalità [di modifica](../../delivery/using/defining-the-email-content.md#adding-images)standard, selezionate **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * Se si utilizza la modalità [di modifica](../../web/using/about-campaign-html-editor.md) avanzata (DCE), passare a un blocco immagine e quindi dal menu contestuale selezionare **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >Non è possibile inserire immagini condivise da  Adobe Campaign nell&#39;accesso [](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) Web quando si utilizza DCE.

1. Nella finestra di selezione che si apre, selezionate un’immagine, quindi confermate.

   Le immagini disponibili provengono dalla libreria Adobe Experience Cloud o dalla  libreria AEM Assets, a seconda della configurazione dell’istanza  Adobe Campaign. Consulta la sezione [Configurazione dell’accesso alle risorse](../../integrations/using/configuring-access-to-assets.md) .

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Se utilizzate l&#39;integrazione con  Adobe Target, potete utilizzare un&#39;immagine condivisa come immagine predefinita. Consulta [questa pagina](../../integrations/using/integrating-with-adobe-target.md).

