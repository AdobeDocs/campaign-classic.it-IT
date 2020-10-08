---
title: Gestione dei report
seo-title: Gestione dei report
description: Gestione dei report
seo-description: null
page-status-flag: never-activated
uuid: 3b8e6f11-4cbd-450e-871b-50fd0ead96db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 21777423-0c8a-4bb1-b210-972f660648bd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 5%

---


# Gestione dei report{#managing-reports}

I report basati su uno schema specifico per i destinatari predefiniti  Adobe Campaign (nm:destinatario o schema collegati) devono essere risviluppati per tenere conto dei dati della tabella personalizzata e delle relative tabelle collegate tramite il mapping di destinazione (vedere la sezione Mappatura [di](../../configuration/using/target-mapping.md) Target).

Per creare nuovi rapporti, consulta [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md).

In alcuni casi, è necessario anche mettere nuovi cubi specifici di queste tabelle. I cubetti sono descritti in [questa sezione](../../reporting/using/about-cubes.md).

Si tratta delle seguenti relazioni:

* **[!UICONTROL Recent proposition tracking]** (RecentProposition): tracciamento delle proposte in tempo reale.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): si apre suddivisi in base al software dell&#39;utente.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analisi delle attività di condivisione, delle aperture e delle sottoscrizioni per periodo di tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicatori di tracciamento per una distribuzione su un’applicazione mobile.
* **[!UICONTROL Offer analysis]** (offerAnalysis): analisi delle offerte per data e canale.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasso di reattività per le ultime consegne.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): suddivisione delle sottoscrizioni attive per applicazione mobile.

