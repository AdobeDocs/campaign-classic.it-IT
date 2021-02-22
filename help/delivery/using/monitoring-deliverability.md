---
solution: Campaign Classic
product: campaign
title: Monitoraggio della recapito in Adobe Campaign Classic
description: Scopri gli strumenti e le linee guida sul monitoraggio della recapito in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: fa5679d91808edb8e3916d5f0e0f54c73198e934
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 2%

---


# Monitoraggio della consegna messaggi{#monitoring-deliverability}

Qui di seguito troverai informazioni sui diversi strumenti di monitoraggio forniti da  Adobe Campaign e alcune linee guida aggiuntive sul monitoraggio delle consegne.

## Strumenti di monitoraggio {#monitoring-tools}

Utilizzate le funzioni offerte da  Adobe Campaign per monitorare la recapito della piattaforma.

Il pacchetto Deliverability consente di accedere a:

* Il report [Inbox rendering report](../../delivery/using/inbox-rendering.md) che consente di visualizzare l&#39;anteprima dei messaggi sui principali client e-mail per eseguire la scansione del contenuto e della reputazione.
* Panoramica della qualità del messaggio (inbox, spam).

Potete anche usare i seguenti strumenti:

* Il rapporto **[!UICONTROL Delivery throughput]** offre una panoramica dell&#39;intero throughput della piattaforma per un determinato periodo di tempo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).
* Ogni consegna genera un rapporto sulle statistiche di trasmissione per i diversi provider di servizi Internet (ISP). Mostra alcune metriche sulla qualità dei dati e sulla reputazione che possono avere un impatto sulla tua recapito, inclusi i seguenti numeri:
   * **[!UICONTROL Hard bounces]** indicano la qualità dei dati. Tale numero dovrebbe essere inferiore al 2%.
   * **[!UICONTROL Soft bounces]** indica la reputazione. Questo numero non deve essere superiore al 10% per un dato ISP.

   Per ulteriori informazioni, vedere la sezione [Statistiche di consegna](../../reporting/using/global-reports.md#delivery-statistics).
* Più in generale, il [dashboard di consegna](../../delivery/using/about-delivery-monitoring.md) consente di accedere a:
   * il [riepilogo delle consegne](../../delivery/using/delivery-dashboard.md#delivery-summary), che mostra i dettagli dell&#39;invio e il numero di messaggi da inviare, elaborare e inviare con esito positivo;
   * i [registri di consegna e la cronologia](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history), che mostrano quale destinazione è stata esclusa e perché;
   * i [registri di monitoraggio](../../delivery/using/delivery-dashboard.md#tracking-logs), che mostrano informazioni di tracciamento come aperture e clic.

## Linee guida per il monitoraggio {#monitoring-guidelines}

Seguono alcune linee guida aggiuntive sul monitoraggio della recapito:

* Controllare regolarmente la [velocità di consegna](../../reporting/using/global-reports.md#delivery-throughput) per l&#39;intera piattaforma per verificare se è coerente con la configurazione originale.
* Verificate che [i tentativi](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) siano impostati correttamente (30 minuti per il periodo dei tentativi e più di 20 tentativi) nei modelli di consegna.
* Verificare regolarmente che la cassetta postale [bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) sia accessibile e che l&#39;account non stia per scadere.
* Controllate ogni throughput di distribuzione per assicurarvi che sia coerente con la validità del contenuto di distribuzione (ad es. Le vendite flash devono essere consegnate in minuti, non in giorni).
* Quando si utilizza [onde](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verificare che ogni onda abbia tempo sufficiente per terminare prima che venga attivata la successiva.
* Verificare che il numero di errori e le nuove [quarantena](../../delivery/using/understanding-quarantine-management.md) siano coerenti con altre consegne.
* Consultate attentamente i [log di consegna](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) per verificare nel dettaglio il tipo di errori evidenziati (elenchi Bloccati, problemi DNS, regole anti-spam, ecc.).

## Spam di segnale {#signal-spam}

Signal Spam è un servizio francese che offre un report anonimo sul loop di feedback per gli ISP francesi (Orange, SFR).

* Questo servizio consente di seguire la reputazione degli ISP francesi e di monitorare l&#39;evoluzione dell&#39;attività dei clienti.

* Il segnale Spam fornisce inoltre reclami diretti che gli utenti finali accedono attraverso un&#39;interfaccia dedicata. Tali reclami vengono quindi messi in quarantena dal database degli indirizzi e-mail.

## 250ok {#deliverability-250ok}

[250](https://250ok.com/) okis è una soluzione di monitoraggio complementare agli strumenti interni di recapito del Adobe  che forniscono elenco Bloccati IP e dominio e indicatori di reputazione.

Le informazioni fornite sono in tempo reale, il che consente un&#39;assistenza proattiva.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
