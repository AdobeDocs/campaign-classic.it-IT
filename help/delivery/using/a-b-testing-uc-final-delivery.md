---
product: campaign
title: Definire la consegna finale
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato
feature: A/B Testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 9%

---

# Definire la consegna finale {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

Una volta creato lo script per selezionare il vincitore del test A/B, puoi definire i parametri della consegna finale.

1. Collega **[!UICONTROL JavaScript code]** attività per gli altri **[!UICONTROL Delivery]** attività.
1. Apri **[!UICONTROL Delivery]** attività.
1. Deseleziona **[!UICONTROL Generate an outbound transition]** per completare il flusso di lavoro con questa attività.
1. Lascia i valori predefiniti delle altre opzioni.

   ![](assets/ab_test_final_delivery.png)

Preparando la consegna specificata nella transizione (definita tramite il **[!UICONTROL Javascript Code]** attività), potrai quindi approvarla e avviare l’invio, come descritto nel passaggio successivo.

Ora puoi avviare il flusso di lavoro. [Ulteriori informazioni](a-b-testing-uc-start-workflow.md).
