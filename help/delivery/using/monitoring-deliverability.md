---
product: campaign
title: Monitorare il recapito messaggi in Adobe Campaign
description: Scopri gli strumenti e le linee guida per il monitoraggio del recapito messaggi in Adobe Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 1%

---

# Monitorare il recapito messaggi{#monitoring-deliverability}

Di seguito trovi i dettagli sui diversi strumenti di monitoraggio forniti da Adobe Campaign, nonché alcune linee guida aggiuntive sull’utilizzo delle funzioni offerte da Adobe Campaign per monitorare il recapito messaggi della piattaforma.

## Informazioni sul monitoraggio del recapito messaggi {#about-deliverability-monitoring}

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. Per utilizzarlo, è necessario installare questo pacchetto. Al termine, riavvia il server affinché il pacchetto venga preso in considerazione.
* Per client in hosting e ibridi, **Monitoraggio della consegna** è configurato nell’istanza dal supporto tecnico e dai consulenti Adobe. Per ulteriori informazioni, contatta il tuo Account Executive Adobe.

* Per le installazioni on-premise, è necessario installare **[!UICONTROL Deliverability monitoring (Email Deliverability)]** tramite il **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Per ulteriori informazioni, consulta [Installare i pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic, **Monitoraggio della consegna** è gestito da **[!UICONTROL Refresh for deliverability]** flusso di lavoro. È installato per impostazione predefinita su tutte le istanze e consente di inizializzare l’elenco delle regole di qualifica della posta non recapitata, l’elenco dei domini e l’elenco dei MX. Una volta **[!UICONTROL Deliverability monitoring (Email Deliverability)]** viene installato, questo flusso di lavoro viene eseguito ogni notte per aggiornare regolarmente l’elenco delle regole e consente di gestire attivamente il recapito messaggi della piattaforma.

Il pacchetto di recapito messaggi consente di accedere a:

* Il [Rapporto di rendering della casella in entrata](inbox-rendering.md) che consente di visualizzare in anteprima i messaggi sui principali client e-mail per esaminare il contenuto e la reputazione.
* Panoramica sulla qualità dei messaggi (posta in arrivo, spam).

## Strumenti di monitoraggio {#monitoring-tools}

È inoltre possibile utilizzare i seguenti strumenti:

* Il **[!UICONTROL Delivery throughput]** Questo rapporto offre una panoramica dell&#39;intera velocità effettiva della piattaforma in un determinato periodo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).
* Ogni consegna genera un rapporto sulle statistiche di trasmissione per i diversi provider di servizi Internet (ISP). Mostra alcune metriche relative alla qualità dei dati e alla reputazione che possono influire sul recapito messaggi, tra cui i seguenti numeri:
   * **[!UICONTROL Hard bounces]** indicare la qualità dei dati. Questo numero deve essere inferiore al 2%.
   * **[!UICONTROL Soft bounces]** indicare la reputazione. Questo numero non deve essere superiore al 10% per un dato ISP.

  Per ulteriori informazioni, consulta [Statistiche consegna](../../reporting/using/global-reports.md#delivery-statistics) sezione.
* Più in generale, [dashboard di consegna](about-delivery-monitoring.md) consente di accedere a:
   * il [riepilogo della consegna](delivery-dashboard.md#delivery-summary), che mostra i dettagli dell&#39;invio e il numero di messaggi da inviare, elaborare e inviare con esito positivo;
   * il [registri e cronologia di consegna](delivery-dashboard.md#delivery-logs-and-history), che indicano quale obiettivo è stato escluso e perché;
   * il [registri di tracciamento](delivery-dashboard.md#tracking-logs), che mostrano informazioni di tracciamento come aperture e clic.

## Linee guida per il monitoraggio {#monitoring-guidelines}

Di seguito sono riportate alcune linee guida aggiuntive sul monitoraggio della consegna dei messaggi:

* Controlla regolarmente la [velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput) per l&#39;intera piattaforma per verificare se è coerente con la configurazione originale.
* Controlla che [nuovi tentativi](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) sono configurate correttamente (30 minuti per il periodo di esecuzione dei nuovi tentativi e più di 20 tentativi) nei modelli di consegna.
* Verifica regolarmente che [rimbalzo](understanding-delivery-failures.md#bounce-mail-management) la cassetta postale è accessibile e l&#39;account non sta per scadere.
* Controlla ogni velocità effettiva di consegna, accessibile dalla [dashboard di consegna](delivery-dashboard.md), per assicurarsi che sia coerente con la validità del contenuto della consegna (ad esempio, &quot;vendite flash&quot; deve essere consegnato in minuti, non in giorni).
* Quando si utilizza [ondate](steps-sending-the-delivery.md#sending-using-multiple-waves), verifica che ogni scaglione abbia abbastanza tempo per terminare prima che venga attivato il successivo.
* Verifica che il numero di errori e le nuove [quarantena](understanding-quarantine-management.md) sono coerenti con le altre consegne.
* Consulta attentamente il [registri di consegna](delivery-dashboard.md#delivery-logs-and-history) in dettaglio per verificare il tipo di errori evidenziati (inserisce nell&#39;elenco Bloccati, problemi DNS, regole anti-spam, ecc.).
