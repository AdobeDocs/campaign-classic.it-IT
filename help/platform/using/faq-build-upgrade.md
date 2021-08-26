---
product: campaign
title: Domande frequenti sull’aggiornamento della build
description: Domande comuni relative agli aggiornamenti della build di Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 85e2135d-a1a3-44f0-a4f9-de38db5c8726
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 5%

---

# Domande frequenti sull’aggiornamento della build {#build-upgrade-faq}

![](../../assets/common.svg)

 Adobe Campaign viene aggiornato regolarmente. Se hai familiarità con le nostre [Note sulla versione](../../rn/using/rn-overview.md) pubblicate, probabilmente sei consapevole del fatto che in media 2/3 versioni secondarie contenenti nuove funzioni, miglioramenti e correzioni vengono rilasciati ogni anno. Inoltre, rilasciamo periodicamente build contenenti solo correzioni cumulative. Questa cadenza regolare di aggiornamenti mira a ottenere il più recente e più grande nelle vostre mani, mantenendo il vostro ambiente completamente sicuro e ovviamente migliorando la vostra esperienza con il nostro prodotto.

È fondamentale che i nostri clienti eseguano la versione più recente di Adobe Campaign. Permette anche all&#39;Adobe di aiutare in modo molto più efficiente nel caso in cui si incontrano problemi - identificare, riprodurre e risolvere un problema su una build precedente richiede in genere più tempo, per non parlare del fatto che alcuni problemi che si possono incontrare possono essere già stati risolti in una build recente.

[!DNL Gold Standard] è la versione con supporto a lungo termine di Campaign Classic. In qualità di utente [!DNL Gold Standard] in hosting, puoi beneficiare automaticamente, senza alcun intervento da parte tua, dell’aggiornamento [!DNL Gold Standard] con la versione stabile più recente. Anche i clienti con implementazioni on-premise e ibride possono beneficiare delle versioni [!DNL Gold Standard]. Se effettui la migrazione da una build precedente, ti consigliamo di eseguire prima l’aggiornamento a questa versione. [Ulteriori informazioni](../../rn/using/gs-overview.md).

## Cos’è un aggiornamento della build?

Un aggiornamento della build si verifica quando il software Adobe Campaign Classic viene aggiornato al numero di build protetto più recente, ma rimane nello stesso livello di build principale/secondario. Ad esempio: Campaign Classic v7 build 9026 per Campaign v7 build 9032.

Ulteriori informazioni [in questa sezione](../../rn/using/rn-overview.md).

## Qual è la versione più recente di Adobe Campaign Classic?

La versione più recente di Campaign Classic, con nuove funzioni e documentazione, è descritta nell&#39;ultima [Note sulla versione](../../rn/using/latest-release.md).

## Come faccio a sapere quale versione eseguo?

Controlla la tua versione dal menu **[!UICONTROL Help > About...]** nella console del client di Adobe Campaign. La casella **[!UICONTROL About]** contiene informazioni dettagliate sulla versione e sulla build in esecuzione sia per la console che per il server.

