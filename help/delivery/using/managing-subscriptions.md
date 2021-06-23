---
product: campaign
title: Gestione degli abbonamenti
description: Gestione degli abbonamenti
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 2%

---

# Gestione degli abbonamenti{#managing-subscriptions}

## Informazioni sui servizi di informazione {#about-information-services}

Un servizio d&#39;informazione comprende:

* Registrazione e abbonamento (opt-in),
* Cancellazione, annullamento volontario dell’abbonamento (opt-out) o annullamento automatico dell’abbonamento (servizio a tempo limitato, ad esempio un’offerta di prova),
* Meccanismi di conferma dell’abbonamento e del suo annullamento (meccanismi semplici con conferma, doppio consenso, ecc.),
* Tracciamento della cronologia degli abbonati.

In linea di massima, questi servizi comprendono rapporti statistici specifici: tracciamento degli abbonati, livello di fedeltà, tendenze di annullamento dell’abbonamento, ecc.

Per le e-mail, i collegamenti di annullamento dell’abbonamento obbligatori vengono generati automaticamente e l’intero processo di consenso/rinuncia è completamente automatizzato, con tracciamento della cronologia per garantire la piena conformità alle normative in vigore.

Sono disponibili tre modalità di abbonamento/annullamento dell’abbonamento al servizio:

1. manuale
1. importando (solo abbonamento),
1. tramite un modulo web

