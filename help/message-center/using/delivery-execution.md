---
product: campaign
title: Esecuzione della consegna
description: Ulteriori informazioni sull’esecuzione e il monitoraggio della consegna dei messaggi transazionali
feature: Transactional Messaging, Message Center, Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 930c6395-0c00-40ee-a925-3e0cae67c55f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 4%

---

# Esecuzione della consegna {#delivery-execution}



## Invio di messaggi transazionali {#transactional-message-send}

Nell’istanza di esecuzione, una volta completata la fase di arricchimento e dopo aver collegato un modello di consegna all’evento, la consegna viene inviata.

>[!NOTE]
>
>L’MTA dà priorità all’elaborazione dei messaggi transazionali rispetto a qualsiasi altra consegna.

Tutte le consegne sono raggruppate in **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** cartella.

![](assets/messagecenter_deliveries_execinstances_001.png)

Per impostazione predefinita, sono ordinate in sottocartelle per mese di consegna. Questo ordinamento può essere modificato nelle proprietà del modello di messaggio, come illustrato di seguito.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), tutti i messaggi transazionali possono essere inviati anche con l’MTA avanzato di Adobe Campaign per migliorare il recapito messaggi, la velocità effettiva e la gestione delle e-mail non consegnate. Tutti gli impatti sono gli stessi dei messaggi di marketing standard.

## Monitoraggio dei messaggi transazionali {#transactional-message-monitoring}

Per monitorare i messaggi transazionali, seleziona la [registri di consegna](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

Le consegne transazionali inviate dall’istanza di esecuzione vengono sincronizzate nuovamente con l’istanza di controllo tramite un flusso di lavoro tecnico (**[!UICONTROL Message Center execution instance]**) che viene eseguito ogni ora.

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

Per monitorare l’attività e l’esecuzione delle istanze di esecuzione, vedi [Rapporti di messaggistica transazionale](../../message-center/using/about-transactional-messaging-reports.md).
