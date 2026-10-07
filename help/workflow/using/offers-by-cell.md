---
product: campaign
title: Offerte per cella
description: Offerte per cella
feature: Workflows, Targeting Activity, Interaction
hide: true
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
TQID: 'https://experienceleague.adobe.com/ddCHWdqnyWjUtP3lcc3yIaUHffGkNCbnVKWiJVfhdjg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 7%
---
# Offerte per cella{#offers-by-cell}



L&#39;attività **[!UICONTROL Offers by cell]** consente di distribuire il gruppo in entrata (ad esempio da una query) in più segmenti e di specificare un&#39;offerta da presentare per ciascuno di questi segmenti.

Questa attività può essere utilizzata solo con **Interaction**. Per ulteriori informazioni, consulta questa [sezione](../../interaction/using/about-outbound-channels.md).

Per eseguire questa operazione:

1. Aggiungere l&#39;attività **[!UICONTROL Offers by cell]** dopo aver specificato la popolazione target, quindi aprirla.
1. Nella scheda **[!UICONTROL General]**, seleziona lo spazio dell&#39;offerta in cui desideri presentare le offerte.
1. Nella scheda **[!UICONTROL Cells]**, specifica i diversi sottoinsiemi utilizzando il pulsante **[!UICONTROL Add]**:

   * Specifica la popolazione del sottoinsieme utilizzando le regole di filtro e limitazione disponibili.
   * Quindi, seleziona l’offerta da presentare al sottoinsieme. Le offerte disponibili sono quelle idonee per lo spazio dell’offerta selezionato al passaggio precedente.

     ![](assets/int_offer_per_cell1.png)

1. Quindi configura un’attività di consegna che corrisponde al canale scelto. Consulta [Consegne cross-channel](cross-channel-deliveries.md).
