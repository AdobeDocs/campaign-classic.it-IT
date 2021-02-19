---
solution: Campaign Classic
product: campaign
title: Gestione delle sottoscrizioni
description: Gestione delle sottoscrizioni
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 2%

---


# Gestione degli abbonamenti{#managing-subscriptions}

## Informazioni sui servizi di informazione {#about-information-services}

Un servizio di informazione comprende:

* Registrazione e iscrizione (opt-in),
* Cancellazione, annullamento dell&#39;iscrizione volontaria (opt out) o annullamento dell&#39;iscrizione automatica (servizio a tempo limitato, ad esempio come offerta di prova),
* meccanismi di conferma dell’iscrizione e dell’annullamento della sottoscrizione (semplici meccanismi con conferma, doppio consenso, ecc.),
* Tracciamento della cronologia degli abbonati.

In linea di massima, questi servizi includono specifici rapporti statistici: tracciamento sottoscrizione, livello fedeltà, tendenze annullamento sottoscrizione ecc.

Per le e-mail, i collegamenti di annullamento dell&#39;iscrizione obbligatori vengono generati automaticamente e l&#39;intero processo di opt in/opt out è completamente automatizzato, con il monitoraggio della cronologia per garantire la piena conformità con le normative in vigore.

Sono disponibili tre modalità di iscrizione/annullamento dell’iscrizione al servizio:

1. manual
1. importando (solo abbonamento),
1. tramite un modulo Web