>[!NOTE]
>
>Un esempio per creare un modulo di abbonamento con doppio consenso è descritto in [questa sezione](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## Creazione di un servizio informazioni {#creating-an-information-service}

Puoi creare e gestire abbonamenti a servizi di informazione con messaggi di conferma associati o consegne automatiche agli abbonati.

Per accedere alla mappa dei servizi di informazione, apri la scheda **[!UICONTROL Profiles and Targets]** e fai clic sul collegamento **[!UICONTROL Services and Subscriptions]** .

![](assets/s_ncs_user_services_new.png)

Per modificare un servizio esistente, fai clic sul suo nome. Per creare un servizio, fai clic sul pulsante **[!UICONTROL Create]** situato sopra l’elenco.

![](assets/s_ncs_user_services_add.png)

* Immetti il nome del servizio nel campo **[!UICONTROL Label]** e seleziona il canale di consegna: e-mail, dispositivi mobili, Facebook, Twitter o applicazioni mobili.

   >[!NOTE]
   >
   >Gli abbonamenti a facebook e Twitter sono descritti in [questa sezione](../../social/using/about-social-marketing.md). Gli abbonamenti alle applicazioni mobili sono descritti in [Informazioni sul canale app mobile](about-mobile-app-channel.md).

* Per un servizio di tipo Email, seleziona la **Modalità di consegna**. Le modalità possibili sono: **[!UICONTROL Newsletter]** o **[!UICONTROL Viral]**.
* Puoi inviare **messaggi di conferma** per un abbonamento o il suo annullamento. A questo scopo, seleziona i modelli di consegna da utilizzare per creare le consegne corrispondenti dai campi **[!UICONTROL Subscription]** e **[!UICONTROL Unsubscription]** . Questi modelli devono essere configurati con una mappatura di destinazione di tipo **[!UICONTROL Subscription]**, senza un target definito. Consulta la sezione [Informazioni sul canale e-mail](about-email-channel.md).
* Per impostazione predefinita, gli abbonamenti sono illimitati. Puoi deselezionare l’opzione **[!UICONTROL Unlimited]** per definire una durata di validità per il servizio. La durata può essere specificata in giorni (**[!UICONTROL d]** ) o mesi (**[!UICONTROL m]** ).

Una volta salvato, il servizio viene aggiunto all’elenco Servizi e iscrizioni: Fare clic sul nome per modificarlo. Sono disponibili diverse schede. La scheda **[!UICONTROL Subscriptions]** ti consente di visualizzare l’elenco degli abbonati al servizio informazioni (**[!UICONTROL Active subscriptions]** scheda ) o la cronologia dell’abbonamento o del suo annullamento (**[!UICONTROL History]** scheda ). Puoi anche aggiungere ed eliminare gli abbonati da questa scheda. Consulta [Aggiunta ed eliminazione di abbonati](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Il pulsante **[!UICONTROL Detail...]** ti consente di esaminare le proprietà dell’abbonamento per il destinatario selezionato.

Puoi modificare le proprietà dell’abbonamento per un destinatario.

![](assets/s_ncs_user_services_modify.png)

Nel dashboard, fai clic sulla scheda **[!UICONTROL Reports]** per tenere traccia delle sottoscrizioni: modifiche dei livelli di abbonamento, numero totale di abbonati, ecc. È possibile archiviare i rapporti e esaminare la cronologia da questa scheda.

## Aggiunta ed eliminazione di abbonati {#adding-and-deleting-subscribers}

Dalla scheda **[!UICONTROL Subscriptions]** di un servizio informazioni, fai clic su **[!UICONTROL Add]** per aggiungere abbonati. Puoi anche fare clic con il pulsante destro del mouse sull’elenco degli abbonati e selezionare **[!UICONTROL Add]**. Seleziona la cartella in cui sono memorizzati i profili da sottoscrivere, quindi seleziona i profili da sottoscrivere e fai clic su **[!UICONTROL OK]** per eseguire la convalida.

Per eliminare gli abbonati, selezionali e fai clic su **[!UICONTROL Delete]**. Puoi anche fare clic con il pulsante destro del mouse sull’elenco degli abbonati e selezionare **[!UICONTROL Delete]**.

In entrambi i casi, puoi inviare un messaggio di conferma agli utenti interessati se è stato allegato al servizio un modello di consegna per gli annullamenti di abbonamenti (consulta [Creazione di un servizio di informazioni](#creating-an-information-service)). Un avviso consente di convalidare o meno questa consegna:

![](assets/s_ncs_user_services_update.png)

Consulta [Meccanismi di abbonamento e annullamento dell’abbonamento](#subscription-and-unsubscription-mechanisms).

## Consegna agli abbonati di un servizio {#delivering-to-the-subscribers-of-a-service}

Per fornire agli abbonati di un servizio di informazione, è possibile indirizzare gli abbonati al servizio di informazione interessato, come nell&#39;esempio seguente:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>La mappatura della destinazione deve essere **[!UICONTROL Subscriptions]**.

Seleziona **[!UICONTROL Subscribers of an information service]** e fai clic su **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Seleziona il servizio di informazioni di destinazione e fai clic su **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

La scheda **[!UICONTROL Preview]** ti consente di visualizzare l’elenco dei sottoscrittori del servizio informazioni selezionato.

## Meccanismi di abbonamento e di annullamento dell’abbonamento {#subscription-and-unsubscription-mechanisms}

Puoi impostare meccanismi di abbonamento e annullamento dell’abbonamento per automatizzare i processi e la gestione degli abbonati.

>[!NOTE]
>
>Puoi inviare un messaggio di conferma ai nuovi abbonati.\
>Il contenuto di questo messaggio viene definito nella configurazione del servizio informazioni tramite i campi **[!UICONTROL Subscription]** o **[!UICONTROL Unsubscription]** .
>
>I messaggi di conferma vengono creati tramite i modelli di consegna specificati in questi campi. Queste mappature di destinazione devono essere **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Iscrizione di un destinatario a un servizio {#subscribing-a-recipient-to-a-service}

Per registrare i destinatari per un servizio di informazione, puoi:

* Aggiungi manualmente il servizio: a questo scopo, dalla scheda **[!UICONTROL Subscriptions]** del profilo, fai clic su **[!UICONTROL Add]** e seleziona il servizio informazioni interessato.

   Per ulteriori informazioni, consulta la sezione sulla modifica del profilo in [questa sezione](../../platform/using/editing-a-profile.md).

* Iscriviti automaticamente un set di destinatari a questo servizio. L’elenco dei destinatari può provenire da un’operazione di filtro, un gruppo, una cartella, un’importazione o una selezione diretta tramite il mouse. Per sottoscrivere questi destinatari, seleziona i profili e fai clic con il pulsante destro del mouse su di essi. Selezionare **[!UICONTROL Actions > Subscribe selection to a service...]**, selezionare il servizio interessato e avviare l&#39;operazione.
* Importa i destinatari e abbonali automaticamente a un servizio di informazioni. A questo scopo, seleziona il servizio interessato nell’ultimo passaggio della procedura guidata di importazione.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/executing-import-jobs.md).

* Utilizza un modulo web per consentire ai destinatari di iscriversi a un servizio.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/about-web-applications.md).

* Creazione di un flusso di lavoro di targeting e utilizzo di una casella **[!UICONTROL Subscription service]**.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   I flussi di lavoro e le relative modalità di utilizzo sono descritti in [questa sezione](../../workflow/using/about-workflows.md).

### Annullamento dell’iscrizione di un destinatario da un servizio {#unsubscribing-a-recipient-from-a-service}

#### Annullamento manuale dell’abbonamento {#manual-unsubscribing}

Le consegne e-mail devono contenere un collegamento di annullamento dell’abbonamento, per legge. I destinatari possono fare clic su questo collegamento per aggiornare il proprio profilo ed essere esclusi dagli obiettivi delle consegne future.

Il collegamento di annullamento dell’abbonamento predefinito viene inserito tramite l’ultimo pulsante nella barra degli strumenti dell’editor di contenuti fornito nella procedura guidata di consegna (consulta [Informazioni sulla personalizzazione](about-personalization.md)). Quando il destinatario fa clic su questo collegamento, il profilo viene aggiunto al  di elenco Bloccati (rinuncia), il che significa che il destinatario non sarà più oggetto di targeting da parte di alcuna azione di consegna.

Tuttavia, i destinatari possono scegliere di annullare l’iscrizione a un servizio senza annullare l’iscrizione a tutti i servizi. Per fare ciò, puoi utilizzare un modulo web (consulta [questa sezione](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) o inserire un collegamento di annullamento dell’abbonamento personalizzato (consulta [Blocchi di personalizzazione](personalization-blocks.md)).

Puoi anche annullare manualmente l’iscrizione di un destinatario dal profilo del destinatario. A questo scopo, fare clic sulla scheda **[!UICONTROL Subscriptions]** del destinatario interessato, selezionare i servizi di informazione interessati e fare clic su **[!UICONTROL Delete]**.

È infine possibile annullare l’iscrizione di uno o più destinatari tramite il servizio di informazione interessato. A questo scopo, fai clic sulla scheda **[!UICONTROL Subscriptions]** del servizio, seleziona i destinatari interessati e fai clic su **[!UICONTROL Delete]**.

#### Annullamento automatico della sottoscrizione {#automatic-unsubscription}

Un servizio di informazione può avere una durata limitata. I destinatari verranno automaticamente annullati alla scadenza del periodo di validità. Questo periodo è specificato nella scheda **[!UICONTROL Edit]** delle proprietà del servizio. Viene espresso in giorni.

![](assets/s_ncs_user_services_delay.png)

Puoi anche impostare un flusso di lavoro di annullamento dell’abbonamento per una popolazione. A questo scopo, segui la stessa procedura utilizzata per un flusso di lavoro di abbonamento, ma seleziona l’opzione **[!UICONTROL Unsubscription]** . Consulta [Iscrizione di un destinatario a un servizio](#subscribing-a-recipient-to-a-service).

### Tracciamento dei sottoscrittori {#subscriber-tracking}

Puoi tenere traccia delle modifiche negli abbonamenti ai servizi di informazione utilizzando il collegamento **[!UICONTROL Reports]** nel dashboard.

![](assets/s_ncs_user_services_report.png)
