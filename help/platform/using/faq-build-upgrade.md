---
title: Domande frequenti sull'aggiornamento della build
description: Domande comuni relative agli aggiornamenti delle build di Campaign
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: tm+mt
source-git-commit: cb96a238f4c8e413377ce6102b065b91badfe6db
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 2%

---


# Domande frequenti sull&#39;aggiornamento build {#build-upgrade-faq}

 Adobe Campaign viene aggiornato regolarmente. Se hai familiarità con le nostre note [sulla](../../rn/using/rn-overview.md)versione pubblicate, probabilmente sei a conoscenza del fatto che in media 2/3 versioni secondarie con nuove funzioni, miglioramenti e correzioni vengono rilasciati ogni anno. Inoltre, rilasciamo periodicamente build con solo correzioni cumulative. Questa cadenza regolare di aggiornamenti mira a ottenere l&#39;ultimo e più grande nelle vostre mani, mantenendo il vostro ambiente completamente sicuro e ovviamente migliorando la vostra esperienza con il nostro prodotto.

È fondamentale che i nostri clienti eseguano la versione più recente di  Adobe Campaign. Permette anche  Adobe di aiutare molto più efficacemente in caso di problemi - identificare, riprodurre e risolvere un problema su una vecchia build richiede generalmente più tempo, per non parlare del fatto che alcuni problemi che si possono incontrare possono essere già stati risolti in una recente build.

