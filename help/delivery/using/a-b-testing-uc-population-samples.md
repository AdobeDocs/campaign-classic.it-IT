---
product: campaign
title: Configurare i campioni di popolazione
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato
feature: A/B Testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 7%

---

# Configurare i campioni di popolazione {#step-2--configuring-population-samples}

![](../../assets/common.svg)

## Configurare l’attività Query {#configuring-the-query-activity}

* Fai doppio clic sul pulsante **[!UICONTROL Query]** attività.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Fai clic sul pulsante **[!UICONTROL Edit query]** e seleziona i destinatari a cui desideri rivolgerti.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Collega **[!UICONTROL Query]** attività **[!UICONTROL Split]** attività.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## Configurare l’attività Split {#configuring-the-split-activity}

Questa attività ti consente di creare diverse popolazioni: quella che riceve la consegna A, quella che riceve la consegna B, e la popolazione rimanente. L’utilizzo di una selezione casuale consente di eseguire il targeting di solo una parte della popolazione di ciascuna consegna.

1. Creazione della popolazione A:

   * Fai doppio clic sul pulsante **[!UICONTROL Split]** attività.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Nella scheda esistente, modifica l’etichetta nel gruppo A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Seleziona la **[!UICONTROL Limit the selected records]** opzione .

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Fai clic sul pulsante **[!UICONTROL Edit]** collegamento, seleziona **[!UICONTROL Activate random sampling]** e fai clic su **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Imposta la soglia al 10%, quindi fai clic su **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creazione della popolazione B:

   * Fai clic su **[!UICONTROL Add]** per creare una nuova scheda per il gruppo B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limitare la popolazione al 10% come in precedenza.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creazione della popolazione rimanente:

   * Vai alla scheda **[!UICONTROL General]**. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Seleziona **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Modifica l’etichetta per specificare che la popolazione non include né A né B, quindi fai clic su **[!UICONTROL OK]** per chiudere l’attività.

      ![](assets/use_case_abtesting_createrecipients_013.png)

Ora puoi creare i due modelli di consegna. [Ulteriori informazioni](a-b-testing-uc-delivery-templates.md)).
