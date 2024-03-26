---
product: campaign
title: SpamAssassin
description: Scopri come impostare il rilevamento di posta indesiderata con SpamAssassin
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 5%

---

# SpamAssassin{#spamassassin}

Adobe Campaign può essere configurato per funzionare con [SpamAssassin](https://spamassassin.apache.org), servizio di terze parti utilizzato per il filtro dello spam nelle e-mail. Ciò ti consente di valutare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

SpamAssassin sfrutta una varietà di tecniche di rilevamento spam, tra cui:

* Rilevamento di spam basato su DNS e su checksum fuzzy
* Filtro bayesiano
* Programmi esterni
* Inserisce nell&#39;elenco Bloccati
* Database online

>[!NOTE]
>
>SpamAssassin deve essere installato e configurato nel server applicazioni Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-spamassassin.md).
>
>Le regole che determinano se un elemento è spam o meno vengono gestite tramite SpamAssassin e possono essere modificate da un amministratore con privilegi.

## Utilizzare SpamAssassin in Campaign {#using-spamassassin}

Dopo aver creato la consegna e-mail e averne definito il contenuto, segui i passaggi indicati di seguito per valutare i rischi.

Per ulteriori informazioni sulla creazione e la progettazione di una consegna, consulta [questa sezione](about-email-channel.md).

1. Vai a **[!UICONTROL Preview]** scheda.
1. Seleziona un destinatario per visualizzare l’anteprima della consegna.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Se non selezioni un destinatario, non è possibile eseguire il controllo anti-spam.

1. Un messaggio di avvertenza fornisce il risultato del test. Se viene rilevato un livello di rischio elevato, viene visualizzato il seguente messaggio di avvertenza:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Fai clic su **[!UICONTROL More...]** accanto all’avviso.
1. Seleziona la scheda **[!UICONTROL Anti-spam checking]**.
1. Vai a **[!UICONTROL Points / Rule / Description]** per visualizzare i motivi di questo rischio.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Ogni volta che fai clic su **[!UICONTROL Anti-spam checking]**, viene chiamato il servizio SpamAssassin e il messaggio viene nuovamente analizzato per rilevare la presenza di posta indesiderata. Assicurati di aver modificato il contenuto prima di eseguire di nuovo l’analisi anti-spam.
