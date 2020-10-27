---
title: Informazioni su Adobe Experience Manager
seo-title: Informazioni su Adobe Experience Manager
description: Informazioni su Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---


# Informazioni su Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] è un&#39;integrazione tra  Adobe Campaign e  Adobe Analytics mediante la pipeline. La pipeline recupera le azioni o gli attivatori degli utenti dal sito Web. Un abbandono del carrello è un esempio di trigger. Gli attivatori vengono elaborati in  Adobe Campaign per inviare e-mail in tempo quasi reale.

[!DNL Triggers] eseguire azioni di marketing entro un breve intervallo di tempo a seguito dell&#39;azione di un utente. Il tempo di risposta tipico è inferiore a un&#39;ora.

Consente integrazioni più agili, poiché la configurazione è minima e non coinvolge una terza parte.
Supporta inoltre volumi elevati di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l&#39;integrazione può elaborare un milione di attivatori all&#39;ora.

## [!DNL Triggers] architettura {#triggers-architecture}

Il [!DNL pipelined] processo è sempre in esecuzione sul server di marketing Adobe Campaign . Si collega alla pipeline, recupera gli eventi e li elabora immediatamente.

![](assets/triggers_2.png)

Il [!DNL pipelined] processo accede al Experience Cloud  utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l&#39;autenticazione al momento del recupero degli eventi.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).

>[!NOTE]
>
>L&#39;ulteriore elaborazione degli eventi viene effettuata nell&#39;ambito del pacchetto ACX fornito al di fuori dell&#39;implementazione predefinita. L&#39;evento ricevuto viene elaborato immediatamente utilizzando il codice JavaScript. Viene salvata in una tabella di database senza ulteriore elaborazione in tempo reale. Le attivazioni vengono utilizzate per il targeting tramite un flusso di lavoro della campagna che invia e-mail. La campagna è configurata in modo che il cliente che ha attivato l&#39;evento riceva un&#39;e-mail.
