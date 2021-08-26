---
product: campaign
title: Pubblicazione su Twitter
description: Pubblicazione su Twitter
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: e030c029-d1ee-4749-94e3-6bdfc8d89a34
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 5%

---

# Pubblicazione su Twitter{#publishing-on-twitter}

![](../../assets/v7-only.svg)

## Pubblicazione sugli account Twitter {#publishing-on-your-twitter-accounts}

Una volta completata la configurazione, Social Marketing ti consente di inviare tweet ai tuoi account Twitter.

### Limitazioni {#limitations}

Le seguenti limitazioni sono vincoli inerenti a Twitter.

* Il messaggio non può superare i 140 caratteri.
* Il formato HTML non è supportato.

### Creazione della consegna {#creating-the-delivery}

Crea una nuova consegna basata sul modello di consegna **[!UICONTROL Tweet (twitter)]** .

![](assets/social_twitter_delivery_001.png)

### Selezione del target principale {#selecting-the-main-target}

Seleziona gli account a cui desideri inviare i tweet.

1. Fai clic sul collegamento **[!UICONTROL To]**.

   ![](assets/social_twitter_delivery_002.png)

1. Fai clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Seleziona **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. Nel campo **[!UICONTROL Folder]** , seleziona la cartella del servizio che contiene l’account Twitter. Quindi seleziona l’account Twitter a cui desideri inviare il tuo tweet.

   ![](assets/social_twitter_delivery_011.png)

### Selezione del target della bozza {#selecting-the-target-of-the-proof}

La scheda **[!UICONTROL Target of the proofs]** ti consente di definire l’account Twitter da utilizzare per testare le consegne prima della consegna finale. È quindi consigliabile creare un account Twitter privato dedicato all’invio di bozze. Per ulteriori informazioni su come creare un account Twitter privato, consulta [Creazione di un account di test su Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). I passaggi per selezionare il target della bozza sono gli stessi che per selezionare il target principale. Fai riferimento a [Creazione di un account di test su Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Se utilizzi lo stesso account di test Twitter per tutte le consegne, puoi salvare la destinazione della bozza nel modello di consegna **[!UICONTROL Tweet]** , accessibile tramite il nodo **[!UICONTROL Resources > Templates > Delivery templates]** . Il target della bozza verrà quindi immesso per impostazione predefinita per ogni nuova consegna.

### Definizione del contenuto del messaggio {#defining-the-message-content}

Digita il contenuto del tweet nella scheda **[!UICONTROL Content]** .

![](assets/social_twitter_delivery_005.png)

### Visualizzazione dell&#39;anteprima {#viewing-the-preview}

La scheda **[!UICONTROL Preview]** ti consente di visualizzare un rendering del tweet.

1. Fai clic sulla scheda **[!UICONTROL Preview]** .
1. Fai clic sul menu a discesa **[!UICONTROL Test personalization]** e seleziona **[!UICONTROL Service]**.
1. Nel campo **[!UICONTROL Folder]** , seleziona la cartella del servizio che contiene il tuo account Twitter.
1. Scegli l&#39;account Twitter con cui testare l&#39;anteprima.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>L&#39;anteprima può differire leggermente dal tweet finale. Consigliamo vivamente di inviare una prova prima della consegna finale per visualizzare un rendering esatto del tweet. Fai riferimento a [Invio della bozza](#sending-the-proof).

### Configurazione del tracciamento {#configuring-tracking}

Il tracciamento può essere visualizzato nei rapporti di consegna e nella scheda **[!UICONTROL Edit > Tracking]** della consegna e del servizio.

La configurazione del tracciamento è la stessa di una consegna e-mail. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/about-delivery-monitoring.md).

>[!NOTE]
>
>Nel modello di consegna **[!UICONTROL Tweet]**, il tracciamento è abilitato per impostazione predefinita.

>[!IMPORTANT]
>
>Non riusciamo a distinguere tra robot che analizzano i tweet e utenti che stanno cliccando.

### Invio della bozza {#sending-the-proof}

