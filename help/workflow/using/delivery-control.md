---
solution: Campaign Classic
product: campaign
title: Controllo della consegna
description: Scopri di più sull'attività del flusso di lavoro di controllo Consegna
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# Controllo della consegna{#delivery-control}

Un&#39;azione di tipo **Controllo consegna** consente di avviare, mettere in pausa o interrompere una consegna.

Può trattarsi della consegna specificata nella transizione, di una consegna selezionata esplicitamente o di una consegna calcolata da uno script. Per ulteriori informazioni, vedere [Consegna](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

Se selezionate **[!UICONTROL Start]**, l&#39;attività eseguirà tutti i passaggi necessari per avviare la consegna (calcolo target, preparazione contenuto, consegna). Se alcuni di questi passaggi sono già stati eseguiti da un&#39;attività di flusso di lavoro precedente, non verranno eseguiti di nuovo. Ad esempio, se la stima di destinazione è già stata eseguita da un&#39;attività di tipo **[!UICONTROL Delivery]** (fare riferimento a [Delivery](../../workflow/using/delivery.md)), l&#39;attività **[!UICONTROL Act on the delivery]** avvierà i passaggi rimanenti (preparazione e distribuzione dei contenuti).

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Generate an outbound transition]**

   Crea una transizione in uscita che verrà attivata al termine dell&#39;esecuzione. Potete scegliere se recuperare o meno la destinazione della consegna in uscita.

* **[!UICONTROL Processing errors]**

   Fare riferimento a [Errori di elaborazione](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parametri di input {#input-parameters}

* deliveryId

Identificatore di recapito, se l&#39;azione selezionata è **[!UICONTROL Specified in the transition]**.
