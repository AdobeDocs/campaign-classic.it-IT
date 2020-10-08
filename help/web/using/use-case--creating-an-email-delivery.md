---
title: '"Caso d’uso: creazione di una consegna e-mail"'
seo-title: '"Caso d’uso: creazione di una consegna e-mail"'
description: '"Caso d’uso: creazione di una consegna e-mail"'
seo-description: null
page-status-flag: never-activated
uuid: 7cd6329c-63d5-4cf0-9451-f0b4c2eaf0dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 4ec34980-62a2-47b9-b103-de4290925624
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 3%

---


# Caso d’uso: creazione di una consegna e-mail{#use-case-creating-an-email-delivery}

In questo caso di utilizzo, verranno illustrati i passaggi necessari per progettare una distribuzione di e-mail utilizzando  Adobe Campaign Digital Content Editor (DCE).

Il nostro obiettivo finale è quello di creare una consegna con un modello personalizzato che contenga:

* Un indirizzo diretto per un destinatario (utilizzando i nomi e i secondi)
* Due tipi di collegamenti a un URL esterno
* Una pagina mirror
* Collegamento a un&#39;applicazione Web

>[!NOTE]
>
>Prima di iniziare, dovete avere almeno un modello **** HTML configurato per ospitare il contenuto delle consegne future.
>
>Nella consegna **[!UICONTROL Properties]** , assicurarsi che **[!UICONTROL Content editing mode]** (nella **[!UICONTROL Advanced]** scheda) sia impostato su **[!UICONTROL DCE]**. Per garantire il funzionamento ottimale dell&#39;editor, consultare le best practice per la modifica dei [contenuti](../../web/using/content-editing-best-practices.md).

## Passaggio 1 - Creazione di una consegna {#step-1---creating-a-delivery}

Per creare una nuova consegna, posizionate il cursore nella scheda **Campagne** e fate clic su **Consegne**. Fare clic sul pulsante **Crea** sopra l&#39;elenco delle consegne esistenti. For more on creating deliveries, refer to [this page](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Passaggio 2 - Selezione di un modello {#step-2---selecting-a-template}

Selezionate un modello di consegna, quindi assegnate un nome alla consegna. Questo nome sarà visibile solo agli utenti della console  Adobe Campaign e non ai destinatari, ma questa intestazione verrà visualizzata nell’elenco delle consegne. Fai clic su **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Passaggio 3 - Selezione di un contenuto {#step-3---selecting-a-content}

Digital Content Editor viene fornito con diversi modelli out-of-the-box con strutture variabili (colonne, aree di testo, ecc.).

Selezionate il modello di contenuto da utilizzare, quindi fate clic sul **[!UICONTROL Start with the selected content]** pulsante per visualizzare il modello nella consegna creata.

![](assets/dce_select_model.png)

Potete anche importare un contenuto HTML creato al di fuori di  Adobe Campaign selezionando **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Potete salvare questo contenuto come modello da utilizzare in futuro. Una volta creato un modello di contenuto personalizzato, potete visualizzarlo in anteprima dall&#39;elenco dei modelli. For more on this, refer to [Template management](../../web/using/template-management.md).

>[!CAUTION]
>
>Se utilizzate l&#39;interfaccia **Web** Adobe Campaign, dovete importare un file .zip contenente il contenuto HTML e le immagini correlate.

## Passaggio 4 - Progettazione del messaggio {#step-4---designing-the-message}

* Visualizza il nome e il secondo dei destinatari

   Per inserire il primo e il secondo nome dei destinatari in un campo di testo nella consegna, fare clic sul campo di testo selezionato, quindi posizionare il cursore nel punto in cui si desidera visualizzarli. Fate clic sulla prima icona nella barra degli strumenti a comparsa, quindi fate clic su **[!UICONTROL Personalization block]**. Selezionate **[!UICONTROL Greetings]**, quindi fate clic su **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Inserire un collegamento in un’immagine

   Per indirizzare i destinatari della consegna a un indirizzo esterno tramite un&#39;immagine, fai clic sull&#39;immagine desiderata per visualizzare la barra degli strumenti a comparsa, posiziona il cursore sulla prima icona e fai clic **[!UICONTROL Link to an external URL]**. Per ulteriori informazioni, vedere [Aggiunta di un collegamento](../../web/using/editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Immettete l’URL del collegamento nel campo **URL** utilizzando il seguente formato **https://www.myURL.com**, quindi confermate.

   Il collegamento può essere modificato in qualsiasi momento utilizzando la sezione a destra della finestra.

* Inserire un collegamento nel testo

   Per integrare un collegamento esterno nel testo, selezionate del testo o un blocco di testo, quindi fate clic sulla prima icona nella barra degli strumenti a comparsa. Fare clic **[!UICONTROL Link to an external URL]**, inserire l&#39;indirizzo del collegamento nel **[!UICONTROL URL]** campo. Per ulteriori informazioni, vedere [Aggiunta di un collegamento](../../web/using/editing-content.md#adding-a-link).

   Il collegamento può essere modificato in qualsiasi momento utilizzando la sezione a destra della finestra.

   >[!CAUTION]
   >
   >Il testo immesso nel **[!UICONTROL Label]** campo sostituisce il testo originale.

* Aggiungere una pagina mirror

   Per consentire ai destinatari di visualizzare il contenuto della distribuzione in un browser Web, potete integrare nella distribuzione un collegamento a una pagina mirror.

   Fare clic sul campo di testo in cui si desidera visualizzare il collegamento pubblicato. Fate clic sulla prima icona nella barra degli strumenti a comparsa, selezionate **[!UICONTROL Personalization block]**, quindi **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Fate clic **[!UICONTROL Save]** per confermare.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >L’etichetta del blocco di personalizzazione sostituisce automaticamente il testo originale nella distribuzione.

* Integrazione di un collegamento a un&#39;applicazione Web

   Digital Content Editor consente di integrare i collegamenti alle applicazioni Web dalla console  Adobe Campaign, ad esempio una pagina di destinazione o una pagina di modulo. Per ulteriori informazioni, vedere [Collegamento a un&#39;applicazione](../../web/using/editing-content.md#link-to-a-web-application)Web.

   Selezionare un campo di testo per il collegamento a un&#39;applicazione Web, quindi fare clic sulla prima icona. Scegliete **[!UICONTROL Link to a Web application]**, quindi selezionate l&#39;applicazione desiderata facendo clic sull&#39;icona alla fine del campo Applicazione **** Web.

   ![](assets/dce_webapp.png)

   Fate clic su **Salva** per confermare.

   >[!NOTE]
   >
   >Questo passaggio richiede di salvare almeno un&#39;applicazione Web prima. che si trovano nella **[!UICONTROL Campaigns > Web applications]** scheda della console.

## Passaggio 5 - Salvataggio della consegna {#step-5---saving-the-delivery}

Una volta integrato il contenuto, salvate la distribuzione facendo clic su **Salva**. Ora verrà visualizzato nell&#39;elenco delle consegne, disponibile nella **[!UICONTROL Campaigns > Deliveries]** scheda.
