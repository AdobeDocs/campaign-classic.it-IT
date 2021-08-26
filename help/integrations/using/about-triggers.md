---
product: campaign
title: Informazioni sugli attivatori Adobe Experience Cloud
description: Guida introduttiva all’implementazione di Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 16%

---

# Introduzione ad Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

![](../../assets/common.svg)

[!DNL Triggers] è un’integrazione tra Adobe Campaign e Adobe Analytics che utilizza la pipeline. La pipeline recupera le azioni o gli attivatori degli utenti dal sito web. Un abbandono del carrello è un esempio di trigger. Gli attivatori vengono elaborati in Adobe Campaign per inviare e-mail in tempo quasi reale.

>[!CAUTION]
>
>Questa funzionalità non è disponibile come funzione predefinita del prodotto. La sua implementazione richiede l’intervento della Consulenza Adobe. Per maggiori informazioni, contatta un rappresentante Adobe di fiducia

[!DNL Triggers] esegui le azioni di marketing entro un breve intervallo di tempo dopo l’azione di un utente. Il tempo di risposta tipico è inferiore a un&#39;ora.

Consente integrazioni più agili poiché la configurazione è minima e non è coinvolta una terza parte.
Supporta inoltre elevati volumi di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l&#39;integrazione può elaborare un milione di trigger all&#39;ora.

## [!DNL Triggers] architettura {#triggers-architecture}

Il processo [!DNL pipelined] è sempre in esecuzione sul server di marketing Adobe Campaign. Si connette alla pipeline, recupera gli eventi ed elabora immediatamente.

![](assets/triggers_2.png)

Il processo [!DNL pipelined] accede all&#39;Experience Cloud utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l’autenticazione durante il recupero degli eventi.

Per ulteriori informazioni sull&#39;autenticazione, consulta questa [pagina](../../integrations/using/configuring-adobe-io.md).
