---
title: Condivisione dei tipi di pubblico con Adobe Experience Cloud
seo-title: Condivisione dei tipi di pubblico con Adobe Experience Cloud
description: Condivisione dei tipi di pubblico con Adobe Experience Cloud
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 418a36cd51106dae2b4201c8b5abda9b05285a18

---


# Condivisione dei tipi di pubblico con Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>L&#39;utilizzo di questa integrazione richiede l&#39;implementazione di IMS. Consultate la sezione su [IMS](../../integrations/using/about-adobe-id.md).

Adobe Campaign consente di scambiare e condividere audience/segmenti con le soluzioni e i servizi di base di Adobe Experience Cloud. A tal fine, devi integrare **Adobe Campaign** con il servizio **di base** Persone (noto anche come servizio **di base** Profili e pubblico) o Adobe Audience Manager. Potrete quindi:

* Importa audience/segmenti condivisi da diverse soluzioni Adobe Experience Cloud in Adobe Campaign. Le audience possono essere importate tramite elenchi in Adobe Campaign.
* Esportare elenchi sotto forma di audience condivise di Adobe Experience Cloud. Queste audience possono essere utilizzate nelle diverse soluzioni Adobe Experience Cloud che utilizzi. Le audience possono essere esportate dopo il targeting in un flusso di lavoro, utilizzando un&#39;attività dedicata **[!UICONTROL Update shared audience]** .

>[!CAUTION]
>
>A seconda del tipo di dati, l&#39;importazione di audience in Adobe Campaign potrebbe essere soggetta a restrizioni legali.

L&#39;integrazione supporta due tipi di Adobe Experience Cloud ID:

* **ID** visitatore: questo tipo di identificatore riunisce i visitatori di Adobe Experience Cloud con i destinatari di Adobe Campaign.
* **ID** dichiarato: questo tipo di identificatore riunisce tutti i tipi di dati con gli elementi del database Adobe Campaign. È rappresentata in Adobe Campaign come chiave di riconciliazione predefinita.
