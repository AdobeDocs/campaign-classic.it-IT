---
solution: Campaign Classic
product: campaign
title: Accesso a un database esterno
description: Scopri come accedere e elaborare i dati in un database esterno
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 3%

---


# Introduzione a Federated Data Access {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

## Prerequisiti {#operating-principle}

L&#39;opzione FDA consente di estendere il modello dati in un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati provenienti dalle origini SQL.

Per utilizzare questa funzionalità, i prerequisiti sono elencati di seguito:

* **Configurazione**: ad Snowflake, per impostare Federated Data Access è necessario un modello di hosting **locale** o **ibrido** . [Ulteriori informazioni](../../installation/using/hosting-models.md)
* **Versione** del database esterno: è necessario disporre di un database esterno compatibile con il modulo Adobe Campaign FDA . L&#39;elenco dei sistemi di database e delle versioni compatibili è dettagliato nella matrice [di](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)compatibilità delle campagne.
* **Autorizzazioni**: gli utenti devono inoltre disporre delle autorizzazioni [](../../installation/using/remote-database-access-rights.md) necessarie in  Adobe Campaign e nel database esterno.

## Limitazioni {#limitations}

L&#39;opzione FDA è stata creata per manipolare i dati nei database esterni in modalità batch nei flussi di lavoro. Per evitare problemi di prestazioni, si consiglia di utilizzare il modulo FDA nel contesto di operazioni unitarie, ad esempio: personalizzazione, interazione, messaggistica in tempo reale, ecc.

Evitate le operazioni che richiedono l&#39;utilizzo del Adobe Campaign  e del database esterno il più possibile. A questo scopo, potete:

* Esportate il database Adobe Campaign  nel database esterno ed eseguite le operazioni solo dal database esterno prima di reimportare i risultati in  Adobe Campaign.

* Raccogliere i dati dal database Adobe Campaign  esterno ed eseguire le operazioni localmente.

Se desiderate eseguire la personalizzazione nelle consegne utilizzando i dati del database esterno, raccogliete i dati da utilizzare in un flusso di lavoro per renderlo disponibile in una tabella temporanea. Quindi utilizzate i dati della tabella temporanea per personalizzare la consegna.

L&#39;opzione FDA è soggetta ai limiti del sistema di database esterno utilizzato.

## Raccomandazioni {#recommendations}

### Creare schemi temporanei {#create-temporary-schemas}

È possibile gestire diversi accessi al database esterno di Greenplum tramite FDA. Un&#39;opzione dedicata consente di creare uno schema di lavoro direttamente durante la configurazione dell&#39;account esterno.

![](assets/fda_work_table.png)

>[!NOTE]
>
>Questa opzione è disponibile solo con PostgreSQL Greenplum.

### Ottimizzazione della personalizzazione delle e-mail con dati esterni {#optimizing-email-personalization-with-external-data}

Puoi pre-elaborare la personalizzazione dei messaggi in un flusso di lavoro dedicato. Per eseguire questa operazione, utilizzate l&#39; **[!UICONTROL Prepare the personalization data with a workflow]** opzione, disponibile nella **[!UICONTROL Analysis]** scheda delle proprietà di consegna.

Durante l&#39;analisi della consegna, questa opzione crea ed esegue automaticamente un flusso di lavoro che memorizza tutti i dati collegati alla destinazione in una tabella temporanea, compresi i dati provenienti da tabelle collegate in un database esterno.

Questa opzione migliora notevolmente le prestazioni durante l&#39;esecuzione del passaggio di personalizzazione.

### Use data from an external database in a workflow {#using-data-from-an-external-database-in-a-workflow}

In più attività  flusso di lavoro Adobe Campaign, potete utilizzare i dati memorizzati in un database esterno.

* **Filtro su dati** esterni - L&#39;attività [Query](../../workflow/using/targeting-data.md#selecting-data) consente di aggiungere dati esterni e di utilizzarli nelle configurazioni di filtro definite. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/targeting-data.md#selecting-data).

* **Creazione di sottoinsiemi** - L&#39;attività [Dividi](../../workflow/using/split.md) consente di creare sottoinsiemi. È possibile utilizzare dati esterni per definire i criteri di filtro da utilizzare. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/split.md).

* **Carica database** esterno - È possibile utilizzare i dati esterni nell&#39;attività di caricamento [](../../workflow/using/data-loading--rdbms-.md) dei dati (RDBMS). Ulteriori informazioni in [questa pagina](../../workflow/using/data-loading--rdbms-.md).

* **Aggiunta di informazioni e collegamenti** - L&#39;attività [Arricchimento](../../workflow/using/enrichment.md) consente di aggiungere dati aggiuntivi alla tabella di lavoro del flusso di lavoro e collegamenti a una tabella esterna. In questo contesto, può utilizzare i dati provenienti da un database esterno. Ulteriori informazioni in [questa pagina](../../workflow/using/enrichment.md).
