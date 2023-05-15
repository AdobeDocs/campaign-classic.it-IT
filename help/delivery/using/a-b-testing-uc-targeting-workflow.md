---
product: campaign
title: Creare un flusso di lavoro di targeting
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# Creare un flusso di lavoro di targeting {#step-1--creating-a-targeting-workflow}



È necessario creare il flusso di lavoro nel **[!UICONTROL Targeting and Workflows]** scheda di una campagna. È costituito da un **[!UICONTROL Query]** un’attività **[!UICONTROL Split]** attività collegata a due **[!UICONTROL Email delivery]** attività, **[!UICONTROL Wait]** un’attività **[!UICONTROL JavaScript code]** e un **[!UICONTROL Delivery]** attività.

1. Se non lo hai già fatto, crea una campagna (per ulteriori informazioni, consulta [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vai alla scheda **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifica l’etichetta del flusso di lavoro esistente o fai clic su **[!UICONTROL Add]** per crearne una nuova (per ulteriori informazioni, consulta [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilizza il mouse per trascinare le attività nel diagramma del flusso di lavoro, incluso un **[!UICONTROL Query]** (**[!UICONTROL Target]** scheda), a **[!UICONTROL Split]** (**[!UICONTROL Target]** scheda), due **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** scheda), a **[!UICONTROL Wait]** attività (**[!UICONTROL Flow Control]** scheda), a **[!UICONTROL JavaScript code]** attività (**[!UICONTROL Actions]** scheda ), e a **[!UICONTROL Delivery]** attività (**[!UICONTROL Actions]** ).

![](assets/use_case_abtesting_targetwkfl_004.png)

Ora puoi configurare i campioni di popolazione. [Ulteriori informazioni](a-b-testing-uc-population-samples.md).
