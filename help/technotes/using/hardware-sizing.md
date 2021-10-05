---
product: campaign
title: Raccomandazioni per il dimensionamento dell'hardware per Campaign Classic v7
description: Raccomandazioni per il dimensionamento dell'hardware per Campaign Classic v7
source-git-commit: 0deb18bb0376fc5e94d063145280426ff54db786
workflow-type: tm+mt
source-wordcount: '2512'
ht-degree: 1%

---

# Raccomandazioni per il dimensionamento dell&#39;hardware{#hardware-sizing-reco}

![](../../assets/v7-only.svg)

## Panoramica

>[!CAUTION]
>
>Questo articolo è fornito solo come guida di esempio generale. È necessario interagire con il Customer Success Manager di Adobe Campaign per misurare le dimensioni esatte della distribuzione prima di avviare il progetto Campaign. **Non** acquisire o distribuire alcuna infrastruttura o hardware fino a quando non viene fatto questo.

Questo documento fornisce raccomandazioni generali per la distribuzione di Adobe Campaign Classic v7 nel centro dati on-premise o nell’ambiente cloud virtualizzato. Questo tipo di distribuzione, noto come **ibrido** o **mid-sourcing**, posiziona l’istanza di marketing di Campaign e il database di marketing sotto il tuo controllo operativo, utilizzando i servizi Adobe Cloud Messaging per inviare e-mail, messaggi SMS o SMPP e raccogliere e-mail aperte, rimbalzate e dati di tracciamento dei clic.

L’istanza di marketing è la parte dell’architettura di Adobe Campaign che guida tutte le attività di marketing e memorizza tutti i dati dei destinatari e i dati analitici restituiti dalle campagne. L’istanza di marketing è un set di server on-premise che eseguono i servizi Adobe Campaign e un database relazionale.

>[!CAUTION]
>
>Le informazioni contenute in questo documento non si applicano se utilizzi un’istanza Adobe Campaign completamente ospitata (distribuita nei Cloud Services di Adobe).

La compatibilità software è descritta in [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).


### Scenari

I diagrammi di distribuzione e le raccomandazioni di dimensionamento dell&#39;hardware sono forniti per tre scenari rappresentativi:

