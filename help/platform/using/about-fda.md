---
title: Accesso a un database esterno
seo-title: Accesso a un database esterno
description: Accesso a un database esterno
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9d22af2a2e25cb0dd83759096139996372f60c33

---


# Informazioni su Federated Data Access {#about-federated-data-access}

Adobe Campaign fornisce l&#39;opzione **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

>[!CAUTION]
>
>L&#39;accesso a un database esterno tramite FDA è possibile solo per installazioni locali o ibride, ad eccezione dei connettori Snowflake. Per ulteriori informazioni, consultare questa [pagina](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Principio di funzionamento {#operating-principle}

L&#39;opzione FDA consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati provenienti dalle origini SQL.

Per utilizzare questa funzionalità, è necessario:

1. Disporre di un database esterno compatibile con il modulo FDA di Adobe Campaign. L&#39;elenco dei sistemi di database e delle versioni compatibili è dettagliato nella matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità. Gli utenti devono anche disporre delle autorizzazioni [](../../platform/using/remote-database-access-rights.md) necessarie in Adobe Campaign e nel database esterno.
1. [Installate i driver](../../platform/using/specific-configuration-database.md) corrispondenti al database sul server Adobe Campaign.
1. [Crea e configura un account](../../platform/using/connecting-to-database.md) esterno che consente di stabilire la connessione tra Adobe Campaign e il database esterno. Per ulteriori informazioni sugli account esterni disponibili, fare riferimento a questa [pagina](../../platform/using/external-accounts.md).
1. [Crea lo schema](../../platform/using/creating-data-schema.md) del database esterno in Adobe Campaign. Questo consente di riconoscere la struttura dati del database esterno.
1. Alla fine, [create una nuova mappatura](../../platform/using/defining-data-mapping.md) di destinazione dallo schema creato in precedenza, nel caso in cui i destinatari delle consegne provengano dal database esterno. Ciò presenta alcune limitazioni, in particolare per quanto riguarda la personalizzazione delle consegne.

Una volta creato lo schema dati, i dati possono essere elaborati nei flussi di lavoro Adobe Campaign. For more on this, refer to [this section](../../workflow/using/accessing-an-external-database--fda-.md).

## Best practice e raccomandazioni {#best-practices-and-recommendations}

L&#39;opzione FDA è stata creata per manipolare i dati nei database esterni in modalità batch nei flussi di lavoro. L&#39;utilizzo della FDA in un altro contesto, ad esempio per le operazioni unitarie, deve essere effettuato con cautela (Personalizzazione, Interazione, consegne in tempo reale, ecc.).

Evitate le operazioni che richiedono l&#39;utilizzo del più possibile di Adobe Campaign e del database esterno. A questo scopo, potete:

* Esporta il database di Adobe Campaign nel database esterno ed esegui le operazioni solo dal database esterno prima di reimportare i risultati in Adobe Campaign.
* Raccogli i dati dal database Adobe Campaign esterno ed esegui le operazioni localmente.

Se desiderate eseguire la personalizzazione nelle consegne utilizzando i dati del database esterno, raccogliete i dati da utilizzare in un flusso di lavoro per renderlo disponibile in una tabella temporanea. Quindi utilizzate i dati della tabella temporanea per personalizzare la consegna.

## Limitazioni {#limitations}

L&#39;opzione FDA è soggetta alla limitazione soft del sistema di database esterno utilizzato.

Per motivi di prestazioni, non consigliamo di utilizzare questa funzionalità per eseguire operazioni unitarie (personalizzazione della consegna, modulo Interazione, tempo reale).
