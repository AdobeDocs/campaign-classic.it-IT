---
product: campaign
title: Oggetti di applicazione
description: Oggetti di applicazione
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---

# Oggetti di applicazione{#application-objects}

![](../../assets/v7-only.svg)

Gli oggetti incorporati devono essere monitorati ed evitare che crescano troppo è importante.

## Sequenza degli ID {#sequence-of-ids}

Adobe Campaign utilizza una sequenza ID che deve essere utilizzata di conseguenza: **xtkNewId**. Se la sequenza viene consumata molto rapidamente (ovvero da 100.000 al giorno), devi verificare che sia coerente con i requisiti aziendali, ad esempio l’invio di milioni di e-mail al giorno. È possibile definire una sequenza dedicata per particolari tabelle. Puoi impostare un flusso di lavoro per monitorare l’utilizzo degli ID.

Quando la sequenza raggiunge più di 2 miliardi (2.147.483.648 è il numero esatto), torna a zero. Bisogna evitarlo e creare problemi, motivo per cui questa sequenza deve essere monitorata.

Per evitare questo problema con tabelle di grandi dimensioni, è consigliabile utilizzare una sequenza specifica. Questo può essere fatto con l&#39;attributo **pkSequence** nello schema.

I flussi di lavoro ad alta frequenza che creano molti registri utilizzeranno molti ID. È quindi vivamente consigliato evitare troppi registri e alte frequenze nei flussi di lavoro.

Se la sequenza è già stata ciclicata, la soluzione migliore è passare ad ID negativi, a partire da -2.147.483.648.

## Cartelle {#folders}

Ci dovrebbero essere meno di 1000 cartelle su qualsiasi istanza. L’utilizzo di più cartelle può causare problemi di prestazioni con il client Campaign. È possibile impostare un processo di monitoraggio per contare il numero di cartelle, flussi di lavoro, ecc., e generare di nuovo rapporti su base periodica.

Questo metodo evidenzia anche gli utenti che creano troppi oggetti.

## Consegne {#deliveries}

Ci dovrebbero essere meno di 1000 consegne sull’istanza in qualsiasi momento. Molte consegne consumano spazio nel database e creano problemi. Un’istanza che crea più di 10 consegne al giorno deve essere controllata in base ai requisiti aziendali. Prendi in considerazione l’utilizzo di consegne continue per creare meno consegne. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/continuous-delivery.md).

Le consegne con più di due anni devono essere eliminate dall’istanza.

## File {#files}

Il numero di file sul disco dell&#39;application server non deve aumentare a tempo indeterminato.

I flussi di lavoro di importazione creano file e quindi causano l&#39;espansione del disco. Questo può essere impedito utilizzando l&#39;attività [Raccolta file](../../workflow/using/file-collector.md) standard. Il raccoglitore file sposta i file in una cartella temporanea e li elimina automaticamente.

Se un flusso di lavoro importa file e non utilizza le funzioni standard, deve essere eliminato per ridurre al minimo lo spazio su disco.

## Dati e registri transazionali {#transactional-data-and-logs}

Ogni [flusso di lavoro](../../workflow/using/data-life-cycle.md#work-table) che importa dati in Adobe Campaign determina un aumento delle dimensioni del database.

Controlla che i flussi di lavoro di pulizia o pulizia siano in esecuzione ed elimina efficacemente i record. Tutti i dati e i registri transazionali devono essere eliminati. L&#39;attività di pulizia elimina solo le tabelle standard: tracciamento e registri ampi. Tabelle specifiche devono essere eliminate da flussi di lavoro specifici. Fai riferimento a [questa sezione](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Controlla l’invecchiamento dei dati transazionali controllando la data di creazione più vecchia dei record.
