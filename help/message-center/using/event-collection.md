---
solution: Campaign Classic
product: campaign
title: Raccolta di eventi
description: Raccolta di eventi
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 5%

---


# Raccolta di eventi{#event-collection}

Gli eventi generati dal sistema di informazione possono essere raccolti utilizzando due modalità:

* Le chiamate ai metodi SOAP consentono di inviare gli eventi in  Adobe Campaign: il metodo PushEvent consente di inviare un evento alla volta, mentre il metodo PushEvents consente di inviarne diversi contemporaneamente. Fare riferimento alla descrizione [dell&#39;](../../message-center/using/event-description.md)evento.
* La creazione di un flusso di lavoro consente di recuperare gli eventi importando i file o tramite un gateway SQL (con l&#39;opzione **Federated Data Access** ).

Una volta raccolti, gli eventi vengono suddivisi, in base ai flussi di lavoro tecnici, tra le code in tempo reale e le code batch delle istanze di esecuzione, in attesa di essere collegati a un modello di messaggio.

![](assets/messagecenter_events_queues_001.png)