Abbiamo quindi avviato il programma [Gold Standard](https://helpx.adobe.com/it/campaign/kb/gold-standard.html) per collaborare con i clienti per aggiornare i loro ambienti in modo proattivo e regolare.

## Cos&#39;è un aggiornamento di build?

Un aggiornamento della build è il momento in cui il software Adobe Campaign Classic viene aggiornato al numero di build più recente, ma rimane nello stesso livello di build principale/minore. Ad esempio: Campaign Classic v7 build 9026 in Campaign v7 build 9032.

Ulteriori informazioni [in questa sezione](../../rn/using/rn-overview.md).

## Qual è l&#39;ultima versione di Adobe Campaign Classic?

La versione Campaign Classic più recente, con nuove funzioni e documentazione, è dettagliata nelle note sulla [versione più recenti](../../rn/using/latest-release.md).

## Come posso sapere quale versione sto eseguendo?

Controllate la versione dal **[!UICONTROL Help > About...]** menu nella  console Adobe Campaign Client. La **[!UICONTROL About]** casella contiene informazioni dettagliate sulla versione e sulla build in esecuzione sia per la console che per il server.

Ulteriori informazioni [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Cosa significa lo stato di compilazione?

A partire dal Campaign Classic 19.2, a ciascuna build viene associato uno stato.

Ulteriori informazioni [in questa sezione](../../rn/using/rn-overview.md).

## L&#39;aggiornamento di una build è uguale all&#39;aggiornamento di una versione?

No. Un aggiornamento di build è un aggiornamento incrementale all&#39;interno di una determinata versione principale, mentre un aggiornamento di versione è un passaggio da una versione principale all&#39;altra. Gli aggiornamenti delle build sono semplici, in quanto non comportano in genere modifiche importanti dei modelli architettonici, tecnici o di dati.

Gli aggiornamenti di versione, d&#39;altra parte, solitamente comportano modifiche tecniche significative e, a seconda della profondità della configurazione per un determinato cliente, possono richiedere modifiche significative della configurazione e/o una reimplementazione parziale.

Ad esempio, utilizzando le informazioni sul server dalla schermata nella sezione precedente:

* L&#39;aggiornamento di una build comporterebbe il passaggio dalla build 6880 a qualsiasi build superiore a 6880. Ad esempio, da v6.1.1 build 8222 a v6.1.1 build 8666

* Un aggiornamento di una versione comporterebbe il passaggio dalla versione 6.0.2 a qualsiasi versione successiva alla 6.0.2.  Ad esempio: v6.0.1 build 2222 a v6.1.1 build 8666

## Devo eseguire il backup dei miei dati prima di questi aggiornamenti?

 Adobe eseguirà un backup del sistema prima di qualsiasi modifica. Tuttavia, se esiste un lavoro di personalizzazione critico che si trova nel sistema non di produzione (server di sviluppo o di pre-produzione), è ALTAMENTE CONSIGLIATO esportare il lavoro come pacchetto prima di qualsiasi aggiornamento.

Per ulteriori informazioni, [guardate questo video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## Quando avranno luogo gli aggiornamenti?

Ai clienti verrà offerto un intervallo di date tra cui scegliere. Le modifiche al sistema di produzione non vengono eseguite durante le festività.

Gli aggiornamenti delle build possono essere eseguiti da lunedì a giovedì e i venerdì vengono utilizzati solo per le istanze non di produzione.

## Quanto tempo ci vorrà per l&#39;aggiornamento della build?

Il tempo necessario per eseguire un aggiornamento della build dipende da diversi fattori:

* Dimensione del database da sottoporre a backup o ripristino (l&#39;aggiornamento dei database di dimensioni maggiori richiede più tempo)
* Le dimensioni degli ambienti (molti dei nostri clienti hanno diversi server che gestiscono funzioni specifiche, con ambienti più grandi che richiedono più tempo per effettuare l&#39;aggiornamento)
* La complessità del sistema (alcuni sistemi hanno più servizi e connessioni dipendenti da verificare, che richiedono la verifica della stabilità e delle prestazioni di tali sistemi)

L&#39;aggiornamento della build è un processo in due fasi:

1. Preparazione del sistema per l&#39;aggiornamento - Tenendo conto delle specificità dell&#39;ambiente, questa fase porta essenzialmente a un upgrade completo su un ambiente non di produzione. Una volta che l&#39;ambiente aggiornato è stato reso verde da un punto di vista tecnico e funzionale, la fase 2 può accadere. Questa prima fase, a seconda dei fattori sopra citati, può richiedere da alcuni giorni a un paio di settimane.

1. L&#39;aggiornamento stesso - L&#39;ambiente di produzione viene aggiornato. Questa fase viene solitamente eseguita in poche ore. Per gli ambienti molto complessi, è opportuno prevedere tempi di inattività più lunghi. Nel caso in cui qualcosa vada storto, viene definita una strategia di rollback che può essere eseguita.

For more information, [refer to this document](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html).

## Quali risorse sono necessarie per l&#39;aggiornamento della build?

Il processo di aggiornamento della build richiede le risorse seguenti:

*  architetto Adobe - Per architetture ospitate o cloud/ibride, l&#39;architetto deve coordinarsi con l&#39;Assistenza clienti.
* Project Manager - In hosting: il team di hosting collaborerà con il team di assistenza clienti e il cliente per coordinare la cronologia dell&#39;aggiornamento per tutte le istanze.
* Amministratore Adobe Campaign  - In hosting: il team di hosting esegue l&#39;aggiornamento.
*  operatore Adobe Campaign\utente di marketing - L&#39;operatore esegue test sulle istanze di sviluppo, test e produzione.

## Come posso prepararmi per l&#39;aggiornamento della build?

Nei sistemi di sviluppo e gestione temporanea, esportate qualsiasi lavoro critico e da conservare. Per ulteriori informazioni, [guardate questo video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Aggiorna la tua conoscenza dei flussi di lavoro e delle consegne dei percorsi critici sviluppati nei registri di esecuzione (o dal team/partner di consulenza) rivedendo la documentazione fornita al team al termine dell’implementazione.

Identificare volumi ridotti o tempi di traffico ridotti che sarebbero ideali per le finestre di manutenzione in quanto produrranno il minor impatto sull&#39;azienda.

Rivedete l&#39;elenco di controllo per l&#39;aggiornamento della [build riportato di seguito](#check-list) e i vostri piani di test e assicuratevi che le risorse in grado di eseguire questi test siano disponibili entro 24-48 ore. del completamento di un aggiornamento.

For more information, [refer to this document](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html).

## È possibile eseguire gli aggiornamenti durante le ore notturne o durante le ore di inattività?

Gli aggiornamenti possono essere eseguiti fuori orario. È sempre consigliabile aggiornare l&#39;ambiente durante le ore di inattività dell&#39;azienda quando nessun utente aziendale è connesso all&#39;istanza.

## Quali sono i costi associati all&#39;aggiornamento di una build?

Non vi sono costi per installare l&#39;aggiornamento della build per i clienti ospitati. In caso di sviluppi personalizzati nel sistema, il Cliente dovrà identificare le risorse necessarie per testare tali sviluppi dopo l&#39;aggiornamento e per correggere eventuali problemi riscontrati con tali sviluppi personalizzati.

## Sarà possibile accedere all&#39;istanza durante il processo di aggiornamento?

No. Il server viene arrestato durante un aggiornamento per garantire che l&#39;integrità dei dati venga mantenuta durante l&#39;aggiornamento del prodotto. Al termine, viene riavviato e tutti i servizi riprendono.

## I messaggi e-mail continueranno a essere inviati da Centro messaggi durante il processo di aggiornamento?

Quando l&#39;aggiornamento viene eseguito per il Centro messaggi (RT), non invierà e-mail dall&#39;istanza. Nota: tutti i processi che vengono interrotti quando un sistema Campaign viene spento vengono ripresi automaticamente al riavvio del sistema. Ciò include consegne attive o pianificate, tracciamento e calcoli delle metriche per le consegne inviate in precedenza.

## I flussi di lavoro continueranno a essere eseguiti e a inviare le consegne?

No. Durante l&#39;aggiornamento della build, i servizi di flusso di lavoro e posta vengono entrambi interrotti. Ciò significa che i flussi di lavoro non verranno eseguiti e che le consegne non verranno inviate. I dati riprenderanno al riavvio del sistema. Tuttavia,  Adobe consiglia vivamente di controllare tutti i flussi di lavoro dei percorsi critici dopo un aggiornamento per assicurarne l’esecuzione e la salute.

## I miei collegamenti di tracciamento funzioneranno ancora durante l&#39;aggiornamento?

I collegamenti di tracciamento funzioneranno durante l&#39;aggiornamento. Non è possibile inviare nuove e-mail durante l’aggiornamento, ma i collegamenti di tracciamento inclusi nelle e-mail già inviate saranno operativi.

## Devo essere disponibile durante il processo di aggiornamento della build?

Sì. I clienti devono fornire  Adobe un punto di contatto disponibile durante o subito dopo l&#39;aggiornamento della propria istanza di produzione.   Adobe contatterà questa persona via e-mail, a meno che non siano stati presi altri provvedimenti. In questo modo sarà possibile garantire una transizione senza problemi e la convalida immediata delle attività critiche.  Adobe contatterà il Cliente al termine dell&#39;aggiornamento della build per la conferma.

## Devo aggiornare la console client?

Sì. La console client deve trovarsi nella stessa build o nella build più recente dell&#39;istanza del server. Una volta completato l&#39;aggiornamento, la console client deve richiedere di eseguire l&#39;aggiornamento alla build più recente per assicurarsi che rimanga allineata con la build del server.

## Qual è il piano di ripristino? I backup dei dati personali vengono conservati?

Il piano di ripristino consiste nel ripristinare il sistema con l&#39;ultimo backup disponibile. I backup vengono memorizzati per 7 giorni per i clienti del centro dati e per 14 giorni per i clienti  Amazon Web Service (AWS).

## Quanto tempo sarà necessario per eseguire il rollback?

Dipende dalle dimensioni del backup del database. Il tempo medio necessario per il completamento è di 4 ore.

## Quali tipi di test vengono eseguiti sul mio sistema dopo l&#39;aggiornamento?

Fare riferimento all&#39;elenco di controllo per l&#39;aggiornamento della [build riportato di seguito](#check-list).

## Che tipo di test devo eseguire dopo l&#39;aggiornamento?

Gli ambienti di sviluppo e di fase vengono aggiornati in sequenza o insieme, ma prima di aggiornare l&#39;istanza di produzione è necessario effettuare un&#39;operazione di disconnessione. Questo consente a ogni cliente di effettuare test approfonditi prima di accettare qualsiasi modifica alla produzione.

Vedi elenco di controllo [per l&#39;aggiornamento della build riportato di seguito](#check-list). I clienti devono eseguire test simili, così come altri test necessari per l&#39;ambiente.

## Con quale frequenza è necessario eseguire un aggiornamento della build?

Per garantire prestazioni, disponibilità e sicurezza ottimali del sistema,  Adobe collaborerà con i Clienti per garantire che i sistemi vengano aggiornati almeno una volta all&#39;anno.

## Verrà eseguita una chiusura per con un aggiornamento della build?

Sì. Il server viene arrestato durante un aggiornamento per garantire che l&#39;integrità dei dati venga mantenuta durante l&#39;aggiornamento del prodotto. Al termine, viene riavviato e tutti i servizi riprendono.

## Chi devo contattare per aprire il ticket di aggiornamento della build?

Se si verificano dei problemi dopo un aggiornamento della build, contatta [Assistenza](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)clienti di Adobe. L&#39;Assistenza clienti pianifica le date di creazione e apre biglietti relativi all&#39;aggiornamento della build.

Ulteriori informazioni nelle opzioni [Guida e Supporto per Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)

## Genera elenco di controllo dell&#39;aggiornamento {#check-list}

### Controllo post aggiornamento del server di messaggistica Cloud

1. Invio di una consegna di test
   1. Convalida dei registri di consegna e del relativo flusso di lavoro
   1. Convalida dei registri di tracciamento aggiornati
   1. Convalida della pagina mirror e dei collegamenti di tracciamento
1. Conferma tutti i flussi di lavoro tecnici in stato di avvio
1. Verifica che anche tutti i processi siano attivi

### Elenco di controllo post aggiornamento del server di marketing

* È possibile accedere al server? Controlla che la console client della campagna funzioni senza errori o avvisi.
* Dopo l&#39;aggiornamento, accertatevi di utilizzare la stessa versione della console utilizzata per la versione di build.
* Esistono applicazioni Web che inseriscono dati nel database Campaign? In tal caso, eseguiteli e verificate che possano inserire nuovi record tramite API.
* È possibile inviare correttamente un&#39;e-mail di prova? Crea una nuova consegna utilizzando un modello noto, inviala a un destinatario di test, verifica la personalizzazione, collegamento non sub, mirror page tutto il lavoro.
* Sono in esecuzione tutti i flussi di lavoro dei percorsi critici? Controlla flussi di lavoro, apri giornale di registrazione flussi di lavoro, verifica che non ci siano errori.
* Tutte le cartelle sono presenti, visibili e accessibili? Scorri diverse cartelle e seleziona.
tutto il contenuto viene visualizzato e presente.
* Le consegne verranno effettuate con il fuso orario corretto?

   * Verifica la data di creazione e la data di modifica con la marca temporale e il fuso orario
   * Verifica che l&#39;esecuzione di scheduler funzioni in un flusso di lavoro all&#39;ora specificata
   * Recupera elenco di flussi di lavoro in stato PAUSED e FAILED. Avvio e monitoraggio
   * Esegui test AB per uno scenario
   * Test delle notifiche push con le relative funzionalità di tracciamento per i collegamenti profondi
   * Test invio SMS
   * Se hai un FDA esterno connesso, verifica se i dati vengono inviati in entrambi i modi
   * Se utilizzate integrazioni come  Adobe Campaign-Adobe Experience Manager,  Adobe Campaign- Adobe Analytics, verificate se funzionano comunque come prima

**Vedi anche**

* [Esecuzione di un aggiornamento della build](../../production/using/build-upgrade.md)
* [Note sulla versione Campaign Classic](../../rn/using/rn-overview.md)
* [Opzioni di assistenza e supporto per Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programma Gold Standard](https://helpx.adobe.com/it/campaign/kb/gold-standard.html)