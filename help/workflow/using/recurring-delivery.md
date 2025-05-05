---
product: campaign
title: Consegna ricorrente
description: Ulteriori informazioni sull’attività del flusso di lavoro Consegna ricorrente
feature: Workflows
hide: true
hidefromtoc: true
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 11%

---

# Consegna ricorrente{#recurring-delivery}

Un&#39;attività **[!UICONTROL Recurring delivery]** consente di configurare un&#39;occorrenza del modello di consegna specifica per una campagna.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#recurring-delivery-video)

Questa attività è disponibile solo dalla scheda **[!UICONTROL Targeting and workflows]** trovata in una campagna.

Per eseguire questa operazione:

1. Seleziona il modello di consegna su cui basare l’attività.

   ![](assets/recurring_delivery_001.png)

1. Configura il modello di consegna.

Il processo di configurazione per questa attività è simile a quello della creazione di un modello di consegna in termini di opzioni disponibili. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/about-templates.md).

>[!CAUTION]
>
>Le consegne ricorrenti non supportano l&#39;anteprima del contenuto o l&#39;invio di bozze contenenti [dati di destinazione](../../workflow/using/data-life-cycle.md#target-data) elementi di personalizzazione.

Per un esempio di questa attività in uso, fai riferimento a questa [sezione](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Come impostare la consegna ricorrente {#set-up-recurring-delivery}

Una **consegna ricorrente** creerà una nuova istanza di consegna ogni volta che viene eseguita. Ad esempio, se il flusso di lavoro è pianificato per essere eseguito una volta alla settimana, in un anno si otterranno 52 consegne. Ciò significa anche che i log ampi e quelli di tracciamento saranno separati per ogni istanza di consegna.

![Consegna ricorrente](assets/delivery_recurring.jpg)

Se desideri interrompere l’esecuzione di una consegna ricorrente, devi annullare completamente la campagna o interrompere l’esecuzione del flusso di lavoro. L’interruzione della consegna dal dashboard Campaign interrompe solo l’occorrenza della consegna: le istanze successive della consegna ricorrente continueranno a essere create a ogni esecuzione del flusso di lavoro.

>[!NOTE]
>
>Impossibile inviare una bozza da un&#39;attività di tipo **[!UICONTROL Recurring delivery]**.
> 
>Per creare direttamente una consegna tramite un flusso di lavoro della campagna, utilizza le attività specifiche del canale preconfigurate (ad esempio **[!UICONTROL Recurring delivery]**).

## Video tutorial {#recurring-delivery-video}

Questo video spiega come configurare una consegna ricorrente e un’attività di pianificazione.

>[!VIDEO](https://video.tv.adobe.com/v/27506?quality=12&captions=ita)

Ulteriori video dimostrativi di Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
