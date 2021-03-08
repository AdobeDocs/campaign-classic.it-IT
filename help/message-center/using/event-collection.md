---
solution: Campaign Classic
product: campaign
title: Raccolta di eventi
description: Raccolta di eventi
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# Raccolta di eventi{#event-collection}

Gli eventi generati dal sistema di informazione possono essere raccolti utilizzando due modalità:

* Le chiamate ai metodi SOAP consentono di inviare eventi in push in Adobe Campaign: il metodo PushEvent consente di inviare un evento alla volta, il metodo PushEvents ne consente l&#39;invio di più contemporaneamente. Fare riferimento a [Descrizione evento](../../message-center/using/event-description.md).
* La creazione di un flusso di lavoro consente di recuperare gli eventi importando i file o tramite un gateway SQL (con l’opzione **Federated Data Access** ).

Una volta raccolti, gli eventi vengono suddivisi, per flussi di lavoro tecnici, tra le code in tempo reale e quelle batch delle istanze di esecuzione, in attesa di essere collegati a un modello di messaggio.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Nelle istanze di esecuzione, le cartelle **[!UICONTROL Real time events]** o **[!UICONTROL Batch events]** non devono essere impostate come visualizzazioni, in quanto ciò potrebbe causare problemi di accesso ai diritti. Per ulteriori informazioni sull&#39;impostazione di una cartella come visualizzazione, consulta [questa sezione](../../platform/using/access-management-folders.md).
