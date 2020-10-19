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
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 10%

---


# Matrice di capacità per modello host {#capability-matrix-per-model}

 Adobe Campaign Classic include una serie di moduli e opzioni. La disponibilità di questi moduli e il loro utilizzo possono dipendere dal tipo di implementazione dell&#39;installazione. In questo articolo vengono condivisi alcuni dettagli sulle differenze principali per alcune funzionalità tra distribuzioni in hosting completo (Managed Services) e in sede.

Questa pagina mostra le principali differenze tra le distribuzioni in hosting (Managed Services) e quelle in sede. Le specifiche di distribuzione ibrida dipendono dagli elementi ospitati dal Adobe  e ospitati nella propria sede.

I diversi modelli di hosting sono introdotti [in questa sezione](../../installation/using/hosting-models.md).

## Matrice di capacità{#capability-matrix}

| Funzionalità | Ospitato | Ibrido | In sede | Dettagli |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurare il server Campaign | Su richiesta | Disponibile | Disponibile | Il file[di configurazione del](../../installation/using/the-server-configuration-file.md)server può essere modificato solo da  Adobe per i clienti ospitati. |
| Ccn e-mail | Su richiesta | Su richiesta | Disponibile | Per architetture ospitate e ibride, contattate il vostro responsabile commerciale per attivare e-mail CCN. Per le installazioni locali, seguite le linee guida della documentazione. [Ulteriori informazioni](../../installation/using/email-archiving.md) |
| Gestisci istanza di esecuzione Centro messaggi | Su richiesta | Su richiesta | Disponibile | Per le distribuzioni in hosting, determinate impostazioni, come la creazione di utenti nell&#39;istanza di esecuzione, possono essere eseguite solo da  Adobe. [Ulteriori informazioni](../../message-center/using/about-transactional-messaging.md) |
| Gestione della piattaforma Mid-sourcing | Su richiesta | Su richiesta | Disponibile | Le piattaforme di midsourcing ospitate da  Adobe possono essere configurate solo da  Adobe. |
| Rendering in entrata tramite Litmus | Su richiesta | Su richiesta | Disponibile | Hai bisogno di un account Litmus. È necessario contattare  Adobe per ottenere i dettagli necessari o eseguire la configurazione di rendering Inbox. [Ulteriori informazioni](../../delivery/using/inbox-rendering.md) |
| Integrazione con IMS ( Adobe ID) | Su richiesta | Su richiesta | Su richiesta | Il provisioning IMS viene eseguito da  Adobe. Questa integrazione è un prerequisito per le integrazioni Adobe Experience Cloud. [Ulteriori informazioni](../../integrations/using/about-adobe-id.md) |
| Cifratura/decrittografia dei dati per i trasferimenti di file | Su richiesta | Disponibile | Disponibile | Per abilitare la pre o la post-elaborazione dei file è necessario installare l&#39;utility necessaria sul server Adobe Campaign . I clienti ospitati possono utilizzare il Pannello di controllo Campaign Campaign. [Ulteriori informazioni](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Zipping/decompressione di file | Disponibile su richiesta | Disponibile | Per abilitare la pre o la post-elaborazione dei file è necessario installare l&#39;utility necessaria sul server Adobe Campaign . I clienti ospitati possono utilizzare il Pannello di controllo Campaign Campaign. [Ulteriori informazioni](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Delega nome di dominio | Su richiesta | Su richiesta | Non disponibile | [Ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html) |
| Installazione di SpamAssassin | Su richiesta | Disponibile | Disponibile | L&#39;installazione di SpamAssassin richiede la modifica del file di configurazione del server. [Ulteriori informazioni](../../delivery/using/spamassassin.md) |
| Accesso ai rapporti sulla recapito | Disponibile | Su richiesta | Disponibile | In alcune distribuzioni ibride, non è possibile accedere ai rapporti sulla recapito dall&#39;istanza di marketing. |
| Configurazione dell’autenticazione LDAP | Non disponibile | Disponibile | Disponibile | La configurazione LDAP è possibile solo per le installazioni locali o ibride. [Ulteriori informazioni](../../installation/using/connecting-through-ldap.md) |


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
* [Programma](https://helpx.adobe.com/it/campaign/kb/gold-standard.html)Gold Standard.
