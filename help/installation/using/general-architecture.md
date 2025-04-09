---
product: campaign
title: Architettura generale di Campaign Classic
description: Scopri come installare e configurare Campaign Classic
feature: Installation, Architecture
audience: installation
content-type: reference
level: Intermediate, Experienced
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 0%

---

# Architettura generale{#general-architecture}



La tipica distribuzione della soluzione Adobe Campaign è costituita dai seguenti componenti:

* **Ambiente client personalizzato**

  Interfaccia grafica intuitiva in cui gli utenti possono comunicare e tenere traccia delle offerte di marketing, creare campagne, rivedere e gestire tutte le attività di marketing, i programmi e i piani (comprese e-mail, flussi di lavoro e pagine di destinazione), creare e gestire profili cliente e definire i tipi di pubblico cliente.

* **Ambiente di sviluppo**

  Software lato server che esegue le campagne di marketing tramite canali di comunicazione scelti, tra cui e-mail, SMS, notifiche push, direct mail, web o social, in base alle regole e ai flussi di lavoro definiti nell’interfaccia utente.

* **Contenitori database**

  Basato sulla tecnologia del database relazionale, il database di Adobe Campaign memorizza tutte le informazioni sui clienti, i componenti delle campagne, le offerte e i flussi di lavoro, nonché i risultati delle campagne nei contenitori del database dei clienti.

Adobe Campaign si basa su un’architettura orientata ai servizi (SOA, Service-Oriented Architecture) e comprende diversi moduli funzionali. Questi moduli possono essere distribuiti su uno o più computer, in una o più istanze, a seconda dei vincoli in termini di scalabilità, disponibilità e isolamento del servizio. L&#39;ambito delle configurazioni di distribuzione è pertanto molto ampio e si estende su un singolo computer centrale fino a configurazioni che includono più server dedicati su più siti.

>[!NOTE]
>
>In qualità di fornitore di software, EMC specifica l&#39;infrastruttura hardware e software compatibile. I suggerimenti sull&#39;hardware qui riportati sono solo a scopo informativo e si basano sulla nostra esperienza. Adobe non è responsabile per le decisioni prese in base ad esse. Dipende anche dalle regole e dalle pratiche aziendali, nonché dalla criticità e dai livelli di prestazioni richiesti del progetto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Se non specificato diversamente, l’installazione, gli aggiornamenti e la manutenzione di tutti i componenti di una piattaforma Adobe Campaign sono di responsabilità dell’amministratore del computer che li ospita. Ciò include l&#39;implementazione dei prerequisiti per le applicazioni Adobe Campaign e la conformità con la [Matrice di compatibilità](../../rn/using/compatibility-matrix.md) di Campaign tra i componenti.

## Livello di presentazione {#presentation-layer}

È possibile accedere all’applicazione in modi diversi, a seconda delle esigenze degli utenti: rich client, thin client o integrazione API.

* **Client avanzato**: l&#39;interfaccia utente principale dell&#39;applicazione è un client avanzato, ovvero un&#39;applicazione nativa (Windows) che comunica con il server applicazioni Adobe Campaign esclusivamente con protocolli Internet standard (SOAP, HTTP, ecc.). Questa console offre una produttività semplice e intuitiva, utilizza una larghezza di banda molto ridotta (tramite l&#39;utilizzo di una cache locale) ed è progettata per una facile distribuzione. Questa console può essere distribuita da un browser Internet, può essere aggiornata automaticamente e non richiede alcuna configurazione di rete specifica perché genera solo traffico HTTP(S).
* **Thin client**: è possibile accedere a determinate parti dell&#39;applicazione tramite un semplice browser Web utilizzando un&#39;interfaccia utente di HTML, inclusi il modulo di reporting, le fasi di approvazione della consegna, le funzionalità del modulo Marketing distribuito (centrale/locale), il monitoraggio delle istanze, ecc. Questa modalità consente di includere le funzionalità di Adobe Campaign in una Intranet o in una Extranet.
* **Integrazione tramite API**: in alcuni casi è possibile chiamare il sistema da un&#39;applicazione esterna utilizzando le API dei servizi Web esposte tramite il protocollo SOAP.

## Livello applicazione logico {#logical-application-layer}

Adobe Campaign è un&#39;unica piattaforma con diverse applicazioni che si combinano per creare un&#39;architettura aperta e scalabile. La piattaforma Adobe Campaign è scritta su un livello di applicazione flessibile ed è facilmente configurabile per soddisfare le esigenze aziendali. Ciò risponde alle crescenti esigenze dell&#39;azienda sia dal punto di vista funzionale che tecnico. L&#39;architettura distribuita garantisce scalabilità lineare del sistema, da migliaia di messaggi a milioni di messaggi.

Adobe Campaign si basa su un set di processi lato server che funzionano insieme.

I processi principali sono i seguenti:

**Server applicazioni** (nlserver web)

Questo processo espone l’intera gamma di funzionalità di Adobe Campaign tramite le API dei servizi web (SOAP - HTTP + XML). Inoltre, può generare in modo dinamico le pagine web utilizzate per l’accesso basato su HTML (report, moduli web, ecc.). Per ottenere questo risultato, questo processo include un server Apache Tomcat JSP. Processo a cui si connette la console.

**Motore flusso di lavoro** (nlserver wfserver)

