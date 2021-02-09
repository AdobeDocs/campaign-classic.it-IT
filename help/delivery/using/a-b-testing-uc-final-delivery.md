---
solution: Campaign Classic
product: campaign
title: Definizione della consegna finale
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# Definizione della consegna finale {#step-6--defining-the-final-delivery}

Una volta creato lo script per selezionare il vincitore del test A/B, è possibile definire i parametri del recapito finale.

1. Collegare l&#39;attività **[!UICONTROL JavaScript code]** all&#39;attività **[!UICONTROL Delivery]** rimanente.
1. Aprite l&#39;attività **[!UICONTROL Delivery]**.
1. Deselezionate l&#39;opzione **[!UICONTROL Generate an outbound transition]** per completare il flusso di lavoro con questa attività.
1. Lasciate le altre opzioni ai valori predefiniti.

   ![](assets/ab_test_final_delivery.png)

Preparando la consegna specificata nella transizione (definita tramite l&#39;attività **[!UICONTROL Javascript Code]**), potrai quindi approvarla e avviare l&#39;invio, come descritto nel passaggio successivo.
