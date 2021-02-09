---
solution: Campaign Classic
product: campaign
title: Creazione di un flusso di lavoro di targeting
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 9%

---


# Creazione di un flusso di lavoro di targeting {#step-1--creating-a-targeting-workflow}

È necessario creare il flusso di lavoro nella scheda **[!UICONTROL Targeting and Workflows]** di una campagna. È composta da un&#39;attività **[!UICONTROL Query]**, un&#39;attività **[!UICONTROL Split]** collegata a due attività **[!UICONTROL Email delivery]**, un&#39;attività **[!UICONTROL Wait]**, un&#39;attività **[!UICONTROL JavaScript code]** e un&#39;attività **[!UICONTROL Delivery]**.

1. Se non lo avete ancora fatto, create una campagna (per ulteriori informazioni, fate riferimento a questa [sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vai alla scheda **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modificate l&#39;etichetta del flusso di lavoro esistente o fate clic su **[!UICONTROL Add]** per crearne uno nuovo (per ulteriori informazioni, consultate questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilizzare il mouse per trascinare le attività nel diagramma del flusso di lavoro, inclusa una **[!UICONTROL Query]** (**[!UICONTROL Target]** scheda), una **[!UICONTROL Split]** (**[!UICONTROL Target]** scheda), due **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** scheda), un&#39;attività **[!UICONTROL Wait]** (**[!UICONTROL Flow Control]** scheda), un&#39;attività **[!UICONTROL JavaScript code]** (**[!UICONTROL Actions]** scheda) e una **[!UICONTROL Delivery]** attività (**[!UICONTROL Actions]** scheda).

![](assets/use_case_abtesting_targetwkfl_004.png)
