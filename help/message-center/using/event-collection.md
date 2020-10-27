---
title: Raccolta di eventi
seo-title: Raccolta di eventi
description: Raccolta di eventi
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 7%

---


# Raccolta di eventi{#event-collection}

Gli eventi generati dal sistema di informazione possono essere raccolti utilizzando due modalità:

* Le chiamate ai metodi SOAP consentono di inviare gli eventi in  Adobe Campaign: il metodo PushEvent consente di inviare un evento alla volta, mentre il metodo PushEvents consente di inviarne diversi contemporaneamente. Fare riferimento alla descrizione [dell&#39;](../../message-center/using/event-description.md)evento.
* La creazione di un flusso di lavoro consente di recuperare gli eventi importando i file o tramite un gateway SQL (con l&#39;opzione **Federated Data Access** ).

Una volta raccolti, gli eventi vengono suddivisi, in base ai flussi di lavoro tecnici, tra le code in tempo reale e le code batch delle istanze di esecuzione, in attesa di essere collegati a un modello di messaggio.

![](assets/messagecenter_events_queues_001.png)
