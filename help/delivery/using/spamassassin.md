---
product: campaign
title: SpamAssassin
description: Scopri come impostare il rilevamento di spam e-mail con SpamAssassin
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# SpamAssassin{#spamassassin}

![](../../assets/common.svg)

Adobe Campaign può essere configurato per lavorare con [SpamAssassin](https://spamassassin.apache.org), un servizio di terze parti utilizzato per il filtraggio degli spam e-mail. Questo ti consente di valutare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

SpamAssassin sfrutta una varietà di tecniche di rilevamento dello spam, tra cui:

* Rilevamento di spam basato su DNS e con checksum approssimativo
* Filtro bayesiano
* Programmi esterni
* Elenchi Bloccati
* Database online

>[!NOTE]
>
>SpamAssassin deve essere installato e configurato sul server dell&#39;applicazione Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-spamassassin.md).
>
>Le regole che determinano se un elemento è spam o meno vengono gestite tramite SpamAssassin e possono essere modificate da un amministratore con privilegi di .

## Utilizzare SpamAssassin in Campaign {#using-spamassassin}

Dopo aver creato la consegna e-mail e averne definito il contenuto, segui la procedura seguente per valutare i rischi.

Per ulteriori informazioni sulla creazione e la progettazione di una consegna, consulta [questa sezione](about-email-channel.md).

1. Vai alla scheda **[!UICONTROL Preview]**. 
1. Seleziona un destinatario per visualizzare l’anteprima della consegna.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Se non si seleziona un destinatario, non è possibile eseguire il controllo anti-spam.

1. Un messaggio di avviso fornisce il risultato del test. Se viene rilevato un elevato livello di rischio, viene visualizzato il seguente messaggio di avviso:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Fai clic sul pulsante **[!UICONTROL More...]** accanto all’avviso.
1. Seleziona la scheda **[!UICONTROL Anti-spam checking]**.
1. Vai a **[!UICONTROL Points / Rule / Description]** per visualizzare i motivi di questo rischio.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Ogni volta che fai clic sul pulsante **[!UICONTROL Anti-spam checking]**, viene chiamato il servizio SpamAssassin e il messaggio viene nuovamente analizzato per il rilevamento di anti-spam. Assicurati di aver modificato il contenuto prima di eseguire nuovamente l’analisi anti-spam.
