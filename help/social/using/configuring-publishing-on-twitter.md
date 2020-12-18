---
solution: Campaign Classic
product: campaign
title: Configurazione della pubblicazione su Twitter
description: Configurazione della pubblicazione su Twitter
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 2%

---


# Configurazione della pubblicazione su Twitter{#configuring-publishing-on-twitter}

Affinché  Adobe Campaign possa inviare tweet ai vostri account Twitter, dovete delegare l&#39;accesso in scrittura a  Adobe Campaign per questi account. A tal fine, eseguite i seguenti passaggi di configurazione:

* Create un account Twitter.
* Create un account Twitter di prova per l&#39;invio delle prove di stampa.
* Create un&#39;applicazione Twitter per account Twitter.
* Per ogni applicazione Twitter, create un nuovo servizio di tipo **[!UICONTROL Twitter]**.

![](assets/social_diagram_twitter_service.png)

## Prerequisiti {#prerequisites}

Per iniziare, create uno o più account Twitter a cui inviare i tweet.

Per creare un account Twitter, andate a [https://twitter.com](https://twitter.com).

## Creazione di un account di prova su Twitter {#creating-a-test-account-on-twitter}

È inoltre consigliabile creare un account Twitter privato che possa essere utilizzato per inviare le prove su Twitter (per ulteriori informazioni, vedere [Invio delle prove](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Create un nuovo account Twitter.
* Fare clic sul menu nell&#39;angolo superiore destro e selezionare **[!UICONTROL Settings]**.
* Selezionare la scheda **[!UICONTROL Security and privacy]** e selezionare la casella **[!UICONTROL Protect my Tweets]**.
* Fate clic sul pulsante **[!UICONTROL Save Changes]** nella parte inferiore della pagina.

![](assets/social_twitter_test_page.png)

## Creazione di un&#39;applicazione su Twitter {#creating-an-application-on-twitter}

Affinché  Adobe Campaign possa inviare tweet ai vostri account Twitter, è necessario creare un&#39;applicazione Twitter per account Twitter. A questo scopo, eseguire i seguenti passaggi:

1. Accedete al vostro account Twitter.
1. Inserite il seguente indirizzo nel browser Internet: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Fate clic sul pulsante **[!UICONTROL Create New App]** a destra.

   ![](assets/social_create_twitter_app_001.png)

1. Consentono alla procedura guidata di seguire il processo.

   Per consentire a questa applicazione di  Adobe Campaign di inviare tweet al tuo account, vai alla scheda **[!UICONTROL Permissions]** dell&#39;applicazione e seleziona **[!UICONTROL Read and Write]** per la sezione **[!UICONTROL Access]**. Nella scheda **[!UICONTROL Settings]** è inoltre necessario lasciare vuoto il campo **[!UICONTROL Callback URL]**.

   ![](assets/social_create_twitter_app_002.png)

## Delega dell&#39;accesso in scrittura a  Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Per ogni applicazione Twitter, è necessario creare un servizio di tipo **[!UICONTROL Twitter]** diverso che includerà le impostazioni dell&#39;applicazione.

Questo passaggio richiede l’accesso simultaneo alla console  Adobe Campaign e a un browser Internet collegato al vostro account Twitter:

* **Twitter**: selezionate l’applicazione creata in precedenza ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) e fate clic sulla  **[!UICONTROL Keys and Access Tokens]** scheda.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: andare nell&#39; **[!UICONTROL Profiles and targets]** universo, fare clic sul  **[!UICONTROL Services and Subscriptions]** collegamento e fare clic sul  **[!UICONTROL Create]** pulsante.

   ![](assets/social_twitter_service_007.png)

1. Selezionare il tipo **[!UICONTROL Twitter]**.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >L&#39;opzione **[!UICONTROL Synchronize subscriptions]** è abilitata per impostazione predefinita. Quando la casella è selezionata, il flusso di lavoro di sincronizzazione dell&#39;account Twitter (fare riferimento a [Sincronizzazione degli account Twitter](#synchronizing-twitter-accounts)) recupera l&#39;elenco dei follower Twitter in modo da poter inviare loro messaggi diretti (fare riferimento a [Invio di messaggi diretti agli abbonati](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Se non si desidera recuperare l&#39;elenco dei follower, deselezionare questa casella.

1. Immettete l’etichetta e il nome interno del servizio.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >La **[!UICONTROL Internal name]** del servizio deve essere identica al nome dell&#39;account Twitter. Per essere certi che non si verifichino errori di immissione, attenetevi alla seguente procedura.

   * Fai clic sul pulsante **[!UICONTROL Save]**.
   * Nella panoramica dei servizi, fai clic sul servizio Twitter appena creato.
   * Seleziona la scheda **[!UICONTROL Twitter page]**. L&#39;account Twitter deve essere visualizzato.

      ![](assets/social_twitter_service_010.png)

1. Nel campo **[!UICONTROL Visitor folder]**, selezionate la cartella del visitatore in cui verranno creati i follower. Per ulteriori informazioni, fare riferimento a [Principio operativo](../../social/using/publishing-on-twitter.md#operating-principle). Per impostazione predefinita, i follower vengono creati nella directory principale della cartella **[!UICONTROL Visitors]**.

   ![](assets/social_twitter_service_010_b.png)

1. Su Twitter, copiate il contenuto dei campi **[!UICONTROL Consumer Key (API Key)]** e **[!UICONTROL Consumer Secret (API Secret)]** e incollatelo nei campi **[!UICONTROL Consumer key]** e **[!UICONTROL Consumer secret]** della console.

   ![](assets/social_twitter_service_012.png)

1. Su Twitter, copiate il contenuto dei campi **[!UICONTROL Access Token]** e **[!UICONTROL Access Token Secret]** e incollatelo nei campi **[!UICONTROL Access token]** e **[!UICONTROL Access token secret]** della console.

   ![](assets/social_twitter_service_013.png)

1. Nella console Adobe Campaign , fate clic su **[!UICONTROL Save]**. La delega dell&#39;accesso in scrittura a  Adobe Campaign è ora completa.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>È necessario creare un servizio di tipo **[!UICONTROL Twitter]** per ogni applicazione Twitter.

Il flusso di lavoro **[!UICONTROL Twitter account Synchronization]** sincronizza gli account Twitter in  Adobe Campaign. Per ulteriori informazioni, vedere [Sincronizzazione delle pagine Facebook](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Sincronizzazione degli account Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Affinché il flusso di lavoro possa recuperare l&#39;elenco degli utenti Twitter iscritti, la casella **[!UICONTROL Twitter account synchronization]** deve essere selezionata nella sezione di modifica del servizio collegato all&#39;account. Per ulteriori informazioni, vedere [Delegazione dell&#39;accesso in scrittura a  Adobe Campaign](#delegating-write-access-to-adobe-campaign).

Il flusso di lavoro **[!UICONTROL Twitter account synchronization]**, a cui si accede tramite il nodo **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, consente di sincronizzare gli account Twitter configurati in precedenza con  Adobe Campaign. Per impostazione predefinita, questo flusso di lavoro viene attivato ogni giovedì alle 7:30.

>[!NOTE]
>
>È possibile avviare il flusso di lavoro in qualsiasi momento eseguendo l&#39;elaborazione dell&#39;attività prevista. Potete inoltre modificare il pianificatore per modificare la frequenza di attivazione del flusso di lavoro. Per ulteriori informazioni sull&#39;utilità di pianificazione, consultare [questa sezione](../../workflow/using/scheduler.md).

Ora puoi inviare tweet ai tuoi account Twitter e messaggi diretti ai tuoi follower. Per ulteriori informazioni, consulta: [Pubblicazione su Twitter](../../social/using/publishing-on-twitter.md).
