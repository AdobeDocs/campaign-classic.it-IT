---
product: campaign
title: Configurare i campioni di popolazione
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 6%

---

# Test AB: configurare i campioni di popolazione {#step-2--configuring-population-samples}

## Configurare l’attività Query {#configuring-the-query-activity}

* Fai doppio clic su **[!UICONTROL Query]** attività.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Fai clic su **[!UICONTROL Edit query]** e seleziona i destinatari di cui desideri eseguire il targeting.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Collega **[!UICONTROL Query]** attività al **[!UICONTROL Split]** attività.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Configurare l’attività Split {#configuring-the-split-activity}

Questa attività ti consente di creare diverse popolazioni: quella che riceve la consegna A, quella che riceve la consegna B e la popolazione rimanente. L’utilizzo della selezione casuale consente di eseguire il targeting di solo una parte della popolazione di ogni consegna.

1. Creazione della popolazione A:

   * Fai doppio clic su **[!UICONTROL Split]** attività.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * Nella scheda esistente, modifica l’etichetta in popolazione A.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * Seleziona la **[!UICONTROL Limit the selected records]** opzione.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * Fai clic su **[!UICONTROL Edit]** link, seleziona **[!UICONTROL Activate random sampling]** e fai clic su **[!UICONTROL Next]**.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * Imposta la soglia su 10%, quindi fai clic su **[!UICONTROL Finish]**.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creazione della popolazione B:

   * Clic **[!UICONTROL Add]** per creare una nuova scheda per la popolazione B.

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limita la popolazione al 10% come in precedenza.

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creazione della popolazione rimanente:

   * Vai alla scheda **[!UICONTROL General]**. 

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * Seleziona **[!UICONTROL Generate complement]**.

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * Modifica l’etichetta per specificare che questa popolazione non include né A né B e fai clic su **[!UICONTROL OK]** per chiudere l&#39;attività.

     ![](assets/use_case_abtesting_createrecipients_013.png)

Ora puoi creare i due modelli di consegna. [Ulteriori informazioni](a-b-testing-uc-delivery-templates.md)).
