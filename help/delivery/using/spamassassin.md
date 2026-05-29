---
product: campaign
title: SpamAssassin
description: Scopri come impostare il rilevamento di posta indesiderata con SpamAssassin
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
TQID: https://experienceleague.adobe.com/nZB19N90xSjDCNnibtwcPBm75SSyxkq1hQxICXCOg2A
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 273
ht-degree: 6%

---

# SpamAssassin{#spamassassin}

Adobe Campaign può essere configurato per funzionare con [SpamAssassin](https://spamassassin.apache.org), un servizio di terze parti utilizzato per il filtro della posta indesiderata. Ciò ti consente di valutare le e-mail per determinare se un messaggio corre il rischio di essere considerato come spam dagli strumenti anti-spam utilizzati al momento della ricezione.

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

1. Vai alla scheda **[!UICONTROL Preview]**.
1. Seleziona un destinatario per visualizzare l’anteprima della consegna.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Se non selezioni un destinatario, non è possibile eseguire il controllo anti-spam.

1. Un messaggio di avvertenza fornisce il risultato del test. Se viene rilevato un livello di rischio elevato, viene visualizzato il seguente messaggio di avvertenza:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Fare clic sul collegamento **[!UICONTROL More...]** accanto all&#39;avviso.
1. Seleziona la scheda **[!UICONTROL Anti-spam checking]**.
1. Andare alla sezione **[!UICONTROL Points / Rule / Description]** per visualizzare i motivi di questo rischio.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Ogni volta che si fa clic su **[!UICONTROL Anti-spam checking]**, viene chiamato il servizio SpamAssassin e il messaggio viene nuovamente analizzato per rilevare la posta indesiderata. Assicurati di aver modificato il contenuto prima di eseguire di nuovo l’analisi anti-spam.
