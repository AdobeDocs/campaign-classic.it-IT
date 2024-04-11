---
product: campaign
title: Consigli per il dimensionamento hardware per Campaign Classic v7
description: Consigli per il dimensionamento hardware per Campaign Classic v7
feature: Technote
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2569'
ht-degree: 1%

---

# Consigli sui requisiti hardware in base alle dimensioni{#hardware-sizing-reco}



## Panoramica

>[!CAUTION]
>
>Questo articolo viene fornito solo come guida di esempio generale. Prima di avviare il progetto Campaign, rivolgiti al tuo Customer Success Manager Adobe Campaign per misurare esattamente le dimensioni della tua implementazione. **Do not** acquisire o distribuire qualsiasi infrastruttura o hardware fino al termine dell&#39;operazione.

Questo documento fornisce consigli generali per l’implementazione di Adobe Campaign Classic v7 nel data center on-premise o nell’ambiente cloud virtualizzato. Questo tipo di distribuzione, denominata **ibrido** o **mid-sourcing**, posiziona l’istanza di marketing e il database di marketing di Campaign sotto il tuo controllo operativo, mentre utilizzi i servizi di messaggistica Adobe Cloud per inviare e-mail, SMS o messaggi SMPP e raccogliere i dati di apertura, mancato recapito e tracciamento dei clic delle e-mail.

L’istanza marketing è la parte dell’architettura di Adobe Campaign che gestisce tutte le attività di marketing e memorizza tutti i dati dei destinatari e i dati analitici restituiti dalle campagne. L’istanza marketing è un set di server locali che eseguono servizi Adobe Campaign e un database relazionale.

>[!CAUTION]
>
>Le informazioni contenute in questo documento non si applicano se utilizzi un’istanza Adobe Campaign completamente in hosting (distribuita in Cloud Service di Adobi).

La compatibilità software è descritta in [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).


### Scenari

I diagrammi di distribuzione e i suggerimenti per il dimensionamento dell&#39;hardware vengono forniti per tre scenari rappresentativi:

