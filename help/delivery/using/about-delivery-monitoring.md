---
product: campaign
title: Introduzione al monitoraggio della consegna
description: Ulteriori informazioni sulle funzionalità di monitoraggio della distribuzione di Campaign Classic
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

---

# Introduzione al monitoraggio della consegna {#about-delivery-monitoring}

>[!IMPORTANT]
>
>In questa pagina sono documentate **le funzionalità di monitoraggio specifiche di Campaign Classic v7** per le distribuzioni ibride e on-premise.

## Funzioni di monitoraggio

### Monitoraggio della consegna {#monitoring-deliveries}

**Per le distribuzioni ibride/on-premise di Campaign Classic v7**, è necessario un monitoraggio aggiuntivo per le risorse del server e la configurazione dell&#39;MTA (Mail Transfer Agent).

#### Risolvere i problemi relativi alle consegne in sospeso {#pending-deliveries}

Cosa succede se le consegne non vengono inviate e il loro stato rimane **In sospeso**?

* Il processo di esecuzione è in attesa della disponibilità di alcune risorse. L’MTA potrebbe non essere stato avviato.
Verifica che i moduli mta@instance siano avviati sui server MTA e, se necessario, avvia il modulo MTA. [Ulteriori informazioni](../../production/using/administration.md).

* La consegna potrebbe utilizzare un’affinità non configurata nell’istanza di invio.
Suggerimento: controlla la configurazione della gestione del traffico (affinità IP). Per ulteriori informazioni, consulta Controllare il traffico SMTP in uscita.

>[!NOTE]
>
>Questi passaggi possono essere eseguiti solo da un utente esperto sulle installazioni on-premise.

### Monitoraggio della consegna {#deliverability-monitoring}

#### Installazione del pacchetto di consegna {#deliverability-package}

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. Per utilizzarlo, è necessario installare questo pacchetto. Al termine, riavvia il server affinché il pacchetto venga preso in considerazione.

* Per i client in hosting e ibridi, **Monitoraggio del recapito messaggi** è configurato nella tua istanza dal supporto tecnico e dai consulenti di Adobe. Per ulteriori informazioni, contatta il tuo account executive di Adobe.

* Per le installazioni locali, è necessario installare il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Per ulteriori informazioni, consulta [Installare i pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

#### Flusso di lavoro di consegna {#deliverability-workflow}

In Adobe Campaign Classic, **Monitoraggio del recapito messaggi** è gestito dal flusso di lavoro **[!UICONTROL Refresh for deliverability]**. È installato per impostazione predefinita su tutte le istanze e consente di inizializzare l’elenco delle regole di qualifica della posta non recapitata, l’elenco dei domini e l’elenco dei MX. Una volta installato il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]**, questo flusso di lavoro viene eseguito ogni notte per aggiornare regolarmente l&#39;elenco delle regole e consentire di gestire attivamente il recapito messaggi della piattaforma.

**Il pacchetto di recapito messaggi consente di accedere a:**

* Il report di rendering della [Posta in arrivo](inbox-rendering.md) che consente di visualizzare l&#39;anteprima dei messaggi sui principali client di posta elettronica per analizzare il contenuto e la reputazione.
* Panoramica sulla qualità dei messaggi (posta in arrivo, spam).

#### Strumenti di monitoraggio {#monitoring-tools}

**Per le installazioni on-premise**, è possibile utilizzare i seguenti strumenti di monitoraggio:

