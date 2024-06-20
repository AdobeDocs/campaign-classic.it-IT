---
product: campaign
title: Aggiornamenti alla documentazione di Adobe Campaign Classic v7
description: In questa pagina sono elencate tutte le nuove funzioni e gli aggiornamenti presenti nella documentazione di Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: 98859f6452b5f1008a19a48b9b77edd9acf49261
workflow-type: tm+mt
source-wordcount: '3746'
ht-degree: 99%

---

# Aggiornamenti alla documentazione{#documentation-updates}

In questa pagina sono elencate tutte le nuove funzioni e gli aggiornamenti alla documentazione in base al mese e alla versione di Campaign.

Per gli aggiornamenti relativi alla versione, consulta le [Note sulla versione di Adobe Campaign Classic](../../rn/using/latest-release.md).

## 2024

### Giugno 2024 {#june-2024}

È stata aggiunta una nota per specificare come cancellare le variabili di istanza al riavvio dei flussi di lavoro. [Ulteriori informazioni](../../workflow/using/starting-a-workflow.md)

### Aprile 2024 {#apr-2024}

È stata aggiunta una nota di avviso per informare sulla creazione di utenti con Adobe Identity Management System (IMS). [Ulteriori informazioni](../../platform/using/access-management.md)

Sono state aggiunte opzioni mancanti per l’attività del flusso di lavoro Download web. [Ulteriori informazioni](../../workflow/using/web-download.md)

È stata aggiunta una nota di avviso alle attività **Cambia dimensione** e **Cambia origine dati** relative al rispettivo utilizzo in un flusso di lavoro. [Ulteriori informazioni](../../workflow/using/change-data-source.md)

### Marzo 2024 {#mar-2024}

La sezione sulla configurazione dell’app mobile è stata aggiornata per la connessione basata su token a APN per iOS. [Ulteriori informazioni](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)

### Gennaio 2024 {#jan-2024}

Sono state aggiunte informazioni sulla definizione del campo postalAddress predefinito per Direct Mail e sul motivo per cui è importante assicurarsi che gli indirizzi siano completi. [Ulteriori informazioni](../../delivery/using/about-direct-mail-channel.md)

È stata aggiunta una nuova pagina su come configurare il canale SMS in Campaign in un’infrastruttura mid-sourcing. [Ulteriori informazioni](../../delivery/using/sms-set-up-mid.md)

## 2023

### Dicembre 2023 {#dec-2023}

Il codice JWT (JSON Web Tokens) è attualmente in fase di ammortamento e viene sostituito con OAuth. La transizione viene eseguita progressivamente nelle prossime versioni di Campaign e la documentazione verrà aggiornata per riflettere tali aggiornamenti.

È stata aggiunta la configurazione dell’account esterno FDA per Amazon Redshift. [Ulteriori informazioni](../../installation/using/configure-fda-redshift.md)

### Agosto 2023 {#aug-2023}

È stata aggiunta una limitazione per specificare che non è possibile utilizzare Adobe Campaign per decomprimere file compressi di dimensioni superiori a 4 Gb. [Ulteriori informazioni](../../platform/using/unzip-decrypt.md)

### Aprile 2023 {#apr-2023}

È stata aggiunta una nota tecnica su come abilitare gli ambienti on-premise/ibridi di Microsoft Edge basato su Chromium. [Ulteriori informazioni](../../technotes/using/edge-chromium.md)

### Marzo 2023 {#mar-2023}

È stata aggiornata la sezione Note sulla versione 7.3.3 con miglioramenti e patch. [Ulteriori informazioni](latest-release.md)


+++ 2022


## Novembre 2022 {#nov-2022}

È stata aggiornata la sezione Note sulla versione 7.3.2 con miglioramenti e patch. [Maggiori informazioni](latest-release.md)

Matrice di compatibilità aggiornata con il supporto Teradata 17. [Maggiori informazioni](compatibility-matrix.md)

La sezione Gestione delle risorse e dei file è stata aggiornata con ulteriori informazioni sull’attributo **uploadWhiteList**. [Maggiori informazioni](../../installation/using/file-res-management.md)

