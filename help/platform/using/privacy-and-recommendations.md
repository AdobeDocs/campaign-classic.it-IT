---
title: Privacy e raccomandazioni
seo-title: Privacy e raccomandazioni
description: Privacy e raccomandazioni
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: 247d73933991047603b8d61c7489d976c448dd52
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 8%

---


# Privacy and Consent{#privacy-and-recommendations}

## Raccomandazioni generali {#general-recommendations}

 Adobe Campaign è uno strumento potente per la raccolta e il trattamento di grandi quantità di dati, tra cui dati personali e sensibili. Ecco perché la privacy deve essere gestita con attenzione.

* Fare sempre un uso responsabile ed etico delle informazioni personali.

* Non inviare e-mail, notifiche push e messaggi SMS non richiesti (&quot;spam&quot;).  Adobe crede fermamente nei principi di marketing delle autorizzazioni per promuovere il valore e la fedeltà della vita dei clienti, e pertanto vieta severamente l&#39;uso di  Adobe Campaign nell&#39;invio di messaggi non richiesti.

Prenditi del tempo per esaminare la [Lista di controllo protezione e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html) per scoprire gli elementi principali da verificare in materia di protezione e privacy.

### Norme sulla privacy {#privacy-regulations}

Per gestire correttamente la privacy e gestire i dati personali, lavorare nell&#39;ambito delle normative applicabili alle regioni in cui si opera. Tali regolamenti comprendono:
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (Regolamento generale europeo sulla protezione dei dati)
* [DPA](https://www.gov.uk/data-protection) (implementazione del GDPR da parte del Regno Unito)
* [Direttiva europea relativa alla vita privata e alle comunicazioni elettroniche](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (legge statunitense che fissa le regole e i requisiti per le e-mail commerciali)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;Chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (legge tailandese sulla protezione dei dati personali)
* [La LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (legge brasiliana sulla protezione dei dati) - entrerà in vigore a partire dal 16 agosto 2020

>[!NOTE]
>
>Per ulteriori informazioni su come GDPR, CCPA, PDPA e LGPD si applicano a  Adobe Campaign, consulta [questa pagina](https://helpx.adobe.com/it/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

### Adobe Experience Cloud privacy {#experience-cloud-privacy}

 Adobe Campaign fa parte delle soluzioni Adobe Experience Cloud. Il modo in cui viene gestita la privacy in Campaign rispetta i principi generali  Experience Cloud, come ad esempio:

* **Quali informazioni vengono raccolte quando si utilizza Adobe Experience Cloud?**

   In qualità di azienda che utilizza le soluzioni Adobe Experience Cloud, potete scegliere quali informazioni raccogliere e inviare al vostro account Adobe Experience Cloud. Alcuni esempi dei tipi di informazioni che possono essere raccolti sono l&#39;attività di navigazione Web, gli indirizzi IP, le informazioni sulla posizione dai dispositivi mobili, i tassi di successo della campagna, gli elementi acquistati o inseriti nel carrello, ecc.

   >[!NOTE]
   >
   >Come per tutti i prodotti  Adobe, Campaign raccoglie informazioni sugli utenti dell&#39;app e del sito Web. Per ulteriori informazioni, consulta l’ [Informativa](https://www.adobe.com/privacy/policy.html)sulla privacy di Adobe.

* **Utilizzo di Adobe Experience Cloud per la raccolta delle informazioni**

   * Le soluzioni Adobe Experience Cloud utilizzano cookie e tecnologie simili, come web beacon (noti anche come tag o pixel), per consentire la raccolta delle informazioni. Per ulteriori informazioni sui cookie e sulle funzionalità di tracciamento con  Adobe Campaign, consulta [questa sezione](#tracking-capabilities).
   * Puoi anche utilizzare le tecnologie Adobe Experience Cloud nelle tue app mobili. Per ulteriori informazioni sull&#39;invio di invii mobili con Campaign, consulta Canale [](../../delivery/using/sms-channel.md) SMS e Canale [app](../../delivery/using/about-mobile-app-channel.md)Mobile.

* **Scelte sulla privacy degli utenti relative all&#39;utilizzo di Adobe Experience Cloud**

    Adobe ti chiede di fornire ai clienti le politiche sulla privacy che descrivono:

   * Le tue prassi sulla privacy in relazione ad Adobe Experience Cloud
   * Come gli utenti possono impostare le proprie preferenze per la raccolta o l&#39;utilizzo delle proprie informazioni in relazione ad Adobe Experience Cloud

   >[!NOTE]
   >
   >Per quanto riguarda tutti  prodotti di Adobe, gli utenti di Campaign possono scegliere di non condividere le informazioni raccolte su di essi tramite app e siti Web. Per ulteriori informazioni, consulta le Domande frequenti relative all’utilizzo di [Adobe Experience Cloud](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html).

Per ulteriori dettagli sulla privacy di Adobe Experience Cloud, consultate [questa pagina](https://www.adobe.com/it/privacy/experience-cloud.html).

## Dati personali e personale {#personal-data}

Durante la gestione della privacy, è importante definire quali dati devono essere gestiti con cura e da chi.
* **Dati** personali sono informazioni che possono identificare direttamente o indirettamente un individuo vivente.
* **Dati** personali sensibili sono informazioni relative alla razza, alle opinioni politiche, alle convinzioni religiose, al contesto penale, alle informazioni genetiche, ai dati sulla salute, alla preferenza sessuale, alle informazioni biometriche, nonché all’appartenenza a un sindacato.

Le [principali legislazioni](#privacy-regulations) si riferiscono alle diverse entità che gestiscono i dati come segue:
* Un **titolare del trattamento** dei dati è l&#39;autorità che determina i mezzi e lo scopo della raccolta, dell&#39;uso e della condivisione dei dati personali.
* Un **processore** dati è qualsiasi individuo o parte che raccoglie, utilizza o condivide dati personali come indicato dal Titolare del trattamento.
* Un **Soggetto** dati è qualsiasi individuo vivente i cui dati personali sono raccolti, utilizzati o condivisi e che può essere identificato, direttamente o indirettamente, in riferimento a tali dati personali.

Pertanto, in quanto azienda che raccoglie e condivide dati personali, sei il Titolare del trattamento dei dati, i tuoi clienti sono i Soggetti dati e  Adobe Campaign agisce come un Processore dei dati quando tratta i loro dati personali come da te diretto. In quanto titolare del trattamento dei dati, è responsabilità dell&#39;utente gestire la relazione con gli interessati, ad esempio per la gestione delle richieste [di](#privacy-requests)privacy.

Quando si integra Campaign con altre soluzioni  Experience Cloud in cui i tipi di pubblico possono essere trasferiti da un sistema all&#39;altro, come [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager o il servizio](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md)di base Persone, [Campaign Standard](../../integrations/using/synchronizing-audiences.md)o con altre soluzioni tramite i connettori [](../../platform/using/crm-connectors.md)CRM, è necessario prestare maggiore attenzione alla protezione dei dati personali.

## Acquisizione dati {#data-acquisition}

 Adobe Campaign consente di raccogliere dati, comprese informazioni personali e riservate. È pertanto essenziale ricevere e monitorare il consenso dei destinatari.

* Chiedi sempre ai destinatari di ricevere le comunicazioni. A tal fine, è necessario rispettare al più presto le richieste di rifiuto e verificare il consenso mediante un processo di doppio consenso. Per ulteriori informazioni, consultate [Creare un modulo di iscrizione con doppio consenso](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* Non importate elenchi fraudolenti e utilizzate indirizzi iniziali per verificare che il file client non venga utilizzato in modo fraudolento. Per ulteriori informazioni, vedere [Informazioni sugli indirizzi](../../delivery/using/about-seed-addresses.md)iniziali.
* Tramite la gestione del consenso e dei diritti, puoi tenere traccia delle preferenze dei destinatari e gestire chi all&#39;interno dell&#39;organizzazione può accedere ai dati. Per ulteriori informazioni, consulta [questa sezione](#consent).
* Facilitare e gestire le richieste di privacy dei destinatari. Per ulteriori informazioni, consulta [questa sezione](#privacy-requests).

## Gestione della privacy {#privacy-management}

La gestione della privacy si riferisce a tutti i processi e gli strumenti che possono aiutarti a rispettare le normative sulla privacy (GDPR, CCPA, ecc.). Ottenete una panoramica della gestione della privacy in [questa pagina](https://helpx.adobe.com/it/campaign/kb/campaign-privacy-overview.html).

 Adobe Campaign offre diverse serie di funzioni dedicate alla gestione della privacy:
* Gestione del consenso, conservazione dei dati e ruoli utente. Vedi [questa sezione](#consent).
* Richieste sulla privacy (Diritto di accesso e Diritto di essere Dimenticato). Vedi [questa sezione](#privacy-requests).
* Rinuncia alla vendita di informazioni personali (specifiche CCPA). Vedi [questa sezione](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html#ccpa).

In [questa sezione](https://helpx.adobe.com/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow)sono illustrate le principali funzionalità di Privacy di Campaign e un esempio delle persone coinvolte.


### Consenso, mantenimento e ruoli {#consent}

In origine,  Adobe Campaign offre importanti caratteristiche essenziali per la privacy:

* **Gestione** del consenso: Attraverso il processo di gestione delle iscrizioni, potete gestire le preferenze dei destinatari e tenere traccia dei destinatari che hanno acconsentito a quale tipo di iscrizioni. Per ulteriori informazioni, consultate [Informazioni sulle sottoscrizioni](../../delivery/using/about-services-and-subscriptions.md).
* **Conservazione** dei dati: Tutte le tabelle di registro standard integrate hanno periodi di conservazione preimpostati, in genere limitano la memorizzazione dei dati a un massimo di 6 mesi. Con i flussi di lavoro è possibile impostare ulteriori periodi di conservazione. Per maggiori informazioni, rivolgiti ai consulenti del Adobe  o agli amministratori tecnici.
* **Gestione** dei diritti:  Adobe Campaign consente di gestire i diritti assegnati ai vari operatori Campaign tramite ruoli predefiniti o personalizzati diversi. Questo consente di gestire chi all’interno della società può accedere, modificare o esportare diversi tipi di dati. Per ulteriori informazioni, consultate [Informazioni sulla gestione](../../platform/using/access-management.md)degli accessi.

Per ulteriori informazioni su queste funzioni e su come gestirle in  Adobe Campaign, consultate [questa pagina](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#consent).

### Richieste sulla privacy {#privacy-requests}

 Adobe Campaign offre funzionalità aggiuntive per facilitare la preparazione di un utente in qualità di titolare del trattamento per determinate richieste di privacy:

* Il **diritto di accesso** è il diritto per l&#39;interessato di ottenere dalla conferma del Titolare dei Dati se i dati personali che li riguardano sono trattati, dove e perché.

* Il **Diritto di essere Dimenticato** (richiesta di cancellazione) autorizza l&#39;interessato a far cancellare i propri dati personali.

>[!NOTE]
>
>Questo set di strumenti è disponibile qui per aiutarti a rispettare la privacy per GDPR, CCPA, PDPA e LGPD. Per ulteriori informazioni su queste diverse normative, consulta [questa pagina](https://helpx.adobe.com/it/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

<!--* **GDPR** (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

* **CCPA** (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

* **Thailand's PDPA** (Personal Data Protection Act) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. This regulation applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.

Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil. This regulation also applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.-->

Le richieste **di accesso** ed **eliminazione** vengono presentate in [questa pagina](https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess). I passaggi di implementazione per creare queste richieste sono descritti in [questa sezione](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html#ManagingPrivacyRequests). <!--Tutorials are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).-->

## Funzionalità di tracciamento {#tracking-capabilities}

### Cookie {#cookies}

Grazie alle sue funzionalità di tracciamento,  Adobe Campaign permette di monitorare la navigazione dei destinatari della consegna utilizzando tre tipi di cookie: un cookie di sessione e due cookie permanenti.

* A **session cookie**: the **nlid** cookie contains the identifier of the email sent to the contact (**broadlogId**) and the identifier of the message template (**deliveryId**). Viene aggiunto quando il contatto fa clic su un URL incluso in un’e-mail inviata da Adobe Campaign e ti consente di tracciarne il comportamento sul web. Questo cookie di sessione viene cancellato automaticamente alla chiusura del browser. Il contatto può configurare il browser per rifiutare i cookie.

* Un cookie **** permanente: il cookie **UUID** (Universal Unique IDentifier) è condiviso tra le soluzioni Adobe Experience Cloud. Viene impostata una volta fino a quando non viene visualizzata dal browser client quando viene generato un nuovo valore. Questo cookie consente di identificare gli utenti che interagiscono con le soluzioni del Experience Cloud  quando visitano un sito Web. Può essere depositato da una pagina di destinazione (per associare attività cliente sconosciute a un destinatario) o da una consegna. La descrizione di questo cookie è disponibile [qui](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-mc.html).

<!--The **nllastdelid** cookie (introduced in Campaign Classic 20.3) is a permanent cookie which contains the **deliveryId** of the last delivery that user clicked the link from. This cookie is used - when the session cookie is missing - to identify the tracking table that will be used.-->

Regolamenti come il Regolamento generale sulla protezione dei dati (General Data Protection Regulation, GDPR) affermano che le aziende richiedono l&#39;accordo degli utenti del sito Web prima di installare qualsiasi cookie.

* Dovete informare gli utenti che i vostri siti sono dotati di strumenti di monitoraggio Web tramite una richiesta di autorizzazione (che viene visualizzata sopra la pagina, ad esempio) con una casella di controllo per autorizzare l&#39;uso dei cookie, o aggiungere un banner nella parte superiore della prima pagina su cui accedono, ecc.
* Le finestre pop-up dovrebbero essere evitate in quanto spesso sono bloccate dai browser.

### Tracciamento dei messaggi {#message-tracking}

 Adobe Campaign consente di tenere traccia delle e-mail inviate e del comportamento dei destinatari della consegna: apertura, clic su collegamenti, annullamento di iscrizioni, ecc. Per ulteriori informazioni, consulta [Informazioni sul tracciamento](../../delivery/using/about-message-tracking.md)dei messaggi.

A tal fine, aggiungi i collegamenti [](../../delivery/using/how-to-configure-tracked-links.md) tracciati ai messaggi per misurare l&#39;impatto del comportamento di consegna e destinatario nella scheda [Tracciamento](../../delivery/using/monitoring-a-delivery.md#tracking-logs) del dashboard di consegna. I dati di tracciamento vengono interpretati nel rapporto [Indicatori](../../reporting/using/delivery-reports.md#tracking-indicators) di tracciamento.

### Tracciamento Web {#web-tracking}

 Adobe Campaign consente inoltre di monitorare il modo in cui i destinatari possono sfogliare il sito Web: inserire tag di tracciamento per raccogliere informazioni e misurare le visite sulle pagine dell&#39;applicazione Web. Per ulteriori informazioni, vedere [Tracciamento di un&#39;applicazione](../../web/using/tracking-a-web-application.md)Web.

La configurazione del tracciamento Web viene presentata in [questa sezione](../../configuration/using/about-web-tracking.md).

Per gestire ulteriormente il tracciamento,  Adobe Campaign consente di visualizzare un banner di rinuncia per interrompere il tracciamento dei comportamenti Web degli utenti finali che rifiutano il tracciamento del comportamento. Per ulteriori informazioni, vedere [Web application tracking opt-out](../../web/using/web-application-tracking-opt-out.md).
