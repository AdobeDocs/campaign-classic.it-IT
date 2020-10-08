---
title: Informazioni sulla recapito in Adobe Campaign Classic
description: Ulteriori informazioni sulla gestione della recapito in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Controllo del contenuto del messaggio{#control-message-content}

Per migliorare il tasso di recapito delle e-mail e assicurarsi che le e-mail arrivino ai destinatari, l&#39;e-mail deve rispettare un certo numero di regole descritte di seguito.

## Indirizzo mittente {#sender-address}

Alcuni ISP controllano la validità dell&#39;indirizzo del mittente (Da) prima di accettare i messaggi. Un indirizzo con formato non corretto potrebbe essere rifiutato dal server ricevente. È necessario assicurarsi che l&#39;indirizzo corretto sia specificato a livello di istanza (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) o negli scenari più frequentemente utilizzati.

## Collegamento e modulo di rifiuto {#opt-out}

Per impostazione predefinita, quando il messaggio viene analizzato, una regola di tipologia verifica se è stato incluso un collegamento di rinuncia e genera un avviso se risulta mancante. È possibile modificare questa regola in modo che venga generato un errore anziché un semplice avviso e impedire che una consegna venga eseguita senza questo collegamento.

È necessario verificare che il collegamento di rinuncia funzioni correttamente prima di ogni invio. Ad esempio, quando si invia la prova, verificare che il collegamento sia valido, che il modulo sia online e che la convalida di questo elemento modifichi il valore del **[!UICONTROL No longer contact this recipient]** campo in **[!UICONTROL Yes]**. È consigliabile eseguire questo controllo in modo sistematico perché l&#39;errore umano è sempre possibile quando si inserisce il collegamento o si modifica il modulo.

Se viene rilevato un problema relativo all&#39;annullamento dell&#39;iscrizione dopo l&#39;avvio della consegna, è comunque possibile eseguire un&#39;annullamento dell&#39;iscrizione manualmente (utilizzando, ad esempio, la funzione di aggiornamento di massa) per i destinatari che fanno clic sul collegamento di annullamento dell&#39;iscrizione anche se non sono stati in grado di confermare la scelta.

Come regola generale, non cercate di ostacolare i destinatari che desiderano rifiutare richiedendo loro di compilare campi quali ad esempio il loro indirizzo e-mail o nome. Il modulo deve avere un solo pulsante di convalida e la riconciliazione deve essere eseguita solo sull&#39;identificatore crittografato. La richiesta di conferma aggiuntiva non è affidabile: un utente può avere due indirizzi e-mail reindirizzati alla stessa casella (ad esempio: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se il destinatario è in grado di ricordare solo il primo indirizzo e desidera annullare l&#39;iscrizione tramite un messaggio inviato all&#39;altro, il modulo rifiuterà l&#39;indirizzo perché l&#39;identificatore crittografato e l&#39;indirizzo e-mail immesso non corrispondono.

## SpamAssassin {#spamassassin}

 Adobe Campaign può essere configurato per lavorare con SpamAssassin. Questo consente di segnare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

Prima di iniziare una consegna, la scheda Anteprima consente di valutare i rischi. Un messaggio di avviso fornisce il risultato del test.

Ulteriori informazioni in questa [sezione](../../delivery/using/spamassassin.md).