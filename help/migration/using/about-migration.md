---
product: campaign
title: Migrazione a Campaign Classic
description: Scopri come migrare a Campaign Classic da una versione precedente di Campaign
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# Introduzione alla migrazione{#about-migration}



Questo documento descrive i prerequisiti per una migrazione e i passaggi per una migrazione a Adobe Campaign Classic v7. I passaggi e le impostazioni facoltative dipendono dalla configurazione.

Il processo di migrazione deve essere eseguito con cautela, i suoi effetti devono essere considerati in anticipo e la procedura deve essere eseguita con rigore. Deve essere eseguito solo da un utente esperto. Ti consigliamo vivamente di contattare [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) prima di avviare qualsiasi procedura di migrazione.

La migrazione deve essere testata preventivamente nell’ambiente di test/staging per garantire che funzioni senza problemi e senza errori. La migrazione dell’ambiente di produzione deve essere eseguita solo dopo che l’ambiente di test migrato è stato completamente convalidato.

>[!NOTE]
>
>Le nuove funzioni e i miglioramenti apportati ad Adobe Campaign v7 sono descritti in dettaglio nella [Note sulla versione](../../rn/using/latest-release.md).


## Prerequisiti

* Il processo di migrazione deve essere eseguito da utenti esperti. È necessario essere assistiti almeno da un esperto di database, un amministratore di sistema e uno sviluppatore di applicazioni di Adobe Campaign.
* Prima di avviare la migrazione, verifica che i sistemi e i componenti di sistema utilizzati siano compatibili con v7. [Ulteriori informazioni](../../rn/using/compatibility-matrix.md).
* Se utilizzi Adobe Campaign Cloud Messaging (implementazione mid-sourcing), contatta l’Assistenza clienti Adobe prima di iniziare.
* Prima di avviare un processo di migrazione, **deve** eseguire il backup dei dati.
* Il completamento del processo di migrazione potrebbe richiedere diversi giorni.
* Adobe Campaign v7 è una versione più sicura rispetto alle precedenti: questo influisce sulle linee guida di configurazione per evitare problemi come il danneggiamento dei dati e per preservare l’integrità dei dati nel database. In qualità di cliente, sei responsabile del test di tutte le configurazioni, inclusi i flussi di lavoro.

Altri prerequisiti sono disponibili in [questa pagina](../../migration/using/before-starting-migration.md).


## Ambiente modernizzato {#modernizing-your-environment}

L’esecuzione di una migrazione può rappresentare un’opportunità per aggiornare l’ambiente (motori di database, sistemi operativi). Adobe Campaign consiglia vivamente di aggiornare gli ambienti di produzione alle versioni più recenti.

>[!CAUTION]
>
>Per ulteriori informazioni sulle versioni supportate da Adobe Campaign v7, consulta [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

## Passaggi chiave della migrazione {#key-migration-steps}

La procedura generale per la migrazione ad Adobe Campaign v7 è descritta in [questa pagina](../../migration/using/before-starting-migration.md).


## Configurazioni specifiche {#specific-configurations}

Le modifiche apportate da Adobe Campaign v7 possono anche comportare la necessità di adattare alcune configurazioni specifiche sviluppate nelle versioni precedenti. Pertanto, potrebbe essere necessario eseguire un controllo di audit su tutte le configurazioni prima della migrazione: contatta Adobe Campaign per assistenza.

Ad esempio, è necessario prestare particolare attenzione alle impostazioni specifiche per le applicazioni web, le estensioni dello schema con SQLdata o la clonazione di schemi preconfigurati. Per ulteriori informazioni, consulta [questa pagina](../../migration/using/configuring-your-platform.md).

Allo stesso modo, per rispondere all’aumento della sicurezza in Adobe Campaign, sono stati modificati alcuni meccanismi interni: devi adattare di conseguenza queste configurazioni.

