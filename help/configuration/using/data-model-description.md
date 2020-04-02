---
title: Descrizione del modello di dati Adobe Campaign Classic
description: Questo documento descrive il modello dati di Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707e16e9e493e175c70af606bf4568a9127cedb2

---


# Descrizione modello dati campagna{#data-model-description}

Adobe Campaign viene fornito con un modello dati predefinito. Questa sezione fornisce alcuni dettagli sulle tabelle integrate del modello dati di Adobe Campaign e sulla loro interazione.

Per accedere alla descrizione di ciascuna tabella, passare a **[!UICONTROL Admin > Configuration > Data schemas]**, selezionare una risorsa dall&#39;elenco e fare clic sulla **[!UICONTROL Documentation]** scheda.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>La struttura fisica e logica dei dati trasferiti nell&#39;applicazione è descritta in XML. Obbedisce a una grammatica specifica di Adobe Campaign, denominata schema. Per ulteriori informazioni sugli schemi di Adobe Campaign, consulta questa [sezione](../../configuration/using/about-schema-reference.md).

## Descrizione delle tabelle principali {#description-main-tables}

Adobe Campaign si basa su un database relazionale contenente tabelle collegate tra loro.

Il diagramma seguente mostra i join tra le principali tabelle aziendali del modello dati di Adobe Campaign con i campi principali per ciascuna tabella.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

Il modello dati di Adobe Campaign predefinito include le tabelle principali elencate di seguito.

### NmsRecipient {#NmsRecipient}

Questa tabella corrisponde allo schema **nms:destinatario** .

Si tratta della tabella predefinita utilizzata per i **destinatari delle consegne**. Di conseguenza, contiene le informazioni richieste per le consegne attraverso i vari canali:

* sEmail: indirizzo e-mail.
* iEmailFormat: formato preferenziale per le e-mail (1 per Testo, 2 per HTML e 0 per non definito).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity sono utilizzati per costruire l&#39;indirizzo postale (in conformità con lo standard XPZ 10-011 AFNOR dal maggio 1997).
* sPhone, sMobilePhone, sFax contengono rispettivamente i numeri di telefono, telefono cellulare e fax.
* iBlackList è il flag di rifiuto predefinito utilizzato per i profili (1 significa &quot;non iscritto&quot;, 0 in caso contrario).

