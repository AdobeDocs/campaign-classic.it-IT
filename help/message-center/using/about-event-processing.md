---
product: campaign
title: Elaborazione di eventi
description: Scopri come vengono elaborati gli eventi di messaggistica transazionale in Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 2%

---

# Elaborazione di eventi {#about-event-processing}



Nel contesto dei messaggi transazionali, un evento viene generato da un sistema di informazioni esterno e inviato ad Adobe Campaign tramite **[!UICONTROL PushEvent]** e **[!UICONTROL PushEvents]** metodi (vedere [Descrizione evento](../../message-center/using/event-description.md)).

Questo evento contiene dati collegati all’evento, ad esempio [tipo](../../message-center/using/creating-event-types.md) (conferma dell’ordine, creazione di un account su un sito web, ecc.), indirizzo e-mail o numero di cellulare, nonché altre informazioni che ti consentono di arricchire e personalizzare il messaggio transazionale prima della consegna (informazioni di contatto del cliente, lingua del messaggio, formato e-mail, ecc.).

Esempio di dati evento:

![](assets/messagecenter_events_request_001.png)

## Passaggi di elaborazione degli eventi {#event-processing}

Per elaborare gli eventi di messaggistica transazionale, alle istanze di esecuzione vengono applicati i seguenti passaggi:

1. [Raccolta di eventi](#event-collection)
1. [Trasferimento di eventi a un modello di messaggio](#routing-towards-a-template)
1. Arricchimento degli eventi con i dati di personalizzazione
1. [Esecuzione della consegna](../../message-center/using/delivery-execution.md)
1. [Riciclaggio di eventi](#event-recycling) consegna collegata non riuscita (tramite un flusso di lavoro Adobe Campaign)

Una volta eseguiti tutti i passaggi precedenti tramite l’istanza di esecuzione, ogni destinatario destinatario riceve un messaggio personalizzato.

>[!NOTE]
>
>Per ulteriori informazioni sulle istanze di messaggistica transazionale, consulta [Architettura dei messaggi transazionali](../../message-center/using/transactional-messaging-architecture.md).


## Raccolta di eventi {#event-collection}

Gli eventi generati dal sistema di informazione possono essere raccolti utilizzando due modalità:

* Le chiamate ai metodi SOAP consentono di inviare eventi in Adobe Campaign: il metodo PushEvent consente di inviare un evento alla volta, il metodo PushEvents consente di inviare diversi eventi alla volta. Per ulteriori informazioni, consulta [Descrizione evento](../../message-center/using/event-description.md).

* La creazione di un flusso di lavoro consente di recuperare gli eventi importando file o tramite un gateway SQL (con [Federated Data Access](../../installation/using/about-fda.md) opzionale).

Una volta raccolti, gli eventi vengono suddivisi per flussi di lavoro tecnici tra le code in tempo reale e batch delle istanze di esecuzione, in attesa di essere collegati a un modello di messaggio.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Nelle istanze di esecuzione, il **[!UICONTROL Real time events]** o **[!UICONTROL Batch events]** le cartelle non devono essere impostate come viste, in quanto ciò potrebbe causare problemi di diritti di accesso. Per ulteriori informazioni sull’impostazione di una cartella come visualizzazione, consulta [questa sezione](../../platform/using/access-management-folders.md).

## Instradamento verso un modello {#routing-towards-a-template}

Una volta pubblicato il modello di messaggio nelle istanze di esecuzione, vengono generati automaticamente due modelli: uno da collegare a un evento in tempo reale e uno da collegare a un evento batch.

La fase di instradamento consiste nel collegare un evento al modello di messaggio appropriato, in base a:

* Il tipo di evento specificato nelle proprietà dell’evento stesso:

  ![](assets/messagecenter_event_type_001.png)

* Tipo di evento specificato nelle proprietà del modello di messaggio:

  ![](assets/messagecenter_event_type_002.png)

Per impostazione predefinita, il ciclo si basa sulle seguenti informazioni:

* Tipo di evento
* Canale da utilizzare (per impostazione predefinita: e-mail)
* Modello di consegna più recente, in base alla data di pubblicazione

## Stati degli eventi {#event-statuses}

Il **Cronologia eventi**, in **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** , raggruppa tutti gli eventi elaborati in un’unica vista. Possono essere categorizzate per tipo di evento o per **stato**. Questi stati sono:

* **In sospeso**: l’evento può essere:

   * Un evento che è stato appena raccolto e che non è ancora stato elaborato. Il **[!UICONTROL Number of errors]** mostra il valore 0. Il modello e-mail non è ancora stato collegato.
   * Un evento elaborato ma la cui conferma è errata. Il **[!UICONTROL Number of errors]** mostra un valore diverso da 0. Per sapere quando questo evento verrà elaborato di nuovo, consulta **[!UICONTROL Process requested on]** colonna.

* **Consegna in sospeso**: l’evento è stato elaborato e il modello di consegna è collegato. L’e-mail è in attesa di consegna e viene applicato il processo di consegna classico. Per ulteriori informazioni, puoi aprire la consegna.
* **Inviato**, **Ignorato** e **Errore di consegna**: questi stati di consegna vengono recuperati tramite **updateEventsStatus** flusso di lavoro. Per ulteriori informazioni, puoi aprire la consegna pertinente.
* **Evento non coperto**: fase di routing della messaggistica transazionale non riuscita. Ad esempio, Adobe Campaign non ha trovato l’e-mail che funge da modello per l’evento.
* **Evento scaduto**: è stato raggiunto il numero massimo di tentativi di invio. L’evento è considerato nullo.

## Riciclaggio degli eventi {#event-recycling}

Se la consegna di un messaggio su un canale specifico non riesce, Adobe Campaign può inviarlo nuovamente utilizzando un canale diverso. Ad esempio, se una consegna sul canale SMS non riesce, il messaggio viene inviato nuovamente utilizzando il canale e-mail.

A questo scopo, devi configurare un flusso di lavoro che ricrea tutti gli eventi con **Errore di consegna** e assegna loro un canale diverso.

>[!CAUTION]
>
>Questo passaggio può essere eseguito solo utilizzando un flusso di lavoro ed è quindi riservato agli utenti esperti. Per ulteriori informazioni, contatta il responsabile del tuo account Adobe.