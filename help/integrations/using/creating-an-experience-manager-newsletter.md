---
product: campaign
title: Creazione di una newsletter di Experience Manager
description: Creazione di una newsletter di Experience Manager
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# Creazione di una newsletter di Experience Manager{#creating-an-experience-manager-newsletter}

![](../../assets/common.svg)

Questa integrazione può essere utilizzata ad esempio per creare una newsletter in Adobe Experience Manager che verrà quindi utilizzata in Adobe Campaign come parte di una campagna e-mail.

**Da Adobe Experience Manager:**

1. Nell’istanza di authoring AEM, fai clic sul pulsante **Adobe Experience** in alto a sinistra nella pagina e seleziona **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Seleziona **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Fai clic sul pulsante **[!UICONTROL Create]** in alto a destra nella pagina, quindi seleziona **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Seleziona la **[!UICONTROL Adobe Campaign Email (AC 6.1)]** modello e nome della newsletter.
1. Una volta creata la pagina, accedi al **[!UICONTROL Page information]** menu e fai clic su **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. In **[!UICONTROL Cloud Services]** scheda , seleziona **[!UICONTROL Adobe Campaign]** come **[!UICONTROL Cloud service configuration]** e la tua istanza Adobe Campaign nel secondo menu a discesa.

   ![](assets/aem_uc_4.png)

1. Modifica il contenuto delle e-mail aggiungendo componenti, ad esempio campi di personalizzazione da Adobe Campaign.
1. Quando l’e-mail è pronta, accedi al **[!UICONTROL Page information]** menu e fai clic su **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Dal primo menu a discesa, seleziona **[!UICONTROL Publish to Adobe Campaign]** come modello di flusso di lavoro e fai clic su **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Quindi, come nel passaggio precedente, avvia il **[!UICONTROL Approve for Campaign]** workflow.
1. Nella parte superiore della pagina viene visualizzata una liberatoria. Fai clic su **[!UICONTROL Complete]** per confermare la revisione e fare clic su **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Fai clic nuovamente **[!UICONTROL Complete]** e seleziona **[!UICONTROL Newsletter approval]** in **[!UICONTROL Next Step]** a discesa.

   ![](assets/aem_uc_8.png)

La newsletter è ora pronta e sincronizzata in Adobe Campaign.

**Da Adobe Campaign:**

1. Da **[!UICONTROL Campaigns]** scheda , fai clic su **[!UICONTROL Deliveries]** then **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. In **[!UICONTROL Delivery template]** a discesa, seleziona il **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** modello.

   ![](assets/aem_uc_10.png)

1. Aggiungi un **[!UICONTROL Label]** alla consegna e fai clic su **[!UICONTROL Continue]**.
1. Fai clic sul pulsante **[!UICONTROL Synchronize]**.

   Se questo pulsante non viene visualizzato nell’interfaccia, fai clic sul pulsante **[!UICONTROL Properties]** e seleziona il pulsante **[!UICONTROL Advanced]** scheda . La **[!UICONTROL Content editing mode]** campo impostato su **[!UICONTROL AEM]** con la tua istanza AEM nel **[!UICONTROL AEM account]** campo .

   ![](assets/aem_uc_11.png)

1. Seleziona la consegna creata in precedenza in Adobe Experience Manager e fai clic su **[!UICONTROL Ok]**.
1. Fai clic sul pulsante **[!UICONTROL Refresh content]** non appena vengono apportate alcune modifiche alla consegna AEM.

   ![](assets/aem_uc_12.png)

L’e-mail è ora pronta per essere inviata al pubblico.
