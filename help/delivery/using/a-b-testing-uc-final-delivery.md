---
product: campaign
title: Definizione della consegna finale
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 7%

---

# Definizione della consegna finale {#step-6--defining-the-final-delivery}

Una volta creato lo script per selezionare il vincitore del test A/B, puoi definire i parametri della consegna finale.

1. Collega l&#39;attività **[!UICONTROL JavaScript code]** all&#39;attività **[!UICONTROL Delivery]** rimanente.
1. Apri l’attività **[!UICONTROL Delivery]** .
1. Deseleziona l’opzione **[!UICONTROL Generate an outbound transition]** per completare il flusso di lavoro con questa attività.
1. Lascia i valori predefiniti delle altre opzioni.

   ![](assets/ab_test_final_delivery.png)

Preparando la consegna specificata nella transizione (definita tramite l’attività **[!UICONTROL Javascript Code]** ), potrai quindi approvarla e avviare l’invio, come descritto nel passaggio successivo.

Ora puoi avviare il flusso di lavoro (vedi [Passaggio 7: Avvia il flusso di lavoro](../../delivery/using/a-b-testing-uc-start-workflow.md)).
