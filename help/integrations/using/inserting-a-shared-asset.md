---
product: campaign
title: Inserimento di una risorsa condivisa
description: Inserimento di una risorsa condivisa
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: d399c4800fe6c5b128a6ccb5fec15262cbef5ee8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# Inserimento di una risorsa condivisa{#inserting-a-shared-asset}

Le risorse condivise da Adobe Experience Cloud possono essere utilizzate nelle e-mail e nelle pagine di destinazione come segue:

1. Crea un nuovo messaggio e-mail o una nuova pagina di destinazione.

   Se utilizzi risorse dalla libreria delle risorse di Adobe Experience Manager, utilizza un modello di consegna creato quando [configurazione dell’integrazione](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Se non disponi di questo modello specifico, assicurati che nella consegna **Proprietà**, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** è impostato su **DCE** e che sia fornito l’account esterno AEM che desideri utilizzare per accedere alla libreria di risorse di AEM Assets.

1. Nella finestra di modifica, seleziona l’opzione per aggiungere un’immagine:

   * Se utilizzi [modalità di modifica standard](../../delivery/using/defining-the-email-content.md#adding-images), seleziona **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * Se utilizzi [modalità di modifica avanzata](../../web/using/about-campaign-html-editor.md) (DCE), passa a un blocco immagine, quindi seleziona dal menu contestuale **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >Non è possibile inserire immagini condivise da Adobe Campaign in [accesso web](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) quando si utilizza il DCE.

1. Nella finestra di selezione visualizzata, seleziona un’immagine e conferma.

   Le immagini disponibili provengono dalla libreria Adobe Experience Cloud o dalla libreria AEM Assets, a seconda della configurazione dell’istanza Adobe Campaign. Fai riferimento a [Configurazione dell’accesso alle risorse](../../integrations/using/configuring-access-to-assets.md) sezione .

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Se utilizzi l’integrazione con Adobe Target, puoi utilizzare un’immagine condivisa come immagine predefinita. Consulta [questa pagina](../../integrations/using/integrating-with-adobe-target.md).
