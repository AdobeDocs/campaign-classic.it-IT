---
solution: Campaign Classic
product: campaign
title: Configurazione dei campioni di popolazione
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 3%

---


# Configurazione dei campioni popolazione {#step-2--configuring-population-samples}

## Configurazione dell&#39;attività Query {#configuring-the-query-activity}

* Fate doppio clic sull&#39;attività **[!UICONTROL Query]**.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Fare clic sul collegamento **[!UICONTROL Edit query]** e selezionare i destinatari desiderati.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Collegate l&#39;attività **[!UICONTROL Query]** all&#39;attività **[!UICONTROL Split]**.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## Configurazione dell&#39;attività divisa {#configuring-the-split-activity}

Questa attività consente di creare diverse popolazioni: quella che riceve la consegna A, quella che riceve la consegna B, e la popolazione rimanente. Utilizzando la selezione casuale è possibile eseguire il targeting di una parte della popolazione di ciascuna consegna.

1. Creazione popolazione A:

   * Fate doppio clic sull&#39;attività **[!UICONTROL Split]**.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Nella scheda esistente, modificare l&#39;etichetta nella popolazione A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selezionare l&#39;opzione **[!UICONTROL Limit the selected records]**.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Fare clic sul collegamento **[!UICONTROL Edit]**, selezionare **[!UICONTROL Activate random sampling]**, quindi fare clic su **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Impostate la soglia su 10%, quindi fate clic su **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creazione popolazione B:

   * Fare clic su **[!UICONTROL Add]** per creare una nuova scheda per la popolazione B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limitare la popolazione al 10% come in precedenza.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creazione della popolazione rimanente:

   * Vai alla scheda **[!UICONTROL General]**. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Seleziona **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Modificate l&#39;etichetta per specificare che la popolazione non include né A né B, quindi fate clic su **[!UICONTROL OK]** per chiudere l&#39;attività.

      ![](assets/use_case_abtesting_createrecipients_013.png)
