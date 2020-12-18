---
solution: Campaign Classic
product: campaign
title: Consegna ricorrente
description: Ulteriori informazioni sull'attività del flusso di lavoro di distribuzione ricorrente
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---


# Consegna ricorrente{#recurring-delivery}

Un&#39;attività **[!UICONTROL Recurring delivery]** consente di configurare un&#39;occorrenza del modello di consegna specifica per una campagna.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#recurring-delivery-video)

Questa attività è disponibile solo dalla scheda **[!UICONTROL Targeting and workflows]** presente in una campagna.

Per eseguire questa operazione:

1. Selezionate il modello di consegna su cui verrà basata l&#39;attività.

   ![](assets/recurring_delivery_001.png)

1. Configurare il modello di consegna.

Il processo di configurazione per questa attività è simile a quello della creazione di un modello di consegna in termini di opzioni disponibili. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/about-templates.md).

Per un esempio dell&#39;attività in uso, fare riferimento a questa sezione [](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Come impostare la consegna ricorrente

Una **consegna ricorrente** creerà una nuova istanza di consegna ogni volta che viene eseguita. Ad esempio, se il flusso di lavoro è pianificato per essere eseguito una volta alla settimana, il risultato sarà 52 Consegne dopo un anno. Ciò significa anche che i log di registro e di monitoraggio ampi saranno separati da ogni istanza di consegna.

![Consegna ricorrente](assets/delivery_recurring.jpg)

>[!NOTE]
>
>Non è possibile inviare una prova da un&#39;attività di tipo **[!UICONTROL Recurring delivery]**.\
>Per creare direttamente una consegna tramite un flusso di lavoro della campagna, utilizzate le attività specifiche del canale preconfigurate (ad es. **[!UICONTROL Email delivery]**).

## Video di esercitazione (#periodico-delivery-video)

In questo video viene illustrato come configurare un&#39;attività di consegna periodica e un&#39;attività di pianificazione.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).

