---
solution: Campaign Classic
product: campaign
title: Privacy e consenso
description: Ulteriori informazioni su Privacy e Consenso
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Privacy e consenso{#privacy-and-recommendations}

## Raccomandazioni generali {#general-recommendations}

Adobe Campaign è uno strumento utile per la raccolta e l’elaborazione di grandi quantità di dati, compresi informazioni personali e dati riservati. Ecco perché è fondamentale gestire attentamente la privacy.

* Fai sempre uso delle informazioni personali in modo responsabile ed etico.

* Non inviare e-mail, notifiche push e messaggi SMS non richiesti (“spam”). Adobe crede fermamente nei principi del permission marketing per promuovere la fedeltà e il valore del ciclo di vita del cliente, e pertanto vieta severamente l’utilizzo di Adobe Campaign per l’invio di messaggi non richiesti.

Prenditi del tempo per esaminare la [Lista di controllo protezione e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html) per scoprire gli elementi principali da verificare in materia di protezione e privacy.

### Normative sulla privacy {#privacy-regulations}

Per gestire correttamente la privacy e i dati personali, attieniti alle normative applicabili alle regioni in cui operi. Tali normative comprendono:
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_it) (Regolamento generale europeo sulla protezione dei dati)
* [DPA](https://www.gov.uk/data-protection) (implementazione del GDPR nel Regno Unito)
* [Direttiva europea relativa alla vita privata e alle comunicazioni elettroniche](https://eur-lex.europa.eu/legal-content/IT/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (legge statunitense che definisce le regole e i requisiti per le e-mail commerciali)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (legge sulla protezione dei dati personali in Thailandia)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf)  (Legge sulla Protezione Generale dei Dati in Brasile) - sarà in vigore a partire dal 16 agosto 2020

>[!NOTE]
>
>Per ulteriori informazioni su come GDPR, CCPA, PDPA e LGPD si applicano a  Adobe Campaign, vedere [questa pagina](../../platform/using/privacy-management.md#privacy-management-regulations).

### Privacy di Adobe Experience Cloud {#experience-cloud-privacy}

 Adobe Campaign fa parte delle soluzioni Adobe Experience Cloud. Il modo in cui viene gestita la privacy in Campaign rispetta i principi generali di Experience Cloud, come ad esempio quanto segue:

* **Quali informazioni vengono raccolte durante l’utilizzo di Adobe Experience Cloud**

   In qualità di azienda che utilizza le soluzioni Adobe Experience Cloud, puoi scegliere quali informazioni raccogliere e inviare all’account Adobe Experience Cloud. Alcuni esempi dei tipi di informazioni che possono essere raccolti includono l’attività di navigazione web, gli indirizzi IP, le informazioni sulla posizione inviate dai dispositivi mobili, i tassi di successo delle campagne, gli elementi acquistati o inseriti nel carrello, ecc.

   >[!NOTE]
   >
   >Come tutti i prodotti Adobe, Campaign raccoglie informazioni sugli utenti dell’app e del sito web. Per ulteriori informazioni, consulta l’[Informativa sulla privacy di Adobe](https://www.adobe.com/privacy/policy.html).

* **Utilizzare Adobe Experience Cloud per raccogliere informazioni**

   * Le soluzioni Adobe Experience Cloud utilizzano cookie e tecnologie simili, come web beacon (noti anche come tag o pixel), per consentirti di raccogliere informazioni. Per ulteriori informazioni sui cookie e sulle funzionalità di tracciamento con Adobe Campaign, consulta [questa sezione](#tracking-capabilities).
   * Puoi anche utilizzare le tecnologie Adobe Experience Cloud nelle tue app mobili. Per ulteriori informazioni sull&#39;invio di invii mobili con Campaign, vedi [canale SMS](../../delivery/using/sms-channel.md) e [canale app mobile](../../delivery/using/about-mobile-app-channel.md).

* **Scelte degli utenti in materia di privacy relative all’utilizzo di Adobe Experience Cloud**

    Adobe richiede che tu fornisca ai clienti le informative sulla privacy che descrivono:

   * Le tue prassi in materia di privacy in relazione ad Adobe Experience Cloud
   * In che modo gli utenti possono impostare le proprie preferenze per la raccolta o l’utilizzo delle proprie informazioni in relazione ad Adobe Experience Cloud

   >[!NOTE]
   >
   >Come per tutti i prodotti di Adobe, gli utenti di Campaign possono scegliere di rinunciare alla condivisione di informazioni raccolte su di loro tramite app e siti web. Per ulteriori informazioni, consulta le [domande frequenti relative all’utilizzo di Adobe Experience Cloud](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html).

Per ulteriori dettagli sulla privacy di Adobe Experience Cloud, consulta [questa pagina](https://www.adobe.com/it/privacy/experience-cloud.html).

## Dati personali e utenti tipo {#personal-data}

Nella gestione della privacy è importante definire quali dati devono essere gestiti con cura e chi si occupa della gestione.
* **I dati personali** sono informazioni che possono identificare direttamente o indirettamente un individuo.
* **I dati personali riservati** sono informazioni relative alla razza, alle opinioni politiche, alle credenze religiose, ai precedenti penali, alle informazioni genetiche, ai dati sulla salute, alle preferenze sessuali e alle informazioni biometriche di un individuo, nonché alla sua appartenenza a un sindacato.

Durante l&#39;integrazione di Campaign con altre soluzioni  Experience Cloud in cui il pubblico può essere trasferito da un sistema all&#39;altro, come [ Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [ Audience Manager o il servizio core Persone](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md) o con altre soluzioni tramite [Connettori CRM](../../platform/using/crm-connectors.md), è necessario prestare maggiore attenzione alla protezione dei dati personali.

Le [normative principali](#privacy-regulations) si riferiscono alle diverse entità che gestiscono i dati come segue:
* Il **titolare del trattamento** è l’autorità che determina i mezzi e lo scopo della raccolta, dell’utilizzo e della condivisione dei dati personali.
* Il **responsabile del trattamento** è qualsiasi individuo o parte che raccoglie, utilizza o condivide dati personali come indicato dal titolare del trattamento.
* L’**interessato** è qualsiasi individuo i cui dati personali vengono raccolti, utilizzati o condivisi e che può essere identificato direttamente o indirettamente in base a tali dati personali.

Pertanto, in quanto azienda che raccoglie e condivide dati personali, ricopri il ruolo di titolare del trattamento, i tuoi clienti costituiscono gli interessati e Adobe Campaign agisce come responsabile del trattamento quando tratta i loro dati personali secondo le istruzioni da te fornite. In quanto titolare del trattamento, sei responsabile della gestione del rapporto con gli interessati, ad esempio durante la gestione delle [richieste di accesso a dati personali](#privacy-requests).

### Scenario del caso d’uso {#use-case-scenario}

Per illustrare il modo in cui interagiscono i diversi utenti tipo, ecco un esempio di un caso d’uso dettagliato di customer experience relativo al GDPR.

In questo esempio, il cliente Adobe Campaign è una compagnia aerea. La compagnia aerea è il **titolare del trattamento** e tutti i suoi clienti sono gli **interessati**. Laura in questo caso particolare è una cliente della compagnia aerea.

Di seguito sono elencati i diversi utenti tipo utilizzati in questo esempio:

* **Laura** è l’**interessato**. È il destinatario che riceve messaggi dalla compagnia aerea. Ammettiamo che Laura sia una viaggiatrice frequente e che a un certo punto decida di non voler ricevere messaggi pubblicitari o di marketing personalizzati da parte della compagnia aerea. Laura chiederà alla compagnia aerea (sulla base del loro processo) di cancellare il suo numero di viaggiatrice frequente.

* **Anne** è il **titolare del trattamento** presso la compagnia aerea. Riceve la richiesta di Laura, recupera gli ID utili richiesti per identificare l’interessato e invia la richiesta da Adobe Campaign.

* **Adobe Campaign** è il **responsabile del trattamento**.

![](assets/privacy-gdpr-flow.png)

Di seguito è riportato il flusso generale relativo a questo caso d’uso:

1. L’**interessato** (Laura) invia una richiesta GDPR al **titolare del trattamento** tramite e-mail, assistenza clienti o un portale web.

1. Il **titolare del trattamento** (Anne) invia la richiesta GDPR a Campaign tramite l’interfaccia o utilizzando un’API.

1. Una volta che il **responsabile del trattamento** (Adobe Campaign) riceve le informazioni, interviene sulla richiesta GDPR e invia una risposta o una conferma al **titolare del trattamento** (Anne).

1. Il **titolare del trattamento** (Anne) esamina le informazioni e le invia nuovamente all’**interessato** (Laura).

## Acquisizione dei dati {#data-acquisition}

 Adobe Campaign ti consente di raccogliere dati, incluse informazioni personali e riservate. È pertanto essenziale ricevere e monitorare il consenso dei destinatari.

* Assicurati che i destinatari ricevano le comunicazioni solo se lo desiderano. Per farlo, accetta al più presto le richieste di rifiuto e verifica il consenso mediante un processo di doppio consenso. Per ulteriori informazioni, vedere [Creare un modulo di iscrizione con doppio opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* Non importate elenchi fraudolenti e utilizzate indirizzi iniziali per verificare che il file client non venga utilizzato in modo fraudolento. Per ulteriori informazioni, vedere [Informazioni sugli indirizzi iniziali](../../delivery/using/about-seed-addresses.md).
* Tramite la gestione del consenso e dei diritti puoi tenere traccia delle preferenze dei destinatari e gestire chi all’interno dell’organizzazione può accedere ai dati. Per ulteriori informazioni, consulta [questa sezione](#consent).
* Facilita e gestisci le richieste di accesso a dati personali dei destinatari. Per ulteriori informazioni, consulta [questa sezione](#privacy-requests).

## Gestione della privacy {#privacy-management}

La gestione della privacy si riferisce a tutti i processi e agli strumenti che possono aiutarti a rispettare le normative sulla privacy (GDPR, CCPA, ecc.). Per una panoramica sulla gestione della privacy, visita [questa pagina](https://helpx.adobe.com/it/campaign/kb/campaign-privacy-overview.html).

 Adobe Campaign offre varie serie di funzioni dedicate alla gestione della privacy:
* Gestione del consenso, conservazione dei dati e ruoli degli utenti. Vedi [questa sezione](#consent).
* Richieste di accesso a dati personali (diritto di accesso e diritto all’oblio). Vedi [questa sezione](#privacy-requests).
* Rinuncia alla vendita di informazioni personali (relativa al CCPA). Vedi [questa sezione](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

In [questa sezione](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-faq.html?lang=it#getting-started) sono illustrate le principali funzionalità di Campaign relative alla privacy e un esempio degli utenti tipo coinvolti.

### Consenso, conservazione e ruoli {#consent}

Adobe Campaign offre da sempre funzioni importanti necessarie per la privacy:

* **Gestione del consenso**: attraverso il processo di gestione degli abbonamenti, puoi gestire le preferenze dei destinatari e tenere traccia dei destinatari che hanno acconsentito all’abbonamento e di che tipo di abbonamento si tratta. Per ulteriori informazioni, vedere [Informazioni sulle iscrizioni](../../delivery/using/about-services-and-subscriptions.md).
* **Conservazione dei dati**: tutte le tabelle di registro standard integrate dispongono di periodi di conservazione preimpostati, che in genere limitano l’archiviazione dei dati a un massimo di 6 mesi. Puoi impostare ulteriori periodi di conservazione con i flussi di lavoro. Per maggiori informazioni, rivolgiti ai consulenti o agli amministratori tecnici di Adobe.
* **Gestione dei diritti**: Adobe Campaign consente di gestire i diritti assegnati ai vari operatori Campaign tramite diversi ruoli predefiniti o personalizzati. Questo consente di gestire chi può modificare, esportare o accedere a diversi tipi di dati all’interno dell’azienda. Per ulteriori informazioni, consulta [Informazioni sulla gestione degli accessi](../../platform/using/access-management.md).

Per ulteriori informazioni su queste funzioni e sulla loro gestione in Adobe Campaign, consulta [questa sezione](../../platform/using/privacy-management.md#consent-retention-roles).

### Richieste di accesso a dati personali {#privacy-requests}

 Adobe Campaign offre funzionalità aggiuntive per consentirti di attenerti a determinate richieste di accesso a dati personali in qualità di titolare del trattamento:

* Il **diritto di accesso** è il diritto dell’interessato di ottenere conferma da parte del titolare del trattamento sul fatto che i dati personali che lo riguardano siano trattati o meno, su dove avvenga il trattamento e sullo scopo del trattamento.

* Il **diritto all’oblio** (richiesta di cancellazione) autorizza l’interessato a richiedere che il titolare del trattamento cancelli i suoi dati personali.

Le richieste di **accesso** ed **eliminazione** vengono presentate in [questa sezione](../../platform/using/privacy-management.md#right-access-forgotten).

I passaggi di implementazione per creare queste richieste sono illustrati in [questa sezione](../../platform/using/privacy-requests.md).

## Funzionalità di tracciamento {#tracking-capabilities}

### Cookie {#cookies}

Grazie alle sue funzionalità di tracciamento,  Adobe Campaign permette di monitorare la navigazione dei destinatari della consegna utilizzando tre tipi di cookie: un cookie di sessione e due cookie permanenti.

* Un cookie **session**: il cookie **nlid** contiene l&#39;identificatore dell&#39;e-mail inviata al contatto (**broadlogId**) e l&#39;identificatore del modello di messaggio (**deliveryId**). Viene aggiunto quando il contatto fa clic su un URL incluso in un’e-mail inviata da Adobe Campaign e ti consente di tracciarne il comportamento sul web. Questo cookie di sessione viene cancellato automaticamente alla chiusura del browser. Il contatto può configurare il browser per rifiutare i cookie.

* Due **cookie** permanenti:
   * Il cookie **UUID** (Universal Unique IDentifier) è condiviso tra le soluzioni Adobe Experience Cloud. Viene impostato una volta fino a quando non scompare dal browser client quando viene generato un nuovo valore. Questo cookie consente di identificare gli utenti che interagiscono con le soluzioni del Experience Cloud  quando visitano un sito Web. Può essere depositato da una pagina di destinazione (per associare attività cliente sconosciute a un destinatario) o da una consegna. La descrizione di questo cookie è disponibile in [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=en#ec-cookies).
   * Il cookie **nllastdelid** (introdotto nel Campaign Classic 20.3) è un cookie permanente che contiene l&#39; **deliveryId** dell&#39;ultima consegna da cui l&#39;utente ha fatto clic sul collegamento. Questo cookie viene utilizzato - quando manca il cookie di sessione - per identificare la tabella di tracciamento che verrà utilizzata.

Normative quali il Regolamento generale sulla protezione dei dati (GDPR) affermano che le aziende necessitano del consenso degli utenti del sito web per installare i cookie.

* Dovete informare gli utenti che i vostri siti sono dotati di strumenti di monitoraggio Web tramite una richiesta di autorizzazione (che viene visualizzata sopra la pagina, ad esempio) con una casella di controllo per autorizzare l&#39;uso dei cookie, o aggiungere un banner nella parte superiore della prima pagina su cui accedono, ecc.
* Le finestre pop-up dovrebbero essere evitate in quanto spesso sono bloccate dai browser.

### Tracciamento dei messaggi {#message-tracking}

 Adobe Campaign consente di tenere traccia delle e-mail inviate e del comportamento dei destinatari della consegna: apertura, clic su collegamenti, annullamento di iscrizioni, ecc. Per ulteriori informazioni, vedere [Informazioni sul tracciamento dei messaggi](../../delivery/using/about-message-tracking.md).

A questo scopo, aggiungi [collegamenti tracciati](../../delivery/using/how-to-configure-tracked-links.md) ai messaggi per misurare l&#39;impatto del comportamento di consegna e destinatario nella scheda [Tracciamento](../../delivery/using/delivery-dashboard.md#tracking-logs) del dashboard di consegna. I dati di tracciamento vengono interpretati nel report [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators).

### Tracciamento Web {#web-tracking}

 Adobe Campaign consente inoltre di monitorare il modo in cui i destinatari possono sfogliare il sito Web: inserire tag di tracciamento per raccogliere informazioni e misurare le visite sulle pagine dell&#39;applicazione Web. Per ulteriori informazioni, vedere [Tracciamento di un&#39;applicazione Web](../../web/using/tracking-a-web-application.md).

La configurazione del tracciamento Web viene presentata in [questa sezione](../../configuration/using/about-web-tracking.md).

Per gestire ulteriormente il tracciamento,  Adobe Campaign consente di visualizzare un banner di rinuncia per interrompere il tracciamento dei comportamenti Web degli utenti finali che rifiutano il tracciamento del comportamento. Per ulteriori informazioni, vedere [Rinuncia al tracciamento delle applicazioni Web](../../web/using/web-application-tracking-opt-out.md).
