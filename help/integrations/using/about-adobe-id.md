---
product: campaign
title: Utilizza il tuo Adobe ID per connetterti ad Adobe Campaign
description: Ulteriori informazioni sull’implementazione di Adobe IMS in Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 15%

---

# Informazioni su Adobe ID {#about-adobe-id}

Adobe Identity Management System (IMS) consente agli amministratori di creare e gestire l’accesso degli utenti ad applicazioni e servizi. Per ulteriori informazioni sui diversi tipi di ID Adobe, consulta [questa pagina](https://helpx.adobe.com/it/enterprise/using/users.html).

Gli utenti di Campaign possono connettersi alla console di Adobe Campaign utilizzando il proprio Adobe ID, invece dell&#39;[autenticazione nativa utente/password](../../platform/using/access-management-operators.md). Questa implementazione offre i seguenti vantaggi:

* Lo stesso ID può essere utilizzato per tutte le soluzioni Experience Cloud.
* La connessione viene mantenuta quando si utilizza Adobe Campaign con diverse integrazioni.
* Criteri di gestione password più sicuri rispetto a login/password nativi.
* Utilizzo di account Federated ID (provider di ID esterno).

>[!IMPORTANT]
>
> In Campaign v8, la connessione con l’utente o la password (ovvero l’autenticazione nativa) non è consentita. **L&#39;Adobe consiglia di eseguire questa migrazione a partire da Campaign v7.3.5 per eseguire senza problemi la migrazione a Campaign v8.**
>
>Scopri come effettuare la migrazione ad Adobe IMS in [questa sezione](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## Altre risorse

| Pagine utili | Risorse aggiuntive |
|---|---|
| [Configurazione di IMS](../../integrations/using/configuring-ims.md) | [Domande frequenti su Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) |
| [Implementazione di IMS](../../integrations/using/implementing-ims.md) | [Gestione degli accessi](../../platform/using/access-management.md) |
| [Risoluzione dei problemi IMS](../../integrations/using/ims-troubleshooting.md) | [Installazione dei pacchetti Campaign](../../installation/using/installing-campaign-standard-packages.md) |
