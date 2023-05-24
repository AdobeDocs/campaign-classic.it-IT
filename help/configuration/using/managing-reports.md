---
product: campaign
title: Gestione dei rapporti
description: Gestione dei rapporti
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# Gestione dei rapporti{#managing-reports}



I rapporti basati su uno schema specifico per i destinatari predefiniti di Adobe Campaign (nm:recipient o schema linked) devono essere risviluppati per tenere conto dei dati della tabella personalizzata e delle sue tabelle collegate tramite la mappatura di destinazione (vedi [Mappatura target](../../configuration/using/target-mapping.md) sezione ).

Per creare nuovi rapporti, consulta [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md).

In alcuni casi, è inoltre necessario inserire nuovi cubi specifici per queste tabelle. I cubi sono descritti in [questa sezione](../../reporting/using/ac-cubes.md).

Sono interessate le seguenti relazioni:

* **[!UICONTROL Recent proposition tracking]** (recentiPropositions): tracciamento delle proposte in tempo reale.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): apre suddivisi in base al software dell’utente.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analisi delle attività di condivisione, aperture e abbonamenti per periodo di tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicatori di tracciamento per una consegna su un’app mobile.
* **[!UICONTROL Offer analysis]** (offerAnalysis): analisi delle offerte per data e canale.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasso di reattività per le consegne più recenti.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): suddivisione degli abbonamenti attivi per app mobile.
