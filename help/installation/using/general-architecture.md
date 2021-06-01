---
product: campaign
title: Architettura generale
description: Scopri come installare e configurare Campaign Classic.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1336'
ht-degree: 0%

---

# Architettura generale{#general-architecture}

La tipica implementazione della soluzione Adobe Campaign consiste dei seguenti componenti:

* **Ambiente client personalizzato**

   Interfaccia grafica intuitiva in cui gli utenti possono comunicare e monitorare le offerte di marketing, creare campagne, rivedere e gestire tutte le attività, i programmi e i piani di marketing, incluse e-mail, flussi di lavoro e pagine di destinazione, creare e gestire i profili dei clienti e definire i tipi di pubblico cliente.

* **Ambiente di sviluppo**

   Software lato server che esegue le campagne di marketing attraverso i canali di comunicazione selezionati, inclusi e-mail, SMS, notifiche push, direct mail, web o social, in base alle regole e ai flussi di lavoro definiti nell’interfaccia utente.

* **Contenitori di database**

   In base alla tecnologia di database relazionale, il database di Adobe Campaign memorizza tutte le informazioni dei clienti, i componenti della campagna, le offerte e i flussi di lavoro, nonché i risultati della campagna nei contenitori di database dei clienti.

Adobe Campaign si basa su un’architettura orientata ai servizi (SOA) e comprende diversi moduli funzionali. Questi moduli possono essere distribuiti su uno o più computer, in istanze singole o multiple, a seconda dei vincoli in termini di scalabilità, disponibilità e isolamento del servizio. L&#39;ambito delle configurazioni di distribuzione è quindi molto ampio e si estende su un singolo computer centrale fino a configurazioni che includono più server dedicati su più siti.

>[!NOTE]
>
>In qualità di fornitore di software, si specificano infrastrutture hardware e software compatibili. Le raccomandazioni hardware qui riportate sono a scopo puramente informativo e si basano sulla nostra esperienza. L&#39;Adobe non è responsabile delle decisioni prese sulla base di tali decisioni. Dipenderà anche dalle tue regole e pratiche aziendali, dalla criticità e dai livelli di prestazioni richiesti del progetto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Se non esplicitamente specificato diversamente, l’installazione, gli aggiornamenti e la manutenzione di tutti i componenti di una piattaforma Adobe Campaign sono responsabilità degli amministratori di computer che li ospitano. Ciò include l’implementazione dei prerequisiti per le applicazioni Adobe Campaign e la conformità alla matrice di compatibilità di Campaign [tra i componenti.](../../rn/using/compatibility-matrix.md)

## Livello presentazione {#presentation-layer}

L’accesso all’applicazione può essere effettuato in diversi modi, a seconda delle esigenze degli utenti: Integrazione con client avanzati, thin client o API.

* **Client** avanzato: L&#39;interfaccia utente principale dell&#39;applicazione è un client avanzato, in altre parole un&#39;applicazione nativa (Windows) che comunica con il server dell&#39;applicazione Adobe Campaign esclusivamente con i protocolli Internet standard (SOAP, HTTP, ecc.). Questa console garantisce un&#39;ottima facilità di utilizzo per la produttività, utilizza una larghezza di banda molto ridotta (tramite l&#39;utilizzo di una cache locale) ed è progettata per una facile installazione. Questa console può essere distribuita da un browser Internet, può essere aggiornata automaticamente e non richiede alcuna configurazione di rete specifica perché genera solo traffico HTTP(S).
* **Thin client**: Alcune parti dell&#39;applicazione sono accessibili tramite un semplice browser web che utilizza un&#39;interfaccia utente HTML, tra cui il modulo di reporting, le fasi di approvazione della consegna, le funzionalità del modulo Marketing distribuito (centrale/locale), il monitoraggio delle istanze, ecc. Questa modalità consente di includere le funzionalità di Adobe Campaign in una Intranet o in una Intranet.
* **Integrazione tramite le API**: In alcuni casi, il sistema può essere chiamato da un’applicazione esterna utilizzando le API dei servizi Web esposte tramite il protocollo SOAP.

## Livello applicazione logico {#logical-application-layer}

Adobe Campaign è una piattaforma singola con diverse applicazioni che si combinano per creare un’architettura aperta e scalabile. La piattaforma Adobe Campaign è scritta su un livello di applicazione flessibile ed è facilmente configurabile per soddisfare le esigenze aziendali di un’azienda. Ciò consente di soddisfare le crescenti esigenze dell&#39;impresa sia da un punto di vista funzionale che tecnico. L&#39;architettura distribuita garantisce una scalabilità lineare del sistema, che passa da migliaia di messaggi a milioni di messaggi.

Adobe Campaign si basa su un set di processi lato server che funzionano insieme.

I processi principali sono i seguenti:

**Server applicazioni**  (web nlserver)

Questo processo espone l’intera gamma di funzionalità di Adobe Campaign tramite le API dei servizi web (SOAP - HTTP + XML). Inoltre, può generare in modo dinamico le pagine web utilizzate per l’accesso basato su HTML (rapporti, moduli web, ecc.). Per ottenere questo risultato, questo processo include un server Apache Tomcat JSP. Questo è il processo a cui la console si connette.

**Motore del flusso di lavoro**  (nlserver wfserver)

Esegue i processi del flusso di lavoro definiti nell&#39;applicazione.