Ulteriori informazioni [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Cosa significa lo stato della build?

A partire da Campaign Classic 19.2, a ogni build è associato uno stato.

Ulteriori informazioni [in questa sezione](../../rn/using/rn-overview.md).

## Un aggiornamento di una build è la stessa cosa di un aggiornamento di una versione?

No. Un aggiornamento della build è un aggiornamento incrementale all’interno di una determinata versione principale, mentre un aggiornamento della versione è un passaggio da una versione principale all’altra. Gli aggiornamenti delle build sono semplici in quanto non richiedono in genere modifiche importanti dei modelli architettonici, tecnici o di dati.

Gli aggiornamenti delle versioni, invece, solitamente comportano modifiche tecniche significative e, a seconda della profondità della configurazione per un dato cliente, possono richiedere modifiche di configurazione significative e/o una reimplementazione parziale.

Ad esempio, utilizzando le informazioni sul server dalla schermata nella sezione precedente:

* Un aggiornamento della build richiede lo spostamento dalla build 6880 a qualsiasi build successiva alla versione 6880. Ad esempio, v6.1.1 build 8222-v6.1.1 build 866

* Un aggiornamento di una versione richiede lo spostamento dalla versione 6.0.2 a qualsiasi versione successiva alla versione 6.0.2. Ad esempio: build 8666 dalla versione 6.0.1 222 alla versione 6.1.1

## Devo eseguire il backup dei miei dati prima di questi aggiornamenti?

Adobe effettuerà un backup del sistema prima di eventuali modifiche. Tuttavia, se c&#39;è un lavoro di personalizzazione critico che si trova nel sistema non di produzione (server di sviluppo o di staging), è ALTAMENTE CONSIGLIATO esportare che funziona come pacchetto prima di qualsiasi aggiornamento.

![](assets/do-not-localize/how-to-video.png) Per ulteriori informazioni,  [guarda questo video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## Quando avverranno gli aggiornamenti?

Ai clienti verrà offerto un intervallo di date tra cui scegliere. Le modifiche al sistema di produzione non vengono eseguite durante le festività.

Gli aggiornamenti della build possono essere eseguiti da lunedì a giovedì e i venerdì vengono utilizzati solo per le istanze non di produzione.

## Quanto tempo ci vorrà per l’aggiornamento della build?

Il tempo necessario per eseguire un aggiornamento della build dipende da diversi fattori:

* Dimensione del database da sottoporre a backup o ripristino (l&#39;aggiornamento dei database di grandi dimensioni richiede più tempo)
* Le dimensioni degli ambienti (molti dei nostri clienti hanno diversi server che gestiscono funzioni specifiche, con ambienti più grandi che richiedono più tempo per l&#39;aggiornamento)
* La complessità del sistema (alcuni sistemi hanno servizi e connessioni più dipendenti da verificare, che richiedono una verifica della stabilità e delle prestazioni di tali sistemi)

L’aggiornamento della build è un processo in due fasi:

1. Preparazione del sistema per l&#39;aggiornamento - Tenendo conto delle specificità dell&#39;ambiente, questa fase porta essenzialmente a un aggiornamento completo su un ambiente non di produzione. Una volta che l&#39;ambiente aggiornato è stato approvato dal punto di vista tecnico e funzionale, può verificarsi la fase 2. Questa prima fase, a seconda dei fattori di cui sopra, può richiedere da pochi giorni a un paio di settimane.

1. L&#39;aggiornamento stesso - L&#39;ambiente di produzione viene aggiornato. Questa fase viene solitamente eseguita in poche ore. Per gli ambienti molto complessi, si dovrebbe prevedere un tempo di inattività più lungo. Nel caso in cui qualcosa vada storto, viene definita una strategia di rollback che può essere eseguita.

Per ulteriori informazioni, [fare riferimento a questo documento](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html).

## Quali risorse sono necessarie per l’aggiornamento della build?

Il processo di aggiornamento della build richiede le seguenti risorse:

* Architetto di Adobe : per le architetture ospitate o cloud messaging/ibride, l’architetto deve coordinarsi con l’Assistenza clienti.
* Project Manager - Ospitato: il team di hosting collaborerà con il team di assistenza clienti e il cliente per coordinare la cronologia dell’aggiornamento per tutte le istanze.
* Amministratore Adobe Campaign - Ospitato: il team di hosting esegue l&#39;aggiornamento.
* Operatore Adobe Campaign\utente marketing : l&#39;operatore esegue test sulle istanze di sviluppo, test e produzione.

## Come posso preparare l’aggiornamento della build?

Nei sistemi di sviluppo e staging, esporta qualsiasi lavoro critico e deve essere conservato. Per ulteriori informazioni, [guarda questo video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Aggiorna la tua conoscenza dei flussi di lavoro e delle consegne dei percorsi critici sviluppati nei tuoi run book (o dal team/partner di consulenza) esaminando la documentazione fornita al tuo team al termine dell’implementazione.

Identificare volumi ridotti o tempi di traffico ridotti che sarebbero ideali per le finestre di manutenzione in quanto produrranno l&#39;impatto più basso sul business.

Rivedi la nostra [lista di controllo per l&#39;aggiornamento della build qui sotto](#check-list) e i tuoi piani di test e assicurati che le risorse che possono eseguire questi test siano disponibili entro 24-48 ore. del completamento di un aggiornamento.

Per ulteriori informazioni, [fare riferimento a questo documento](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html).

## Gli aggiornamenti possono essere eseguiti di notte o durante le ore di inattività?

Gli aggiornamenti possono essere eseguiti fuori orario. Si consiglia sempre di aggiornare l&#39;ambiente durante le ore di inattività aziendali quando nessun utente aziendale è connesso all&#39;istanza.

## Quali sono i costi associati a un aggiornamento della build?

Non vi è alcun costo per installare l&#39;aggiornamento della build per i clienti ospitati. Se nel sistema sono presenti sviluppi personalizzati, il Cliente dovrà identificare le risorse necessarie per testare tali sviluppi dopo l&#39;aggiornamento e per correggere eventuali problemi riscontrati con tali sviluppi personalizzati.

## Sarà possibile accedere all’istanza durante il processo di aggiornamento?

No. Il server viene arrestato durante un aggiornamento per garantire che l’integrità dei dati venga mantenuta durante l’aggiornamento del prodotto. Una volta completato, viene riavviato e tutti i servizi riprendono.

## Le e-mail continueranno a essere inviate dal Centro messaggi durante il processo di aggiornamento?

Quando l’aggiornamento avviene per Message Center (Centro messaggi) (RT), non invia e-mail dall’istanza. Nota: tutti i processi che vengono interrotti quando un sistema Campaign viene spento vengono ripresi automaticamente al riavvio del sistema. Sono inclusi consegne, tracciamento e calcoli di metriche attivi o pianificati per le consegne inviate in precedenza.

## I flussi di lavoro continueranno a essere eseguiti e a inviare le consegne?

No. Durante l’aggiornamento della build, i servizi di flusso di lavoro e di posta vengono entrambi interrotti. Ciò significa che i flussi di lavoro non verranno eseguiti e che le consegne non verranno inviate. Essi riprenderanno una volta riavviato il sistema. Tuttavia, Adobe consiglia vivamente di controllare tutti i flussi di lavoro dei percorsi critici dopo un aggiornamento per garantire che siano in esecuzione e in buona salute.

## I miei collegamenti di tracciamento continueranno a funzionare durante l’aggiornamento?

I collegamenti di tracciamento funzioneranno durante l’aggiornamento. Non è possibile inviare nuove e-mail durante l’aggiornamento, ma i collegamenti di tracciamento inclusi nelle e-mail già inviate saranno operativi.

## È necessario essere disponibili durante il processo di aggiornamento della build?

Sì. I clienti devono fornire ad Adobe un punto di contatto disponibile durante o subito dopo l’aggiornamento della propria istanza di produzione.  L’Adobe contatterà questa persona via e-mail a meno che non vengano presi altri accordi. Ciò garantirà una transizione senza problemi e una convalida immediata delle attività critiche. Adobe contatterà il cliente una volta che l&#39;aggiornamento della build è stato completato per la conferma.

## Devo aggiornare la console client?

Sì. La console client deve trovarsi nella stessa build dell’istanza server. Una volta completato l’aggiornamento, nella console client viene richiesto di eseguire l’aggiornamento alla build più recente per assicurarsi che rimanga allineata alla build del server.

## Qual è il piano di rollback? Vengono conservati i backup dei dati?

Il piano di rollback consiste nel ripristinare il sistema con l&#39;ultimo backup disponibile. I backup vengono archiviati per 7 giorni per i clienti del centro dati e per 14 giorni per i clienti di Amazon Web Service (AWS).

## Quanto tempo ci vorrà per eseguire il rollback?

Dipende dalle dimensioni del backup del database. Il tempo medio necessario per il completamento è di 4 ore.

## Quali tipi di test vengono eseguiti sul sistema dopo l’aggiornamento?

Fai riferimento alla [lista di controllo per l&#39;aggiornamento della build qui sotto](#check-list).

## Che tipo di test devo eseguire dopo l’aggiornamento?

Gli ambienti di sviluppo e di stage vengono aggiornati in sequenza o insieme, ma prima di aggiornare l’istanza di produzione è necessaria un’autorizzazione. Questo consente a ogni cliente di eseguire test approfonditi prima di annullare qualsiasi modifica alla produzione.

Vedi l&#39;elenco [elenco di controllo per l&#39;aggiornamento della build qui sotto](#check-list). I clienti devono eseguire test simili e altri test necessari per l’ambiente.

## Quanto spesso devo eseguire un aggiornamento della build?

Al fine di garantire prestazioni, disponibilità e sicurezza ottimali del sistema, Adobe collabora con i clienti per garantire che i sistemi vengano aggiornati almeno una volta all&#39;anno.

## Verrà eseguito un arresto per con un aggiornamento della build?

Sì. Il server viene arrestato durante un aggiornamento per garantire che l’integrità dei dati venga mantenuta durante l’aggiornamento del prodotto. Una volta completato, viene riavviato e tutti i servizi riprendono.

## Chi devo contattare per aprire il ticket di aggiornamento della build?

Se si verificano problemi dopo un aggiornamento della build, contatta l’ [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). L’Assistenza clienti pianifica le date della build e apre i ticket relativi all’aggiornamento della build.

Ulteriori informazioni in [Opzioni di Aiuto e supporto per Campaign Classic](../../support.md)

## Lista di controllo per l&#39;aggiornamento della build {#check-list}

### Elenco di controllo post aggiornamento del server di messaggistica cloud

1. Inviare una consegna del test
   1. Convalida i registri di consegna e il relativo flusso di lavoro
   1. Convalida i registri di tracciamento aggiornati
   1. Convalida della pagina speculare e collegamenti di tracciamento
1. Conferma che tutti i flussi di lavoro tecnici siano in stato di avvio
1. Verifica che anche tutti i processi siano attivi

### Elenco di controllo post aggiornamento del server di marketing

* Puoi accedere al server? Controlla che la console del client di Campaign funzioni senza errori o avvisi.
* Dopo l’aggiornamento, assicurati di utilizzare la stessa versione della console della versione di build.
* Hai applicazioni web che inseriscono dati nel database Campaign? In caso affermativo, eseguili e
verifica che possano inserire nuovi record tramite API.
* Puoi inviare correttamente un’e-mail di test? Crea una nuova consegna utilizzando un modello noto, inviala a
un solo destinatario del test, verifica personalizzazione, collegamento non sub, pagina speculare funziona tutto.
* Sono in esecuzione tutti i flussi di lavoro dei percorsi critici? Controlla flussi di lavoro, apri giornale di registrazione flussi di lavoro, verifica
che non ci sono errori.
* Tutte le cartelle sono presenti, visibili e accessibili? Sfoglia cartelle diverse e controlla.
tutto il contenuto viene visualizzato e presente.
* Le consegne vengono effettuate con il fuso orario corretto?

   * Verifica la data di creazione e la data di modifica con la marca temporale e il fuso orario
   * Verifica che l’esecuzione della pianificazione funzioni in un flusso di lavoro all’ora specificata
   * Recupera elenco di flussi di lavoro in stato di PAUSED e FAILED (PAUSED e FAILED). Avviare e monitorare
   * Esegui test AB per uno scenario
   * Test delle notifiche push e delle relative funzionalità di tracciamento per i collegamenti profondi
   * Test invio di SMS
   * Se hai un FDA esterno connesso, verifica se i dati vengono inviati in entrambi i modi
   * Se utilizzi integrazioni come Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, verifica se funzionano ancora come prima

**Vedi anche**

* [Esecuzione di un aggiornamento della build](../../production/using/build-upgrade.md)
* [Note sulla versione di Campaign Classic](../../rn/using/rn-overview.md)
* [Opzioni di aiuto e supporto per Campaign Classic](../../support.md)
* [[!DNL Gold Standard] programma](../../rn/using/gs-overview.md)