1. [Moderate-Size](#scenario-1) - 5 milioni di destinatari attivi nel sistema
1. [Grande dimensione](#scenario-2) - 20 milioni di beneficiari attivi nel sistema
1. [Enterprise](#scenario-3) - 50 milioni di destinatari attivi, con messaggistica transazionale

### Presupposti

In questo documento vengono inoltre utilizzati i seguenti tipi di utilizzo per tutti e tre gli scenari:

* Le campagne e-mail di grandi dimensioni vengono inviate due volte alla settimana, a circa il 50% dei destinatari attivi
* Le direct mailing vengono generate una volta al mese per ogni destinatario nel sistema
* I messaggi SMS vengono inviati a circa il 10% dei destinatari attivi ogni mese
* Lo schema di database che definisce ogni destinatario è stato esteso con una tabella aggiuntiva, contenente circa 200 byte di dati per ogni destinatario
* Il modulo di interazione di Adobe Campaign viene utilizzato per aggiungere offerte all’e-mail in uscita
* I dati di tracciamento delle e-mail vengono conservati nel sistema Campaign per 90 giorni

## Linee guida generali

Campaign è un’applicazione incentrata sul database e le prestazioni del server di database sono fondamentali. Flussi di lavoro in esecuzione, segmentazione, tracciamento dei caricamenti di dati, interazioni in entrata, analisi e altre attività generano tutte attività di database. In generale, le dimensioni e la frequenza di queste operazioni determinano le dimensioni dei server di database.

I server applicazioni nell’istanza marketing richiedono CPU e memoria sufficienti per eseguire flussi di lavoro e rispondere alle chiamate API SOAP, incluse le richieste degli utenti della console Campaign. I requisiti della CPU possono essere significativi per i flussi di lavoro che utilizzano interazioni in uscita con regole di offerta complesse, flussi di lavoro che eseguono JavaScript personalizzato e applicazioni web con livelli di traffico elevati.

Le applicazioni web di Campaign possono essere distribuite anche sui server app dell’istanza di marketing o su sistemi server web separati. Poiché i carichi di lavoro delle applicazioni web entrano in conflitto con i flussi di lavoro critici e gli utenti della console Campaign, le applicazioni web e le interazioni in entrata possono essere distribuite su server separati, per garantire che le funzionalità principali di Campaign vengano eseguite in modo affidabile e con buone prestazioni.

Per sicurezza e disponibilità, l’Adobe consiglia di separare il traffico di Internet dal traffico generato dagli utenti aziendali. Per questo motivo, i diagrammi contengono due gruppi di server: il server Web (Internet, Web1 e Web2) e i server app (processi aziendali, App1 e App2).

Per i mittenti di e-mail commerciali è un requisito legale disporre di una pagina web di rinuncia funzionale. L&#39;Adobe consiglia di disporre di un computer ridondante in ciascun server di gruppo per scenari di failover. È particolarmente vero se Adobe Campaign ospita le pagine di rinuncia.

### Inverti proxy

L’architettura di Campaign applica un livello di sicurezza elevato utilizzando SSL su HTTP (HTTPS) per comunicare tra l’istanza di marketing e Adobe Cloud Messaging. Sicurezza, affidabilità e disponibilità vengono applicate utilizzando proxy inversi in una subnet &quot;zona demilitarizzata&quot; (DMZ) per isolare e proteggere i server e il database delle istanze di marketing.

### Load balancer

Il load balancer per i server app è configurato in una configurazione attiva/passiva, con HTTPS terminato sul proxy. Il load balancer per i server Web è configurato in una configurazione attiva/attiva, con HTTPS terminato nel proxy.

L’Adobe fornisce un elenco esclusivo dei percorsi URL che possono essere inoltrati al server Adobe Campaign nell’ambiente di distribuzione.

### Architettura

L&#39;architettura generale è quasi identica indipendentemente dai volumi. I requisiti di sicurezza e di elevata disponibilità richiedono almeno quattro server, due dei quali se non si utilizzano applicazioni Web. La differenza nella configurazione varia principalmente nella configurazione hardware, come il core della CPU e la memoria.

## Scenario 1: distribuzione di dimensioni medie{#scenario-1}

![](assets/scenario-1.png)

Volume stimato:

| Canale | Volume |
| ----------------------- | ----------------- |
| Destinatari attivi | 5 milioni |
| E-mail | 4,2 milioni/mese |
| Direct mail | 1 milione/mese |
| SMS mobile | 100.000/mese |
| Volume e-mail giornaliero di picco | 500 |

Per questi volumi, una coppia di sistemi Application Server Adobe Campaign offre tutte le funzionalità per gli utenti del client Adobe Campaign e l&#39;esecuzione dei flussi di lavoro. Per 5 milioni di destinatari attivi e questo volume di e-mail, i carichi di lavoro del server dell&#39;applicazione non sono a uso intensivo di CPU o I/O; la maggior parte della pressione è sul database.

I server Web Adobe Campaign sono visualizzati nell&#39;area protetta.

### Server Web e Application Server

Questo scenario consiglia di installare Adobe Campaign su quattro computer, con le seguenti specifiche:

**CPU quad-core da 3 GHz, 8 GB di RAM, RAID 1 o 10, 2 unità SSD da 80 GB**

Questi sistemi creano l’istanza di marketing Application Server che supporta direttamente gli utenti della console Campaign ed esegue i flussi di lavoro della campagna.

Inverti i proxy in un traffico di bilanciamento del carico DMZ verso i server web Adobe Campaign. Non è necessario installare lo stack di software Adobe Campaign sui computer proxy; è possibile utilizzare qualsiasi software proxy inverso o apparecchiatura di rete.

Le funzioni di consenso/rinuncia all’abbonamento e centro preferenze possono essere fornite da Campaign o dal tuo sito web. Se scegli di implementare questa funzionalità sul tuo sito web, devi assicurarti che le informazioni sulle preferenze e sugli abbonamenti vengano propagate al database di marketing di Campaign. Normalmente viene eseguita creando file di estrazione che vengono caricati automaticamente dai flussi di lavoro di Campaign.

Il consumo di spazio su disco nei server applicazioni dipende dal periodo di conservazione dei file scambiati con provider di servizi di terze parti (ad esempio, fornitori di stampa per Direct Mail) e dalle dimensioni e dalla conservazione dei file flat importati, come gli aggiornamenti delle sottoscrizioni o delle preferenze dal sito Web o estratti dai sistemi CRM o di marketing.

### Database

Di seguito sono riportate le raccomandazioni hardware per il server di database.

**CPU 3Ghz+ a 4 core, 16 GB di RAM, RAID 1 o 10, SSD da 128 GB minimo**

La stima della memoria presuppone il caching completo di circa 500.000 destinatari per un lancio di una campagna di grandi dimensioni, più spazio buffer RDBMS per l’esecuzione di flussi di lavoro, l’importazione di dati di tracciamento e altre attività simultanee.

Si stima che lo spazio su disco necessario nel database per memorizzare tutti i dati tecnici di Adobe Campaign (campagne, tracciamento, tabelle di lavoro e così via) sia di circa 35 GB in base a un periodo di conservazione di tre mesi. Se si sceglie di conservare i dati di tracciamento per 6 mesi, le dimensioni del database aumentano fino a circa 40 GB e la conservazione a 12 mesi aumenta le dimensioni del database fino a circa 45 GB. I dati dei destinatari consumano circa 5 GB per questo ambiente.

>[!CAUTION]
>
>Questa stima non include dati aggiuntivi sul cliente. Se si prevede di replicare colonne o tabelle aggiuntive di dati dei clienti nel database di Adobe Campaign, è necessario stimare il fabbisogno di spazio su disco aggiuntivo per tale database. Anche i segmenti o gli elenchi caricati richiedono più spazio di archiviazione, a seconda delle dimensioni, della frequenza e del periodo di conservazione.

Considera inoltre che, a causa del volume di informazioni elaborate ogni giorno, le operazioni di I/O al secondo del server di database sono fondamentali. Ad esempio, in un giorno di picco, puoi distribuire campagne indirizzate a un totale di 500.000 destinatari. Per eseguire ogni campagna, Adobe Campaign inserisce 500.000 record in una tabella contenente circa 12 milioni di record (la tabella del registro di consegna). Per fornire prestazioni accettabili durante la distribuzione della campagna, l’Adobe consiglia un minimo di 60.000 IOPS casuali di lettura/scrittura da 4 KB per questo scenario.


## Scenario 2: distribuzione di grandi dimensioni{#scenario-2}

![](assets/scenario-2.png)

Volume stimato:

| Canale | Volume |
| ----------------------- | ----------------- |
| Destinatari attivi | 20 milioni |
| E-mail | 42 milioni/mese |
| Direct mail | 10 milioni/mese |
| SMS mobile | 1.000.000/mese |
| Volume e-mail giornaliero di picco | 5.000.000 |

### Server Web e Application Server

In questo scenario, Adobe consiglia di installare Adobe Campaign su quattro computer, due server applicazioni e due server web, con le seguenti specifiche:

**CPU quad-core da 3 GHz, 8 GB di RAM, RAID 1 o 10, SSD da 80 GB**

Gli Application Server supportano direttamente gli utenti della console Campaign e l’esecuzione dei flussi di lavoro delle campagne. Questa funzionalità viene implementata su due server identici per l&#39;elevata disponibilità, condividendo un file system NAS (Network-Attached Storage) per abilitare il failover.

I server web ospitano applicazioni web di Campaign che supportano 10 milioni di destinatari attivi nel sistema.

Fai riferimento a [Scenario 1: distribuzione di dimensioni medie](#scenario-1) per ulteriori commenti su proxy, centri preferenze/gestione degli abbonamenti e utilizzo dello spazio su disco.

### Database

Di seguito sono riportate le raccomandazioni hardware per il server di database.

**CPU 3Ghz+ 8-core, 64 GB di RAM, RAID 1 o 10, 2 x 320 GB SSD o RAID 10, 640 GB SSD minimo**

La stima della memoria presuppone il caching completo di circa 5.000.000 di destinatari per un lancio di una campagna di grandi dimensioni, più spazio buffer RDBMS per l’esecuzione di flussi di lavoro, l’importazione di dati di tracciamento e altre attività simultanee.

Si stima che lo spazio su disco necessario nel database per memorizzare tutti i dati tecnici di Adobe Campaign (campagne, tracciamento, tabelle di lavoro e così via) sia di circa 280 GB in base a un periodo di conservazione di 3 mesi. Se si sceglie di conservare i dati di tracciamento per 6 mesi, le dimensioni del database aumentano fino a circa 450 GB e la conservazione a 12 mesi aumenta le dimensioni del database fino a circa 900 GB. I dati dei destinatari consumano circa 15 GB per questo ambiente.

## Scenario 3: distribuzione aziendale con Centro messaggi{#scenario-3}

![](assets/scenario-3.png)

Volume stimato:

| Canale | Volume |
| ----------------------- | ----------------- |
| Destinatari attivi | 50 milioni |
| E-mail | 108 milioni/mese |
| Direct mail | 25 milioni/mese |
| SMS mobile | 2,5 milioni/mese |
| Messaggi transazionali | 2,5 milioni/mese |
| Volume e-mail giornaliero di picco | 2,5 milioni |


La distribuzione che supporta 50 milioni di destinatari è sostanzialmente la stessa di cui [Scenario 2](#scenario-2): il traffico delle applicazioni web di Campaign viene indirizzato ai server web di Campaign, pertanto i picchi di traffico web dopo lanci di campagne di grandi dimensioni non influiscono sui flussi di lavoro di Campaign e sugli utenti della console client.

Questa distribuzione include anche le chiamate al Centro messaggi, guidate dai siti web e dalle applicazioni personali.


### Server Web e Application Server

In questo scenario, Adobe consiglia di installare Adobe Campaign su quattro computer, come segue:

* Server applicazioni
  **Due sistemi, CPU quad-core da 3 GHz, 8 GB di RAM, RAID 1 o 10, SSD da 80 GB**

* Server web
  **Due sistemi, CPU quad-core da 3 GHz, 16 GB di RAM, RAID 1 o 10, SSD da 80 GB**


Gli Application Server supportano direttamente gli utenti della console Campaign e l’esecuzione dei flussi di lavoro delle campagne. Questa funzionalità viene implementata su due server identici per l&#39;elevata disponibilità, condividendo un file system NAS (Network-Attached Storage) per abilitare il failover.

I server web ospitano applicazioni web di Campaign che supportano 10 milioni di destinatari attivi nel sistema.

Fai riferimento a [Scenario 1: distribuzione di dimensioni medie](#scenario-1) per ulteriori commenti su proxy, centri preferenze/gestione degli abbonamenti e utilizzo dello spazio su disco.

### Database

Di seguito sono riportate le raccomandazioni hardware per il server di database.

**CPU 3Ghz+ 8-core, RAM 96 GB, RAID 1 o 10, SSD da 1,5 TB (minimo)**

La stima della memoria presuppone il caching completo di circa 12.500.000 destinatari per un lancio di una campagna di grandi dimensioni, più spazio buffer RDBMS per l’esecuzione di flussi di lavoro, l’importazione di dati di tracciamento e altre attività simultanee.

Si stima che lo spazio su disco necessario nel database per memorizzare tutti i dati tecnici di Adobe Campaign (campagne, tracciamento, tabelle di lavoro e così via) sia di circa 700 GB in base a un periodo di conservazione di 3 mesi. Se si sceglie di conservare i dati di tracciamento per 6 mesi, le dimensioni del database aumentano fino a circa 1,2 TB e la conservazione a 12 mesi aumenta le dimensioni del database fino a circa 2 TB. I dati dei destinatari consumano circa 50 GB per questo ambiente.

## Linee guida per la modifica delle ipotesi

Le ipotesi formulate per questi scenari hanno tutti un impatto significativo sui suggerimenti hardware e sull&#39;architettura di distribuzione. In questa sezione vengono illustrate le linee guida basate su presupposti diversi. Contatta il team di consulenza Adobe Campaign per consigli specifici per soddisfare le tue esigenze.

* **Numero di destinatari**
I destinatari attivi richiedono sia spazio di archiviazione che spazio buffer del database, pertanto più destinatari in genere richiedono più memoria e capacità della CPU sul server del database. Gli aumenti di archiviazione sono relativamente piccoli per i destinatari stessi, ma possono essere significativi per i dati di tracciamento degli eventi conservati per le campagne e-mail.

* **Dimensione campagna e-mail**
La frequenza dei lanci delle campagne ha un impatto sui requisiti della CPU del server di database. In combinazione con direct mailing, interazioni in entrata e altri flussi di lavoro, le operazioni di segmentazione per le campagne e-mail hanno messo un carico significativo sul server del database.

* **Frequenza direct mailing**
La frequenza delle direct mailing può influire sui requisiti della CPU del server di database. In combinazione con i lanci di campagne e altri flussi di lavoro, le operazioni di segmentazione per la posta diretta hanno comportato un carico significativo sul server del database.

* **Volume messaggio SMS**
Come per la dimensione della campagna e-mail, il volume dei messaggi SMS non carica grandi quantità sui server Campaign situati on-premise; il carico si trova principalmente sui server Adobe Cloud Messaging sul cloud. La segmentazione per le campagne SMS, come e-mail e direct mail, può comportare un carico significativo sul database di marketing. Pertanto, la frequenza dei lanci di campagne SMS e la complessità della segmentazione sono più rilevanti del volume di messaggi SMS.

* **Complessità dello schema del database**
La quantità di dati per ogni destinatario attivo richiede sia spazio di archiviazione che spazio buffer del database, pertanto più destinatari in genere richiedono più memoria e CPU sul server del database. Gli schemi complessi richiedono inoltre l’unione di più tabelle per la segmentazione, in modo che le operazioni di segmentazione possano essere eseguite molto più lentamente e richiedano più CPU e memoria del database quando i dati vengono distribuiti su più tabelle.

  La memoria del server di database viene stimata assicurandosi che il pool di buffer del database possa essere sufficientemente grande da contenere tutti i dati dei destinatari, più tabelle temporanee per l&#39;esecuzione dei flussi di lavoro e un margine per altre operazioni del database.

* **Utilizzo dell’interazione in uscita**
Le regole di interazione in modalità batch vengono valutate nei flussi di lavoro che trasferiscono tutta la complessità di calcolo al database. Il fattore principale di impegno nel database è il numero totale di offerte idonee calcolate durante una chiamata al motore (dimensione target X numero medio di offerte per destinatario prima di mantenere le N migliori offerte). La velocità della CPU del server di database è il primo fattore di prestazioni.

* **Interazioni in entrata o utilizzo dell’API SOAP**
Le regole e le offerte di interazione in entrata vengono valutate nel database di marketing, e richiedono notevoli risorse del server di database, in particolare la CPU. L’utilizzo intensivo delle interazioni in entrata o delle API SOAP richiede server web separati per separare il carico di lavoro dall’esecuzione dei flussi di lavoro di Campaign.

* **Tracciamento del periodo di conservazione dei dati**
Un aumento della conservazione dei dati di tracciamento oltre i 90 giorni richiede una maggiore capacità di archiviazione del database e può rallentare il sistema perché l’inserimento di nuovi dati di tracciamento va a beneficio di tabelle di grandi dimensioni. Il tracciamento dei dati non è utile per la segmentazione della campagna dopo 90 giorni, pertanto si consiglia di ridurre il periodo di conservazione.

  Se hai bisogno di un’analisi a lungo termine dell’esperienza di marketing del destinatario, i dati di tracciamento devono essere spostati in Adobe Analytics o in un altro sistema di analisi.

## Virtualizzazione

Tutti i server di Campaign sono buoni candidati per la virtualizzazione. Per garantire disponibilità e prestazioni appropriate, è necessario affrontare diversi problemi.

* **Configurazione di failover**
I server cluster, ad esempio i server applicazioni ridondanti in un proxy con carico bilanciato, devono essere distribuiti su hardware separato per garantire che entrambe le VM non vadano in esaurimento in caso di guasto hardware.

* **Configurazione I/O**
Qualsiasi configurazione RAID consigliata deve essere mantenuta per la sicurezza del database, per garantire che la perdita di un dispositivo di storage non causi la perdita di dati.

* **Prestazioni I/O**
La classificazione IOPS consigliata per l&#39;archiviazione del database deve essere rispettata. I servizi cloud come Amazon EC2 potrebbero non fornire le prestazioni richieste e devono essere valutati attentamente. Ad esempio, i volumi SSD con provisioning Amazon EC2 sono attualmente classificati a 20.000 IOPS ciascuno. Ulteriori informazioni in [Documentazione di Amazon](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)), in modo che una configurazione RAID a 4 volumi sia classificata a 80.000 IOPS, che potrebbe non essere sufficiente.

Adobe consiglia di eseguire test delle prestazioni per qualsiasi installazione virtualizzata di Adobe Campaign prima di metterla in produzione.

## Argomenti correlati

* [Processi di monitoraggio delle campagne](../../production/using/monitoring-processes.md)
* [Architettura generale di Campaign](../../installation/using/general-architecture.md)
* [Problemi relativi a prestazioni e velocità effettiva](../../production/using/performance-and-throughput-issues.md)
* [Lista di controllo per sicurezza e privacy](../../installation/using/get-started-security-privacy.md)
