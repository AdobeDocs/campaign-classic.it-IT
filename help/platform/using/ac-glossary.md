---
product: campaign
title: Glossario di Adobe Campaign
description: Glossario di Adobe Campaign
feature: Overview
role: User, Developer
level: Beginner
exl-id: 81f207a0-bb72-450b-abe4-0b229b6b1f3a
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '6197'
ht-degree: 2%

---

# Glossario di Adobe Campaign{#ac-glossary}

Di seguito è riportata la definizione dei termini e dei concetti chiave in Adobe Campaign, con i collegamenti alla relativa documentazione. Fai clic su un termine per visualizzarne la definizione.

## A - D{#sec-1}

+++**Test A/B**

Il test A/B è una funzionalità che consente all’utente di definire due o tre varianti di e-mail: ogni variante viene inviata ai campioni di popolazione per determinare quale ha il risultato migliore. Una volta determinata, la variante vincente viene quindi inviata alla popolazione rimanente.

Ulteriori informazioni sui [test A/B](../../delivery/using/get-started-a-b-testing.md).
+++

+++**Gestione degli accessi**

La gestione degli accessi consente agli amministratori di assegnare accesso e autorizzazioni agli utenti di Adobe Campaign. Le autorizzazioni includono la possibilità di visualizzare e/o utilizzare le funzioni di Adobe Campaign, ad esempio l’esecuzione di flussi di lavoro, la definizione di schemi e la gestione dei tipi di pubblico.

Ulteriori informazioni su [Gestione degli accessi](access-management.md).
+++

<!--
+++**ACS Connector**

ACS Connector (Prime Offering) bridges Adobe Campaign v7 and Adobe Campaign Standard. It is an integrated feature in Campaign v7 that automatically replicates data to Campaign Standard, uniting the best of both applications. Campaign v7 has advanced tools to manage the primary marketing database. The data replication from Campaign v7 allows Campaign Standard to leverage the rich data in a user-friendly environment. 

Learn more about [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++
-->

+++**Attività**

Un’attività è un elemento della palette che viene aggiunto a un flusso di lavoro per definire una funzionalità di esecuzione. L’attività è un contenitore che esegue un’attività. In un flusso di lavoro, una determinata attività può produrre più attività, in particolare quando vi è un ciclo continuo o azioni ricorrenti (periodiche).

Ulteriori informazioni sulle attività del flusso di lavoro sono disponibili nella [documentazione di Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities
.html){target="_blank"}.
+++

+++**Profilo attivo**

I profili sono considerati attivi se sono stati targetizzati o se è avvenuta una comunicazione con essi negli ultimi 12 mesi tramite qualsiasi canale. In base al contratto, a ciascuna istanza di Campaign viene fornito un numero specifico di profili attivi conteggiati a scopo di fatturazione.

Ulteriori informazioni su [Profili attivi](../../platform/using/about-profiles.md#active-profiles).
+++

+++**Attività flusso di lavoro di approvazione**

*Contesto: marketing distribuito della campagna*

L’attività Approvazione locale è un’attività del flusso di lavoro utilizzata per impostare un processo di approvazione della consegna prima che i messaggi vengano inviati.

+++

+++**Pubblico**

Un pubblico è il set risultante di profili che soddisfano i criteri di una definizione di filtro, in base a regole e attributi.

Ulteriori informazioni sui tipi di pubblico sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=it){target="_blank"}.
+++

+++**Audit trail**

Audit trail acquisisce in tempo reale un elenco completo delle azioni e degli eventi che si verificano all’interno dell’istanza Adobe Campaign. Include una modalità autonoma di accedere alla cronologia dei dati per poter rispondere a domande quali: cosa è successo ai flussi di lavoro e chi li ha aggiornati per ultimo o cosa hanno fatto gli utenti nell’istanza.

Ulteriori informazioni su [Audit trail](../../production/using/audit-trail.md).
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**Modalità batch**

*Contesto: interazione campagna*

Nel contesto dell’interazione con Campaign, la modalità batch consente al motore di offerta di selezionare l’offerta o le offerte migliori per un set di contatti. Le regole di idoneità/definizione delle priorità vengono applicate a tutti i contatti del set.

Ulteriori informazioni sull&#39;[interazione](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Campagna**

Campaign è un’interfaccia per coordinare, definire ed eseguire campagne di marketing. Le campagne possono contenere uno o più flussi di lavoro, consegne, documenti e altri punti di dati correlati in un’unica interfaccia di facile utilizzo.

Ulteriori informazioni sulle campagne nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html){target=_blank}.
+++

<!--
-----NOT USEFUL HERE?-----
+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++
-->

+++**Canale**

Un canale è un mezzo attraverso il quale viene inviata una comunicazione. I canali incorporati in Adobe Campaign sono e-mail, SMS, direct mailing, notifiche push, LINE e X (precedentemente noti come Twitter). I canali personalizzati possono essere implementati per esigenze di canale non standard.

Ulteriori informazioni su [Canali](../../delivery/using/communication-channels.md).
+++

+++**Console client**

La console client di Campaign è un client avanzato che consente di connettersi ai server applicazioni di Campaign. L&#39;applicazione eseguibile della console client (con estensione exe) è installata in un computer con un sistema operativo Microsoft Windows. La console client di Campaign centralizza tutte le funzionalità e le impostazioni.

Ulteriori informazioni su [Console client](../../platform/using/adobe-campaign-workspace.md).
+++

+++**Approvazione dei contenuti**

L’approvazione del contenuto è il processo in base al quale un operatore o un gruppo di operatori separato approva il contenuto di una consegna prima che possa essere inviata.

Ulteriori informazioni sull&#39;approvazione dei contenuti nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html?lang=it){target="_blank"}.

+++

+++**Gruppi di controllo**

Utilizza i gruppi di controllo per misurare l’impatto delle campagne escludendo parte delle relative audience. Gli operatori possono confrontare il comportamento della popolazione target che ha ricevuto il messaggio con il comportamento dei contatti non mirati. In base ai registri di invio, gli operatori possono anche eseguire il targeting di un gruppo di controllo in campagne future.

Ulteriori informazioni sui gruppi di controllo sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html#add-a-control-group){target="_blank"}.
+++

+++**Pannello di controllo**

Il Pannello di controllo Campaign aiuta gli amministratori di prodotto di Adobe Campaign ad aumentare l’efficienza del loro lavoro, consentendo loro di gestire le impostazioni e monitorare gli utilizzi per ciascuna delle loro istanze. L’interfaccia intuitiva consente di monitorare facilmente l’utilizzo delle risorse chiave, nonché di eseguire attività amministrative come l’elenco consentiti di indirizzi IP, il monitoraggio dell’archiviazione SFTP, la gestione delle chiavi e altro ancora.

