---
title: Matrice di funzionalità locali, ibride e ospitate della campagna
description: Scopri le principali differenze tra le distribuzioni in hosting e quelle in sede
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c03e90b2e2f57606749c86cda343ce5756fec122
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 18%

---


# Matrice di capacità {#capability-matrix-per-model}

 Adobe Campaign Classic include una serie di moduli e opzioni. La disponibilità di questi moduli e il loro utilizzo possono dipendere dal tipo di implementazione dell&#39;installazione. In questo articolo vengono condivisi alcuni dettagli sulle differenze principali per alcune funzionalità tra distribuzioni in hosting completo (Managed Services) e in sede.

Questa pagina mostra le principali differenze tra le distribuzioni in hosting (Managed Services) e quelle in sede. Le specifiche di distribuzione ibrida dipendono dagli elementi ospitati dal Adobe  e ospitati nella propria sede.

I diversi modelli di hosting sono introdotti [in questa sezione](../../installation/using/hosting-models.md).

## Disponibilità per modello di distribuzione {#capability-matrix}

| Funzionalità | Ospitato | Ibrido | In sede | Dettagli |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurare il server Campaign | Su richiesta | Disponibile | Disponibile | [Ulteriori informazioni](../../installation/using/the-server-configuration-file.md) |
| Ccn e-mail | Su richiesta | Su richiesta | Disponibile | [Ulteriori informazioni](../../installation/using/email-archiving.md) |
| Gestisci istanza di esecuzione Centro messaggi | Su richiesta | Su richiesta | Disponibile | [Ulteriori informazioni](../../message-center/using/about-transactional-messaging.md) |
| Gestione della piattaforma Mid-sourcing | Su richiesta | Su richiesta | Disponibile | [Ulteriori informazioni](../../installation/using/mid-sourcing-server.md) |
| Rendering in entrata tramite Litmus | Su richiesta | Su richiesta | Disponibile | [Ulteriori informazioni](../../delivery/using/inbox-rendering.md) |
| Integrazione con IMS ( Adobe ID) | Su richiesta | Su richiesta | Su richiesta | [Ulteriori informazioni](../../integrations/using/about-adobe-id.md) |
| Cifratura/decrittografia dei dati per i trasferimenti di file | Su richiesta | Disponibile | Disponibile | [Ulteriori informazioni](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Zipping/decompressione di file | Su richiesta | Disponibile | Disponibile | [Ulteriori informazioni](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Delega nome di dominio | Su richiesta | Su richiesta | Non disponibile | [Ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html) |
| Installazione di SpamAssassin | Su richiesta | Disponibile | Disponibile | [Ulteriori informazioni](../../delivery/using/spamassassin.md) |
| Accesso ai rapporti sulla recapito | Disponibile | Su richiesta | Disponibile | [Ulteriori informazioni](../../delivery/using/monitoring-deliverability.md) |
| Configurazione dell’autenticazione LDAP | Non disponibile | Disponibile | Disponibile | [Ulteriori informazioni](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [Ulteriori informazioni](../../platform/using/about-fda.md)

>[!CAUTION]
>
>L&#39;accesso a un database esterno tramite FDA è possibile solo per installazioni locali o ibride, ad eccezione del connettore [di Snowflake](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**Vedi anche**

* [Matrice di compatibilità](../../rn/using/compatibility-matrix.md)
* [Note sulla versione](../../rn/using/latest-release.md)
* [Aggiornamenti Campaign Classic](../../rn/using/rn-overview.md)
* [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md)
* [Versioni Gold Standard](../../rn/using/gold-standard.md)
* [Programma Gold Standard](https://helpx.adobe.com/it/campaign/kb/gold-standard.html)
