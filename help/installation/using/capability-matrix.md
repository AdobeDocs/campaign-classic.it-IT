---
solution: Campaign Classic
product: campaign
title: Matrice di funzionalità on-premise, ibrida e in hosting di Campaign
description: Scopri le principali differenze tra distribuzioni in hosting e on-premise
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 16%

---


# Matrice di funzionalità per modello{#capability-matrix-per-model}

 Adobe Campaign Classic include una serie di moduli e opzioni. La disponibilità di questi moduli e il loro utilizzo possono dipendere dal tipo di distribuzione dell’installazione. Questo articolo condivide alcuni dettagli sulle differenze principali per alcune funzioni tra distribuzioni in hosting completo (Managed Services) e on-premise.

Questa pagina mostra le differenze principali tra le distribuzioni in hosting (Managed Services) e on-premise. Le specificità delle implementazioni ibride dipendono dagli elementi ospitati da Adobe e ospitati nei tuoi locali.

I diversi modelli di hosting sono introdotti [in questa sezione](../../installation/using/hosting-models.md).

## Disponibilità per modello di distribuzione {#capability-matrix}

| Funzionalità | Ospitato | Ibrido | On-Premise | Dettagli |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurare il server Campaign | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../installation/using/the-server-configuration-file.md) |
| Ccn e-mail | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../installation/using/email-archiving.md) |
| Gestisci istanza di esecuzione del Centro messaggi | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../message-center/using/about-transactional-messaging.md) |
| Gestione della piattaforma di mid-sourcing | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../installation/using/mid-sourcing-server.md) |
| Rendering della casella in entrata tramite Litmus | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../delivery/using/inbox-rendering.md) |
| Integrazione con IMS (Adobe ID) | On-demand | On-demand | On-demand | [Ulteriori informazioni](../../integrations/using/about-adobe-id.md) |
| Crittografia/decrittografia dei dati per i trasferimenti di file | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../platform/using/unzip-decrypt.md) |
| Zipping/decompressione di file | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../platform/using/unzip-decrypt.md) |
| Delega nome di dominio | On-demand | On-demand | Non disponibile | [Ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html) |
| Installazione di SpamAssassin | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../delivery/using/spamassassin.md) |
| Accesso ai rapporti sul recapito messaggi | Disponibile | On-demand | Disponibile | [Ulteriori informazioni](../../delivery/using/monitoring-deliverability.md) |
| Configurazione dell&#39;autenticazione LDAP | Non disponibile | Disponibile | Disponibile | [Ulteriori informazioni](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign fornisce l&#39;opzione **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign. [Ulteriori informazioni](../../installation/using/about-fda.md)

>[!CAUTION]
>
>L&#39;accesso a un database esterno tramite FDA è possibile solo per installazioni on-premise o ibride, ad eccezione del [connettore di Snowflake](../../installation/using/configure-fda-snowflake.md).


**Vedi anche**

* [Matrice di compatibilità](../../rn/using/compatibility-matrix.md)
* [Note sulla versione](../../rn/using/latest-release.md)
* [Aggiornamenti Campaign Classic](../../rn/using/rn-overview.md)
* [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] release](../../rn/using/gold-standard.md)
* [[!DNL Gold Standard] programma](../../rn/using/gs-overview.md)
