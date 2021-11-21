---
product: campaign
title: Informazioni sul recapito messaggi in Adobe Campaign Classic
description: Ulteriori informazioni sulla gestione del recapito messaggi in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 4%

---

# Controllo del contenuto del messaggio{#control-message-content}

![](../../assets/common.svg)

Per essere sicuri che le e-mail raggiungano i destinatari e migliorino il tasso di recapito delle e-mail, devono rispettare una serie di regole. In caso contrario, il contenuto di alcuni messaggi può essere rilevato come spam. Adobe Campaign offre diversi strumenti per rendere i contenuti conformi a queste regole.

Segui i principi elencati di seguito durante la progettazione del contenuto del messaggio:

* [Indirizzo mittente](#sender-address): l&#39;indirizzo deve identificare esplicitamente il mittente. Il dominio deve essere di proprietà e registrato al mittente. Il registro di dominio non deve essere privatizzato.
* [Personalizzazione](#personalization): la personalizzazione del contenuto e la definizione del tempo di invio per destinatario aumentano le possibilità di apertura del messaggio.
* Immagini e testo: rispettare un rapporto testo/immagine decente (ad esempio 60% di testo e 40% di immagini).
* [Collegamento di annullamento dell’abbonamento](#opt-out) e pagina di destinazione: il collegamento di annullamento dell’abbonamento è essenziale. Deve essere visibile e valido e il modulo deve essere funzionale.
* Anteprima: utilizza gli strumenti offerti da Adobe Campaign per controllare e ottimizzare il contenuto della tua e-mail ([Rendering della casella in entrata](#message-responsiveness), [SpamAssassin](#spamassassin)).

Per ulteriori suggerimenti su come ottimizzare il recapito messaggi durante la progettazione dei contenuti, consulta la sezione [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>Per ulteriori informazioni sulla modifica del contenuto delle e-mail, consulta [Definizione del contenuto dell’e-mail](defining-the-email-content.md) e [Creare contenuti personalizzati](design-and-personalize.md).

## Indirizzo mittente {#sender-address}

Alcuni ISP controllano la validità dell’indirizzo del mittente (**[!UICONTROL From]**) prima di accettare i messaggi. Un indirizzo formato in modo non corretto può causare il rifiuto da parte del server ricevente.

È necessario assicurarsi che a livello di istanza sia fornito un indirizzo corretto (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) o negli scenari più utilizzati.

Per ulteriori informazioni, consulta [Definizione del mittente](defining-the-email-content.md).

## Personalizzazione {#personalization}

Per migliorare l’esperienza dei destinatari e farli aprire l’e-mail, Adobe Campaign ti consente di personalizzare i messaggi.

Per ulteriori informazioni sull’utilizzo dei campi di personalizzazione in Adobe Campaign, consulta [questa sezione](personalization-fields.md).

Alcuni suggerimenti per ottimizzare la personalizzazione durante la creazione dei contenuti sono presentati in [questa sezione](design-and-personalize.md#optimize-personalization).

## Collegamento e modulo di rinuncia {#opt-out}

Per impostazione predefinita, quando il messaggio viene analizzato, un [regola di tipologia](steps-validating-the-delivery.md#validation-process-with-typologies) verifica se un collegamento di rinuncia è stato incluso e genera un avviso in caso di assenza. Puoi modificare questa regola in modo che venga generato un errore invece di un semplice avviso e impedire che una consegna venga interrotta senza questo collegamento.

Devi verificare che il collegamento di rinuncia funzioni correttamente prima di ogni invio. Ad esempio, quando invii la bozza, accertati che il collegamento sia valido, che il modulo sia online e che la convalida di questo modifichi il valore del **[!UICONTROL No longer contact this recipient]** campo a **[!UICONTROL Yes]**. È necessario eseguire questo controllo sistematicamente perché l’errore umano è sempre possibile quando si inserisce il collegamento o si modifica il modulo.

Scopri come inserire un collegamento di rinuncia [in questa sezione](personalization-blocks.md#personalization-blocks-example).

Se viene rilevato un problema relativo all’annullamento dell’abbonamento dopo l’avvio della consegna, è comunque possibile eseguire manualmente un’annullamento dell’abbonamento (utilizzando, ad esempio, la funzione di aggiornamento di massa) per i destinatari che fanno clic sul collegamento di rinuncia anche se non sono stati in grado di confermare la scelta.

Come regola generale, non cercare di ostacolare i destinatari che desiderano rinunciare richiedendo loro di compilare campi come ad esempio il loro indirizzo e-mail o nome. Il modulo deve avere un solo pulsante di convalida e la riconciliazione deve essere eseguita solo sull’identificatore crittografato.

La richiesta di conferma aggiuntiva non è affidabile: un utente può avere due indirizzi e-mail reindirizzati alla stessa casella (ad esempio: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se il destinatario è in grado di ricordare solo il primo indirizzo e desidera annullare l’iscrizione tramite un messaggio inviato all’altro, il modulo lo rifiuterà perché l’identificatore crittografato e l’indirizzo e-mail inserito non corrisponderanno.

## Rendering della casella in entrata {#message-responsiveness}

Prima di inviare il messaggio, puoi verificarne la reattività controllando l’aspetto del messaggio su diversi dispositivi. In questo modo sarà possibile visualizzarlo in modo ottimale su una varietà di client web, e-mail web e dispositivi.

Per ottenere questo risultato, Adobe Campaign acquisisce il rendering e lo rende disponibile in un report dedicato. Ciò ti permette di visualizzare in anteprima il messaggio inviato nei vari contesti in cui potrebbe essere ricevuto.

Per ulteriori informazioni, consulta [Rendering della casella in entrata](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign può essere configurato per lavorare con SpamAssassin. Questo consente di valutare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

Prima di avviare una consegna, il **[!UICONTROL Preview]** La scheda ti consente di valutare i rischi. Un messaggio di avviso fornisce il risultato del test.

Ulteriori informazioni [sezione](spamassassin.md).