Il campo iFolderId è la chiave esterna che collega il destinatario alla propria cartella di esecuzione. Per ulteriori informazioni, consulta [XtkFolder](#XtkFolder).

Il campo sCountryCode è il codice ISO alfa 2 3166-1 (2 caratteri) del paese associato al destinatario. Questo campo è in realtà una chiave esterna nella tabella di riferimento del paese (NmsCountry), che contiene le etichette del paese e altri dati del codice del paese. Se il paese non è popolato, il valore XX viene memorizzato (e viene utilizzato al posto di un record con ID zero).

Per ulteriori informazioni sulla tabella Destinatario, consulta questa [sezione](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Questa tabella corrisponde allo schema **nms:group** .

Consente di creare gruppi **statici di destinatari**. Esiste una relazione molti-a-molti tra i destinatari e i gruppi. Ad esempio, un destinatario può appartenere a diversi gruppi e un gruppo può contenere più destinatari. I gruppi possono essere creati manualmente, tramite un&#39;importazione o mediante il targeting delle consegne. I gruppi vengono spesso utilizzati come destinazioni di consegna. Nel campo è presente un indice univoco che rappresenta il nome interno del gruppo sName. Il gruppo è collegato a una cartella (la chiave è iFolderId). Per ulteriori informazioni, vedere [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

La tabella delle relazioni NmsRcpGrpRel contiene solo i due campi corrispondenti agli identificatori delle tabelle collegate iRecipientId e iGroupId.

### NmsService {#NmsService}

Questa tabella corrisponde allo schema **nms:service** .

I servizi sono entità simili ai gruppi (raggruppamenti di destinatari statici), con la differenza che circolano più informazioni e consentono una gestione semplice delle sottoscrizioni e degli annullamento delle sottoscrizioni tramite i moduli.

Nel campo è presente un indice univoco che rappresenta il nome interno del servizio sName. Il servizio è collegato a una cartella (la chiave è iFolderId). Per ulteriori informazioni, vedere [XtkFolder](#XtkFolder)). Infine, il campo iType specifica il canale di consegna del servizio (0 per e-mail, 1 per SMS, 2 per telefono, 3 per posta diretta e 4 per fax).

### NmsSubscription {#NmsSubscription}

Questa tabella corrisponde allo schema **nms:subscription** .

Consente di gestire le iscrizioni dei destinatari ai servizi di informazione.

### NmsSubHisto {#NmsSubHisto}

Questa tabella corrisponde allo schema **nms:subHisto** .

Se le iscrizioni vengono gestite utilizzando i moduli Web o l&#39;interfaccia dell&#39;applicazione, nella tabella NmsSubHisto vengono memorizzate tutte le sottoscrizioni e le sottoscrizioni. Il campo iAction specifica l’azione (0 per l’annullamento della sottoscrizione e 1 per la sottoscrizione) eseguita alla data memorizzata nel campo tsDate.

### NmsDelivery {#NmsDelivery}

Questa tabella corrisponde allo schema **nms:delivery** .

Ogni record in questa tabella rappresenta un&#39;azione **di** consegna o un modello **di** consegna. Contiene tutti i parametri necessari per eseguire le consegne (target, contenuto, ecc.). I registri di consegna (trasmissione) (NmsBroadLog) e gli URL di tracciamento associati (NmsTrackingUrl) vengono creati durante la fase di analisi (vedere di seguito per ulteriori dettagli su entrambe le tabelle).

Nel campo è presente un indice univoco che rappresenta il nome interno della consegna sInternalName o dello scenario. La consegna è collegata a una cartella di esecuzione (la chiave esterna è iFolderProcessId. Per ulteriori informazioni, vedere [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Contiene **tutte le cartelle della struttura** visibili nella scheda **Navigazione** della console.

Le cartelle vengono digitate: il valore del campo sModel specifica il tipo di dati che è possibile includere nella cartella. Questo campo consente inoltre alla console client di visualizzare correttamente i dati con i moduli corrispondenti. I possibili valori per questo campo sono definiti in navTree.

La struttura ad albero è gestita dai campi iParentId e iChildCount. Il campo sFullName fornisce il percorso completo della cartella nella struttura. Infine, nel campo è presente un indice univoco che rappresenta il nome interno della cartella sName.

## Consegna e monitoraggio {#delivery-and-tracking}

Questo insieme di tabelle è collegato al modulo **Consegna** , che consente di monitorare le consegne e eventuali problemi riscontrati durante l&#39;invio dei messaggi. Per ulteriori informazioni, consulta [Monitoraggio delle consegne](../../delivery/using/monitoring-a-delivery.md). Per ulteriori informazioni sul tracciamento, vedi [Tracciamento dei messaggi](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Questa tabella corrisponde allo schema **nms:wideLogMsg** . Si tratta di un&#39;estensione della tabella del registro di consegna.

## Gestione delle campagne {#campaign-management}

Questo insieme di tabelle è collegato al modulo Campagne **** marketing, che consente di definire, ottimizzare, eseguire e analizzare campagne di comunicazione e marketing. Per ulteriori informazioni, consulta [Informazioni sulle campagne](../../campaign/using/designing-marketing-campaigns.md)di marketing.

![](assets/data-model_campaign.png)

* **NmsOperation**: Questa tabella corrisponde allo schema **nms:operation** . Contiene i dati delle campagne di marketing.
* **NmsDeliveryOutline**: Questa tabella corrisponde allo schema **nms:deliveryOutline** . Contiene le proprietà estese della consegna (profilo di consegna).
* **NmsDlvOutlineItem**: Questa tabella corrisponde allo schema **nms:dlvOutlineItem** . Contiene gli articoli di un profilo di consegna.
* **NmsDeliveryCustomization**: Questa tabella corrisponde allo schema **nms:deliveryCustomization** . Contiene i campi di personalizzazione di una distribuzione.
* **NmsBudget**: Questa tabella corrisponde allo schema **nms:budget** . Contiene i dati di un budget per una campagna, un piano, un programma, un&#39;attività e/o consegne.
* **NmsDocument**: Questa tabella corrisponde allo schema **nms:document** . Contiene i documenti di marketing della campagna sotto forma di file (immagini, Excel o file Word, ecc.)
* **XtkWorkflow**: Questa tabella corrisponde allo schema **xtk:workflow** . Contiene il targeting delle campagne.
* **NmsTask**: Questa tabella corrisponde allo schema **nms:task** . Contiene la definizione di un&#39;attività di marketing.
* **NmsAsset**: Questa tabella corrisponde allo schema **nms:asset** . Contiene la definizione di una risorsa di marketing.

## Coerenza delle comunicazioni {#communication-consistency}

Questo insieme di tabelle è collegato al modulo **Campaign Optimization** , che consente di controllare, filtrare e monitorare l&#39;invio di consegne. Per ulteriori informazioni, consultate [Informazioni sulle tipologie di campagne](../../campaign/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Questa tabella corrisponde allo schema **nms:typologyRule** . Contiene le regole che si applicano alle consegne a seconda delle tipologie.
* **NmsType**: Questa tabella corrisponde allo schema **nms:typology** . Contiene l&#39;insieme di regole da applicare alle consegne che corrispondono alla tipologia.
* **NmsTypologyRuleRel**: Questa tabella corrisponde allo schema **nms:typologyRuleRel** . Contiene le relazioni tra le tipologie e le loro regole.
* **NmsVolumeLine**: Questa tabella corrisponde allo schema **nms:volumeLine** . Contiene la serie di linee di disponibilità delle regole di capacità.
* **NmsVolumeConsumed**: Questa tabella corrisponde allo schema **nms:volumeConsumed** . Contiene tutte le linee di consumo delle regole di capacità.

## Gestione delle risposte {#response-management}

Questo insieme di tabelle è collegato al modulo **Response Manager** , che consente di misurare il successo e la redditività delle campagne di marketing o delle proposte di offerta per tutti i canali di comunicazione. Per ulteriori informazioni, consultate [Informazioni su Gestione](../../campaign/using/about-response-manager.md)risposte.

![](assets/data-model_response.png)

### NmsRemaHypoeses {#NmsRemaHypothesis}

Questa tabella coincide con lo schema **nms:remaHypoeses** . Contiene la definizione dell&#39;ipotesi di misura.

Questa tabella contiene informazioni importanti archiviate in XML, tra cui:

**Contesto di esecuzione (informazioni memorizzate in XML)**

Il contesto di esecuzione popola le tabelle e i campi da prendere in considerazione per il calcolo delle misurazioni, vale a dire:
* Lo schema di memorizzazione del registro di reazione nms:remaMatchRcp.
* Schema della tabella delle transazioni (ad esempio, acquisti).
* Lo schema di query, che consente di definire la tabella iniziale delle condizioni di ipotesi.
* I collegamenti ai singoli, che consentono di identificare l&#39;individuo in base allo schema di query.
* Data transazione. Questo campo non è obbligatorio, ma si consiglia di utilizzarlo per limitare il perimetro di calcolo.
* Importo transazione: è un campo facoltativo per il calcolo automatico degli indicatori di reddito.

**Perimetro di ipotesi (informazioni memorizzate in XML)**

Il perimetro di ipotesi consiste nel filtraggio dell&#39;ipotesi in base alla tabella dello schema di query.

**Script di overload dell&#39;ipotesi (informazioni memorizzate in XML)**

Lo script di overload di ipotesi è un codice JavaScript che consente di sovraccaricare il contenuto dell&#39;ipotesi durante l&#39;esecuzione.

**Indicatori di misura**

I seguenti indicatori vengono aggiornati automaticamente durante l&#39;esecuzione dell&#39;ipotesi:

* Numero di reazioni: **iTransaction**. Numero di righe nella tabella dei registri di reazione.
* Numero di persone contattate: **iContactReact**. Numero distinto di contatti mirati nell&#39;ipotesi.
* Conteggio gruppi di controllo: **iProofReact**. Numero distinto di contatti di gruppi di controllo mirati nell&#39;ipotesi.
* Tasso di risposta contattato: **dContactReactRate**. Tasso di risposta dei contatti mirati nell&#39;ipotesi.
* Tasso di risposta del gruppo di controllo: **dProofReactRate**. Tasso di risposta del gruppo di controllo delle ipotesi.
* Entrate totali della popolazione contattata: **dContactReactTotalAmount**. Entrate totali dei contatti mirati nell&#39;ipotesi.
* Entrate medie del gruppo di controllo: **dContactReactAvgAmount**. Entrate medie dei contatti del gruppo di controllo mirato nell&#39;ipotesi.
* Entrate totali del gruppo di controllo: **dProofReactTotalAmount**. Entrate totali del gruppo di controllo delle ipotesi.
* Entrate medie del gruppo di controllo: **dProofReactAvgAmount**. Entrate medie del gruppo di controllo delle ipotesi.
* Margine totale per contatto: **dContactReactTotalMargin**. Margine totale per contatto mirato nell&#39;ipotesi.
* Margine medio per contatto: **dContactReactAvgMargin**. Margine medio per contatto mirato nell&#39;ipotesi.
* Margine totale del gruppo di controllo: **ProofReactTotalMargin**. Margine totale del gruppo di controllo oggetto dell&#39;ipotesi.
* Margine medio del gruppo di controllo: **ProofReactAvgMargin**. Margine medio del gruppo di controllo oggetto dell&#39;ipotesi.
* Entrate aggiuntive: **AdditionalAmount**. (Ricavi medi di contattati - Ricavi medi del gruppo di controllo) * Numero di contattati.
* Margine aggiuntivo: **AdditionalMargin**. (Margine medio di contattati - Margine medio del gruppo di controllo) / Numero di contattati.
* Costo medio per contatto (espressione SQL). Costo calcolato della consegna / Numero di contatti.
* ROI (espressione SQL). Costo calcolato della consegna / Margine totale della consegna contattata.
* ROI effettivo (espressione SQL). Costo calcolato della consegna/margine aggiuntivo.
* Significato: **iSignificativy** (espressione SQL). Contiene valori da 0 a 3 a seconda del significato della campagna.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Questa tabella corrisponde allo schema **nms:remaMatchRcp** .

Contiene un record che rappresenta la reazione di un individuo a una data ipotesi. Questi record sono stati creati durante l&#39;esecuzione delle ipotesi.

## Simulazione e consegna {#simulation-and-delivery}

Questo insieme di tabelle è collegato al modulo **Simulazione** , che consente di verificare la distribuzione delle offerte appartenenti a una categoria o a un ambiente prima di inviare la proposta ai destinatari. Per ulteriori informazioni, consultate [Informazioni sulla simulazione](../../interaction/using/about-offers-simulation.md)delle offerte.

![](assets/data-model_simulation.png)

* **NmsSimulation**: Questa tabella corrisponde allo schema **nms:simulazione** . Rappresenta una simulazione per un insieme di consegne o offerte su una determinata popolazione.
* **NmsDlvSimulationRel**: Questa tabella corrisponde allo schema **nms:dlvSimulationRel** . Contiene l&#39;elenco delle consegne preso in considerazione nella simulazione. L&#39;ambito della simulazione è memorizzato in XML.
* **NmsOfferSimulationRel**: Questa tabella corrisponde allo schema **nms:offerSimulationRel** . Consente di collegare una simulazione a un’offerta.

## Modulo di interazione {#interaction-module}

Questo insieme di tabelle è collegato al modulo **Interazione** , che permette di rispondere in tempo reale durante un&#39;interazione con un determinato contatto, rendendogli una o più offerte adattate. Per ulteriori informazioni, consulta Gestione delle [interazioni e delle](../../interaction/using/interaction-and-offer-management.md)offerte.

* **NmsOffer**: Questa tabella corrisponde allo schema **nms:offer** . Contiene la definizione di ogni offerta di marketing.
* **NmsPropositionRcp**: Questa tabella corrisponde allo schema **nms:propositionRcp** . Contiene il registro multicanale delle proposte di marketing inviate a ciascun utente. Il record viene creato quando una proposta viene preparata o effettivamente fatta a un individuo.
* **NmsOfferSpace**: Questa tabella corrisponde allo schema **nms:offerSpace** . Contiene la definizione delle posizioni in cui vengono presentate le proposte.
* **NmsOfferContext**: Questa tabella corrisponde allo schema **nms:offerContext** . Contiene criteri aggiuntivi per l&#39;applicabilità della proposta e per la definizione della formula di calcolo del peso.
* **NmsOfferView**: Questa tabella corrisponde a **nms:offerView**. Contiene le rappresentazioni delle offerte.
* **NmsOfferCategory**: Questa tabella corrisponde a **nms:offerCategory**. Contiene le categorie delle offerte.
* **NmsOfferEnv**: Questa tabella corrisponde a **nms:offerEnv**. Contiene gli ambienti delle offerte.

## Modulo Centro messaggi {#message-center-module}

Il seguente insieme di tabelle è collegato al modulo **Transactional messaging** (Message Center), che consente di gestire le comunicazioni singole ed univoche inviate a un utente e generate da eventi attivati dai sistemi informativi. Per ulteriori informazioni, vedere [Informazioni sui messaggi](../../message-center/using/about-transactional-messaging.md)transazionali.

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Questa tabella corrisponde allo schema **nms:rtEvent** . Contiene una definizione di eventi in tempo reale.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Questa tabella corrisponde allo schema **nms:batchEvent** . Contiene la definizione degli eventi per batch.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Modulo NMAC {#nmac-module}

Questo insieme di tabelle è collegato al canale **app** mobile, che consente di inviare notifiche personalizzate ai terminali iOS e Android tramite app. Per ulteriori informazioni, consulta [Informazioni sul canale](../../delivery/using/about-mobile-app-channel.md)delle app mobili.

* **NmsMobileApp**: Questa tabella corrisponde allo schema **nms:mobileApp** . Contiene le applicazioni mobili definite in Adobe Campaign.
* **NmsAppSubscription**: Questa tabella corrisponde allo schema **nms:appSubscription** . Contiene le informazioni degli abbonati relative a una o più applicazioni.
* **NmsAppSubscriptionRcp**: Questa tabella corrisponde allo schema **nms:appSubscriptionRcp** . Consente di collegare i visitatori che hanno effettuato l’iscrizione a un’applicazione alla tabella dei destinatari.
* **NmsExcludeLogAppSubRcp**: Questa tabella corrisponde allo schema **nms:excludeLogAppSubRcp** .
* **NmsTrackingLogAppSubRcp**: Questa tabella corrisponde allo schema **nms:trackingLogAppSubRcp** .
* **NmsBroadLogAppSubRcp**: Questa tabella corrisponde allo schema **nms:wideLogAppSubRcp** .

## Modulo di marketing social {#social-marketing-module}

Questo insieme di tabelle è collegato al modulo **Gestione dei social network** , che consente di interagire con clienti e potenziali clienti tramite Facebook e Twitter. Per ulteriori informazioni, consultate [Informazioni sul marketing](../../social/using/about-social-marketing.md)social.

![](assets/data-model_social.png)

* **NmsVisitor**: Questa tabella corrisponde allo schema **nms:visitor** . Contiene informazioni sui visitatori.
* **NmsVisitorSub**: Questa tabella corrisponde allo schema **nms:visitorSub** . Consente di collegare un visitatore ai servizi a cui si è iscritto (Twitter o Facebook).
* **NmsFriendShipRel**: Questa tabella corrisponde allo schema **nms:amicshipRel** . Consente di collegare i visitatori ai loro amici nel contesto del servizio Facebook.
* **NmsVisitorInterestRel**: Questa tabella corrisponde allo schema **nms:visitorInterestRel** . Consente di collegare i visitatori e i loro interessi.
* **NmsInterest**: Questa tabella corrisponde allo schema **nms:interest** . Contiene l&#39;elenco degli interessi di ogni visitatore.