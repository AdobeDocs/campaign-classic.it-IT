---
product: campaign
title: Consegna ricorrente
description: Ulteriori informazioni sull’attività del flusso di lavoro di consegna ricorrente
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---

# Consegna ricorrente{#recurring-delivery}

Un’attività **[!UICONTROL Recurring delivery]** ti consente di configurare un’occorrenza del modello di consegna specifica per una campagna.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#recurring-delivery-video)

Questa attività è disponibile solo dalla scheda **[!UICONTROL Targeting and workflows]** presente in una campagna.

Per eseguire questa operazione:

1. Seleziona il modello di consegna su cui verrà basata l’attività.

   ![](assets/recurring_delivery_001.png)

1. Configura il modello di consegna.

Il processo di configurazione per questa attività è simile a quello di creazione di un modello di consegna in termini di opzioni disponibili. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/about-templates.md).

Per un esempio di utilizzo di questa attività, consulta questa [sezione](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Come impostare una consegna ricorrente

Una **consegna ricorrente** creerà una nuova istanza di consegna ogni volta che viene eseguita. Ad esempio, se il flusso di lavoro è pianificato per essere eseguito una volta alla settimana, si otterranno 52 consegne dopo un anno. Ciò significa anche che i registri di registro e di tracciamento ampi saranno separati da ogni istanza di consegna.

![Consegna ricorrente](assets/delivery_recurring.jpg)

>[!NOTE]
>
>Non è possibile inviare una bozza da un&#39;attività di tipo **[!UICONTROL Recurring delivery]**.\
>Per creare direttamente una consegna tramite un flusso di lavoro della campagna, utilizza le attività specifiche del canale preconfigurate (ad esempio **[!UICONTROL Email delivery]**).

## Video tutorial (#ricorrenti-delivery-video)

Questo video spiega come configurare una consegna ricorrente e un’attività di pianificazione.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
