---
product: campaign
title: Definire la consegna finale
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 5%

---

# Test AB: definire la consegna finale {#step-6--defining-the-final-delivery}

Una volta creato lo script per selezionare il vincitore del test A/B, puoi definire i parametri della consegna finale.

1. Connetti **[!UICONTROL JavaScript code]** attività al resto **[!UICONTROL Delivery]** attività.
1. Apri **[!UICONTROL Delivery]** attività.
1. Deseleziona la **[!UICONTROL Generate an outbound transition]** per completare il flusso di lavoro con questa attività.
1. Lascia i valori predefiniti per le altre opzioni.

   ![](assets/ab_test_final_delivery.png)

Preparando la consegna specificata nella transizione (definita tramite il **[!UICONTROL Javascript Code]** attività), potrai quindi approvarlo e avviare l’invio, come descritto nel passaggio successivo.

Ora puoi avviare il flusso di lavoro. [Ulteriori informazioni](a-b-testing-uc-start-workflow.md).
