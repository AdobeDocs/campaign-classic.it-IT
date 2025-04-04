---
product: campaign
title: Flussi di lavoro tecnici
description: Ulteriori informazioni sui flussi di lavoro tecnici disponibili con i pacchetti Campaign Classic
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 1%

---

# Flussi di lavoro tecnici{#about-technical-workflows}



## Informazioni sui flussi di lavoro tecnici {#overview}

I flussi di lavoro descritti in questa sezione vengono installati con i diversi pacchetti incorporati di Adobe Campaign. Questi pacchetti e i relativi flussi di lavoro tecnici dipendono dal contratto di licenza. I pacchetti incorporati sono descritti in [questa sezione](../../installation/using/installing-campaign-standard-packages.md).

Per impostazione predefinita, i flussi di lavoro tecnici sono disponibili in una sottocartella del seguente nodo: **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

I flussi di lavoro tecnici possono essere avviati e modificati solo da operatori con diritti di amministrazione. Per ulteriori informazioni sulle autorizzazioni, consulta questa [sezione](../../platform/using/access-management-groups.md#default-groups).

>[!NOTE]
>
>I flussi di lavoro tecnici relativi al modulo Centro messaggi sono disponibili per impostazione predefinita nel nodo **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**.

Per ulteriori informazioni su come monitorare i flussi di lavoro tecnici, consulta la [sezione dedicata](monitoring-technical-workflows.md).

## Elenco dei flussi di lavoro tecnici {#list-technical-workflows}

| Flusso di lavoro tecnico | Pacchetto | Descrizione |
|------|--------|-----------|
| **Pulizia alias** (aliasCleansing) | Consegna | Questo flusso di lavoro standardizza i valori di enumerazione. Viene attivato ogni giorno alle 3 per impostazione predefinita. |
| **Fatturazione** (fatturazione) | Consegna | Questo flusso di lavoro invia il rapporto sull’attività del sistema all’operatore di &quot;fatturazione&quot; tramite e-mail. Viene attivato il 25 di ogni mese sull’istanza Marketing. |
| **Calcolo delle statistiche di Twitter** (statsTwitter) | Social network (Social marketing) - Solo Campaign v7 | Questo flusso di lavoro calcola le statistiche relative ai retweet e alle visite su X (precedentemente noto come Twitter). |
| **Processi campagna** (operationMgt) | Campagne di marketing (Campaign) | Questo flusso di lavoro gestisce i processi per le campagne di marketing (avvio, targeting, estrazione file, ecc.). Crea anche flussi di lavoro relativi a campagne ricorrenti e periodiche. |
| **Raccogli dati per il servizio HeatMap** (collectDataHeatMapService) | Installato per impostazione predefinita | Questo flusso di lavoro recupera i dati richiesti dal servizio HeatMap. |
| **Raccogli richieste di accesso a dati personali** (collectPrivacyRequests) | Regolamento sulla protezione dei dati personali | Questo flusso di lavoro genera i dati del destinatario memorizzati in Adobe Campaign e li rende disponibili per il download nella schermata della richiesta di accesso a dati personali. |
| **Calcolo costi** (budgetMgt) | Campagne di marketing (Campaign) | Questo flusso di lavoro avvia il calcolo delle righe spese e costi per budget, piani, programmi, campagne, consegne e attività. |
| **Pulizia database** (pulizia) | Consegna | Questo flusso di lavoro è il flusso di lavoro di manutenzione del database: esegue calcoli diversi dalle statistiche e dai processi ed elimina i dati obsoleti dal database in base alla configurazione definita nella procedura guidata di distribuzione. Viene attivato ogni giorno alle 4 per impostazione predefinita. Per ulteriori informazioni, consulta [questa pagina](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic). |
| **Elimina utenti LINE bloccati** (deleteBlockedLineUsersV2) | Canale LINE | Questo flusso di lavoro assicura che i dati degli utenti LINE V2 vengano eliminati dopo che hanno bloccato l’account ufficiale LINE per 180 giorni. |
| **Elimina dati richieste privacy** (deletePrivacyRequestsData) | Regolamento sulla protezione dei dati personali | Questo flusso di lavoro elimina i dati del destinatario memorizzati in Adobe Campaign. |
| **Indicatori di consegna** (deliveryIndicators) | Piattaforma di mid-sourcing | Questo flusso di lavoro aggiorna gli indicatori di tracciamento della consegna per una consegna. Questo flusso di lavoro viene attivato ogni ora per impostazione predefinita. |
| **Processi forum di discussione** (newsgroupMgt) | Risorse di marketing (MRM) | Questo flusso di lavoro gestisce la consegna delle notifiche dai forum di discussione. Viene attivato quando si riceve un segnale di approvazione |
| **Processi di marketing distribuito** (centralLocalMgt) | Marketing centrale e locale (marketing distribuito) | Questo flusso di lavoro avvia l’elaborazione correlata all’utilizzo del modulo di marketing distribuito. Avvia la creazione di campagne locali e gestisce le notifiche relative agli ordini e alla disponibilità dei pacchetti delle campagne. |
| **Eliminazione eventi** (webAnalyticsPurgeWebEvents) | Connettori di analisi web | Questo flusso di lavoro ti consente di eliminare ogni evento dal campo del database in base al periodo configurato nel campo Durata. |
| **Esporta tipi di pubblico in Adobe Experience Cloud** (exportSharedAudience) | Integrazione con Adobe Experience Cloud | Questo flusso di lavoro esporta i tipi di pubblico come tipi di pubblico/segmenti condivisi. Questi tipi di pubblico possono essere utilizzati nelle diverse soluzioni Adobe Experience Cloud che utilizzi. |
| **Previsione** (previsione) | Consegna | Questo flusso di lavoro analizza le consegne salvate nel calendario provvisorio (crea registri provvisori). Per impostazione predefinita viene attivato ogni giorno all’1. |
| **Calcolo aggregato completo (cubo propositionrcp)** (agg_nmspropositionrcp_full) | Motore di offerta (interazione) | Questo flusso di lavoro aggiorna l’aggregato completo per il cubo della proposta di offerta. Per impostazione predefinita viene attivato ogni giorno alle 6. Questo aggregato acquisisce le seguenti dimensioni: Canale, Consegna, Offerta di marketing e Data. Il cubo della proposta di offerta viene quindi utilizzato per generare rapporti basati sulle offerte. Ulteriori informazioni sui cubi sono disponibili in [questa sezione](../../reporting/using/ac-cubes.md). |
| **Identificazione dei contatti convertiti** (webAnalyticsFindConverted) | Connettori di analisi web | Questo flusso di lavoro indicizza i visitatori del sito che hanno completato l’acquisto dopo una campagna di remarketing. I dati recuperati da questo flusso di lavoro sono accessibili nel rapporto sull’efficienza del remarketing (consulta questa pagina). |
| **Importa tipi di pubblico da Adobe Experience Cloud** (importSharedAudience) | Integrazione con Adobe Experience Cloud | Questo flusso di lavoro ti consente di importare tipi di pubblico/segmenti da diverse soluzioni Adobe Experience Cloud in Adobe Campaign. |
| **Processi su consegne nelle campagne** (deliveryMgt) | Campagne di marketing (Campaign) | Questo flusso di lavoro attiva le consegne approvate e avvia la post-elaborazione del provider di servizi per una consegna esterna. Invia inoltre notifiche di approvazione e promemoria. |
| **Processi nei provider di servizi** (providerMgt) | Campagne di marketing (Campaign) | Questo flusso di lavoro avvia l’elaborazione del provider (e-mail al router e post-elaborazione) dopo l’approvazione delle consegne. |
| **Aggiornamento token di accesso LINE V2** (updateLineV2AccessToken) | Canale LINE - Solo Campaign v7 | Questo flusso di lavoro aggiorna il token di accesso alla LINE V2. |
| **Migrazione da MID a LineUserID** (MIDToUserIDMigration) | Canale LINE | Questo flusso di lavoro genera l’ID degli utenti LINE V2 per la migrazione da LINE V1 a LINE V2. |
| **Notifiche delle risorse di marketing** (assetMgt) | Risorse di marketing (MRM) | Questo flusso di lavoro gestisce le notifiche collegate all’approvazione e alla pubblicazione delle risorse di marketing. |
| **Centro messaggi &lt;nome_account_esterno>** (mcSynch_&lt;nome_account_esterno>) | Controllo dei messaggi transazionali (Centro messaggi - Controllo) | Questo flusso di lavoro: <ul><li>recupera l’elenco degli eventi elaborati dalle operazioni.</li><li>si sincronizza con la tabella NmsBroadLogMsg per recuperare le qualifiche dei messaggi di consegna.</li><li>recupera i registri di consegna degli eventi non appena la sincronizzazione con la tabella NmsBroadLogMsg è stata completata.</li><li>si sincronizza con la tabella NmsTrackingUrl per recuperare il tracciamento per gli URL di consegna.</li><li>recupera gli URL di tracciamento degli eventi non appena la sincronizzazione con la tabella NmsTrackingUrl è stata completata.</li><li>consente di recuperare tutti gli indirizzi e-mail messi in quarantena ogni tre ore dopo l’invio di una consegna.</li></ul> |
| **Calcolo aggregato completo MessageCenter** (agg_messageCenter_full) | Controllo dei messaggi transazionali (Centro messaggi - Controllo) | Questo flusso di lavoro aggiorna l’aggregato completo per il cubo del centro messaggi. Viene attivato ogni giorno alle 3 per impostazione predefinita. Questo aggregato acquisisce le seguenti dimensioni: Canale, Data, Stato e Tipo evento. Il cubo Centro messaggi viene quindi utilizzato per generare rapporti basati sugli eventi. Ulteriori informazioni sui cubi sono disponibili in [questa sezione](../../reporting/using/ac-cubes.md) |
| **Mid-sourcing (contatori di consegna)** (defaultMidSourcingDlv) | Trasferisci a mid-sourcing | Questo flusso di lavoro raccoglie informazioni sul conteggio delle consegne sul server di mid-sourcing. Le informazioni sul conteggio includono indicatori generali di consegna come il numero di consegne inviate, ecc. Le informazioni di tracciamento come le aperture non sono incluse. Viene attivato ogni dieci minuti per impostazione predefinita. |
| **Mid-sourcing (registri di consegna)** (defaultMidSourcingLog) | Trasferisci a mid-sourcing | Questo flusso di lavoro raccoglie i registri di consegna sul server di mid-sourcing. Viene attivato ogni ora per impostazione predefinita. |
| **Gestione rinuncia NMAC** (mobileAppOptOutMgt) | Canale app mobile | Questo flusso di lavoro aggiorna gli annullamenti degli abbonamenti alle notifiche sui dispositivi mobili. Viene attivato ogni 6 ore tra l’1 e mezzanotte. Per ulteriori dettagli, fare riferimento a [questa sezione](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines). |
| **Notifica offerta** (offerMgt) | Consegna | Questo flusso di lavoro distribuisce le offerte approvate nell’ambiente online, nonché in ogni categoria contenuta nel catalogo delle offerte. |
| **Pulizia flussi di lavoro sospesi** (cleanupPausedWorkflows) | Consegna | Questo flusso di lavoro analizza i flussi di lavoro in pausa la cui gravità è impostata su Normal e attiva avvisi e notifiche se sono stati messi in pausa troppo a lungo. Dopo un mese, i flussi di lavoro tecnici in pausa vengono interrotti incondizionatamente. Per impostazione predefinita viene attivato ogni lunedì alle 5. Per ulteriori informazioni, consultare [Gestione dei flussi di lavoro in pausa](monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Pulizia richieste privacy** (cleanupPrivacyRequests) | Regolamento sulla protezione dei dati personali | Questo flusso di lavoro cancella i file di richiesta di accesso che sono più vecchi di 90 giorni. |
| **Elaborazione eventi batch** (batchEventsProcessing) | Esecuzione dei messaggi transazionali (Centro messaggi - Esecuzione) | Questo flusso di lavoro ti consente di mettere in coda gli eventi batch prima di associarli a un modello di messaggio. |
| **Elaborazione eventi in tempo reale** (rtEventsProcessing) | Esecuzione dei messaggi transazionali (Centro messaggi - Esecuzione) | Questo flusso di lavoro consente di mettere in coda eventi in tempo reale prima di associarli a un modello di messaggio. |
| **Sincronizzazione proposta** (propositionSynch) | Controllo del motore di offerta con istanza di esecuzione | Questo flusso di lavoro sincronizza le proposte tra l’istanza di marketing e l’istanza di esecuzione utilizzate per le interazioni. |
| **Ripristino di eventi Web** (webAnalyticsGetWebEvents) | Connettori di analisi web | Ogni ora, questo flusso di lavoro scarica segmenti sul comportamento degli utenti Internet su un determinato sito, li inserisce nel database di Adobe Campaign e avvia il flusso di lavoro di remarketing. |
| **Reporting aggregates** (reportingAggregates) | Consegna | Questo flusso di lavoro aggiorna gli aggregati utilizzati nei rapporti. Viene attivato ogni giorno alle 2 per impostazione predefinita. |
| **Invio di indicatori e attributi della campagna** (webAnalyticsSendMetrics) | Connettori di analisi web | Questo flusso di lavoro consente di inviare gli indicatori della campagna e-mail da Adobe Campaign a Adobe Experience Cloud Suite tramite il connettore Adobe® Analytics. Gli indicatori interessati sono i seguenti: Inviato (iSent), conteggio totale di aperture (iTotalRecipientOpen), numero totale di destinatari che hanno fatto clic (iTotalRecipientClick), errori (iError), rinuncia (opt-out) (iOptOut). |
| **Magazzino: Ordini e avvisi** (stockMgt) | Campagne di marketing (Campaign) | Questo flusso di lavoro avvia il calcolo delle scorte nelle linee dell&#39;ordine e gestisce le soglie degli avvisi di avvertenza. |
| **Sincronizzazione dei fan di Facebook** (syncFacebookFans) | Social network (Social marketing) - Solo Campaign v7 | Questo flusso di lavoro importa i fan di Facebook in Adobe Campaign ogni giorno alle 7. |
| **Sincronizzazione pagine Facebook** (syncFacebook) | Social network (Social marketing) - Solo Campaign v7 | Questo flusso di lavoro sincronizza le pagine Facebook con Adobe Campaign ogni giorno alle 7. |
| **Sincronizzazione delle pagine Twitter** (syncTwitter) | Social network (Social marketing) - Solo Campaign v7 | Questo flusso di lavoro importa X follower in Adobe Campaign ogni giorno alle 7. |
| **Notifica attività** (taskMgt) | Risorse di marketing (MRM) - Solo Campaign v7 | Questo flusso di lavoro ti consente di inviare messaggi di notifica relativi alle attività nelle campagne di marketing. |
| **Tracciamento** (tracciamento) | Consegna | Questo flusso di lavoro esegue il ripristino e il consolidamento delle informazioni di tracciamento. Assicura inoltre il ricalcolo delle statistiche di tracciamento e consegna, in particolare quelle utilizzate dai flussi di lavoro di archiviazione del Centro messaggi. Per impostazione predefinita viene attivato una volta all’ora. |
| **Aggiorna stato evento** (updateEventsStatus) | Esecuzione dei messaggi transazionali (Centro messaggi - Esecuzione) | Questo flusso di lavoro ti consente di assegnare uno stato a un evento. Gli stati degli eventi sono i seguenti:<ul><li>In sospeso: l’evento è in coda. Non è ancora stato associato alcun modello di messaggio.</li><li>In attesa di consegna: l’evento è in coda, gli è stato associato un modello di messaggio ed è attualmente in fase di elaborazione da parte della consegna.</li><li>Inviato: questo stato viene copiato dai registri di consegna. Significa che la consegna è stata inviata.</li><li>Ignored by the delivery: questo stato viene copiato dai log di consegna. Significa che la consegna è stata ignorata.</li><li>Errore di consegna: questo stato viene copiato dai registri di consegna. Significa che la consegna non è riuscita.</li><li>Evento non coperto: l’evento non è stato associato a un modello di messaggio. L’evento non verrà rielaborato.</li></ul> |
| **Aggiorna per il recapito messaggi** (deliverabilityUpdate) | Consegna | Questo flusso di lavoro viene eseguito ogni notte e gestisce le regole di qualifica delle e-mail non recapitate, nonché l’elenco di domini e MX. Questo richiede che la porta HTTPS sia aperta sulla piattaforma. |