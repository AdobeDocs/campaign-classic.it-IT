---
solution: Campaign Classic
product: campaign
title: Tabelle che richiedono manutenzione
description: Tabelle che richiedono manutenzione
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---


# Tabelle che richiedono manutenzione{#tables-to-maintain}

L&#39;elenco delle tabelle da gestire dipende dalla versione di  Adobe Campaign, dalla modalità di utilizzo e dalla configurazione del modello di dati.

L&#39;elenco seguente contiene solo le tabelle maggiormente soggette a frammentazione. Gli impatti sono i seguenti:

* il consumo eccessivo di spazio su disco, con conseguente impatto sull&#39;accesso al database,
* indici che non sono stati aggiornati regolarmente e che rallentano le prestazioni delle query.

##  tabelle Adobe Campaign {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Nome tabella </strong><br /> </th> 
   <th> <strong>Dimensioni</strong><br /> </th> 
   <th> <strong>Tipo principale di attività</strong><br /> </th> 
   <th> <strong>Commenti</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Updates<br /> </td> 
   <td> Esiste un record per azione di consegna. Un singolo record può essere aggiornato più volte per riflettere l'avanzamento della distribuzione, pertanto gli indici di questa tabella tendono a frammentarsi rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Media<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabella di lavoro in cui vengono inseriti i record durante la preparazione della consegna. Vengono quindi aggiornati durante la consegna e infine eliminati al termine della consegna.<br /> Questa tabella tende a frammentarsi rapidamente anche se le sue dimensioni medie sono piuttosto limitate.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, eliminazioni<br /> </td> 
   <td> Questa tabella contiene le informazioni necessarie per generare pagine mirror personalizzate. Contiene un campo Memo (CLOB) e come tale tenderà ad essere molto grande. Il volume è direttamente proporzionale alla cronologia delle pagine mirror conservate. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Media<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene le statistiche sul processo di consegna. I suoi documenti sono regolarmente aggiornati. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Media<br /> </td> 
   <td> Aggiornamenti, inserzioni<br /> </td> 
   <td> Questa tabella contiene informazioni sugli indirizzi e-mail. Viene spesso aggiornato durante il processo di quarantena (i record vengono creati al primo errore di consegna, aggiornati quando i contatori cambiano ed eliminati una volta che la consegna ha esito positivo). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Updates<br /> </td> 
   <td> Esiste un record per ogni istanza del flusso di lavoro, quindi pochissimi record. Tuttavia, la tabella viene regolarmente aggiornata per riflettere lo stato e l'avanzamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Ogni esecuzione di un'attività del flusso di lavoro porta alla creazione di un record in questa tabella. Il meccanismo di rimozione li elimina una volta scaduti.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Ogni transizione attivata tra le attività di un flusso di lavoro porta alla creazione di un record in questa tabella. Il meccanismo di rimozione li elimina una volta scaduti. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Molto piccolo <br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella è specifica per il motore del flusso di lavoro. Consente l'invio di comandi ai flussi di lavoro (ad esempio Start, Stop, Pausa). Anche se è piccola, questa tabella viene presa in considerazione durante l'eliminazione delle tabelle transazionali collegate ai flussi di lavoro.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Più grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa è la tabella più grande del sistema. Esiste un record per messaggio inviato, e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, eliminazioni<br /> </td> 
   <td> I registri di tracciamento vengono inseriti ed eliminati quando la cronologia viene eliminata, ma non vengono aggiornati. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Updates<br /> </td> 
   <td> Questa tabella contiene informazioni utilizzate per gli errori SMTP idonei. È abbastanza piccolo, ma sarà massicciamente aggiornato, quindi gli indici in questa tabella tendono a frammentarsi rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorState<br /> </td> 
   <td> Media<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene gli aggregati relativi agli errori SMTP ordinati per dominio. Contiene inizialmente informazioni dettagliate, aggregate dall’attività di pulizia una volta che questa è obsoleta. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (in un'istanza mid-sourcing)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Solo quando l'istanza 5.10 (o successiva) viene utilizzata come istanza mid-sourcing. Questa è una delle tabelle più grandi del database. Esiste un record per messaggio inviato, e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. Quando si utilizza il mid-sourcing, la raccomandazione consiste nel limitare la cronologia (solitamente meno di due mesi), quindi questa tabella rimane ragionevole in termini di dimensioni (meno di 30 Go per 60 milioni di righe, data+indice), ma è molto importante ricrearla di tanto in tanto. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (quando viene utilizzata la tabella NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa è la tabella più grande del sistema. Esiste un record per messaggio inviato, e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. In 5.10, questa tabella è più piccola dell'equivalente in 4.05 (NmsBroadLog), poiché il testo del messaggio SMTP è fattorizzato nella tabella NmsBroadLogMsg nella versione 5.10. Tuttavia, rimane essenziale reindicizzare questa tabella regolarmente (ogni due settimane per iniziare) e rigenerarla completamente di tanto in tanto (una volta al mese, o quando le prestazioni sono influenzate). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (quando viene utilizzata una tabella di destinazione esterna)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Come NmsBroadLogRcp ma con una tabella di destinatari esterna. Adattate Yyy e Xxx con i valori nella mappatura della consegna. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (quando viene utilizzata la tabella NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, eliminazioni<br /> </td> 
   <td> I registri di tracciamento vengono inseriti ed eliminati quando la cronologia viene eliminata, ma non vengono aggiornati. Il volume dipende dalla durata della conservazione dei dati. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (quando viene utilizzata la tabella del destinatario esterno)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, eliminazioni<br /> </td> 
   <td> Come NmsTrackingLogRcp ma con una tabella di destinatari esterna. Adattate Yyy e Xxx con i valori utilizzati nella mappatura della consegna. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle del registro di trasmissione, ma con NmsRtEvent invece di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle trackingLog, ma con la tabella NmsRtEvent al posto di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabella contenente la coda degli eventi del Centro messaggi. Lo stato di questi eventi viene aggiornato dal Centro messaggi durante l'elaborazione. Le eliminazioni vengono effettuate durante la rimozione. Vi consigliamo di ricreare regolarmente l'indice di questa tabella e di rigenerarlo.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (istanza di controllo del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Simile a NmsRtEvent. Questa tabella archivia ogni evento da tutte le istanze di esecuzione. Viene utilizzato da nessun processo in tempo reale, solo dai report.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Molto piccolo<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabelle che includono le applicazioni mobili e la relativa configurazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti<br /> </td> 
   <td> Tabella che include gli identificatori dei dispositivi mobili (indirizzi) utilizzati per inviare la notifica (simile a una tabella dei destinatari).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, aggiornamenti, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle del registro di trasmissione, ma con NmsappSubscriptionRcp invece di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserzioni, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle trackingLog, ma con la tabella NmsappSubscriptionRcp invece di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserzioni, eliminazioni<br /> </td> 
   <td> Tabella che include le sessioni utente. Il numero di inserzioni ed eliminazioni è molto importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tabelle cliente {#customer-tables}

Oltre all&#39;elenco riportato sopra, anche le tabelle contenenti elementi creati dai clienti (che non esistono nel modello dati Adobe Campaign ) durante la configurazione della piattaforma possono essere soggette a frammentazione, soprattutto se vengono aggiornate frequentemente durante le procedure di caricamento o sincronizzazione dei dati. Queste tabelle possono essere parte del modello dati Adobe Campaign predefinito  (ad esempio, **NmsRecipient**). In questo caso, spetta all&#39;amministratore della piattaforma Adobe Campaign  eseguire un controllo del proprio modello di database specifico per trovare queste tabelle personalizzate. Queste tabelle non sono necessariamente menzionate esplicitamente nelle nostre procedure di manutenzione.
