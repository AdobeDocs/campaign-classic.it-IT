---
product: campaign
title: Elaborazione di eventi
description: Scopri come vengono elaborati gli eventi di messaggistica transazionale in Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 2%

---

# Elaborazione di eventi {#about-event-processing}



Nel contesto della messaggistica transazionale, un evento viene generato da un sistema di informazioni esterno e inviato ad Adobe Campaign tramite il **[!UICONTROL PushEvent]** e **[!UICONTROL PushEvents]** metodi (vedi [Descrizione evento](../../message-center/using/event-description.md)).

Questo evento contiene dati collegati all&#39;evento, ad esempio [type](../../message-center/using/creating-event-types.md) (conferma dell’ordine, creazione dell’account su un sito web, ecc.), indirizzo e-mail o numero di cellulare, nonché altre informazioni che consentono di arricchire e personalizzare il messaggio transazionale prima della consegna (informazioni di contatto del cliente, lingua del messaggio, formato e-mail, ecc.).

Esempio di dati evento:

![](assets/messagecenter_events_request_001.png)

## Passaggi di elaborazione degli eventi {#event-processing}

Per elaborare gli eventi di messaggistica transazionale, i seguenti passaggi vengono applicati alle istanze di esecuzione:

1. [Raccolta di eventi](#event-collection)
1. [Trasferimento di eventi a un modello di messaggio](#routing-towards-a-template)
1. Arricchimento degli eventi con dati di personalizzazione
1. [Esecuzione della consegna](../../message-center/using/delivery-execution.md)
1. [Riciclo degli eventi](#event-recycling) la cui consegna collegata non è riuscita (tramite un flusso di lavoro Adobe Campaign)

Una volta eseguiti tutti i passaggi precedenti tramite l’istanza di esecuzione, ogni destinatario con targeting riceve un messaggio personalizzato.

>[!NOTE]
>
>Per ulteriori informazioni sulle istanze di messaggistica transazionale, consulta [Architettura della messaggistica transazionale](../../message-center/using/transactional-messaging-architecture.md).


## Raccolta di eventi {#event-collection}

Gli eventi generati dal sistema di informazione possono essere raccolti utilizzando due modalità:

* Le chiamate ai metodi SOAP consentono di inviare eventi in push in Adobe Campaign: il metodo PushEvent consente di inviare un evento alla volta, il metodo PushEvents consente di inviare diversi eventi contemporaneamente. Per ulteriori informazioni, consulta [Descrizione evento](../../message-center/using/event-description.md).

* La creazione di un flusso di lavoro consente di recuperare gli eventi importando i file o tramite un gateway SQL (con [Federated Data Access](../../installation/using/about-fda.md) ).

Una volta raccolti, gli eventi vengono suddivisi per flussi di lavoro tecnici tra le code in tempo reale e batch delle istanze di esecuzione, in attesa di essere collegati a un modello di messaggio.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Nelle istanze di esecuzione, la **[!UICONTROL Real time events]** o **[!UICONTROL Batch events]** le cartelle non devono essere impostate come visualizzazioni, in quanto ciò potrebbe causare problemi di accesso ai diritti. Per ulteriori informazioni sull’impostazione di una cartella come visualizzazione, consulta [questa sezione](../../platform/using/access-management-folders.md).

## Instradamento verso un modello {#routing-towards-a-template}

Una volta pubblicato il modello di messaggio sulle istanze di esecuzione, vengono generati automaticamente due modelli: da collegare a un evento in tempo reale e da collegare a un evento batch.

La fase di indirizzamento consiste nel collegare un evento al modello di messaggio appropriato, in base a:

* Il tipo di evento specificato nelle proprietà dell&#39;evento stesso:

   ![](assets/messagecenter_event_type_001.png)

* Il tipo di evento specificato nelle proprietà del modello di messaggio:

   ![](assets/messagecenter_event_type_002.png)

Per impostazione predefinita, il ciclo di produzione si basa sulle seguenti informazioni:

* Il tipo di evento
* Il canale da utilizzare (per impostazione predefinita: e-mail)
* Il modello di consegna più recente, in base alla data di pubblicazione

## Stati degli eventi {#event-statuses}

La **Cronologia eventi**, **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** , raggruppa tutti gli eventi elaborati in un’unica visualizzazione. Possono essere suddivisi per tipo di evento o per **status**. Questi stati sono:

* **In sospeso**: L’evento può essere:

   * Un evento che è appena stato raccolto e che non è ancora stato elaborato. La **[!UICONTROL Number of errors]** mostra il valore 0. Il modello e-mail non è ancora stato collegato.
   * Un evento elaborato ma la cui conferma è errata. La **[!UICONTROL Number of errors]** mostra un valore diverso da 0. Per sapere quando questo evento verrà elaborato di nuovo, consulta la **[!UICONTROL Process requested on]** colonna.

* **Consegna in sospeso**: L’evento è stato elaborato e il modello di consegna è collegato. L’e-mail è in attesa di consegna e viene applicato il processo di consegna classico . Per ulteriori informazioni, puoi aprire la consegna.
* **Inviato**, **Ignorato** e **Errore di consegna**: Questi stati di consegna vengono recuperati tramite **updateEventsStatus** workflow. Per ulteriori informazioni, puoi aprire la consegna pertinente.
* **Evento non coperto**: La fase di indirizzamento della messaggistica transazionale non è riuscita. Ad esempio, Adobe Campaign non ha trovato l’e-mail che funge da modello per l’evento.
* **Evento scaduto**: È stato raggiunto il numero massimo di tentativi di invio. L&#39;evento è considerato nullo.

## Riciclaggio degli eventi {#event-recycling}

Se la consegna di un messaggio su un canale specifico non riesce, Adobe Campaign può inviare nuovamente il messaggio utilizzando un canale diverso. Ad esempio, se una consegna sul canale SMS non riesce, il messaggio viene inviato nuovamente utilizzando il canale e-mail.

A questo scopo, devi configurare un flusso di lavoro che ricrea tutti gli eventi con il **Errore di consegna** e assegna loro un canale diverso.

>[!CAUTION]
>
>Questo passaggio può essere eseguito solo utilizzando un flusso di lavoro ed è pertanto riservato agli utenti esperti. Per ulteriori informazioni, contatta il tuo responsabile dell&#39;account di Adobe.