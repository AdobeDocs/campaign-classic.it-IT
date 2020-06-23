---
title: Inserimento di un’immagine dinamica
seo-title: Inserimento di un’immagine dinamica
description: Inserimento di un’immagine dinamica
seo-description: null
page-status-flag: never-activated
uuid: 4acc905e-625c-45aa-bb70-7dde22911aa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: f6e4d22b-4ad3-4a1e-8a6f-3bdfc1da0535
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 0%

---


# Inserimento di contenuto dinamico Target {#inserting-a-dynamic-image}

In questa guida verrà illustrato come integrare un&#39;offerta dinamica di Target in un&#39;e-mail  Adobe Campaign.

Vogliamo creare una consegna che includa un blocco immagine che verrà modificato dinamicamente in base al paese del destinatario. I dati vengono inviati con ciascuna richiesta mbox e dipendono dall&#39;indirizzo IP del visitatore.

In questo messaggio e-mail, desideriamo che una delle immagini possa variare dinamicamente in base alle seguenti esperienze utente:

* L&#39;e-mail viene aperta in Francia.
* L&#39;e-mail viene aperta negli Stati Uniti.
* Se non si applica nessuna di queste condizioni, viene visualizzata un&#39;immagine predefinita.

![](assets/target_4.png)

A tal fine, è necessario eseguire i seguenti passaggi sia in  Adobe Campaign che in Target:

