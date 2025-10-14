---
product: campaign
title: Monitorare il recapito messaggi in Adobe Campaign
description: Scopri gli strumenti e le linee guida per il monitoraggio del recapito messaggi in Adobe Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 1%

---

# Monitorare il recapito messaggi{#monitoring-deliverability}

Di seguito trovi i dettagli sui diversi strumenti di monitoraggio forniti da Adobe Campaign, nonché alcune linee guida aggiuntive sull’utilizzo delle funzioni offerte da Adobe Campaign per monitorare il recapito messaggi della piattaforma.

## Informazioni sul monitoraggio del recapito messaggi {#about-deliverability-monitoring}

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. Per utilizzarlo, è necessario installare questo pacchetto. Al termine, riavvia il server affinché il pacchetto venga preso in considerazione.
* Per i client in hosting e ibridi, **Monitoraggio del recapito messaggi** è configurato nella tua istanza dal supporto tecnico e dai consulenti di Adobe. Per ulteriori informazioni, contatta il tuo account executive di Adobe.

* Per le installazioni locali, è necessario installare il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Per ulteriori informazioni, consulta [Installare i pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic, **Monitoraggio del recapito messaggi** è gestito dal flusso di lavoro **[!UICONTROL Refresh for deliverability]**. È installato per impostazione predefinita su tutte le istanze e consente di inizializzare l’elenco delle regole di qualifica della posta non recapitata, l’elenco dei domini e l’elenco dei MX. Una volta installato il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]**, questo flusso di lavoro viene eseguito ogni notte per aggiornare regolarmente l&#39;elenco delle regole e consentire di gestire attivamente il recapito messaggi della piattaforma.

Il pacchetto di recapito messaggi consente di accedere a:

* Il report di rendering della [Posta in arrivo](inbox-rendering.md) che consente di visualizzare l&#39;anteprima dei messaggi sui principali client di posta elettronica per analizzare il contenuto e la reputazione.
* Panoramica sulla qualità dei messaggi (posta in arrivo, spam).

## Strumenti di monitoraggio {#monitoring-tools}

È inoltre possibile utilizzare i seguenti strumenti:

* Il report **[!UICONTROL Delivery throughput]** offre una panoramica della velocità effettiva dell&#39;intera piattaforma per un determinato periodo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).
* Ogni consegna genera un rapporto sulle statistiche di trasmissione per i diversi provider di servizi Internet (ISP). Mostra alcune metriche relative alla qualità dei dati e alla reputazione che possono influire sul recapito messaggi, tra cui i seguenti numeri:
   * **[!UICONTROL Hard bounces]** indica la qualità dei dati. Questo numero deve essere inferiore al 2%.
   * **[!UICONTROL Soft bounces]** indicare la reputazione. Questo numero non deve essere superiore al 10% per un dato ISP.

  Per ulteriori informazioni, consulta la sezione [Statistiche di consegna](../../reporting/using/global-reports.md#delivery-statistics).
* Più in generale, il [dashboard di consegna](about-delivery-monitoring.md) ti consente di accedere a:
   * il [riepilogo di consegna](delivery-dashboard.md#delivery-summary), che mostra i dettagli dell&#39;invio e il numero di messaggi da inviare, elaborare e inviare con successo;
   * i [registri di consegna e cronologia](delivery-dashboard.md#delivery-logs-and-history), che mostrano quale destinazione è stata esclusa e perché;
   * i [registri di tracciamento](delivery-dashboard.md#tracking-logs), che mostrano informazioni di tracciamento come aperture e clic.

## Linee guida per il monitoraggio {#monitoring-guidelines}

Di seguito sono riportate alcune linee guida aggiuntive sul monitoraggio della consegna dei messaggi:

* Controlla regolarmente la [velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput) per l&#39;intera piattaforma per verificare se è coerente con la configurazione originale.
* Verifica che [nuovi tentativi](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) siano configurati correttamente (30 minuti per il periodo di esecuzione dei nuovi tentativi e più di 20 tentativi) nei modelli di consegna.
* Verificare regolarmente che la cassetta postale [bounce](understanding-delivery-failures.md#bounce-mail-management) sia accessibile e che l&#39;account non stia per scadere.
* Controlla ogni velocità effettiva di consegna, accessibile dal [dashboard di consegna](delivery-dashboard.md), per assicurarti che sia coerente con la validità del contenuto della consegna (ad esempio, le &quot;vendite flash&quot; devono essere consegnate in minuti, non in giorni).
* Quando utilizzate le onde, verificate che ogni onda abbia tempo sufficiente per terminare prima che venga attivata quella successiva. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html?lang=it#sending-using-multiple-waves){target="_blank"}.
* Verifica che il numero di errori e le nuove [quarantene](understanding-quarantine-management.md) siano coerenti con le altre consegne.
* Consulta attentamente i [registri di consegna](delivery-dashboard.md#delivery-logs-and-history) per verificare il tipo di errori evidenziati (inserisce nell&#39;elenco Bloccati di, problemi DNS, regole anti-spam, ecc.).
