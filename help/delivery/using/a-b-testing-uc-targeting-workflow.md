---
product: campaign
title: Creare un flusso di lavoro di targeting
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 5%

---

# Test AB: creare un flusso di lavoro di targeting {#step-1--creating-a-targeting-workflow}

È necessario creare il flusso di lavoro nella scheda **[!UICONTROL Targeting and Workflows]** di una campagna. È costituita da un&#39;attività **[!UICONTROL Query]**, un&#39;attività **[!UICONTROL Split]** collegata a due attività **[!UICONTROL Email delivery]**, un&#39;attività **[!UICONTROL Wait]**, un&#39;attività **[!UICONTROL JavaScript code]** e un&#39;attività **[!UICONTROL Delivery]**.

1. Se non lo hai già fatto, crea una campagna. Per ulteriori informazioni, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=it){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Passa alla scheda **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifica l&#39;etichetta del flusso di lavoro esistente o fai clic su **[!UICONTROL Add]** per crearne una nuova (per ulteriori informazioni, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=it){target="_blank"}.

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilizzare il mouse per trascinare le attività nel diagramma del flusso di lavoro, incluse una scheda **[!UICONTROL Query]** (**[!UICONTROL Target]**), una scheda **[!UICONTROL Split]** (**[!UICONTROL Target]**), due schede **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]**), un&#39;attività **[!UICONTROL Wait]** (**[!UICONTROL Flow Control]**), un&#39;attività **[!UICONTROL JavaScript code]** (**[!UICONTROL Actions]**) e un&#39;attività **[!UICONTROL Delivery]** (**[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)

Ora puoi configurare i campioni di popolazione. [Ulteriori informazioni](a-b-testing-uc-population-samples.md).
