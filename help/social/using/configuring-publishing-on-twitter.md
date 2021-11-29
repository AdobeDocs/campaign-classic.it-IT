---
product: campaign
title: Configurazione della pubblicazione su Twitter
description: Configurazione della pubblicazione su Twitter
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 7%

---

# Passaggi di configurazione da pubblicare su Twitter{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

Affinché Adobe Campaign possa inviare tweet ai tuoi account Twitter, devi delegare l’accesso in scrittura ad Adobe Campaign per questi account. A questo scopo, applica i seguenti passaggi di configurazione:

* Crea un account Twitter.
* Crea un account Twitter di prova per l’invio di bozze.
* Crea un&#39;applicazione Twitter per account Twitter.
* Per ogni applicazione Twitter, crea un nuovo **[!UICONTROL Twitter]** servizio del tipo.

![](assets/social_diagram_twitter_service.png)

## Prerequisiti {#prerequisites}

Inizia creando uno o più account Twitter a cui inviare i tweet.

Per creare un account Twitter, vai a [https://twitter.com](https://twitter.com){target=&quot;_blank&quot;}.

## Creare un account di test su Twitter {#creating-a-test-account-on-twitter}

Crea un account Twitter privato che può essere utilizzato per l’invio [bozze di tweet](../../social/using/publishing-on-twitter.md#sending-the-proof). Per creare un account Twitter privato, effettua le seguenti operazioni:

1. Crea un nuovo account Twitter.
1. Accedere all’account  **[!UICONTROL Settings]**.
1. Sfoglia per **[!UICONTROL Privacy & Safety]** e **[!UICONTROL Audience and Tagging]** e controlla **[!UICONTROL Protect your Tweets]** opzione . I tuoi Tweet e altre informazioni sull&#39;account sono visibili solo alle persone che ti seguono.

![](assets/social_twitter_test_page.png)

## Creare un’applicazione in Twitter {#creating-an-application-on-twitter}

Affinché Adobe Campaign possa inviare tweet ai tuoi account Twitter, devi creare un’applicazione Twitter per account Twitter. A questo scopo, esegui i seguenti passaggi:

1. Accedi al tuo account Twitter.
1. Inserisci il seguente indirizzo nel browser Internet: [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps).
1. Quindi fai clic sul pulsante **[!UICONTROL Create an App]** a destra.

   ![](assets/social_create_twitter_app_001.png)

1. Consentono alla procedura guidata di guidarti attraverso il processo.

   Affinché questa applicazione consenta ad Adobe Campaign di inviare tweet al tuo account, vai alla pagina **[!UICONTROL Permissions]** scheda dell&#39;applicazione e seleziona **[!UICONTROL Read and Write]** per **[!UICONTROL Access]** sezione . In **[!UICONTROL Settings]** , è inoltre necessario uscire dalla **[!UICONTROL Callback URL]** campo vuoto.

   ![](assets/social_create_twitter_app_002.png)

## Delega dell’accesso in scrittura ad Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Per ogni applicazione Twitter, è necessario creare un **[!UICONTROL Twitter]** digitare il servizio che include le impostazioni dell&#39;applicazione.

Questo passaggio richiede l’accesso simultaneo alla console Adobe Campaign e a un browser Internet connesso al tuo account Twitter:

* in **Twitter**: da [questa pagina](https://developer.twitter.com/en/portal/projects-and-apps), seleziona l’app creata in precedenza e modifica il **Autorizzazioni app**.

   ![](assets/social_twitter_service_002.png)

   Modifica le **Tasti e token** per accedere ai dettagli dell’app.

* in **Adobe Campaign**: vai al **[!UICONTROL Profiles and targets]** fai clic sulla scheda **[!UICONTROL Services and Subscriptions]** fai clic sul pulsante **[!UICONTROL Create]** pulsante .

   ![](assets/social_twitter_service_007.png)

1. Seleziona la **[!UICONTROL Twitter]** digitare.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >La **[!UICONTROL Synchronize subscriptions]** è attivata per impostazione predefinita. Quando la casella è selezionata, il flusso di lavoro di sincronizzazione dell’account Twitter (consulta [Sincronizzazione degli account Twitter](#synchronizing-twitter-accounts)) recupera l’elenco dei follower di Twitter in modo da poter inviare loro messaggi diretti (consulta [Invio di messaggi diretti agli abbonati](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Se non si desidera recuperare l&#39;elenco dei follower, deselezionare questa casella.

1. Immetti l’etichetta e il nome interno del servizio.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >La **[!UICONTROL Internal name]** del servizio deve essere identico al nome dell&#39;account Twitter. Per assicurarti che non ci siano errori di immissione, applica i seguenti passaggi.

   * Fai clic sul pulsante **[!UICONTROL Save]**.
   * Nella panoramica dei servizi, fai clic sul servizio Twitter appena creato.

   <!-- * Select the **[!UICONTROL Twitter page]** tab. The Twitter account should be displayed. 
    
      ![](assets/social_twitter_service_010.png)-->

1. In **[!UICONTROL Visitor folder]** selezionare la cartella in cui verranno creati i follower. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../social/using/publishing-on-twitter.md#operating-principle). Per impostazione predefinita, i follower vengono salvati in **[!UICONTROL Visitors]** cartella.

   ![](assets/social_twitter_service_010_b.png)

1. Su Twitter, copia il contenuto del **[!UICONTROL Consumer Key (API Key)]** e **[!UICONTROL Consumer Secret (API Secret)]** e incollalo nel **[!UICONTROL Consumer key]** e **[!UICONTROL Consumer secret]** campi della console del client Campaign.

   ![](assets/social_twitter_service_012.png)

1. Su Twitter, copia il contenuto del **[!UICONTROL Access Token]** e **[!UICONTROL Access Token Secret]** e incollalo nel **[!UICONTROL Access token]** e **[!UICONTROL Access token secret]** campi della console del client Campaign.

   ![](assets/social_twitter_service_013.png)

1. Nella console del client Campaign, fai clic su **[!UICONTROL Save]**. Hai delegato l’accesso in scrittura ad Adobe Campaign.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>È necessario crearne uno **[!UICONTROL Twitter]** servizio per applicazione Twitter.

La **[!UICONTROL Twitter account Synchronization]** il flusso di lavoro sincronizza gli account Twitter in Adobe Campaign. Per ulteriori informazioni, consulta [questa pagina](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Sincronizzazione degli account Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Affinché il flusso di lavoro recuperi l’elenco degli abbonati a Twitter, la **[!UICONTROL Twitter account synchronization]** deve essere selezionato nella sezione di modifica del servizio collegato all&#39;account. Per ulteriori informazioni al riguardo, consulta [questa sezione](#delegating-write-access-to-adobe-campaign).

La **[!UICONTROL Twitter account synchronization]** , accessibile tramite il **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** consente di sincronizzare gli account Twitter configurati in precedenza con Adobe Campaign. Per impostazione predefinita, questo flusso di lavoro viene attivato ogni giovedì alle 7:30.

>[!NOTE]
>
>È possibile avviare il flusso di lavoro in qualsiasi momento eseguendo l&#39;elaborazione prevista delle attività. Puoi anche modificare la pianificazione per modificare la frequenza di attivazione del flusso di lavoro. Per ulteriori informazioni sulla pianificazione, consulta [questa sezione](../../workflow/using/scheduler.md).

Ora puoi inviare tweet ai tuoi account Twitter e inviare messaggi diretti ai tuoi follower. Per ulteriori informazioni, consulta [questa pagina](../../social/using/publishing-on-twitter.md).
