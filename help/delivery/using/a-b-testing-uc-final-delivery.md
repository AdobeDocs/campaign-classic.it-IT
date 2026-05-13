---
product: campaign
title: Definire la consegna finale
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
TQID: https://experienceleague.adobe.com/P0oI4PhLZB-iBFDrEJ2Qy7eIOPYWSWYu5s6j3yCN6j0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 119
ht-degree: 5%

---

# Test AB: definire la consegna finale {#step-6--defining-the-final-delivery}

Una volta creato lo script per selezionare il vincitore del test A/B, puoi definire i parametri della consegna finale.

1. Connettere l&#39;attività **[!UICONTROL JavaScript code]** all&#39;attività **[!UICONTROL Delivery]** rimanente.
1. Apri l&#39;attività **[!UICONTROL Delivery]**.
1. Deseleziona l&#39;opzione **[!UICONTROL Generate an outbound transition]** per completare il flusso di lavoro con questa attività.
1. Lascia i valori predefiniti per le altre opzioni.

   ![](assets/ab_test_final_delivery.png)

Preparando la consegna specificata nella transizione (definita tramite l&#39;attività **[!UICONTROL Javascript Code]**), potrai approvarla e avviare l&#39;invio, come descritto nel passaggio successivo.

Ora puoi avviare il flusso di lavoro. [Ulteriori informazioni](a-b-testing-uc-start-workflow.md).
