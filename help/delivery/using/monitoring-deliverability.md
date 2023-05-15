---
product: campaign
title: Monitoraggio del recapito messaggi in Adobe Campaign
description: Scopri gli strumenti e le linee guida sul monitoraggio del recapito messaggi in Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# Monitorare il recapito messaggi{#monitoring-deliverability}



Di seguito sono riportati i dettagli sui diversi strumenti di monitoraggio forniti da Adobe Campaign, nonché alcune linee guida aggiuntive sull’utilizzo delle funzionalità offerte da Adobe Campaign per monitorare il recapito messaggi della piattaforma.

## Informazioni sul monitoraggio del recapito messaggi {#about-deliverability-monitoring}

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. Per utilizzarlo, è necessario installare questo pacchetto. Al termine, riavvia il server per tenere conto del pacchetto.
* Per client ospitati e ibridi, **Monitoraggio del recapito messaggi** è configurato nell’istanza da un servizio di assistenza tecnica e consulenti Adobe. Per ulteriori informazioni, contatta il tuo Adobe Account Executive.

* Per le installazioni on-premise, devi installare il **[!UICONTROL Deliverability monitoring (Email Deliverability)]** tramite **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Per ulteriori informazioni, consulta [Installare i pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic, **Monitoraggio del recapito messaggi** è gestito dal **[!UICONTROL Refresh for deliverability]** workflow. È installato per impostazione predefinita su tutte le istanze e ti consente di inizializzare l’elenco delle regole di qualifica della posta non recapitata, l’elenco dei domini e l’elenco delle MX. Una volta che **[!UICONTROL Deliverability monitoring (Email Deliverability)]** Il pacchetto è installato, questo flusso di lavoro viene eseguito ogni notte per aggiornare regolarmente l’elenco delle regole e consente di gestire attivamente il recapito messaggi della piattaforma.

Il pacchetto Recapito messaggi ti consente di accedere a:

* La [Casella in entrata - Rapporto di rendering](inbox-rendering.md) che consente di visualizzare in anteprima i messaggi sui principali client e-mail al fine di eseguire la scansione del contenuto e della reputazione.
* Panoramica della qualità dei messaggi (inbox, spam).

## Strumenti di monitoraggio {#monitoring-tools}

Puoi anche utilizzare i seguenti strumenti:

* La **[!UICONTROL Delivery throughput]** report offre una panoramica dell&#39;intero throughput della piattaforma per un determinato periodo di tempo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).
* Ogni consegna genera un rapporto sulle statistiche di trasmissione per i diversi provider di servizi Internet (ISP). Mostra alcune metriche sulla qualità dei dati e sulla reputazione che possono influenzare il recapito messaggi, inclusi i seguenti numeri:
   * **[!UICONTROL Hard bounces]** indicano la qualità dei dati. Questo numero dovrebbe essere inferiore al 2%.
   * **[!UICONTROL Soft bounces]** indicare la reputazione. Questo numero non deve essere superiore al 10% per un dato ISP.

   Per ulteriori informazioni, consulta la sezione [Statistiche di consegna](../../reporting/using/global-reports.md#delivery-statistics) sezione .
* Più in generale, la [dashboard di consegna](about-delivery-monitoring.md) consente di accedere a:
   * la [riepilogo della consegna](delivery-dashboard.md#delivery-summary), che mostra i dettagli dell’invio e il numero di messaggi da inviare, elaborare e inviare con successo;
   * la [registri di consegna e cronologia](delivery-dashboard.md#delivery-logs-and-history), che indicano quale obiettivo è stato escluso e perché;
   * la [log di tracking](delivery-dashboard.md#tracking-logs), che mostrano informazioni di tracciamento come aperture e clic.

## Linee guida per il monitoraggio {#monitoring-guidelines}

Di seguito sono riportate alcune linee guida aggiuntive sul monitoraggio delle consegne:

* Controllare regolarmente il [velocità di consegna](../../reporting/using/global-reports.md#delivery-throughput) per l&#39;intera piattaforma per verificare se è coerente con la configurazione originale.
* Controlla che [tentativi](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) sono impostati correttamente (30 minuti per il periodo di esecuzione dei nuovi tentativi e più di 20 tentativi) nei modelli di consegna.
* verificare regolarmente che [rimbalzo](understanding-delivery-failures.md#bounce-mail-management) cassetta postale accessibile e l&#39;account non sta per scadere.
* Controlla ogni throughput di consegna, accessibile dal [dashboard di consegna](delivery-dashboard.md), per assicurarti che sia coerente con la validità del contenuto di consegna (ad es. Le vendite flash devono essere consegnate in minuti, non in giorni).
* Quando utilizzi [onde](steps-sending-the-delivery.md#sending-using-multiple-waves), verifica che ogni onda abbia tempo sufficiente per terminare prima che venga attivata quella successiva.
* Verifica che il numero di errori e di nuovi [quarantena](understanding-quarantine-management.md) sono coerenti con altre consegne.
* Consulta attentamente [registri di consegna](delivery-dashboard.md#delivery-logs-and-history) in dettaglio per verificare il tipo di errori evidenziati (elenco Bloccati, problemi DNS, regole anti-spam, ecc.).
