---
solution: Campaign Classic
product: campaign
title: Gestione dei report
description: Gestione dei report
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---


# Gestione dei report{#managing-reports}

I report basati su uno schema specifico per i destinatari predefiniti  Adobe Campaign (nm:destinatario o schema collegato) devono essere risviluppati per tenere conto dei dati della tabella personalizzata e delle relative tabelle collegate tramite il mapping di destinazione (vedere la sezione [Mappatura destinazione](../../configuration/using/target-mapping.md)).

Per creare nuovi rapporti, fare riferimento a [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md).

In alcuni casi, è necessario anche mettere nuovi cubi specifici di queste tabelle. I cubi sono descritti in [questa sezione](../../reporting/using/about-cubes.md).

Si tratta delle seguenti relazioni:

* **[!UICONTROL Recent proposition tracking]** (RecentProposition): tracciamento delle proposte in tempo reale.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): si apre suddivisi in base al software dell&#39;utente.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analisi delle attività di condivisione, delle aperture e delle sottoscrizioni per periodo di tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicatori di tracciamento per una distribuzione su un’applicazione mobile.
* **[!UICONTROL Offer analysis]** (offerAnalysis): analisi delle offerte per data e canale.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasso di reattività per le ultime consegne.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): suddivisione delle sottoscrizioni attive per applicazione mobile.

