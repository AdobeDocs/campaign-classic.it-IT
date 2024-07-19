---
product: campaign
title: Configurare i campioni di popolazione
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 4%

---

# Test AB: configurare i campioni di popolazione {#step-2--configuring-population-samples}

## Configurare l’attività Query {#configuring-the-query-activity}

* Fare doppio clic sull&#39;attività **[!UICONTROL Query]**.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Fai clic sul collegamento **[!UICONTROL Edit query]** e seleziona i destinatari di cui desideri eseguire il targeting.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Collega l&#39;attività **[!UICONTROL Query]** all&#39;attività **[!UICONTROL Split]**.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Configurare l’attività Dividi {#configuring-the-split-activity}

Questa attività ti consente di creare diverse popolazioni: quella che riceve la consegna A, quella che riceve la consegna B e la popolazione rimanente. L’utilizzo della selezione casuale consente di eseguire il targeting di solo una parte della popolazione di ogni consegna.

1. Creazione della popolazione A:

   * Fare doppio clic sull&#39;attività **[!UICONTROL Split]**.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * Nella scheda esistente, modifica l’etichetta in popolazione A.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selezionare l&#39;opzione **[!UICONTROL Limit the selected records]**.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * Fare clic sul collegamento **[!UICONTROL Edit]**, selezionare **[!UICONTROL Activate random sampling]** e fare clic su **[!UICONTROL Next]**.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * Impostare la soglia su 10%, quindi fare clic su **[!UICONTROL Finish]**.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creazione della popolazione B:

   * Fare clic su **[!UICONTROL Add]** per creare una nuova scheda per la popolazione B.

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limita la popolazione al 10% come in precedenza.

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creazione della popolazione rimanente:

   * Passa alla scheda **[!UICONTROL General]**.

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * Seleziona **[!UICONTROL Generate complement]**.

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * Modificare l&#39;etichetta per specificare che il gruppo non include né A né B e fare clic su **[!UICONTROL OK]** per chiudere l&#39;attività.

     ![](assets/use_case_abtesting_createrecipients_013.png)

Ora puoi creare i due modelli di consegna. [Ulteriori informazioni](a-b-testing-uc-delivery-templates.md)).
