---
product: campaign
title: Informazioni sul recapito messaggi in Adobe Campaign Classic
description: Ulteriori informazioni sulla gestione del recapito messaggi in Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 6%

---

# Controllare il contenuto del messaggio{#control-message-content}


Per fare in modo che le e-mail raggiungano i destinatari e migliorare il tasso di recapito dei messaggi e-mail, devono rispettare una serie di regole. In caso contrario, il contenuto di alcuni messaggi potrebbe essere rilevato come spam. Adobe Campaign fornisce diversi strumenti per rendere i contenuti conformi a queste regole.

Durante la progettazione del contenuto del messaggio, segui i principi elencati di seguito:

* [Indirizzo mittente](#sender-address): l’indirizzo deve identificare esplicitamente il mittente. Il dominio deve essere di proprietà del mittente e deve essere registrato presso di esso. Impossibile privatizzare il Registro di sistema del dominio.
* [Personalizzazione](#personalization): la personalizzazione del contenuto e la definizione di un tempo di invio per destinatario aumentano le possibilità che il messaggio venga aperto.
* Immagini e testo: rispetta un rapporto testo/immagine decente (ad esempio 60% di testo e 40% di immagini).
* [Collegamento per annullare l’iscrizione](#opt-out) e pagina di destinazione: il collegamento di annullamento dell’abbonamento è essenziale. Deve essere visibile e valido e il modulo deve essere funzionale.
* Anteprima: utilizza gli strumenti offerti da Adobe Campaign per verificare e ottimizzare il contenuto dell’e-mail ([Rendering casella in entrata](#message-responsiveness), [SpamAssassin](#spamassassin)).

Per ulteriori suggerimenti su come ottimizzare il recapito messaggi durante la progettazione dei contenuti, consulta [Guida alle procedure consigliate per la consegna dei messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>Per ulteriori informazioni sulla modifica del contenuto delle e-mail, consulta [Definire il contenuto dell’e-mail](defining-the-email-content.md) e [Creare contenuti personalizzati](design-and-personalize.md).

## Indirizzo mittente {#sender-address}

Alcuni ISP verificano la validità dell&#39;indirizzo del mittente (**[!UICONTROL From]**) prima di accettare i messaggi. Un indirizzo con formato non corretto può comportare il rifiuto da parte del server ricevente.

È necessario assicurarsi che venga fornito un indirizzo corretto a livello di istanza (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) o negli scenari più utilizzati.

Per ulteriori informazioni, consulta [questa pagina](defining-the-email-content.md).

## Personalizzazione {#personalization}

Per migliorare l’esperienza dei destinatari e farli aprire l’e-mail, Adobe Campaign ti consente di personalizzare i messaggi.

Per ulteriori informazioni sull’utilizzo dei campi di personalizzazione in Adobe Campaign, consulta [questa sezione](personalization-fields.md).

Alcuni suggerimenti per ottimizzare la personalizzazione durante la creazione dei contenuti sono presentati in [questa sezione](design-and-personalize.md#optimize-personalization).

## Collegamento e modulo per la rinuncia {#opt-out}

Per impostazione predefinita, quando il messaggio viene analizzato, viene [regola di tipologia](steps-validating-the-delivery.md#validation-process-with-typologies) controlla se è stato incluso un collegamento di rinuncia e, in caso contrario, genera un avviso. Puoi modificare questa regola in modo da generare un errore anziché un semplice avviso e interrompere una consegna senza questo collegamento.

Prima di ogni invio, verifica che il collegamento di rinuncia funzioni correttamente. Ad esempio, quando invii la bozza, accertati che il collegamento sia valido, che il modulo sia in linea e che la convalida di questo modifichi il valore di **[!UICONTROL No longer contact this recipient]** campo a **[!UICONTROL Yes]**. Dovresti effettuare questo controllo in modo sistematico perché è sempre possibile un errore umano durante l’immissione del collegamento o la modifica del modulo.

Scopri come inserire un collegamento di rinuncia [in questa sezione](personalization-blocks.md#personalization-blocks-example).

Se viene rilevato un problema relativo all’annullamento dell’abbonamento dopo l’avvio della consegna, è ancora possibile eseguire manualmente un annullamento dell’abbonamento (ad esempio, utilizzando la funzione di aggiornamento di massa) per i destinatari che fanno clic sul collegamento di rinuncia anche se non sono stati in grado di confermare la scelta.

Come regola generale, non cercare di intralciare i destinatari che desiderano rinunciare richiedendo loro di compilare campi come il loro indirizzo e-mail o nome, ad esempio. Il modulo deve avere un solo pulsante di convalida e la riconciliazione deve essere eseguita solo sull’identificatore crittografato.

La richiesta di conferma aggiuntiva non è affidabile: un utente può avere due indirizzi e-mail reindirizzati alla stessa casella (ad esempio: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se il destinatario è in grado di ricordare solo il primo indirizzo e desidera annullare l’abbonamento tramite un messaggio inviato all’altro, il modulo lo rifiuterà perché l’identificatore crittografato e l’indirizzo e-mail inserito non corrisponderanno.

## Rendering della casella in entrata {#message-responsiveness}

Prima di inviare il messaggio, puoi verificarne la reattività controllando come si presenterà su diversi dispositivi. In questo modo, si assicurerà che venga visualizzato in modo ottimale su diversi client web, servizi di posta sul web e dispositivi.

Per ottenere questo risultato, Adobe Campaign acquisisce il rendering e lo rende disponibile in un report dedicato. Ciò ti permette di visualizzare in anteprima il messaggio inviato nei vari contesti in cui potrebbe essere ricevuto.

Per ulteriori informazioni, consulta [Rendering casella in entrata](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign può essere configurato per funzionare con SpamAssassin. Questo consente di valutare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

Prima di iniziare una consegna, il **[!UICONTROL Preview]** consente di valutare i rischi. Un messaggio di avvertenza fornisce il risultato del test.

Ulteriori informazioni [sezione](spamassassin.md).
