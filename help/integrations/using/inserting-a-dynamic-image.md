---
product: campaign
title: Inserimento di un’immagine dinamica
description: Inserimento di un’immagine dinamica
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 2%

---

# Inserimento di contenuto dinamico Target {#inserting-a-dynamic-image}

In questa guida verrà illustrato come integrare un’offerta dinamica da Target in un’e-mail in Adobe Campaign.

Vogliamo creare una consegna che includa un blocco immagine che cambierà dinamicamente in base al paese del destinatario. I dati vengono inviati con ogni richiesta mbox e dipendono dall’indirizzo IP del visitatore.

In questa e-mail, vogliamo che una delle immagini possa variare dinamicamente in base alle seguenti esperienze utente:

* L&#39;e-mail viene aperta in Francia.
* L’e-mail viene aperta negli Stati Uniti.
* Se non si applica nessuna di queste condizioni, viene visualizzata un&#39;immagine predefinita.

![](assets/target_4.png)

Affinché questo funzioni, è necessario eseguire i seguenti passaggi sia in Adobe Campaign che in Target:

1. [Inserimento dell’offerta dinamica in un messaggio e-mail](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Creazione di offerte di reindirizzamento](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Creazione di tipi di pubblico](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Creazione di un’attività Targeting esperienze](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Anteprima e invio del messaggio e-mail](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Inserimento dell’offerta dinamica in un messaggio e-mail {#inserting-dynamic-offer}

In Adobe Campaign, una volta definito il target e il contenuto dell’e-mail, puoi inserire un’immagine dinamica da Target.

A questo scopo, specifica l’URL dell’immagine predefinita, il nome della posizione e i campi da trasferire a Target.

In Adobe Campaign, esistono due modi per inserire un’immagine dinamica da Target in un messaggio e-mail:

* Se utilizzi l’editor di contenuti digitali, scegli un’immagine esistente e seleziona **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** dalla barra degli strumenti.

   ![](assets/target_5.png)

* Se utilizzi l’editor standard, posiziona il cursore nel punto in cui desideri inserire l’immagine e seleziona **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** dal menu a discesa di personalizzazione.

   ![](assets/target_12.png)

### Definizione dei parametri immagine {#defining-image-parameters}

* L&#39;URL di **[!UICONTROL Default image]**: Immagine che verrà visualizzata quando non viene soddisfatta alcuna condizione. Puoi anche selezionare un’immagine dalla libreria Risorse.
* Il **[!UICONTROL Target location]**: Immetti un nome per la posizione dell’offerta dinamica. Dovrai selezionare questa posizione nell’attività di Target.
* Il **[!UICONTROL Landing Page]**: Se desideri reindirizzare l’immagine predefinita a una pagina di destinazione predefinita. Questo URL è adatto solo nei casi in cui l’immagine predefinita viene visualizzata nell’e-mail finale ed è facoltativa.
* Il **[!UICONTROL Additional decision parameters]**: Specifica la mappatura tra i campi definiti nei segmenti Adobe Target e i campi Adobe Campaign. I campi Adobe Campaign utilizzati devono essere stati specificati nella rawbox. Nel nostro esempio, è stato aggiunto il campo Paese .

Se utilizzi le autorizzazioni Enterprise nelle impostazioni di Adobe Target, aggiungi la proprietà corrispondente in questo campo. Ulteriori informazioni sulle autorizzazioni Enterprise di Target in [questa pagina](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html).

![](assets/target_13.png)

## Creazione di offerte di reindirizzamento {#create-redirect-offers}

In Target puoi creare diverse versioni dell’offerta. A seconda di ogni esperienza utente, è possibile creare un’offerta di reindirizzamento e specificare l’immagine da visualizzare.

Nel nostro caso, sono necessarie due offerte di reindirizzamento, la terza (quella predefinita) deve essere definita in Adobe Campaign.

1. Per creare una nuova offerta di reindirizzamento in Target Standard, dalla scheda **[!UICONTROL Content]** fai clic su **[!UICONTROL Code offers]**.

1. Fai clic su **[!UICONTROL Create]**, quindi su **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Immetti un nome per l’offerta e l’URL dell’immagine.

   ![](assets/target_6.png)

1. Segui la stessa procedura per l’offerta di reindirizzamento rimanente. Per ulteriori informazioni, consulta questa [pagina](https://docs.adobe.com/help/en/target/using/experiences/offers/offer-redirect.html).

## Creazione di tipi di pubblico {#audiences-target}

In Target, devi creare i due tipi di pubblico in cui le persone che visitano la tua offerta verranno categorizzate per i diversi contenuti da consegnare. Per ogni pubblico, aggiungi una regola per definire chi potrà visualizzare l’offerta.

1. Per creare un nuovo pubblico in Target, dalla scheda **[!UICONTROL Audiences]** fai clic su **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Aggiungi un nome al pubblico.

   ![](assets/audiences_2.png)

1. Fai clic su **[!UICONTROL Add a rule]** e seleziona una categoria. La regola utilizza criteri specifici per il targeting dei visitatori. Puoi perfezionare le regole aggiungendo condizioni o creando nuove regole in altre categorie.

1. Segui la stessa procedura per i tipi di pubblico rimanenti.

## Creazione di un’attività Targeting esperienze {#creating-targeting-activity}

In Target, dobbiamo creare un’attività Targeting esperienze, definire le diverse esperienze e associarle alle offerte corrispondenti.

### Definizione del pubblico {#defining-the-audience}

1. Per creare un’attività Targeting esperienze, dalla scheda **[!UICONTROL Activities]** fai clic su **[!UICONTROL Create Activity]** , quindi **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. Seleziona **[!UICONTROL Form]** come **[!UICONTROL Experience Composer]**.

1. Scegli un pubblico facendo clic sul pulsante **[!UICONTROL Change audience]** .

   ![](assets/target_10_2.png)

1. Seleziona il pubblico creato nei passaggi precedenti.

   ![](assets/target_10_3.png)

1. Crea un’altra esperienza facendo clic su **[!UICONTROL Add Experience Targeting]**.

### Definizione della posizione e del contenuto {#defining-location-content}

Aggiungi un contenuto per ogni pubblico:

1. Seleziona il nome della posizione scelto al momento dell’inserimento dell’offerta dinamica in Adobe Campaign.

   ![](assets/target_15.png)

1. Fai clic sul pulsante a discesa e seleziona **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Seleziona l’offerta di reindirizzamento creata in precedenza.

   ![](assets/target_content_2.png)

1. Segui gli stessi passaggi per la seconda esperienza.

### Definizione dell’attività {#defining-activity}

La finestra **[!UICONTROL Target]** riepiloga l’attività. Se necessario, puoi aggiungere altre esperienze.

![](assets/target_experience.png)

La finestra **[!UICONTROL Goal & Settings]** ti consente di personalizzare l’attività impostando una priorità, un obiettivo o una durata.

La sezione **[!UICONTROL Reporting Settings]** ti consente di selezionare un’azione e di modificare i parametri che determinano quando viene raggiunto l’obiettivo.

![](assets/target_experience_2.png)

## Anteprima e invio dell’e-mail in Campaign Classic {#preview-send-email}

In Adobe Campaign, ora puoi visualizzare l’anteprima del messaggio e-mail e testarne il rendering su destinatari diversi. Noterai che l’immagine cambia in base alle diverse esperienze create. Per ulteriori informazioni sulla creazione di e-mail, consulta questa [pagina](../../delivery/using/defining-the-email-content.md).

Ora puoi inviare il tuo messaggio e-mail, inclusa un’offerta dinamica da Target.

![](assets/target_20.png)
