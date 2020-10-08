---
title: Pubblicazione su Facebook
seo-title: Pubblicazione su Facebook
description: Pubblicazione su Facebook
seo-description: null
page-status-flag: never-activated
uuid: f15170fa-0e7d-4913-81d6-0072c1ece482
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 335cf2de-1874-4e48-9538-f0937641cf96
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 3%

---


# Pubblicazione su Facebook{#publishing-on-facebook}

Una volta completata la configurazione, Social Marketing vi consente di pubblicare pubblicazioni sui muri delle vostre pagine Facebook.

## Limitazioni {#limitations}

Le seguenti limitazioni sono inerenti a Facebook.

* I messaggi non possono superare i 1.000 caratteri.
* HTML non è supportato.

## Creazione della consegna {#creating-the-delivery}

Create una nuova consegna utilizzando il modello di **[!UICONTROL Publish to a brand page]** consegna.

![](assets/social_facebook_delivery_001.png)

## Selecting the main target {#selecting-the-main-target}

È necessario selezionare le pagine sulle quali si desidera pubblicare la pubblicazione.

1. Fate clic sul **[!UICONTROL To]** collegamento.

   ![](assets/social_facebook_delivery_010.png)

1. Fai clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/social_facebook_delivery_011.png)

1. Seleziona **[!UICONTROL A Facebook page]**.

   ![](assets/social_facebook_delivery_012.png)

1. Nel **[!UICONTROL Folder]** campo, selezionate la cartella del servizio che contiene la pagina Facebook. Per impostazione predefinita, le pagine sono memorizzate nella cartella principale del **[!UICONTROL Facebook]** servizio. Selezionate quindi la pagina Facebook sulla quale desiderate pubblicare i post.

   ![](assets/social_facebook_delivery_013.png)

## Selezione della destinazione di prova {#selecting-the-proof-target}

