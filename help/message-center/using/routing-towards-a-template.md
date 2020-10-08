---
title: Instradamento verso un modello
seo-title: Instradamento verso un modello
description: Instradamento verso un modello
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 12%

---


# Instradamento verso un modello{#routing-towards-a-template}

Una volta pubblicato il modello di messaggio nelle istanze di esecuzione, vengono automaticamente generati due modelli da collegare a un evento in tempo reale o batch. La fase di routing consiste nel collegare un evento al modello di messaggio appropriato. Il collegamento si basa sul tipo di evento specificato nelle proprietà dell&#39;evento stesso e quelle del modello.

Definizione del tipo di evento nelle proprietà dell&#39;evento:

![](assets/messagecenter_event_type_001.png)

Definizione del tipo di evento nelle proprietà del modello di messaggio:

![](assets/messagecenter_event_type_002.png)

Per impostazione predefinita, il routing si basa sulle seguenti informazioni:

* il tipo di evento,
* il canale da utilizzare (per impostazione predefinita: email),
* il modello di consegna più recente, in base alla data di pubblicazione.

