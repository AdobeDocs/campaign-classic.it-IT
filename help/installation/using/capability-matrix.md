---
product: campaign
title: Matrice di funzionalità on-premise, ibride e in hosting per Campaign
description: Scopri le principali differenze tra le distribuzioni in hosting e quelle on-premise
feature: Installation, Architecture
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 26%

---

# Matrice di capacità per modello{#capability-matrix-per-model}



 Adobe Campaign Classic include una serie di moduli e opzioni. La disponibilità di questi moduli e il loro utilizzo possono dipendere dal tipo di distribuzione dell’installazione. Questo articolo condivide alcuni dettagli sulle principali differenze per alcune funzioni tra le distribuzioni completamente in hosting (Managed Services) e quelle on-premise.

Questa pagina mostra le principali differenze tra le distribuzioni in hosting (Managed Services) e quelle on-premise. Le specificità delle distribuzioni ibride dipendono dagli elementi ospitati da Adobe e ospitati nelle tue sedi.

I diversi modelli di hosting sono introdotti [in questa sezione](../../installation/using/hosting-models.md).

## Disponibilità per modello di distribuzione {#capability-matrix}

| Funzionalità | In hosting | Ibrido | On-premise | Dettagli |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurare il server Campaign | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../installation/using/the-server-configuration-file.md) |
| Invia e-mail in Ccn | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../installation/using/email-archiving.md) |
| Gestisci istanza di esecuzione del Centro messaggi | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../message-center/using/about-transactional-messaging.md) |
| Gestione della piattaforma di mid-sourcing | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../installation/using/mid-sourcing-server.md) |
| Rendering della casella in entrata tramite Litmus | On-demand | On-demand | Disponibile | [Ulteriori informazioni](../../delivery/using/inbox-rendering.md) |
| Integrazione con IMS (Adobe ID) | On-demand | On-demand | On-demand | [Ulteriori informazioni](../../integrations/using/about-adobe-id.md) |
| Crittografia/decrittografia dei dati per i trasferimenti di file | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../platform/using/unzip-decrypt.md) |
| Compressione/decompressione di file | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../platform/using/unzip-decrypt.md) |
| Delega nome dominio | On-demand | On-demand | Non disponibile | [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=it) |
| Installazione di SpamAssassin | On-demand | Disponibile | Disponibile | [Ulteriori informazioni](../../delivery/using/spamassassin.md) |
| Accesso ai rapporti sul recapito messaggi | Disponibile | On-demand | Disponibile | [Ulteriori informazioni](../../delivery/using/monitoring-deliverability.md) |
| Configurazione dell’autenticazione LDAP | Non disponibile | Disponibile | Disponibile | [Ulteriori informazioni](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign fornisce l&#39;opzione **Federated Data Access** (FDA) per elaborare le informazioni archiviate in uno o più database esterni: è possibile accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign. [Ulteriori informazioni](../../installation/using/about-fda.md)

>[!CAUTION]
>
>I sistemi di database esterni compatibili dipendono dal modello di hosting. Ulteriori informazioni nella [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md).
>

**Vedi anche**

* [Matrice di compatibilità](../../rn/using/compatibility-matrix.md)
* [Note sulla versione](../../rn/using/latest-release.md)
* [Aggiornamenti Campaign Classic](../../rn/using/rn-overview.md)
* [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md)
* [Versioni [!DNL Gold Standard]](../../rn/using/gold-standard.md)
