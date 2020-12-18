---
solution: Campaign Classic
product: campaign
title: Subscription Services
description: Ulteriori informazioni sull'attività del flusso di lavoro Servizi iscrizione
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---


# Subscription Services{#subscription-services}

Un&#39;attività di tipo **Servizi di iscrizione** consente di creare o eliminare una sottoscrizione a un servizio di informazione per la popolazione specificata nella transizione.

Per configurarlo, modificate l&#39;attività e inseritene l&#39;etichetta, quindi selezionate l&#39;azione da eseguire (Iscrizione o Annulla sottoscrizione) e il servizio interessato, come nell&#39;esempio seguente:

![](assets/edit_service_inscription.png)

1. Immettete l&#39;etichetta dell&#39;attività.
1. Selezionare **[!UICONTROL Generate an outbound transition]** se si desidera creare una transizione alla fine dell&#39;esecuzione.

   In genere, l&#39;iscrizione di una destinazione a un servizio di informazioni segna la fine del flusso di lavoro di targeting, motivo per cui l&#39;opzione non è attivata per impostazione predefinita.

1. Fare clic su **[!UICONTROL Subscription]** o **[!UICONTROL Unsubscription]** se si desidera abbonarsi o annullare l&#39;iscrizione della popolazione specificata al servizio di informazioni selezionato.
1. Selezionate **[!UICONTROL Send a confirmation message]** per notificare ai destinatari che sono iscritti o che non hanno più effettuato la sottoscrizione a un servizio.

   Il contenuto di questo messaggio viene specificato in un modello di consegna relativo al servizio informazioni. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/managing-subscriptions.md).

## Esempio: Iscriviti a un elenco di destinatari per una newsletter {#example--subscribe-a-list-of-recipients-to-a-newsletter}

In un&#39;unica operazione, il seguente flusso di lavoro mira a rendere un elenco di destinatari idonei per una newsletter, destinata ai lavoratori che vivono a Parigi, al fine di consentire loro di iscriversi.

A tal fine, è necessario escludere anche i destinatari che hanno già effettuato la sottoscrizione.

>[!CAUTION]
>
>Prima di iscriversi manualmente a un servizio, verifica che i destinatari accetti di ricevere le comunicazioni dall’utente.

![](assets/subscription_services_example.png)

1. Aggiungete le seguenti tre query:

   * Un solo destinatario di età compresa tra i 18 e i 60 anni.
   * Un secondo targeting per i destinatari che vivono a Parigi.
   * Un terzo destinatario che non è attualmente iscritto alla newsletter.

1. Aggiungete un&#39;attività di intersezione per fare riferimento incrociato ai diversi risultati.
1. Se lo desideri, inserisci un aggiornamento dell&#39;elenco per mantenere aggiornato l&#39;elenco degli ultimi utenti iscritti.
1. Inserite un&#39;attività di servizi di iscrizione, quindi fate doppio clic su di essa per configurarla.
1. Immettete l&#39;etichetta dell&#39;attività e selezionate **[!UICONTROL Subscription]**.

   Se lo desiderate, potete informare i destinatari della loro iscrizione alla newsletter selezionando la casella **[!UICONTROL Send a confirmation message]**.

1. Selezionate la cartella in cui si trova la newsletter, quindi selezionate la newsletter dall’elenco visualizzato.
1. Lasciate deselezionata l&#39;opzione **[!UICONTROL Generate outbound transition]** in modo che l&#39;attività contrassegni la fine del flusso di lavoro, quindi fate clic su **[!UICONTROL Ok]**.

Durante l’esecuzione del flusso di lavoro, i destinatari corrispondenti a tutte e tre le query vengono aggiunti all’elenco e sottoscritti alla newsletter.

Per verificare che l&#39;iscrizione sia stata eseguita correttamente, andate alla scheda **[!UICONTROL Subscription]** dei destinatari.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.
