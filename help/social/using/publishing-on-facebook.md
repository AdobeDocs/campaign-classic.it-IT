---
product: campaign
title: Pubblicazione su Facebook
description: Pubblicazione su Facebook
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: 84d6cb2e-c7f9-43d7-a98c-22613d456193
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 3%

---

# Pubblicazione su Facebook{#publishing-on-facebook}

![](../../assets/v7-only.svg)

Una volta completata la configurazione, Social Marketing consente di pubblicare pubblicazioni sulle pareti delle pagine Facebook.

## Limitazioni {#limitations}

Le seguenti limitazioni sono inerenti a Facebook.

* I messaggi non possono superare i 1.000 caratteri.
* HTML non è supportato.

## Creazione della consegna {#creating-the-delivery}

Crea una nuova consegna utilizzando **[!UICONTROL Publish to a brand page]** modello di consegna.

![](assets/social_facebook_delivery_001.png)

## Selezione del target principale {#selecting-the-main-target}

Selezionare le pagine sulle quali si desidera pubblicare la pubblicazione.

1. Fai clic sul collegamento **[!UICONTROL To]**.

   ![](assets/social_facebook_delivery_010.png)

1. Fai clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/social_facebook_delivery_011.png)

1. Seleziona **[!UICONTROL A Facebook page]**.

   ![](assets/social_facebook_delivery_012.png)

1. In **[!UICONTROL Folder]** selezionare la cartella del servizio contenente la pagina Facebook. Per impostazione predefinita, le pagine vengono memorizzate nella directory principale della **[!UICONTROL Facebook]** cartella del servizio. Quindi seleziona la pagina Facebook su cui desideri pubblicare.

   ![](assets/social_facebook_delivery_013.png)

## Selezione della destinazione della bozza {#selecting-the-proof-target}

