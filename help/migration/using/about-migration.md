---
product: campaign
title: Migrazione ad Campaign Classic
description: Scopri come migrare a Campaign Classic da una versione precedente di Campaign
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# Guida introduttiva alla migrazione{#about-migration}

![](../../assets/v7-only.svg)

Questo documento descrive i prerequisiti di una migrazione, i passaggi per una migrazione a Adobe Campaign Classic v7. I passaggi e le impostazioni facoltative dipendono dalla configurazione.

Il processo di migrazione deve essere svolto con cautela, i suoi impatti devono essere presi in considerazione in anticipo e la procedura deve essere eseguita con rigore. Deve essere eseguito solo da un utente esperto. Consigliamo vivamente di contattare [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) prima di avviare una procedura di migrazione.

La migrazione deve essere testata in anticipo sull’ambiente di test/stage per assicurarsi che funzioni correttamente e senza errori. La migrazione dell’ambiente di produzione deve essere eseguita solo dopo che l’ambiente di test migrato è stato completamente convalidato.

>[!NOTE]
>
>Le nuove funzioni e i miglioramenti apportati con Adobe Campaign v7 sono descritti in [Note sulla versione](../../rn/using/latest-release.md).


## Prerequisiti

* Il processo di migrazione deve essere eseguito da utenti esperti. Devi essere assistito da almeno un esperto di database, un amministratore di sistema e uno sviluppatore di applicazioni di Adobe Campaign.
* Prima di avviare la migrazione, verifica che i sistemi e i componenti di sistema utilizzati siano compatibili con v7. [Ulteriori informazioni](../../rn/using/compatibility-matrix.md).
* Se utilizzi Adobe Campaign Cloud Messaging (distribuzione di mid-sourcing), contatta l’Assistenza clienti Adobe prima di iniziare.
* Prima di avviare un processo di migrazione, **deve** eseguire il backup dei dati.
* Il processo di migrazione potrebbe richiedere diversi giorni per essere completato.
* Adobe Campaign v7 è una versione più sicura rispetto alle precedenti: questo influisce sulle linee guida di configurazione per evitare problemi quali il danneggiamento dei dati e per preservare l’integrità dei dati nel database. In qualità di cliente, sei responsabile del test di tutte le configurazioni, compresi i flussi di lavoro.

Sono disponibili ulteriori prerequisiti in [questa pagina](../../migration/using/before-starting-migration.md).


## Ambiente moderno {#modernizing-your-environment}

L’esecuzione di una migrazione può essere un’opportunità per aggiornare l’ambiente (motori di database, sistemi operativi). Adobe Campaign consiglia vivamente di aggiornare gli ambienti di produzione alle versioni più recenti.

>[!CAUTION]
>
>Per ulteriori informazioni sulle versioni supportate da Adobe Campaign v7, consulta [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

## Passaggi chiave per la migrazione {#key-migration-steps}

La procedura generale per la migrazione ad Adobe Campaign v7 è descritta in [questa pagina](../../migration/using/before-starting-migration.md).


## Configurazioni specifiche {#specific-configurations}

Le modifiche introdotte da Adobe Campaign v7 possono anche significare che è necessario adattare alcune configurazioni specifiche sviluppate nelle versioni precedenti. Pertanto, potrebbe essere necessario eseguire un controllo di tutte le configurazioni prima della migrazione: contatta Adobe Campaign per assistenza.

Ad esempio, è necessario prestare particolare attenzione alle impostazioni specifiche per le applicazioni Web, alle estensioni dello schema con SQLdata o alla duplicazione di schemi preconfigurata. Per ulteriori informazioni, consulta [questa pagina](../../migration/using/configuring-your-platform.md).

Allo stesso modo, per rispondere all’aumento della sicurezza in Adobe Campaign, sono stati modificati alcuni meccanismi interni: devi adattare di conseguenza queste configurazioni.

