---
product: campaign
title: Condivisione di tipi di pubblico con Adobe Experience Cloud
description: Condivisione di tipi di pubblico con Adobe Experience Cloud
feature: Audiences
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
TQID: https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 253
ht-degree: 49%

---

# Condivisione di tipi di pubblico con Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Per condividere i tipi di pubblico con le soluzioni Adobe Experience Cloud, devi implementare Adobe Identity Management System. [Ulteriori informazioni su IMS](../../integrations/using/about-adobe-id.md).

Con Adobe Campaign puoi condividere audience e segmenti con i servizi Adobe Experience Cloud. Sono disponibili due opzioni:

1. Invia i dati dei segmenti di Adobe Experience Platform ad Adobe Campaign. Per implementare questa integrazione, devi collegare il tuo Real-Time Customer Data Platform a Campaign (RTCDP). [Per ulteriori informazioni, consulta questa sezione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=it){target="_blank"}.

1. Integra **Adobe Campaign** con **Experience Cloud Audiences** o **Adobe Audience Manager**. Potrai quindi:

   * Importare tipi di pubblico/segmenti condivisi da diverse soluzioni Adobe Experience Cloud in Adobe Campaign. I tipi di pubblico possono essere importati tramite elenchi in Adobe Campaign.

   * Esportare elenchi sotto forma di tipi di pubblico condivisi di Adobe Experience Cloud. Questi tipi di pubblico possono essere utilizzati nelle diverse soluzioni Adobe Experience Cloud che utilizzi. I tipi di pubblico possono essere esportati dopo il targeting in un flusso di lavoro, utilizzando un’attività **[!UICONTROL Update shared audience]**.

Questa integrazione supporta due tipi di ID Adobe Experience Cloud:

* **ID visitatore**: questo tipo di identificatore riconcilia i visitatori di Adobe Experience Cloud con i destinatari di Adobe Campaign.
* **ID dichiarato**: questo tipo di identificatore riconcilia tutti i tipi di dati con gli elementi del database Adobe Campaign. In Adobe Campaign è rappresentato come chiave di riconciliazione predefinita.

  >[!NOTE]
  >
  > L’origine dati Declared ID (ID dichiarato) può ora essere utilizzata anche con l’integrazione Experience Cloud Assets.
  >
