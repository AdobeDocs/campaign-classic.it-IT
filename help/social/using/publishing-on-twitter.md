---
product: campaign
title: Pubblicazione su Twitter
description: Pubblicazione su Twitter
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: e030c029-d1ee-4749-94e3-6bdfc8d89a34
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 6%

---

# Pubblicare su Twitter{#publishing-on-twitter}

![](../../assets/v7-only.svg)

## Pubblica sui tuoi account Twitter {#publishing-on-your-twitter-accounts}

Una volta completata la configurazione, Social Marketing ti consente di inviare tweet ai tuoi account Twitter.

### Limitazioni {#limitations}

Le seguenti limitazioni sono vincoli inerenti a Twitter.

* Il messaggio non può superare i 140 caratteri.
* Il formato HTML non è supportato.

### Creare la consegna {#creating-the-delivery}

Crea una nuova consegna basata su **[!UICONTROL Tweet (twitter)]** modello di consegna.

![](assets/social_twitter_delivery_001.png)

### Selezionare la destinazione principale {#selecting-the-main-target}

Seleziona gli account a cui desideri inviare i tweet.

1. Fai clic sul collegamento **[!UICONTROL To]**.

   ![](assets/social_twitter_delivery_002.png)

1. Fai clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Seleziona **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. In **[!UICONTROL Folder]** selezionare la cartella del servizio che contiene l&#39;account Twitter. Quindi seleziona l’account Twitter a cui desideri inviare il tuo tweet.

   ![](assets/social_twitter_delivery_011.png)

### Selezionare la destinazione della bozza {#selecting-the-target-of-the-proof}

La **[!UICONTROL Target of the proofs]** La scheda ti consente di definire l’account Twitter da utilizzare per testare le consegne prima della consegna finale. È quindi consigliabile creare un account Twitter privato dedicato all’invio di bozze. Per ulteriori informazioni su come creare un account Twitter privato, consulta [questa sezione](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). I passaggi per selezionare il target della bozza sono gli stessi che per selezionare il target principale. Fai riferimento a [questa sezione](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Se utilizzi lo stesso account di test Twitter per tutte le consegne, puoi salvare la destinazione della bozza nella sezione **[!UICONTROL Tweet]** modello di consegna, accessibile tramite il **[!UICONTROL Resources > Templates > Delivery templates]** nodo. Il target della bozza verrà quindi immesso per impostazione predefinita per ogni nuova consegna.

### Definire il contenuto del messaggio {#defining-the-message-content}

Digita il contenuto del tuo tweet nel **[!UICONTROL Content]** scheda .

![](assets/social_twitter_delivery_005.png)

### Anteprima del messaggio {#viewing-the-preview}

La **[!UICONTROL Preview]** consente di visualizzare un rendering del tweet.

1. Fai clic sul pulsante **[!UICONTROL Preview]** scheda .
1. Fai clic sul pulsante **[!UICONTROL Test personalization]** menu a discesa e seleziona **[!UICONTROL Service]**.
1. In **[!UICONTROL Folder]** , seleziona la cartella del servizio che contiene il tuo account Twitter.
1. Scegli l&#39;account Twitter con cui testare l&#39;anteprima.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>L&#39;anteprima può differire leggermente dal tweet finale. Consigliamo vivamente di inviare una prova prima della consegna finale per visualizzare un rendering esatto del tweet. Fai riferimento a [questa sezione](#sending-the-proof).

### Configurare il tracciamento {#configuring-tracking}

Il tracciamento può essere visualizzato nei rapporti di consegna e nel **[!UICONTROL Edit > Tracking]** scheda della consegna e del servizio.

La configurazione del tracciamento è la stessa di una consegna e-mail. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/about-delivery-monitoring.md).

>[!NOTE]
>
>In **[!UICONTROL Tweet]** modello di consegna, il tracciamento è abilitato per impostazione predefinita.

>[!CAUTION]
>
>Non riusciamo a distinguere tra robot che analizzano i tweet e utenti che stanno cliccando.

### Invia la bozza {#sending-the-proof}

