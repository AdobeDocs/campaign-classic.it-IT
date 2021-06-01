---
product: campaign
title: Tabelle che richiedono manutenzione
description: Tabelle che richiedono manutenzione
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---

# Tabelle che richiedono manutenzione{#tables-to-maintain}

L’elenco delle tabelle da gestire dipende dalla versione di Adobe Campaign, dalla modalità di utilizzo e dalla configurazione del modello dati.

Nell&#39;elenco seguente sono elencate solo le tabelle più soggette a frammentazione. Gli impatti sono i seguenti:

* un eccessivo consumo di spazio su disco, con conseguente impatto sull&#39;accesso al database,
* indici che non sono stati aggiornati regolarmente, il che rallenta le prestazioni delle query.

## Tabelle Adobe Campaign {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Nome tabella  </strong><br /> </th> 
   <th> <strong>Dimensione</strong><br /> </th> 
   <th> <strong>Tipo principale di attività</strong><br /> </th> 
   <th> <strong>Commenti</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Aggiornamenti<br /> </td> 
   <td> Esiste un record per azione di consegna. Un singolo record può essere aggiornato diverse volte per riflettere l’avanzamento della consegna, pertanto gli indici in questa tabella tendono a frammentarsi rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Media<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabella di lavoro in cui vengono inseriti i record durante la preparazione della consegna. Vengono quindi aggiornati durante la consegna ed infine eliminati una volta completata la consegna.<br /> Questa tabella tende a frammentarsi rapidamente anche se le sue dimensioni medie sono abbastanza limitate.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene le informazioni necessarie per generare pagine mirror personalizzate. Contiene un campo Memo (CLOB) e come tale tenderà ad essere molto grande. Il volume è direttamente proporzionale alla cronologia delle pagine mirror conservate. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Media<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene statistiche sul processo di consegna. I suoi documenti vengono regolarmente aggiornati. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Media<br /> </td> 
   <td> Aggiornamenti, inserimenti<br /> </td> 
   <td> Questa tabella contiene informazioni sugli indirizzi e-mail. Viene spesso aggiornato come parte del processo di quarantena (i record vengono creati al primo errore di consegna, aggiornati quando i contatori cambiano ed eliminati una volta completata la consegna). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Aggiornamenti<br /> </td> 
   <td> C'è un record per istanza di flusso di lavoro, quindi pochissimi record. Tuttavia, la tabella viene regolarmente aggiornata per riflettere lo stato e l'avanzamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Ogni esecuzione di un’attività del flusso di lavoro porta alla creazione di un record in questa tabella. Il meccanismo di eliminazione li elimina una volta scaduti.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Ogni transizione attivata tra le attività di un flusso di lavoro porta alla creazione di un record in questa tabella. Il meccanismo di eliminazione li elimina una volta scaduti. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Molto piccolo <br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella è specifica del motore del flusso di lavoro. Consente l’invio di comandi ai flussi di lavoro (ad esempio Start, Stop, Pause). Anche se è piccola, questa tabella viene presa in considerazione durante l'eliminazione delle tabelle transazionali collegate ai flussi di lavoro.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Più grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questo è il tavolo più grande del sistema. Esiste un record per messaggio inviato e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> I registri di tracciamento vengono inseriti ed eliminati quando la cronologia viene eliminata, ma non vengono aggiornati. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Aggiornamenti<br /> </td> 
   <td> Questa tabella contiene informazioni utilizzate per gli errori SMTP qualificati. È abbastanza piccolo, ma verrà aggiornato massicciamente, quindi gli indici in questa tabella tendono a frammentarsi rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Media<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene gli aggregati sugli errori SMTP ordinati per dominio. Contiene inizialmente informazioni dettagliate che vengono aggregate dall’attività di pulizia una volta che questa è obsoleta. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (su un'istanza di mid-sourcing)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Solo quando l’istanza 5.10 (o successiva) viene utilizzata come istanza di mid-sourcing. Questa è una delle tabelle più grandi del database. Esiste un record per messaggio inviato e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. Quando si utilizza la mid-sourcing, si consiglia di limitare la cronologia (di solito meno di due mesi), quindi questa tabella rimane ragionevole in termini di dimensioni (meno di 30 Go per 60 milioni di righe, data+index), ma è molto importante ricostruirla di tanto in tanto. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (quando viene utilizzata la tabella NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questo è il tavolo più grande del sistema. Esiste un record per messaggio inviato e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. In 5.10, questa tabella è inferiore all’equivalente in 4.05 (NmsBroadLog), in quanto il testo del messaggio SMTP viene fattorizzato nella tabella NmsBroadLogMsg nella versione 5.10. Tuttavia, rimane essenziale reindicizzare regolarmente questa tabella (ogni due settimane per iniziare) e ricostruirla completamente di tanto in tanto (una volta al mese, o quando le prestazioni sono influenzate). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (quando viene utilizzata una tabella dei destinatari esterna)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Come NmsBroadLogRcp ma con una tabella dei destinatari esterna. Adatta Yyy e Xxx con i valori nella mappatura della consegna. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (quando viene utilizzata la tabella NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> I registri di tracciamento vengono inseriti ed eliminati quando la cronologia viene eliminata, ma non vengono aggiornati. Il volume dipende dalla lunghezza del periodo di conservazione dei dati. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (quando viene utilizzata la tabella dei destinatari esterna)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> Come NmsTrackingLogRcp ma con una tabella dei destinatari esterna. Adatta Yyy e Xxx con i valori utilizzati nella mappatura della consegna. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle del registro di trasmissione, ma con NmsRtEvent invece di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle trackingLog, ma con la tabella NmsRtEvent al posto di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabella contenente la coda eventi del Centro messaggi. Lo stato di tali eventi viene aggiornato dal Centro messaggi durante l’elaborazione. Le eliminazioni vengono effettuate durante l'eliminazione. Ti consigliamo di ricreare regolarmente l'indice di questa tabella e di ricrearlo.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (istanza di controllo del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Simile a NmsRtEvent. Questa tabella archivia ogni evento da tutte le istanze di esecuzione. Viene utilizzato senza alcun processo in tempo reale, solo dai report.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Molto piccolo<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
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
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle del registro di trasmissione, ma con NmsappSubscriptionRcp invece di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle trackingLog, ma con la tabella NmsappSubscriptionRcp invece di NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> Tabella che include le sessioni utente. Il numero di inserimenti e cancellazioni è molto importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tabelle dei clienti {#customer-tables}

Oltre all’elenco precedente, le tabelle contenenti create dai clienti (che non esistono nel modello dati di Adobe Campaign) durante la configurazione della piattaforma possono anche essere soggette a frammentazione, soprattutto se vengono aggiornate frequentemente durante le procedure di caricamento o sincronizzazione dei dati. Queste tabelle possono far parte del modello dati predefinito di Adobe Campaign (ad esempio **NmsRecipient**). In questo caso, spetta all’amministratore della piattaforma Adobe Campaign eseguire un controllo del proprio modello di database specifico per trovare queste tabelle personalizzate. Queste tabelle non sono necessariamente menzionate esplicitamente nelle nostre procedure di manutenzione.
