---
product: campaign
title: Sincronizzazione delle applicazioni web
description: Sincronizzazione delle applicazioni web
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# Sincronizzazione delle applicazioni web{#synchronizing-web-applications}

![](../../assets/v7-only.svg)

In questo caso d’uso, invieremo una comunicazione, utilizzando Campaign Standard, che include un collegamento a un’applicazione web Campaign v7. Quando il destinatario fa clic sul collegamento nell’e-mail, l’applicazione Web visualizza un modulo contenente diversi campi precaricati con i dati del destinatario e un collegamento di abbonamento a una newsletter. Il destinatario può aggiornare i propri dati e iscriversi al servizio. Il suo profilo verrà aggiornato in Campaign v7 e le informazioni saranno replicate in Campaign Standard.

Se in Campaign v7 sono presenti molti servizi e applicazioni web, puoi scegliere di non ricrearli tutti in Campaign Standard. Il connettore ACS consente di utilizzare tutte le applicazioni e i servizi Web esistenti di Campaign v7 e di collegarli a una consegna inviata da Campaign Standard.

## Prerequisiti {#prerequisites}

A questo scopo, è necessario:

* Destinatari memorizzati nel database Campaign v7 e sincronizzati con Campaign Standard. Fai riferimento a [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md) sezione .
* un servizio e un’applicazione web creati e pubblicati in Campaign v7.
* l&#39;applicazione web deve contenere **[!UICONTROL Pre-loading]** utilizzando **[!UICONTROL Adobe Campaign encryption]** metodo di identificazione.

## Creazione dell&#39;applicazione e del servizio Web {#creating-the-web-application-and-service}

In Campaign v7, puoi creare applicazioni web che consentono ai destinatari di abbonarsi a un servizio. L’applicazione web e il servizio sono progettati e memorizzati in Campaign v7 e puoi aggiornare il servizio tramite una comunicazione Campaign Standard. Per ulteriori informazioni sulle applicazioni web in Campaign v7, consulta [questa sezione](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

In Campaign v7, sono stati creati i seguenti oggetti:

* un servizio di newsletter
* un&#39;applicazione web contenente **[!UICONTROL Pre-loading]**, **[!UICONTROL Page]** e **[!UICONTROL Storage]** attività.

1. Vai a **[!UICONTROL Resources > Online > Web applications]** e selezionare un&#39;applicazione web esistente.

   ![](assets/acs_connect_lp_2.png)

1. Modifica le **[!UICONTROL Preloading]** attività. La **[!UICONTROL Auto-load data referenced in the form]** è selezionato e il **[!UICONTROL Adobe Campaign encryption]** metodo di identificazione selezionato. In questo modo l’applicazione Web precarica i campi del modulo con i dati memorizzati nel database di Adobe Campaign. Vedi [presente documento](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Modifica le **[!UICONTROL Page]**. Sono stati inclusi tre campi (Nome, E-mail e Telefono), nonché una casella di controllo per invitare il destinatario a registrarsi a una newsletter (**[!UICONTROL Newsletter]** servizio).

   ![](assets/acs_connect_lp_3.png)

1. Vai a **[!UICONTROL Profiles and Target > Services and subscriptions]** e aprire **[!UICONTROL Newsletter]** servizio. Questo è il servizio che verrà aggiornato dalla comunicazione Campaign Standard. È possibile vedere che nessun destinatario ha ancora effettuato la sottoscrizione a questo servizio.

   ![](assets/acs_connect_lp_5.png)

1. Vai a **[!UICONTROL Profiles and Targets > Recipient]** e seleziona un destinatario. Puoi vedere che questo profilo non si è ancora iscritto al servizio.

   ![](assets/acs_connect_lp_6.png)

## Replica dei dati {#replicating-the-data}

Per replicare i dati necessari tra Campaign v7 e Campaign Standard, sono disponibili diversi modelli di flusso di lavoro di replica. La **[!UICONTROL Profiles replication]** il flusso di lavoro replica automaticamente tutti i destinatari di Campaign v7 in Campaign Standard. Vedi [Flussi di lavoro tecnici e di replica](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). La **[!UICONTROL Landing pages replication]** il flusso di lavoro consente la replica delle applicazioni web che si desidera utilizzare in Campaign Standard.

![](assets/acs_connect_lp_1.png)

Per verificare che i dati siano stati replicati correttamente, segui questi passaggi in Campaign Standard:

1. Dalla schermata iniziale, fai clic su **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Cerca il destinatario di Campaign v7 e verifica che questo destinatario sia presente in Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. Dalla barra superiore, fai clic su **[!UICONTROL Marketing activities]**, e cerca l’applicazione web Campaign v7. Viene visualizzata come pagina di destinazione in Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Fai clic sul pulsante **[!UICONTROL Adobe Campaign]** , nell&#39;angolo in alto a sinistra, quindi seleziona **Profili e pubblico > Servizi** e controlla che sia presente anche il servizio newsletter.

   ![](assets/acs_connect_lp_10.png)

## Progettazione e invio dell’e-mail {#designing-and-sending-the-email}

In questa parte, vedremo come includere un collegamento, in un’e-mail di Campaign Standard, alla pagina di destinazione replicata da un’applicazione web Campaign v7.

I passaggi per creare, progettare e inviare l’e-mail sono gli stessi che per un’e-mail classica. Consulta la sezione [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it) documentazione.

1. Crea un nuovo messaggio e-mail e scegli uno o più profili replicati come pubblico.
1. Modificare il contenuto e inserire un **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Seleziona la pagina di destinazione replicata dall’applicazione web Campaign v7.

   ![](assets/acs_connect_lp_13.png)

1. Prepara l’e-mail, invia le bozze e invia l’e-mail finale.
1. Uno dei destinatari apre l’e-mail e fa clic sul collegamento all’abbonamento alla newsletter.

   ![](assets/acs_connect_lp_14.png)

1. Il destinatario aggiunge un numero di telefono e controlla la casella di abbonamento alla newsletter.

   ![](assets/acs_connect_lp_15.png)

## Recupero delle informazioni aggiornate {#retrieving-the-updated-information}

Quando il destinatario aggiorna i propri dati da tramite l’applicazione web, Adobe Campaign v7 recupera in modo sincrono le informazioni aggiornate. Viene quindi replicato da Campaign v7 a Campaign Standard.

1. In Campaign v7, vai a **[!UICONTROL Profiles and Target > Services and subscriptions]** e aprire **[!UICONTROL Newsletter]** servizio. Ora il destinatario viene visualizzato nell’elenco degli abbonati.

   ![](assets/acs_connect_lp_16.png)

1. Vai a **[!UICONTROL Profiles and Targets > Recipient]** e selezionare il destinatario. Il numero di telefono è ora memorizzato.

   ![](assets/acs_connect_lp_17.png)

1. In **[!UICONTROL Subscriptions]** è inoltre possibile vedere che il destinatario si è iscritto al servizio newsletter.

   ![](assets/acs_connect_lp_18.png)

1. Attendi alcuni minuti per l’esecuzione del flusso di lavoro di replica del profilo.
1. In Campaign Standard, accedi al tuo profilo destinatario per verificare che i dati aggiornati siano stati replicati correttamente da Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Modifica il profilo. Il numero di telefono è stato aggiornato.

   ![](assets/acs_connect_lp_20.png)

1. Fai clic sul pulsante **[!UICONTROL Subscriptions]** scheda . Viene visualizzato il servizio newsletter.

   ![](assets/acs_connect_lp_21.png)
