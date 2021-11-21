---
product: campaign
title: 'Caso di utilizzo: creazione di una consegna e-mail'
description: Creazione di un caso di utilizzo di consegna e-mail
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Caso d’uso: creazione di una consegna e-mail{#use-case-creating-an-email-delivery}

![](../../assets/common.svg)

In questo caso d’uso, imparerai a progettare una consegna e-mail utilizzando Adobe Campaign Digital Content Editor (DCE).

Il nostro obiettivo finale è quello di creare una consegna con un modello personalizzato che contiene:

* Un indirizzo diretto per un destinatario (utilizzando il nome e il secondo nome)
* Due tipi di collegamenti a un URL esterno
* Una pagina speculare
* Collegamento a un&#39;applicazione Web

>[!NOTE]
>
>Prima di iniziare, devi averne almeno uno **Modello HTML** configurato per ospitare il contenuto delle consegne future.
>
>Nella consegna **[!UICONTROL Properties]**, assicurati che **[!UICONTROL Content editing mode]** (in **[!UICONTROL Advanced]** è impostato su **[!UICONTROL DCE]**. Per garantire il funzionamento ottimale dell’editor, fai riferimento alla [Best practice per la modifica dei contenuti](content-editing-best-practices.md).

## Passaggio 1 - Creazione di una consegna {#step-1---creating-a-delivery}

Per creare una nuova consegna, posiziona il cursore nel **Campagne** e fai clic su **Consegne**. Fai clic su **Crea** , sopra l’elenco delle consegne esistenti. Per ulteriori informazioni sulla creazione di consegne, consulta [questa pagina](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Passaggio 2: selezionare un modello {#step-2---selecting-a-template}

Seleziona un modello di consegna, quindi assegna un nome alla consegna. Questo nome sarà visibile solo agli utenti della console Adobe Campaign e non ai destinatari, tuttavia questa intestazione verrà visualizzata nell’elenco delle consegne. Fai clic su **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Passaggio 3: selezionare un contenuto {#step-3---selecting-a-content}

L’editor di contenuti digitali è dotato di vari modelli predefiniti con strutture diverse (colonne, aree di testo, ecc.).

Seleziona il modello di contenuto da utilizzare, quindi fai clic sul pulsante **[!UICONTROL Start with the selected content]** per visualizzare il modello nella consegna creata.

![](assets/dce_select_model.png)

Puoi anche importare un contenuto HTML creato al di fuori di Adobe Campaign selezionando **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Puoi salvare il contenuto come modello da utilizzare in futuro. Una volta creato un modello di contenuto personalizzato, puoi visualizzarlo in anteprima dall’elenco dei modelli. Per ulteriori informazioni, consulta [Gestione dei modelli](template-management.md).

>[!CAUTION]
>
>Se utilizzi **Interfaccia web Adobe Campaign**, è necessario importare un file .zip contenente il contenuto di HTML e le immagini correlate.

## Passaggio 4: progettare il messaggio {#step-4---designing-the-message}

* Visualizza il nome e il secondo nome dei destinatari

   Per inserire il nome e il nome dei destinatari in un campo di testo nella consegna, fai clic sul campo di testo scelto, quindi posiziona il cursore nel punto in cui desideri visualizzarli. Fai clic sulla prima icona nella barra degli strumenti a comparsa, quindi fai clic su **[!UICONTROL Personalization block]**. Seleziona **[!UICONTROL Greetings]**, quindi fai clic su **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Inserire un collegamento in un’immagine

   Per indirizzare i destinatari a un indirizzo esterno tramite un’immagine, fai clic sull’immagine corrispondente per visualizzare la barra degli strumenti a comparsa, posiziona il cursore sulla prima icona e fai clic su **[!UICONTROL Link to an external URL]**. Per ulteriori informazioni, consulta [Aggiunta di un collegamento](editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Immetti l’URL del collegamento nel **URL** utilizzando il formato seguente **https://www.myURL.com**, quindi conferma.

   Il collegamento può essere modificato in qualsiasi momento utilizzando la sezione a destra della finestra.

* Inserire un collegamento nel testo

   Per integrare un collegamento esterno nel testo della consegna, seleziona un testo o un blocco di testo, quindi fai clic sulla prima icona nella barra degli strumenti a comparsa. Fai clic su **[!UICONTROL Link to an external URL]**, inserisci l&#39;indirizzo del collegamento nel **[!UICONTROL URL]** campo . Per ulteriori informazioni, consulta [Aggiunta di un collegamento](editing-content.md#adding-a-link).

   Il collegamento può essere modificato in qualsiasi momento utilizzando la sezione a destra della finestra.

   >[!CAUTION]
   >
   >Il testo immesso nel campo **[!UICONTROL Label]** sostituisce il testo originale.

* Aggiungere una pagina speculare

   Per consentire ai destinatari di visualizzare il contenuto della consegna in un browser Web, puoi integrare nella consegna un collegamento a una pagina speculare.

   Fare clic sul campo di testo in cui si desidera visualizzare il collegamento pubblicato. Fai clic sulla prima icona nella barra degli strumenti a comparsa, seleziona **[!UICONTROL Personalization block]**, quindi **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Fai clic su **[!UICONTROL Save]** per confermare.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >L’etichetta del blocco di personalizzazione sostituisce automaticamente il testo originale nella consegna.

* Integrare un collegamento a un’applicazione Web

   L’editor di contenuti digitali consente di integrare i collegamenti alle applicazioni Web dalla console Adobe Campaign, ad esempio una pagina di destinazione o una pagina del modulo. Per ulteriori informazioni, consulta [Collegamento a un&#39;applicazione Web](editing-content.md#link-to-a-web-application).

   Selezionare un campo di testo per il collegamento a un&#39;applicazione Web, quindi fare clic sulla prima icona. Scegli **[!UICONTROL Link to a Web application]**, quindi seleziona l’applicazione desiderata facendo clic sull’icona alla fine del **Applicazione Web** campo .

   ![](assets/dce_webapp.png)

   Fai clic su **Salva** per confermare.

   >[!NOTE]
   >
   >Questo passaggio richiede di salvare almeno un&#39;applicazione Web in anticipo. Questi sono disponibili nella **[!UICONTROL Campaigns > Web applications]** della console.

## Passaggio 5 - Salvataggio della consegna {#step-5---saving-the-delivery}

Una volta integrato il contenuto, salva la consegna facendo clic su **Salva**. Ora verrà visualizzato nell’elenco delle consegne, disponibile nella sezione **[!UICONTROL Campaigns > Deliveries]** scheda .
