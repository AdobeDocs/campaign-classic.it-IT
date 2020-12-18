---
solution: Campaign Classic
product: campaign
title: Condivisione di tipi di pubblico con Adobe Experience Cloud
description: Condivisione di tipi di pubblico con Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Condivisione di tipi di pubblico con Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Per condividere i tipi di pubblico con le soluzioni Adobe Experience Cloud, è necessario implementare  Adobe  Identity Management System. [Ulteriori informazioni su IMS](../../integrations/using/about-adobe-id.md).

Con  Adobe Campaign, puoi condividere audience e segmenti con le soluzioni e i servizi di base di Adobe Experience Cloud. Sono disponibili due opzioni:

1. Invia i dati dei segmenti Adobe Experience Platform a  Adobe Campaign. Per implementare questa integrazione, devi collegare la tua piattaforma dati cliente in tempo reale a Campaign (RTCDP). [Ulteriori informazioni in questa sezione](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrare **Adobe Campaign** con **Servizio di base Persone** (noto anche come **Servizio di base Profili e pubblico**) o Adobe Audience Manager. Potrete quindi:

   * Importa audience/segmenti condivisi da diverse soluzioni Adobe Experience Cloud in  Adobe Campaign. Le audience possono essere importate tramite elenchi in  Adobe Campaign.

   * Esportare gli elenchi sotto forma di audience condivise Adobe Experience Cloud. Queste audience possono essere utilizzate nelle diverse soluzioni Adobe Experience Cloud che utilizzate. Le audience possono essere esportate dopo il targeting in un flusso di lavoro, utilizzando un&#39;attività **[!UICONTROL Update shared audience]** dedicata.

Questa integrazione supporta due tipi di ID Adobe Experience Cloud:

* **ID** visitatore: questo tipo di identificatore riunisce i visitatori di Adobe Experience Cloud con  destinatari Adobe Campaign.
* **ID** dichiarato: questo tipo di identificatore riunisce tutti i tipi di dati con gli elementi del database Adobe Campaign . È rappresentata in  Adobe Campaign come chiave di riconciliazione predefinita.