Si consiglia vivamente di inviare una prova della pubblicazione prima della consegna finale per ottenere un rendering esatto della pubblicazione su una pagina di test Twitter privata. Per ulteriori informazioni sulla creazione di un account Twitter privato, consulta [questa sezione](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). I passaggi per selezionare la destinazione della bozza sono descritti in [questa sezione](#selecting-the-target-of-the-proof).

La consegna delle prove è identica alle consegne delle e-mail. Fai riferimento a [questa sezione](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Invia il messaggio {#sending-the-message}

1. Una volta approvato il contenuto, fai clic sul pulsante **[!UICONTROL Send]** pulsante .
1. Seleziona **[!UICONTROL Deliver as soon as possible]** e fai clic su **[!UICONTROL Analyze]** pulsante .

   >[!NOTE]
   >
   >La **[!UICONTROL Postpone the delivery]** consente di posticipare la consegna a una data successiva.

   ![](assets/social_twitter_delivery_012.png)

1. Al termine dell’analisi, controlla il risultato.
1. Fai clic su **[!UICONTROL Confirm delivery]**, quindi fai clic su **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Inviare messaggi diretti agli abbonati {#sending-direct-messages-to-subscribers}

### Principio di funzionamento {#operating-principle}

La **[!UICONTROL Synchronize Twitter accounts]** workflow (fai riferimento a [Ulteriori informazioni](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)) recupera l’elenco degli abbonati a Twitter in modo da poter inviare loro messaggi diretti. I seguaci recuperati sono memorizzati in una tabella specifica: la tabella dei visitatori. Per visualizzare l’elenco dei follower di Twitter, vai alla pagina **[!UICONTROL Profiles and Targets > Visitors]** nodo.

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>Affinché il flusso di lavoro possa recuperare l’elenco dei follower di Twitter, la **[!UICONTROL Synchronize Twitter accounts]** deve essere selezionata nella schermata Modifica del servizio collegato all&#39;account. Per ulteriori informazioni, consulta: [Delega dell’accesso in scrittura ad Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Per ogni follower, Adobe Campaign recupera le seguenti informazioni:

* **[!UICONTROL Origin]**: nome del social network (**Twitter** in questo caso)
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
* HTML non è supportato.
* Non puoi inviare più di 250 messaggi diretti al giorno. Per evitare di superare questa soglia, puoi fornire in diverse ondate. Le consegne a ondate sono configurate come le consegne e-mail. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Creare la consegna {#creating-the-delivery-}

Crea una nuova consegna basata su **[!UICONTROL Tweet (Direct Message)]** modello di consegna.

![](assets/social_twitter_delivery_010.png)

### Selezionare la destinazione principale {#selecting-the-main-target-1}

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

   * Seleziona **[!UICONTROL Filter conditions]** per definire una query e visualizzarne il risultato. Questa opzione è la stessa delle consegne e-mail. Fai riferimento a [questa sezione](../../platform/using/defining-filter-conditions.md) per ulteriori informazioni.

      ![](assets/social_twitter_delivery_018.png)

### Selezionare la destinazione della bozza {#selecting-the-target-of-the-proof-1}

La **[!UICONTROL Target of the proofs]** consente di selezionare il follower che riceverà la bozza del messaggio diretto. Il processo di selezione è lo stesso del target principale. Fai riferimento a [Selezione del target principale](#selecting-the-main-target).

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Se desideri inviare tutte le bozze dei messaggi diretti allo stesso follower di Twitter, puoi salvare la destinazione della bozza nella **[!UICONTROL Tweet (Direct Message)]** modello di consegna, accessibile tramite il **[!UICONTROL Resources > Templates > Delivery templates]** nodo. Il target della bozza verrà quindi immesso per impostazione predefinita per ogni nuova consegna.

### Definire il contenuto del messaggio {#defining-message-content-}

Immetti il contenuto del tweet nel **[!UICONTROL Content]** scheda .

![](assets/social_twitter_delivery_015.png)

I campi di personalizzazione possono essere utilizzati nello stesso modo delle consegne e-mail, ad esempio per aggiungere il nome del follower nel corpo del messaggio. La personalizzazione dei contenuti è descritta in [questa sezione](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

I seguenti passaggi sono gli stessi dell’invio di un tweet a un account Twitter. Fai riferimento a [Pubblicazione sugli account Twitter](#publishing-on-your-twitter-accounts).
