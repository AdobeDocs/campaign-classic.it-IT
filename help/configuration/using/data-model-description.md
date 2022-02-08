---
product: campaign
title: Descrizione del modello dati Adobe Campaign Classic
description: Questo documento descrive il modello dati di Adobe Campaign
feature: Data Model
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '2374'
ht-degree: 1%

---

# Descrizione del modello dati di Campaign{#data-model-description}

![](../../assets/v7-only.svg)

Adobe Campaign viene fornito con un modello dati predefinito. Questa sezione fornisce alcuni dettagli sulle tabelle integrate del modello dati Adobe Campaign e sulla loro interazione.

Per accedere alla descrizione di ciascuna tabella, vai a **[!UICONTROL Admin > Configuration > Data schemas]**, seleziona una risorsa dall’elenco e fai clic sul pulsante **[!UICONTROL Documentation]** scheda .

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>La struttura fisica e logica dei dati trasferiti nell’applicazione è descritta in XML. Essa obbedisce a una grammatica specifica ad Adobe Campaign, denominata schema. Per ulteriori informazioni sugli schemi Adobe Campaign, consulta [questa sezione](../../configuration/using/about-schema-reference.md).

## Descrizione delle principali tabelle {#description-main-tables}

Adobe Campaign si basa su un database relazionale contenente tabelle collegate tra loro.

Il diagramma seguente mostra i join tra le principali tabelle aziendali del modello dati Adobe Campaign con i campi principali per ciascuna tabella.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

Il modello dati Adobe Campaign predefinito include le tabelle principali elencate di seguito.

### NmsRecipient {#NmsRecipient}

Questa tabella corrisponde a **nms:recipient** schema.

È la tabella predefinita utilizzata per **destinatari di consegne**. Di conseguenza, contiene le informazioni necessarie per le consegne tramite i vari canali:

* sEmail: indirizzo e-mail.
* iEmailFormat: formato preferito per le e-mail (1 per Testo, 2 per HTML e 0 se non definito).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity sono utilizzati per costruire l&#39;indirizzo postale (in conformità con lo standard XPZ 10-011 AFNOR dal maggio 1997).
* sPhone, sMobilePhone, sFax contengono rispettivamente i numeri di telefono, telefono cellulare e fax.
* iBlackList è il flag di rinuncia predefinito utilizzato per i profili (1 significa &quot;non iscritto&quot;, 0 in caso contrario).

