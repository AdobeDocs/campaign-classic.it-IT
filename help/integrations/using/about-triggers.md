---
solution: Campaign Classic
product: campaign
title: Informazioni su Adobe Experience Cloud Triggers
description: Introduzione all'implementazione di Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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

## [!DNL Triggers] architettura  {#triggers-architecture}

Il processo [!DNL pipelined] è sempre in esecuzione sul server di marketing Adobe Campaign . Si collega alla pipeline, recupera gli eventi e li elabora immediatamente.

![](assets/triggers_2.png)

Il processo [!DNL pipelined] effettua l&#39;accesso al Experience Cloud  utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l&#39;autenticazione al momento del recupero degli eventi.

Per ulteriori informazioni sull&#39;autenticazione, fare riferimento a questa [pagina](../../integrations/using/configuring-adobe-io.md).
