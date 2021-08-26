---
product: campaign
title: Controllo della consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro Controllo consegna
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---

# Controllo della consegna{#delivery-control}

![](../../assets/common.svg)

Un&#39;azione di tipo **Controllo consegna** consente di avviare, mettere in pausa o interrompere una consegna.

Può trattarsi della consegna specificata nella transizione, di una consegna selezionata esplicitamente o di una consegna calcolata da uno script. Per ulteriori informazioni, consulta [Consegna](delivery.md).

![](assets/edit_diffusion_act.png)

Se selezioni **[!UICONTROL Start]**, l’attività eseguirà tutti i passaggi necessari per avviare la consegna (calcolo di destinazione, preparazione dei contenuti, consegna). Se alcuni di questi passaggi sono già stati eseguiti da un’attività di flusso di lavoro precedente, non verranno eseguiti di nuovo. Ad esempio, se la stima del target è già stata eseguita da un’attività di tipo **[!UICONTROL Delivery]** (consulta [Consegna](delivery.md)), l’attività **[!UICONTROL Act on the delivery]** avvierà i passaggi rimanenti (preparazione e consegna dei contenuti).

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Generate an outbound transition]**

   Crea una transizione in uscita che verrà attivata al termine dell’esecuzione. Puoi scegliere se recuperare o meno il target della consegna in uscita.

* **[!UICONTROL Processing errors]**

   Fare riferimento a [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Parametri di input {#input-parameters}

* deliveryId

Identificatore di consegna, se l&#39;azione selezionata è **[!UICONTROL Specified in the transition]**.
