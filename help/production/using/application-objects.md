---
title: Oggetti di applicazione
seo-title: Oggetti di applicazione
description: Oggetti di applicazione
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 4%

---


# Oggetti di applicazione{#application-objects}

Gli oggetti incorporati devono essere monitorati ed è importante evitare che la loro crescita sia eccessiva.

## Sequenza di ID {#sequence-of-ids}

 Adobe Campaign utilizza una sequenza di ID che deve essere utilizzata di conseguenza: **xtkNewId**. Se la sequenza viene consumata molto rapidamente (ovvero da 100.000 al giorno), è necessario verificare che sia conforme ai requisiti aziendali, ad esempio inviare milioni di e-mail al giorno. È possibile definire una sequenza dedicata per tabelle particolari. Puoi impostare un flusso di lavoro per monitorare l’utilizzo degli ID.

Quando la sequenza raggiunge più di 2 miliardi (2.147.483.648 è il numero esatto), torna a zero. Deve essere evitata e creare problemi, motivo per cui questa sequenza deve essere monitorata.

Per evitare questo problema con tabelle di grandi dimensioni, è consigliabile utilizzare una sequenza specifica. Questo può essere fatto con l&#39;attributo **pkSequence** nello schema.

Flussi di lavoro ad alta frequenza che creano molti file di registro richiederanno molti ID. Si consiglia quindi di evitare troppi registri e frequenze elevate nei flussi di lavoro.

Se la sequenza è già passata, la soluzione migliore è passare agli ID negativi, a partire da -2.147.483.648.

## Cartelle {#folders}

In qualsiasi istanza devono essere presenti meno di 1000 cartelle. La presenza di più cartelle può causare problemi di prestazioni con il client Campaign. Potete impostare un processo di monitoraggio per contare il numero di cartelle, flussi di lavoro e così via, e generare un rapporto periodico.

Questo metodo evidenzia anche gli utenti che creano troppi oggetti.

## Consegne {#deliveries}

L&#39;istanza deve contenere meno di 1000 consegne in qualsiasi momento. L&#39;utilizzo di un gran numero di consegne richiede spazio nel database e crea problemi. Un&#39;istanza che crea più di 10 consegne al giorno deve essere verificata in base ai requisiti aziendali. Considerate l&#39;utilizzo di consegne continue per creare meno consegne. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/continuous-delivery.md).

Le consegne di durata superiore a due anni dovrebbero essere eliminate dall&#39;istanza.

## File {#files}

Il numero di file sul disco del server dell&#39;applicazione non deve aumentare all&#39;infinito.

I flussi di lavoro di importazione creano i file e causano quindi l’espansione del disco. Questo può essere impedito utilizzando l&#39;attività di raccolta [standard](../../workflow/using/file-collector.md) File. Il raccoglitore file sposta i file in una cartella temporanea e li elimina automaticamente.

Se un flusso di lavoro importa file e non utilizza le funzioni standard, deve essere eliminato per ridurre al minimo lo spazio su disco.

## Dati e registri transazionali {#transactional-data-and-logs}

Ogni [flusso di lavoro](../../workflow/using/data-life-cycle.md#work-table) che importa i dati in  Adobe Campaign determina un aumento delle dimensioni del database.

Verificate che i flussi di lavoro di pulizia o rimozione siano in esecuzione e che i record vengano eliminati in modo efficace. Tutti i dati e i registri transazionali devono essere eliminati. L&#39;attività di pulizia elimina solo le tabelle standard: tracking e log ampi. Le tabelle specifiche devono essere eliminate da flussi di lavoro specifici. Fai riferimento a [questa sezione](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Controlla i dati delle transazioni di invecchiamento controllando la data di creazione più vecchia dei record.
