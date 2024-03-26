---
product: campaign
title: Introduzione alla personalizzazione
description: Scopri come personalizzare i messaggi e utilizzare il contenuto condizionale in Campaign
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 40%

---

# Introduzione alla personalizzazione{#about-personalization}

Il contenuto e l’aspetto dei messaggi consegnati da Adobe Campaign possono essere personalizzati in diversi modi. Tali modi possono essere combinati in base a criteri ottenuti in modo particolare dai profili dei destinatari. Per le consegne e-mail, puoi definire gli elementi e le condizioni di personalizzazione di una consegna direttamente in JavaScript da **[!UICONTROL Source]** del messaggio. In generale, Adobe Campaign ti consente di:

* Personalizzare il formato del messaggio. Consulta [Contenuto del messaggio](defining-the-email-content.md#message-content).
* Inserire campi di personalizzazione dinamici. Consulta [Campi di personalizzazione](personalization-fields.md).
* Inserire blocchi di personalizzazione predefiniti. Consulta [Blocchi di personalizzazione](personalization-blocks.md).
* Creare contenuto condizionale. Consulta la sezione [Contenuto condizionale](conditional-content.md) sezione.

>[!CAUTION]
>
>Le seguenti variabili sono variabili interne che possono essere utilizzate per la personalizzazione ma non devono essere modificate: **consegna**, **messaggio**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposta**.
