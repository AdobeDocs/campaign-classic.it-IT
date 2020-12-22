---
solution: Campaign Classic
product: campaign
title: Raccolta di eventi
description: Raccolta di eventi
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: d1130691e40c0cac183db37a4c0b410d00bb696a
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 4%

---


# Raccolta di eventi{#event-collection}

Gli eventi generati dal sistema di informazione possono essere raccolti utilizzando due modalità:

* Le chiamate ai metodi SOAP consentono di inviare gli eventi in  Adobe Campaign: il metodo PushEvent consente di inviare un evento alla volta, mentre il metodo PushEvents consente di inviarne diversi contemporaneamente. Fare riferimento a [Descrizione evento](../../message-center/using/event-description.md).
* La creazione di un flusso di lavoro consente di recuperare gli eventi importando i file o tramite un gateway SQL (con l&#39;opzione **Federated Data Access**).

Una volta raccolti, gli eventi vengono suddivisi, in base ai flussi di lavoro tecnici, tra le code in tempo reale e le code batch delle istanze di esecuzione, in attesa di essere collegati a un modello di messaggio.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Nelle istanze di esecuzione, le cartelle **[!UICONTROL Real time events]** o **[!UICONTROL Batch events]** non devono essere impostate come viste, in quanto ciò potrebbe causare problemi di accesso [right](../../platform/using/access-management.md#about-permissions). Per ulteriori informazioni sull&#39;impostazione di una cartella come visualizzazione, vedere [Informazioni sulle viste](../../platform/using/access-management.md#about-views).