1. [Moderate-Size](#scenario-1)  - 5 milioni di destinatari attivi nel sistema
1. [Grandi dimensioni](#scenario-2)  - 20 milioni di destinatari attivi nel sistema
1. [Enterprise](#scenario-3)  - 50 milioni di destinatari attivi, con messaggi transazionali

### Ipotesi

Questo documento presuppone anche i seguenti tipi di utilizzo per tutti e tre gli scenari:

* Le campagne e-mail di grandi dimensioni vengono inviate due volte alla settimana, a circa il 50% dei destinatari attivi
* Gli invii diretti vengono generati una volta al mese per ogni destinatario nel sistema
* I messaggi SMS vengono inviati a circa il 10% dei destinatari attivi ogni mese
* Lo schema del database che definisce ogni destinatario è stato esteso con una tabella aggiuntiva, contenente circa 200 byte di dati per ciascun destinatario
* Il modulo di interazione Adobe Campaign viene utilizzato per aggiungere offerte all’e-mail in uscita
* I dati di tracciamento e-mail vengono conservati nel sistema Campaign per 90 giorni

## Linee guida generali

Campaign è un’applicazione incentrata sul database e le prestazioni del server di database sono fondamentali. L’esecuzione di flussi di lavoro, segmentazione, caricamento di dati di tracciamento, interazioni in entrata, analisi e altre attività genera tutte attività di database. In generale, le dimensioni e la frequenza di queste operazioni determinano le dimensioni dei server di database.

I server applicazioni nella tua istanza di marketing richiedono CPU e memoria sufficienti per eseguire flussi di lavoro e rispondere alle chiamate API SOAP, comprese le richieste degli utenti della console Campaign. I requisiti della CPU possono essere significativi per i flussi di lavoro che utilizzano interazioni in uscita con regole di offerta complesse, flussi di lavoro che eseguono JavaScript personalizzato e applicazioni web con livelli di traffico elevati.

Le applicazioni web di Campaign possono essere distribuite anche sui server app dell’istanza di marketing o su sistemi server web separati. Poiché i carichi di lavoro delle applicazioni web sono in conflitto con i flussi di lavoro critici e gli utenti della console Campaign, le applicazioni web e le interazioni in entrata possono essere distribuite su server separati, per garantire che la funzionalità di base di Campaign sia eseguita in modo affidabile con buone prestazioni.

Per la sicurezza e la disponibilità, l&#39;Adobe consiglia di separare il traffico di Internet dal traffico generato dagli utenti aziendali. Per questo motivo, i diagrammi contengono due gruppi di server: il server web (web-face Web1 e Web2) e i server app (business process App1 e App2).

È un requisito legale per i mittenti e-mail commerciali avere una pagina web di rinuncia funzionale. Adobe consiglia di disporre di un computer ridondante in ciascun server di gruppo per gli scenari di failover. È particolarmente vero se Adobe Campaign ospita le pagine di rinuncia.

### Proxy inversi

L’architettura di Campaign garantisce un’elevata sicurezza utilizzando SSL su HTTP (HTTPS) per comunicare tra l’istanza di marketing e Adobe Cloud Messaging. Sicurezza, affidabilità e disponibilità vengono applicate utilizzando proxy inverso in una subnet &quot;zona demilitarizzata&quot; (DMZ) per isolare e proteggere i server e il database delle istanze di marketing.

### Load balancer

Il load balancer per i server app è configurato in una configurazione attiva/passiva, con HTTPS terminato sul proxy. Il load balancer per i server Web è configurato in una configurazione attiva/attiva, con HTTPS terminato sul proxy.

Adobe fornisce l’elenco esclusivo dei percorsi URL che possono essere inoltrati al server Adobe Campaign nell’ambiente di distribuzione.

### Architettura

L&#39;architettura generale è quasi identica, indipendentemente dai volumi. I requisiti di sicurezza e di elevata disponibilità impongono un minimo di quattro server; due server se non vengono utilizzate webApps. La differenza nella configurazione varia principalmente nella configurazione dell&#39;hardware come il core della CPU e la memoria.

## Scenario 1: Distribuzione a dimensione moderata{#scenario-1}

![](assets/scenario-1.png)

Volume stimato:

| Canale | Volume |
| ----------------------- | ----------------- |
| Destinatari attivi | 5 milioni |
| E-mail | 4,2 milioni/mese |
| Direct mail | 1 milione/mese |
| SMS mobile | 100.000/mese |
| Picco volume e-mail giornaliero | 500 |

Per questi volumi, una coppia di sistemi server applicativi Adobe Campaign fornisce tutte le funzionalità per gli utenti client Adobe Campaign e l&#39;esecuzione di un flusso di lavoro. Per 5 milioni di destinatari attivi e questo volume di e-mail, i carichi di lavoro del server applicazioni non richiedono un uso intensivo della CPU o dell’I/O; la maggior parte dello stress è nel database.

I server web Adobe Campaign vengono visualizzati nell’area protetta.

### Server web e applicazioni

Questo scenario consiglia di installare Adobe Campaign su quattro computer, con le seguenti specifiche:

**CPU quad-core da 3 Ghz+, 8 GB di RAM, RAID 1 o 10, 2 x 80 GB SSD**

Questi sistemi creano l’istanza di marketing Application Server, che supporta direttamente gli utenti della console Campaign ed esegue i flussi di lavoro delle campagne.

Invertire i proxy in un traffico di bilanciamento del carico DMZ nei server Web Adobe Campaign. Non è necessario installare lo stack software Adobe Campaign su macchine proxy; è possibile utilizzare qualsiasi software reverse proxy o apparecchiatura di rete.

Le funzioni di opt-in/opt-out dell’abbonamento e del centro preferenze possono essere fornite da Campaign o dal tuo sito web. Se scegli di implementare questa funzionalità sul tuo sito web, assicurati che le informazioni sulle preferenze e sugli abbonamenti vengano propagate al database di marketing di Campaign. Normalmente viene eseguito creando file di estrazione che vengono caricati automaticamente dai flussi di lavoro Campaign.

Il consumo di spazio su disco su Application Server dipende dal periodo di conservazione dei file scambiati con fornitori di servizi di terze parti (ad esempio, fornitori di stampa per Direct Mail) e dalle dimensioni e dalla conservazione dei file flat importati, come gli aggiornamenti di abbonamento o preferenza dal tuo sito Web, o estratti dai tuoi sistemi CRM o di marketing.

### Database

Le raccomandazioni hardware per il server di database sono le seguenti:

**CPU a 4 core da 3 Ghz+, RAM da 16 GB, RAID 1 o 10, SSD da 128 GB minima**

La stima della memoria presuppone il caching completo di circa 500.000 destinatari per un avvio di una campagna di grandi dimensioni, oltre allo spazio buffer RDBMS per l’esecuzione di flussi di lavoro, l’importazione di dati di tracciamento e altre attività simultanee.

Si stima che lo spazio su disco necessario nel database per memorizzare tutti i dati tecnici Adobe Campaign (campagne, tracciamento, tabelle di lavoro e così via) sia di circa 35 GB in base a un periodo di conservazione di tre mesi. Se scegli di conservare i dati di tracciamento per 6 mesi, le dimensioni del database aumentano a circa 40 GB e la conservazione a 12 mesi aumenta le dimensioni del database a circa 45 GB. I dati dei destinatari consumano circa 5 GB per questo ambiente.

>[!CAUTION]
>
>Questa stima non include dati cliente aggiuntivi. Se si prevede di replicare ulteriori colonne o tabelle di dati dei clienti nel database Adobe Campaign, è necessario stimare il fabbisogno aggiuntivo di spazio su disco per tale database. I segmenti o gli elenchi caricati richiedono anche più spazio di archiviazione, a seconda delle dimensioni, della frequenza e del periodo di conservazione.

Considera inoltre che, a causa del volume di informazioni elaborate quotidianamente, l&#39;IOPS del database server è fondamentale. Ad esempio, in un giorno di picco, puoi distribuire campagne indirizzate a un totale di 500.000 destinatari. Per eseguire ogni campagna, Adobe Campaign inserisce 500.000 record in una tabella contenente circa 12 milioni di record (la tabella dei log di consegna). Per fornire prestazioni accettabili durante la distribuzione della campagna, Adobe consiglia un minimo di 60.000 IOPS di lettura/scrittura casuali da 4 KB per questo scenario.


## Scenario 2: Installazione di grandi dimensioni{#scenario-2}

![](assets/scenario-2.png)

Volume stimato:

| Canale | Volume |
| ----------------------- | ----------------- |
| Destinatari attivi | 20 milioni |
| E-mail | 42 milioni al mese |
| Direct mail | 10 milioni al mese |
| SMS mobile | 1.000.000/mese |
| Picco volume e-mail giornaliero | 5.000.000 |

### Server web e applicazioni

In questo scenario, Adobe consiglia di installare Adobe Campaign su quattro computer, due server applicazioni e due server web, con le seguenti specifiche:

**CPU quad-core da 3 Ghz+, 8 GB di RAM, RAID 1 o 10, SSD da 80 GB**

I server applicazioni supportano direttamente gli utenti della console Campaign e l’esecuzione dei flussi di lavoro delle campagne. Questa funzionalità viene implementata su due server identici per l&#39;elevata disponibilità, condividendo un file system NAS (Network-Attached Storage) per abilitare il failover.

I server web ospitano applicazioni web Campaign che supportano i 10 milioni di destinatari attivi nel sistema.

Fare riferimento a [Scenario 1: Distribuzione di dimensioni moderate](#scenario-1) per ulteriori commenti su proxy, centri preferenza/gestione sottoscrizione e utilizzo dello spazio su disco.

### Database

Le raccomandazioni hardware per il server di database sono le seguenti:

**CPU 3Ghz+ 8 core, 64 GB di RAM, RAID 1 o 10, 2 SSD da 320 GB o RAID 10, SSD da 640 GB minima**

La stima della memoria presuppone il caching completo di circa 5.000.000 destinatari per un avvio di una campagna di grandi dimensioni, oltre allo spazio buffer RDBMS per l’esecuzione di flussi di lavoro, l’importazione di dati di tracciamento e altre attività simultanee.

Si stima che lo spazio su disco necessario nel database per memorizzare tutti i dati tecnici Adobe Campaign (campagne, tracciamento, tabelle di lavoro e così via) sia di circa 280 GB in base a un periodo di conservazione di 3 mesi. Se scegli di conservare i dati di tracciamento per 6 mesi, le dimensioni del database aumentano a circa 450 GB e la conservazione a 12 mesi aumenta le dimensioni del database a circa 900 GB. I dati dei destinatari consumano circa 15 GB per questo ambiente.

## Scenario 3: Distribuzione aziendale con Centro messaggi{#scenario-3}

![](assets/scenario-3.png)

Volume stimato:

| Canale | Volume |
| ----------------------- | ----------------- |
| Destinatari attivi | 50 milioni |
| E-mail | 108 milioni al mese |
| Direct mail | 25 milioni al mese |
| SMS mobile | 2,5 milioni/mese |
| Messaggi transazionali | 2,5 milioni/mese |
| Picco volume e-mail giornaliero | 2,5 milioni |


La distribuzione che supporta 50 milioni di destinatari è essenzialmente la stessa mostrata nello [Scenario 2](#scenario-2): Il traffico dell’applicazione web Campaign viene indirizzato ai server web Campaign, pertanto gli scoppi di traffico web dopo gli avvii di grandi campagne non influiscono sui flussi di lavoro di Campaign e sugli utenti della console client.

Questa distribuzione include anche le chiamate al Centro messaggi, gestite dai siti web e dalle applicazioni personali.


### Server web e applicazioni

In questo scenario, Adobe consiglia di installare Adobe Campaign su quattro computer, come segue:

* Server applicazioni
   **Due sistemi, CPU quad-core 3Ghz+, RAM da 8 GB, SSD RAID 1 o 10, SSD da 80 GB**

* Server web
   **Due sistemi, CPU quad-core 3Ghz+, RAM da 16 GB, SSD RAID 1 o 10, SSD da 80 GB**


I server applicazioni supportano direttamente gli utenti della console Campaign e l’esecuzione dei flussi di lavoro delle campagne. Questa funzionalità viene implementata su due server identici per l&#39;elevata disponibilità, condividendo un file system NAS (Network-Attached Storage) per abilitare il failover.

I server web ospitano applicazioni web Campaign che supportano i 10 milioni di destinatari attivi nel sistema.

Fare riferimento a [Scenario 1: Distribuzione di dimensioni moderate](#scenario-1) per ulteriori commenti su proxy, centri preferenza/gestione sottoscrizione e utilizzo dello spazio su disco.

### Database

Le raccomandazioni hardware per il server di database sono le seguenti:

**CPU a 8 core da 3 Ghz+, RAM da 96 GB, RAID 1 o 10, SSD da 1,5 TB minima**

La stima della memoria presuppone il caching completo di circa 12.500.000 destinatari per un avvio di una campagna di grandi dimensioni, oltre allo spazio buffer RDBMS per l’esecuzione di flussi di lavoro, l’importazione di dati di tracciamento e altre attività simultanee.

Si stima che lo spazio su disco necessario nel database per memorizzare tutti i dati tecnici Adobe Campaign (campagne, tracciamento, tabelle di lavoro e così via) sia di circa 700 GB in base a un periodo di conservazione di 3 mesi. Se si sceglie di conservare i dati di tracciamento per 6 mesi, le dimensioni del database aumentano a circa 1,2 TB e la conservazione a 12 mesi aumenta le dimensioni del database a circa 2 TB. I dati dei destinatari consumano circa 50 GB per questo ambiente.

## Linee guida per la modifica delle ipotesi

Le ipotesi formulate per questi scenari hanno un impatto significativo sulle raccomandazioni hardware e sull&#39;architettura di distribuzione. Questa sezione illustra le linee guida relative a diverse ipotesi. Contatta il team di consulenza Adobe Campaign per suggerimenti specifici in base alle tue esigenze.

* **Numero di**
destinatariI destinatari attivi richiedono spazio di archiviazione e spazio buffer del database, pertanto un numero maggiore di destinatari in genere richiede una maggiore capacità di memoria e CPU sul server di database. Gli incrementi di archiviazione sono relativamente piccoli per i destinatari stessi, ma possono essere significativi per i dati di tracciamento degli eventi conservati per le campagne e-mail.

* **E-mail Campaign**
DimensioneLa frequenza dei lanci delle campagne ha un impatto sui requisiti della CPU del server di database. Insieme alla direct mailing, alle interazioni in entrata e ad altri flussi di lavoro, le operazioni di segmentazione per le campagne e-mail caricano notevolmente il server di database.

* **Direct Mail**
FrequencyLa frequenza delle direct mailing può influire sui requisiti della CPU del server di database. Insieme ai lanci di campagne e ad altri flussi di lavoro, le operazioni di segmentazione per gli invii diretti caricano notevolmente il server di database.

* **SMS Message**
VolumeLike dimensione della campagna e-mail, il volume del messaggio SMS non inserisce carichi di grandi dimensioni sui server Campaign situati on-premise; il caricamento è eseguito principalmente sui server Adobe Cloud Messaging sul cloud. La segmentazione per le campagne SMS, come e-mail e direct mailing, può caricare notevolmente il database di marketing. Pertanto la frequenza degli avvii delle campagne SMS e la complessità della segmentazione sono più rilevanti del volume dei messaggi SMS.

* **Complessità**
dello schema di databaseLa quantità di dati per ogni destinatario attivo richiede spazio di archiviazione e spazio buffer del database, pertanto più destinatari in genere richiedono più memoria e CPU sul server di database. Gli schemi complessi richiedono anche l’unione di più tabelle per la segmentazione, pertanto le operazioni di segmentazione possono essere eseguite molto più lentamente e richiedono più CPU e memoria del database quando i dati vengono distribuiti su più tabelle.

   La memoria del server di database viene stimata garantendo che il pool di buffer del database possa essere sufficientemente grande da contenere tutti i dati dei destinatari, oltre alle tabelle temporanee per l&#39;esecuzione dei flussi di lavoro, oltre a un margine per altre operazioni del database.

* **Le regole di**
utilizzo dell&#39;interazione in uscita per l&#39;interazione in modalità batch vengono valutate nei flussi di lavoro che trasferiscono al database tutta la complessità del calcolo. Il principale fattore di sforzo sul database è il numero totale di offerte ammissibili calcolate durante una chiamata al motore (dimensione obiettivo X numero medio di offerte per destinatario prima di mantenere le N migliori offerte). La velocità della CPU del server di database è il primo fattore di prestazioni.

* **Le regole e le offerte di interazione in entrata o API SOAP**
UsageInbound vengono valutate nel database di marketing, richiedendo notevoli risorse del server di database, in particolare la CPU. L’utilizzo intensivo di Interazioni in entrata o API SOAP richiede server web separati per separare il carico di lavoro dall’esecuzione dei flussi di lavoro di Campaign.

* **Tracciamento del**
periodo di conservazione dei datiL&#39;aumento della conservazione dei dati di tracciamento oltre i 90 giorni richiede più spazio di archiviazione del database e può rallentare il sistema perché l&#39;inserimento di nuovi dati di tracciamento va in tabelle di grandi dimensioni. I dati di tracciamento non sono utili per la segmentazione delle campagne dopo 90 giorni, pertanto si consiglia di ridurre il periodo di conservazione.

   I dati di tracciamento devono essere spostati in Adobe Analytics o in un altro sistema di analisi se hai bisogno di un’analisi a lungo termine dell’esperienza di marketing dei destinatari.

## Virtualizzazione

Tutti i server Campaign sono candidati ideali per la virtualizzazione. Vari problemi devono essere affrontati per garantire la disponibilità e le prestazioni adeguate.

* **I server**
di configurazione non riusciti, ad esempio i server applicazioni ridondanti con un proxy con bilanciamento del carico, devono essere distribuiti su un hardware separato per garantire che entrambe le VM non si spegnano in caso di errore hardware.

* **Configurazione I/O**
Qualsiasi configurazione RAID consigliata deve essere mantenuta per la sicurezza del database, per garantire che la perdita di un dispositivo di storage non causi la perdita di dati.

* ****
Prestazioni I/OÈ necessario rispettare la classificazione IOPS consigliata per lo storage del database. I servizi cloud come Amazon EC2 potrebbero non fornire le prestazioni richieste e devono essere valutati attentamente. Ad esempio, i volumi SSD con provisioning Amazon EC2 sono attualmente valutati a 20.000 IOPS ciascuno. Ulteriori informazioni sono disponibili nella [documentazione Amazon](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html), in modo che una configurazione RAID a 4 volumi venga classificata a 80.000 IOPS, il che potrebbe non essere sufficiente.

Adobe consiglia di eseguire test delle prestazioni per qualsiasi implementazione virtualizzata di Adobe Campaign prima di mettere il sistema in produzione.

## Argomenti correlati

* [Processi di monitoraggio delle campagne](../../production/using/monitoring-processes.md)
* [Architettura generale della campagna](../../installation/using/general-architecture.md)
* [Prestazioni e problemi di velocità effettiva](../../production/using/performance-and-throughput-issues.md)
* [Lista di controllo per sicurezza e privacy](../../installation/using/get-started-security-privacy.md)
