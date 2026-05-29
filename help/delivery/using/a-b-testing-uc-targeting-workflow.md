---
product: campaign
title: Creare un flusso di lavoro di targeting
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
TQID: https://experienceleague.adobe.com/D4O223FYCiIwT-P4WCXa1gYjxB56lCGVIuGL3x-fDRo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
subfeature_v2: id: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 168
ht-degree: 23%

---

# Test AB: creare un flusso di lavoro di targeting {#step-1--creating-a-targeting-workflow}

È necessario creare il flusso di lavoro nella scheda **[!UICONTROL Targeting and Workflows]** di una campagna. È costituita da un&#39;attività **[!UICONTROL Query]**, un&#39;attività **[!UICONTROL Split]** collegata a due attività **[!UICONTROL Email delivery]**, un&#39;attività **[!UICONTROL Wait]**, un&#39;attività **[!UICONTROL JavaScript code]** e un&#39;attività **[!UICONTROL Delivery]**.

1. Se non lo hai già fatto, crea una campagna. Per ulteriori informazioni, fai riferimento alla [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=it){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vai alla scheda **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifica l&#39;etichetta del flusso di lavoro esistente o fai clic su **[!UICONTROL Add]** per crearne una nuova (per ulteriori informazioni, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=it){target="_blank"}.

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilizzare il mouse per trascinare le attività nel diagramma del flusso di lavoro, incluse una scheda **[!UICONTROL Query]** (**[!UICONTROL Target]**), una scheda **[!UICONTROL Split]** (**[!UICONTROL Target]**), due schede **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]**), un&#39;attività **[!UICONTROL Wait]** (**[!UICONTROL Flow Control]**), un&#39;attività **[!UICONTROL JavaScript code]** (**[!UICONTROL Actions]**) e un&#39;attività **[!UICONTROL Delivery]** (**[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)

Ora puoi configurare i campioni di popolazione. [Ulteriori informazioni](a-b-testing-uc-population-samples.md).
