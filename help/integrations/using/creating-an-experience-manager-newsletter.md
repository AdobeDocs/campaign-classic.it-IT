---
title: Creazione di una newsletter  Experience Manager
seo-title: Creazione di una newsletter  Experience Manager
description: Creazione di una newsletter  Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%

---


# Creating an Experience Manager newsletter{#creating-an-experience-manager-newsletter}

Questa integrazione può essere utilizzata, ad esempio, per creare una newsletter in Adobe Experience Manager che verrà quindi utilizzata in  Adobe Campaign come parte di una campagna e-mail.

Per un esempio più dettagliato sull&#39;utilizzo di questa integrazione, consultate questa guida [](https://helpx.adobe.com/campaign/kb/acc-aem.html)dettagliata.

**Da Adobe Experience Manager:**

1. Dall’istanza di creazione AEM, fate clic sul logo **Adobe Experience** in alto a sinistra nella pagina e selezionate **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Seleziona **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Fare clic sul **[!UICONTROL Create]** pulsante in alto a destra della pagina, quindi selezionare **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Selezionate il **[!UICONTROL Adobe Campaign Email (AC 6.1)]** modello e assegnate un nome alla newsletter.
1. Una volta creata la pagina, accedete al **[!UICONTROL Page information]** menu e fate clic su **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Nella **[!UICONTROL Cloud Services]** scheda, selezionate **[!UICONTROL Adobe Campaign]** come **[!UICONTROL Cloud service configuration]** e l’istanza Adobe Campaign  nel secondo elenco a discesa.

   ![](assets/aem_uc_4.png)

1. Modificate il contenuto delle e-mail aggiungendo componenti, ad esempio campi di personalizzazione da  Adobe Campaign.
1. Quando il messaggio e-mail è pronto, accedete al **[!UICONTROL Page information]** menu e fate clic su **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Dal primo elenco a discesa, selezionate **[!UICONTROL Publish to Adobe Campaign]** come modello di workflow e fate clic su **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Quindi, come nel passaggio precedente, avviate il **[!UICONTROL Approve for Campaign]** flusso di lavoro.
1. Nella parte superiore della pagina viene visualizzata una dichiarazione di non responsabilità. Fate clic **[!UICONTROL Complete]** per confermare la revisione e fate clic su **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Fai di nuovo clic **[!UICONTROL Complete]** e seleziona **[!UICONTROL Newsletter approval]** nel **[!UICONTROL Next Step]** menu a discesa.

   ![](assets/aem_uc_8.png)

La newsletter è ora pronta e sincronizzata in  Adobe Campaign.

**Da  Adobe Campaign:**

1. From the **[!UICONTROL Campaigns]** tab, click **[!UICONTROL Deliveries]** then **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Nel **[!UICONTROL Delivery template]** menu a discesa, selezionate il **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** modello.

   ![](assets/aem_uc_10.png)

1. Aggiungi un **[!UICONTROL Label]** elemento alla consegna e fai clic su **[!UICONTROL Continue]**.
1. Fai clic sul pulsante **[!UICONTROL Synchronize]**.

   Se il pulsante non è visualizzato nell&#39;interfaccia, fare clic sul **[!UICONTROL Properties]** pulsante e selezionare la **[!UICONTROL Advanced]** scheda. Il **[!UICONTROL Content editing mode]** campo deve essere impostato su **[!UICONTROL AEM]** con l&#39;istanza AEM nel **[!UICONTROL AEM account]** campo.

   ![](assets/aem_uc_11.png)

1. Selezionate la consegna precedentemente creata in Adobe Experience Manager e fate clic su **[!UICONTROL Ok]**.
1. Fai clic sul **[!UICONTROL Refresh content]** pulsante non appena vengono apportate alcune modifiche alla consegna AEM.

   ![](assets/aem_uc_12.png)

L&#39;e-mail è ora pronta per essere inviata al pubblico.