* Il report **[!UICONTROL Delivery throughput]** offre una panoramica della velocità effettiva dell&#39;intera piattaforma per un determinato periodo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).
* Ogni consegna genera un rapporto sulle statistiche di trasmissione per i diversi provider di servizi Internet (ISP). Mostra alcune metriche relative alla qualità dei dati e alla reputazione che possono influire sul recapito messaggi, tra cui i seguenti numeri:
   * **[!UICONTROL Hard bounces]** indica la qualità dei dati. Questo numero deve essere inferiore al 2%.
   * **[!UICONTROL Soft bounces]** indicare la reputazione. Questo numero non deve essere superiore al 10% per un dato ISP.

  Per ulteriori informazioni, consulta la sezione [Statistiche di consegna](../../reporting/using/global-reports.md#delivery-statistics).

#### Linee guida per il monitoraggio {#monitoring-guidelines}

**Per le installazioni on-premise**, ecco alcune linee guida aggiuntive sul monitoraggio del recapito messaggi:

* Controlla regolarmente la [velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput) per l&#39;intera piattaforma per verificare se è coerente con la configurazione originale.
* Verifica che [nuovi tentativi](delivery-failures-quarantine.md#retries-after-a-delivery-temporary-failure) siano configurati correttamente (30 minuti per il periodo di esecuzione dei nuovi tentativi e più di 20 tentativi) nei modelli di consegna.
* Verificare regolarmente che la cassetta postale [bounce](delivery-failures-quarantine.md#bounce-mail-management) sia accessibile e che l&#39;account non stia per scadere.
* Controlla ogni velocità effettiva di consegna, accessibile dal [dashboard di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}, per assicurarti che sia coerente con la validità del contenuto della consegna (ad esempio, le &quot;vendite flash&quot; devono essere consegnate in minuti, non in giorni).
* Quando utilizzate le onde, verificate che ogni onda abbia tempo sufficiente per terminare prima che venga attivata quella successiva.
* Verifica che il numero di errori e le nuove [quarantene](delivery-failures-quarantine.md) siano coerenti con le altre consegne.
* Consulta attentamente i [registri di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} per verificare il tipo di errori evidenziati (inserisce nell&#39;elenco Bloccati di, problemi DNS, regole anti-spam, ecc.).

### Risoluzione dei problemi {#delivery-troubleshooting}

È possibile eseguire azioni specifiche quando si verificano problemi con le consegne in **distribuzioni ibride/on-premise**:

* [Problemi di recapito messaggi](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemi relativi alla visualizzazione delle immagini](../../production/using/image-display-issues.md)
* [Problemi di prestazioni della consegna](delivery-performance-troubleshooting.md)
* [Problemi relativi ai file temporanei](../../production/using/temporary-files.md) - *solo clienti on-premise*

## Monitorare le consegne

Le seguenti risorse ti aiuteranno a monitorare e tenere traccia delle prestazioni di consegna in Campaign Classic v7:

### Accedere al dashboard di consegna

Scopri come accedere agli elenchi di consegna e utilizzare il dashboard di consegna per monitorare l’attività di invio:

* [Monitorare le consegne nell&#39;interfaccia utente di Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentazione di Campaign v8, applicabile sia a v7 che a v8)
* [Stati di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentazione di Campaign v8)
* [Avanzate: personalizza i registri di consegna](customize-delivery-logs.md) (solo v7 ibrida/on-premise - estensione schema)

### Tracciare le interazioni dei messaggi

Tieni traccia di aperture, clic e interazioni dei destinatari con le consegne:

* [Documentazione di tracciamento dei messaggi](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (documentazione di Campaign v8, applicabile sia a v7 che a v8)
* [Configurare i collegamenti tracciati](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (documentazione di Campaign v8)
* [Accedi ai registri di tracciamento](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (documentazione di Campaign v8)

### Ottimizzare le prestazioni di consegna

Best practice e risoluzione dei problemi relativi alle prestazioni di consegna:

* [Best practice per le consegne](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentazione di Campaign v8, applicabile sia a v7 che a v8)
* [Prestazioni della consegna e risoluzione dei problemi](delivery-performance-troubleshooting.md) (configurazioni specifiche per ibridi/on-premise v7)

### Informazioni su errori e quarantene

Gestire gli errori di consegna, le e-mail non recapitate e gli indirizzi in quarantena:

* [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentazione di Campaign v8: guida completa sia per v7 che per v8)
* [Gestione della quarantena](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentazione di Campaign v8: guida completa per v7 e v8)
* [Errori di consegna e configurazione della quarantena](delivery-failures-quarantine.md) (configurazioni specifiche per ibridi/on-premise v7)
