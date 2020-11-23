---
solution: Campaign Classic
product: campaign
title: Sincronizzazione delle applicazioni web
description: Sincronizzazione delle applicazioni web
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 1%

---


# Sincronizzazione delle applicazioni web{#synchronizing-web-applications}

In questo caso di utilizzo, invieremo una comunicazione, utilizzando Campaign Standard, che include un collegamento a un&#39;applicazione Web Campaign v7. Quando il destinatario fa clic sul collegamento nell&#39;e-mail, l&#39;applicazione Web visualizza un modulo contenente diversi campi precaricati con i dati del destinatario e un collegamento di iscrizione a una newsletter. Il destinatario può aggiornare i propri dati e abbonarsi al servizio. Il suo profilo verrà aggiornato in Campaign v7 e le informazioni verranno replicate in Campaign Standard.

Se disponete di molti servizi e applicazioni Web in Campaign v7, potete scegliere di non ricrearli tutti in Campaign Standard. ACS Connector consente di utilizzare tutte le applicazioni e i servizi Web di Campaign v7 esistenti e di collegarli a una consegna inviata dal Campaign Standard.

## Prerequisiti {#prerequisites}

A tal fine, è necessario:

* Destinatari memorizzati nel database Campaign v7 e sincronizzati con i Campaign Standard. Fare riferimento alla sezione [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md) .
* un servizio e un&#39;applicazione Web creati e pubblicati in Campaign v7.
* l&#39;applicazione Web deve contenere un&#39; **[!UICONTROL Pre-loading]** attività che utilizza il metodo di **[!UICONTROL Adobe Campaign encryption]** identificazione.

## Creazione dell’applicazione e del servizio Web {#creating-the-web-application-and-service}