La **[!UICONTROL Target of the proofs]** scheda consente di definire la pagina Facebook da utilizzare per testare le consegne prima di inviarle. È consigliabile creare a tal fine una pagina Facebook privata dedicata. Per ulteriori informazioni sulla creazione di una pagina Facebook privata, consultate [Creazione di una pagina](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)Facebook di prova. Per selezionare la destinazione di prova, eseguire le stesse operazioni della destinazione principale: [Selezione della destinazione](#selecting-the-main-target)principale.

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Se utilizzate la stessa pagina di test Facebook per tutte le consegne, potete salvare la destinazione della prova nel modello di **[!UICONTROL Publish to a brand page]** consegna, a cui si accede tramite il **[!UICONTROL Resources > Templates > Delivery templates]** nodo. La destinazione della prova verrà immessa per impostazione predefinita per ogni nuova consegna.

## Definizione dell&#39;audience {#defining-the-audience}

Se desiderate utilizzare i segmenti locali per definire il tipo di pubblico autorizzato a visualizzare la pubblicazione, è consigliabile creare una pagina Facebook per segmento (ad esempio:  Adobe Campaign Paris,  Adobe Campaign London, ecc.).

Tuttavia è anche possibile utilizzare i filtri per l&#39;audience utilizzati da Facebook. La **[!UICONTROL Audience]** scheda della **[!UICONTROL Select target window]** scheda offre quattro filtri:

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>Utilizzate questa funzione con attenzione. Nei rapporti di consegna, l&#39; **[!UICONTROL Number of fans]** indicatore non terrà conto di questi filtri Facebook.
>
>Facebook può modificare l&#39;elenco dei filtri per l&#39;audience e i relativi valori.

## Definizione del contenuto del messaggio {#defining-message-content}

Selezionate il tipo di pubblicazione utilizzando il menu a **[!UICONTROL Content type]** discesa.

![](assets/social_facebook_delivery_006.png)

Sono disponibili i seguenti tipi di consegne:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### Pubblicazione di uno stato {#publishing-a-status}

Un recapito del tipo di stato può contenere solo testo, come nell&#39;esempio seguente:

![](assets/social_create_facebook_wall_post_004.png)

Inserire lo stato di pubblicazione nella zona di input.

![](assets/social_facebook_delivery_015.png)

### Pubblicazione di uno stato con un collegamento {#publishing-a-status-with-a-link}

Un tipo di stato fornito con un collegamento può contenere testo, immagini e un collegamento. Nella sezione seguente viene descritta la simmetria tra i campi della schermata di distribuzione e la pubblicazione finale su Facebook:

![](assets/social_facebook_delivery_007.png)

Immettete i vari campi:

>[!IMPORTANT]
>
>Tutti gli URL devono iniziare con **&quot;http://&quot;** o **&quot;https://&quot;**.

1. Nel **[!UICONTROL Status]** campo, immettete il testo che verrà visualizzato sotto il nome della pagina.
1. Nel **[!UICONTROL Name]** campo, inserire il titolo della pubblicazione.
1. Nel **[!UICONTROL Link]** campo, immettete l’URL a cui punta la pubblicazione.

   >[!NOTE]
   >
   >Se desiderate aggiungere il **[!UICONTROL Link]** campo all&#39;URL di un&#39;applicazione Facebook per promuoverlo, vi consigliamo di adattarlo ai criteri di visualizzazione dello smartphone:
   >
   >1. Selezionate l’applicazione Facebook [https://developers.facebook.com/apps](https://developers.facebook.com/apps), quindi selezionate la **[!UICONTROL Settings > Basic]** scheda.
   >1. Immettere il **[!UICONTROL Namespace]** campo.
   >1. Immettere il **[!UICONTROL Mobile Site URL]** campo: quando un utente fa clic sul collegamento della pubblicazione sul proprio smartphone, viene automaticamente reindirizzato da Facebook all&#39;URL definito in questo campo.
   >1. Create l&#39;applicazione Web in modo che il display di Facebook sia personalizzato in funzione del dispositivo utilizzato (smartphone o PC).
   >1. Passate al **[!UICONTROL Link]** campo della pubblicazione tramite la console Adobe Campaign , immettete l’URL del **[!UICONTROL Canvas page]** campo.


1. Nel **[!UICONTROL Image]** campo, immettete l’URL dell’immagine che verrà visualizzata a sinistra della pubblicazione.

   >[!IMPORTANT]
   >
   >L&#39;immagine deve essere ospitata su un sito Internet pubblico per poter essere caricata da Facebook.

1. Nel **[!UICONTROL Caption]** campo, immettete il testo che verrà visualizzato alla fine della pubblicazione.
1. Vai al **[!UICONTROL Description]** campo e immetti il testo da visualizzare sotto il titolo.

![](assets/social_facebook_delivery_005.png)

### Pubblicazione di uno stato con un collegamento YouTube {#publishing-a-status-with-a-youtube-link}

Questo tipo di contenuto consente di pubblicare un collegamento a un video di YouTube. Come per uno stato con un collegamento regolare, potete definire uno stato, un nome, una didascalia, una descrizione e un collegamento aggiuntivo. L’immagine viene aggiunta automaticamente da Facebook. Le simmetrie tra i campi della schermata di distribuzione e la pubblicazione finale su Facebook sono descritte di seguito:

![](assets/social_facebook_delivery_youtube_1.png)

Immettete i vari campi:

>[!CAUTION]
>
>Tutti gli URL devono iniziare con **&quot;http://&quot;** o **&quot;https://&quot;**.

1. Nel **[!UICONTROL Status]** campo, immettete il testo che verrà visualizzato sotto il nome della pagina.
1. Nel **[!UICONTROL Name]** campo, inserire il titolo della pubblicazione.
1. Nel **[!UICONTROL Video code]** campo , inserite il codice del video di YouTube. Ad esempio, per il collegamento https://www.youtube.com/watch?v=abc123456&#39;, il codice video sarà &#39;abc123456&#39;.
1. Nel **[!UICONTROL Caption]** campo, immettete il testo che verrà visualizzato alla fine della pubblicazione.
1. Vai al **[!UICONTROL Description]** campo e immetti il testo da visualizzare sotto il titolo.

![](assets/social_facebook_delivery_youtube.png)

### Pubblicazione di un album fotografico {#publishing-a-photo-album}

Questo tipo di contenuto consente di pubblicare un album fotografico. Potete aggiungere un nome e una descrizione per l&#39;album, nonché una didascalia per ogni foto. Le simmetrie tra i campi della schermata di distribuzione e la pubblicazione finale su Facebook sono descritte di seguito:

![](assets/social_facebook_delivery_photos_1.png)

Immettete i vari campi:

1. Inizia inserendo il **[!UICONTROL Album name]**.
1. Inserite quindi il testo **[!UICONTROL Description]** da visualizzare sopra le foto.
1. Per aggiungere una foto, fate clic sul **[!UICONTROL Add]** pulsante, selezionate la foto e fate clic **[!UICONTROL Open]**.
1. È possibile aggiungere una didascalia a ogni foto.

![](assets/social_facebook_delivery_photos.png)

## Anteprima {#previewing}

La **[!UICONTROL Preview]** scheda consente di visualizzare il rendering della pubblicazione.

1. Fate clic sulla **[!UICONTROL Preview]** scheda.
1. Fare clic sul **[!UICONTROL Test personalization]** menu a discesa e selezionare **[!UICONTROL Service]**.
1. Nel **[!UICONTROL Folder]** campo, selezionate la cartella del servizio che contiene le pagine Facebook. Per impostazione predefinita, le pagine sono memorizzate nella cartella principale del **[!UICONTROL Facebook]** servizio.
1. Selezionate la pagina Facebook sulla quale desiderate testare l’anteprima.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>L’anteprima potrebbe essere leggermente diversa dalla pubblicazione finale su Facebook. Si consiglia vivamente di inviare una prova prima della consegna finale per un rendering esatto della pubblicazione. Fare riferimento a [Invio della prova](#sending-the-proof).

## Configurazione del tracciamento {#configuring-tracking}

Il tracciamento può essere visualizzato nei rapporti di consegna e nella **[!UICONTROL Edit > Tracking]** scheda della consegna e del servizio.

I clic sull’URL contenuto nella consegna vengono misurati da  Adobe Campaign. Il numero di clic sul **[!UICONTROL Like]** pulsante, il numero di commenti e il numero di fan sono misurati da Facebook.

La configurazione del tracciamento è la stessa di una distribuzione tramite e-mail. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>Nel modello di **[!UICONTROL Publish to a brand page]** consegna, il tracciamento è attivato per impostazione predefinita.

## Invio della prova {#sending-the-proof}

Si consiglia vivamente di inviare una prova della pubblicazione prima della consegna finale per visualizzare l&#39;esatto rendering della pubblicazione su una pagina di test Facebook privata. Per ulteriori informazioni sulla creazione di una pagina di test Facebook privata, consultate [Creazione di una pagina](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)Facebook di prova. I passaggi per selezionare la prova di destinazione sono descritti in [Selezione della destinazione](#selecting-the-proof-target)della prova.

La consegna della prova è identica alle consegne tramite e-mail. Fai riferimento a [questa sezione](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Invio del messaggio {#sending-the-message}

1. Una volta approvato il contenuto, fate clic sul **[!UICONTROL Send]** pulsante .
1. Selezionate **[!UICONTROL Deliver as soon as possible]** e fate clic sul **[!UICONTROL Analyze]** pulsante.

   >[!NOTE]
   >
   >L&#39; **[!UICONTROL Postpone the delivery]** opzione consente di posticipare la consegna a una data successiva.

   ![](assets/social_facebook_delivery_009.png)

1. Una volta completata l&#39;analisi, verificare il risultato.
1. Fate clic **[!UICONTROL Confirm delivery]**, quindi fate clic **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)

