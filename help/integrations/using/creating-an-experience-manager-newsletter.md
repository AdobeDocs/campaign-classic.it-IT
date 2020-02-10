---
title: Creazione di una newsletter Experience Manager
seo-title: Creazione di una newsletter Experience Manager
description: Creazione di una newsletter Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Creazione di una newsletter Experience Manager{#creating-an-experience-manager-newsletter}

Questa integrazione può essere utilizzata ad esempio per creare una newsletter in Adobe Experience Manager che verrà quindi utilizzata in Adobe Campaign come parte di una campagna e-mail.

Per un esempio più dettagliato su come utilizzare questa integrazione, consultate questa guida [](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html)dettagliata.

**Da Adobe Experience Manager:**

1. Dall’istanza di creazione di AEM, fate clic sul logo **Adobe Experience** in alto a sinistra nella pagina e selezionate **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Selezionare **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Master Area > Email campaigns]**.
1. Fare clic sul **[!UICONTROL Create]** pulsante in alto a destra della pagina, quindi selezionare **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Selezionate il **[!UICONTROL Adobe Campaign Email (AC 6.1)]** modello e assegnate un nome alla newsletter.
1. Una volta creata la pagina, accedete al **[!UICONTROL Page information]** menu e fate clic su **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Nella **[!UICONTROL Cloud Services]** scheda, seleziona **[!UICONTROL Adobe Campaign]** come **[!UICONTROL Cloud service configuration]** e la tua istanza di Adobe Campaign nel secondo elenco a discesa.

   ![](assets/aem_uc_4.png)

1. Modifica il contenuto delle e-mail aggiungendo componenti, ad esempio campi di personalizzazione da Adobe Campaign.
1. Quando il messaggio e-mail è pronto, accedete al **[!UICONTROL Page information]** menu e fate clic su **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Dal primo elenco a discesa, selezionate **[!UICONTROL Publish to Adobe Campaign]** come modello di workflow e fate clic su **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Quindi, come nel passaggio precedente, avviate il **[!UICONTROL Approve for Campaign]** flusso di lavoro.
1. Nella parte superiore della pagina viene visualizzata una dichiarazione di non responsabilità. Fate clic **[!UICONTROL Complete]** per confermare la revisione e fate clic su **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Fai di nuovo clic **[!UICONTROL Complete]** e seleziona **[!UICONTROL Newsletter approval]** nel **[!UICONTROL Next Step]** menu a discesa.

   ![](assets/aem_uc_8.png)

La newsletter è ora pronta e sincronizzata in Adobe Campaign.

**Da Adobe Campaign:**

1. Dalla **[!UICONTROL Campaigns]** scheda, fare clic **[!UICONTROL Deliveries]** quindi **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Nel **[!UICONTROL Delivery template]** menu a discesa, selezionate il **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** modello.

   ![](assets/aem_uc_10.png)

1. Aggiungi una **[!UICONTROL Label]** consegna e fai clic su **[!UICONTROL Continue]**.
1. Fate clic sul **[!UICONTROL Synchronize]** pulsante.

   Se il pulsante non è visualizzato nell&#39;interfaccia, fare clic sul **[!UICONTROL Properties]** pulsante e selezionare la **[!UICONTROL Advanced]** scheda. Il **[!UICONTROL Content editing mode]** campo deve essere impostato su **[!UICONTROL AEM]** con l’istanza AEM presente nel **[!UICONTROL AEM account]** campo.

   ![](assets/aem_uc_11.png)

1. Seleziona la consegna precedentemente creata in Adobe Experience Manager e fai clic su **[!UICONTROL Ok]**.
1. Non appena vengono apportate alcune modifiche alla consegna di AEM, fai clic **[!UICONTROL Refresh content]** sul pulsante .

   ![](assets/aem_uc_12.png)

L&#39;e-mail è ora pronta per essere inviata al pubblico.
