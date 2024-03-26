---
product: campaign
title: Oggetti di applicazione
description: Oggetti di applicazione
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 5%

---

# Oggetti di applicazione{#application-objects}



Gli oggetti incorporati devono essere monitorati ed è importante evitare che crescano troppo.

## Sequenza di ID {#sequence-of-ids}

Adobe Campaign utilizza una sequenza ID che deve essere utilizzata di conseguenza: **xtkNewId**. Se la sequenza viene consumata molto rapidamente (da 100.000 al giorno), devi verificare che sia coerente con i requisiti aziendali, ad esempio l’invio di milioni di e-mail al giorno. È possibile definire una sequenza dedicata per tabelle particolari. Puoi impostare un flusso di lavoro per monitorare l’utilizzo degli ID.

Quando la sequenza raggiunge più di 2 miliardi (2.147.483.648 è il numero esatto), torna a zero. Deve essere evitato e crea problemi, ed è per questo che questa sequenza deve essere monitorata.

Per evitare questo problema con tabelle di grandi dimensioni, è consigliabile utilizzare una sequenza specifica. Questa operazione può essere eseguita con **pkSequence** nello schema.

I flussi di lavoro ad alta frequenza che creano molti registri richiederanno molti ID. Pertanto, si consiglia vivamente di evitare troppi registri e alte frequenze nei flussi di lavoro.

Se la sequenza è già ciclicata, la soluzione migliore è passare agli ID negativi, partendo da -2.147.483.648.

## Cartelle {#folders}

Su qualsiasi istanza devono essere presenti meno di 1000 cartelle. Se il numero di cartelle supera questo limite, si possono verificare problemi di prestazioni con il client Campaign. È possibile impostare un processo di monitoraggio per contare il numero di cartelle, flussi di lavoro e così via e generare rapporti periodici.

Questo metodo evidenzia anche gli utenti che creano troppi oggetti.

## Consegne {#deliveries}

In qualsiasi momento nell’istanza dovrebbero essere presenti meno di 1000 consegne. La presenza di un numero elevato di consegne consuma spazio nel database e crea problemi. Un’istanza che crea più di 10 consegne al giorno deve essere verificata in base ai requisiti aziendali. Valuta l’utilizzo di consegne continue per creare meno consegne. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/continuous-delivery.md).

Le consegne più vecchie di due anni devono essere eliminate dall’istanza.

## File {#files}

Il numero di file sul disco del server applicazioni non deve aumentare indefinitamente.

I flussi di lavoro di importazione creano file e quindi causano l’espansione del disco. Questo può essere impedito utilizzando lo standard [Raccoglitore file](../../workflow/using/file-collector.md) attività. L&#39;agente di raccolta file sposta i file in una cartella temporanea e li elimina automaticamente.

Se un flusso di lavoro importa file e non utilizza le funzioni standard, deve essere eliminato per ridurre al minimo lo spazio su disco.

## Dati e registri transazionali {#transactional-data-and-logs}

Ogni [workflow](../../workflow/using/data-life-cycle.md#work-table) che importa i dati in Adobe Campaign fa crescere le dimensioni del database.

Verifica che i flussi di lavoro di pulizia o rimozione siano in esecuzione e che i record vengano eliminati in modo efficace. Tutti i dati e i registri transazionali devono essere eliminati. L’attività di pulizia elimina solo le tabelle standard: i registri di tracciamento e i registri generali. Tabelle specifiche devono essere eliminate da flussi di lavoro specifici. Fai riferimento a [questa sezione](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Controlla la misurazione della durata dei dati transazionali controllando la data di creazione dei record meno recente.