La **[!UICONTROL Target of the proofs]** La scheda ti consente di definire la pagina Facebook da utilizzare per testare le consegne prima di inviarle. È consigliabile creare una pagina Facebook privata dedicata a questo scopo. Per ulteriori informazioni sulla creazione di una pagina Facebook privata, consulta [Creazione di una pagina Facebook di test](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Per selezionare il target della bozza, esegui gli stessi passaggi del target principale: [Selezione del target principale](#selecting-the-main-target).

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Se utilizzi la stessa pagina di test di Facebook per tutte le consegne, puoi salvare il target della bozza nella **[!UICONTROL Publish to a brand page]** modello di consegna, accessibile tramite **[!UICONTROL Resources > Templates > Delivery templates]** nodo. Il target della bozza verrà immesso per impostazione predefinita per ogni nuova consegna.

## Definizione del pubblico {#defining-the-audience}

Se desideri utilizzare i segmenti locali per perfezionare il tipo di pubblico autorizzato a visualizzare la pubblicazione, ti consigliamo di creare una pagina Facebook per segmento (ad esempio: Adobe Campaign Paris, Adobe Campaign London, ecc.).

Tuttavia è anche possibile utilizzare i filtri del pubblico utilizzati da Facebook. La **[!UICONTROL Audience]** della scheda **[!UICONTROL Select target window]** offre quattro filtri:

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>Usa questa funzione con attenzione. Nei rapporti di consegna, la **[!UICONTROL Number of fans]** Questo indicatore non terrà conto di questi filtri Facebook.
>
>Facebook può modificare l’elenco dei filtri per il pubblico e i relativi valori.

## Definizione del contenuto del messaggio {#defining-message-content}

Seleziona il tipo di pubblicazione utilizzando **[!UICONTROL Content type]** menu a discesa.

![](assets/social_facebook_delivery_006.png)

Sono disponibili i seguenti tipi di consegne:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### Pubblicazione di uno stato {#publishing-a-status}

Una consegna di tipo di stato può contenere solo testo, come nell’esempio seguente:

![](assets/social_create_facebook_wall_post_004.png)

Inserire lo stato di pubblicazione nella zona di input.

![](assets/social_facebook_delivery_015.png)

### Pubblicazione di uno stato con un collegamento {#publishing-a-status-with-a-link}

Una consegna di tipo stato con un collegamento può contenere testo, immagini e un collegamento. La sezione seguente descrive la simmetria tra i campi della schermata di modifica della consegna e la pubblicazione finale su Facebook:

![](assets/social_facebook_delivery_007.png)

Inserisci i vari campi:

>[!IMPORTANT]
>
>Tutti gli URL devono iniziare con **&quot;http://&quot;** o **&quot;https://&quot;**.

1. In **[!UICONTROL Status]** immettere il testo che verrà visualizzato sotto il nome della pagina.
1. In **[!UICONTROL Name]** immettere il titolo della pubblicazione.
1. In **[!UICONTROL Link]** , immetti l&#39;URL a cui punta la pubblicazione.

   >[!NOTE]
   >
   >Se desideri aggiungere il **[!UICONTROL Link]** all&#39;URL di un&#39;applicazione Facebook per promuoverlo, ti consigliamo di adattarlo ai criteri di visualizzazione per smartphone:
   >
   >1. Selezionare l’applicazione Facebook [https://developers.facebook.com/apps](https://developers.facebook.com/apps), quindi seleziona la **[!UICONTROL Settings > Basic]** scheda .
   >1. Inserisci il **[!UICONTROL Namespace]** campo .
   >1. Inserisci il **[!UICONTROL Mobile Site URL]** campo: quando un utente fa clic sul collegamento di pubblicazione sul proprio smartphone, viene automaticamente reindirizzato da Facebook all&#39;URL definito in questo campo.
   >1. Crea l&#39;applicazione web in modo che il display Facebook sia personalizzato in funzione del dispositivo utilizzato (smartphone o PC).
   >1. Vai a **[!UICONTROL Link]** nel campo della pubblicazione tramite la console Adobe Campaign, immetti l’URL della **[!UICONTROL Canvas page]** campo .


1. In **[!UICONTROL Image]** , immetti l’URL dell’immagine che verrà visualizzata a sinistra della pubblicazione.

   >[!IMPORTANT]
   >
   >L&#39;immagine deve essere ospitata su un sito Internet pubblico per consentire a Facebook di caricarla.

1. In **[!UICONTROL Caption]** immettere il testo che verrà visualizzato alla fine della pubblicazione.
1. Vai a **[!UICONTROL Description]** e immetti il testo da visualizzare sotto il titolo.

![](assets/social_facebook_delivery_005.png)

### Pubblicazione di uno stato con un collegamento YouTube {#publishing-a-status-with-a-youtube-link}

Questo tipo di contenuto consente di pubblicare un collegamento a un video di YouTube. Come per uno stato con un collegamento regolare, puoi definire uno stato, un nome, una didascalia, una descrizione e un collegamento aggiuntivo. L’immagine viene aggiunta automaticamente da Facebook. Di seguito sono descritte le simmetrie tra i campi della schermata di modifica della consegna e la pubblicazione finale su Facebook:

![](assets/social_facebook_delivery_youtube_1.png)

Inserisci i vari campi:

>[!IMPORTANT]
>
>Tutti gli URL devono iniziare con **&quot;http://&quot;** o **&quot;https://&quot;**.

1. In **[!UICONTROL Status]** immettere il testo che verrà visualizzato sotto il nome della pagina.
1. In **[!UICONTROL Name]** immettere il titolo della pubblicazione.
1. In **[!UICONTROL Video code]** , immetti il codice del video di YouTube. Ad esempio, per il collegamento &quot;https://www.youtube.com/watch?v=abc123456&#39;&quot;, il codice video sarà &quot;abc123456&quot;.
1. In **[!UICONTROL Caption]** immettere il testo che verrà visualizzato alla fine della pubblicazione.
1. Vai a **[!UICONTROL Description]** e immetti il testo da visualizzare sotto il titolo.

![](assets/social_facebook_delivery_youtube.png)

### Pubblicazione di un album fotografico {#publishing-a-photo-album}

Questo tipo di contenuto consente di pubblicare un album fotografico. È possibile aggiungere un nome e una descrizione per l&#39;album, nonché una didascalia per ogni foto. Di seguito sono descritte le simmetrie tra i campi della schermata di modifica della consegna e la pubblicazione finale su Facebook:

![](assets/social_facebook_delivery_photos_1.png)

Inserisci i vari campi:

1. Inizia inserendo il **[!UICONTROL Album name]**.
1. Quindi inserisci il **[!UICONTROL Description]** da visualizzare sopra le foto.
1. Per aggiungere una foto, fai clic sul pulsante **[!UICONTROL Add]** seleziona la foto e fai clic su **[!UICONTROL Open]**.
1. È possibile aggiungere una didascalia a ogni foto.

![](assets/social_facebook_delivery_photos.png)

## Anteprima {#previewing}

La **[!UICONTROL Preview]** consente di visualizzare il rendering della pubblicazione.

1. Fai clic sul pulsante **[!UICONTROL Preview]** scheda .
1. Fai clic sul pulsante **[!UICONTROL Test personalization]** menu a discesa e seleziona **[!UICONTROL Service]**.
1. In **[!UICONTROL Folder]** selezionare la cartella del servizio che contiene le pagine Facebook. Per impostazione predefinita, le pagine vengono memorizzate nella directory principale del **[!UICONTROL Facebook]** cartella del servizio.
1. Seleziona la pagina Facebook sulla quale desideri testare l’anteprima.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>L’anteprima potrebbe essere leggermente diversa dalla pubblicazione finale di Facebook. Si consiglia vivamente di inviare una prova prima della consegna finale per un rendering esatto della pubblicazione. Fai riferimento a [Invio della bozza](#sending-the-proof).

## Configurazione del tracciamento {#configuring-tracking}

Il tracciamento può essere visualizzato nei rapporti di consegna e nel **[!UICONTROL Edit > Tracking]** scheda della consegna e del servizio.

I clic sull’URL contenuto nella consegna vengono misurati da Adobe Campaign. Il numero di clic sul **[!UICONTROL Like]** il numero di commenti e il numero di ventole sono misurati da Facebook.

La configurazione del tracciamento è la stessa di una consegna e-mail. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/about-delivery-monitoring.md).

>[!NOTE]
>
>In **[!UICONTROL Publish to a brand page]** modello di consegna, il tracciamento è abilitato per impostazione predefinita.

## Invio della bozza {#sending-the-proof}

Si consiglia vivamente di inviare una prova della pubblicazione prima della consegna finale per visualizzare l’esatto rendering della pubblicazione su una pagina di test Facebook privata. Per ulteriori informazioni sulla creazione di una pagina di test Facebook privata, consulta [Creazione di una pagina Facebook di test](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). I passaggi per selezionare la bozza di destinazione sono descritti in [Selezione della destinazione della bozza](#selecting-the-proof-target).

La consegna delle prove è identica alle consegne delle e-mail. Fai riferimento a [questa sezione](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Invio del messaggio {#sending-the-message}

1. Una volta approvato il contenuto, fai clic sul pulsante **[!UICONTROL Send]** pulsante .
1. Seleziona **[!UICONTROL Deliver as soon as possible]** e fai clic su **[!UICONTROL Analyze]** pulsante .

   >[!NOTE]
   >
   >La **[!UICONTROL Postpone the delivery]** consente di posticipare la consegna a una data successiva.

   ![](assets/social_facebook_delivery_009.png)

1. Una volta completata l’analisi, controlla il risultato.
1. Fai clic su **[!UICONTROL Confirm delivery]**, quindi fai clic su **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)
