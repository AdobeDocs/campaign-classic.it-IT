---
product: campaign
title: Condivisione di tipi di pubblico con Adobe Experience Cloud
description: Condivisione di tipi di pubblico con Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 4%

---

# Condivisione di tipi di pubblico con Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

![](../../assets/common.svg)

>[!CAUTION]
>
>Per condividere i tipi di pubblico con le soluzioni Adobe Experience Cloud, devi implementare Adobe Identity Management System. [Ulteriori informazioni su IMS](../../integrations/using/about-adobe-id.md).

Con Adobe Campaign puoi condividere tipi di pubblico e segmenti con le soluzioni e i servizi di base di Adobe Experience Cloud. Sono disponibili due opzioni:

1. Invia i dati dei segmenti Adobe Experience Platform ad Adobe Campaign. Per implementare questa integrazione, devi collegare il tuo Real-time Customer Data Platform a Campaign (RTCDP). [Ulteriori informazioni in questa sezione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).


1. Integrare **Adobe Campaign** con **Servizio core persone** (noto anche come **Servizio principale Profili e pubblico**) o Adobe Audience Manager. Potrai quindi:

   * Importa tipi di pubblico/segmenti condivisi da diverse soluzioni Adobe Experience Cloud in Adobe Campaign. I tipi di pubblico possono essere importati tramite elenchi in Adobe Campaign.

   * Esporta elenchi sotto forma di tipi di pubblico condivisi di Adobe Experience Cloud. Questi tipi di pubblico possono essere utilizzati nelle diverse soluzioni Adobe Experience Cloud che utilizzi. I tipi di pubblico possono essere esportati dopo il targeting in un flusso di lavoro, utilizzando un **[!UICONTROL Update shared audience]** attività.

Questa integrazione supporta due tipi di ID Adobe Experience Cloud:

* **ID visitatore**: questo tipo di identificatore concilia i visitatori di Adobe Experience Cloud con i destinatari di Adobe Campaign.
* **ID dichiarato**: questo tipo di identificatore riconcilia tutti i tipi di dati con gli elementi del database Adobe Campaign. È rappresentato in Adobe Campaign come chiave di riconciliazione predefinita.

   >[!NOTE]
   >
   > L’origine dati Declared ID (ID dichiarato) può ora essere utilizzata anche con l’integrazione del servizio core People.
   >
   >Se utilizzi l’integrazione del servizio core Persone e desideri aggiungere l’integrazione di Audience Manager, ti servirà l’aiuto di un consulente Adobe Audience Manager per evitare di perdere tutte le sincronizzazioni ID raccolte durante la transizione all’utilizzo di questa origine dati Declared ID in un contesto Adobe Audience Manager.
