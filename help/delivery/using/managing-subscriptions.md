---
product: campaign
title: Gestire le iscrizioni
description: Scopri come gestire gli abbonamenti in Adobe Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Subscriptions
role: User
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: 4d8c4ba846148d3df00a76ecc29375b9047c2b20
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 2%

---

# Gestire le iscrizioni{#managing-subscriptions}

## Informazioni sui servizi di informazione {#about-information-services}

Un servizio di informazione comprende:

* Registrazione e abbonamento (opt-in)
* annullamento della registrazione, annullamento volontario dell’abbonamento (opt out) o annullamento automatico dell’abbonamento (servizio a tempo limitato, ad esempio come offerta di prova),
* meccanismi di conferma dell’abbonamento e del suo annullamento (meccanismi semplici con conferma, doppio consenso, ecc.),
* Tracciamento della cronologia degli abbonati.

Come funzione standard, questi servizi includono rapporti statistici specifici: tracciamento degli abbonati, livello di fedeltà, tendenze di annullamento dell’abbonamento, ecc.

Per le e-mail, i collegamenti di annullamento dell’abbonamento obbligatori vengono generati automaticamente e l’intero processo di consenso/rinuncia viene completamente automatizzato, con tracciamento della cronologia per garantire la piena conformità alle normative in vigore.

Esistono tre modalità di abbonamento/annullamento abbonamento al servizio:

1. manuale
1. importando (solo abbonamento),
1. tramite un modulo web