>[!NOTE]
>
>Un esempio per creare un modulo di iscrizione con doppio consenso è descritto in [questa sezione](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## Creazione di un servizio di informazione {#creating-an-information-service}

Potete creare e gestire le iscrizioni ai servizi di informazione con i messaggi di conferma associati o le consegne automatiche agli abbonati.

Per accedere alla mappa dei servizi di informazione, andate all&#39;universo **[!UICONTROL Profiles and Targets]** e fate clic sul collegamento **[!UICONTROL Services and Subscriptions]**.

![](assets/s_ncs_user_services_new.png)

Per modificare un servizio esistente, fate clic sul suo nome. Per creare un servizio, fate clic sul pulsante **[!UICONTROL Create]** situato sopra l&#39;elenco.

![](assets/s_ncs_user_services_add.png)

* Immettete il nome del servizio nel campo **[!UICONTROL Label]** e selezionate il canale di consegna: e-mail, dispositivi mobili, Facebook, Twitter o applicazioni per dispositivi mobili.

   >[!NOTE]
   >
   >Le iscrizioni Facebook e Twitter sono descritte in [questa sezione](../../social/using/about-social-marketing.md). Le iscrizioni alle applicazioni mobili sono dettagliate in [Informazioni sul canale delle app mobili](../../delivery/using/about-mobile-app-channel.md).

* Per un servizio tipo e-mail, selezionare la **Modalità consegna**. Le modalità possibili sono: **[!UICONTROL Newsletter]** o **[!UICONTROL Viral]**.
* È possibile inviare **messaggi di conferma** per ottenere un&#39;iscrizione o annullare l&#39;iscrizione. A tal fine, selezionate i modelli di consegna da utilizzare per creare le consegne corrispondenti dai campi **[!UICONTROL Subscription]** e **[!UICONTROL Unsubscription]**. Questi modelli devono essere configurati con un mapping di destinazione di tipo **[!UICONTROL Subscription]**, senza una destinazione definita. Vedere la sezione [Informazioni sul canale e-mail](../../delivery/using/about-email-channel.md).
* Per impostazione predefinita, le iscrizioni sono illimitate. È possibile deselezionare l&#39;opzione **[!UICONTROL Unlimited]** per definire una durata di validità per il servizio. La durata può essere specificata in giorni (**[!UICONTROL d]** ) o mesi (**[!UICONTROL m]** ).

Una volta salvato, il servizio viene aggiunto all&#39;elenco Servizi e iscrizioni: Fate clic sul suo nome per modificarlo. Sono disponibili diverse schede. La scheda **[!UICONTROL Subscriptions]** consente di visualizzare l&#39;elenco degli utenti iscritti al servizio informazioni (**[!UICONTROL Active subscriptions]** scheda) o alla cronologia di sottoscrizione/annullamento dell&#39;iscrizione (**[!UICONTROL History]** scheda). È inoltre possibile aggiungere ed eliminare sottoscrittori da questa scheda. Vedere [Aggiunta ed eliminazione di abbonati](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Il pulsante **[!UICONTROL Detail...]** consente di visualizzare le proprietà di iscrizione per il destinatario selezionato.

Potete modificare le proprietà di iscrizione per un destinatario.

![](assets/s_ncs_user_services_modify.png)

Nel dashboard, fate clic sulla scheda **[!UICONTROL Reports]** per tenere traccia delle sottoscrizioni: modifiche nei livelli di iscrizione, numero totale di abbonati, ecc. È possibile archiviare i rapporti e consultare le cronologia da questa scheda.

## Aggiunta ed eliminazione di abbonati {#adding-and-deleting-subscribers}

Dalla scheda **[!UICONTROL Subscriptions]** di un servizio di informazione, fate clic su **[!UICONTROL Add]** per aggiungere utenti. È inoltre possibile fare clic con il pulsante destro del mouse sull&#39;elenco di utenti iscritti e selezionare **[!UICONTROL Add]**. Selezionate la cartella in cui sono memorizzati i profili da sottoscrivere, quindi selezionate i profili da sottoscrivere e fate clic su **[!UICONTROL OK]** per eseguire la convalida.

Per eliminare gli abbonati, selezionateli e fate clic su **[!UICONTROL Delete]**. È inoltre possibile fare clic con il pulsante destro del mouse sull&#39;elenco degli utenti iscritti e selezionare **[!UICONTROL Delete]**.

In entrambi i casi, è possibile inviare un messaggio di conferma agli utenti interessati se al servizio è stato allegato un modello di consegna per le sottoscrizioni (vedere [Creazione di un servizio di informazione](#creating-an-information-service)). Un avviso consente di convalidare o non convalidare la consegna:

![](assets/s_ncs_user_services_update.png)

Vedere [Meccanismi di iscrizione e annullamento della sottoscrizione](#subscription-and-unsubscription-mechanisms).

## Consegna agli abbonati di un servizio {#delivering-to-the-subscribers-of-a-service}

Per fornire agli abbonati di un servizio di informazione, potete indirizzare gli abbonati al servizio di informazione interessato, come nell’esempio seguente:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>Il mapping di destinazione deve essere **[!UICONTROL Subscriptions]**.

Seleziona **[!UICONTROL Subscribers of an information service]** e fai clic su **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Selezionate il servizio di informazioni di destinazione e fate clic su **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

La scheda **[!UICONTROL Preview]** consente di visualizzare l&#39;elenco degli abbonati al servizio di informazioni selezionato.

## Meccanismi di iscrizione e annullamento della sottoscrizione {#subscription-and-unsubscription-mechanisms}

Potete configurare meccanismi di iscrizione e annullamento dell’iscrizione per automatizzare i processi e la gestione degli abbonati.

>[!NOTE]
>
>Potete inviare un messaggio di conferma ai nuovi sottoscrittori.\
>Il contenuto di questo messaggio viene definito nella configurazione del servizio informazioni tramite i campi **[!UICONTROL Subscription]** o **[!UICONTROL Unsubscription]**.
>
>I messaggi di conferma vengono creati tramite i modelli di consegna specificati in questi campi. Tali mappature di destinazione devono essere **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Iscrizione di un destinatario a un servizio {#subscribing-a-recipient-to-a-service}

Per registrare i destinatari per un servizio di informazione, potete:

* Aggiungete manualmente il servizio: a tal fine, dalla scheda **[!UICONTROL Subscriptions]** del profilo, fare clic su **[!UICONTROL Add]** e selezionare il servizio informazioni interessato.

   Per ulteriori informazioni, consultare la sezione sulla modifica del profilo in [questa sezione](../../platform/using/editing-a-profile.md).

* Iscriviti automaticamente a questo servizio un set di destinatari. L&#39;elenco dei destinatari può provenire da un&#39;operazione di filtro, un gruppo, una cartella, un&#39;importazione o una selezione diretta utilizzando il mouse. Per iscriverti a questi destinatari, seleziona i profili e fai clic con il pulsante destro del mouse. Selezionare **[!UICONTROL Actions > Subscribe selection to a service...]**, selezionare il servizio interessato e avviare l&#39;operazione.
* Importa i destinatari e li iscrivi automaticamente a un servizio di informazione. A questo scopo, selezionate il servizio in questione nell’ultimo passaggio della procedura guidata di importazione.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/executing-import-jobs.md).

* Utilizzare un modulo Web per consentire ai destinatari di iscriversi a un servizio.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/about-web-applications.md).

* Creazione di un flusso di lavoro di targeting e utilizzo di una casella **[!UICONTROL Subscription service]**.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   I flussi di lavoro e come utilizzarli sono descritti in [questa sezione](../../workflow/using/about-workflows.md).

### Annullamento dell&#39;iscrizione di un destinatario da un servizio {#unsubscribing-a-recipient-from-a-service}

#### Annullamento manuale della sottoscrizione {#manual-unsubscribing}

per legge, le consegne e-mail devono contenere un collegamento per annullare l&#39;iscrizione. I destinatari possono fare clic su questo collegamento per aggiornare il proprio profilo ed essere esclusi dagli obiettivi delle consegne future.

Il collegamento predefinito per l&#39;annullamento della sottoscrizione viene inserito tramite l&#39;ultimo pulsante nella barra degli strumenti dell&#39;editor di contenuti disponibile nella procedura guidata di distribuzione (vedere [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md)). Quando il destinatario fa clic su questo collegamento, il profilo viene aggiunto al elenco Bloccati (rinuncia), il che significa che il destinatario non sarà più preso di mira da alcuna azione di consegna.

I destinatari possono tuttavia scegliere di annullare l’iscrizione a un servizio senza annullare l’iscrizione a tutti i servizi. A tal fine, è possibile utilizzare un modulo Web (fare riferimento a [questa sezione](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) o inserire un collegamento personalizzato senza iscrizione (vedere [Blocchi di personalizzazione](../../delivery/using/personalization-blocks.md)).

Puoi anche annullare l’iscrizione di un destinatario manualmente dal profilo del destinatario. A tal fine, fare clic sulla scheda **[!UICONTROL Subscriptions]** del destinatario interessato, selezionare i servizi di informazione interessati e fare clic su **[!UICONTROL Delete]**.

È infine possibile annullare l’iscrizione di uno o più destinatari tramite il servizio di informazione interessato. A tal fine, fare clic sulla scheda **[!UICONTROL Subscriptions]** del servizio, selezionare i destinatari interessati e fare clic su **[!UICONTROL Delete]**.

#### Annullamento automatico della sottoscrizione {#automatic-unsubscription}

Un servizio di informazione può avere una durata limitata. I destinatari verranno annullati automaticamente alla scadenza del periodo di validità. Questo periodo è specificato nella scheda **[!UICONTROL Edit]** delle proprietà del servizio. Viene espresso in giorni.

![](assets/s_ncs_user_services_delay.png)

Potete anche impostare un flusso di lavoro di annullamento della sottoscrizione per una popolazione. A questo scopo, seguite la stessa procedura utilizzata per un flusso di lavoro di iscrizione, ma selezionate l&#39;opzione **[!UICONTROL Unsubscription]**. Vedere [Iscrizione di un destinatario a un servizio](#subscribing-a-recipient-to-a-service).

### Tracciamento sottoscrittore {#subscriber-tracking}

Potete tenere traccia delle modifiche apportate alle iscrizioni ai servizi di informazione utilizzando il collegamento **[!UICONTROL Reports]** nel dashboard.

![](assets/s_ncs_user_services_report.png)
