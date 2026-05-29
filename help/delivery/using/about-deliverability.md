---
product: campaign
title: Introduzione al recapito messaggi in Campaign
description: Scopri le best practice per la consegna dei messaggi
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
TQID: https://experienceleague.adobe.com/UuHzMhIx2zL3VxZXxnKM3UHBlN4Mkr7qy47Ttk-43d0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: beb7a3c1-66ab-4786-b879-7621375b3c40
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 851
ht-degree: 6%

---

# Che cos’è il recapito messaggi{#about-deliverability}

Il recapito messaggi consente di misurare il successo delle campagne che raggiungono la casella in entrata dei destinatari senza che vengano saltati o contrassegnati come spam. [Scopri perché il recapito messaggi è importante](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=it#why-deliverability-matters).

Più precisamente, il recapito messaggi e-mail si riferisce all’insieme di caratteristiche che determinano la capacità di un messaggio di raggiungere la sua destinazione, tramite un indirizzo e-mail personale, in un breve periodo di tempo e con la qualità prevista in termini di contenuto e formato.

Per informazioni più approfondite sulla consegna dei messaggi e per ulteriori informazioni su termini, concetti e approcci chiave, consulta la [Guida alle best practice per la consegna dei messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

## Come migliorare il recapito messaggi {#deliverability-key-points}

I problemi di recapito dei messaggi sono solitamente legati a misure di protezione contro lo spam implementate dai provider di servizi Internet e dagli amministratori del server di posta.

* Per raccomandazioni generali su come progettare campagne di e-mail marketing di successo, consulta [Strategia e definizione di recapito messaggi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=it).

* Per raccomandazioni più specifiche su come ottimizzare il recapito dei messaggi e-mail in Adobe Campaign, Adobe consiglia di utilizzare le best practice elencate in questa sezione.

>[!NOTE]
>
>Poiché gli ISP sono obbligati a sviluppare continuamente nuove sofisticate tecniche di filtro per proteggere i propri clienti dagli spammer, la consegna delle e-mail è caratterizzata da criteri e regole in continua evoluzione. Fai riferimento alla [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it), che viene aggiornata regolarmente.

### Percentuale di consegna

Il tasso di recapito messaggi è il numero di messaggi che raggiungono le caselle in entrata dei destinatari rispetto al numero di messaggi consegnati. Per migliorare il recapito messaggi, puoi aumentare questo tasso.

Con Adobe Campaign, il tasso di consegna dipende da numerosi fattori, in particolare:

* Corretta configurazione delle istanze: contatta il rappresentante Adobe per assistenza.
* Configurazione di rete legittima: vedere [Impostazione e strategia del dominio](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=it#domain-setup-and-strategy).
* La reputazione dell&#39;indirizzo IP: vedi [Strategia IP](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=it#ip-strategy).
* Bassi [reclami](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html?lang=it) e [tassi di mancato recapito](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html?lang=it#hard-bounces).
* Contenuto del messaggio: vedi [Controlla il contenuto dell&#39;e-mail](control-message-content.md).
* Autenticazione messaggi (SPF, DKIM, DMARC): vedere [questa sezione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=it#authentication).
* Reputazione del mittente: per informazioni sulla valutazione della reputazione del mittente da parte degli ISP principali, vedere [questa sezione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html?lang=it).

## Strumenti di recapito messaggi della campagna {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign fornisce diversi strumenti per monitorare e migliorare le prestazioni di consegna della piattaforma. Questa pagina evidenzia anche i principi principali da tenere presenti per ottimizzare il recapito dei messaggi durante l’utilizzo di Campaign.

### Crea il messaggio con attenzione

Durante la configurazione, la progettazione e il test del messaggio, assicurati di seguire le best practice indicate nelle sezioni elencate di seguito. L’utilizzo di tutte le funzioni fornite da Adobe Campaign consente di migliorare il recapito messaggi.

* [Best practice per la consegna](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=it){target="_blank"}.
* [Controllare il contenuto dell’e-mail](control-message-content.md)
* [Rendering della casella in entrata](inbox-rendering.md)
* [Invio di una bozza](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=it){target="_blank"}

### Verificare il consenso tramite il doppio consenso {#double-opt-in}

Per evitare l’invio di messaggi a indirizzi non validi, limitare le comunicazioni improprie e migliorare la reputazione del mittente, Adobe consiglia di implementare un doppio meccanismo di consenso. Questo metodo ti consente di garantire che i destinatari si siano abbonati intenzionalmente.

Per ulteriori informazioni, consulta [Creare un abbonamento con doppio consenso](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

Per ulteriori informazioni sulle best practice per la raccolta di dati dai clienti, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html?lang=it#data-quality-and-hygiene).

### Gestione della quarantena

Adobe Campaign gestisce un elenco che raccoglie i reclami e i mancati recapiti non recapitati di posta indesiderata, i mancati recapiti permanenti e i mancati recapiti non permanenti che si verificano in modo coerente.

Per proteggere il recapito messaggi, i destinatari i cui indirizzi sono in tale elenco sono esclusi per impostazione predefinita da tutte le consegne future, perché l’invio a questi contatti potrebbe danneggiare la reputazione del mittente.

Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena consente quindi di evitare che questi provider aggiungano altri elementi al elenco Bloccati del sistema di protezione.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Errori di consegna](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentazione di Campaign v8: guida completa)
* [Informazioni sulla gestione della quarantena](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentazione di Campaign v8: guida completa)

### Utilizzare strumenti di monitoraggio e reporting

Utilizza le funzioni offerte da Adobe Campaign per monitorare il recapito messaggi.

Adobe Campaign consente di controllare le prestazioni delle consegne tramite una serie di indicatori e rapporti in tempo reale incorporati per migliorare insight sulle consegne.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Introduzione al monitoraggio della consegna](about-delivery-monitoring.md)
* [Introduzione ai rapporti incorporati di Campaign](../../reporting/using/about-campaign-built-in-reports.md)
