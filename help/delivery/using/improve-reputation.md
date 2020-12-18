---
solution: Campaign Classic
product: campaign
title: Miglioramento della reputazione nell'utilizzo di Adobe Campaign Classic
description: Scopri di più sul miglioramento della tua reputazione quando usi Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 2%

---


# Crescita reputazione{#improve-reputation}

Per evitare di esaurire i destinatari, elimina gli indirizzi e-mail duplicati dalla destinazione. Questo passaggio protegge la tua reputazione di invio e assicura una buona gestione della quarantena.  Adobe Campaign offre gli strumenti necessari per attuare queste raccomandazioni ed evitare il rischio di essere aggiunto al elenco Bloccati dal provider.

Per evitare il più possibile duplicazioni, è necessario eseguire le azioni seguenti:

* Le importazioni devono essere configurate con attenzione
* Prestate attenzione durante la modifica degli indirizzi e-mail
* Prestate attenzione durante le importazioni automatiche
* I profili devono essere ordinati in cartelle diverse

La gestione della quarantena è presentata in [questa sezione](../../delivery/using/understanding-quarantine-management.md).

Qui di seguito troverete informazioni sulla gestione dei duplicati e della quarantena.

È possibile monitorare il volume delle e-mail inviate per indirizzo IP. Per questo è necessaria un&#39;estensione dello schema. È necessario estendere la tabella dei registri di trasmissione per aggiungere l&#39;&quot;identificatore pubblico&quot; e creare un flusso di lavoro per estrarre e visualizzare i dati. Contatta  Adobe se ti serve.

## Duplica {#duplicates}

La presenza di indirizzi e-mail duplicati può avere molteplici conseguenze:

* Lo stesso messaggio viene inviato più di una volta. Anche se Campaign esegue una procedura di deduplicazione per impostazione predefinita prima dell&#39;invio, non c&#39;è nulla che fermi l&#39;invio dello stesso messaggio da parte di azioni diverse con lo stesso contenuto quando una destinazione viene divisa.
* Richieste di annullamento sottoscrizione non rispettate. Se un destinatario annulla la sottoscrizione dopo aver ricevuto un messaggio, il profilo duplicato sarà comunque idoneo per i messaggi futuri.

Oltre a questa procedura di opt-in, questa situazione porterà probabilmente gli utenti a considerare i messaggi come spam e ad avviare una procedura di elenco Bloccati presso l&#39;ISP.

È necessario essere particolarmente prudenti quando si eseguono operazioni sul database:

* Le importazioni devono essere configurate meticolosamente, in particolare quando si sceglie la chiave di riconciliazione.
* Gli indirizzi e-mail modificati possono anche essere fonte di duplicati. In particolare, due indirizzi con domini diversi possono essere indirizzati alla stessa cassetta postale, ad esempio nel caso di una società che ha cambiato nome e che ha mantenuto il dominio precedente per un certo periodo di tempo: joe.doe@amce-co.com e joe.doe@acme-rebranded.com.
* Le importazioni automatiche, sia che si tratti di elenchi o di altre basi di dati, sono elementi di cui tenere conto nella gestione dei profili. Cosa succede quando si elimina o si sposta un profilo in un&#39;altra partizione? Potrebbe essere ricreato nella partizione iniziale da un&#39;importazione automatica, ad esempio, quando viene inserito un ordine di acquisto.
* La memorizzazione dei profili in diverse cartelle può essere implementata utilizzando le viste anziché le partizioni. In questo modo, sei sicuro che i profili si trovano nella stessa partizione fisica pur continuando a consentire la visualizzazione e la gestione dei diritti adeguati.

Ci sono, comunque, casi in cui i duplicati tra le diverse partizioni sono normali. Ad esempio, quando si inviano dati per terze parti o entità aziendali diverse, è logico che la stessa persona sia un destinatario per diversi motivi. Tuttavia, raramente è normale trovare duplicati all&#39;interno della stessa partizione.

## Quarantenne {#quarantines}

 Adobe Campaign gestisce un elenco di indirizzi in quarantena. I destinatari i cui indirizzi sono posti in quarantena sono esclusi per impostazione predefinita durante l&#39;analisi del recapito: non sono mirati. Un indirizzo e-mail può essere messo in quarantena, ad esempio se la casella in entrata è piena o se l’indirizzo non esiste. In tutti i casi, la quarantena corrisponde alle norme specifiche di seguito indicate.

La gestione della quarantena è presentata in [questa sezione](../../delivery/using/understanding-quarantine-management.md).