1. [Inserimento dell’offerta dinamica in un messaggio e-mail](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Creazione di offerte di reindirizzamento](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Creazione di un pubblico](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Creazione di un&#39;attività Experience Targeting](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Anteprima e invio del messaggio e-mail](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Inserimento dell’offerta dinamica in un messaggio e-mail {#inserting-dynamic-offer}

Ad  Adobe Campaign, una volta definita la destinazione e il contenuto dell’e-mail, potete inserire un’immagine dinamica da Target.

A questo scopo, specificate l’URL dell’immagine predefinita, il nome del percorso e i campi che desiderate trasferire ad Target.

 Adobe Campaign, esistono due modi per inserire un’immagine dinamica da Target in un messaggio e-mail:

* Se utilizzate l’editor del contenuto digitale, scegliete un’immagine esistente e selezionate **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** dalla barra degli strumenti.

   ![](assets/target_5.png)

* Se usate l’editor standard, posizionate il cursore nel punto in cui desiderate inserire l’immagine e selezionate **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** dal menu a discesa Personalizzazione.

   ![](assets/target_12.png)

### Definizione dei parametri immagine {#defining-image-parameters}

* URL **[!UICONTROL Default image]** del sito: Immagine che verrà visualizzata quando nessuna delle condizioni è soddisfatta. Puoi anche selezionare un’immagine dalla libreria Risorse.
* Il **[!UICONTROL Target location]** seguente indirizzo: Immettete un nome per la posizione dell&#39;offerta dinamica. Dovrete selezionare questo percorso nell&#39;attività Target.
* Il **[!UICONTROL Landing Page]** seguente indirizzo: Se si desidera che l&#39;immagine predefinita venga reindirizzata a una pagina di destinazione predefinita. Questo URL è solo per i casi in cui l’immagine predefinita viene visualizzata nell’e-mail finale ed è facoltativa.
* Il **[!UICONTROL Additional decision parameters]** seguente indirizzo: Specificate la mappatura tra i campi definiti nei segmenti del Adobe Target  e i campi del Adobe Campaign . I campi  Adobe Campaign utilizzati devono essere stati specificati nella rawbox. Nel nostro esempio, abbiamo aggiunto il campo Paese.

Se utilizzate le autorizzazioni Enterprise nelle impostazioni  Adobe Target, aggiungete la proprietà corrispondente in questo campo. Ulteriori informazioni sulle autorizzazioni Target Enterprise in [questa pagina](https://docs.adobe.com/content/help/en/target/using/administer/manage-users/enterprise/properties-overview.html).

![](assets/target_13.png)

## Creazione di offerte di reindirizzamento {#create-redirect-offers}

In Target, potete creare diverse versioni dell’offerta. A seconda dell’esperienza utente, è possibile creare un’offerta di reindirizzamento e specificare l’immagine da visualizzare.

Nel nostro caso, abbiamo bisogno di due offerte di reindirizzamento, la terza (quella predefinita) deve essere definita in  Adobe Campaign.

1. Per creare una nuova offerta di reindirizzamento in Target Standard, fate clic su **[!UICONTROL Content]** nella **[!UICONTROL Code offers]** scheda.

1. Fate clic **[!UICONTROL Create]** quindi **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Immettete un nome per l’offerta e l’URL dell’immagine.

   ![](assets/target_6.png)

1. Seguite la stessa procedura per l&#39;offerta di reindirizzamento rimanente. For more on this, refer to this [page](https://docs.adobe.com/help/en/target/using/experiences/offers/offer-redirect.html).

## Creazione di un pubblico {#audiences-target}

In Target, è necessario creare i due tipi di pubblico in cui le persone che visiteranno l&#39;offerta verranno classificate per i diversi contenuti da distribuire. Per ogni audience, aggiungete una regola per definire chi sarà in grado di visualizzare l&#39;offerta.

1. Per creare una nuova audience in Target, dalla **[!UICONTROL Audiences]** scheda fare clic su **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Aggiungi un nome al pubblico.

   ![](assets/audiences_2.png)

1. Fate clic su **[!UICONTROL Add a rule]** e selezionate una categoria. La regola utilizza criteri specifici per eseguire il targeting dei visitatori. È possibile definire le regole aggiungendo condizioni o creando nuove regole in altre categorie.

1. Seguite la stessa procedura per i tipi di pubblico rimanenti.

## Creazione di un&#39;attività Experience Targeting {#creating-targeting-activity}

In Target, dobbiamo creare un&#39;attività Experience Targeting (Targeting delle esperienze), definire le diverse esperienze e associarle alle offerte corrispondenti.

### Defining the audience {#defining-the-audience}

1. Per creare un&#39;attività Experience Targeting, dalla **[!UICONTROL Activities]** scheda fai clic su **[!UICONTROL Create Activity]** quindi **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. Selezionare **[!UICONTROL Form]** come **[!UICONTROL Experience Composer]**.

1. Scegliete un&#39;audience facendo clic sul **[!UICONTROL Change audience]** pulsante.

   ![](assets/target_10_2.png)

1. Selezionate l&#39;audience creata nei passaggi precedenti.

   ![](assets/target_10_3.png)

1. Create un&#39;altra esperienza facendo clic su **[!UICONTROL Add Experience Targeting]**.

### Definizione della posizione e del contenuto {#defining-location-content}

Aggiungete un contenuto per ogni audience:

1. Selezionate il nome della posizione scelta al momento dell’inserimento dell’offerta dinamica in  Adobe Campaign.

   ![](assets/target_15.png)

1. Fate clic sul pulsante a discesa e selezionate **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Selezionate l’offerta di reindirizzamento precedentemente creata.

   ![](assets/target_content_2.png)

1. Seguite gli stessi passaggi per la seconda esperienza.

### Definizione dell&#39;attività {#defining-activity}

La **[!UICONTROL Target]** finestra riepiloga l&#39;attività. Se necessario, potete aggiungere altre esperienze.

![](assets/target_experience.png)

La **[!UICONTROL Goal & Settings]** finestra consente di personalizzare l&#39;attività impostando una priorità, un obiettivo o una durata.

La **[!UICONTROL Reporting Settings]** sezione consente di selezionare un&#39;azione e di modificare i parametri che determinano quando viene raggiunto l&#39;obiettivo.

![](assets/target_experience_2.png)

## Anteprima e invio del messaggio e-mail in Campaign Classic {#preview-send-email}

 Adobe Campaign, ora potete visualizzare l’anteprima dell’e-mail e verificarne il rendering su diversi destinatari. Noterete che l&#39;immagine cambia in base alle diverse esperienze create. Per ulteriori informazioni sulla creazione di e-mail, consultate questa [pagina](../../delivery/using/defining-the-email-content.md).

Ora è possibile inviare l&#39;e-mail con un&#39;offerta dinamica da Target.

![](assets/target_20.png)
