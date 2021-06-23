---
product: campaign
title: Informazioni sul recapito messaggi in Campaign
description: Scopri le best practice per il recapito messaggi
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 9%

---

# Che cos’è il recapito messaggi{#about-deliverability}

Il recapito messaggi ti consente di misurare il successo delle campagne che raggiungono la casella in entrata dei destinatari senza rimbalzare o essere contrassegnate come spam. [Scopri perché il recapito messaggi è importante](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Più precisamente, il recapito messaggi e-mail si riferisce al set di caratteristiche che determinano la capacità di un messaggio di raggiungere la sua destinazione, tramite un indirizzo e-mail personale, in un breve periodo di tempo e con la qualità prevista in termini di contenuto e formato.

Per informazioni più approfondite sul recapito messaggi e per ulteriori informazioni su termini, concetti e approcci chiave per il recapito messaggi, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

## Come migliorare il recapito messaggi {#deliverability-key-points}

I problemi di recapito sono solitamente collegati a misure di protezione contro lo spam implementate da fornitori di servizi Internet e amministratori di server di posta.

* Per raccomandazioni generali su come progettare campagne di marketing e-mail di successo, consulta [Strategia di recapito messaggi e definizione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Per consigli più specifici su come ottimizzare il recapito messaggi delle e-mail di Adobe Campaign, Adobe consiglia di utilizzare le best practice elencate in questa sezione.

>[!NOTE]
>
>Poiché gli ISP sono obbligati a sviluppare continuamente nuove tecniche di filtraggio sofisticate per proteggere i loro clienti dagli spammer, la consegna delle e-mail è caratterizzata da criteri e regole in continua evoluzione. Assicurati di fare riferimento alla [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) che viene aggiornata regolarmente.

### Tasso di consegna

Il tasso di recapito messaggi è il numero di messaggi che hanno colpito le caselle in entrata dei destinatari rispetto al numero di messaggi inviati. Per migliorare il recapito messaggi, puoi lavorare per aumentare questo tasso.

Con Adobe Campaign, il tasso di consegna dipende da numerosi fattori, in particolare:

* Configurazione corretta delle istanze: contatta il tuo rappresentante Adobe per assistenza.
* Configurazione di rete legittima: consulta [questa sezione](optimize-delivery.md#network-config) e [Configurazione e strategia del dominio](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* La reputazione del tuo indirizzo IP: consulta [Strategia IP](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Qualità degli indirizzi interessati: consulta [Gestione della quarantena](optimize-delivery.md#quarantine-management).
* Percentuali basse [reclami](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) e [mancate consegne](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces).
* Contenuto del messaggio: consulta [Controllo del contenuto delle e-mail](control-message-content.md).
* Autenticazione dei messaggi (SPF, DKIM, DMARC): vedere [questa sezione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* reputazione del mittente: per scoprire come gli ISP principali valutano la reputazione di un mittente, consulta [questa sezione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Strumenti per il recapito messaggi di Campaign {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign fornisce diversi strumenti per monitorare e migliorare le prestazioni di recapito messaggi della piattaforma. Questa pagina evidenzia anche i principi principali che dovresti tenere a mente per ottimizzare il recapito messaggi durante l’utilizzo di Campaign.

### Crea il messaggio con attenzione

Durante la configurazione, la progettazione e il test del messaggio, assicurati di seguire le best practice menzionate nelle sezioni elencate di seguito. L’utilizzo di tutte le funzioni fornite da Adobe Campaign consente di migliorare il recapito messaggi.

* [Best practice per la consegna](delivery-best-practices.md)
* [Controllo dei contenuti dell’e-mail](control-message-content.md)
* [Rendering della casella in entrata](inbox-rendering.md)
* [Invio di una prova](steps-validating-the-delivery.md#sending-a-proof)

### Verifica il consenso tramite doppio consenso {#double-opt-in}

Per evitare l’invio di messaggi a indirizzi non validi, limitare le comunicazioni non corrette e migliorare la reputazione del mittente, l’Adobe consiglia di implementare un doppio meccanismo di consenso. Questo metodo ti consente di garantire che i destinatari si siano abbonati intenzionalmente.

Per ulteriori informazioni, consulta [Creare un abbonamento con doppio consenso](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

Per ulteriori informazioni sulle best practice per la raccolta di dati dai clienti, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Gestione della quarantena

Adobe Campaign gestisce un elenco che raccoglie reclami di spam, rimbalzi duri e mancati rimbalzi morbidi che si verificano in modo coerente.

Per proteggere il recapito messaggi, i destinatari i cui indirizzi si trovano in tale elenco vengono esclusi per impostazione predefinita da tutte le consegne future, in quanto l’invio a tali contatti potrebbe danneggiare la reputazione dell’invio.

Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena ti consente quindi di evitare di essere aggiunta al elenco Bloccati da questi provider.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Informazioni sugli errori di consegna](understanding-delivery-failures.md)
* [Informazioni sulla gestione della quarantena](understanding-quarantine-management.md)
* [Quarantena rispetto elenco Bloccati](understanding-quarantine-management.md#quarantine-vs-denylist)

### Utilizzare strumenti di monitoraggio e reporting

Utilizza le funzioni offerte da Adobe Campaign per monitorare il recapito messaggi.

Adobe Campaign ti consente di verificare le prestazioni delle consegne tramite un set di indicatori e rapporti in tempo reale incorporati per ottenere informazioni più approfondite sulle consegne.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Monitoraggio del recapito messaggi](monitoring-deliverability.md)
* [Informazioni sul monitoraggio delle consegne](about-delivery-monitoring.md)
* [Informazioni sui report incorporati di Campaign](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
