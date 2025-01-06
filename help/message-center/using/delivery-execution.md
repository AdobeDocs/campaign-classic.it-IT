---
product: campaign
title: Esecuzione della consegna
description: Ulteriori informazioni sull’esecuzione e il monitoraggio della consegna dei messaggi transazionali
feature: Transactional Messaging, Message Center, Monitoring
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 930c6395-0c00-40ee-a925-3e0cae67c55f
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 1%

---

# Esecuzione della consegna {#delivery-execution}



## Invio di messaggi transazionali {#transactional-message-send}

Nell’istanza di esecuzione, una volta completata la fase di arricchimento e dopo aver collegato un modello di consegna all’evento, la consegna viene inviata.

>[!NOTE]
>
>L’MTA dà priorità all’elaborazione dei messaggi transazionali rispetto a qualsiasi altra consegna.

Tutte le consegne sono raggruppate nella cartella **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Per impostazione predefinita, sono ordinate in sottocartelle per mese di consegna. Questo ordinamento può essere modificato nelle proprietà del modello di messaggio, come illustrato di seguito.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Per le installazioni in hosting o ibride, se hai eseguito l&#39;aggiornamento all&#39;[MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), tutti i messaggi transazionali possono essere inviati anche con l&#39;MTA avanzato di Adobe Campaign per migliorare il recapito messaggi, la velocità effettiva e la gestione dei messaggi non recapitati. Tutti gli impatti sono gli stessi dei messaggi di marketing standard.

## Monitoraggio dei messaggi transazionali {#transactional-message-monitoring}

Per monitorare i messaggi transazionali, controlla i [registri di consegna](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

Le consegne transazionali inviate dall&#39;istanza di esecuzione vengono sincronizzate con l&#39;istanza di controllo tramite un flusso di lavoro tecnico (**[!UICONTROL Message Center execution instance]**) che viene eseguito ogni ora.

>[!NOTE]
>
>Le consegne settimanali accumulano gli eventi in base all’ultimo aggiornamento dell’evento e non alla data di creazione dell’evento. Pertanto, durante l’estrazione dei registri di consegna della messaggistica transazionale dall’istanza di controllo, l’ID di consegna associato a ciascun ID del registro di consegna può cambiare nel tempo man mano che il registro viene aggiornato (ad esempio, quando viene ricevuto un mancato recapito in entrata per l’evento).

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->

Per monitorare l&#39;attività e l&#39;esecuzione delle istanze di esecuzione, vedere [Rapporti sulla messaggistica transazionale](../../message-center/using/about-transactional-messaging-reports.md).
