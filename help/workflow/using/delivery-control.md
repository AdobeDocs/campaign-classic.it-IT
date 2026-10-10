---
product: campaign
title: Controllo della consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro Controllo consegna
feature: Workflows
hide: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
TQID: 'https://experienceleague.adobe.com/WVXqtjcGQQOQJfVi58BqtLPqgG7AkgslAzQk4Vjbl9k'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%
---
# Controllo della consegna{#delivery-control}



Un&#39;azione di tipo **Controllo di consegna** consente di avviare, mettere in pausa o interrompere una consegna.

Può trattarsi della consegna specificata nella transizione, di una consegna selezionata esplicitamente o di una consegna calcolata da uno script. Per ulteriori informazioni, consulta [Consegna](delivery.md).

![](assets/edit_diffusion_act.png)

Se si seleziona **[!UICONTROL Start]**, l&#39;attività eseguirà tutti i passaggi necessari per avviare la consegna (calcolo del target, preparazione del contenuto, consegna). Se alcuni di questi passaggi sono già stati eseguiti da un’attività del flusso di lavoro precedente, non verranno eseguiti nuovamente. Ad esempio, se la stima di destinazione è già stata eseguita da un&#39;attività di tipo **[!UICONTROL Delivery]** (fare riferimento a [Consegna](delivery.md)), l&#39;attività di tipo **[!UICONTROL Act on the delivery]** avvierà i passaggi rimanenti (preparazione e consegna dei contenuti).

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Generate an outbound transition]**

  Crea una transizione in uscita che verrà attivata alla fine dell’esecuzione. Puoi scegliere se recuperare o meno la destinazione della consegna in uscita.

* **[!UICONTROL Processing errors]**

  Consulta [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Parametri di input {#input-parameters}

* deliveryId

Identificatore di consegna, se l&#39;azione selezionata è **[!UICONTROL Specified in the transition]**.
