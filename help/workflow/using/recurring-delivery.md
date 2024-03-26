---
product: campaign
title: Consegna ricorrente
description: Ulteriori informazioni sull’attività del flusso di lavoro Consegna ricorrente
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: cfc38df8184a8f59d49ce27eb7875783e8941611
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 11%

---

# Consegna ricorrente{#recurring-delivery}

A **[!UICONTROL Recurring delivery]** attività consente di configurare un’occorrenza del modello di consegna specifica per una campagna.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#recurring-delivery-video)

Questa attività è disponibile solo da **[!UICONTROL Targeting and workflows]** scheda trovata in una campagna.

Per eseguire questa operazione:

1. Seleziona il modello di consegna su cui basare l’attività.

   ![](assets/recurring_delivery_001.png)

1. Configura il modello di consegna.

Il processo di configurazione per questa attività è simile a quello della creazione di un modello di consegna in termini di opzioni disponibili. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/about-templates.md).

>[!CAUTION]
>
>Le consegne ricorrenti non supportano l’anteprima del contenuto o l’invio di bozze, tra cui [dati di destinazione](../../workflow/using/data-life-cycle.md#target-data) elementi di personalizzazione.

Per un esempio di questa attività in uso, fai riferimento a questo [sezione](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Come impostare la consegna ricorrente {#set-up-recurring-delivery}

A **consegna ricorrente** creerà una nuova istanza di consegna ogni volta che viene eseguita. Ad esempio, se il flusso di lavoro è pianificato per essere eseguito una volta alla settimana, in un anno si otterranno 52 consegne. Ciò significa anche che i log ampi e quelli di tracciamento saranno separati per ogni istanza di consegna.

![Consegna ricorrente](assets/delivery_recurring.jpg)

Se desideri interrompere l’esecuzione di una consegna ricorrente, devi annullare completamente la campagna o interrompere l’esecuzione del flusso di lavoro. L’interruzione della consegna dal dashboard Campaign interrompe solo l’occorrenza della consegna: le istanze successive della consegna ricorrente continueranno a essere create a ogni esecuzione del flusso di lavoro.

>[!NOTE]
>
>Non è possibile inviare una bozza da un **[!UICONTROL Recurring delivery]** attività di tipo.
> 
>Per creare direttamente una consegna tramite un flusso di lavoro della campagna, utilizza le attività specifiche del canale preconfigurate (ad esempio **[!UICONTROL Recurring delivery]**).

## Video tutorial {#recurring-delivery-video}

Questo video spiega come configurare una consegna ricorrente e un’attività di pianificazione.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Sono disponibili altri video dimostrativi sui Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
