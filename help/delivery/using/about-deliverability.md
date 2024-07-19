---
product: campaign
title: Introduzione al recapito messaggi in Campaign
description: Scopri le best practice per la consegna dei messaggi
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 7%

---

# Che cos’è il recapito messaggi{#about-deliverability}

Il recapito messaggi consente di misurare il successo delle campagne che raggiungono la casella in entrata dei destinatari senza che vengano saltati o contrassegnati come spam. [Scopri perché il recapito messaggi è importante](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Più precisamente, il recapito messaggi e-mail si riferisce all’insieme di caratteristiche che determinano la capacità di un messaggio di raggiungere la sua destinazione, tramite un indirizzo e-mail personale, in un breve periodo di tempo e con la qualità prevista in termini di contenuto e formato.

Per informazioni più approfondite sulla consegna dei messaggi e per ulteriori informazioni sui termini, i concetti e gli approcci chiave per la consegna dei messaggi, consulta l&#39;[Adobe di Guida alle best practice per la consegna dei messaggi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

## Come migliorare il recapito messaggi {#deliverability-key-points}

I problemi di recapito dei messaggi sono solitamente legati a misure di protezione contro lo spam implementate dai provider di servizi Internet e dagli amministratori del server di posta.

* Per raccomandazioni generali su come progettare campagne di e-mail marketing di successo, consulta [Strategia e definizione di recapito messaggi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Per raccomandazioni più specifiche su come ottimizzare il recapito dei messaggi e-mail di Adobe Campaign, l’Adobe consiglia di utilizzare le best practice elencate in questa sezione.

>[!NOTE]
>
>Poiché gli ISP sono obbligati a sviluppare continuamente nuove sofisticate tecniche di filtro per proteggere i propri clienti dagli spammer, la consegna delle e-mail è caratterizzata da criteri e regole in continua evoluzione. Fai riferimento alla [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it), che viene aggiornata regolarmente.

### Percentuale di consegna

Il tasso di recapito messaggi è il numero di messaggi che raggiungono le caselle in entrata dei destinatari rispetto al numero di messaggi consegnati. Per migliorare il recapito messaggi, puoi aumentare questo tasso.

Con Adobe Campaign, il tasso di consegna dipende da numerosi fattori, in particolare:

* Corretta configurazione delle istanze: contatta il rappresentante dell’Adobe per assistenza.
* Configurazione di rete legittima: vedi [questa sezione](optimize-delivery.md#network-config) e [Configurazione e strategia del dominio](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* La reputazione dell&#39;indirizzo IP: vedi [Strategia IP](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Qualità degli indirizzi di destinazione: vedi [Gestione quarantena](optimize-delivery.md#quarantine-management).
* Bassi [reclami](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) e [tassi di mancato recapito](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces).
* Contenuto del messaggio: vedi [Controlla il contenuto dell&#39;e-mail](control-message-content.md).
* Autenticazione messaggi (SPF, DKIM, DMARC): vedere [questa sezione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Reputazione del mittente: per informazioni sulla valutazione della reputazione del mittente da parte degli ISP principali, vedere [questa sezione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Strumenti di recapito messaggi della campagna {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign fornisce diversi strumenti per monitorare e migliorare le prestazioni di consegna della piattaforma. Questa pagina evidenzia anche i principi principali da tenere presenti per ottimizzare il recapito dei messaggi durante l’utilizzo di Campaign.

### Crea il messaggio con attenzione

Durante la configurazione, la progettazione e il test del messaggio, assicurati di seguire le best practice indicate nelle sezioni elencate di seguito. L’utilizzo di tutte le funzioni fornite da Adobe Campaign consente di migliorare il recapito messaggi.

* [Best practice per la consegna](delivery-best-practices.md)
* [Controllare il contenuto dell’e-mail](control-message-content.md)
* [Rendering della casella in entrata](inbox-rendering.md)
* [Invio di una bozza](steps-validating-the-delivery.md#sending-a-proof)

### Verificare il consenso tramite il doppio consenso {#double-opt-in}

Per evitare l’invio di messaggi a indirizzi non validi, limitare le comunicazioni improprie e migliorare la reputazione del mittente, l’Adobe consiglia di implementare un doppio meccanismo di consenso. Questo metodo ti consente di garantire che i destinatari si siano abbonati intenzionalmente.

Per ulteriori informazioni, consulta [Creare un abbonamento con doppio consenso](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

Adobe Per ulteriori informazioni sulle best practice per la raccolta di dati dai clienti, consulta la [Guida alle best practice per il recapito di messaggi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Gestione della quarantena

Adobe Campaign gestisce un elenco che raccoglie i reclami e i mancati recapiti non recapitati di posta indesiderata, i mancati recapiti permanenti e i mancati recapiti non permanenti che si verificano in modo coerente.

Per proteggere il recapito messaggi, i destinatari i cui indirizzi sono in tale elenco sono esclusi per impostazione predefinita da tutte le consegne future, perché l’invio a questi contatti potrebbe danneggiare la reputazione del mittente.

Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena consente quindi di evitare che questi provider aggiungano altri elementi al elenco Bloccati del sistema di protezione.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Errori di consegna](understanding-delivery-failures.md)
* [Informazioni sulla gestione della quarantena](understanding-quarantine-management.md)
* [Quarantena e inserisco nell&#39;elenco Bloccati di](understanding-quarantine-management.md#quarantine-vs-denylist)

### Utilizzare strumenti di monitoraggio e reporting

Utilizza le funzioni offerte da Adobe Campaign per monitorare il recapito messaggi.

Adobe Campaign consente di controllare le prestazioni delle consegne tramite una serie di indicatori e rapporti in tempo reale incorporati per ottenere informazioni approfondite sulle consegne.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Monitorare il recapito messaggi](monitoring-deliverability.md)
* [Introduzione al monitoraggio della consegna](about-delivery-monitoring.md)
* [Introduzione ai rapporti incorporati di Campaign](../../reporting/using/about-campaign-built-in-reports.md)
