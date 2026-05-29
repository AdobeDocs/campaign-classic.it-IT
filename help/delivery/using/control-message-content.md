---
product: campaign
title: Informazioni sul recapito messaggi in Adobe Campaign Classic
description: Ulteriori informazioni sulla gestione del recapito messaggi in Adobe Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
TQID: https://experienceleague.adobe.com/5O5mdQrj0-Ts1C-lZRDHqDYwit4dSUOZHzG5SVDVitA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 842
ht-degree: 5%

---

# Controllare il contenuto del messaggio{#control-message-content}

Per fare in modo che le e-mail raggiungano i destinatari e migliorare il tasso di recapito dei messaggi e-mail, devono rispettare una serie di regole. In caso contrario, il contenuto di alcuni messaggi potrebbe essere rilevato come spam. Adobe Campaign fornisce diversi strumenti per rendere i contenuti conformi a queste regole.

Durante la progettazione del contenuto del messaggio, segui i principi elencati di seguito:

* [Indirizzo mittente](#sender-address): l&#39;indirizzo deve identificare esplicitamente il mittente. Il dominio deve essere di proprietà del mittente e deve essere registrato presso di esso. Impossibile privatizzare il Registro di sistema del dominio.
* [Personalization](#personalization): la personalizzazione del contenuto e la definizione di un tempo di invio per destinatario aumentano le possibilità che il messaggio venga aperto.
* Immagini e testo: rispetta un rapporto testo/immagine decente (ad esempio 60% di testo e 40% di immagini).
* [Collegamento per l&#39;annullamento dell&#39;abbonamento](#opt-out) e pagina di destinazione: il collegamento per l&#39;annullamento dell&#39;abbonamento è essenziale. Deve essere visibile e valido e il modulo deve essere funzionale.
* Anteprima: utilizza gli strumenti offerti da Adobe Campaign per verificare e ottimizzare il contenuto dell&#39;e-mail ([Rendering della casella in entrata](#message-responsiveness), [SpamAssassin](#spamassassin)).

Per ulteriori suggerimenti per ottimizzare il recapito messaggi durante la progettazione del contenuto, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>Per ulteriori informazioni sulla modifica del contenuto delle e-mail, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html){target="_blank"}.

## Indirizzo mittente {#sender-address}

Alcuni ISP verificano la validità dell&#39;indirizzo del mittente (**[!UICONTROL From]**) prima di accettare i messaggi. Un indirizzo con formato non corretto può comportare il rifiuto da parte del server ricevente.

È necessario assicurarsi che sia fornito un indirizzo corretto a livello di istanza (menu **[!UICONTROL Tools > Advanced > deployment wizard...]**) o negli scenari utilizzati più di frequente.

Per ulteriori informazioni, fai riferimento alla [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html){target="_blank"}.

## Personalizzazione {#personalization}

Per migliorare l’esperienza dei destinatari e farli aprire l’e-mail, Adobe Campaign ti consente di personalizzare i messaggi.

Per ulteriori informazioni sull&#39;utilizzo dei campi di personalizzazione in Adobe Campaign, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/personalize/personalization-fields){target="_blank"}.

## Collegamento e modulo per la rinuncia {#opt-out}

Per impostazione predefinita, quando il messaggio viene analizzato, una regola di tipologia controlla se è stato incluso un collegamento di rinuncia e, in caso contrario, genera un avviso. Puoi modificare questa regola in modo da generare un errore anziché un semplice avviso e interrompere una consegna senza questo collegamento. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html){target="_blank"}.

Prima di ogni invio, verifica che il collegamento di rinuncia funzioni correttamente. Ad esempio, quando invii la bozza, accertati che il collegamento sia valido, che il modulo sia in linea e che la convalida di questo modifichi il valore del campo **[!UICONTROL No longer contact this recipient]** in **[!UICONTROL Yes]**. Dovresti effettuare questo controllo in modo sistematico perché è sempre possibile un errore umano durante l’immissione del collegamento o la modifica del modulo.

Scopri come inserire una rinuncia nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html){target="_blank"}.

Se viene rilevato un problema relativo all’annullamento dell’abbonamento dopo l’avvio della consegna, è ancora possibile eseguire manualmente un annullamento dell’abbonamento (ad esempio, utilizzando la funzione di aggiornamento di massa) per i destinatari che fanno clic sul collegamento di rinuncia anche se non sono stati in grado di confermare la scelta.

Come regola generale, non cercare di intralciare i destinatari che desiderano rinunciare richiedendo loro di compilare campi come il loro indirizzo e-mail o nome, ad esempio. Il modulo deve avere un solo pulsante di convalida e la riconciliazione deve essere eseguita solo sull’identificatore crittografato.

La richiesta di conferma aggiuntiva non è affidabile: un utente può avere due indirizzi e-mail reindirizzati alla stessa casella (ad esempio: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se il destinatario è in grado di ricordare solo il primo indirizzo e desidera annullare l’abbonamento tramite un messaggio inviato all’altro, il modulo lo rifiuterà perché l’identificatore crittografato e l’indirizzo e-mail inserito non corrisponderanno.

## Rendering della casella in entrata {#message-responsiveness}

Prima di inviare il messaggio, puoi verificarne la reattività controllando come si presenterà su diversi dispositivi. In questo modo, si assicurerà che venga visualizzato in modo ottimale su diversi client web, servizi di posta sul web e dispositivi.

Per ottenere questo risultato, Adobe Campaign acquisisce il rendering e lo rende disponibile in un report dedicato. Questo ti permette di visualizzare in anteprima il messaggio inviato nei vari contesti in cui potrebbe essere ricevuto.

Per ulteriori informazioni, consulta [Rendering in entrata](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign può essere configurato per funzionare con SpamAssassin. Questo consente di valutare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

Prima di avviare una consegna, la scheda **[!UICONTROL Preview]** consente di valutare i rischi. Un messaggio di avvertenza fornisce il risultato del test.

Ulteriori informazioni in questa [sezione](spamassassin.md).
