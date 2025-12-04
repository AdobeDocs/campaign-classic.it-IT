---
product: campaign
title: Best practice per le prestazioni di consegna
description: Ulteriori informazioni sulle prestazioni di consegna e sulle best practice
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# Best practice per le prestazioni di consegna {#delivery-performances}

>[!NOTE]
>
>Una guida completa sulle prestazioni e sulle best practice per la consegna è documentata nella pagina [Best practice per la consegna in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Questo contenuto si applica sia agli utenti di Campaign Classic v7 che a quelli di Campaign v8.
>
>In questa pagina sono documentate le **configurazioni delle prestazioni specifiche di Campaign Classic v7** per le distribuzioni ibride e on-premise.

Per informazioni complete sulle prestazioni di consegna, l&#39;ottimizzazione della piattaforma, la gestione della quarantena, la manutenzione del database e le raccomandazioni sulla pianificazione, consulta la [documentazione sulle best practice di consegna di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Ottimizzazione delle prestazioni {#best-practices-performance}

Per **distribuzioni ibride/on-premise di Campaign Classic v7**, le seguenti ottimizzazioni del database e dell&#39;infrastruttura possono migliorare le prestazioni di consegna:

### Ottimizzazione del database

**Indirizzi indice** per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione. Un indice può essere dichiarato dall’elemento principale dello schema di dati. Questa ottimizzazione richiede l’accesso diretto al database e la personalizzazione dello schema, disponibili nelle distribuzioni on-premise.

### Ottimizzazione dell&#39;infrastruttura

**Configurazione delle consegne di grandi dimensioni**: le consegne a più di un milione di destinatari richiedono spazio nelle code di invio. Per le installazioni on-premise, gli elementi secondari MTA possono essere configurati per gestire dimensioni batch personalizzate. Contatta l’amministratore di sistema per regolare queste impostazioni in base alla capacità dell’infrastruttura.

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, l’ottimizzazione dell’infrastruttura e la configurazione MTA sono gestite da Adobe. Consulta le [Best practice per la consegna di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} per raccomandazioni sulle prestazioni applicabili alla distribuzione.

## Manutenzione del database {#performance-issues}

Per **distribuzioni ibride/on-premise di Campaign Classic v7**, la manutenzione della piattaforma e del database influisce direttamente sulle prestazioni di invio della consegna.

Le attività di manutenzione regolari includono:

**Pulizia database**: utilizzare il flusso di lavoro di pulizia del database per rimuovere i registri di consegna precedenti, i dati di tracciamento e le tabelle temporanee. Una scarsa manutenzione del database può rallentare la preparazione e l’invio delle consegne.

**Monitoraggio delle prestazioni del database**: monitorare le prestazioni delle query, la frammentazione dell&#39;indice e le statistiche delle tabelle. Per istruzioni dettagliate, consulta [questa pagina](../../production/using/database-performances.md).

**Monitoraggio del flusso di lavoro tecnico**: assicurati che tutti i flussi di lavoro tecnici (in particolare i flussi di lavoro di pulizia, tracciamento e aggiornamento del recapito messaggi) vengano eseguiti correttamente senza errori.

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, la manutenzione del database e i flussi di lavoro tecnici sono monitorati e gestiti da Adobe. Concentrati sul monitoraggio specifico della consegna come descritto nella [Documentazione sulle consegne del monitoraggio di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Argomenti correlati

* [Best practice per la consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentazione di Campaign v8)
* [Monitora il recapito messaggi](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (documentazione di Campaign v8)
* [Risoluzione dei problemi nelle consegne](delivery-troubleshooting.md)
* [Prestazioni del database](../../production/using/database-performances.md) (v7 ibrido/on-premise)