Esegue i processi del flusso di lavoro definiti nell’applicazione.

Gestisce inoltre flussi di lavoro tecnici eseguiti periodicamente, tra cui:

* Tracciamento: recupero e consolidamento dei registri di tracciamento. Consente di recuperare i registri dal server di reindirizzamento e creare gli indicatori aggregati utilizzati dal modulo di reporting.
* Pulizia: pulizia del database. Utilizzato per eliminare i vecchi record ed evitare la crescita esponenziale del database.
* Fatturazione: invio automatico di un rapporto di attività per la piattaforma (dimensioni del database, numero di azioni di marketing, numero di profili attivi, ecc.).

**Server di recapito** (mta nlserver)

Adobe Campaign dispone di funzionalità di trasmissione e-mail native. Questo processo funziona come agente di trasferimento di posta SMTP (MTA). Esegue la personalizzazione &quot;uno a uno&quot; dei messaggi e ne gestisce la consegna fisica. Funziona tramite processi di consegna e gestisce i nuovi tentativi automatici. Inoltre, quando il tracciamento è abilitato, sostituisce automaticamente gli URL in modo che puntino al server di reindirizzamento.

Questo processo può gestire la personalizzazione e l’invio automatico a un router di terze parti per SMS, fax e direct mail.

**Server di reindirizzamento** (nlserver webmdl)

Per le e-mail, Adobe Campaign gestisce automaticamente il tracciamento dei clic e delle aperture (un’altra possibilità è il tracciamento transazionale a livello di sito web). A questo scopo, gli URL incorporati nei messaggi e-mail vengono riscritti in modo da puntare a questo modulo, che registra il passaggio dell’utente Internet prima di reindirizzarlo all’URL richiesto.

Per garantire la massima disponibilità, questo processo è completamente indipendente dal database: gli altri processi server comunicano con esso utilizzando solo chiamate SOAP (HTTP, HTTP(S) e XML). Tecnicamente, questa funzionalità è implementata in un modulo di estensione di un server HTTP (estensione ISAPI in IIS, o un modulo DSO Apache, ecc.) ed è disponibile solo in Windows.

Sono disponibili anche altri processi più tecnici:

**Gestione delle e-mail non recapitate** (nlserver inMail)

Questo processo consente di raccogliere automaticamente le e-mail dalle cassette postali configurate per ricevere messaggi non recapitati restituiti in caso di errore di consegna. Questi messaggi vengono quindi sottoposti a elaborazione basata su regole per determinare i motivi della mancata consegna (destinatario sconosciuto, quota superata, ecc.) e per aggiornare lo stato di consegna nel database.

Tutte queste operazioni sono completamente automatiche e preconfigurate.

**Stato consegna SMS** (nlserver sms)

Questo processo esegue il polling del router SMS per raccogliere lo stato di avanzamento e aggiornare il database.

**Scrittura dei messaggi del registro** (nlserver syslogd)

Questo processo tecnico acquisisce i messaggi di registro e le tracce generate dagli altri processi e li scrive sul disco rigido. In questo modo è possibile disporre di numerose informazioni per la diagnosi in caso di problemi.

**Scrittura dei registri di tracciamento** (nlserver trackinglogd)

Questo processo salva su disco i registri di tracciamento generati dal processo di reindirizzamento.

**Scrittura di eventi in entrata** (nlserver interaction)

Questo processo garantisce la registrazione sul disco degli eventi in entrata, nel quadro di Interaction.

**Supervisione dei moduli** (watchdog nlserver)

Questo processo tecnico funge da processo primario che genera gli altri. Vengono inoltre monitorati e riavviati automaticamente in caso di problemi, mantenendo così il massimo tempo di attività del sistema.

**Server statistiche** (nlserver stat)

Questo processo mantiene statistiche sul numero di connessioni, sui messaggi inviati per ciascun server di posta a cui vengono inviati i messaggi, nonché sulle relative limitazioni (numero massimo di connessioni simultanee, messaggi all&#39;ora e/o connessione). Consente inoltre di federare più istanze o computer se condividono gli stessi indirizzi IP pubblici.

>[!NOTE]
>
>L&#39;elenco completo dei moduli di Adobe Campaign è disponibile in [questo documento](../../production/using/operating-principle.md).

## Livello di persistenza {#persistence-layer}

Il database viene utilizzato come livello di persistenza e contiene quasi tutte le informazioni gestite da Adobe Campaign. Ciò include sia dati funzionali (profili, abbonamenti, contenuti, ecc.), sia dati tecnici (processi e registri di consegna, registri di tracciamento, ecc.) e dati di lavoro (acquisti, lead).

L’affidabilità del database è della massima importanza, in quanto la maggior parte dei componenti di Adobe Campaign richiede l’accesso al database per eseguire le proprie attività (con l’eccezione, in particolare, del modulo di reindirizzamento).

La piattaforma viene fornita con un data mart centrato sul marketing o può essere facilmente posizionata su un data mart e uno schema esistenti utilizzando uno dei principali sistemi di gestione di database relazionali (RDBMS). La piattaforma Adobe Campaign accede a tutti i dati all’interno del data mart tramite chiamate SQL da Adobe Campaign al database. Adobe Campaign fornisce inoltre una serie completa di strumenti ETL (Extract Transform and Load) per eseguire l’importazione e l’esportazione dei dati all’interno e all’esterno del sistema.
