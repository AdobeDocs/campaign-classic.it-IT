---
product: campaign
title: Creare un flusso di lavoro di targeting
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# Test AB: creare un flusso di lavoro di targeting {#step-1--creating-a-targeting-workflow}

È necessario creare il flusso di lavoro in **[!UICONTROL Targeting and Workflows]** di una campagna. È costituito da un **[!UICONTROL Query]** attività, a **[!UICONTROL Split]** attività collegata a due **[!UICONTROL Email delivery]** attività, a **[!UICONTROL Wait]** attività, a **[!UICONTROL JavaScript code]** attività e un **[!UICONTROL Delivery]** attività.

1. Se non lo hai già fatto, crea una campagna (per ulteriori informazioni, consulta [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vai a **[!UICONTROL Targeting and Workflows]** scheda.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifica l’etichetta del flusso di lavoro esistente o fai clic su **[!UICONTROL Add]** per crearne uno nuovo (per ulteriori informazioni, consulta [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilizza il mouse per trascinare e rilasciare le attività nel diagramma del flusso di lavoro, incluso un **[!UICONTROL Query]** (**[!UICONTROL Target]** ), una **[!UICONTROL Split]** (**[!UICONTROL Target]** , due **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** ), una **[!UICONTROL Wait]** attività (**[!UICONTROL Flow Control]** ), una **[!UICONTROL JavaScript code]** attività (**[!UICONTROL Actions]** ) e un **[!UICONTROL Delivery]** attività (**[!UICONTROL Actions]** ).

![](assets/use_case_abtesting_targetwkfl_004.png)

Ora puoi configurare i campioni di popolazione. [Ulteriori informazioni](a-b-testing-uc-population-samples.md).
