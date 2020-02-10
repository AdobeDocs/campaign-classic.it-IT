---
title: Il canale delle app mobili in Adobe Campaign Classic
description: Questa sezione fornisce informazioni generali specifiche per il canale dell'app mobile in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# Il canale delle app mobili{#about-mobile-app-channel}

>[!CAUTION]
>
>Questo documento descrive in dettaglio il processo per l&#39;integrazione dell&#39;applicazione mobile con la piattaforma Adobe Campaign. Non fornisce informazioni su come creare l’applicazione mobile o come configurarla per la gestione delle notifiche. Per ulteriori informazioni, consultate la documentazione ufficiale Apple ([https://developer.apple.com/](https://developer.apple.com/)) e Android ([https://developer.android.com/index.html](https://developer.android.com/index.html)).

Le sezioni seguenti forniscono informazioni specifiche per il canale dell&#39;app mobile. Per informazioni globali su come creare una consegna, consulta[questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

Canale **app** mobile consente di utilizzare la piattaforma Adobe Campaign per inviare notifiche personalizzate ai terminali iOS e Android tramite app. Sono disponibili due canali di consegna:

* Canale iOS che consente di inviare notifiche ai dispositivi mobili Apple.

   ![](assets/nmac_intro_2.png)

* Canale Android che consente di inviare messaggi di dati ai dispositivi mobili Android.

   ![](assets/nmac_intro_1.png)

In base a questi due canali, nei flussi di lavoro della campagna sono disponibili due attività di consegna:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>Per i messaggi transazionali sono inoltre disponibili due modelli di messaggio transazionali.

Potete definire il comportamento dell&#39;applicazione quando l&#39;utente attiva la notifica per visualizzare la schermata che corrisponde al contesto dell&#39;applicazione. Ad esempio:

* Viene inviata una notifica al cliente per informarlo che il suo pacco è uscito dal magazzino. Attivando la notifica si apre una pagina contenente informazioni relative alla consegna.
* L&#39;utente ha aggiunto elementi al carrello, ma ha lasciato l&#39;applicazione senza completare l&#39;acquisto. Viene inviata una notifica in cui si informa che il carrello è stato abbandonato. Quando attivano la notifica, l’elemento viene visualizzato sullo schermo.

>[!CAUTION]
>
>* È necessario assicurarsi che le notifiche inviate a un&#39;applicazione mobile siano conformi ai prerequisiti e alle condizioni specificati da Apple (Apple Push Notification Service) e Google (Google Cloud Messaging).
>* Avviso: in alcuni paesi, la legge prevede che gli utenti siano informati del tipo di dati che utilizzano le applicazioni mobili e dello scopo della loro elaborazione. Devi controllare la legislazione.


Il flusso di lavoro **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) aggiorna le sottoscrizioni di notifica sui dispositivi mobili. Per ulteriori informazioni su questo flusso di lavoro, consulta la guida [](../../workflow/using/mobile-app-channel.md)Flussi di lavoro.

Adobe Campaign è compatibile sia con APNS binari che con HTTP/2. Per ulteriori dettagli sui passaggi di configurazione, consulta la sezione [Connettori](../../delivery/using/setting-up-mobile-app-channel.md#connectors) .
