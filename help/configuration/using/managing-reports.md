---
product: campaign
title: Gestione dei rapporti
description: Gestione dei rapporti
feature: Reporting, Configuration
role: Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 3%

---

# Gestione dei rapporti{#managing-reports}



I rapporti basati su uno schema specifico per i destinatari Adobe Campaign predefiniti (nm:recipient o collegati a schema) devono essere risviluppati per tenere conto dei dati della tabella personalizzata e delle relative tabelle collegate tramite la mappatura di destinazione (vedi la sezione [Mappatura di destinazione](../../configuration/using/target-mapping.md)).

Per creare nuovi report, consultare [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md).

In alcuni casi, è inoltre necessario inserire nuovi cubi specifici per queste tabelle. I cubi sono descritti in [questa sezione](../../reporting/using/ac-cubes.md).

Sono interessate le seguenti relazioni:

* **[!UICONTROL Recent proposition tracking]** (recentiPropositions): tracciamento delle proposte in tempo reale.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): viene aperto suddiviso in base al software utente.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analisi delle attività di condivisione, aperture e abbonamenti per periodo di tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicatori di tracciamento per una consegna su un&#39;app mobile.
* **[!UICONTROL Offer analysis]** (offerAnalysis): analisi delle offerte per data e canale.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasso di reattività per le consegne più recenti.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): suddivisione degli abbonamenti attivi per app mobile.
