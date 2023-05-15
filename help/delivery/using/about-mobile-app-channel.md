---
product: campaign
title: Guida introduttiva al canale app mobile
description: Guida introduttiva al canale app mobile in Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Push
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 2%

---

# Guida introduttiva al canale app mobile{#about-mobile-app-channel}



La **Canale app mobile** consente di utilizzare la piattaforma Adobe Campaign per inviare notifiche push personalizzate ai terminali iOS e Android tramite app.

>[!CAUTION]
>
>Questo documento descrive il processo di integrazione dell’app mobile con la piattaforma Adobe Campaign. Non fornisce informazioni su come creare l’app mobile o su come configurarla per la gestione delle notifiche. Per ulteriori informazioni, consulta l’Apple ufficiale [documentazione](https://developer.apple.com/) e Android [documentazione](https://developer.android.com/index.html).

Sono disponibili due canali di consegna:

* Canale iOS che consente di inviare notifiche ai dispositivi mobili Apple.

   ![](assets/nmac_intro_2.png)

* Canale Android che consente di inviare messaggi di dati ai dispositivi mobili Android.

   ![](assets/nmac_intro_1.png)

Corrispondente a questi due canali, nei flussi di lavoro delle campagne sono presenti due attività di consegna:

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>Per la messaggistica transazionale sono disponibili anche due modelli di messaggio transazionale.

Puoi definire il comportamento dell’applicazione per quando l’utente attiva la notifica per visualizzare la schermata che corrisponde al contesto dell’applicazione. Ad esempio:

* Viene inviata una notifica al cliente per comunicare che il suo pacco è uscito dal magazzino. Quando si attiva la notifica, viene aperta una pagina con informazioni relative alla consegna.
* L’utente ha aggiunto elementi al carrello, ma ha lasciato l’applicazione senza completare l’acquisto. Viene inviata una notifica che dice loro che il loro carrello è stato abbandonato. Quando attivano la notifica, l’elemento viene visualizzato sullo schermo.

>[!CAUTION]
>
>* Devi accertarti che le notifiche inviate a un’app mobile siano conformi ai prerequisiti e alle condizioni specificati da Apple (Apple Push Notification Service) e Google (Firebase Cloud Messaging).
>* Avviso: in alcuni paesi, la legge richiede che gli utenti siano informati del tipo di dati raccolti per le applicazioni mobili e dello scopo del loro trattamento. Devi controllare la legislazione.


La **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) il flusso di lavoro aggiorna le sottoscrizioni di notifiche sui dispositivi mobili. Per ulteriori informazioni su questo flusso di lavoro, consulta [elenco dei flussi di lavoro tecnici](../../workflow/using/about-technical-workflows.md).

Adobe Campaign è compatibile con le APN HTTP/2. Per ulteriori dettagli sui passaggi di configurazione, consulta la [questa sezione](configuring-the-mobile-application.md) sezione .

Per informazioni globali su come creare una consegna, consulta [questa sezione](steps-about-delivery-creation-steps.md).

## Percorso dati {#data-path}

Gli schemi seguenti descrivono i passaggi che consentono a un’app mobile di scambiare dati con Adobe Campaign. Questo processo coinvolge tre entità:

* l&#39;applicazione mobile
* il servizio di notifica: APN (Apple Push Notification Service) per Apple e FCM (Firebase Cloud Messaging) per Android
* Adobe Campaign

Le tre fasi principali del processo di notifica sono: registrazione dell’applicazione in Adobe Campaign (raccolta abbonamenti), consegne e tracciamento.

### Passaggio 1: Raccolta abbonamenti {#step-1--subscription-collection}

L’app mobile viene scaricata dall’utente da App Store o da Google Play. Questa applicazione contiene le impostazioni di connessione (certificato iOS e chiave di progetto per Android) e la chiave di integrazione. Alla prima apertura dell’applicazione (a seconda della configurazione), è possibile chiedere all’utente di inserire le informazioni di registrazione (@userKey: e-mail o numero di account, ad esempio). Allo stesso tempo, l&#39;applicazione chiede al servizio di notifica di raccogliere un ID di notifica (ID push). Tutte queste informazioni (impostazioni di connessione, chiave di integrazione, identificatore di notifica, userKey) vengono inviate ad Adobe Campaign.

![](assets/nmac_register_view.png)

### Passaggio 2: Consegna {#step-2--delivery}

Gli addetti al marketing eseguono il targeting degli abbonati alle applicazioni. Il processo di consegna invia le impostazioni di connessione al servizio di notifica (certificato iOS e chiave di progetto per Android), all’ID di notifica (ID push) e al contenuto della notifica. Il servizio di notifica invia notifiche ai terminali di destinazione.

Le seguenti informazioni sono disponibili in Adobe Campaign:

* Solo Android: numero di dispositivi che hanno visualizzato la notifica (impression)
* Android e iOS: numero di clic sulla notifica

![](assets/nmac_delivery_view.png)

Il server Adobe Campaign deve essere in grado di contattare il server APN sulla porta 443 per il connettore iOS HTTP/2.

Per verificare che funzioni correttamente, utilizza i seguenti comandi:

* Per le prove:

   ```
   api.development.push.apple.com:443
   ```

* In produzione:

   ```
   api.push.apple.com:443
   ```

Con il connettore iOS HTTP/2, l&#39;MTA e il server web devono essere in grado di contattare gli APN sulla porta 443.

Se hai bisogno di utilizzare il connettore iOS HTTP/2 tramite un proxy, consulta questo [page](../../installation/using/file-res-management.md#proxy-connection-configuration).