In Campaign v7, potete creare applicazioni Web che consentano ai destinatari di iscriversi a un servizio. L’applicazione e il servizio Web sono progettati e memorizzati in Campaign v7 e potete aggiornare il servizio tramite una comunicazione Campaign Standard. Per ulteriori informazioni sulle applicazioni Web in Campaign v7, consulta [questa sezione](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

In Campaign v7 sono stati creati i seguenti oggetti:

* un servizio newsletter
* un&#39;applicazione Web contenente un&#39; **[!UICONTROL Pre-loading]**, una **[!UICONTROL Page]** e un&#39; **[!UICONTROL Storage]** attività.

1. Passate a **[!UICONTROL Resources > Online > Web applications]** e selezionate un&#39;applicazione Web esistente.

   ![](assets/acs_connect_lp_2.png)

1. Modificate l&#39; **[!UICONTROL Preloading]** attività. La **[!UICONTROL Auto-load data referenced in the form]** casella è selezionata e il metodo di **[!UICONTROL Adobe Campaign encryption]** identificazione è selezionato. In questo modo l&#39;applicazione Web precarica i campi del modulo con i dati memorizzati nel database Adobe Campaign . Vedere [questo documento](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Modificate il **[!UICONTROL Page]**. Sono stati inclusi tre campi (Nome, E-mail e Telefono), nonché una casella di controllo per invitare il destinatario a registrarsi a una newsletter (**[!UICONTROL Newsletter]** servizio).

   ![](assets/acs_connect_lp_3.png)

1. Accedete a **[!UICONTROL Profiles and Target > Services and subscriptions]** e aprite il **[!UICONTROL Newsletter]** servizio. Questo è il servizio che verrà aggiornato dalla comunicazione Campaign Standard. È possibile che nessun destinatario abbia ancora effettuato la sottoscrizione a questo servizio.

   ![](assets/acs_connect_lp_5.png)

1. Vai a **[!UICONTROL Profiles and Targets > Recipient]** e seleziona un destinatario. Potete vedere che non ha ancora effettuato l’iscrizione al servizio.

   ![](assets/acs_connect_lp_6.png)

## Replica dei dati {#replicating-the-data}

Per replicare i dati necessari tra Campaign v7 e Campaign Standard, sono disponibili diversi modelli di flusso di lavoro di replica. Il **[!UICONTROL Profiles replication]** flusso di lavoro replica automaticamente tutti i destinatari di Campaign v7 in Campaign Standard. Consultate Flussi di lavoro [](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows)tecnici e di replica. Il **[!UICONTROL Landing pages replication]** flusso di lavoro consente la replica delle applicazioni Web che si desidera utilizzare in Campaign Standard.

![](assets/acs_connect_lp_1.png)

Per verificare che i dati siano stati replicati correttamente, procedere come segue in Campaign Standard:

1. Dalla schermata principale, fate clic su **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Cercate il destinatario di Campaign v7 e verificate che sia visualizzato in Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. Dalla barra superiore, fate clic su **[!UICONTROL Marketing activities]** e cercate l&#39;applicazione Web Campaign v7. Viene visualizzata come una pagina di destinazione in Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Fate clic sul **[!UICONTROL Adobe Campaign]** logo, nell’angolo in alto a sinistra, quindi selezionate **Profili e pubblico > Servizi** e verificate che sia presente anche il servizio newsletter.

   ![](assets/acs_connect_lp_10.png)

## Progettazione e invio del messaggio e-mail {#designing-and-sending-the-email}

In questa parte verrà illustrato come includere un collegamento, in un messaggio e-mail Campaign Standard, alla pagina di destinazione replicata da un&#39;applicazione Web Campaign v7.

I passaggi per creare, progettare e inviare il messaggio e-mail sono gli stessi che per un messaggio e-mail classico. Consultate la documentazione di [Adobe Campaign Standard](https://helpx.adobe.com/support/campaign/standard.html) .

1. Create un nuovo messaggio e-mail e scegliete uno o più profili replicati come audience.
1. Modificate il contenuto e inserite un **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Selezionate la pagina di destinazione replicata dall’applicazione Web Campaign v7.

   ![](assets/acs_connect_lp_13.png)

1. Preparate l&#39;e-mail, inviate le prove e l&#39;e-mail finale.
1. Uno dei destinatari apre l’e-mail e fa clic sul collegamento all’iscrizione alla newsletter.

   ![](assets/acs_connect_lp_14.png)

1. Aggiunge un numero di telefono e seleziona la casella di iscrizione alla newsletter.

   ![](assets/acs_connect_lp_15.png)

## Recupero delle informazioni aggiornate {#retrieving-the-updated-information}

Quando il destinatario aggiorna i dati dall’applicazione Web,  Adobe Campaign v7 recupera in modo sincrono le informazioni aggiornate. Viene quindi replicato da Campaign v7 a Campaign Standard.

1. In Campaign v7, accedete a **[!UICONTROL Profiles and Target > Services and subscriptions]** e aprite il **[!UICONTROL Newsletter]** servizio. Il destinatario viene ora visualizzato nell’elenco degli utenti iscritti.

   ![](assets/acs_connect_lp_16.png)

1. Vai a **[!UICONTROL Profiles and Targets > Recipient]** e seleziona il destinatario. Ora è possibile vedere che il numero di telefono è memorizzato.

   ![](assets/acs_connect_lp_17.png)

1. Nella **[!UICONTROL Subscriptions]** scheda è inoltre possibile vedere che si è iscritto al servizio newsletter.

   ![](assets/acs_connect_lp_18.png)

1. Attendere alcuni minuti per l&#39;esecuzione del flusso di lavoro di replica del profilo.
1. In Campaign Standard, accedi al profilo del destinatario per verificare che i dati aggiornati siano stati replicati correttamente da Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Modificate il profilo. Il numero di telefono è stato aggiornato.

   ![](assets/acs_connect_lp_20.png)

1. Click on the **[!UICONTROL Subscriptions]** tab. Viene ora visualizzato il servizio newsletter.

   ![](assets/acs_connect_lp_21.png)

