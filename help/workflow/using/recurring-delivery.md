---
title: Consegna ricorrente
seo-title: Consegna ricorrente
description: Consegna ricorrente
seo-description: null
page-status-flag: never-activated
uuid: 715855df-fe29-46e8-a7ab-d534f010a26e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 185d3256-a21e-47d7-bee7-7b91762ca1e2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 9%

---


# Consegna ricorrente{#recurring-delivery}

Un&#39; **[!UICONTROL Recurring delivery]** attività consente di configurare un&#39;occorrenza del modello di consegna specifica per una campagna.

Questa attività è disponibile solo dalla **[!UICONTROL Targeting and workflows]** scheda trovata in una campagna.

Per eseguire questa operazione:

1. Selezionate il modello di consegna su cui verrà basata l&#39;attività.

   ![](assets/recurring_delivery_001.png)

1. Configurare il modello di consegna.

Il processo di configurazione per questa attività è simile a quello della creazione di un modello di consegna in termini di opzioni disponibili. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/about-templates.md).

Per un esempio dell&#39;attività in uso, consultate questa [sezione](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Come impostare la consegna ricorrente

Una consegna **** periodica crea una nuova istanza di consegna ogni volta che viene eseguita. Ad esempio, se il flusso di lavoro è pianificato per essere eseguito una volta alla settimana, il risultato sarà 52 Consegne dopo un anno. Ciò significa anche che i log di registro e di monitoraggio ampi saranno separati da ogni istanza di consegna.

![Consegna ricorrente](assets/delivery_recurring.jpg)

In questo video viene illustrato come configurare un&#39;attività di consegna periodica e un&#39;attività di pianificazione.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>Non è possibile inviare una prova da un&#39;attività di **[!UICONTROL Recurring delivery]** tipo.\
>Per creare direttamente una consegna tramite un flusso di lavoro della campagna, utilizzate le attività specifiche del canale preconfigurate (ad es. **[!UICONTROL Email delivery]**).
