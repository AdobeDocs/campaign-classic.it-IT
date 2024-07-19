---
product: campaign
title: Domande frequenti sull’aggiornamento della build
description: Domande comuni relative agli aggiornamenti della build di Campaign
feature: Upgrade, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 85e2135d-a1a3-44f0-a4f9-de38db5c8726
source-git-commit: f39dc6077a7ddc3fb9b53d4082c08e65e7683f10
workflow-type: tm+mt
source-wordcount: '2026'
ht-degree: 1%

---

# Domande frequenti sull’aggiornamento della build {#build-upgrade-faq}


Adobe Campaign viene aggiornato regolarmente. Se conosci le nostre [Note sulla versione](../../rn/using/rn-overview.md) pubblicate, probabilmente sai che ogni anno vengono rilasciate in media 2/3 versioni secondarie complete di nuove funzioni, miglioramenti e correzioni. Inoltre, rilasciamo periodicamente build contenenti solo correzioni cumulative. Questa frequenza regolare di aggiornamenti mira a ottenere il massimo e più recente nelle tue mani, mantenendo l’ambiente completamente sicuro e ovviamente migliorando la tua esperienza con il nostro prodotto.

È fondamentale che i nostri clienti eseguano la versione più recente di Adobe Campaign. Consente inoltre ad Adobe di aiutare in modo molto più efficiente in caso di problemi: in genere, identificare, riprodurre e risolvere un problema in una build precedente richiede più tempo, per non parlare del fatto che alcuni problemi che potresti incontrare potrebbero essere già stati risolti in una build recente.

In qualità di utente in hosting, puoi beneficiare automaticamente, senza alcun intervento da parte tua, dell’aggiornamento annuale di Campaign con la versione stabile più recente. Anche i clienti con implementazioni on-premise e ibride possono beneficiare di questa versione. Se effettui la migrazione da una build precedente, ti consigliamo di eseguire prima l’aggiornamento a questa versione. [Ulteriori informazioni](../../rn/using/rn-overview.md).

## Che cos’è un aggiornamento della build?

Un aggiornamento della build si verifica quando il software Adobe Campaign Classic viene aggiornato al numero di build sicuro più recente, ma rimane nello stesso livello di build principale/secondario. Ad esempio: da Campaign Classic v7 build 9026 a Campaign v7 build 9032.

Per ulteriori informazioni, consulta [questa sezione](../../rn/using/rn-overview.md).

## Qual è la versione più recente di Adobe Campaign Classic?

La versione più recente di Campaign Classic, incluse le nuove funzionalità e la documentazione, è illustrata in dettaglio nelle [Note sulla versione](../../rn/using/latest-release.md) più recenti.

## Come posso sapere quale versione sto eseguendo?

Controlla la versione dal menu **[!UICONTROL Help > About...]** nella console del client Adobe Campaign. La casella **[!UICONTROL About]** contiene informazioni dettagliate sulla versione e sulla build in esecuzione sia per la console che per il server.

