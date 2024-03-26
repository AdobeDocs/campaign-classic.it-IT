---
product: campaign
title: Condivisione di tipi di pubblico con Adobe Experience Cloud
description: Condivisione di tipi di pubblico con Adobe Experience Cloud
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 62%

---

# Condivisione di tipi di pubblico con Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}



>[!CAUTION]
>
>Per condividere i tipi di pubblico con le soluzioni Adobe Experience Cloud, devi implementare Adobe Identity Management System. [Ulteriori informazioni su IMS](../../integrations/using/about-adobe-id.md).

Con Adobe Campaign puoi condividere audience e segmenti con le soluzioni e i servizi di base di Adobe Experience Cloud. Sono disponibili due opzioni:

1. Invia i dati dei segmenti di Adobe Experience Platform ad Adobe Campaign. Per implementare questa integrazione, devi collegare il tuo Real-time Customer Data Platform a Campaign (RTCDP). [Per ulteriori informazioni, consulta questa sezione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

1. Integrare **Adobe Campaign** con **Servizio core People** (noto anche come **Servizio core Profili e pubblico**) o Adobe Audience Manager. Potrai quindi:

   * Importare tipi di pubblico/segmenti condivisi da diverse soluzioni Adobe Experience Cloud in Adobe Campaign. I tipi di pubblico possono essere importati tramite elenchi in Adobe Campaign.

   * Esportare elenchi sotto forma di tipi di pubblico condivisi di Adobe Experience Cloud. Questi tipi di pubblico possono essere utilizzati nelle diverse soluzioni Adobe Experience Cloud che utilizzi. I tipi di pubblico possono essere esportati dopo il targeting in un flusso di lavoro, utilizzando un’attività **[!UICONTROL Update shared audience]**.

Questa integrazione supporta due tipi di ID Adobe Experience Cloud:

* **ID visitatore**: questo tipo di identificatore riconcilia i visitatori di Adobe Experience Cloud con i destinatari di Adobe Campaign.
* **ID dichiarato**: questo tipo di identificatore riconcilia tutti i tipi di dati con gli elementi del database Adobe Campaign. In Adobe Campaign è rappresentato come chiave di riconciliazione predefinita.

  >[!NOTE]
  >
  > L’origine dati ID dichiarato ora piò essere utilizzata anche con l’integrazione del servizio core People.
  >
  >Se utilizzi l’integrazione con il servizio core People e desideri aggiungere l’integrazione con Audience Manager, ti servirà l’aiuto di un consulente Adobe Audience Manager per evitare di perdere tutte le sincronizzazioni ID raccolte durante la transizione all’utilizzo dell’origine dati ID dichiarato in un contesto Adobe Audience Manager.
