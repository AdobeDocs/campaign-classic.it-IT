---
product: campaign
title: Prestazioni della consegna e risoluzione dei problemi
description: Scopri come ottimizzare le prestazioni di consegna e risolvere i problemi in Campaign Classic v7
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Prestazioni della consegna e risoluzione dei problemi {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Una guida completa sulle prestazioni e sulle best practice per la consegna è documentata nella pagina [Best practice per la consegna in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Questo contenuto si applica sia agli utenti di Campaign Classic v7 che a quelli di Campaign v8.
>
>In questa pagina sono documentate **configurazioni specifiche per Campaign Classic v7** per l&#39;ottimizzazione delle prestazioni e la risoluzione dei problemi nelle distribuzioni ibride e on-premise.

Per informazioni complete sulle prestazioni di consegna, l&#39;ottimizzazione della piattaforma, la gestione della quarantena, la manutenzione del database e le raccomandazioni sulla pianificazione, consulta la [documentazione sulle best practice di consegna di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Ottimizzazione delle prestazioni {#performance-optimization}

Per **distribuzioni ibride/on-premise di Campaign Classic v7**, le seguenti ottimizzazioni del database e dell&#39;infrastruttura possono migliorare le prestazioni di consegna.

### Ottimizzazione del database

**Indirizzi indice** per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione. Un indice può essere dichiarato dall’elemento principale dello schema di dati. Questa ottimizzazione richiede l’accesso diretto al database e la personalizzazione dello schema, disponibili nelle distribuzioni on-premise.

### Ottimizzazione dell&#39;infrastruttura

**Configurazione delle consegne di grandi dimensioni**: le consegne a più di un milione di destinatari richiedono spazio nelle code di invio. Per le installazioni on-premise, gli elementi secondari MTA possono essere configurati per gestire dimensioni batch personalizzate. Contatta l’amministratore di sistema per regolare queste impostazioni in base alla capacità dell’infrastruttura.

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, l’ottimizzazione dell’infrastruttura e la configurazione MTA sono gestite da Adobe. Consulta le [Best practice per la consegna di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} per raccomandazioni sulle prestazioni applicabili alla distribuzione.

### Manutenzione del database {#database-maintenance}

Per **distribuzioni ibride/on-premise di Campaign Classic v7**, la manutenzione della piattaforma e del database influisce direttamente sulle prestazioni di invio della consegna.

Le attività di manutenzione regolari includono:

**Pulizia database**: utilizzare il flusso di lavoro di pulizia del database per rimuovere i registri di consegna precedenti, i dati di tracciamento e le tabelle temporanee. Una scarsa manutenzione del database può rallentare la preparazione e l’invio delle consegne.

**Monitoraggio delle prestazioni del database**: monitorare le prestazioni delle query, la frammentazione dell&#39;indice e le statistiche delle tabelle. Per istruzioni dettagliate, consulta [questa pagina](../../production/using/database-performances.md).

**Monitoraggio del flusso di lavoro tecnico**: assicurati che tutti i flussi di lavoro tecnici (in particolare i flussi di lavoro di pulizia, tracciamento e aggiornamento del recapito messaggi) vengano eseguiti correttamente senza errori.

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, la manutenzione del database e i flussi di lavoro tecnici sono monitorati e gestiti da Adobe. Concentrati sul monitoraggio specifico della consegna come descritto nella [Documentazione sulle consegne del monitoraggio di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Risoluzione dei problemi di consegna {#troubleshooting}

>[!NOTE]
>
>Una guida completa sulla risoluzione dei problemi di consegna è documentata nella documentazione di Campaign v8, applicabile sia agli utenti di Campaign Classic v7 che di Campaign v8:
>
>* Soluzioni e errori di consegna comuni: [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnosi di consegna lenta: [Monitorare le consegne nell&#39;interfaccia utente di Campaign](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Best practice di consegna: [Best practice di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>In questa sezione viene documentata la risoluzione dei problemi specifici di **Campaign Classic v7** per le distribuzioni ibride e on-premise.

Per **distribuzioni ibride/on-premise di Campaign Classic v7**, i seguenti passaggi per la risoluzione dei problemi sono specifici per l&#39;infrastruttura gestita.

### Configurazione regole MX

In caso di problemi di limitazione con ISP specifici, potrebbe essere necessario rivedere e modificare la configurazione delle regole MX. Per ulteriori informazioni sulle regole MX e sulle quote, consultare [questa sezione](../../installation/using/email-deliverability.md#about-mx-rules).

### Manutenzione del database per le prestazioni di consegna

Se riscontri il seguente errore nelle distribuzioni di mid-sourcing:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

La causa è collegata a problemi di prestazioni in cui l’istanza di marketing trascorre troppo tempo a creare dati prima di inviarli al server di mid-sourcing.

**Per le installazioni on-premise**, eseguire un&#39;operazione di vuoto e reindicizzazione sul database. Per ulteriori informazioni sulla manutenzione del database, consultare [questa sezione](../../production/using/recommendations.md).

È inoltre necessario riavviare tutti i flussi di lavoro con un&#39;attività pianificata e tutti i flussi di lavoro con stato non riuscito. Fai riferimento a [questa sezione](../../workflow/using/scheduler.md).

### Monitoraggio tecnico dei flussi di lavoro

Per le installazioni on-premise, assicurati che tutti i flussi di lavoro tecnici relativi al recapito messaggi siano in esecuzione senza errori:

**Flusso di lavoro di aggiornamento del recapito messaggi**: aggiornamenti regole di qualifica della posta non recapitata e indicatori di recapito messaggi.

**Flusso di lavoro di tracciamento**: elabora i dati di tracciamento per le consegne inviate.

**Flusso di lavoro di pulizia del database**: elimina regolarmente i registri di consegna precedenti e le tabelle temporanee per mantenere le prestazioni.

Controllare lo stato del flusso di lavoro in **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, i flussi di lavoro tecnici e il monitoraggio dell’infrastruttura sono gestiti da Adobe. Concentrati sul contenuto e sul targeting della consegna come descritto nella [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Argomenti correlati

* [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentazione di Campaign v8)
* [Best practice per la consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentazione di Campaign v8)
* [Monitorare le consegne nell&#39;interfaccia utente di Campaign](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentazione di Campaign v8)
* [Manutenzione del database](../../production/using/recommendations.md) (v7 ibrido/on-premise)
* [Recapito e-mail](../../installation/using/email-deliverability.md) (v7 ibrido/on-premise)
* [Prestazioni del database](../../production/using/database-performances.md) (v7 ibrido/on-premise)