La documentazione sulle aree di protezione è stata aggiornata con ulteriori informazioni sull’attributo **allowDebug**. [Maggiori informazioni](../../installation/using/security-zones.md#recommendations)

La guida alla migrazione è stata aggiornata. I riferimenti alle versioni non supportate di Adobe Campaign sono stati rimossi. [Maggiori informazioni](../../migration/using/about-migration.md)


## Luglio 2022 {#july-2022}

<!--Transition to the new deliverability server is detailed in a new technote. [Read more](../../technotes/using/deliverability-server.md)-->

**Aggiornamenti alla documentazione in arrivo con la versione 7.3.1**

Matrice di compatibilità aggiornata. [Maggiori informazioni](compatibility-matrix.md)

È stata aggiornata la sezione Note sulla versione. [Maggiori informazioni](rn-overview.md)

Notifiche urgenti con iOS 15. [Ulteriori informazioni](../../delivery/using/create-notifications-ios.md)


## Marzo 2022 {#mar-2022}

È stata aggiunta una descrizione dettagliata per l’opzione **[!UICONTROL Test SMTP delivery]**. [Maggiori informazioni](../../delivery/using/steps-sending-the-delivery.md#delivery-additiona-parameters)

La pagina Introduzione agli aggiornamenti è stata aggiornata per chiarire le linee guida per l’aggiornamento della console Campaign. [Maggiori informazioni](../../rn/using/rn-overview.md)

È ora disponibile la nuova build di Campaign v7.2.2. [Maggiori informazioni](../../rn/using/latest-release.md)

<!--Added troubleshooting information related to the ACS connector. [Read more](../../integrations/using/troubleshooting-the-acs-connector.md)-->

Le versioni legacy di PostgreSQL che hanno raggiunto la fine del ciclo di vita sono state aggiunte alla pagina [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md#dbe-eol).

## Febbraio 2022 {#february-2022}

La sezione attività **Trasferimento file** è stata aggiornata con un promemoria per monitorare manualmente le dimensioni del contenuto archiviato nella directory SFTP nel caso in cui l’opzione **Elimina i file di origine dopo il trasferimento** non sia selezionata. [Maggiori informazioni](../../workflow/using/file-transfer.md#properties)

La sezione Quarantena ed Elenco bloccati è stata resa più chiara. [Maggiori informazioni](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

Sono state aggiornate le sezioni su come mettere in quarantena un indirizzo e come rimuovere gli indirizzi dall’elenco di quarantena. [Maggiori informazioni](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

È stata aggiunta una best practice per flussi di lavoro che consiglia di non eseguire più richieste di arresto sullo stesso flusso di lavoro. [Maggiori informazioni](../../workflow/using/workflow-best-practices.md)

Sono state aggiunte informazioni su come interrompere l’esecuzione di una consegna ricorrente all’interno di una campagna. [Maggiori informazioni](../../workflow/using/recurring-delivery.md)

## Gennaio 2022 {#january-2022}

**Aggiornamenti alla documentazione in arrivo con la versione 7.2.1**

Matrice di compatibilità aggiornata. [Maggiori informazioni](compatibility-matrix.md)

È stata aggiornata la sezione Note sulla versione. [Maggiori informazioni](rn-overview.md)

È stata aggiornata la configurazione dell’account esterno FDA per Snowflake. [Maggiori informazioni](../../installation/using/configure-fda-snowflake.md)

È stata aggiornata la configurazione dell’account esterno FDA per Azure Synapse Analytics. [Maggiori informazioni](../../installation/using/configure-fda-synapse.md#azure-external)

È stato aggiornato il connettore FDA BigQuery Google. [Maggiori informazioni](../../installation/using/configure-fda-google-big-query.md)

Dopo essere state dichiarate obsolete, le attività di azione Microsoft CRM, Salesforce, Oracle CRM On Demand sono state rimosse dalla documentazione.

È stata aggiunta la nuova opzione **Interrompi in caso di errore** alla sezione Gestione errori del flusso di lavoro. [Maggiori informazioni](../../workflow/using/advanced-parameters.md#in-case-of-errors)

È stata aggiunta l’opzione di aggiornamento batch nell’attività del connettore di gestione delle relazioni con i clienti. [Maggiori informazioni](../../workflow/using/crm-connector.md)

+++

+++ 2021

## Dicembre 2021{#dec-2021}

Le note sulla versione di Campaign Classic v7 sono state riorganizzate per semplificare la navigazione. [Maggiori informazioni](rn-overview.md)

La documentazione sull’edizione dei moduli in Campaign è stata aggiornata e migliorata. [Maggiori informazioni](../../configuration/using/editing-forms.md)

CentOs 8 ha raggiunto la fine del ciclo di vita ed è ora obsoleto con Adobe Campaign Classic. [Maggiori informazioni](deprecated-features.md)

## Novembre 2021{#nov-2021}

È stata aggiunta una limitazione relativa agli SMS in arrivo (MO). [Maggiori informazioni](../../delivery/using/sms-protocol.md#multipart)

Aggiornamento dei dettagli dei registri del processo di migrazione per la distribuzione del connettore CRM. [Maggiori informazioni](../../migration/using/testing-the-migration.md#verification-process)

Sono stati aggiunti requisiti sulle autorizzazioni IMS per implementare l’integrazione Adobe Campaign-Adobe Analytics. [Maggiori informazioni](../../integrations/using/adobe-analytics-provisioning.md)

È stata aggiornata la data di fine del ciclo di vita di Connettore dati Adobe Analytics dal 1° marzo 2022 al 17 agosto 2022. [Maggiori informazioni](deprecated-features.md)

È stata aggiunta una sezione su come utilizzare JavaScript per calcolare i valori, scambiare dati ed eseguire operazioni specifiche utilizzando chiamate SOAP.[Maggiori informazioni](../../workflow/using/javascript-scripts-and-templates.md)

Sono stati aggiunti esempi di implementazione di codici JavaScript nei flussi di lavoro. [Maggiori informazioni](../../workflow/using/javascript-in-workflows.md)


## Ottobre 2021{#oct-2021}

Le note tecniche esistenti sono state raggruppate nella nuova sezione **Note tecniche**.

La pagina **Consigli sui requisiti hardware in base alle dimensioni** è stata aggiornata e aggiunta alla sezione **Note tecniche**. [Leggi tutto](../../technotes/using/hardware-sizing.md)

## Settembre 2021{#sept-2021}

**Aggiornamenti alla documentazione in arrivo con la versione 21.1.4**

Il tipo di grafico **Misuratore** è stato rimosso.

Le schermate e i parametri delle applicazioni web e dei rapporti sono stati aggiornati in seguito alla rimozione di Adobe Flash.

La descrizione del [flusso di lavoro tecnico di fatturazione](../../production/using/monitoring-processes.md#billing-report) è stata aggiornata con un nuovo guardrail.

## Agosto 2021{#aug-2021}

È stata aggiunta una nuova attività del flusso di lavoro: Cambia origine dati - [Ulteriori informazioni](../../workflow/using/change-data-source.md)

I badge di applicabilità sono stati aggiunti alle pagine della documentazione: **Applicabile solo alla versione v7** per le funzionalità di Campaign Classic v7 e **Applicabile alle versioni v7 e v8** per le funzionalità comuni.

È stata aggiunta una nota sull’integrazione tra Campaign e AEM Assets, dismessa a partire da Adobe Experience Manager 6.4. [Ulteriori informazioni](../../integrations/using/configuring-access-to-assets.md)


## Luglio 2021 {#july-2021}

[La versione 21.1.3 di Campaign](../../rn/using/latest-release.md#release-21-1-3-build-9330) è stata spostata in General Availability (GA).


## Giugno 2021 {#june-2021}

La sezione **Messaggistica transazionale** è stata riorganizzata e chiarita con una nuova sezione Introduzione, che include uno [schema avanzato](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle) per una migliore comprensione del processo. [Ulteriori informazioni](../../message-center/using/about-transactional-messaging.md)

**Aggiornamenti alla documentazione in arrivo con la versione 21.1.3**

Integrazione con il Journey Orchestration Adobe - [Ulteriori informazioni](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=it). Un caso d’uso dettagliato è presentato in [questa pagina](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=it)

Miglioramenti al canale LINE - [Ulteriori informazioni](../../delivery/using/line-channel.md)

Nuovo connettore FDA Vertica Analytics - [Ulteriori informazioni](../../installation/using/configure-fda-vertica.md)

Nuovo connettore FDA BigQuery Google: [ulteriori informazioni](../../installation/using/configure-fda-google-big-query.md)

La descrizione del flusso di lavoro tecnico “Fatturazione (billing)” include ora le attività originariamente eseguite dal “Numero di profili di fatturazione attivi (billingActiveContactCount)”. [Ulteriori informazioni](../../workflow/using/about-technical-workflows.md)

## Maggio 2021 {#may-2021}

La documentazione del rapporto Workflow Heatmap è stata aggiornata e migliorata. [Leggi tutto](../../workflow/using/heatmap.md)

I requisiti della console client di Campaign sono stati aggiornati nella matrice di compatibilità. [Leggi tutto](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

La procedura di installazione della console client di Campaign è stata migliorata e chiarita. [Leggi tutto](../../installation/using/installing-the-client-console.md)

È stata creata una nuova nota tecnica sul problema relativo alla firma degli URL tracciati. [Leggi tutto](../../technotes/using/tracked-urls.md)

## Aprile 2021 {#april-2021}

È stata aggiunta una nuova sezione su come lavorare con le origini e le destinazioni di Adobe Experience Platform per condividere i dati tra Campaign Classic e Adobe Real-time Customer Data Platform (RTCDP). [Leggi tutto](../../integrations/using/get-started-sources-destinations.md)

È stata creata una nuova nota tecnica sull’aggiornamento della qualifica dei messaggi non recapitati dopo un’interruzione dell’ISP. [Leggi tutto](../../delivery/using/update-bounce-qualification.md)

## Marzo 2021 {#march-2021}

La [sezione Introduzione agli SMS](../../delivery/using/sms-channel.md) è stata riorganizzata e migliorata. Ora puoi imparare a [configurare il canale SMS](../../delivery/using/sms-set-up.md), [creare un SMS](../../delivery/using/sms-create.md), [inviare e tracciare gli SMS](../../delivery/using/sms-send.md) nelle sezioni dedicate.

La pagina “Opzioni di aiuto e supporto” per Campaign Standard è stata integrata nella documentazione di base. [Leggi tutto](../../support.md)

È stata aggiunta una nuova sezione con best practice e controlli da eseguire in materia di sicurezza e privacy. [Leggi tutto](../../installation/using/get-started-security-privacy.md)

Il [capitolo sulla gestione delle autorizzazioni](../../platform/using/access-management.md) è stato migliorato e suddiviso in sezioni, inclusi dettagli su [operatori](../../platform/using/access-management-operators.md), [gruppi di operatori](../../platform/using/access-management-groups.md), [diritti denominati](../../platform/using/access-management-named-rights.md) e [gestione delle cartelle](../../platform/using/access-management-folders.md).

Scopri come creare e gestire le campagne attraverso queste nuove pagine:
* [Creare e configurare modelli di campagna](../../campaign/using/marketing-campaign-templates.md)
* [Consegne di campagne di marketing](../../campaign/using/marketing-campaign-deliveries.md)
* [Selezionare il pubblico delle campagne](../../campaign/using/marketing-campaign-target.md)
* [Gestire i documenti associati](../../campaign/using/marketing-campaign-assets.md)
* [Impostare e gestire il processo di approvazione](../../campaign/using/marketing-campaign-approval.md)

Nella sezione dell’attività **[!UICONTROL Advanced JavaScript]** sono state aggiunte informazioni su come utilizzare il metodo task.setCompleted() per terminare l’attività ed evitare richiami futuri. [Leggi tutto](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

La sezione [Recapito messaggi](../../delivery/using/about-deliverability.md) è stata aggiornata e ora include i collegamenti alla nuova [guida Adobe alle best practice per il recapito messaggi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it). Tutte le informazioni generiche relative al recapito dei messaggi valide per varie soluzioni Adobe sono state spostate nell’[Appendice alla Guida alle best practice](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html?lang=it#additional-resources).

## Febbraio 2021 {#release-21.1}

**Aggiornamenti alla documentazione in arrivo con la versione 21.1**

La documentazione della nuova funzionalità **Email Feedback Service** (versione beta privata) è disponibile [qui](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service).

La sezione sul **file di configurazione del server** è stata aggiornata con i parametri di configurazione necessari per la connessione di Campaign a un altro servizio utilizzando IMS. [Leggi tutto](../../installation/using/the-server-configuration-file.md#ims)

Nell’elenco degli stati di consegna, la descrizione dello stato **Taken into account by the service provider** (Preso in considerazione dal fornitore di servizi) è stata aggiornata: questo stato viene ora utilizzato anche per le consegne e-mail inviate tramite il servizio di feedback e-mail, [Email Feedback Service](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service). [Leggi tutto](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

Sono ora documentate le scelte rapide da tastiera disponibili nella nuova schermata di accesso di Adobe Campaign. [Leggi tutto](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**Altri aggiornamenti**

È stata aggiunta una nuova sezione con informazioni dettagliate su come eseguire test A/B utilizzando i flussi di lavoro. [Leggi tutto](../../delivery/using/get-started-a-b-testing.md)

La sezione sull’MTA avanzato di Adobe Campaign è stata spostata [qui](../../delivery/using/sending-with-enhanced-mta.md).

È stata aggiunta una nuova pagina che fornisce una panoramica delle funzionalità di tracciamento di [!DNL Campaign Classic]. [Leggi tutto](../../delivery/using/about-message-tracking.md)

È stata aggiunta una sezione per la risoluzione dei problemi comuni relativi al tracciamento. [Leggi tutto](../../delivery/using/tracking-troubleshooting.md)

La sezione **Invio di un messaggio e-mail** è stata riorganizzata e chiarita con nuove sottosezioni. [Leggi tutto](../../delivery/using/sending-messages.md)

Sono state aggiunte informazioni su come aggiungere alle e-mail collegamenti che possono essere personalizzati e che supportano il tracciamento. [Leggi tutto](../../delivery/using/tracking-personalized-links.md).

## Gennaio 2021 {#jan-2021}

La sezione dell’attività **[!UICONTROL Fork]** è stata arricchita con informazioni sulle best practice. [Leggi tutto](../../workflow/using/fork.md)

La sezione **Connettori CRM** è stata aggiornata, migliorata e riorganizzata. [Leggi tutto](../../platform/using/crm-connectors.md).

La procedura per connettere **Adobe Campaign a Microsoft Dynamics** è ora descritta in una pagina dedicata. [Leggi tutto](../../platform/using/crm-ms-dynamics.md).

L’API Oracle On Demand è ora obsoleta per la connessione tra un sistema CMR e Campaign. [Leggi tutto](../../rn/using/deprecated-features.md).

Per individuare la versione corrente del servlet web Tomcat incorporato utilizzato in un’istanza di Adobe Campaign, consulta [questo articolo](../../production/using/locate-tomcat-version.md).

L’elenco dei flussi di lavoro tecnici con i pacchetti a essi associati è stato riorganizzato in una sola pagina. [Leggi tutto](../../workflow/using/about-technical-workflows.md)

La sezione relativa alla risoluzione dei problemi nella guida **Monitoraggio** è stata riorganizzata e migliorata con una pagina di destinazione. [Leggi tutto](../../production/using/troubleshooting.md).

È disponibile una nuova sezione **Importazione ed esportazione di dati** con nuove pagine su flussi di lavoro, compressione dei dati, crittografia e best practice per l’importazione. [Leggi tutto](../../platform/using/get-started-data-import-export.md)

+++


+++ 2020


## Dicembre 2020 {#dec-2020}

La sezione **Monitoraggio della consegna** è stata riorganizzata in argomenti tematici. [Leggi tutto](../../delivery/using/about-delivery-monitoring.md)

È stato aggiunto un caso di utilizzo su come aggiungere gli indirizzi IP dei mittenti ai registri di consegna. [Leggi tutto](../../delivery/using/delivery-dashboard.md#use-case)

Le domande frequenti sulla privacy sono state spostate in [questa sezione](../../platform/using/privacy-faq.md).

È stato aggiunto un caso d’uso su come utilizzare la funzionalità di unione dell’attività **[!UICONTROL Deduplication]**. [Leggi tutto](../../workflow/using/deduplication-merge.md)

Il protocollo del connettore SMS e la pagina delle sue impostazioni sono ora descritti [qui](../../delivery/using/sms-protocol.md).

È stata aggiunta una nota alla sezione **Messaggistica transazionale** per segnalare che, onde evitare problemi di diritti di accesso, le cartelle degli eventi non devono essere impostate come viste nelle istanze di esecuzione. [Leggi tutto](../../message-center/using/about-event-processing.md#event-collection)

## Novembre 2020 {#nov-2020}

La panoramica del modello dati della campagna è stata migliorata e riorganizzata. [Ulteriori informazioni](../../configuration/using/about-data-model.md).

La configurazione dell’account esterno è stata spostata in [questa sezione](../../installation/using/external-accounts.md).

La documentazione di Federated Data Access (FDA) per Campaign è stata migliorata con i dettagli di ogni configurazione di database esterno e spostata in [questa sezione](../../installation/using/about-fda.md).

La versione 20.2.3 di Campaign è stata spostata in Disponibilità generale (General Availability, GA).

La sezione Dati personali è stata spostata e arricchita con due nuove pagine: [Gestione della privacy](../../platform/using/privacy-management.md) e [Gestione delle richieste di accesso ai dati personali](../../platform/using/privacy-requests.md).

Nella pagina di configurazione del server di midsourcing è stata aggiunta una nota per specificare che il nome interno dell’account esterno non deve essere aggiornato una volta che il server è stato configurato. [Leggi tutto](../../installation/using/mid-sourcing-server.md)

Sono state aggiunte informazioni sulla sintassi da utilizzare per specificare il percorso di un server SFTP esterno. [Leggi tutto](../../platform/using/sftp-server-usage.md#external-SFTP-server)

La sezione Dati personali e Persone è stata aggiornata con uno scenario di utilizzo che illustra l’interazione delle diverse persone in materia di dati personali. [Leggi tutto](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

È stata aggiunta una nuova sezione in cui sono elencate le domande frequenti sulla privacy. [Leggi tutto](../../platform/using/privacy-faq.md)

## Ottobre 2020 {#oct-2020}

**Nuove funzionalità incluse nella versione 20.3**

Miglioramenti delle notifiche push per iOS - [Leggi tutto](../../delivery/using/configuring-the-mobile-application.md)

Miglioramenti delle notifiche push per Android - [Leggi tutto](../../delivery/using/configuring-the-mobile-application-android.md)

**Altri aggiornamenti alla documentazione in arrivo con la versione**

La Matrice di compatibilità è stata aggiornata. [Leggi tutto](../../rn/using/compatibility-matrix.md)

La pagina Funzioni obsolete e rimosse è stata aggiornata. [Leggi tutto](../../rn/using/deprecated-features.md)

Le note sulla versione e la matrice di compatibilità per la versione [!DNL Gold Standard] sono ora disponibili in una pagina dedicata.
[Leggi tutto](../../rn/using/gold-standard.md).

L’integrazione Triggers, originariamente basata sull’autenticazione OAuth per accedere alla pipeline ora è stata modificata e spostata in Adobe I/O. [Ulteriori informazioni](../../integrations/using/about-triggers.md#implement)

**Altri aggiornamenti**

Le pagine della documentazione sono state rinnovate per riflettere l’aggiornamento Tomcat 8.

Sono stati aggiunti dettagli nella descrizione della casella “Informazioni su” nella sezione “Ottenere la versione corretta di Adobe Campaign”. [Leggi tutto](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

Nella sezione “Aggiornamento Adobe Campaign Classic” sono state aggiunte le linee guida per eseguire un aggiornamento della build. [Maggiori informazioni](../../production/using/build-upgrade.md)

Alle domande comuni su Campaign è stata aggiunta una sezione di domande frequenti sull’aggiornamento della build. Leggi tutto [Leggi tutto](../../platform/using/faq-build-upgrade.md)

Ora è presente una sezione dedicata dove sono descritti i modelli di Campaign on-premise, in hosting e ibridi. [Leggi tutto](../../installation/using/hosting-models.md)

La matrice delle funzionalità di Campaign per il modello in hosting è stata aggiornata e spostata nella Guida all’installazione. [Leggi tutto](../../installation/using/capability-matrix.md)

La sezione sulle funzionalità avanzate di reportistica delle campagne è stata migliorata con l’aggiunta di specifiche su come utilizzare i parametri URL e le variabili nei report personalizzati. [Leggi tutto](../../reporting/using/advanced-functionalities.md)

La pagina delle proprietà del report è stata riorganizzata e arricchita per facilitare la configurazione. [Leggi tutto](../../reporting/using/properties-of-the-report.md)

## Settembre 2020 {#september-2020}

È stata aggiunta una nota per specificare che il conteggio dei profili attivi è disponibile solo per le istanze Marketing. [Leggi tutto](../../platform/using/about-profiles.md#active-profiles)

È stato aggiunto un nuovo esempio sull’utilizzo dell’editor dello schema per collegare un campo a una tabella di riferimento esistente. [Leggi tutto](../../configuration/using/examples-of-schemas-edition.md#uc-link)

È stata aggiunta una nota relativa all’utilizzo di dati aggiuntivi con indirizzi iniziali nelle consegne. [Leggi tutto](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## Agosto 2020 {#aug-2020}

Un’intera sezione è dedicata alla scoperta delle best practice relative alla progettazione della consegna e all’invio di contenuti con Campaign. [Leggi tutto](../../delivery/using/delivery-best-practices.md)

La pagina di destinazione Best practice per il recapito di messaggi è stata migliorata per facilitare l’accesso alle sottosezioni. [Leggi tutto](../../delivery/using/about-deliverability.md)

Sono ora disponibili video di spiegazione sui seguenti argomenti:

* [Come impostare la gestione dell’affaticamento utilizzando le regole di tipologia e i filtri predefiniti](../../campaign-opt/using/about-campaign-typologies.md)

* [Come creare un messaggio e-mail in una campagna](../../campaign/using/marketing-campaign-deliveries.md)

* [Come creare una newsletter multilingue con contenuti condizionali](../../delivery/using/conditional-content.md)

* [Come configurare e distribuire un modello di consegna](../../delivery/using/creating-a-delivery-template.md)

* [Come attivare e utilizzare AMP per le e-mail](../../delivery/using/defining-interactive-content.md)

* [Personalizzare le e-mail utilizzando blocchi di contenuto dinamici](../../delivery/using/personalization-blocks.md)

* [Come personalizzare le e-mail utilizzando i campi di personalizzazione](../../delivery/using/personalization-fields.md)

* [Come gestire seed e bozze in un’e-mail](../../delivery/using/steps-defining-the-target-population.md)

* [Come impostare una consegna ricorrente](../../workflow/using/recurring-delivery.md)

* [Come impostare una consegna continua](../../workflow/using/continuous-delivery.md)

Sono state aggiunte informazioni sui controlli e sulle azioni da eseguire quando viene visualizzato l’errore “Impossibile risolvere il nome host” dopo la connessione a un server FTP. [Leggi tutto](../../platform/using/sftp-server-usage.md)

Nell’elenco dei [casi di utilizzo del flusso di lavoro](../../workflow/using/about-workflow-use-cases.md) sono stati inseriti nuovi esempi:

* Automazione di creazione, edizione e pubblicazione di contenuti
* Impostazione di un processo di approvazione del destinatario prima di avviare una consegna
* Chiamata di una variabile di istanza in una query
* Applicazione di una percentuale divisa su una popolazione

La **[!UICONTROL AND-join]** sezione attività è stata arricchita con informazioni aggiuntive sull’utilizzo, nonché da una nota sull’impiego delle variabili. [Ulteriori informazioni](../../workflow/using/and-join.md)

## Luglio 2020 {#july-2020}

Ai casi di utilizzo del flusso di lavoro è stato aggiunto un esempio che spiega come aggiornare in automatico un elenco mediante una query incrementale. [Leggi tutto](../../workflow/using/about-workflow-use-cases.md)

Le [Note sulla versione](../../rn/using/latest-release.md) sono state riorganizzate: una nuova [pagina di panoramica](../../rn/using/latest-release.md) fornisce informazioni sugli stati della build, sul processo di aggiornamento, sulle raccomandazioni e sui collegamenti importanti. È stata aggiunta anche una pagina dedicata alle versioni [[!DNL Gold Standard] ](../../rn/using/gold-standard.md)e è stata integrata la [matrice di compatibilità](../../rn/using/compatibility-matrix.md).

È stata aggiunta una nuova sezione con le linee guida relative al monitoraggio di Campaign Classic. [Leggi tutto](../../production/using/monitoring-guidelines.md)

La sezione Privacy e consenso è stata migliorata con informazioni più dettagliate e collegamenti utili. [Leggi tutto](../../platform/using/privacy-and-recommendations.md)

La pagina Gestione della privacy in Campaign Classic è stata aggiornata con informazioni sul campo “regolamentazione” che ora è disponibile quando si utilizza l’API per configurare il processo automatico di richiesta di accesso a dati personali. [Ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

La pagina di panoramica sulla Gestione della privacy è stata aggiornata con informazioni sulla Legge tailandese sulla protezione dei dati personali (PDPA) e sulla Lei Geral de Proteção de Dados (LGPD) brasiliana. [Ulteriori informazioni](../../platform/using/privacy-and-recommendations.md)

Sono state aggiunte informazioni sui registri e sul comportamento dei flussi di lavoro secondari in caso di errore. [Leggi tutto](../../workflow/using/sub-workflow.md)

Sono state aggiunte le best practice nella sezione dell’attività **[!UICONTROL Scheduler]**. [Leggi tutto](../../workflow/using/scheduler.md)

## Giugno 2020 {#june-2020}

La sezione Rimozione di un indirizzo in quarantena è stata aggiornata. Ciò include un chiarimento dei casi in cui gli indirizzi vengono automaticamente rimossi dall’elenco di quarantena. [Leggi tutto](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Sono stati aggiunti casi di utilizzo su come [crittografare](../../platform/using/zip-encrypt.md) e [decrittografare](../../platform/using/unzip-decrypt.md) dati tramite il Pannello di controllo e i flussi di lavoro di Campaign.

La pagina di integrazione di Experience Cloud Triggers e Adobe Campaign Classic è stata spostata [qui](../../integrations/using/about-triggers.md).

## Luglio 2020 {#release-20-2}

**Nuove funzionalità incluse nella versione 20.2**

Supporto delle emoticon. [Leggi tutto](../../delivery/using/customizing-emoticon-list.md)

Connettore FDA per Azure Synapse. [Leggi tutto](../../installation/using/configure-fda-synapse.md)

Leggi sulla privacy in Thailandia e Brasile. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Altri aggiornamenti alla documentazione in arrivo con la versione**

La nuova opzione che consente di annullare la pubblicazione di un modello di messaggio transazionale è documentata in [questa sezione](../../message-center/using/publishing-message-templates.md#template-unpublication).

All’elenco delle opzioni di Campaign Classic sono state aggiunte le nuove opzioni che consentono di impostare limitazioni durante l’invio di e-mail contenenti immagini scaricate da un URL personalizzato e allegati. [Leggi tutto](../../installation/using/configuring-campaign-options.md#delivery)

La nuova opzione **Prepare the delivery parts in the database** è documentata in [questa sezione](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

La sezione Convalida della consegna è stata chiarita e aggiornata. [Leggi tutto](../../delivery/using/steps-validating-the-delivery.md)

I parametri relativi al nuovo meccanismo di firma dei collegamenti di tracking sono stati aggiunti alla sezione [File di configurazione del server](../../installation/using/the-server-configuration-file.md).

La Matrice di compatibilità è stata aggiornata. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

La sezione sul flusso di lavoro di pulizia è stata aggiornata. [Ulteriori informazioni](../../production/using/database-cleanup-workflow.md)

Gli endpoint di rete per Campaign sono stati spostati in questa [sezione](../../installation/using/campaign-network-endpoints.md).

La sezione sull’installazione di Spam Assassin è stata aggiornata con il nuovo nome del file di installazione. [Ulteriori informazioni](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

La sezione sulla duplicazione degli ambienti è stata aggiornata. [Ulteriori informazioni](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## Maggio 2020 {#may-2020}

La sezione Monitoraggio del recapito messaggi è stata spostata e migliorata. [Leggi tutto](../../delivery/using/monitoring-deliverability.md)

La sezione Risoluzione dei problemi di recapito messaggi è stata spostata e migliorata. [Leggi tutto](../../delivery/using/deliverability-faq.md)

È stata migliorata la sezione Linee guida sul recapito messaggi per l’avvio di una nuova piattaforma. [Leggi tutto](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it#transition-process)

La sezione Invio di e-mail transazionali con allegati è stata spostata e aggiornata. [Leggi tutto](../../message-center/using/transactional-email-with-attachments.md)

La sezione sulle best practice relative ai pacchetti dati è stata spostata e aggiornata. [Leggi tutto](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## Aprile 2020 {#april-2020}

La tabella delle autorizzazioni FDA è stata spostata nella documentazione Accesso a un database esterno (FDA). [Leggi tutto](../../installation/using/remote-database-access-rights.md)

Le domande frequenti sono state aggiornate con suggerimenti su come eseguire la cancellazione di soft cache e hard cache. [Leggi tutto](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Le best practice relative ai modelli dati sono state migliorate, con informazioni aggiuntive sugli indici. [Leggi tutto](../../configuration/using/data-model-best-practices.md#indexes)

La sezione che descrive il modello dati integrato di Adobe Campaign è stata aggiornata con ulteriori dettagli su ogni tabella. [Leggi tutto](../../configuration/using/data-model-description.md)

I casi di utilizzo dei flussi di lavoro sono stati aggiornati e riorganizzati in sezioni tematiche. [Leggi tutto](../../workflow/using/about-workflow-use-cases.md)

Le sezioni [Qualificazione di mail non recapitate](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) e [Regole di gestione delle e-mail](../../delivery/using/understanding-delivery-failures.md#email-management-rules) sono state migliorate con informazioni aggiornate.

L’articolo sull’MTA avanzato di Adobe Campaign è stato aggiornato. Ora si applica solo a Campaign Classic. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/acc-campaign-enhanced-mta.html)

## Marzo 2020 {#march-2020}

Le best practice relative ai modelli dati sono state aggiornate con nuove sezioni, tra cui [Sequenze](../../configuration/using/data-model-best-practices.md#sequences), [Prestazioni](../../configuration/using/data-model-best-practices.md#performance) e [Tabelle di grandi dimensioni](../../configuration/using/data-model-best-practices.md#large-tables). [Leggi tutto](../../configuration/using/data-model-best-practices.md)

È ora disponibile una nuova sezione che descrive il modello dati integrato di Adobe Campaign e l’interazione tra le tabelle. [Leggi tutto](../../configuration/using/data-model-description.md)

Nella home page della documentazione sono stati aggiunti altri collegamenti chiave. [Leggi tutto](../../campaign-classic-home.md)

È stato aggiunto un caso di utilizzo su come integrare un’offerta dinamica da Adobe Target in un’e-mail in Adobe Campaign. [Leggi tutto](../../integrations/using/inserting-a-dynamic-image.md)

È ora disponibile una nuova sezione in cui sono elencate le diverse lingue disponibili in Adobe Campaign. [Leggi tutto](../../platform/using/adobe-campaign-workspace.md#languages)

Le linee guida per la gestione degli accessi sono state aggiornate con ulteriori informazioni sui diritti denominati. [Leggi tutto](../../platform/using/access-management-named-rights.md)

## Febbraio 2020 {#february-2020}

È ora disponibile una nuova sezione in cui sono illustrate le best practice e le principali raccomandazioni per la progettazione del modello dati di Adobe Campaign. [Leggi tutto](../../configuration/using/data-model-best-practices.md)

È disponibile una nuova sezione sulle configurazioni delle e-mail tecniche. [Leggi tutto](../../installation/using/email-deliverability.md)

Le domande frequenti sul recapito messaggi sono state aggiornate con ulteriori dettagli sul messaggio di errore relativo alle “quote soddisfatte”. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP per e-mail è ora supportato da nuovi provider e-mail: la relativa documentazione è stata aggiornata. [Leggi tutto](../../delivery/using/defining-interactive-content.md)

La sezione Archiviazione di e-mail è stata migliorata. [Leggi tutto](../../installation/using/email-archiving.md#recommendations-and-limitations)

## Gennaio 2020 {#release-20-1}

**Nuove funzionalità incluse nella versione 20.1**

Connettore FDA Snowflake. [Leggi tutto](../../installation/using/configure-fda-snowflake.md)

Miglioramenti del connettore FDA Hadoop. [Leggi tutto](../../installation/using/configure-fda-hadoop.md)

**Altri aggiornamenti alla documentazione in arrivo con la versione**

Le guide di [installazione](../../installation/using/general-architecture.md), [produzione](../../production/using/foreword.md) e [configurazione](../../configuration/using/additional-parameters.md) sono state aggiornate con la nuova unità di sistema utilizzata dall’avvio del servizio nlserver. Puoi continuare a utilizzare /etc/init.d/nlserver6, ma Adobe consiglia ora di utilizzare il comando systemctl per interagire con il servizio nlserver.

La guida all’installazione è stata aggiornata e sincronizzata con la versione più recente della matrice di compatibilità. Sono stati aggiunti nuovi sistemi supportati. Sono state rimosse le occorrenze di sistemi obsoleti e non supportati. [Leggi tutto](../../installation/using/general-architecture.md)

La Matrice di compatibilità è stata aggiornata con i connettori FDA Hadoop 3.0 e Snowflake. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

Nella guida all’installazione è stata aggiunta una best practice sull’affinità degli IP. [Leggi tutto](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

La sezione sul flusso di lavoro di pulizia del database è stata aggiornata. Le cifre delle batch fornite ora riflettono l’implementazione del codice. [Leggi tutto](../../production/using/database-cleanup-workflow.md)

Nella guida alla messaggistica transazionale è stata aggiunta una limitazione su FDA tramite HTTP. [Leggi tutto](../../production/using/database-cleanup-workflow.md)

Sono state aggiunte informazioni sulla nuova opzione che ti consente di definire un periodo di timeout per le attività del flusso di lavoro **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]**. [Leggi tutto](../../workflow/using/sql-code-and-javascript-code.md)

Sono state aggiunte informazioni sulla nuova visualizzazione **[!UICONTROL Start Pending]** disponibile nel nodo **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Leggi tutto](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

La guida [Invio di notifiche push](../../delivery/using/about-mobile-app-channel.md) è stata spostata, riorganizzata e migliorata con informazioni più chiare.

Il nuovo parametro per la configurazione dei report URL è stato documentato [qui](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

La pagina della **matrice delle funzionalità on-premise e in hosting di Campaign Classic** è stata aggiornata con i nuovi connettori FDA. [Ulteriori informazioni](../../installation/using/capability-matrix.md).

La pagina della **matrice delle funzionalità di Campaign Classic** è stata aggiornata. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

Il nuovo flusso di lavoro **[!UICONTROL Cleanup of Nmsaddress]** è stato documentato [qui](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

È stata aggiunta una limitazione quando si utilizza un’attività di query in un flusso di lavoro. [Ulteriori informazioni](../../workflow/using/query.md).

È stata aggiunta una nuova sezione che descrive le regole di convalida degli indirizzi e-mail migliorate per porre un indirizzo in quarantena nel caso di un errore morbido. [Leggi tutto](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Il parametro del file di configurazione che indica se un’istanza utilizza o meno l’MTA avanzato è ora documentato. [Leggi tutto](../../installation/using/the-server-configuration-file.md#mta)

La sezione Recapito messaggi è stata spostata, riorganizzata e migliorata con contenuti aggiornati. [Leggi tutto](../../delivery/using/about-deliverability.md)

È ora disponibile una nuova sezione che descrive le nozioni di base sul modello dati di Adobe Campaign Classic e come accedere alla descrizione di ogni tabella. [Leggi tutto](../../configuration/using/about-data-model.md)

L’articolo sull’MTA avanzato di Adobe Campaign è stato aggiornato con informazioni più dettagliate sull’installazione di un pacchetto di tipologia in istanze che non aggiungono le intestazioni dell’MTA avanzato richieste a ogni messaggio. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

I casi di utilizzo relativi alla progettazione di query sono stati riorganizzati in sezioni separate. [Leggi tutto](../../workflow/using/querying-recipient-table.md)

È ora disponibile una nuova sezione sui suggerimenti per la gestione delle offerte e l’utilizzo del modulo di interazione in Adobe Campaign Classic. [Leggi tutto](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

La documentazione relativa all’interazione è stata arricchita con collegamenti a diversi video che consentono di comprendere al meglio come gestire le offerte. [Leggi tutto](../../interaction/using/interaction-and-offer-management.md)

L’articolo sulle best practice per l’ottimizzazione delle query in esecuzione nell’istanza è stato integrato nella documentazione. [Leggi tutto](../../workflow/using/query.md#optimizing-queries)

La guida al reporting è stata aggiornata e riorganizzata. [Leggi tutto](../../reporting/using/about-adobe-campaign-reporting-tools.md)

È stato aggiunto un esempio di come utilizzare una variabile di istanza in un flusso di lavoro. [Leggi tutto](../../workflow/using/javascript-scripts-and-templates.md)

+++