Ulteriori informazioni su [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it).
+++

+++**Cubi**

*Contesto: analisi di marketing*

Cube è uno strumento di esplorazione dei dati intuitivo di Adobe Campaign che consente agli utenti di creare e condividere rapporti dinamici.

Ulteriori informazioni su [Cubi](../../reporting/using/ac-cubes.md).
+++

+++**Risorse personalizzate**

Adobe Campaign viene fornito con un modello dati predefinito, in cui i tipi di dati vengono definiti tramite l’installazione di vari pacchetti. Gli operatori possono arricchire il modello dati fornito estendendo le risorse per aggiungere campi personalizzati o tabelle personalizzate, ad esempio tabelle di transazioni o di prodotti.

Ulteriori informazioni sulle [risorse personalizzate](../../configuration/using/about-schema-edition.md).
+++

+++**Modello dati**

Il modello dati di Campaign è un set di schemi che definiscono i tipi di dati e le relative relazioni (collegamenti). Il modello dati è una definizione astratta implementata fisicamente con un database che contiene i dati effettivi.

Ulteriori informazioni su [Modello dati](../../configuration/using/about-data-model.md).
+++

+++**Flusso di lavoro di pulizia del database**

Il flusso di lavoro di pulizia del database elimina i dati obsoleti per evitare la crescita esponenziale del database. Il flusso di lavoro viene attivato automaticamente senza l’intervento dell’utente.

Ulteriori informazioni sul [flusso di lavoro di pulizia del database](../../production/using/database-cleanup-workflow.md).
+++

<!--
----UNCLEAR----
+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The "Per-Dedicated Server" designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++
-->

+++**Deliverability**

*Contesto: recapito e-mail*

Il recapito messaggi consente di misurare il successo delle campagne che raggiungono la casella in entrata dei destinatari senza che vengano saltati o contrassegnati come spam. Più precisamente, il recapito messaggi e-mail si riferisce all’insieme di caratteristiche che determinano la capacità di un messaggio di raggiungere la sua destinazione, tramite un indirizzo e-mail personale, in un breve periodo di tempo e con la qualità prevista in termini di contenuto e formato.

Ulteriori informazioni su [Recapito messaggi](../../delivery/using/about-deliverability.md).
+++

+++**Consegna**

Una consegna è un elemento di comunicazione marketing specifico che viene inviato a un pubblico su un canale specifico (e-mail, SMS, notifica push, ecc.). Noto anche come &quot;tocco&quot; nella terminologia di marketing.

Ulteriori informazioni su [Consegne](../../delivery/using/communication-channels.md).
+++

+++**Analisi della consegna**

L’analisi della consegna è la preparazione della consegna. Questo processo combina il contenuto con i dati del profilo del destinatario per produrre l’e-mail personalizzata che il destinatario riceve. La logica di analisi della consegna può escludere i destinatari dal target o interrompere completamente la consegna, in base alla logica definita. Questo processo include anche la valutazione della logica del contenuto dinamico e l’inserimento di offerte specifiche per il singolo profilo del destinatario.

Ulteriori informazioni sull&#39;analisi della consegna sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html){target="_blank"}.
+++

+++**Registri di consegna**

I registri di consegna contengono informazioni generate durante l’invio di un messaggio. Questi registri mostrano i dettagli dell’invio, il messaggio preparato, ignorato, inviato o non riuscito. Sono accessibili direttamente dal dashboard di consegna.