>[!NOTE]
>
>Un esempio per creare un modulo di abbonamento con doppio consenso è descritto in [questa sezione](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

## Creazione di un servizio informazioni {#creating-an-information-service}

È possibile creare e gestire gli abbonamenti ai servizi di informazione con i messaggi di conferma associati o le consegne automatiche agli abbonati.

Per accedere alla mappa dei servizi informazioni, aprire la scheda **[!UICONTROL Profiles and Targets]** e fare clic sul collegamento **[!UICONTROL Services and Subscriptions]**.

![](assets/s_ncs_user_services_new.png)

Per modificare un servizio esistente, fare clic sul relativo nome. Per creare un servizio, fare clic sul pulsante **[!UICONTROL Create]** situato sopra l&#39;elenco.

![](assets/s_ncs_user_services_add.png)

* Immetti il nome del servizio nel campo **[!UICONTROL Label]** e seleziona il canale di consegna: e-mail, dispositivi mobili, Facebook, X (precedentemente noto come Twitter) o applicazioni mobili.

  >[!NOTE]
  >
  >Gli abbonamenti Facebook e X sono descritti in [questa sezione](../../social/using/about-social-marketing.md). Gli abbonamenti alle app mobili sono descritti in dettaglio in [Informazioni sul canale app mobile](about-mobile-app-channel.md).

* Per un servizio di tipo E-mail, seleziona la **Modalità di consegna**. Le modalità possibili sono: **[!UICONTROL Newsletter]** o **[!UICONTROL Viral]**.
* Puoi inviare **messaggi di conferma** per un abbonamento o per l&#39;annullamento dell&#39;abbonamento. A questo scopo, seleziona i modelli di consegna da utilizzare per creare le consegne corrispondenti dai campi **[!UICONTROL Subscription]** e **[!UICONTROL Unsubscription]**. Questi modelli devono essere configurati con una mappatura di destinazione di tipo **[!UICONTROL Subscription]**, senza una destinazione definita. Vedere la sezione [Informazioni sul canale e-mail](about-email-channel.md).
* Per impostazione predefinita, le iscrizioni hanno un periodo di validità illimitato. È possibile deselezionare l&#39;opzione **[!UICONTROL Unlimited]** per definire una durata di validità per il servizio. La durata può essere specificata in giorni (**[!UICONTROL d]** ) o mesi (**[!UICONTROL m]** ).

Una volta salvato, il servizio viene aggiunto all’elenco Servizi e abbonamenti: fai clic sul nome per modificarlo. Sono disponibili diverse schede. La scheda **[!UICONTROL Subscriptions]** consente di esaminare l&#39;elenco degli abbonati al servizio informazioni (**[!UICONTROL Active subscriptions]**) o la cronologia degli abbonamenti/annullamenti (scheda **[!UICONTROL History]**). Da questa scheda è inoltre possibile aggiungere ed eliminare sottoscrittori. Vedere [Aggiunta ed eliminazione di sottoscrittori](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Il pulsante **[!UICONTROL Detail...]** consente di esaminare le proprietà della sottoscrizione per il destinatario selezionato.

Puoi modificare le proprietà di abbonamento di un destinatario.

![](assets/s_ncs_user_services_modify.png)

Nel dashboard, fare clic sulla scheda **[!UICONTROL Reports]** per tenere traccia degli abbonamenti: modifiche ai livelli di abbonamento, numero totale di abbonati e così via. Da questa scheda è possibile archiviare i rapporti e esaminare le cronologie.

## Aggiunta ed eliminazione di abbonati {#adding-and-deleting-subscribers}

Dalla scheda **[!UICONTROL Subscriptions]** di un servizio informazioni, fare clic su **[!UICONTROL Add]** per aggiungere abbonati. È inoltre possibile fare clic con il pulsante destro del mouse sull&#39;elenco degli abbonati e selezionare **[!UICONTROL Add]**. Selezionare la cartella in cui sono archiviati i profili da sottoscrivere, quindi selezionare i profili da sottoscrivere e fare clic su **[!UICONTROL OK]** per confermare.

Per eliminare i sottoscrittori, selezionarli e fare clic su **[!UICONTROL Delete]**. È inoltre possibile fare clic con il pulsante destro del mouse sull&#39;elenco degli abbonati e selezionare **[!UICONTROL Delete]**.

In entrambi i casi, è possibile inviare un messaggio di conferma agli utenti interessati se al servizio è stato allegato un modello di consegna per l&#39;annullamento degli abbonamenti (vedere [Creazione di un servizio di informazioni](#creating-an-information-service)). Un avviso consente di convalidare o meno questa consegna:

![](assets/s_ncs_user_services_update.png)

Consulta [Meccanismi di abbonamento e annullamento dell&#39;abbonamento](#subscription-and-unsubscription-mechanisms).

## Fornitura agli abbonati di un servizio {#delivering-to-the-subscribers-of-a-service}

Per fornire agli abbonati a un servizio di informazioni, è possibile rivolgersi agli abbonati al servizio di informazioni interessato, come nell’esempio seguente:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>La mappatura di destinazione deve essere **[!UICONTROL Subscriptions]**.

Seleziona **[!UICONTROL Subscribers of an information service]** e fai clic su **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Selezionare il servizio informazioni di destinazione e fare clic su **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

La scheda **[!UICONTROL Preview]** consente di visualizzare l&#39;elenco degli abbonati al servizio informazioni selezionato.

## Meccanismi di abbonamento e di annullamento dell’abbonamento {#subscription-and-unsubscription-mechanisms}

Puoi impostare meccanismi di abbonamento e annullamento dell’abbonamento per automatizzare i processi e la gestione degli abbonati.

>[!NOTE]
>
>Puoi inviare un messaggio di conferma ai nuovi abbonati.\
>Il contenuto del messaggio è definito nella configurazione del servizio informazioni tramite i campi **[!UICONTROL Subscription]** o **[!UICONTROL Unsubscription]**.
>
>I messaggi di conferma vengono creati tramite i modelli di consegna specificati in questi campi. Queste mappature di destinazione devono essere **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Iscrizione di un destinatario a un servizio {#subscribing-a-recipient-to-a-service}

Per registrare i destinatari di un servizio informazioni, è possibile:

* Aggiungi manualmente il servizio: a questo scopo, dalla scheda **[!UICONTROL Subscriptions]** del profilo, fai clic su **[!UICONTROL Add]** e seleziona il servizio informazioni interessato.

* Iscrivi automaticamente un set di destinatari a questo servizio. L’elenco dei destinatari può provenire da un’operazione di filtro, un gruppo, una cartella, un’importazione o una selezione diretta effettuata con il mouse. Per sottoscrivere questi destinatari, seleziona i profili e fai clic con il pulsante destro del mouse. Selezionare **[!UICONTROL Actions > Subscribe selection to a service...]**, selezionare il servizio interessato e avviare l&#39;operazione.
* Importa i destinatari e abbonali automaticamente a un servizio di informazioni. A questo scopo, seleziona il servizio interessato nell’ultimo passaggio dell’assistente all’importazione.

  Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/executing-import-jobs.md).

* Utilizza un modulo web in modo che i destinatari possano abbonarsi a un servizio.

  Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/about-web-applications.md).

* Creazione di un flusso di lavoro di targeting e utilizzo di una casella **[!UICONTROL Subscription service]**.

  ![](assets/s_ncs_user_subscribe_from_wf.png)

  I flussi di lavoro e la relativa modalità di utilizzo sono descritti in [questa sezione](../../workflow/using/about-workflows.md).

### Annullamento dell’abbonamento di un destinatario da un servizio {#unsubscribing-a-recipient-from-a-service}

#### Annullamento manuale dell’abbonamento {#manual-unsubscribing}

le consegne e-mail devono contenere per legge un collegamento che consenta di annullare l’abbonamento. I destinatari possono fare clic su questo collegamento per aggiornare il loro profilo ed essere esclusi dai target delle consegne future.

Il collegamento predefinito per l&#39;annullamento dell&#39;iscrizione viene inserito tramite l&#39;ultimo pulsante nella barra degli strumenti dell&#39;editor di contenuti fornito nell&#39;assistente alla consegna (vedi [Informazioni sulla personalizzazione](about-personalization.md)). Quando il destinatario fa clic su questo collegamento, il profilo viene aggiunto al inserisco nell&#39;elenco Bloccati di consegna (opt-out), il che significa che il destinatario non sarà più interessato da alcuna azione di consegna.

I destinatari possono tuttavia scegliere di annullare l’abbonamento a un servizio senza annullare l’abbonamento a tutti i servizi. Per consentire questa operazione, puoi utilizzare un modulo web (fai riferimento a [questa sezione](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) o inserire un collegamento di annullamento dell&#39;abbonamento personalizzato (consulta [Blocchi di personalizzazione](personalization-blocks.md)).

Puoi anche annullare manualmente l’abbonamento di un destinatario dal profilo del destinatario. A tale scopo, fare clic sulla scheda **[!UICONTROL Subscriptions]** del destinatario interessato, selezionare i servizi di informazione interessati e fare clic su **[!UICONTROL Delete]**.

È infine possibile annullare l’abbonamento di uno o più destinatari tramite il servizio di informazioni interessato. A tale scopo, fare clic sulla scheda **[!UICONTROL Subscriptions]** del servizio, selezionare i destinatari interessati e fare clic su **[!UICONTROL Delete]**.

#### Annullamento automatico dell’iscrizione {#automatic-unsubscription}

Un servizio di informazione può avere una durata limitata. L’abbonamento dei destinatari verrà annullato automaticamente alla scadenza del periodo di validità. Questo periodo è specificato nella scheda **[!UICONTROL Edit]** delle proprietà del servizio. È espresso in giorni.

![](assets/s_ncs_user_services_delay.png)

Puoi anche impostare un flusso di lavoro di annullamento dell’abbonamento per una popolazione. A tale scopo, seguire la stessa procedura utilizzata per un flusso di lavoro di abbonamento, ma selezionare l&#39;opzione **[!UICONTROL Unsubscription]**. Vedere [Iscrizione di un destinatario a un servizio](#subscribing-a-recipient-to-a-service).

### Tracciamento degli abbonati {#subscriber-tracking}

È possibile tenere traccia delle modifiche apportate agli abbonamenti ai servizi informazioni utilizzando il collegamento **[!UICONTROL Reports]** nel dashboard.

![](assets/s_ncs_user_services_report.png)
