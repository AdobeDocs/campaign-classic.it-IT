---
solution: Campaign Classic
product: campaign
title: Configurazione della pubblicazione su Twitter
description: Configurazione della pubblicazione su Twitter
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 2%

---


# Configurazione della pubblicazione su Twitter{#configuring-publishing-on-twitter}

Affinché Adobe Campaign possa inviare tweet ai tuoi account Twitter, devi delegare l’accesso in scrittura ad Adobe Campaign per questi account. A questo scopo, applica i seguenti passaggi di configurazione:

* Crea un account Twitter.
* Crea un account Twitter di prova per l’invio di bozze.
* Crea un&#39;applicazione Twitter per account Twitter.
* Per ogni applicazione Twitter, crea un nuovo servizio di tipo **[!UICONTROL Twitter]**.

![](assets/social_diagram_twitter_service.png)

## Prerequisiti {#prerequisites}

Per iniziare, crea uno o più account Twitter a cui inviare i tweet.

Per creare un account Twitter, visita [https://twitter.com](https://twitter.com).

## Creazione di un account di prova su Twitter {#creating-a-test-account-on-twitter}

Consigliamo inoltre di creare un account Twitter privato che possa essere utilizzato per inviare bozze su Twitter (per ulteriori informazioni, consulta [Invio della bozza](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Crea un nuovo account Twitter.
* Fai clic sul menu nell’angolo in alto a destra e seleziona **[!UICONTROL Settings]**.
* Selezionare la scheda **[!UICONTROL Security and privacy]** e selezionare la casella **[!UICONTROL Protect my Tweets]**.
* Fai clic sul pulsante **[!UICONTROL Save Changes]** nella parte inferiore della pagina.

![](assets/social_twitter_test_page.png)

## Creazione di un&#39;applicazione su Twitter {#creating-an-application-on-twitter}

Affinché Adobe Campaign possa inviare tweet ai tuoi account Twitter, devi creare un&#39;applicazione Twitter per account Twitter. A questo scopo, esegui i seguenti passaggi:

1. Accedi al tuo account Twitter.
1. Inserisci il seguente indirizzo nel browser Internet: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Quindi fai clic sul pulsante **[!UICONTROL Create New App]** a destra.

   ![](assets/social_create_twitter_app_001.png)

1. Consentono alla procedura guidata di guidarti attraverso il processo.

   Per consentire ad Adobe Campaign di inviare tweet al tuo account, vai alla scheda **[!UICONTROL Permissions]** dell’applicazione e seleziona **[!UICONTROL Read and Write]** per la sezione **[!UICONTROL Access]** . Nella scheda **[!UICONTROL Settings]** è inoltre necessario lasciare vuoto il campo **[!UICONTROL Callback URL]** .

   ![](assets/social_create_twitter_app_002.png)

## Delega dell&#39;accesso in scrittura ad Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Per ogni applicazione Twitter, è necessario creare un servizio di tipo **[!UICONTROL Twitter]** diverso che includerà le impostazioni dell&#39;applicazione.

Questo passaggio richiede l’accesso simultaneo alla console Adobe Campaign e a un browser Internet connesso al tuo account Twitter:

* **Twitter**: seleziona l’applicazione creata in precedenza ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) e fai clic sulla  **[!UICONTROL Keys and Access Tokens]** scheda .

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: vai alla  **[!UICONTROL Profiles and targets]** scheda , fai clic sul  **[!UICONTROL Services and Subscriptions]** collegamento e fai clic sul  **[!UICONTROL Create]** pulsante .

   ![](assets/social_twitter_service_007.png)

1. Selezionare il tipo **[!UICONTROL Twitter]**.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >L’opzione **[!UICONTROL Synchronize subscriptions]** è attivata per impostazione predefinita. Quando la casella è selezionata, il flusso di lavoro di sincronizzazione dell&#39;account Twitter (fare riferimento a [Sincronizzazione degli account Twitter](#synchronizing-twitter-accounts)) recupera l&#39;elenco dei follower Twitter in modo da inviarli direttamente (fare riferimento a [Invio di messaggi diretti agli abbonati](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Se non si desidera recuperare l&#39;elenco dei follower, deselezionare questa casella.

1. Immetti l’etichetta e il nome interno del servizio.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >Il **[!UICONTROL Internal name]** del servizio deve essere identico al nome dell&#39;account Twitter. Per assicurarti che non ci siano errori di immissione, applica i seguenti passaggi.

   * Fai clic sul pulsante **[!UICONTROL Save]**.
   * Nella panoramica dei servizi, fai clic sul servizio di tipo Twitter appena creato.
   * Seleziona la scheda **[!UICONTROL Twitter page]**. Dovrebbe essere visualizzato l&#39;account Twitter.

      ![](assets/social_twitter_service_010.png)

1. Nel campo **[!UICONTROL Visitor folder]** , seleziona la cartella del visitatore in cui verranno creati i follower. Per ulteriori informazioni, consulta [Principio di funzionamento](../../social/using/publishing-on-twitter.md#operating-principle). Per impostazione predefinita, i follower vengono creati nella directory principale della cartella **[!UICONTROL Visitors]**.

   ![](assets/social_twitter_service_010_b.png)

1. Su Twitter, copia il contenuto dei campi **[!UICONTROL Consumer Key (API Key)]** e **[!UICONTROL Consumer Secret (API Secret)]** e incollalo nei campi **[!UICONTROL Consumer key]** e **[!UICONTROL Consumer secret]** della console.

   ![](assets/social_twitter_service_012.png)

1. Su Twitter, copia il contenuto dei campi **[!UICONTROL Access Token]** e **[!UICONTROL Access Token Secret]** e incollalo nei campi **[!UICONTROL Access token]** e **[!UICONTROL Access token secret]** della console.

   ![](assets/social_twitter_service_013.png)

1. Nella console Adobe Campaign, fai clic su **[!UICONTROL Save]**. La delega dell’accesso in scrittura ad Adobe Campaign è ora completa.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>È necessario creare un servizio di tipo **[!UICONTROL Twitter]** per ogni applicazione Twitter.

Il flusso di lavoro **[!UICONTROL Twitter account Synchronization]** sincronizza gli account Twitter in Adobe Campaign. Per ulteriori informazioni, consulta [Sincronizzazione delle pagine Facebook](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Sincronizzazione degli account Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Affinché il flusso di lavoro possa recuperare l’elenco degli abbonati a Twitter, la casella **[!UICONTROL Twitter account synchronization]** deve essere selezionata nella sezione di modifica del servizio collegato all’account. Per ulteriori informazioni, consulta [Delega dell’accesso in scrittura ad Adobe Campaign](#delegating-write-access-to-adobe-campaign).

Il flusso di lavoro **[!UICONTROL Twitter account synchronization]**, accessibile tramite il nodo **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, consente di sincronizzare gli account Twitter configurati in precedenza con Adobe Campaign. Per impostazione predefinita, questo flusso di lavoro viene attivato ogni giovedì alle 7:30.

>[!NOTE]
>
>È possibile avviare il flusso di lavoro in qualsiasi momento eseguendo l&#39;elaborazione prevista delle attività. Puoi anche modificare la pianificazione per modificare la frequenza di attivazione del flusso di lavoro. Per ulteriori informazioni sulla pianificazione, consulta [questa sezione](../../workflow/using/scheduler.md).

Ora puoi inviare tweet ai tuoi account Twitter e messaggi diretti ai tuoi follower. Per ulteriori informazioni, consulta: [Pubblicazione su Twitter](../../social/using/publishing-on-twitter.md).
