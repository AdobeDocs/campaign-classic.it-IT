---
solution: Campaign Classic
product: campaign
title: Architettura generale
description: Scopri come installare e configurare Campaign Classic.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1336'
ht-degree: 0%

---


# Architettura generale{#general-architecture}

La tipica implementazione  soluzione Adobe Campaign consiste dei seguenti componenti:

* **Ambiente client personalizzato**

   Interfaccia grafica intuitiva in cui gli utenti possono comunicare e tenere traccia delle offerte di marketing, creare campagne, rivedere e gestire tutte le attività, i programmi e i piani di marketing, incluse le e-mail, i flussi di lavoro e le pagine di destinazione, creare e gestire i profili dei clienti e definire i tipi di pubblico dei clienti.

* **Ambiente di sviluppo**

   Software lato server che esegue le campagne di marketing attraverso canali di comunicazione selezionati, inclusi e-mail, SMS, notifiche push, posta diretta, web o social, in base alle regole e ai flussi di lavoro definiti nell&#39;interfaccia utente.

* **Contenitori di database**

   In base alla tecnologia di database relazionale, il database  Adobe Campaign memorizza tutte le informazioni sui clienti, i componenti delle campagne, le offerte e i flussi di lavoro, nonché i risultati delle campagne nei contenitori del database dei clienti.

 Adobe Campaign è basato su un&#39;architettura orientata ai servizi (SOA) e comprende diversi moduli funzionali. Questi moduli possono essere distribuiti su uno o più computer, in uno o più casi, a seconda dei vincoli in termini di scalabilità, disponibilità e isolamento del servizio. La portata delle configurazioni di implementazione è quindi molto ampia e si estende su un singolo computer centrale fino a configurazioni che includono più server dedicati su più siti.

>[!NOTE]
>
>In qualità di fornitore di software, è possibile specificare infrastrutture hardware e software compatibili. Le raccomandazioni hardware qui riportate sono solo a scopo informativo e si basano sulla nostra esperienza.  Adobe non è responsabile delle decisioni da esso prese. Dipenderà anche dalle regole e dalle pratiche aziendali, dalla criticità e dai livelli di prestazioni richiesti per il progetto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Se non specificato diversamente, l&#39;installazione, gli aggiornamenti e la manutenzione su tutti i componenti di una piattaforma Adobe Campaign  sono responsabilità dell&#39;amministratore del computer che li ospita. Ciò include l&#39;implementazione dei prerequisiti per  applicazioni Adobe Campaign e la conformità alla matrice [di](../../rn/using/compatibility-matrix.md) compatibilità delle campagne tra i componenti.

## Livello presentazione {#presentation-layer}

L&#39;accesso all&#39;applicazione può essere effettuato in diversi modi, a seconda delle esigenze degli utenti: Integrazione con client Rich, Thin Client o API.

* **Client** avanzato: L&#39;interfaccia utente principale dell&#39;applicazione è un client avanzato, in altre parole un&#39;applicazione nativa (Windows) che comunica con il server applicazione Adobe Campaign  esclusivamente con protocolli Internet standard (SOAP, HTTP, ecc.). Questa console offre una grande facilità di utilizzo per la produttività, utilizza una larghezza di banda molto ridotta (attraverso l&#39;utilizzo di una cache locale) ed è progettata per una facile installazione. Questa console può essere implementata da un browser Internet, può essere aggiornata automaticamente e non richiede alcuna configurazione di rete specifica, perché genera solo traffico HTTP(S).
* **Thin client**: Alcune parti dell&#39;applicazione sono accessibili tramite un semplice browser Web utilizzando un&#39;interfaccia utente HTML, tra cui il modulo di reporting, le fasi di approvazione della consegna, le funzionalità del modulo Distributed Marketing (centrale/locale), il monitoraggio delle istanze, ecc. Questa modalità consente di includere  funzionalità Adobe Campaign in una rete Intranet o in una rete Intranet.
* **Integrazione tramite le API**: In alcuni casi, il sistema può essere chiamato da un&#39;applicazione esterna utilizzando le API dei servizi Web esposte tramite il protocollo SOAP.

## Livello applicazione logico {#logical-application-layer}

 Adobe Campaign è una piattaforma unica con diverse applicazioni che si combinano per creare un&#39;architettura aperta e scalabile. La piattaforma Adobe Campaign  è scritta su un livello di applicazione flessibile ed è facilmente configurabile in base alle esigenze aziendali. In questo modo, le esigenze crescenti dell&#39;azienda vengono soddisfatte sia dal punto di vista funzionale che tecnico. L&#39;architettura distribuita assicura una scalabilità lineare del sistema, che passa da migliaia di messaggi a milioni di messaggi.

 Adobe Campaign si basa su una serie di processi lato server che funzionano insieme.

I processi principali sono:

**Server** applicazioni (web nlserver)

Questo processo espone l&#39;intera gamma di funzionalità di  Adobe Campaign tramite le API dei servizi Web (SOAP - HTTP + XML). Inoltre, può generare in modo dinamico le pagine Web utilizzate per l&#39;accesso basato su HTML (rapporti, moduli Web, ecc.). A tal fine, questo processo include un server Apache Tomcat JSP. Questo è il processo a cui la console si collega.

**Motore** del flusso di lavoro (nlserver wfserver)

Esegue i processi del flusso di lavoro definiti nell&#39;applicazione.

