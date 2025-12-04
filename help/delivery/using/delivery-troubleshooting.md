---
product: campaign
title: Risoluzione dei problemi di invio della consegna
description: Ulteriori informazioni sulle prestazioni di consegna e su come risolvere i problemi relativi al monitoraggio della consegna
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# Risoluzione dei problemi di invio della consegna {#delivery-troubleshooting}

>[!NOTE]
>
>Una guida completa sulla risoluzione dei problemi di consegna è documentata nella documentazione di Campaign v8, applicabile sia agli utenti di Campaign Classic v7 che di Campaign v8:
>
>* Soluzioni e errori di consegna comuni: [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnosi di consegna lenta: [Monitorare le consegne nell&#39;interfaccia utente di Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Best practice di consegna: [Best practice di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Questa pagina documenta la **risoluzione dei problemi specifica di Campaign Classic v7** per le distribuzioni ibride e on-premise.

## Risoluzione dei problemi {#v7-specific}

Per **distribuzioni ibride/on-premise di Campaign Classic v7**, i seguenti passaggi per la risoluzione dei problemi sono specifici per l&#39;infrastruttura gestita:

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
>Per gli utenti di Campaign v8 Managed Cloud Services, i flussi di lavoro tecnici e il monitoraggio dell’infrastruttura sono gestiti da Adobe. Concentrati sul contenuto e sul targeting della consegna come descritto nella [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Argomenti correlati

* [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentazione di Campaign v8)
* [Best practice per la consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentazione di Campaign v8)
* [Monitorare le consegne nell&#39;interfaccia utente di Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentazione di Campaign v8)
* [Manutenzione del database](../../production/using/recommendations.md) (v7 ibrido/on-premise)
* [Recapito e-mail](../../installation/using/email-deliverability.md) (v7 ibrido/on-premise)