Il campo iFolderId è la chiave esterna che collega il destinatario alla relativa cartella di esecuzione. Per ulteriori informazioni, consulta [XtkFolder](#XtkFolder).

Il campo sCountryCode è il codice ISO alfa 2 3166-1 (2 caratteri) del paese associato al destinatario. Questo campo è in realtà una chiave esterna nella tabella di riferimento del paese (NmsCountry), che contiene le etichette del paese e altri dati del codice del paese. Se il paese non è popolato, il valore XX viene memorizzato (e viene utilizzato al posto di un record con ID zero).

Per ulteriori informazioni sulla tabella Destinatario, consulta [questa sezione](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Questa tabella corrisponde a **nms:group** schema.

Consente di creare **gruppi statici di destinatari**. Esiste una relazione molti-a-molti tra destinatari e gruppi. Ad esempio, un destinatario può appartenere a più gruppi e un gruppo può contenere più destinatari. I gruppi possono essere creati manualmente, tramite un’importazione o tramite il targeting di consegna. I gruppi vengono spesso utilizzati come target di consegna. Nel campo è presente un indice univoco che rappresenta il nome interno del gruppo sName. Il gruppo è collegato a una cartella (la chiave è iFolderId). Per ulteriori informazioni, consulta [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

La tabella delle relazioni NmsRcpGrpRel contiene solo i due campi corrispondenti agli identificatori delle tabelle collegate iRecipientId e iGroupId.

### NmsService {#NmsService}

Questa tabella corrisponde a **nms:servizio** schema.

In Adobe Campaign puoi creare e gestire gli abbonamenti ai servizi di informazione (argomenti). Nella tabella NmsService viene memorizzata la definizione dei servizi di informazione (argomenti) a cui i destinatari possono effettuare l’abbonamento (ad esempio una newsletter).

I servizi sono entità simili ai gruppi (raggruppamenti di destinatari statici), con la differenza che forniscono più informazioni e consentono una facile gestione degli abbonamenti e dei loro annullamenti tramite i moduli.

Nel campo è presente un indice univoco che rappresenta il nome interno del servizio sName. Il servizio è collegato a una cartella (la chiave è iFolderId). Per ulteriori informazioni, consulta [XtkFolder](#XtkFolder)). Infine, il campo iType specifica il canale di consegna del servizio (0 per e-mail, 1 per SMS, 2 per telefono, 3 per direct mailing e 4 per fax).

### NmsSubscription {#NmsSubscription}

Questa tabella corrisponde a **nms:abbonamento** schema.

Consente di gestire gli abbonamenti ai destinatari ai servizi di informazione.

### NmsSubHisto {#NmsSubHisto}

Questa tabella corrisponde a **nms:subHisto** schema.

Se le sottoscrizioni vengono gestite utilizzando i moduli web o l’interfaccia dell’applicazione, nella tabella NmsSubHisto verranno analizzate tutte le sottoscrizioni e i annullamenti delle sottoscrizioni. Il campo iAction specifica l’azione (0 per l’annullamento dell’abbonamento e 1 per l’abbonamento) eseguita sulla data memorizzata nel campo tsDate.

### NmsDelivery {#NmsDelivery}

Questa tabella corrisponde a **nms:consegna** schema.

Ogni record in questa tabella rappresenta un **azione di consegna** o **modello di consegna**. Contiene tutti i parametri necessari per l’esecuzione delle consegne (target, contenuto, ecc.). I registri di consegna (trasmissione) (NmsBroadLog) e gli URL di tracciamento associati (NmsTrackingUrl) vengono creati durante la fase di analisi (vedi di seguito per ulteriori dettagli su entrambe le tabelle).

Nel campo è presente un indice univoco che rappresenta il nome interno della consegna sInternalName o dello scenario. La consegna è collegata a una cartella di esecuzione (la chiave esterna è iFolderProcessId. Per ulteriori informazioni, consulta [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Contiene **tutte le cartelle della struttura** visibili nella **Navigazione** della console.

Le cartelle vengono digitate: il valore del campo sModel specifica il tipo di dati che è possibile includere nella cartella. Questo campo consente inoltre alla console client di visualizzare correttamente i dati con i moduli corrispondenti. I possibili valori per questo campo sono definiti in navTree.

La struttura ad albero è gestita dai campi iParentId e iChildCount . Il campo sFullName fornisce il percorso completo della cartella nella struttura. Infine, nel campo è presente un indice univoco che rappresenta il nome interno della cartella sName.

## Consegna e tracciamento {#delivery-and-tracking}

Questo insieme di tabelle è collegato al **Consegna** , che consente di monitorare le consegne e gli eventuali problemi riscontrati durante l’invio dei messaggi. Per ulteriori informazioni, consulta [Monitoraggio delle consegne](../../delivery/using/about-delivery-monitoring.md). Per ulteriori informazioni sul tracciamento, consulta [Tracciamento dei messaggi](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Questa tabella corrisponde a **nms:wideLogMsg** schema. Si tratta di un’estensione della tabella dei registri di consegna.

## Gestione delle campagne {#campaign-management}

Questo insieme di tabelle è collegato al **Campagne di marketing** , che consente di definire, ottimizzare, eseguire e analizzare campagne di comunicazione e marketing. Per ulteriori informazioni, consulta [Informazioni sulle campagne di marketing](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: Questa tabella corrisponde a **nms:operazione** schema. Contiene i dati delle campagne di marketing.
* **NmsDeliveryOutline**: Questa tabella corrisponde a **nms:deliveryOutline** schema. Contiene le proprietà estese della consegna (profilo di consegna).
* **NmsDlvOutlineItem**: Questa tabella corrisponde a **nms:dlvOutlineItem** schema. Contiene gli articoli di un profilo di consegna.
* **NmsDeliveryCustomization**: Questa tabella corrisponde a **nms:deliveryCustomization** schema. Contiene i campi di personalizzazione di una consegna.
* **NmsBudget**: Questa tabella corrisponde a **nms:budget** schema. Contiene i dati di un budget per una campagna, un piano, un programma, un&#39;attività e/o consegne.
* **NmsDocument**: Questa tabella corrisponde a **nms:documento** schema. Contiene i documenti di marketing della campagna sotto forma di file (immagini, excel o file Word, ecc.)
* **XtkWorkflow**: Questa tabella corrisponde a **xtk:workflow** schema. Contiene il targeting delle campagne.
* **NmsTask**: Questa tabella corrisponde a **nms:task** schema. Contiene la definizione di un’attività di marketing.
* **NmsAsset**: Questa tabella corrisponde a **nms:risorsa** schema. Contiene la definizione di una risorsa di marketing.

## Coerenza delle comunicazioni {#communication-consistency}

Questo insieme di tabelle è collegato al **Ottimizzazione di Campaign** , che consente di controllare, filtrare e monitorare l’invio di consegne. Per ulteriori informazioni, consulta [Informazioni sulle tipologie di campagne](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypeRule**: Questa tabella corrisponde a **nms:typologyRule** schema. Contiene le regole che si applicano alle consegne a seconda delle tipologie.
* **NmsType**: Questa tabella corrisponde a **nms:tipologia** schema. Contiene l’insieme di regole da applicare alle consegne che corrispondono alla tipologia.
* **NmsTypeRuleRel**: Questa tabella corrisponde a **nms:typologyRuleRel** schema. Contiene le relazioni tra le tipologie e le loro regole.
* **NmsVolumeLine**: Questa tabella corrisponde a **nms:volumeLine** schema. Contiene l&#39;insieme di linee di disponibilità delle regole di capacità.
* **NmsVolumeConsumed**: Questa tabella corrisponde a **nms:volumeConsumed** schema. Contiene tutte le linee di consumo delle regole di capacità.

## Gestione della risposta {#response-management}

Questo insieme di tabelle è collegato al **Gestione della risposta** , che consente di misurare il successo e la redditività delle campagne di marketing o delle proposte di offerte per tutti i canali di comunicazione. Per ulteriori informazioni, consulta [Informazioni sulla gestione della risposta](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaIpotesi {#NmsRemaHypothesis}

Questa tabella coincide con la **nms:remaHypointesi** schema. Contiene la definizione dell&#39;ipotesi di misurazione.

Questa tabella contiene informazioni significative memorizzate in XML, tra cui:

**Contesto di esecuzione (informazioni archiviate in XML)**

Il contesto di esecuzione popola le tabelle e i campi da prendere in considerazione per il calcolo della misurazione, vale a dire:
* Lo schema di archiviazione del registro di reazione nms:remaMatchRcp.
* Schema della tabella delle transazioni (ad esempio, acquisti).
* Lo schema di query, che consente di definire la tabella iniziale delle condizioni di ipotesi.
* I collegamenti a singoli utenti, che consentono di identificare l’individuo in base allo schema di query.
* Data della transazione. Questo campo non è obbligatorio, ma si consiglia di utilizzarlo per limitare il perimetro di calcolo.
* Importo della transazione: è un campo facoltativo per il calcolo automatico degli indicatori di ricavo.

**Perimetro ipotesi (informazioni archiviate in XML)**

Il perimetro di ipotesi consiste nel filtraggio dell&#39;ipotesi in base alla tabella dello schema di query.

**Script di overload dell&#39;ipotesi (informazioni archiviate in XML)**

Lo script di overload dell&#39;ipotesi è un codice JavaScript che consente di sovraccaricare il contenuto dell&#39;ipotesi durante l&#39;esecuzione.

**Indicatori di misura**

I seguenti indicatori vengono aggiornati automaticamente durante l&#39;esecuzione dell&#39;ipotesi:

* Numero di reazioni: **iTransaction**. Numero di righe nella tabella dei registri di reazione.
* Numero di contatti: **iContactReact**. Numero distinto di contatti mirati nell&#39;ipotesi.
* Numero di gruppi di controllo: **iProofReact**. Numero distinto di contatti del gruppo di controllo mirati nell&#39;ipotesi.
* Tasso di risposta contattato: **dContactReactRate**. Tasso di risposta dei contatti mirati nell&#39;ipotesi.
* Tasso di risposta del gruppo di controllo: **dProofReactRate**. Tasso di risposta del gruppo di controllo delle ipotesi.
* Entrate totali della popolazione contattata: **dContactReactTotalAmount**. Entrate totali dei contatti mirati nell&#39;ipotesi.
* Entrate medie del gruppo di controllo: **dContactReactAvgAmount**. Entrate medie dei contatti del gruppo di controllo mirato nell&#39;ipotesi.
* Entrate totali del gruppo di controllo: **dProofReactTotalAmount**. Entrate totali del gruppo di controllo delle ipotesi.
* Entrate medie del gruppo di controllo: **dReactAvgAmount**. Entrate medie del gruppo di controllo delle ipotesi.
* Margine totale per contatto: **dContactReactTotalMargin**. Margine totale per contatto oggetto dell&#39;ipotesi.
* Margine medio per contatto: **dContactReactAvgMargin**. Margine medio per contatto oggetto dell&#39;ipotesi.
* Margine totale del gruppo di controllo: **dProofReactTotalMargin**. Margine totale del gruppo di controllo oggetto dell&#39;ipotesi.
* Margine medio del gruppo di controllo: **dProofReactAvgMargin**. Margine medio del gruppo di controllo oggetto dell&#39;ipotesi.
* Entrate aggiuntive: **ImportoAggiuntivo**. (Entrate medie dei contattati - Entrate medie del gruppo di controllo) * Numero dei contattati.
* Margine aggiuntivo: **MargineAggiuntivo**. (Margine medio di contatto - Margine medio del gruppo di controllo) / Numero di contatti.
* Costo medio per contatto (espressione SQL). Costo calcolato della consegna / Numero di contatti.
* ROI (espressione SQL). Costo calcolato della consegna / Margine totale di contatto.
* ROI effettivo (espressione SQL). Costo calcolato della consegna/margine aggiuntivo.
* Significato: **Significativo** (espressione SQL). Contiene valori da 0 a 3 a seconda del significato della campagna.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Questa tabella corrisponde a **nms:remaMatchRcp** schema.

Contiene un documento che rappresenta la reazione di un individuo a una data ipotesi. Questi record sono stati creati durante l&#39;esecuzione delle ipotesi.

## Simulazione e consegna {#simulation-and-delivery}

Questo insieme di tabelle è collegato al **Simulazione** , che consente di verificare la distribuzione delle offerte appartenenti a una categoria o a un ambiente prima di inviare la proposta ai destinatari. Per ulteriori informazioni, consulta [Informazioni sulla simulazione delle offerte](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Questa tabella corrisponde a **nms:simulazione** schema. Rappresenta una simulazione per un insieme di consegne o offerte su una determinata popolazione.
* **NmsDlvSimulationRel**: Questa tabella corrisponde a **nms:dlvSimulationRel** schema. Contiene l’elenco delle consegne prese in considerazione nella simulazione. L&#39;ambito della simulazione è memorizzato in XML.
* **NmsOfferSimulationRel**: Questa tabella corrisponde a **nms:offerSimulationRel** schema. Ti consente di collegare una simulazione con un’offerta.

## Modulo di interazione {#interaction-module}

Questo insieme di tabelle è collegato al **Interazione** modulo, che consente di rispondere in tempo reale durante un&#39;interazione con un determinato contatto, rendendoli una o più offerte adattate. Per ulteriori informazioni, consulta [Gestione delle interazioni e delle offerte](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: Questa tabella corrisponde a **nms:offerta** schema. Contiene la definizione di ogni offerta di marketing.
* **NmsPropositionRcp**: Questa tabella corrisponde a **nms:propositionRcp** schema. Contiene il registro cross-channel delle proposte di marketing inviate a ogni singolo utente. Il record viene creato quando una proposta viene preparata o effettivamente presentata a un individuo.
* **NmsOfferSpace**: Questa tabella corrisponde a **nms:offerSpace** schema. Contiene la definizione delle posizioni in cui vengono presentate le proposte.
* **NmsOfferContext**: Questa tabella corrisponde a **nms:offerContext** schema. Contiene criteri aggiuntivi sull&#39;applicabilità della proposta e sulla definizione della formula di calcolo del peso.
* **NmsOfferView**: Questa tabella corrisponde a **nms:offerView**. Contiene le rappresentazioni dell’offerta.
* **NmsOfferCategory**: Questa tabella corrisponde a **nms:offerCategory**. Contiene le categorie di offerta.
* **NmsOfferEnv**: Questa tabella corrisponde a **nms:offerEnv**. Contiene gli ambienti delle offerte.

## Modulo del centro messaggi {#message-center-module}

Il seguente insieme di tabelle è collegato al **Messaggistica transazionale** (Centro messaggi), che consente di gestire comunicazioni singole e uniche inviate a un utente e generate da eventi attivati dai sistemi informativi. Per ulteriori informazioni, consulta [Informazioni sulla messaggistica transazionale](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Questa tabella corrisponde a **nms:rtEvent** schema. Contiene una definizione degli eventi in tempo reale.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Questa tabella corrisponde a **nms:batchEvent** schema. Contiene la definizione degli eventi per batch.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Modulo NMAC {#nmac-module}

Questo insieme di tabelle è collegato al **Canale app mobile**, che consente di inviare notifiche personalizzate ai terminali iOS e Android tramite app. Per ulteriori informazioni, consulta [Informazioni sul canale app mobile](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Questa tabella corrisponde a **nms:mobileApp** schema. Contiene le applicazioni mobili definite in Adobe Campaign.
* **NmsAppSubscription**: Questa tabella corrisponde a **nms:appSubscription** schema. Contiene le informazioni degli abbonati relative a una o più applicazioni.
* **NmsAppSubscriptionRcp**: Questa tabella corrisponde a **nms:appSubscriptionRcp** schema. Consente di collegare i visitatori che si sono abbonati a un’applicazione alla tabella dei destinatari.
* **NmsExcludeLogAppSubRcp**: Questa tabella corrisponde a **nms:excludeLogAppSubRcp** schema.
* **NmsTrackingLogAppSubRcp**: Questa tabella corrisponde a **nms:trackingLogAppSubRcp** schema.
* **NmsBroadLogAppSubRcp**: Questa tabella corrisponde a **nms:wideLogAppSubRcp** schema.

## Modulo di social marketing {#social-marketing-module}

Questo insieme di tabelle è collegato al **Gestione dei social network** , che consente di interagire con clienti e potenziali clienti tramite Facebook e Twitter. Per ulteriori informazioni, consulta [Informazioni sul social marketing](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Questa tabella corrisponde a **nms:visitatore** schema. Contiene informazioni sui visitatori.
* **NmsVisitorSub**: Questa tabella corrisponde a **nms:visitorSub** schema. Consente di collegare un visitatore ai servizi a cui si è iscritto (Twitter o Facebook).
* **NmsFriendShipRel**: Questa tabella corrisponde a **nms:amiciziaRel** schema. Consente di collegare i visitatori ai loro amici nel contesto del servizio Facebook.
* **NmsVisitorInterestRel**: Questa tabella corrisponde a **nms:visitorInterestRel** schema. Ti consente di collegare i visitatori e i loro interessi.
* **NmsInterest**: Questa tabella corrisponde a **nms:interest** schema. Contiene l’elenco degli interessi di ogni visitatore.