Ulteriori informazioni sui [registri di consegna](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

<!--
----STRANGE IN DOCS?----
+++**Delivery fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++
-->

+++**Profilo di consegna**

*Contesto: Direct Mail*

Una struttura di consegna è un set strutturato di elementi (documenti, negozi, coupon promozionali, ecc.) creati dall’azienda e per una particolare campagna. Viene utilizzato nel contesto delle consegne di direct mailing.

Ulteriori informazioni su [Direct mailing](../../delivery/using/about-direct-mail-channel.md).
+++

+++**distribuzione guidata**

La procedura guidata di distribuzione definisce i parametri dell’istanza Campaign, ad esempio lo spazio dei nomi predefinito, la pianificazione della pulizia del database, i periodi di conservazione dei dati e altre impostazioni tecniche.

Ulteriori informazioni sulla [distribuzione guidata](../../installation/using/deploying-an-instance.md#deployment-assistant).
+++

+++**Analisi descrittiva**

L’analisi descrittiva è uno strumento di reporting sensibile al contesto che può essere utilizzato per esaminare i dati nella tabella di lavoro di un flusso di lavoro, i dati selezionati in una cartella o per eseguire analisi approfondite sulle destinazioni e sulle esclusioni delle consegne selezionate.

Ulteriori informazioni su [Analisi descrittiva](../../reporting/using/about-descriptive-analysis.md)
+++

+++**Marketing distribuito**

*Contesto: Marketing distribuito*

Il componente aggiuntivo Marketing distribuito offre agli operatori di campagne uno spazio di lavoro collaborativo per l’implementazione di campagne tra entità centrali (sedi centrali, dipartimenti di marketing, ecc.) ed entità locali (punti vendita, agenzie regionali, ecc.). Questa cooperazione si basa su un&#39;area di lavoro condivisa nota come **elenco di pacchetti Campaign**, in cui i modelli e le istanze di campagna creati centralmente vengono offerti alle entità locali.

Ulteriori informazioni sul Marketing distribuito sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=it){target="_blank"}.
+++

+++**Distribuzione dei valori**

La Distribuzione di valori è uno strumento che mostra la distribuzione dei valori per un attributo di schema attualmente esistente nel database. Questo consente di determinare quali valori sono disponibili, i relativi conteggi e percentuali, nonché di evitare problemi di utilizzo delle maiuscole e dell’ortografia dei valori durante la creazione di una query o di un’espressione.

Ulteriori informazioni su [Distribuzione dei valori](../../platform/using/about-queries-in-campaign.md)
+++

+++**Delega del dominio**

La configurazione del sottodominio ti consente di configurare una sottosezione del dominio (tecnicamente una &quot;zona DNS&quot;) per l’utilizzo con Adobe Campaign.
La delega del dominio consente ad Adobe di controllare e mantenere tutti gli aspetti del DNS necessari per la distribuzione, il rendering e il tracciamento delle campagne e-mail.

Ulteriori informazioni sulla [delega del dominio](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=it)
+++

## E - H {#sec-2}

<!--
----DEPRECATED------>
+++**E4X**

E4X è la versione di JavaScript utilizzata in Adobe Campaign Classic. A volte chiamato ECMAScript, è un&#39;estensione di JavaScript che consente la combinazione di Javascript e primitive XML nello stesso codice. Si noti che E4X è classificato come lingua obsoleta.
+++


+++**Regole di idoneità**

*Contesto: interazione campagna*

Le regole di idoneità sono vincoli applicati a un ambiente, una categoria o un’offerta per quanto riguarda il periodo di validità, l’obiettivo e il peso. Consentono agli operatori di garantire che un’offerta sia in linea con il contatto mirato. Nell’ambiente dell’offerta, le regole di idoneità includono le regole di presentazione applicate alle offerte e ai destinatari a cui eseguire il targeting. Nella categoria, le regole di idoneità consentono agli operatori di limitare la validità della categoria nel tempo, definire i temi dell’applicazione e determinare i destinatari da targetizzare. Possono inoltre definire un peso moltiplicatore per un determinato periodo di tempo. Questo consente agli operatori di condividere le regole per le offerte in altre categorie, semplificandone così la gestione. In un’offerta, le regole di idoneità consentono agli operatori di limitare la validità delle offerte in tempo utile e di determinare i destinatari a cui rivolgersi.

Ulteriori informazioni sulle [regole di idoneità](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Offerta idonea**

*Contesto: interazione campagna*

Un’offerta idonea è un’offerta che soddisfa i vincoli definiti a monte e che può essere offerta in modo coerente a un target.

Ulteriori informazioni sull&#39;[interazione](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Invia e-mail a Ccn**

La funzionalità Ccn e-mail invia una copia esatta in formato EML di un’e-mail consegnata corrispondente, che viene salvata in un indirizzo e-mail Ccn dedicato in cui le e-mail possono essere elaborate e archiviate dal mittente in un sistema esterno.

Ulteriori informazioni sul campo Ccn e-mail sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email-bcc.html){target="_blank"}.
+++

<!--
-----STRANGE FOR DOCS?----
+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++
-->

<!--
-----USEFUL FOR DOCS?----
+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++
-->

+++**Attività di arricchimento**

L’attività Enrichment è un’attività avanzata del flusso di lavoro che consente agli operatori di arricchire i dati della tabella di lavoro generati che verranno elaborati nel flusso di lavoro. Questa attività viene generalmente utilizzata dopo attività di targeting o dopo l’importazione di un file e prima di attività che utilizzano dati oggetto di targeting. Gli arricchimenti possono trasformare i dati di transizione in entrata e configurare l’attività in modo da completare la transizione in uscita con dati migliorati. Consente all’operatore di combinare dati da più set di dati o di creare collegamenti a una risorsa temporanea.

Ulteriori informazioni sull&#39;attività Enrichment sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}.
+++

+++**Enumerazioni**

Un’enumerazione è un tipo di dati definito negli schemi o a livello di Platform che definisce i valori di input validi per un campo. Le enumerazioni vengono visualizzate nell’interfaccia utente e nei generatori di query come elenco a discesa.

Scopri come **utilizzare le enumerazioni** nella [documentazione di Adobe Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.
+++

+++**Visualizzazione Esplora risorse**

La visualizzazione Esplora risorse è una visualizzazione gerarchica delle cartelle che contengono gli artefatti e i dati di Adobe Campaign. Tieni presente che il sistema di cartelle in Adobe Campaign non funziona come una visualizzazione ad albero tipica, in quanto ogni cartella contiene dati di un tipo specifico, ad esempio Consegne, Flussi di lavoro o Offerte.


Ulteriori informazioni sull&#39;interfaccia utente di Campaign nella [documentazione di Adobe Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Account esterni**

Gli account esterni sono punti di ingresso e di uscita del prodotto per la connessione ad altri ambienti e tecnologie. Gli account esterni definiscono i parametri di connessione utilizzati dal prodotto per inviare o ricevere dati da altre origini. I tipi di account esterni tipici sono le connessioni per i siti SFTP, le telecomunicazioni per supportare l’invio di SMS, le cassette postali per l’elaborazione dei mancati recapiti o le connessioni a database esterni.

Ulteriori informazioni su [Account esterni](../../installation/using/external-accounts.md).
+++

+++**Gestione dell&#39;affaticamento**

*Contesto: ottimizzazione campagna*

La gestione dell’eccesso consente di controllare la frequenza e la quantità di messaggi per evitare un’eccessiva sollecitazione dei destinatari e viene spesso applicata utilizzando una regola di tipologia.

Ulteriori informazioni sulla gestione dell&#39;eccesso sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/pressure-rules.html?lang=it){target="_blank"}.
+++

+++**Federated Data Access (FDA)**

Federated Data Access supporta l’estensione del modello dati client per includere un database di terze parti. Rileva automaticamente la struttura delle tabelle di destinazione e utilizza i dati provenienti dalle origini SQL. Puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

Ulteriori informazioni su [Federated Data Access](../../installation/using/about-fda.md).
+++

+++**Approvazione estrazione file**

*Contesto: Direct Mail*

L’approvazione dell’estrazione del file è il processo in base al quale un operatore o un gruppo di operatori separato approva il contenuto e la configurazione di un file estratto prima che venga inviato a un fornitore esterno, ad esempio per una consegna direct mailing.

Per ulteriori informazioni sull&#39;approvazione dell&#39;estrazione dei file, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/direct-mail.html#validating){target="_blank"}.
+++

+++**Dimensione filtro**

La dimensione di filtro è lo schema che contiene i dati o gli attributi utilizzati da una query per filtrare le righe desiderate. Lo schema della dimensione di filtro deve essere collegato direttamente alla dimensione di targeting definita per consentire ad Adobe Campaign di attraversare il database join e restituire le righe dei partecipanti.

Ulteriori informazioni sul filtro delle dimensioni sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html?lang=it#targeting-and-filtering-dimensions){target="_blank"}.
+++

+++**Cartella**

Una cartella è un elemento di visualizzazione di Esplora risorse che contiene record di database di un tipo di dati specifico. L&#39;eccezione è rappresentata dal tipo di cartella Generic utilizzato come elemento organizzativo e che non contiene dati, ma solo altre cartelle.

Ulteriori informazioni sull&#39;interfaccia utente di Campaign nella [documentazione di Adobe Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Visualizzazione cartella**

La visualizzazione Cartella è uno speciale tipo di cartella di Explorer utilizzato per visualizzare tutti i record di un tipo di dati selezionato, indipendentemente dalla cartella a cui appartiene. Le visualizzazioni cartelle vengono utilizzate come strumento amministrativo per gestire i dati partizionati o i dati distribuiti tra più cartelle.

Ulteriori informazioni sull&#39;interfaccia utente di Campaign nella [documentazione di Adobe Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.
+++

+++**Forms**

Forms definisce la rappresentazione dell’interfaccia per un tipo di schema specifico. Forms è lo strumento utilizzato per creare e modificare facilmente elementi di dati nel prodotto, ad esempio Destinatari, Consegne e Campagne. Tutti gli elementi dell’interfaccia in Adobe Campaign vengono creati nel prodotto stesso utilizzando Forms. I moduli sono facoltativi e non tutti gli schemi dispongono di moduli.

Ulteriori informazioni su [Forms](../../configuration/using/identifying-a-form.md).
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**Mappa di calore**

Campaign Heatmap è una tabella che mostra le informazioni sull’esecuzione del flusso di lavoro per un periodo di 24 ore. Visualizza la distribuzione dei flussi di lavoro nel periodo per ora e per intervalli di 5 minuti. La mappa di calore viene utilizzata per valutare il carico del server e determinare le attività del flusso di lavoro che consumano più risorse.

Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/heatmap.html?lang=it){target="_blank"}.
+++

+++**Distribuzione ibrida**

La distribuzione ibrida è una combinazione di servizi on-demand e software on-premise distribuiti per funzionare insieme.

Ulteriori informazioni sulla [distribuzione ibrida](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**Modalità di identificazione**

*Contesto: interazione campagna*

La modalità di identificazione Si riferisce allo stato di un contatto. Può essere esplicito, implicito o anonimo.

* **explicit**: il contatto è identificato dopo il suo accesso all&#39;interfaccia di canale.
* **implicit**: il contatto è stato identificato da un cookie (permanente o sessione). Può essere elaborato come contatto anonimo o identificato.
* **anonimo**: impossibile identificare il contatto.

Ulteriori informazioni sull&#39;[interazione](../../interaction/using/interaction-and-offer-management.md).
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery's recipients. The insertion of the images based on an emails system's "download images" functionality is what generates an "open" entry in Campaign's tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**Interazione in entrata**

*Contesto: interazione campagna*

Un’interazione in entrata è un’interazione successiva a una chiamata in entrata generata dall’azione di un contatto in un canale, ad esempio web, call center o mobile. Questo tipo di interazione viene generalmente elaborato in modalità unitaria (ovvero per destinatario).

Ulteriori informazioni sull&#39;[interazione in entrata](../../interaction/using/about-inbound-channels.md).
+++

+++**Rendering della casella in entrata**

Il rendering della casella in entrata è la generazione di anteprime e-mail che garantisce che il messaggio venga visualizzato ai destinatari in modo ottimale su diversi client web, web mail e dispositivi. Adobe Campaign sfrutta Litmus, che consente ai creatori di contenuti e-mail di visualizzare in anteprima il contenuto dei messaggi in oltre 70 renderer e-mail, come la casella in entrata Gmail o il client Apple Mail.

Ulteriori informazioni sul rendering di [Posta in arrivo](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**Impostazioni istanza**

Le impostazioni delle istanze sono dettagli di configurazione di un’istanza Adobe Campaign. Queste impostazioni sono definite nella procedura guidata di distribuzione (Strumenti>Avanzate>procedura guidata di distribuzione) o nei file di configurazione del server e/o dell&#39;istanza.

Ulteriori informazioni sulle [Impostazioni istanza](../../installation/using/about-initial-configuration.md).

+++

+++**Processi (importazione ed esportazione)**

I processi sono gestiti da un sistema di assistenza che semplifica l’importazione e l’esportazione di dati da e verso il prodotto. I processi utilizzano il sistema di modelli per semplicità e coerenza e possono essere definiti per l’esecuzione in base a una pianificazione.

Ulteriori informazioni sui [processi di importazione ed esportazione](../../platform/using/get-started-data-import-export.md).
+++

+++**Elenchi**

Un elenco è un set di dati statico. Gli elenchi sono tipi di pubblico o segmenti che vengono importati in Campaign da altre origini (Audience Manager, Experience Platform, database, ecc.) e sono visualizzati nell’interfaccia come Elenchi importati.

Ulteriori informazioni su [Elenchi](../../platform/using/creating-and-managing-lists.md).
+++

+++**Cache locale**

La cache locale è l&#39;informazione memorizzata localmente nel computer dell&#39;operatore. Le informazioni memorizzate nella cache vengono utilizzate dalla console per ridurre il traffico necessario verso il server e migliorare le prestazioni. La cancellazione periodica della cache locale (nel menu File) aggiorna le informazioni memorizzate e migliora le prestazioni e la stabilità.

Ulteriori informazioni su [Cache locale](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**Gestione risorse marketing (MRM)**

*Contesto: Gestione risorse marketing (MRM)*

Il modulo **Gestione risorse di marketing (MRM)** in Adobe Campaign consente di controllare le azioni di marketing in modalità collaborativa fornendo una gestione completa e il tracciamento in tempo reale delle attività, dei budget e delle risorse di marketing coinvolte. Gli operatori Adobe Campaign possono coordinare le loro azioni e approvare l’avanzamento in tutte le fasi tramite processi di convalida completi e strumenti di tracciamento appropriati: reporting, tracciamento delle approvazioni, notifiche, forum di discussione, ecc.

Ulteriori informazioni su MRM sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=it){target="_blank"}.
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**Diritti denominati**

I diritti di accesso granulari al database utilizzati per definire l&#39;accesso e i privilegi del gruppo di operatori (ruoli). I diritti denominati vengono compilati durante l’installazione del prodotto e importando vari pacchetti che definiscono funzionalità specifiche dello strumento. È possibile creare diritti denominati personalizzati per supportare i requisiti aziendali dei clienti.

Ulteriori informazioni su [Diritti denominati](../../platform/using/access-management-named-rights.md).
+++

+++**Spazio dei nomi**

Lo spazio dei nomi è una partizione che separa i tipi di dati del cliente dai tipi di dati nativi di Adobe Campaign nel modello di dati. Utilizzato anche per facilitare la migrazione delle definizioni da un’istanza all’altra, ad esempio per spostare uno schema o un modello dall’istanza Sviluppo all’istanza Produzione.

Ulteriori informazioni su [Spazio dei nomi](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

<!--
----generic, not specific to campaign----
+++**Navigation bar**

The navigation bar is the navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++
-->

+++**Struttura di navigazione**

La struttura di navigazione è la navigazione principale nella vista Esplora di Adobe Campaign. La struttura di spostamento funziona come un browser di file, ad esempio Esplora risorse. Le cartelle possono contenere sottocartelle. Selezionando un nodo viene visualizzata la vista corrispondente al nodo. La vista visualizzata è un elenco associato a uno schema e un modulo di input per modificare la riga selezionata. È possibile personalizzare la struttura di navigazione e impostare le autorizzazioni per le cartelle.

Ulteriori informazioni sull&#39;interfaccia utente di Campaign nella [documentazione di Adobe Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Obiettivi**

*Contesto: Gestione risorse marketing (MRM)*

All’interno della campagna, del programma o del piano, gli operatori possono indicare un elenco di obiettivi. Si tratta di valori quantificati da raggiungere. Al termine della campagna, del programma o del piano, il modulo MRM consente agli operatori di confrontare gli obiettivi e i risultati in report dedicati.

Ulteriori informazioni sugli obiettivi nella [documentazione di Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/mrm/creating-and-managing-tasks.html#expenses-and-revenues){target=_blank}.
+++

+++**Catalogo offerte**

*Contesto: interazione campagna*

Un catalogo di offerte è un set di offerte definite in Adobe Campaign che possono essere selezionate durante un’interazione. Il catalogo è organizzato gerarchicamente e ogni nodo corrisponde a una categoria.

Ulteriori informazioni su [Catalogo offerte](../../interaction/using/offer-catalog-overview.md).
+++

+++**Contatto offerta**

*Contesto: interazione campagna*

Un contatto dell’offerta è un contatto di un’interazione in entrata. Durante l’elaborazione delle chiamate al motore, il contatto è associato a una dimensione di targeting. I contatti anonimi non identificati vengono attribuiti alla dimensione di targeting dei visitatori. Esistono due tipi di contatti, identificati e anonimi:

* **Contatto identificato**: un contatto che è stato identificato volontariamente sul canale. Nelle interazioni in uscita, il contatto viene identificato automaticamente.
* **Contatto anonimo**: un contatto che non si è abbonato volontariamente tramite il canale ma che può essere identificato implicitamente tramite un cookie. Questa terminologia viene utilizzata solo per le interazioni in ingresso.

Ulteriori informazioni sull&#39;[interazione](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Ambiente di progettazione dell&#39;offerta**

*Contesto: interazione campagna*

L&#39;ambiente di progettazione **dell&#39;offerta** è l&#39;ambiente in cui gli operatori creano le offerte, definiscono le regole di tipologia e selezionano lo schema di destinazione delle offerte. Anche la tabella per l’archiviazione delle proposte di offerta generate è definita dall’ambiente. Per impostazione predefinita, il componente aggiuntivo Interaction è fornito con un ambiente **Design** e un ambiente **Live** collegati. Entrambi gli ambienti sono preconfigurati per la destinazione della tabella dei destinatari incorporata.

Ulteriori informazioni su [Ambienti di Offer Design](../../interaction/using/fundamental-principles.md).
+++

+++**Arbitraggio del motore di offerta**

*Contesto: interazione campagna*

Il motore di offerta seleziona le offerte che verranno visualizzate in un ambiente (offerte idonee). Il principio di arbitraggio classifica le offerte per priorità in base ai criteri definiti nelle categorie e nelle offerte.

Ulteriori informazioni sull&#39;[interazione](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Eliminazione del motore di offerta**

*Contesto: interazione campagna*

L’eliminazione del motore di offerta è il processo di eliminazione delle offerte non idonee alla selezione. Eseguito prima del passaggio di arbitraggio del motore di offerta.

Ulteriori informazioni sull&#39;[interazione](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Ambiente offerta**

*Contesto: interazione campagna*

L’ambiente dell’offerta è la cartella principale che definisce il catalogo delle offerte, gli spazi disponibili e i filtri predefiniti dell’ambiente. Gli operatori devono creare un ambiente per ogni dimensione di targeting. Esistono due tipi di ambienti di offerta: Progettazione e Live.

Ulteriori informazioni su [Ambienti di offerta](../../interaction/using/fundamental-principles.md).
+++

+++**Ambiente live dell&#39;offerta**

*Contesto: interazione campagna*

L&#39;ambiente di Offer Live è collegato a un **ambiente di progettazione** di Campaign. Contiene offerte di sola lettura il cui contenuto e idoneità sono stati approvati tramite l&#39;**ambiente di progettazione**. Possono essere selezionati per la presentazione su un sito web o per essere inseriti in un messaggio in uscita.

Ulteriori informazioni su [Ambienti Offer Live](../../interaction/using/fundamental-principles.md).
+++

+++**Regole di presentazione delle offerte**

*Contesto: interazione campagna*

Le regole di presentazione delle offerte sono regole di tipologia a cui si fa riferimento nell’ambiente dell’offerta, che consentono agli operatori di escludere offerte specifiche tenendo conto della cronologia delle proposte del destinatario.

Ulteriori informazioni sulle [Regole di presentazione delle offerte](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**Anteprima offerta**

*Contesto: interazione campagna*

Questa è l’anteprima dell’offerta così come viene visualizzata nella sua cartella. È accessibile dalla scheda di anteprima dell’offerta o dal profilo di contatto.

Ulteriori informazioni su [Anteprima offerta](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**Proposta di offerta**

*Contesto: interazione campagna*

Una proposta di offerta è il risultato dell’azione che consiste nel presentare un’offerta a un contatto in un determinato spazio di offerta, ad esempio il banner su un sito web, un contenuto e-mail o SMS. Questo risultato viene memorizzato nella tabella delle proposte di offerta, che definisce l’offerta, il destinatario e la marca temporale, fornendo una registrazione di tutte le offerte che un destinatario ha ricevuto.

Ulteriori informazioni sulle [proposte di offerte](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**Rappresentazione offerta**

*Contesto: interazione campagna*

Per rappresentazione di un’offerta si intendono le informazioni utilizzate dal canale per visualizzare l’offerta. La rappresentazione dell’offerta può essere costruita dalla funzione di rendering dello spazio in cui l’offerta viene rappresentata o immessa direttamente nell’interfaccia (ad esempio, nel blocco HTML). Un’offerta può essere rappresentata da uno spazio.

Ulteriori informazioni sull&#39;[interazione](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Simulazione offerte**

*Contesto: interazione campagna*

Una simulazione di offerta consente agli operatori di testare la distribuzione delle offerte in un ambito definito (data di consegna, segmento di destinazione, numero di offerte, tema, ecc.) prima di inviare effettivamente le offerte. Può essere utilizzato per adeguare le priorità dell’offerta e le regole di idoneità al fine di massimizzare l’efficacia dell’offerta.

Ulteriori informazioni sulle [Simulazioni offerte](../../interaction/using/about-offers-simulation.md).
+++

+++**Spazio dell&#39;offerta**

*Contesto: interazione campagna*

Uno spazio dell’offerta è una cartella che definisce la posizione in cui l’offerta è esposta. La definizione di uno spazio consente di specificare il canale utilizzato, creare il contenuto dell’offerta e specificare le offerte presentate. Lo spazio dell’offerta è l’interfaccia tra il canale e il motore dell’offerta.

Ulteriori informazioni su [Spazio offerte](../../interaction/using/creating-offer-spaces.md).
+++

+++**Temi offerta**

*Contesto: interazione campagna*

I temi dell’offerta sono parole chiave definite in una categoria, che consente agli operatori di filtrare le offerte quando vengono presentate. I temi consentono la selezione non gerarchica delle offerte dalla struttura del catalogo.

Ulteriori informazioni su [Temi offerta](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**Peso offerta**

*Contesto: interazione campagna*

Il peso dell’offerta si basa su formule che definiscono con precisione la rilevanza di un’offerta al fine di consentire al motore di selezionare l’offerta più pertinente. I pesi sono definiti nelle offerte e i moltiplicatori sono definiti nelle categorie. Le offerte idonee vengono prese in considerazione in ordine decrescente di peso.

Ulteriori informazioni su [Peso offerta](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**Operatore**

Un operatore è un utente di Adobe Campaign che dispone delle autorizzazioni per accedere ed eseguire azioni. Gli operatori sono associati a gruppi di operatori e ereditano i diritti e i privilegi di tali gruppi. Puoi anche attribuire i diritti denominati direttamente agli operatori.

Ulteriori informazioni su [Operatori](../../platform/using/access-management-operators.md).
+++

+++**Gruppi di operatori**

I gruppi di operatori consentono di gestire i ruoli per gli operatori di Campaign. È possibile definire gruppi di operatori a cui si attribuiscono diritti, quindi associare gli operatori a uno o più gruppi. Questo consente di riutilizzare i diritti e rendere più coerenti i profili dell’operatore. Inoltre, facilita la gestione e la manutenzione dei profili.

Ulteriori informazioni su [Gruppi di operatori](../../platform/using/access-management-groups.md).
+++

+++**Opzioni**

Le opzioni sono variabili a livello di piattaforma utilizzate per definire le impostazioni dell’istanza Campaign. Le opzioni possono definire intervalli di tempo (ad esempio per il flusso di lavoro di pulizia del database) o altre definizioni globali a livello di piattaforma.

Ulteriori informazioni su [Opzioni](../../installation/using/configuring-campaign-options.md).
+++

+++**Interazione in uscita**

*Contesto: interazione campagna*

Un’interazione in uscita è una chiamata al motore di interazione da un elenco di contatti (utilizzato per la consegna di e-mail, direct mailing, ecc.). A ogni contatto vengono applicate le stesse regole e le stesse procedure. Questo tipo di interazione viene generalmente elaborato in modalità batch.

Ulteriori informazioni sull&#39;[interazione in uscita](../../interaction/using/about-outbound-channels.md).
+++

+++**Esportazione/importazione pacchetto**

Un&#39;esportazione di package è un&#39;operazione che consiste nella generazione di un file XML contenente definizioni di oggetti. I pacchetti vengono utilizzati per migrare funzionalità e definizioni da un’istanza all’altra. Vengono inoltre utilizzati per aggiungere definizioni di prodotto critiche ai sistemi di backup e controllo del codice sorgente.

Ulteriori informazioni su [Esportazione/importazione pacchetto](../../platform/using/working-with-data-packages.md).
+++

+++**Palette**

Nella palette del flusso di lavoro vengono visualizzate le attività disponibili che possono essere aggiunte a un flusso di lavoro. Questo componente viene visualizzato in un formato a schede con le attività del flusso di lavoro raggruppate logicamente per il loro utilizzo. Le attività disponibili nella palette sono determinate dai componenti aggiuntivi installati nell’istanza Campaign e dal contesto di visualizzazione del flusso di lavoro.

Ulteriori informazioni sulla palette sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html#add-and-link-activities){target="_blank"}.
+++

+++**Monitoraggio delle prestazioni**

Le informazioni di monitoraggio delle prestazioni vengono visualizzate nella scheda Monitoraggio. Mostra le metriche per il sistema sottostante, come memoria e utilizzo del CPU, statistiche del server SMTP, processi del server e altre informazioni rilevanti.

Ulteriori informazioni sul [Monitoraggio delle prestazioni](../../production/using/monitoring-processes.md).
+++

+++**Blocchi di personalizzazione**

Adobe Campaign offre blocchi di personalizzazione incorporati che puoi inserire nelle consegne. Sono dinamici, personalizzati e contengono un rendering specifico. Ad esempio, puoi aggiungere un logo, un messaggio di saluto o un collegamento a una pagina speculare. Per impostazione predefinita, sono disponibili diversi blocchi di personalizzazione. Puoi anche definire blocchi di personalizzazione personalizzati che ti consentiranno di ottimizzare la personalizzazione della consegna. I dati effettivi vengono inseriti in ogni messaggio generato durante la fase di analisi della consegna.

Ulteriori informazioni sui blocchi di personalizzazione nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html){target="_blank"}.
+++

+++**Campo Personalization**

Un campo di personalizzazione è un singolo riferimento a un campo dati utilizzato per personalizzare una consegna per un destinatario specifico. Il valore effettivo dei dati viene inserito durante la fase di analisi della consegna.

Ulteriori informazioni sui campi di personalizzazione sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-fields.html){target="_blank"}.
+++

+++**Variabili Personalization**

Le variabili di Personalization sono parti di codice in una consegna che possono visualizzare testo diverso a destinatari diversi in base alle informazioni del destinatario. Questi campi possono essere implementati come campo o blocco di personalizzazione.

Ulteriori informazioni sulle [variabili Personalization](../../delivery/using/about-personalization.md).
+++

+++**Piano**

Un piano è un tipo di cartella utilizzato per organizzare le attività di marketing in base al calendario. Le cartelle di pianificazione nella visualizzazione Esplora definiscono le unità basate sul tempo, ad esempio un anno, un trimestre o un mese. Le cartelle del piano possono essere nidificate e possono contenere altre cartelle del piano, cartelle di programma o campagne.

Ulteriori informazioni sui piani sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=it){target=_blank}.
+++

+++**Filtri predefiniti**

I filtri predefiniti sono query salvate per il riutilizzo. L’utilizzo di filtri predefiniti aumenta la produttività (perché vengono creati una sola volta), aiuta a creare coerenza (perché tutti gli addetti al marketing possono utilizzarli) e riduce le competenze richieste dall’addetto al marketing perché può utilizzare codice o logica che potrebbe non essere in grado di creare.

Per ulteriori informazioni sui filtri, consulta la [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**Chiave primaria**

La chiave primaria è l&#39;identificatore univoco di ogni record di una tabella di database. Una tabella deve avere almeno una chiave. Di regola, le chiavi vengono dichiarate dopo l’elemento principale dello schema e gli indici. Le chiavi primarie non possono essere composite (includere diversi campi).

Ulteriori informazioni sulla [chiave primaria](../../configuration/using/schema/key.md).
+++

+++**Profilo**

Un profilo è un record di informazioni che rappresenta un cliente finale, un potenziale cliente o un lead. Ogni profilo corrisponde a un record nella tabella nmsRecipient o a una tabella esterna contenente l’ID cookie, l’ID cliente, l’identificatore mobile o altre informazioni relative a un canale specifico.

Ulteriori informazioni su [Profili](../../platform/using/about-profiles.md).
+++

+++**Programma**

Le cartelle di programmi e sottoprogrammi organizzano attività di marketing in base a un obiettivo aziendale, ad esempio fedeltà, acquisizione o cross-selling. Possono inoltre rappresentare periodi fiscali o tattiche di campagna, ad esempio eventi o newsletter. Ogni programma contiene campagne collegate a un calendario, che fornisce una visualizzazione complessiva.

Ulteriori informazioni sui programmi nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=it){target=_blank}.
+++

+++**Risorse pubbliche**

La cartella Risorse pubbliche, in Adobe Campaign, contiene le immagini ospitate dal server applicazioni. Le immagini nelle consegne devono essere pubblicate nel server applicazioni (o in un server di hosting di immagini, se Campaign è configurato in questo modo) per essere visualizzate nelle consegne, ad esempio nelle e-mail.

Ulteriori informazioni sulle [risorse pubbliche](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**Invia**

*Contesto: canale app mobile*

Le notifiche push sono messaggi ricevuti dalle app mobili. Le notifiche push sono configurate per funzionare con Adobe Campaign includendo il codice Experience Platform SDK nell’app mobile. Per il push, sono disponibili due canali di consegna: iOS e Android.

Ulteriori informazioni su [Push](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**Destinatario**

In Adobe Campaign, i destinatari sono i profili predefiniti target per l’invio di consegne (e-mail, SMS, ecc.) ai clienti. I dati dei destinatari memorizzati nel database consentono di filtrare il target e aggiungere dati di personalizzazione. In genere si tratta di informazioni personali, di contatto, demografiche e transazionali, ma potrebbe trattarsi di qualsiasi tipo di informazione che supporta il marketing e l’analisi.

Ulteriori informazioni su [Destinatario](../../configuration/using/about-data-model.md).
+++

+++**Funzione di rendering**

*Contesto: interazione campagna*

La funzione di rendering è definita in uno spazio dell’offerta. Viene utilizzato per creare la rappresentazione dell’offerta in base agli attributi definiti nell’offerta. Esistono tre diverse modalità di funzione di rendering: HTML, XML e testo.

Ulteriori informazioni sulla [Funzione di rendering](../../interaction/using/creating-offer-spaces.md).
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**Schema**

Uno schema è un documento XML associato a una tabella di database. Definisce la struttura dati e descrive la definizione SQL della tabella. Gli operatori manipolano gli schemi in Campaign e il prodotto traduce le loro azioni nell’SQL richiesto, che viene quindi eseguito sul database.

Ulteriori informazioni su [Schemi](../../configuration/using/about-schema-reference.md).
+++

+++**Estensione schema**

L’estensione dello schema consente di personalizzare gli schemi predefiniti in base ai casi d’uso aziendali. Ad esempio, puoi aggiungere il campo &quot;Fedeltà&quot; alla tabella Destinatario.

Ulteriori informazioni sull&#39;[estensione schema](../../configuration/using/extending-a-schema.md).
+++

+++**Indirizzi di seed**

Gli indirizzi di seed vengono utilizzati per eseguire il targeting di destinatari che non corrispondono ai criteri di target definiti. In questo modo, i destinatari che non rientrano nell’ambito di consegna possono ricevere la consegna, come farebbe qualsiasi altro destinatario. Vengono aggiunti al pubblico di un messaggio per rilevare eventuali utilizzi fraudolenti del database dei destinatari o per garantire la consegna.

Ulteriori informazioni su [Indirizzi seed](../../delivery/using/about-seed-addresses.md).
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**Servizio**

Adobe Campaign consente di creare e amministrare servizi di informazioni quali newsletter o aggiornamenti dei prodotti e di gestire gli abbonamenti a tali servizi. Diversi servizi possono essere definiti in parallelo.

Ulteriori informazioni su [Servizi](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**Gestione SFTP**

Nel Pannello di controllo, puoi interagire con tutti i server SFTP collegati alle istanze di Campaign a cui hai accesso. Il Pannello di controllo Campaign ti consente di eseguire azioni sui server SFTP, ad esempio monitorare la capacità di archiviazione, gestire gli indirizzi IP per l’inserimento nell’elenco Consentiti e gestire le chiavi SSH pubbliche.

Ulteriori informazioni sulla [gestione SFTP](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html).
+++

+++**Attività dei servizi di abbonamento**

L’attività del flusso di lavoro Subscription services ti consente di creare o eliminare un abbonamento a un servizio di informazioni per il gruppo specificato nella transizione.

Ulteriori informazioni sull&#39;attività Subscription services sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/subscription-services.html){target="_blank"}.
+++

+++**Approvazione target**

*Contesto: marketing distribuito della campagna*

L’approvazione del target è il processo in base al quale un operatore o un gruppo di operatori separato approva il target finale di una consegna (dopo che la fase di analisi ha generato il target) prima che la consegna possa essere inviata.

Ulteriori informazioni sull&#39;attività di approvazione di Target sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/approval.html){target="_blank"}.
+++

+++**Targeting dei dati**

I dati di destinazione sono i dati memorizzati nella tabella di lavoro (transizione) di un flusso di lavoro. Questi dati sono disponibili all’interno della consegna per la personalizzazione del contenuto della consegna o per definire la logica degli elementi dinamici della consegna.

Ulteriori informazioni sui dati di destinazione sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html#target-data){target="_blank"}.
+++

+++**Mappatura del target**

La mappatura di destinazione è la mappatura dei canali di consegna su un tipo di dati specifico. Le mappature di Target definiscono il modo in cui i diversi canali di consegna si collegano ai campi di dati di uno schema. Definisce il modo in cui Campaign invia a quel tipo di dati utilizzando un campo o un’espressione specifica.

Ulteriori informazioni sulla mappatura di destinazione sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/audience/add-profiles/target-mappings.html?lang=it){target="_blank"}.
+++

+++**Attività di targeting**

Le attività di targeting sono attività del flusso di lavoro specifiche per il targeting, la manipolazione dei dati della popolazione e le attività di filtro. Consentono agli operatori di creare uno o più target definendo i set e suddividendoli o combinandoli mediante operazioni di intersezione, unione o esclusione.

Ulteriori informazioni sulle attività di targeting sono disponibili nella [documentazione di Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/targeting-activities
.html){target="_blank"}.
+++

+++**Dimensione targeting**

La dimensione di targeting è il tipo di dati prodotto (restituito) da una query o da altre attività del flusso di lavoro. Adobe Campaign restituisce solo la chiave primaria delle righe del database dei partecipanti, indipendentemente dalla query utilizzata per ottenerle.

Per ulteriori informazioni sulla dimensione di targeting, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}.
+++

+++**Attività attività**

*Contesto: Gestione risorse marketing (MRM)*

L’attività del flusso di lavoro Attività incorpora l’azione umana nella logica di un flusso di lavoro. È possibile specificare due scenari: il primo se l&#39;attività è completata e il secondo se l&#39;attività non è completata. I casi d’uso tipici consistono nell’incorporare azioni offline in una campagna o in azioni personalizzate come le approvazioni.

Per ulteriori informazioni sull&#39;attività Attività, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/mrm/creating-and-managing-tasks.html?lang=it){target="_blank"}.
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**Modello**

Un modello è un elemento di progettazione utilizzato per creare un oggetto. Contiene le impostazioni dell&#39;oggetto e facoltativamente il relativo contenuto. Il sistema di modelli viene utilizzato per creare consegne, campagne, flussi di lavoro e molti altri elementi di Adobe Campaign. I modelli di fabbrica disponibili sono definiti dai pacchetti installati. I modelli possono quindi essere duplicati e personalizzati in base alle esigenze degli operatori di Campaign.
+++

<!--
-----ACS -> SEEDS IN ACC-----
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message's audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
-----NOT FOR DOCS?-----
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**Registri di tracciamento**

Il flusso di lavoro tecnico di tracciamento recupera i dati di tracciamento una volta inviata la consegna e attivato il tracciamento. Questi dati si trovano nella scheda Tracciamento della consegna. Puoi trovare informazioni per aperture e clic su un’e-mail o altre interazioni con un messaggio ricevuto dal destinatario.

Ulteriori informazioni su [Registri di tracciamento](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**Messaggistica transazionale**

La messaggistica transazionale è un modulo di Campaign progettato per gestire le notifiche di attivazione personalizzate generate da eventi inviati da un sistema di informazioni esterno. Un messaggio transazionale è una comunicazione singola e univoca, inviata in tempo reale da un provider, ad esempio un sito web. È particolarmente atteso, perché contiene informazioni importanti che il destinatario desidera controllare o confermare.

Ulteriori informazioni sulla [messaggistica transazionale](../../message-center/using/about-transactional-messaging.md).
+++

&lt;!------- UTILE QUI??----->
+++**Campagne attivate**

Le campagne attivate sono campagne eseguite quando viene ricevuta una richiesta API in un flusso di lavoro. Le chiamate API vengono utilizzate da un’attività Signal nel flusso di lavoro che avvia l’esecuzione del flusso di lavoro.

Ulteriori informazioni sulle campagne attivate sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/external-signal.html){target="_blank"}.
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**Tipologia**

*Contesto: ottimizzazione campagna*

Una tipologia è un raggruppamento di regole di tipologia applicate alla fase di analisi di una consegna. Una tipologia di campagna può contenere diverse regole di tipologia, ma una consegna può fare riferimento a una sola tipologia.

Ulteriori informazioni sulle tipologie sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=it){target="_blank"}.
+++

+++**Regola di tipologia**

*Contesto: ottimizzazione campagna*

Le regole di tipologia sono regole aziendali implementate come parte della fase di analisi della consegna. Le regole di tipologia sono controlli sul contenuto della consegna (regole di controllo) o sul target della consegna (regole di filtro) o su altra logica (regole di pressione) che applicano i requisiti aziendali. Le regole sono elementi granulari che possono essere inclusi in una o più tipologie.

Ulteriori informazioni sulle regole di tipologia sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=it){target="_blank"}.
+++

## U - Z {#sec-6}

+++**Modalità unitaria**

*Contesto: interazione campagna, messaggistica transazionale*

In modalità unitaria, un singolo contatto viene elaborato dal motore di offerta in fase di runtime. Questa modalità viene generalmente utilizzata per le interazioni in entrata e i messaggi transazionali.

Ulteriori informazioni sulla [modalità unitaria](../../interaction/using/about-inbound-channels.md).
+++

+++**Applicazioni Web**

Le applicazioni web sono pagine di applicazioni dinamiche e interattive ospitate dall’istanza Campaign. Contengono dati provenienti dal database e contenuti adattati ai diritti dell’utente connesso. È ad esempio possibile creare un modulo di modifica in una extranet o moduli di notifica che includono dati provenienti dal database con tabelle, grafici, moduli di input e così via. Questa funzionalità consente di progettare e pubblicare pagine Web in cui gli utenti possono cercare o immettere informazioni.

Ulteriori informazioni sulle [applicazioni Web](../../web/using/about-web-applications.md).
+++

+++**Flusso di lavoro**

Un workflow è una rappresentazione visiva del flusso di esecuzione della campagna. Consente di orchestrare l&#39;intera gamma di processi e attività tra i diversi moduli del server applicazioni. Questo ambiente grafico completo ti consente di progettare processi inclusi segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc. Il motore del flusso di lavoro esegue e traccia tali processi.

Ulteriori informazioni su [Flussi di lavoro](../../workflow/using/about-workflows.md).
+++

+++**Diario flusso di lavoro**

Il giornale di registrazione del flusso di lavoro è il registro di esecuzione passo passo di un flusso di lavoro. Contiene tutta la cronologia o l’audit trail del flusso di lavoro. Viene utilizzato a scopo di sviluppo, risoluzione dei problemi o debug.

Ulteriori informazioni sul giornale di registrazione del flusso di lavoro sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}.
+++

+++**Tabella di lavoro**

La tabella di lavoro contiene tutte le informazioni contenute nelle transizioni del flusso di lavoro. Ogni flusso di lavoro utilizza diverse tabelle di lavoro. La tabella di lavoro contiene i risultati dell&#39;attività di origine e il relativo contenuto viene utilizzato come input per l&#39;attività successiva (connessa) nel flusso di lavoro.  La manipolazione (estensione, personalizzazione) della tabella di lavoro è una delle principali competenze di un operatore Adobe Campaign.

Ulteriori informazioni sulle [tabelle di lavoro](../../workflow/using/about-workflows.md).
+++