Si consiglia vivamente di inviare una prova della pubblicazione prima della consegna finale per ottenere un rendering esatto della pubblicazione su una pagina di test Twitter privata. Per ulteriori informazioni sulla creazione di un account Twitter privato, consulta [Creazione di un account di test su Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). I passaggi per selezionare la destinazione della bozza sono descritti in [Selezione della destinazione della bozza](#selecting-the-target-of-the-proof).

La consegna delle prove è identica alle consegne delle e-mail. Fai riferimento a [questa sezione](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Invio del messaggio {#sending-the-message}

1. Una volta approvato il contenuto, fai clic sul pulsante **[!UICONTROL Send]** .
1. Selezionare **[!UICONTROL Deliver as soon as possible]** e fare clic sul pulsante **[!UICONTROL Analyze]**.

   >[!NOTE]
   >
   >L’opzione **[!UICONTROL Postpone the delivery]** ti consente di posticipare la consegna a una data successiva.

   ![](assets/social_twitter_delivery_012.png)

1. Al termine dell’analisi, controlla il risultato.
1. Fare clic su **[!UICONTROL Confirm delivery]**, quindi su **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Invio di messaggi diretti agli abbonati {#sending-direct-messages-to-subscribers}

### Principio di funzionamento {#operating-principle}

Il flusso di lavoro **[!UICONTROL Synchronize Twitter accounts]** (consulta [Sincronizzazione degli account Twitter](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)) recupera l’elenco degli abbonati Twitter in modo da poter inviare loro messaggi diretti. I seguaci recuperati sono memorizzati in una tabella specifica: la tabella dei visitatori. Per visualizzare l’elenco dei follower di Twitter, passa al nodo **[!UICONTROL Profiles and Targets > Visitors]** .

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>Affinché il flusso di lavoro possa recuperare l’elenco dei follower di Twitter, la casella **[!UICONTROL Synchronize Twitter accounts]** deve essere selezionata nella schermata Modifica del servizio collegato all’account. Per ulteriori informazioni, consulta: [Delega dell&#39;accesso in scrittura ad Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Per ogni follower, Adobe Campaign recupera le seguenti informazioni:

* **[!UICONTROL Origin]**: nome del social network (**** Twitterin in questo caso)
* **[!UICONTROL External ID]**: identificatore utente
* **[!UICONTROL User name]**: nome account dell&#39;utente
* **[!UICONTROL Full name]**: nome dell&#39;utente
* **[!UICONTROL Language]**: lingua utente
* **[!UICONTROL Number of friends]**: numero di follower
* **[!UICONTROL Time zone]**: fuso orario utente
* **[!UICONTROL Verified]**: questo campo indica se l’utente dispone di un account Twitter verificato

### Limitazioni {#limitations-1}

Le seguenti limitazioni sono vincoli inerenti a Twitter.

* Il messaggio non può superare i 140 caratteri.
* HTML non supportato.
* Non puoi inviare più di 250 messaggi diretti al giorno. Per evitare di superare questa soglia, puoi fornire in diverse ondate. Le consegne a ondate sono configurate come le consegne e-mail. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Creazione della consegna {#creating-the-delivery-}

Crea una nuova consegna basata sul modello di consegna **[!UICONTROL Tweet (Direct Message)]** .

![](assets/social_twitter_delivery_010.png)

### Selezione del target principale {#selecting-the-main-target-1}

Seleziona i follower a cui desideri inviare il messaggio diretto.

1. Fai clic sul collegamento **[!UICONTROL To]**.

   ![](assets/social_twitter_delivery_016.png)

1. Fai clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Seleziona un tipo di targeting.

   ![](assets/social_twitter_delivery_017.png)

   * Seleziona **[!UICONTROL Twitter subscribers]** per inviare un messaggio diretto a tutti i follower dell’account.

      >[!IMPORTANT]
      >
      >Non puoi inviare più di 250 messaggi al giorno. Se il tuo account Twitter ha più di 250 follower, ti consigliamo vivamente di consegnare in ondate. Questo comporta lo stesso processo delle consegne e-mail. Fai riferimento a [questa sezione](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Seleziona **[!UICONTROL Filter conditions]** per definire una query e visualizzarne il risultato. Questa opzione è la stessa delle consegne e-mail. Per ulteriori informazioni, consulta [questa sezione](../../platform/using/defining-filter-conditions.md) .

      ![](assets/social_twitter_delivery_018.png)

### Selezione del target della bozza {#selecting-the-target-of-the-proof-1}

La scheda **[!UICONTROL Target of the proofs]** ti consente di selezionare il follower che riceverà la bozza del messaggio diretto. Il processo di selezione è lo stesso del target principale. Fare riferimento a [Selezione della destinazione principale](#selecting-the-main-target).

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Se desideri inviare tutte le bozze dei messaggi diretti allo stesso follower di Twitter, puoi salvare la destinazione della bozza nel modello di consegna **[!UICONTROL Tweet (Direct Message)]** , accessibile tramite il nodo **[!UICONTROL Resources > Templates > Delivery templates]** . Il target della bozza verrà quindi immesso per impostazione predefinita per ogni nuova consegna.

### Definizione del contenuto del messaggio {#defining-message-content-}

Immetti il contenuto del tweet nella scheda **[!UICONTROL Content]** .

![](assets/social_twitter_delivery_015.png)

I campi di personalizzazione possono essere utilizzati nello stesso modo delle consegne e-mail, ad esempio per aggiungere il nome del follower nel corpo del messaggio. La personalizzazione dei contenuti è descritta in [questa sezione](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

I seguenti passaggi sono gli stessi dell’invio di un tweet a un account Twitter. Fai riferimento a [Pubblicazione sui tuoi account Twitter](#publishing-on-your-twitter-accounts).
