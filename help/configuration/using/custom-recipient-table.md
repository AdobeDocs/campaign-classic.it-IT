---
title: Informazioni sul modello dati di Adobe Campaign Classic
description: Questo documento descrive le nozioni di base del modello dati di Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Utilizzo di una tabella di destinazione personalizzata{#custom-recipient-table}

Durante la progettazione del modello dati di Adobe Campaign, puoi utilizzare la tabella [dei destinatari](../../configuration/using/default-recipient-table.md)out-of-the-box o decidere di creare una tabella dei destinatari non standard per memorizzare i profili di marketing.

Infatti, se il modello dati non soddisfa la struttura incentrata sui destinatari, puoi impostare altre tabelle come dimensione di targeting in Adobe Campaign. Ad esempio, questo può essere rilevante quando è necessario rivolgersi a famiglie, account (come telefoni cellulari) e società/siti invece che semplicemente a destinatari.

>[!NOTE]
>
>In questo caso, dovrete creare una nuova mappatura [di](../../configuration/using/target-mapping.md)destinazione.

Tutti i principi e i passaggi necessari per utilizzare una tabella di destinatari personalizzata sono descritti in dettaglio in questa [sezione](../../configuration/using/about-custom-recipient-table.md).

I vantaggi derivanti dall&#39;utilizzo di una tabella Destinatario personalizzata sono i seguenti:

## Modello dati flessibile {#flexible-data-model}

La tabella del destinatario out-of-the-box è inutile se non hai bisogno della maggior parte dei campi della tabella Recipient o se il modello dati non è incentrato sul destinatario.

## Scalabilità {#scalability}

I grandi volumi richiedono una tabella semplificata con pochi campi per una progettazione efficiente. La tabella dei destinatari out-of-the-box contiene troppi campi inutili, che possono avere un impatto sulle prestazioni e una scarsa efficienza.

## Posizione dati {#data-location}

Se i dati si trovano in un database di marketing esistente esterno, potrebbe essere necessario troppo impegno per utilizzare la tabella dei destinatari out-of-the-box. Creare una nuova struttura basata su una struttura esistente è più semplice.

## Migrazione semplice {#easy-migration}

Non è necessaria alcuna manutenzione per verificare che tutte le estensioni siano ancora valide al momento dell&#39;aggiornamento.

>[!IMPORTANT]
>
>L&#39;utilizzo di una tabella di destinatari personalizzata è riservato agli utenti avanzati ed è soggetto a alcune limitazioni. Per ulteriori informazioni, consulta questa sezione.