Per ulteriori informazioni, consulta [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Cosa significa lo stato della build?

A partire da Campaign Classic 19.2, a ogni build viene associato uno stato.

Per ulteriori informazioni, consulta [questa sezione](../../rn/using/rn-overview.md).

## Un aggiornamento della build è uguale a un aggiornamento della versione?

No. Un aggiornamento della build è un aggiornamento incrementale all’interno di una determinata versione principale, mentre un aggiornamento della versione è un cambiamento da una versione principale a un’altra. Gli aggiornamenti della build sono semplici, in quanto in genere non comportano alcuna modifica importante a livello architetturale, tecnico o di modello di dati.

Gli aggiornamenti delle versioni, d’altra parte, di solito sono accompagnati da modifiche tecniche significative e, a seconda della profondità della configurazione per un determinato cliente, possono richiedere modifiche significative della configurazione e/o una reimplementazione parziale.

Ad esempio, utilizzando le informazioni sul server tratte dalla schermata della sezione precedente:

* Un aggiornamento della build richiederebbe il passaggio dalla build 9342 a qualsiasi build maggiore di 9342. Ad esempio, da v7.1 a v7.1 build 9342

* Un aggiornamento della versione richiederebbe il passaggio da una versione principale precedente a una versione più recente.

## È necessario eseguire il backup dei dati prima di questi aggiornamenti?

Adobe esegue un backup del sistema prima di qualsiasi modifica. Tuttavia, se nel sistema non di produzione (server di sviluppo o di staging) è presente un lavoro di personalizzazione critico, si CONSIGLIA VIVAMENTE di esportare il lavoro come pacchetto prima di qualsiasi aggiornamento.

<!--
![](assets/do-not-localize/how-to-video.png) For more information, [watch this how to video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).-->

## Quando avverranno gli aggiornamenti?

Ai clienti verrà offerto un intervallo di date tra cui scegliere. Le modifiche al sistema di produzione non vengono eseguite durante le festività.

Gli aggiornamenti della build possono essere eseguiti da lunedì a giovedì e i venerdì vengono utilizzati solo per le istanze non di produzione.

## Quanto tempo ci vorrà per l’aggiornamento della build?

Il tempo necessario per eseguire un aggiornamento della build dipende da diversi fattori:

* Dimensione del database di cui eseguire il backup o il ripristino (i database di grandi dimensioni richiedono più tempo per l&#39;aggiornamento)
* Le dimensioni degli ambienti (molti dei nostri clienti hanno diversi server che gestiscono funzioni specifiche, con ambienti più grandi che richiedono più tempo per l’aggiornamento)
* La complessità del sistema (alcuni sistemi dispongono di servizi e connessioni più dipendenti da verificare, che richiedono la verifica della stabilità e delle prestazioni di tali sistemi)

L’aggiornamento della build è un processo in due fasi:

1. Preparazione del sistema per l&#39;aggiornamento: tenendo conto delle specificità dell&#39;ambiente, questa fase comporta essenzialmente un aggiornamento completamente qualificato in un ambiente non di produzione. Una volta che l&#39;ambiente aggiornato è stato approvato dal punto di vista tecnico e funzionale, può avvenire la fase 2. Questa prima fase, a seconda dei fattori di cui sopra, può richiedere da alcuni giorni a un paio di settimane.

1. L’aggiornamento stesso: l’ambiente di produzione viene aggiornato. Questa fase viene generalmente eseguita in poche ore. Per gli ambienti molto complessi è previsto un tempo di inattività più lungo. In caso di problemi, viene definita una strategia di rollback che può essere eseguita.

Per ulteriori informazioni, [fare riferimento a questo documento](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html).

## Quali risorse sono necessarie per l’aggiornamento della build?

Il processo di aggiornamento della build richiede le seguenti risorse:

* Architetto di Adobe: per le architetture di messaggistica in hosting o cloud/ibride, l’architetto deve coordinarsi con l’Assistenza clienti.
* Project Manager - Hosted: il team di hosting collaborerà con il team dell’Assistenza clienti e con il cliente per coordinare la tempistica dell’aggiornamento per tutte le istanze.
* Amministratore Adobe Campaign - Ospitato: il team di hosting esegue l’aggiornamento.
* Operatore Adobe Campaign\utente marketing: l’operatore esegue test sulle istanze di sviluppo, test e produzione.

## Come posso prepararmi per l’aggiornamento della build?

Nei sistemi di sviluppo e staging, esporta qualsiasi lavoro critico che deve essere mantenuto.

<!--For more information please [watch this how to video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).-->

Aggiorna la tua conoscenza dei flussi di lavoro e delle consegne dei percorsi critici sviluppati nei libri di esecuzione (o dal team/partner di consulenza) esaminando la documentazione fornita al team al termine dell’implementazione.

Identifica i tempi di traffico ridotti o ridotti che sarebbero ideali per le finestre di manutenzione in quanto produrrebbero l’impatto aziendale più basso.

Controlla la [lista di controllo per l&#39;aggiornamento della build seguente](#check-list) e i tuoi piani di test e assicurati che le risorse in grado di eseguire questi test siano disponibili entro 24-48 ore. del completamento di un aggiornamento.

Per ulteriori informazioni, [consulta questa sezione](../../production/using/build-upgrade.md).

## Gli aggiornamenti possono essere eseguiti di notte o fuori orario di lavoro?

Gli aggiornamenti possono essere eseguiti fuori orario. Si consiglia sempre di aggiornare l’ambiente durante gli orari di ufficio, quando nessun utente aziendale è connesso all’istanza.

## Quali sono i costi associati a un aggiornamento della build?

L’installazione dell’aggiornamento della build per i clienti in hosting non comporta costi. Se nel sistema sono presenti sviluppi personalizzati, il Cliente dovrà identificare le risorse necessarie per testare tali sviluppi dopo l&#39;aggiornamento e per correggere eventuali problemi rilevati con tali sviluppi personalizzati.

## Sarà possibile accedere all’istanza durante il processo di aggiornamento?

No. Il server viene arrestato durante un aggiornamento per garantire l&#39;integrità dei dati durante l&#39;aggiornamento del prodotto. Una volta completato, viene riavviato e tutti i servizi riprendono.

## Posso ancora utilizzare la mia istanza Campaign durante il processo di aggiornamento?

No. L’Adobe consiglia di disabilitare tutte le operazioni nella campagna durante il periodo di manutenzione per evitare la perdita o l’assenza di dati. Non devi creare o distribuire campagne, query, flussi di lavoro o consegne durante l’aggiornamento.

## Le e-mail continueranno a essere inviate dal Centro messaggi durante il processo di aggiornamento?

Quando si esegue l’aggiornamento per il Centro messaggi (RT), non invierà e-mail dall’istanza. Nota: tutti i processi interrotti alla chiusura di un sistema Campaign vengono ripresi automaticamente al riavvio del sistema. Ciò include consegne attive o pianificate, calcoli di tracciamento e metriche per le consegne inviate in precedenza.

## I flussi di lavoro continueranno a essere eseguiti e a inviare le consegne?

No. Durante l’aggiornamento della build, il flusso di lavoro e i servizi di posta vengono entrambi interrotti. Ciò significa che i flussi di lavoro non verranno eseguiti e le consegne non verranno inviate. Riprenderanno una volta riavviato il sistema. Tuttavia, Adobe consiglia vivamente di controllare tutti i flussi di lavoro dei percorsi critici dopo un aggiornamento per verificarne l’esecuzione e l’integrità.

## I miei collegamenti di tracciamento continueranno a funzionare durante l’aggiornamento?

A partire da Campaign Classic v7.3.5, i collegamenti di tracciamento sulle e-mail già inviate continuano a funzionare durante l’aggiornamento.

## Devo essere disponibile durante il processo di aggiornamento della build?

Sì. I clienti devono fornire all’Adobe un punto di contatto disponibile durante o immediatamente dopo l’aggiornamento della loro istanza di produzione.  L’Adobe contatterà questa persona via e-mail, a meno che non vengano presi accordi diversi. Ciò garantirà una transizione agevole e la convalida immediata delle attività critiche. L’Adobe contatterà il Cliente una volta completato l’aggiornamento della build per la conferma.

## Devo aggiornare la console client?

Sì. La console client deve trovarsi nella stessa build dell’istanza del server. Al termine dell’aggiornamento, la console client dovrà richiedere di eseguire l’aggiornamento alla build più recente per garantire che rimanga allineata con la build del server.

## Qual è il piano di ripristino? Vengono conservati i backup dei dati?

Il piano di ripristino consiste nel ripristinare il sistema con l&#39;ultimo backup disponibile. I backup vengono archiviati per 7 giorni per i clienti del centro dati e per 14 giorni per i clienti su Amazon Web Service (AWS).

## Quanto tempo è necessario per eseguire il rollback?

Dipende dalle dimensioni del backup del database. Il tempo medio necessario per il completamento è di 4 ore.

## Quali tipi di test vengono eseguiti sul sistema dopo l’aggiornamento?

Consulta l&#39;[elenco di controllo per l&#39;aggiornamento della build seguente](#check-list).

## Quale tipo di test devo eseguire dopo l’aggiornamento?

Gli ambienti di sviluppo e staging vengono aggiornati in sequenza o insieme, ma è necessario un abbonamento prima di aggiornare l’istanza di produzione. Questo consente a ciascun cliente di eseguire test approfonditi prima di approvare qualsiasi modifica alla produzione.

Vedi l&#39;elenco di controllo per l&#39;aggiornamento della build [di seguito](#check-list). I clienti devono eseguire test simili e quelli di cui potrebbero aver bisogno per l’ambiente.

## Con quale frequenza devo eseguire un aggiornamento della build?

Per garantire prestazioni, disponibilità e sicurezza ottimali, Adobe collabora con i clienti per garantire che i sistemi vengano aggiornati almeno una volta all&#39;anno.

## Si verificherà un arresto del sistema per con un aggiornamento della build?

Sì. Il server viene arrestato durante un aggiornamento per garantire l&#39;integrità dei dati durante l&#39;aggiornamento del prodotto. Una volta completato, viene riavviato e tutti i servizi riprendono.

## Chi devo contattare per aprire il ticket di aggiornamento della build?

Se riscontri problemi dopo un aggiornamento della build, contatta [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). L’Assistenza clienti pianifica le date di build e apre i ticket relativi all’aggiornamento della build.

Ulteriori informazioni in [Opzioni di assistenza e supporto per Campaign Classic](../../support.md)

## Elenco di controllo per l’aggiornamento della build {#check-list}

### Elenco di controllo post-aggiornamento del server di messaggistica cloud

1. Inviare una consegna di prova
   1. Convalidare i registri di consegna e il relativo flusso di lavoro
   1. Verificare che i registri di tracciamento siano aggiornati
   1. Convalidare la pagina speculare e i collegamenti di tracciamento
1. Conferma che tutti i flussi di lavoro tecnici siano in stato avviato
1. Verifica che tutti i processi siano attivi

### Elenco di controllo post-aggiornamento server di marketing

* È possibile accedere al server? Controlla che la console client di Campaign funzioni senza pop-up di errore/avviso.
* Dopo l’aggiornamento, assicurati di utilizzare la stessa versione della console della versione di build.
* Esistono applicazioni web che inseriscono dati nel database di Campaign? In tal caso, eseguili e
verifica di poter inserire nuovi record tramite API.
* È possibile inviare un messaggio e-mail di test correttamente? Crea una nuova consegna utilizzando un modello noto, invialo a
un destinatario del test, verifica la personalizzazione, annulla collegamento, pagina mirror tutto funziona.
* Sono in esecuzione tutti i flussi di lavoro dei percorsi critici? Controlla flussi di lavoro, apri giornale di registrazione flussi di lavoro, verifica
che non ci sono errori.
* Tutte le cartelle sono presenti, visibili e accessibili? Sfoglia diverse cartelle e seleziona.
tutti i contenuti vengono visualizzati e presenti.
* Le consegne vengono consegnate con il fuso orario corretto?

   * Verifica la data di creazione e la data di modifica con il timestamp e il fuso orario
   * Verificare che l&#39;esecuzione del modulo di pianificazione funzioni in un flusso di lavoro all&#39;ora specificata
   * Recupera l’elenco dei flussi di lavoro in stato PAUSED e FAILED. Avviarle e monitorarle
   * Eseguire AB Testing per uno scenario
   * Test delle notifiche push e della relativa funzionalità di tracciamento per i collegamenti profondi
   * Testare l’invio di SMS
   * Se hai connesso un FDA esterno, verifica se i dati vengono inviati in entrambi i modi
   * Se utilizzi integrazioni quali Adobe Campaign-Adobe Experience Manager e Adobe Campaign-Adobe Analytics, verifica se funzionano ancora come prima

**Vedi anche**

* [Esecuzione di un aggiornamento della build](../../production/using/build-upgrade.md)
* [Note sulla versione di Campaign Classic](../../rn/using/rn-overview.md)
* [Opzioni di assistenza e supporto per Campaign Classic](../../support.md)
* [Programma di aggiornamento annuale](../../rn/using/rn-overview.md#yearly-upgrade)
