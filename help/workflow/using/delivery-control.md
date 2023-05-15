---
product: campaign
title: Controllo della consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro Controllo consegna
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---

# Controllo della consegna{#delivery-control}



A **Controllo della consegna** L’azione -type ti consente di avviare, mettere in pausa o interrompere una consegna.

Può trattarsi della consegna specificata nella transizione, di una consegna selezionata esplicitamente o di una consegna calcolata da uno script. Per ulteriori informazioni, consulta [Consegna](delivery.md).

![](assets/edit_diffusion_act.png)

Se si seleziona **[!UICONTROL Start]**, l’attività eseguirà tutti i passaggi necessari per avviare la consegna (calcolo del target, preparazione dei contenuti, consegna). Se alcuni di questi passaggi sono già stati eseguiti da un’attività di flusso di lavoro precedente, non verranno eseguiti di nuovo. Ad esempio, se la stima del target è già stata eseguita da un **[!UICONTROL Delivery]** attività del tipo (fare riferimento a [Consegna](delivery.md)), **[!UICONTROL Act on the delivery]** l’attività avvia i passaggi rimanenti (preparazione e distribuzione dei contenuti).

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Generate an outbound transition]**

   Crea una transizione in uscita che verrà attivata al termine dell’esecuzione. Puoi scegliere se recuperare o meno il target della consegna in uscita.

* **[!UICONTROL Processing errors]**

   Fai riferimento a [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Parametri di input {#input-parameters}

* deliveryId

Identificatore di consegna, se l’azione selezionata è **[!UICONTROL Specified in the transition]**.
