---
solution: Campaign Classic
product: campaign
title: SpamAssassin
description: Scopri come impostare il rilevamento di spam via e-mail con SpamAssassin
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---


# SpamAssassin{#spamassassin}

## SpamAssassin {#about-spamassassin}

 Adobe Campaign può essere configurato per l&#39;utilizzo di [SpamAssassin](https://spamassassin.apache.org), un servizio di terze parti utilizzato per il filtraggio dello spam via e-mail. Questo consente di segnare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

SpamAssassin sfrutta una serie di tecniche di rilevamento dello spam, tra cui:

* Rilevamento di spam basato su DNS e con checksum approssimativo
* Filtro bayesiano
* Programmi esterni
* elenchi Bloccati
* Database online

>[!NOTE]
>
>SpamAssassin deve essere installato e configurato sul server  applicazione Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-spamassassin.md).
>
>Le regole che determinano se un elemento è spam o meno vengono gestite tramite SpamAssassin e possono essere modificate da un amministratore con privilegi.

## Utilizzo di SpamAssassin {#using-spamassassin}

Dopo aver creato la consegna e-mail e definito il contenuto, effettuate le operazioni seguenti per valutare i rischi.

Per ulteriori informazioni sulla creazione e la progettazione di una consegna, consultare [questa sezione](../../delivery/using/about-email-channel.md).

1. Vai alla scheda **[!UICONTROL Preview]**. 
1. Seleziona un destinatario per visualizzare l&#39;anteprima della consegna.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Se non si seleziona un destinatario, il controllo anti-spam non può essere eseguito.

1. Un messaggio di avviso fornisce il risultato del test. Se viene rilevato un elevato livello di rischio, viene visualizzato il seguente messaggio di avviso:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Fare clic sul collegamento **[!UICONTROL More...]** accanto all&#39;avviso.
1. Seleziona la scheda **[!UICONTROL Anti-spam checking]**.
1. Andate alla sezione **[!UICONTROL Points / Rule / Description]** per vedere i motivi di questo rischio.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Ogni volta che si fa clic sul **[!UICONTROL Anti-spam checking]**, viene chiamato il servizio SpamAssassin e il messaggio viene nuovamente analizzato per il rilevamento di spam. Prima di eseguire nuovamente l&#39;analisi anti-spam, verificate di aver modificato il contenuto.
