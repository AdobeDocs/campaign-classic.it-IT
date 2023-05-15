---
product: campaign
title: Informazioni su Adobe Experience Cloud Triggers
description: Guida introduttiva all’implementazione di Adobe Experience Cloud Triggers
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# Utilizzo di Campaign e Triggers di Experienci Cloud{#about-adobe-experience-triggers}



[!DNL Triggers] è un’integrazione tra Adobe Campaign e Adobe Analytics che utilizza la pipeline. La pipeline recupera le azioni o gli attivatori degli utenti dal sito web. Un abbandono del carrello è un esempio di trigger. Gli attivatori vengono elaborati in Adobe Campaign per inviare e-mail in tempo quasi reale.

>[!CAUTION]
>
>Questa funzionalità non è disponibile come funzione predefinita del prodotto. Per questa implementazione, devi prima aprire un ticket con il supporto Adobe. Potrai quindi seguire i passaggi descritti in questo [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] esegui le azioni di marketing entro un breve intervallo di tempo dopo l’azione di un utente. Il tempo di risposta tipico è inferiore a un&#39;ora.

Consente integrazioni più agili poiché la configurazione è minima e non è coinvolta una terza parte.
Supporta inoltre elevati volumi di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l&#39;integrazione può elaborare un milione di trigger all&#39;ora.

## [!DNL Triggers] architettura {#triggers-architecture}

La [!DNL pipelined] Il processo è sempre in esecuzione sul server di marketing Adobe Campaign. Si connette alla pipeline, recupera gli eventi ed elabora immediatamente.

![](assets/triggers_2.png)

La [!DNL pipelined] elabora l&#39;accesso all&#39;Experience Cloud utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l’autenticazione durante il recupero degli eventi.

Per ulteriori informazioni sull’autenticazione, consulta questo [page](../../integrations/using/configuring-adobe-io.md).
