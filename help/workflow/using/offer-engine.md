---
product: campaign
title: Motore di offerta
description: Motore di offerta
feature: Workflows, Interaction
hide: true
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
TQID: 'https://experienceleague.adobe.com/oAzSAhtWhfJTWcWowjaewtlVucahY839933SaCQZO10'
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
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 4%
---
# Motore di offerta{#offer-engine}



L&#39;attività **[!UICONTROL Offer engine]** ti consente di definire una chiamata al motore di offerta prima di una consegna.

Questa attività funziona sullo stesso principio dell’attività di arricchimento con una chiamata al motore, arricchendo i dati della popolazione in entrata con un’offerta calcolata dal motore, prima di una consegna.

![](assets/int_offerengine_activity2.png)

Dopo aver configurato la query (consulta questa [sezione](query.md)):

1. Aggiungi e apri un&#39;attività **[!UICONTROL Offer engine]**.
1. Completa i vari campi disponibili per specificare i parametri del motore di offerta della chiamata (spazio dell’offerta, categoria o temi, data di contatto, numero di offerte da mantenere). Il motore calcola automaticamente le offerte da aggiungere in base a questi parametri.

   >[!CAUTION]
   >
   >Se utilizzi questa attività, verranno memorizzate solo le proposte di offerta utilizzate nella consegna.

   ![](assets/int_offerengine_activity1.png)

1. Quindi configura un’attività di consegna che corrisponde al canale scelto. Consulta [Consegne cross-channel](cross-channel-deliveries.md).
