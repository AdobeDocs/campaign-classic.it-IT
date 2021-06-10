---
product: campaign
title: Configurare i connettori FDA
description: Scopri i passaggi di configurazione per FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 11de485a97d112b308c145775537d9b6255f124f
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 5%

---

# Configurazione dei connettori FDA {#specific-configurations-by-database-type}

A seconda dei database esterni a cui desideri accedere da Adobe Campaign, dovrai eseguire alcune configurazioni specifiche. Queste configurazioni richiedono essenzialmente l’installazione di driver e la dichiarazione di variabili di ambiente che appartengono a ogni RDBMS sul server Adobe Campaign.

Come regola generale, devi installare il livello client corrispondente sul database esterno sul server Adobe Campaign.

>[!NOTE]
>
>Le versioni compatibili sono elencate in [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).


## Passaggi di configurazione {#fda-configuration-steps}

Per impostare l&#39;accesso a un database esterno con FDA, i passaggi di configurazione sono i seguenti:

1. Installa i driver e configura l&#39;account esterno corrispondente al database sul server Adobe Campaign. Fai riferimento alle pagine specifiche del database [elencate di seguito](#fda-specific-configuration)
1. Verifica l’account esterno o crea una connessione temporanea tra Adobe Campaign e il database esterno. [Ulteriori informazioni](../../installation/using/connecting-to-database.md)
1. Crea lo schema del database esterno in Adobe Campaign. Ciò ti consente di identificare la struttura dati del database esterno. [Ulteriori informazioni](../../installation/using/creating-data-schema.md)
1. Se necessario, crea una nuova mappatura di destinazione dallo schema creato in precedenza. Questo è necessario se i destinatari delle consegne provengono dal database esterno. Questa implementazione include limitazioni relative alla personalizzazione dei messaggi. [Ulteriori informazioni](../../installation/using/defining-data-mapping.md)

Una volta creato lo schema di dati, i dati possono essere elaborati nei flussi di lavoro Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/accessing-an-external-database--fda-.md).

## Configurazione specifica del database {#fda-specific-configuration}

A seconda dei database esterni a cui desideri accedere da Adobe Campaign, dovrai eseguire alcune configurazioni specifiche. Queste configurazioni comportano essenzialmente l’installazione di driver e la dichiarazione di variabili di ambiente che appartengono a ogni RDBMS sul server Adobe Campaign e la configurazione dell’account esterno.

Segui i collegamenti riportati di seguito per ulteriori informazioni:

* Connetti campagna e [Vertica](../../installation/using/configure-fda-vertica.md)

* Connetti Campaign e [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)

* Connetti campagna e [Azure synapse](../../installation/using/configure-fda-synapse.md)

* Connetti campagna e [Snowflake](../../installation/using/configure-fda-snowflake.md)

* Connetti campagna e [Hadoop](../../installation/using/configure-fda-hadoop.md)

* Connetti Campaign e [Oracle](../../installation/using/configure-fda-oracle.md)

* Connetti campagna e [Netezza](../../installation/using/configure-fda-netezza.md)

* Connetti campagna e [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* Connetti campagna e [Teradata](../../installation/using/configure-fda-teradata.md)

* Connetti Campaign e [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
