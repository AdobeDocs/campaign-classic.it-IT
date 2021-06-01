---
product: campaign
title: Creazione di un flusso di lavoro di targeting
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 8%

---

# Creazione di un flusso di lavoro di targeting {#step-1--creating-a-targeting-workflow}

Devi creare il flusso di lavoro nella scheda **[!UICONTROL Targeting and Workflows]** di una campagna. È costituito da un’attività **[!UICONTROL Query]**, un’attività **[!UICONTROL Split]** collegata a due attività **[!UICONTROL Email delivery]**, un’attività **[!UICONTROL Wait]**, un’attività **[!UICONTROL JavaScript code]** e un’attività **[!UICONTROL Delivery]**.

1. Se non lo hai già fatto, crea una campagna (per ulteriori informazioni, consulta questa [sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vai alla scheda **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modifica l’etichetta del flusso di lavoro esistente o fai clic su **[!UICONTROL Add]** per crearne uno nuovo (per ulteriori informazioni, consulta questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilizza il mouse per trascinare e rilasciare le attività nel diagramma del flusso di lavoro, inclusa una scheda **[!UICONTROL Query]** (**[!UICONTROL Target]** ), una scheda **[!UICONTROL Split]** (**[!UICONTROL Target]** ), due schede **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]**), un’attività **[!UICONTROL Wait]** (**[!UICONTROL Flow Control]** ), un’attività **[!UICONTROL JavaScript code]** (**[!UICONTROL Actions]** scheda) e una scheda &lt;a> attività (**[!UICONTROL Actions]** scheda ).**[!UICONTROL Delivery]**

![](assets/use_case_abtesting_targetwkfl_004.png)

Ora puoi configurare i campioni di popolazione (vedi [Passaggio 2: Configura i campioni di popolazione](../../delivery/using/a-b-testing-uc-population-samples.md)).
