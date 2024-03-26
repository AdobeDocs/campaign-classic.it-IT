---
product: campaign
title: Informazioni su Adobe Experience Cloud Triggers
description: Introduzione all’implementazione di Adobe Experience Cloud Triggers
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 7%

---

# Utilizzo di Campaign e Triggers Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] è un’integrazione tra Adobe Campaign e Adobe Analytics che utilizza la pipeline. La pipeline recupera le azioni o i trigger degli utenti dal sito web. L’abbandono del carrello è un esempio di trigger. Gli attivatori vengono elaborati in Adobe Campaign per inviare e-mail quasi in tempo reale.

>[!CAUTION]
>
>Questa funzionalità non è disponibile come funzione predefinita del prodotto. Per questa implementazione, devi innanzitutto aprire un ticket con il supporto Adobe. Potrai quindi seguire i passaggi descritti in questo [pagina](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] eseguire azioni di marketing entro un breve intervallo di tempo dopo l’azione di un utente. Il tempo di risposta tipico è inferiore a un&#39;ora.

Consente integrazioni più agili, in quanto la configurazione è minima e non è coinvolta una terza parte.
Supporta inoltre elevati volumi di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l’integrazione può elaborare un milione di trigger all’ora.

![](assets/do-not-localize/book.png) Scopri come [creazione di un trigger di Experience Cloud](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) e identificare, definire e monitorare i comportamenti critici dei consumatori.

## [!DNL Triggers] architettura {#triggers-architecture}

Il [!DNL pipelined] Il processo è sempre in esecuzione sul server di marketing Adobe Campaign. Si connette alla pipeline, recupera gli eventi ed li elabora immediatamente.

![](assets/triggers_2.png)

Il [!DNL pipelined] process accede all’Experience Cloud utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l’autenticazione durante il recupero degli eventi.

Per ulteriori informazioni sull’autenticazione, consulta [pagina](../../integrations/using/configuring-adobe-io.md).
