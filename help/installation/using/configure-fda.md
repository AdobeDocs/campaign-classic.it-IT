---
product: campaign
title: Configurare i connettori FDA
description: Scopri i passaggi di configurazione per FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 2%

---

# Configurazione dei connettori FDA {#specific-configurations-by-database-type}



A seconda dei database esterni a cui desideri poter accedere da Adobe Campaign, dovrai eseguire alcune configurazioni specifiche. Queste configurazioni richiedono essenzialmente l’installazione di driver e la dichiarazione delle variabili di ambiente che appartengono a ciascun RDBMS sul server Adobe Campaign.

Come regola generale, devi installare il livello client corrispondente sul database esterno sul server Adobe Campaign.

>[!NOTE]
>
>Le versioni compatibili sono elencate in [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
>

## Passaggi di configurazione {#fda-configuration-steps}

Per impostare l’accesso a un database esterno con FDA, effettua le seguenti operazioni di configurazione:

1. Installare i driver e configurare l&#39;account esterno corrispondente al database sul server Adobe Campaign. Fai riferimento alle pagine specifiche del database [elencate di seguito](#fda-specific-configuration)
1. Verifica l’account esterno o crea una connessione temporanea tra Adobe Campaign e il database esterno. [Ulteriori informazioni](../../installation/using/connecting-to-database.md)
1. Crea lo schema del database esterno in Adobe Campaign. Questo consente di identificare la struttura dati del database esterno. [Ulteriori informazioni](../../installation/using/creating-data-schema.md)
1. Se necessario, crea una nuova mappatura di destinazione dallo schema creato in precedenza. Questa opzione è necessaria se i destinatari delle consegne provengono dal database esterno. Questa implementazione comporta limitazioni relative alla personalizzazione dei messaggi. [Ulteriori informazioni](../../installation/using/defining-data-mapping.md)

Una volta creato lo schema di dati, i dati possono essere elaborati nei flussi di lavoro di Adobe Campaign. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=it){target="_blank"}.

## Configurazione specifica del database {#fda-specific-configuration}

A seconda dei database esterni a cui desideri poter accedere da Adobe Campaign, dovrai eseguire alcune configurazioni specifiche. Queste configurazioni richiedono essenzialmente l’installazione dei driver e la dichiarazione delle variabili di ambiente che appartengono a ciascun RDBMS sul server Adobe Campaign, nonché la configurazione dell’account esterno.

Per ulteriori informazioni, segui i collegamenti riportati di seguito:

* Connetti Campaign e [Amazon Redshift](../../installation/using/configure-fda-redshift.md)
* Connetti Campaign e [Azure Synapse](../../installation/using/configure-fda-synapse.md)
* Connetti Campaign e [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Connetti Campaign e [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Connetti Campaign e [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* Connetti Campaign e [Netezza](../../installation/using/configure-fda-netezza.md)
* Connetti Campaign e [Oracle](../../installation/using/configure-fda-oracle.md)
* Connetti Campaign e [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* Connetti Campaign e [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Connetti Campaign e [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Connetti Campaign e [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Connetti Campaign e [Teradata](../../installation/using/configure-fda-teradata.md)
* Connetti Campaign e [Vertica Analytics](../../installation/using/configure-fda-vertica.md)
