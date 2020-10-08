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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 16%

---


# Informazioni su Federated Data Access {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>L&#39;accesso a un database esterno tramite FDA è possibile solo per installazioni locali o ibride, ad eccezione dei connettori di Snowflake . Per ulteriori informazioni, consulta questa [pagina](https://helpx.adobe.com/it/campaign/kb/acc-on-prem-vs-hosted.html).

## Principio di funzionamento {#operating-principle}

L&#39;opzione FDA consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati provenienti dalle origini SQL.

Per utilizzare questa funzionalità, è necessario:

1. Disporre di un database esterno compatibile con il modulo Adobe Campaign FDA . L&#39;elenco dei sistemi di database e delle versioni compatibili è dettagliato nella matrice [di](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)compatibilità. Gli utenti devono anche disporre delle autorizzazioni [](../../platform/using/remote-database-access-rights.md) necessarie in  Adobe Campaign e nel database esterno.
1. [Installate i driver](../../platform/using/specific-configuration-database.md) corrispondenti al database sul server Adobe Campaign .
1. [Creare e configurare un account](../../platform/using/connecting-to-database.md) esterno che consenta di stabilire la connessione tra  Adobe Campaign e il database esterno. Per ulteriori informazioni sugli account esterni disponibili, fare riferimento a questa [pagina](../../platform/using/external-accounts.md).
1. [Create lo schema](../../platform/using/creating-data-schema.md) del database esterno in  Adobe Campaign. Questo consente di riconoscere la struttura dati del database esterno.
1. Alla fine, [create una nuova mappatura](../../platform/using/defining-data-mapping.md) di destinazione dallo schema creato in precedenza, nel caso in cui i destinatari delle consegne provengano dal database esterno. Ciò presenta alcune limitazioni, in particolare per quanto riguarda la personalizzazione delle consegne.

Una volta creato lo schema di dati, i dati possono essere elaborati  flussi di lavoro Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/accessing-an-external-database--fda-.md).

## Database esterni disponibili {#external-database}

Di seguito è riportato l&#39;elenco di tutti i database esterni compatibili con il modulo Adobe Campaign FDA :

* Analisi della sinapsi di Microsoft Azure. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md#azure-external).
*  Snowflake. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).
* Hadoop. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3).
* Oracle. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* Netezza. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* IQ Sybase. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq).
* Teradata. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md#configure-access-to-teradata).
* SAP HANA. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/specific-configuration-database.md).

## Best practice e raccomandazioni {#best-practices-and-recommendations}

L&#39;opzione FDA è stata creata per manipolare i dati nei database esterni in modalità batch nei flussi di lavoro. L&#39;utilizzo della FDA in un altro contesto, ad esempio per le operazioni unitarie, deve essere effettuato con cautela (Personalizzazione, Interazione, consegne in tempo reale, ecc.).

Evitate le operazioni che richiedono l&#39;utilizzo del Adobe Campaign  e del database esterno il più possibile. A questo scopo, potete:

* Esportate il database Adobe Campaign  nel database esterno ed eseguite le operazioni solo dal database esterno prima di reimportare i risultati in  Adobe Campaign.
* Raccogliere i dati dal database Adobe Campaign  esterno ed eseguire le operazioni localmente.

Se desiderate eseguire la personalizzazione nelle consegne utilizzando i dati del database esterno, raccogliete i dati da utilizzare in un flusso di lavoro per renderlo disponibile in una tabella temporanea. Quindi utilizzate i dati della tabella temporanea per personalizzare la consegna.

## Limitazioni {#limitations}

L&#39;opzione FDA è soggetta alla limitazione soft del sistema di database esterno utilizzato.

Per motivi di prestazioni, non consigliamo di utilizzare questa funzionalità per eseguire operazioni unitarie (personalizzazione della consegna, modulo Interazione, tempo reale).
