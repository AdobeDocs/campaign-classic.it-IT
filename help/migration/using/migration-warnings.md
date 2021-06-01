---
product: campaign
title: Avvisi di migrazione
description: Avvisi di migrazione
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 46b46fc9-c7c9-4c74-b5f3-7935d5368520
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# Avvisi di migrazione{#migration-warnings}

* Il processo di migrazione è riservato agli utenti esperti. Devi essere assistito da almeno un esperto di database, un amministratore di sistema e uno sviluppatore di applicazioni di Adobe Campaign.
* Prima di avviare la migrazione, verifica che i sistemi e i componenti di sistema utilizzati siano in realtà compatibili con v7. Consultare la [matrice di compatibilità](../../rn/using/compatibility-matrix.md).
* Se utilizzi Adobe Campaign Cloud Messaging (in precedenza mid-sourcing), contatta Adobe Campaign prima di avviare l’intera procedura di migrazione.
* Prima di avviare un processo di migrazione, devi eseguire il backup dei dati **e**.
* Il processo di migrazione potrebbe richiedere diversi giorni per essere completato.
* Adobe Campaign v7 è più rigoroso rispetto alle versioni 5.11 e 6.02 in termini di configurazione. Questo è principalmente per evitare problemi come la corruzione dei dati e per preservare l&#39;integrità dei dati nel database. Di conseguenza, alcune funzioni offerte nelle versioni v5.11 e v6.02 potrebbero non funzionare più nella versione v7 e potrebbero quindi essere adattate dopo la migrazione. Prima di mettere in produzione qualsiasi cosa, ti consigliamo di testare sistematicamente tutte le configurazioni, in particolare i flussi di lavoro necessari per utilizzare Adobe Campaign.

>[!NOTE]
>
>È inoltre necessario consultare la sezione [Prima di avviare la migrazione](../../migration/using/before-starting-migration.md) .
