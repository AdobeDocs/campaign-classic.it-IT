---
solution: Campaign Classic
product: campaign
title: Configurare i connettori FDA
description: Scopri i passaggi di configurazione per FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---


# Configurazione dei connettori FDA {#specific-configurations-by-database-type}

A seconda dei database esterni a cui si desidera accedere da  Adobe Campaign, sarà necessario eseguire determinate configurazioni specifiche. Tali configurazioni prevedono essenzialmente l&#39;installazione di driver e la dichiarazione di variabili di ambiente appartenenti a ciascun RDBMS sul server Adobe Campaign .

Come regola generale, è necessario installare il livello client corrispondente nel database esterno sul server Adobe Campaign .

>[!NOTE]
>
>Le versioni compatibili sono elencate in Matrice [compatibilità](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)campagna.


## Passaggi di configurazione {#fda-configuration-steps}

Per impostare l&#39;accesso a un database esterno con FDA, i passaggi di configurazione sono:

1. Installate i driver corrispondenti al database sul server Adobe Campaign . I driver sono elencati nelle pagine specifiche del database [elencate di seguito](#fda-specific-configuration).
1. [Creare e configurare un account](../../installation/using/connecting-to-database.md) esterno che consenta di stabilire la connessione tra  Adobe Campaign e il database esterno. Per ulteriori informazioni sugli account esterni in Campaign, consulta [questa pagina](../../installation/using/external-accounts.md).
1. [Create lo schema](../../installation/using/creating-data-schema.md) del database esterno in  Adobe Campaign. Questo consente di riconoscere la struttura dati del database esterno.
1. Se necessario, [create una nuova mappatura](../../installation/using/defining-data-mapping.md) di destinazione dallo schema creato in precedenza. Questo è richiesto se i destinatari delle consegne provengono dal database esterno. Questa implementazione include limitazioni relative alla personalizzazione dei messaggi.

Una volta creato lo schema di dati, i dati possono essere elaborati  flussi di lavoro Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/accessing-an-external-database--fda-.md).

## Configurazione specifica del database {#fda-specific-configuration}

A seconda dei database esterni a cui si desidera accedere da  Adobe Campaign, sarà necessario eseguire determinate configurazioni specifiche. Tali configurazioni prevedono essenzialmente l&#39;installazione di driver e la dichiarazione di variabili di ambiente appartenenti a ciascun RDBMS sul server Adobe Campaign .

Segui i collegamenti di seguito per saperne di più:

* [Azure synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
