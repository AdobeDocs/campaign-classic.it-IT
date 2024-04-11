---
product: campaign
title: Tabelle che richiedono manutenzione
description: Tabelle che richiedono manutenzione
feature: Monitoring
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Tabelle che richiedono manutenzione{#tables-to-maintain}



L’elenco delle tabelle da gestire dipende dalla versione di Adobe Campaign in uso, dal modo in cui viene utilizzata e dalla configurazione del modello dati.

L’elenco seguente contiene solo le tabelle più soggette a frammentazione. Gli impatti sono i seguenti:

* consumo eccessivo di spazio su disco, con conseguente impatto sull&#39;accesso al database,
* indici che non sono stati aggiornati regolarmente, il che rallenta le prestazioni delle query.

## Tabelle di Adobe Campaign {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Nome tabella </strong><br /> </th> 
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
   <td> Medio<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabella di lavoro in cui vengono inseriti i record durante la preparazione della consegna. Vengono quindi aggiornati durante la consegna e infine eliminati una volta completata la consegna.<br /> Questa tabella tende a frammentarsi rapidamente anche se la sua dimensione media è piuttosto limitata.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene le informazioni necessarie per generare pagine mirror personalizzate. Contiene un campo Memo (CLOB) e come tale tenderà ad essere molto grande. Il volume è direttamente proporzionale alla cronologia delle pagine mirror conservate. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Medio<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene statistiche sul processo di consegna. I suoi registri sono regolarmente aggiornati. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Medio<br /> </td> 
   <td> Aggiornamenti, inserimenti<br /> </td> 
   <td> Questa tabella contiene informazioni sugli indirizzi e-mail. Viene spesso aggiornato come parte del processo di quarantena (i record vengono creati al primo errore di consegna, aggiornati quando i contatori cambiano ed eliminati una volta che la consegna è andata a buon fine). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Aggiornamenti<br /> </td> 
   <td> Esiste un record per istanza di flusso di lavoro, quindi sono presenti pochissimi record. Tuttavia, la tabella viene regolarmente aggiornata per rispecchiare lo stato di avanzamento e i progressi compiuti.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Ogni esecuzione di un’attività del flusso di lavoro comporta la creazione di un record in questa tabella. Il meccanismo di eliminazione li elimina una volta scaduti.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Piccolo<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Ogni transizione attivata tra le attività di un flusso di lavoro determina la creazione di un record in questa tabella. Il meccanismo di eliminazione li elimina una volta scaduti. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Molto piccolo <br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella è specifica per il motore del flusso di lavoro. Consente l’invio di comandi ai flussi di lavoro (ad esempio Avvia, Arresta, Pausa). Anche se piccola, questa tabella viene presa in considerazione durante l’eliminazione delle tabelle transazionali collegate ai flussi di lavoro.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Più grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa è la tabella più grande del sistema. Esiste un record per messaggio inviato e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. <br /> </td> 
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
   <td> Questa tabella contiene informazioni utilizzate per gli errori SMTP di qualificazione. È abbastanza piccolo, ma verrà aggiornato in modo massiccio, quindi gli indici in questa tabella tendono a frammentarsi rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Medio<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa tabella contiene gli aggregati sugli errori SMTP ordinati per dominio. Inizialmente contiene informazioni dettagliate che vengono aggregate dall’attività di pulizia una volta che diventa obsoleta. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (in un’istanza mid-sourcing)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Solo quando l’istanza 5.10 (o successiva) viene utilizzata come istanza di mid-sourcing. Questa è una delle tabelle più grandi del database. Esiste un record per messaggio inviato e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. Quando si utilizza il mid-sourcing, si consiglia di limitare la cronologia (in genere meno di due mesi), in modo che questa tabella rimanga ragionevole in termini di dimensioni (meno di 30 Go per 60 milioni di righe, dati+indice), ma è molto importante ricrearla di tanto in tanto. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (quando si utilizza la tabella NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Questa è la tabella più grande del sistema. Esiste un record per messaggio inviato e questi record vengono inseriti, aggiornati per tenere traccia dello stato di consegna ed eliminati quando la cronologia viene eliminata. Si noti che nella versione 5.10 questa tabella è più piccola dell'equivalente nella versione 4.05 (NmsBroadLog) poiché il testo del messaggio SMTP viene fattorizzato nella tabella NmsBroadLogMsg nella versione 5.10. Tuttavia, rimane essenziale reindicizzare questa tabella regolarmente (a settimane alterne, per iniziare) e ricrearla completamente di tanto in tanto (una volta al mese o quando le prestazioni sono interessate). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (quando viene utilizzata una tabella dei destinatari esterna)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Come NmsBroadLogRcp ma con una tabella dei destinatari esterna. Adatta Yyy e Xxx ai valori presenti nella mappatura della consegna. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (quando si utilizza la tabella NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> I registri di tracciamento vengono inseriti ed eliminati quando la cronologia viene eliminata, ma non vengono aggiornati. Il volume dipende dalla durata della conservazione dei dati. <br /> </td> 
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
   <td> Simile alle altre tabelle broadlog, ma con NmsRtEvent anziché NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( Istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, eliminazioni<br /> </td> 
   <td> Simile alle altre tabelle trackingLog, ma con la tabella NmsRtEvent anziché NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (istanza di esecuzione del Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabella contenente la coda eventi del Centro messaggi. Lo stato di questi eventi viene aggiornato dal Centro messaggi durante l’elaborazione. Le eliminazioni vengono eseguite durante la rimozione. Ti consigliamo di ricreare regolarmente l’indice di questa tabella e di ricrearlo.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (istanza di controllo Centro messaggi)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Simile a NmsRtEvent. Questa tabella archivia ogni evento da tutte le istanze di esecuzione. Viene utilizzato da nessun processo in tempo reale, solo dai rapporti.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Molto piccolo<br /> </td> 
   <td> Inserimenti, aggiornamenti, eliminazioni<br /> </td> 
   <td> Tabelle che includono le app mobili e la relativa configurazione.<br /> </td> 
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
   <td> Simile alle altre tabelle broadlog, ma con NmsappSubscriptionRcp invece di NmsRecipient.<br /> </td> 
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
   <td> Tabella che include le sessioni utente. Il numero di inserimenti ed eliminazioni è molto importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tabelle cliente {#customer-tables}

Oltre all’elenco precedente, anche le tabelle contenenti create dai clienti (che non esistono nel modello dati di Adobe Campaign) durante la configurazione della piattaforma possono essere soggette a frammentazione, soprattutto se vengono aggiornate frequentemente durante le procedure di caricamento o sincronizzazione dei dati. Queste tabelle possono far parte del modello dati predefinito di Adobe Campaign (ad esempio **NmsRecipient**). In questo caso, spetta all’amministratore della piattaforma Adobe Campaign eseguire un controllo del modello di database specifico per individuare queste tabelle personalizzate. Queste tabelle non vengono necessariamente menzionate esplicitamente nelle nostre procedure di manutenzione.
