---
solution: Campaign Classic
product: campaign
title: Monitoraggio del recapito messaggi in Adobe Campaign Classic
description: Scopri gli strumenti e le linee guida sul monitoraggio del recapito messaggi in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---


# Monitoraggio della consegna messaggi{#monitoring-deliverability}

Di seguito sono riportati i dettagli sui diversi strumenti di monitoraggio forniti da Adobe Campaign, nonché alcune linee guida aggiuntive sull’utilizzo delle funzionalità offerte da Adobe Campaign per monitorare il recapito messaggi della piattaforma.

## Monitoraggio del recapito messaggi {#configuration}

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. Per utilizzarlo, è necessario installare questo pacchetto. Al termine, riavvia il server per tenere conto del pacchetto.
* Per i client in hosting e ibridi, il **monitoraggio del recapito** è configurato nella tua istanza da un Adobe di supporto tecnico e consulenti. Per ulteriori informazioni, contatta il tuo Adobe Account Executive.

* Per le installazioni on-premise, devi installare il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Per ulteriori informazioni, consulta [Installazione dei pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic, il **monitoraggio del recapito** è gestito dal flusso di lavoro **[!UICONTROL Refresh for deliverability]**. È installato per impostazione predefinita su tutte le istanze e ti consente di inizializzare l’elenco delle regole di qualifica della posta non recapitata, l’elenco dei domini e l’elenco delle MX. Una volta installato il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]**, questo flusso di lavoro viene eseguito ogni notte per aggiornare regolarmente l’elenco delle regole e consente di gestire attivamente il recapito messaggi della piattaforma.

Il pacchetto Recapito messaggi ti consente di accedere a:

* Il [rapporto di rendering della casella in entrata](../../delivery/using/inbox-rendering.md) che consente di visualizzare in anteprima i messaggi sui principali client e-mail al fine di eseguire la scansione del contenuto e della reputazione.
* Panoramica della qualità dei messaggi (inbox, spam).

## Strumenti di monitoraggio {#monitoring-tools}

Puoi anche utilizzare i seguenti strumenti:

* Il rapporto **[!UICONTROL Delivery throughput]** offre una panoramica dell’intero throughput della piattaforma per un determinato periodo di tempo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).
* Ogni consegna genera un rapporto sulle statistiche di trasmissione per i diversi provider di servizi Internet (ISP). Mostra alcune metriche sulla qualità dei dati e sulla reputazione che possono influenzare il recapito messaggi, inclusi i seguenti numeri:
   * **[!UICONTROL Hard bounces]** indicano la qualità dei dati. Questo numero dovrebbe essere inferiore al 2%.
   * **[!UICONTROL Soft bounces]** indicare la reputazione. Questo numero non deve essere superiore al 10% per un dato ISP.

   Per ulteriori informazioni, consulta la sezione [Statistiche di consegna](../../reporting/using/global-reports.md#delivery-statistics) .
* Più in generale, il [dashboard di consegna](../../delivery/using/about-delivery-monitoring.md) ti consente di accedere a:
   * il [riepilogo della consegna](../../delivery/using/delivery-dashboard.md#delivery-summary), che mostra i dettagli dell&#39;invio e il numero di messaggi da inviare, elaborare e inviare con successo;
   * i [registri di consegna e la cronologia](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history), che mostrano quale target è stato escluso e perché;
   * i [registri di tracciamento](../../delivery/using/delivery-dashboard.md#tracking-logs), che mostrano informazioni di tracciamento come aperture e clic.

## Linee guida per il monitoraggio {#monitoring-guidelines}

Di seguito sono riportate alcune linee guida aggiuntive sul monitoraggio delle consegne:

* Controlla regolarmente la [velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput) per l&#39;intera piattaforma per verificare se è coerente con la configurazione originale.
* Verifica che [nuovi tentativi](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) siano configurati correttamente (30 minuti per il periodo di esecuzione dei nuovi tentativi e più di 20 tentativi) nei modelli di consegna.
* Verifica regolarmente che la cassetta postale [bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) sia accessibile e che l&#39;account non stia per scadere.
* Controlla ogni throughput di consegna, accessibile dal [dashboard di consegna](../../delivery/using/delivery-dashboard.md), per assicurarti che sia coerente con la validità del contenuto di consegna (ad esempio Le vendite flash devono essere consegnate in minuti, non in giorni).
* Quando utilizzi [waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verifica che ogni onda abbia tempo sufficiente per terminare prima che venga attivata la successiva.
* Verifica che il numero di errori e le nuove [quarantene](../../delivery/using/understanding-quarantine-management.md) siano coerenti con altre consegne.
* Consulta attentamente i [log di consegna](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) per controllare il tipo di errori evidenziati (elenco Bloccati, problemi DNS, regole anti-spam, ecc.).

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
