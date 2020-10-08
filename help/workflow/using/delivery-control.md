---
title: Controllo della consegna
seo-title: Controllo della consegna
description: Controllo della consegna
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 5%

---


# Controllo della consegna{#delivery-control}

Un&#39;azione di tipo controllo **** Consegna consente di avviare, mettere in pausa o interrompere una consegna.

Può trattarsi della consegna specificata nella transizione, di una consegna selezionata esplicitamente o di una consegna calcolata da uno script. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

Se selezionate **[!UICONTROL Start]**, l&#39;attività eseguirà tutti i passaggi necessari per avviare la consegna (calcolo target, preparazione contenuto, consegna). Se alcuni di questi passaggi sono già stati eseguiti da un&#39;attività di flusso di lavoro precedente, non verranno eseguiti di nuovo. Ad esempio, se la stima di destinazione è già stata eseguita da un&#39;attività di **[!UICONTROL Delivery]** tipo (fare riferimento a [Consegna](../../workflow/using/delivery.md)), l&#39; **[!UICONTROL Act on the delivery]** attività avvierà i passaggi rimanenti (preparazione e distribuzione dei contenuti).

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Generate an outbound transition]**

   Crea una transizione in uscita che verrà attivata al termine dell&#39;esecuzione. Potete scegliere se recuperare o meno la destinazione della consegna in uscita.

* **[!UICONTROL Processing errors]**

   Fare riferimento a Errori [di](../../workflow/using/monitoring-workflow-execution.md#processing-errors)elaborazione.

## Parametri di input {#input-parameters}

* deliveryId

Identificatore di consegna, se l&#39;azione selezionata è **[!UICONTROL Specified in the transition]**.
