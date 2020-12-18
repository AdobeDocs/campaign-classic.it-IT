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

* Destinatari memorizzati nel database Campaign v7 e sincronizzati con i Campaign Standard. Fare riferimento alla sezione [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md).
* un servizio e un&#39;applicazione Web creati e pubblicati in Campaign v7.
* l&#39;applicazione Web deve contenere un&#39;attività **[!UICONTROL Pre-loading]** utilizzando il metodo di identificazione **[!UICONTROL Adobe Campaign encryption]**.

## Creazione dell&#39;applicazione Web e del servizio {#creating-the-web-application-and-service}

In Campaign v7, potete creare applicazioni Web che consentano ai destinatari di iscriversi a un servizio. L’applicazione e il servizio Web sono progettati e memorizzati in Campaign v7 e potete aggiornare il servizio tramite una comunicazione Campaign Standard. Per ulteriori informazioni sulle applicazioni Web in Campaign v7, consultare [questa sezione](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

In Campaign v7 sono stati creati i seguenti oggetti:

* un servizio newsletter
* un&#39;applicazione Web contenente un&#39;attività **[!UICONTROL Pre-loading]**, **[!UICONTROL Page]** e **[!UICONTROL Storage]**.

1. Vai a **[!UICONTROL Resources > Online > Web applications]** e seleziona un&#39;applicazione Web esistente.

   ![](assets/acs_connect_lp_2.png)

1. Modificate l&#39;attività **[!UICONTROL Preloading]**. La casella **[!UICONTROL Auto-load data referenced in the form]** è selezionata e il metodo di identificazione **[!UICONTROL Adobe Campaign encryption]** è selezionato. In questo modo l&#39;applicazione Web precarica i campi del modulo con i dati memorizzati nel database Adobe Campaign . Vedere [questo documento](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Modificate la **[!UICONTROL Page]**. Sono stati inclusi tre campi (Nome, E-mail e Telefono), nonché una casella di controllo per invitare il destinatario a registrarsi a una newsletter (**[!UICONTROL Newsletter]** servizio).

   ![](assets/acs_connect_lp_3.png)

1. Accedete a **[!UICONTROL Profiles and Target > Services and subscriptions]** e aprite il servizio **[!UICONTROL Newsletter]**. Questo è il servizio che verrà aggiornato dalla comunicazione Campaign Standard. È possibile che nessun destinatario abbia ancora effettuato la sottoscrizione a questo servizio.

   ![](assets/acs_connect_lp_5.png)

1. Vai a **[!UICONTROL Profiles and Targets > Recipient]** e seleziona un destinatario. Potete vedere che non ha ancora effettuato l’iscrizione al servizio.

   ![](assets/acs_connect_lp_6.png)

## Replica dei dati {#replicating-the-data}

Per replicare i dati necessari tra Campaign v7 e Campaign Standard, sono disponibili diversi modelli di flusso di lavoro di replica. Il flusso di lavoro **[!UICONTROL Profiles replication]** replica automaticamente tutti i destinatari di Campaign v7 in Campaign Standard. Vedere [Flussi di lavoro tecnici e di replica](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). Il flusso di lavoro **[!UICONTROL Landing pages replication]** consente la replica delle applicazioni Web che si desidera utilizzare nei Campaign Standard.

![](assets/acs_connect_lp_1.png)

Per verificare che i dati siano stati replicati correttamente, procedere come segue in Campaign Standard:

1. Dalla schermata principale, fare clic su **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Cercate il destinatario di Campaign v7 e verificate che sia visualizzato in Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. Dalla barra superiore, fate clic su **[!UICONTROL Marketing activities]** e cercate l&#39;applicazione Web Campaign v7. Viene visualizzata come una pagina di destinazione in Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Fare clic sul logo **[!UICONTROL Adobe Campaign]**, nell&#39;angolo in alto a sinistra, quindi selezionare **Profili e pubblico > Servizi** e verificare che sia presente anche il servizio newsletter.

   ![](assets/acs_connect_lp_10.png)

## Progettazione e invio dell&#39;e-mail {#designing-and-sending-the-email}

In questa parte verrà illustrato come includere un collegamento, in un messaggio e-mail Campaign Standard, alla pagina di destinazione replicata da un&#39;applicazione Web Campaign v7.

I passaggi per creare, progettare e inviare il messaggio e-mail sono gli stessi che per un messaggio e-mail classico. Consulta la documentazione di [ Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=it).

1. Create un nuovo messaggio e-mail e scegliete uno o più profili replicati come audience.
1. Modificate il contenuto e inserite un elemento **[!UICONTROL Link to a landing page]**.

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

1. In Campaign v7, andate a **[!UICONTROL Profiles and Target > Services and subscriptions]** e aprite il servizio **[!UICONTROL Newsletter]**. Il destinatario viene ora visualizzato nell’elenco degli utenti iscritti.

   ![](assets/acs_connect_lp_16.png)

1. Vai a **[!UICONTROL Profiles and Targets > Recipient]** e seleziona il destinatario. Ora è possibile vedere che il numero di telefono è memorizzato.

   ![](assets/acs_connect_lp_17.png)

1. Nella scheda **[!UICONTROL Subscriptions]** è inoltre possibile vedere che ha effettuato l’iscrizione al servizio newsletter.

   ![](assets/acs_connect_lp_18.png)

1. Attendere alcuni minuti per l&#39;esecuzione del flusso di lavoro di replica del profilo.
1. In Campaign Standard, accedi al profilo del destinatario per verificare che i dati aggiornati siano stati replicati correttamente da Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Modificate il profilo. Il numero di telefono è stato aggiornato.

   ![](assets/acs_connect_lp_20.png)

1. Fare clic sulla scheda **[!UICONTROL Subscriptions]**. Viene ora visualizzato il servizio newsletter.

   ![](assets/acs_connect_lp_21.png)