Gestisce inoltre flussi di lavoro tecnici eseguiti periodicamente, tra cui:

* Tracciamento: Recupero e consolidamento dei registri di tracciamento. Consente di recuperare i registri dal server di reindirizzamento e creare gli indicatori aggregati utilizzati dal modulo di reporting.
* Pulizia: Pulizia del database. Utilizzato per eliminare i vecchi record ed evitare la crescita esponenziale del database.
* Fatturazione: Invio automatico di un report di attività per la piattaforma (dimensione del database, numero di azioni di marketing, ecc.).

**Server** di consegna (mta nlserver)

 Adobe Campaign dispone di funzionalità di trasmissione e-mail native. Questo processo funziona come agente di trasferimento di posta SMTP (MTA). Esegue la personalizzazione &quot;one-to-one&quot; dei messaggi e gestisce la loro consegna fisica. Funziona utilizzando i processi di consegna e gestisce i tentativi automatici. Inoltre, quando il tracciamento è abilitato, sostituisce automaticamente gli URL in modo che puntino al server di reindirizzamento.

Questo processo può gestire la personalizzazione e l&#39;invio automatico a un router di terze parti per SMS, fax e posta diretta.

**Server** di reindirizzamento (webmdl nlserver)

Per le e-mail,  Adobe Campaign gestisce automaticamente il tracciamento aperto e dei clic (il monitoraggio transazionale a livello di sito Web è un&#39;ulteriore possibilità). A tal fine, gli URL incorporati nei messaggi e-mail vengono riscritti in modo da puntare a questo modulo, che registra il passaggio dell&#39;utente Internet prima di reindirizzarli all&#39;URL richiesto.

Per garantire la massima disponibilità, questo processo è completamente indipendente dal database: gli altri processi server comunicano con esso utilizzando solo chiamate SOAP (HTTP, HTTP(S) e XML). Tecnicamente, questa funzionalità è implementata in un modulo di estensione di un server HTTP (estensione ISAPI in IIS, o un modulo DSO Apache, ecc.) ed è disponibile solo in Windows.

Sono disponibili anche altri processi più tecnici:

**Gestione delle e-mail** rimbalzate (nlserver inMail)

Questa procedura consente di raccogliere automaticamente le e-mail dalle cassette postali configurate per ricevere i messaggi rimbalzati che vengono restituiti in caso di mancata consegna. Questi messaggi vengono quindi elaborati in base a regole per determinare i motivi della mancata consegna (destinatari sconosciuti, quota superata, ecc.) e per aggiornare lo stato di consegna nel database.

Tutte queste operazioni sono completamente automatiche e preconfigurate.

**Stato** di consegna SMS (nlserver sms)

Questo processo controlla il router SMS per raccogliere lo stato di avanzamento e aggiornare il database.

**Scrittura dei messaggi** di registro (slogd nlserver)

Questo processo tecnico acquisisce i messaggi di registro e traccia generati dagli altri processi e li scrive sul disco rigido. Questo rende disponibili ampie informazioni per la diagnosi in caso di problemi.

**Scrittura dei registri** di tracciamento (nlserver trackinglogd)

Questo processo consente di salvare su disco i registri di monitoraggio generati dal processo di reindirizzamento.

**Scrittura di eventi** in entrata (interazioni nlserver)

Questo processo assicura la registrazione sul disco di eventi in ingresso, nel quadro di Interaction.

**Moduli** di supervisione (controllo nlserver)

Questo processo tecnico agisce come un processo primario che genera gli altri. Inoltre, li controlla e li riavvia automaticamente in caso di incidenti, mantenendo il massimo tempo di attività del sistema.

**Server** delle statistiche (stato nlserver)

In questo modo vengono mantenute le statistiche sul numero di connessioni, sui messaggi inviati per ogni server di posta a cui vengono inviati i messaggi e sui loro limiti (numero massimo di connessioni simultanee, messaggi per ora/ e/o connessione). Consente inoltre di raggruppare più istanze o computer se condividono gli stessi indirizzi IP pubblici.

>[!NOTE]
>
>L&#39;elenco completo  moduli Adobe Campaign è disponibile in [questo documento](../../production/using/operating-principle.md).

## Livello di persistenza {#persistence-layer}

Il database viene utilizzato come livello di persistenza e contiene quasi tutte le informazioni gestite da  Adobe Campaign. Questo include sia i dati funzionali (profili, iscrizioni, contenuto, ecc.), sia i dati tecnici (processi di consegna e registri, registri di monitoraggio, ecc.) e dati di lavoro (acquisti, lead).

L&#39;affidabilità del database è della massima importanza perché la maggior parte dei componenti Adobe Campaign  richiedono l&#39;accesso al database per eseguire le proprie attività (con la notevole eccezione del modulo di reindirizzamento).

La piattaforma è preconfigurata con un data mart centrato sul marketing o può facilmente stare al di sopra di un data mart esistente e di uno schema utilizzando uno dei principali sistemi di gestione del database relazionale (RDBMS). Tutti i dati all&#39;interno del data mart sono accessibili dalla piattaforma  Adobe Campaign tramite chiamate SQL da  Adobe Campaign al database.  Adobe Campaign fornisce inoltre un complemento completo degli strumenti Estrai trasformazione e Carica (ETL) per eseguire l&#39;importazione ed esportazione di dati all&#39;interno e all&#39;esterno del sistema.