Inoltre, gestisce periodicamente i flussi di lavoro tecnici eseguiti, tra cui:

* Tracciamento: Recupero e consolidamento dei registri di tracciamento. Consente di recuperare i registri dal server di reindirizzamento e di creare gli indicatori aggregati utilizzati dal modulo di reporting.
* Pulizia: Pulizia del database. Utilizzato per eliminare i vecchi record ed evitare la crescita esponenziale del database.
* Fatturazione: Invio automatico di un rapporto di attività per la piattaforma (dimensioni del database, numero di azioni di marketing, ecc.).

**Server di consegna**  (nlserver mta)

Adobe Campaign dispone di funzionalità di trasmissione e-mail native. Questo processo funziona come agente di trasferimento della posta SMTP (MTA). Esegue la personalizzazione &quot;uno a uno&quot; dei messaggi e gestisce la loro consegna fisica. Funziona utilizzando i processi di consegna e gestisce i tentativi automatici. Inoltre, quando il tracciamento è abilitato, sostituisce automaticamente gli URL in modo che puntino al server di reindirizzamento.

Questo processo può gestire la personalizzazione e l&#39;invio automatico a un router di terze parti per SMS, fax e direct mail.

**Server di reindirizzamento**  (nlserver webmdl)

Per le e-mail, Adobe Campaign gestisce automaticamente il tracciamento dei clic e delle pagine aperte (il tracciamento transazionale a livello di sito Web è un’ulteriore possibilità). A tal fine, gli URL incorporati nei messaggi e-mail vengono riscritti per puntare a questo modulo, che registra il passaggio dell’utente Internet prima di reindirizzarli all’URL richiesto.

Per garantire la massima disponibilità, questo processo è completamente indipendente dal database: gli altri processi server comunicano con esso utilizzando solo chiamate SOAP (HTTP, HTTP(S) e XML). Tecnicamente, questa funzionalità viene implementata in un modulo di estensione di un server HTTP (estensione ISAPI in IIS, o un modulo DSO Apache, ecc.) ed è disponibile solo in Windows.

Sono inoltre disponibili altri processi più tecnici:

**Gestione delle e-mail non recapitate**  (nlserver inMail)

Questo processo consente di raccogliere automaticamente e-mail dalle cassette postali configurate per ricevere messaggi rimbalzati che vengono restituiti in caso di errore di consegna. Questi messaggi vengono quindi elaborati in base a regole per determinare i motivi della mancata consegna (destinatario sconosciuto, quota superata, ecc.) e per aggiornare lo stato di consegna nel database.

Tutte queste operazioni sono completamente automatiche e preconfigurate.

**Stato di consegna SMS**  (nlserver sms)

Questo processo controlla il router SMS per raccogliere lo stato di avanzamento e aggiornare il database.

**Scrittura dei messaggi di log**  (nlserver syslogd)

Questo processo tecnico acquisisce i messaggi di log e le tracce generate dagli altri processi e li scrive sul disco rigido. Questo rende disponibili ampie informazioni per la diagnosi in caso di problemi.

**Scrittura dei registri di tracciamento**  (nlserver trackinglogd)

Questo processo consente di salvare su disco i registri di tracciamento generati dal processo di reindirizzamento.

**Scrittura di eventi in entrata**  (interazioni nlserver)

Questo processo assicura la registrazione sul disco di eventi in entrata, nel quadro di Interaction.

**Moduli di supervisione**  (nlserver watchdog)

Questo processo tecnico agisce come un processo primario che genera gli altri. Inoltre, li controlla e li riavvia automaticamente in caso di incidenti, mantenendo il massimo tempo di attività del sistema.

**Server**  statistiche (statistica nlserver)

Questo processo mantiene le statistiche sul numero di connessioni, i messaggi inviati per ogni server di posta a cui vengono inviati i messaggi e le relative limitazioni (numero più elevato di connessioni simultanee, messaggi all’ora/e e/o connessione). Consente inoltre di raggruppare più istanze o computer se condividono gli stessi indirizzi IP pubblici.

>[!NOTE]
>
>L&#39;elenco completo dei moduli Adobe Campaign è disponibile in [questo documento](../../production/using/operating-principle.md).

## Livello di persistenza {#persistence-layer}

Il database viene utilizzato come livello di persistenza e contiene quasi tutte le informazioni gestite da Adobe Campaign. Ciò include sia dati funzionali (profili, abbonamenti, contenuto, ecc.), sia dati tecnici (processi di consegna e registri, registri di tracciamento, ecc.) e dati di lavoro (acquisti, lead).

L’affidabilità del database è della massima importanza perché la maggior parte dei componenti Adobe Campaign richiede l’accesso al database per eseguire le proprie attività (con l’eccezione notevole del modulo di reindirizzamento).

La piattaforma viene fornita con un data mart centrato sul marketing o può facilmente posizionarsi su un data mart esistente e uno schema utilizzando uno dei principali sistemi di gestione del database relazionale (RDBMS). Tutti i dati nel data mart sono accessibili dalla piattaforma Adobe Campaign tramite chiamate SQL da Adobe Campaign al database. Adobe Campaign fornisce inoltre un complemento completo degli strumenti di estrazione trasformazione e caricamento (ETL) per eseguire l’importazione e l’esportazione di dati all’interno e all’esterno del sistema.
