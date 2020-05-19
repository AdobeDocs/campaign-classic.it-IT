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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---


# Privacy e raccomandazioni{#privacy-and-recommendations}

## Informazioni sulla privacy e il consenso {#about-privacy-and-consent}

Adobe Campaign è uno strumento potente per la raccolta e l&#39;elaborazione di una quantità estremamente elevata di dati, comprese informazioni personali. Invitiamo tutti gli utenti di Adobe Campaign a lavorare nell&#39;ambito della legislazione (DPA, CAN-SPAM, Direttiva Europea sulla Privacy e le Comunicazioni Elettroniche, GDPR europea, CCPA, ecc.), a fare un uso responsabile ed etico delle informazioni personali e ad astenersi dall&#39;inviare e-mail, notifiche push e messaggi SMS non richiesti (&quot;spam&quot;). Crediamo fermamente nei principi del marketing delle autorizzazioni per promuovere il valore e la fedeltà della vita dei clienti, e pertanto proibiamo severamente l&#39;uso di Adobe Campaign per inviare messaggi non richiesti.

Per ulteriori informazioni, consulta [privacy](https://www.adobe.com/privacy/marketing-cloud.html)di Adobe Experience Cloud.

Dedica il tempo a seguire l&#39;elenco [di controllo sulla](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html) sicurezza e la privacy per scoprire gli elementi chiave da verificare in materia di sicurezza e privacy.

## Gestione della privacy {#privacy-management}

Adobe Campaign offre una serie di strumenti per aiutarti a rispettare le normative sulla privacy (GDPR, CCPA e altro ancora.)

Il GDPR (General Data Protection Regulation, Regolamento generale sulla protezione dei dati) è la normativa dell’Unione europea sulla privacy che armonizza e aggiorna i requisiti in materia di protezione dei dati. Il Regolamento GDPR si applica ai clienti Adobe Campaign che detengono dati per i soggetti dati residenti nell&#39;UE.

CCPA (California Consumer Privacy Act) offre ai residenti della California nuovi diritti in merito alle loro informazioni personali e impone loro responsabilità in materia di protezione dei dati a determinate entità che conducono attività commerciali in California.

Oltre alla gestione del consenso, alle impostazioni di conservazione dei dati e alla gestione dei diritti, offriamo, in qualità di processore dati, funzionalità aggiuntive per facilitare la disponibilità del titolare del trattamento per determinate richieste di privacy.

In [questo articolo](https://helpx.adobe.com/campaign/kb/acc-privacy.html), scoprirai in che modo Adobe Campaign ti aiuta a gestire le diverse funzionalità della chiave per la privacy: Diritto di accesso, Diritto di essere Dimenticato, consenso, conservazione dei dati e ruoli utente. Troverai anche le best practice per aiutarti a rispettare la Privacy quando utilizzi la nostra soluzione.

## Cookie e funzionalità di tracciamento {#cookies-and-tracking-capabilities}

Grazie alle sue funzionalità di tracciamento, Adobe Campaign consente di monitorare l&#39;esplorazione dei destinatari della distribuzione su un sito Web. A tal fine, Adobe Campaign utilizza i cookie di sessione e i cookie permanenti.

La direttiva europea 2009/136/CE sulla privacy e le comunicazioni elettroniche e il regolamento generale europeo sulla protezione dei dati (GDPR) stabiliscono che le aziende richiedono l&#39;accordo degli utenti dei siti Web prima di installare qualsiasi cookie. Dovete informare gli utenti che i vostri siti sono dotati di strumenti di monitoraggio Web tramite una richiesta di autorizzazione (che viene visualizzata sopra la pagina, ad esempio) con una casella di controllo per autorizzare l&#39;installazione dei cookie, o aggiungere un banner nella parte superiore della prima pagina in cui accedono, ecc. Le finestre a comparsa dovrebbero essere evitate in quanto spesso bloccate dai browser.

La configurazione della gestione del tracciamento utente è disponibile per le applicazioni Web e le pagine di destinazione con un banner di rifiuto. Fare riferimento a [questa pagina](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign utilizza due tipi di cookie:

1. Un cookie di sessione (nlid): contiene l’identificatore dell’e-mail inviata al contatto (BroadlogId) e l’identificatore del modello di messaggio (deliveryId). Viene aggiunto quando il contatto fa clic su un URL incluso in un&#39;e-mail inviata da Adobe Campaign e consente di tracciarne il comportamento sul Web. Questo cookie di sessione viene cancellato automaticamente alla chiusura del browser. Il contatto può configurare il browser per rifiutare i cookie.
1. Un cookie permanente (uuid230): consente di identificare gli utenti che interagiscono con Adobe Campaign quando visitano un sito Web. Viene utilizzato da Adobe Campaign per calcolare il numero di clic e stimare la percentuale di trasferimento durante una campagna di marketing. Viene posizionato quando il contatto fa clic in un&#39;e-mail, compila un modulo in Adobe Campaign o durante la chiamata al motore di interazione in entrata. L&#39;utente può configurare il proprio browser per eliminarlo o rifiutarlo.

## Integrità del database {#database-integrity}

Adobe Campaign offre numerose funzioni. Pertanto utilizza una complessa struttura di database. Il database contiene molte tabelle, campi, collegamenti e indici. Alcune tabelle intermedie non vengono visualizzate nell&#39;interfaccia. Il software crea, elimina o modifica automaticamente alcuni collegamenti, campi e indici. Solo interfacce Adobe Campaign (interfaccia grafica, programma di importazione, modulo server, modulo Web, server di consegna, aggiunta di campi, estensione del database, ecc.) può modificare il contenuto del database conservandone l&#39;integrità.

**Non modificare mai il contenuto o la struttura del database utilizzando strumenti diversi da questo software**. Tali modifiche verrebbero molto probabilmente a danneggiare il database, causando: modifica accidentale o perdita di collegamenti, creazione di record fantasma o collegamenti, messaggi di errore gravi, ecc., e annullamento del contratto di garanzia e supporto tecnico fornito da Adobe Campaign.

Nel sistema Adobe Campaign, tutti i dati sono memorizzati nel database. Il corretto funzionamento dell&#39;intero sistema Adobe Campaign dipende dalla disponibilità di questi dati per: moduli Web per iscrizione, amministrazione e annullamento dell’iscrizione, schermate di amministrazione, code di distribuzione, meccanismi di ottimizzazione della distribuzione, ecc.

## Apache Tomcat {#apache-tomcat}

Adobe Campaign include Apache Tomcat, sviluppato da Apache Software Foundation ( [https://www.apache.org/](https://www.apache.org/)).
