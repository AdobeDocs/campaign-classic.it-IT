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
translation-type: tm+mt
source-git-commit: acb505fac39222e53a3acab6b5c93d10c9d11ba8
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 5%

---


# Informazioni sul canale app mobile{#about-mobile-app-channel}

>[!CAUTION]
>
>Questo documento descrive in dettaglio il processo di integrazione dell’applicazione mobile con la piattaforma Adobe Campaign . Non fornisce informazioni su come creare l’applicazione mobile o su come configurarla per la gestione delle notifiche. Per maggiori informazioni, consulta la [documentazione](https://developer.apple.com/) ufficiale Apple e la [documentazione](https://developer.android.com/index.html)Android.

Le sezioni seguenti forniscono informazioni specifiche per il canale dell&#39;app mobile.

Per informazioni globali su come creare una consegna, consulta[questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

Canale **app** mobile consente di utilizzare la piattaforma Adobe Campaign  per inviare notifiche personalizzate ai terminali iOS e Android tramite app. Sono disponibili due canali di consegna:

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
>* È necessario assicurarsi che le notifiche inviate a un&#39;applicazione mobile siano conformi ai prerequisiti e alle condizioni specificati da Apple (Apple Push Notification Service) e Google (Firebase Cloud Messaging).
>* Avviso: in alcuni paesi, la legge prevede che gli utenti siano informati del tipo di dati che utilizzano le applicazioni mobili e dello scopo della loro elaborazione. Devi controllare la legislazione.


Il flusso di lavoro **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) aggiorna le sottoscrizioni di notifica sui dispositivi mobili. For more information on this workflow, refer to the [Workflows guide](../../workflow/using/mobile-app-channel.md).

 Adobe Campaign è compatibile con APN binari e HTTP/2. Per ulteriori dettagli sui passaggi di configurazione, consulta [Configurazione di un’applicazione mobile nella sezione  Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .

## Percorso dati {#data-path}

Gli schemi seguenti descrivono i passaggi che consentono a un&#39;applicazione mobile di scambiare dati con  Adobe Campaign. Questo processo coinvolge tre entità:

* l’applicazione mobile
* il servizio di notifica: APN (Apple Push Notification Service) per Apple e FCM (Firebase Cloud Messaging) per Android
* Adobe Campaign

Le tre fasi principali del processo di notifica sono: registrazione dell&#39;applicazione in  Adobe Campaign (raccolta di iscrizioni), consegne e tracciamento.

### Passaggio 1: Raccolta di iscrizioni {#step-1--subscription-collection}

L’applicazione mobile viene scaricata dall’utente dall’App Store o da Google Play. Questa applicazione contiene le impostazioni di connessione (certificato iOS e chiave di progetto per Android) e la chiave di integrazione. La prima volta che l&#39;applicazione viene aperta (a seconda della configurazione), all&#39;utente può essere chiesto di immettere le informazioni di registrazione (@userKey: indirizzo e-mail o numero di account, ad esempio). Allo stesso tempo, l&#39;applicazione contesta al servizio di notifica di raccogliere un ID di notifica (ID push). Tutte queste informazioni (impostazioni di connessione, chiave di integrazione, identificatore di notifica, userKey) vengono inviate a  Adobe Campaign.

![](assets/nmac_register_view.png)

### Passaggio 2: Consegna {#step-2--delivery}

Gli addetti al marketing eseguono il targeting degli abbonati alle applicazioni. Il processo di consegna invia le impostazioni di connessione al servizio di notifica (certificato iOS e chiave di progetto per Android), all&#39;ID di notifica (ID push) e al contenuto della notifica. Il servizio di notifica invia notifiche ai terminali di destinazione.

Le seguenti informazioni sono disponibili in  Adobe Campaign:

* Solo Android: numero di dispositivi che hanno visualizzato la notifica (impression)
* Android e iOS: numero di clic sulla notifica

![](assets/nmac_delivery_view.png)

Il server Adobe Campaign  deve essere in grado di contattare il server APN sulle seguenti porte:

* 2195 (invio) e 2186 (servizio di feedback) per connettore binario iOS
* 443 per il connettore iOS HTTP/2

   >[!NOTE]
   >
   > A partire dalla release Campaign 20.3, il connettore legacy binario per iOS è diventato obsoleto. Se utilizzi questo connettore, devi adattare di conseguenza l’implementazione.
 [Ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/migrate-to-apns-http2.html)

Per verificare che funzioni correttamente, usate i seguenti comandi:

* Per le prove:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* In produzione:

   ```
   telnet gateway.push.apple.com
   ```

Se viene utilizzato un connettore binario iOS, MTA e il server Web devono essere in grado di contattare i APN sulla porta 2195 (invio), il server del flusso di lavoro deve essere in grado di contattare i APN sulla porta 2196 (servizio di feedback).

Se si utilizza un connettore iOS HTTP/2, MTA, server Web e server di workflow devono essere in grado di contattare i servizi APN sulla porta 443.

