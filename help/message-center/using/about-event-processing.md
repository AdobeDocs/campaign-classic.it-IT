---
solution: Campaign Classic
product: campaign
title: Informazioni sull’elaborazione di eventi
description: Informazioni sull’elaborazione di eventi
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 3%

---


# Informazioni sull’elaborazione di eventi{#about-event-processing}

Nel contesto dei messaggi transazionali, un evento viene generato da un sistema di informazioni esterno e inviato ad  Adobe Campaign tramite i **[!UICONTROL PushEvent]** metodi e **[!UICONTROL PushEvents]** (fare riferimento alla descrizione [dell&#39;](../../message-center/using/event-description.md)evento). Contiene dati collegati all’evento, come il tipo (ad esempio, conferma dell’ordine o creazione dell’account su un sito Web), l’indirizzo e-mail o il numero di cellulare, nonché altre informazioni che consentono di arricchire e personalizzare il messaggio transazionale prima della consegna. Può trattarsi delle informazioni di contatto del cliente, della lingua del messaggio o del formato e-mail.

Esempio di dati evento:

![](assets/messagecenter_events_request_001.png)

Per elaborare eventi di messaggistica transazionali, è necessario applicare i seguenti passaggi:

1. Raccolta di eventi,
1. Trasferimento di eventi a un modello di messaggio,
1. Arricchimento degli eventi con dati di personalizzazione,
1. Esecuzione della consegna,
1. Riciclo di eventi la cui consegna collegata non è riuscita (questo passaggio può essere eseguito tramite un flusso di lavoro Adobe Campaign ).

## Stati dell&#39;evento {#event-statuses}

La cronologia **** dell&#39;evento, in **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** , raggruppa tutti gli eventi elaborati in un&#39;unica visualizzazione. Possono essere organizzati per tipo di evento o per **stato**. Questi stati sono:

* **In sospeso**: che significa che l&#39;evento può essere:

   * un evento che è stato appena raccolto e che non è ancora stato elaborato. La **[!UICONTROL Number of errors]** colonna mostra il valore 0. Il modello e-mail non è ancora stato collegato.
   * un evento elaborato ma la cui conferma è errata. La **[!UICONTROL Number of errors]** colonna mostra un valore diverso da 0. Per sapere quando verrà elaborato di nuovo questo evento, consultare la **[!UICONTROL Process requested on]** colonna.

* **In attesa di consegna**: l&#39;evento è stato elaborato e il modello di consegna è collegato. L&#39;e-mail è in attesa di consegna e viene applicato il processo di consegna classico. Per ulteriori informazioni, potete aprire la consegna. Fare riferimento a [Consegna](../../delivery/using/about-message-tracking.md).
* **Invio**, **Ignorato** ed errore **di** consegna: questi stati di consegna vengono recuperati tramite il flusso di lavoro **updateEventsStatus** . Per ulteriori informazioni, puoi aprire la consegna corrispondente.
* **Evento non coperto**: la fase di routing del Centro messaggi non è riuscita. Ad esempio,  Adobe Campaign non ha trovato l&#39;e-mail che funge da modello per l&#39;evento.
* **Evento scaduto**: è stato raggiunto il numero massimo di tentativi di invio. L&#39;evento è considerato nullo.
