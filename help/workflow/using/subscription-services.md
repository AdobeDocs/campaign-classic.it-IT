---
product: campaign
title: Attività Subscription services
description: Ulteriori informazioni sull’attività del flusso di lavoro Subscription Services
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# Attività Subscription services{#subscription-services}

![](../../assets/common.svg)

A **Servizi di abbonamento** L’attività -type ti consente di creare o eliminare una sottoscrizione a un servizio di informazioni per la popolazione specificata nella transizione.

Per configurarlo, modifica l’attività e inserisci la relativa etichetta, quindi seleziona l’azione da eseguire (abbonamento o annullamento dell’abbonamento) e il servizio interessato, come nell’esempio seguente:

![](assets/edit_service_inscription.png)

1. Immetti l’etichetta dell’attività.
1. Seleziona **[!UICONTROL Generate an outbound transition]** se desideri creare una transizione alla fine dell’esecuzione.

   In genere, la sottoscrizione di una destinazione a un servizio di informazioni segna la fine del flusso di lavoro di targeting, motivo per cui l’opzione non viene attivata per impostazione predefinita.

1. Fai clic su **[!UICONTROL Subscription]** o **[!UICONTROL Unsubscription]** se si desidera abbonarsi o annullare l’iscrizione della popolazione specificata al servizio informazioni selezionato o al servizio stesso.
1. Seleziona **[!UICONTROL Send a confirmation message]** per notificare ai destinatari che si sono abbonati o hanno annullato l’abbonamento a un servizio.

   Il contenuto di questo messaggio viene specificato in un modello di consegna relativo al servizio informazioni. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/managing-subscriptions.md).

## Esempio: Iscriviti a una newsletter un elenco di destinatari {#example--subscribe-a-list-of-recipients-to-a-newsletter}

In un&#39;unica operazione il seguente flusso di lavoro mira a rendere un elenco di destinatari idonei per una newsletter, destinata ai lavoratori che vivono a Parigi, al fine di ottenere loro l&#39;iscrizione.

A questo scopo, devi anche escludere i destinatari che hanno già effettuato la sottoscrizione.

>[!CAUTION]
>
>Prima di effettuare manualmente l’abbonamento dei destinatari a un servizio, verifica che tali destinatari accettino di ricevere comunicazioni dall’utente.

![](assets/subscription_services_example.png)

1. Aggiungi le tre query seguenti:

   * Uno dei destinatari di targeting di età compresa tra i 18 e i 60 anni.
   * Un secondo targeting per i destinatari che vivono a Parigi.
   * Un terzo destinatario che al momento non è iscritto alla newsletter.

1. Aggiungi un’attività di intersezione per fare riferimento incrociato ai diversi risultati.
1. Se lo desideri, inserisci un aggiornamento dell’elenco per mantenere aggiornato l’elenco degli ultimi abbonati.
1. Inserisci un’attività di servizi di abbonamento, quindi fai doppio clic su questa per configurarla.
1. Immetti l’etichetta dell’attività e seleziona **[!UICONTROL Subscription]**.

   Se lo desideri, puoi informare i destinatari della loro iscrizione alla newsletter selezionando la **[!UICONTROL Send a confirmation message]** scatola.

1. Seleziona la cartella in cui si trova la newsletter, quindi seleziona la newsletter dall’elenco visualizzato.
1. Lascia la **[!UICONTROL Generate outbound transition]** deselezionata affinché questa attività contrassegni la fine del flusso di lavoro, quindi fai clic su **[!UICONTROL Ok]**.

Durante l’esecuzione del flusso di lavoro, i destinatari corrispondenti a tutte e tre le query vengono aggiunti all’elenco e abbonati alla newsletter.

Puoi verificare che l’abbonamento sia stato eseguito correttamente accedendo al **[!UICONTROL Subscription]** per i destinatari.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.
