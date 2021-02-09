---
solution: Campaign Classic
product: campaign
title: Esecuzione della consegna
description: Esecuzione della consegna
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: fd6195ca447fa0345189f3153f44ad2f9a067210
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 7%

---


# Esecuzione della consegna{#delivery-execution}

## Invio di messaggi transazionali {#transactional-message-send}

Nell’istanza di esecuzione, una volta completata la fase di arricchimento e collegato un modello di consegna all’evento, la consegna viene inviata.

>[!NOTE]
>
>L&#39;MTA dà priorità all&#39;elaborazione dei messaggi transazionali rispetto a qualsiasi altra consegna.

Tutte le consegne sono raggruppate nella cartella **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Per impostazione predefinita, sono ordinati in sottocartelle per mese di consegna. Questo ordinamento può essere modificato nelle proprietà del modello di messaggio come mostrato di seguito.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Per le installazioni ospitate o ibride, se avete effettuato l&#39;aggiornamento a [MTA](../../delivery/using/sending-with-enhanced-mta.md) Enhanced, tutti i messaggi transazionali possono essere inviati anche con l&#39;MTA avanzato di Adobe Campaign  per migliorare la recapito, il throughput e la gestione dei bounce. Tutti gli effetti sono gli stessi dei messaggi di marketing standard.

## Monitoraggio dei messaggi transazionali {#transactional-message-monitoring}

Per monitorare i messaggi transazionali, controlla i registri di consegna. L&#39;accesso ai registri di consegna è presentato in [questa sezione](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

Le consegne transazionali inviate dall&#39;istanza di esecuzione vengono sincronizzate nuovamente nell&#39;istanza di controllo tramite un flusso di lavoro tecnico (**[!UICONTROL Message Center execution instance]**) che viene eseguito ogni ora.

>[!NOTE]
>
>Le consegne accumulano settimanalmente gli eventi in base all&#39;ultimo aggiornamento dell&#39;evento e non in base alla data di creazione dell&#39;evento. Di conseguenza, quando si estraggono i registri di consegna dei messaggi transazionali dall&#39;istanza di controllo, l&#39;ID di consegna associato a ciascun ID del registro di consegna potrebbe cambiare nel tempo mano a mano che il registro viene aggiornato (ad esempio, quando viene ricevuto un rimbalzo in entrata per l&#39;evento).

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