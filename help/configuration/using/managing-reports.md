---
product: campaign
title: Gestione dei rapporti
description: Gestione dei rapporti
feature: Reporting, Configuration
role: Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
TQID: https://experienceleague.adobe.com/LA4v5oODC9n5K2Ttox9SF7lwcGQOU7IDEvL1P4Sls-4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 154
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
