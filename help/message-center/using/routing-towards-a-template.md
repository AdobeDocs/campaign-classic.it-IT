---
solution: Campaign Classic
product: campaign
title: Instradamento verso un modello
description: Instradamento verso un modello
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 9%

---


# Instradamento verso un modello{#routing-towards-a-template}

Una volta pubblicato il modello di messaggio nelle istanze di esecuzione, vengono automaticamente generati due modelli da collegare a un evento in tempo reale o batch. La fase di routing consiste nel collegare un evento al modello di messaggio appropriato. Il collegamento si basa sul tipo di evento specificato nelle proprietà dell&#39;evento stesso e quelle del modello.

Definizione del tipo di evento nelle proprietà dell&#39;evento:

![](assets/messagecenter_event_type_001.png)

Definizione del tipo di evento nelle proprietà del modello di messaggio:

![](assets/messagecenter_event_type_002.png)

Per impostazione predefinita, il routing si basa sulle seguenti informazioni:

* Il tipo di evento
* Canale da utilizzare (per impostazione predefinita: email)
* Modello di consegna più recente, in base alla data di pubblicazione
