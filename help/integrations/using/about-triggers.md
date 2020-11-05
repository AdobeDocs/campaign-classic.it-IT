---
title: Informazioni su Adobe Experience Cloud Triggers
description: Introduzione all'implementazione di Adobe Experience Cloud Triggers
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 16%

---


# Guida introduttiva ad Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] è un&#39;integrazione tra  Adobe Campaign e  Adobe Analytics mediante la pipeline. La pipeline recupera le azioni o gli attivatori degli utenti dal sito Web. Un abbandono del carrello è un esempio di trigger. Gli attivatori vengono elaborati in  Adobe Campaign per inviare e-mail in tempo quasi reale.

>[!CAUTION]
>
>Questa funzionalità non è disponibile come funzione predefinita del prodotto. La sua implementazione richiede l’intervento della Consulenza Adobe. Per maggiori informazioni, contatta un rappresentante Adobe di fiducia

[!DNL Triggers] eseguire azioni di marketing entro un breve intervallo di tempo a seguito dell&#39;azione di un utente. Il tempo di risposta tipico è inferiore a un&#39;ora.

Consente integrazioni più agili, poiché la configurazione è minima e non coinvolge una terza parte.
Supporta inoltre volumi elevati di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l&#39;integrazione può elaborare un milione di attivatori all&#39;ora.

## [!DNL Triggers] architettura {#triggers-architecture}

Il [!DNL pipelined] processo è sempre in esecuzione sul server di marketing Adobe Campaign . Si collega alla pipeline, recupera gli eventi e li elabora immediatamente.

![](assets/triggers_2.png)

Il [!DNL pipelined] processo accede al Experience Cloud  utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l&#39;autenticazione al momento del recupero degli eventi.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).
