---
title: Ultima versione
description: Ultima versione Campaign Classic
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2163'
ht-degree: 76%

---


# Ultima versione{#latest-release}

![](assets/do-not-localize/cp-icon.png) **Nuova versione del Pannello di controllo Campaign di giugno** con monitoraggio dei profili attivi, audit del recapito messaggi del sottodominio e gestione delle chiavi GPG. [Ulteriori informazioni](https://docs.adobe.com/content/help/it-IT/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) Versione 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_11 settembre 2020_

* Risolto un problema di regressione che causava il blocco della preparazione della consegna a causa di una singola funzione errata sulla parte di consegna che generava un sovraccarico di memoria. (NEO-27346)
* È stato risolto un problema di post-aggiornamento che disattivava Apache e il server Web prima della ripubblicazione dell’applicazione Web. (NEO-27155)
* È stata corretta una regressione nella gestione dei modelli HTML che causava la visualizzazione degli URL di tracciamento a causa di un&#39;interpretazione errata delle schede. (NEO-25909)
* È stato risolto un problema relativo al flusso di lavoro di pulizia del database che poteva non riuscire a causa di un&#39;origine dati non gestita. (NEO-23160, NEO-23364)
* Il flusso di lavoro di pulizia ora svuota gli elenchi scaduti per batch di 100 invece di uno per uno.
* È stata corretta una regressione che impediva di modificare il nome interno di un account esterno. (NEO-27323)
* Correzione di una regressione durante l&#39;aggiornamento successivo che causava un avvio errato del server (log degli errori).
* La gestione degli aggiornamenti per la memoria condivisa è stata migliorata. I passaggi aggiuntivi richiesti in 20.2 non sono più necessari.

## ![](assets/do-not-localize/orange_2.png) Versione 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_22 luglio 2020_

* È stato risolto un problema che impediva il funzionamento del tracciamento quando la funzione di firma era disabilitata. (NEO-26411)
* È stato risolto un problema che causava il blocco dei collegamenti non firmati da domini personalizzati quando questi dovevano essere consentiti. (NEO-25210)
* È stato risolto un problema che poteva impedire di aprire/fare clic sugli URL di tracciamento quando si utilizzavano alcune versioni precedenti di Outlook. (NEO-25688)
* È stato corretto un problema a causa del quale gli URL delle pagine mirror venivano definiti in modo non corretto nelle comunicazioni e-mail (a causa di un controllo errato dei caratteri ASCII). (NEO-26084)
* È stato risolto un problema con la gestione degli URL di codifica nel servizio di anti-phishing. (NEO-25283)
* È stato risolto un problema che impediva il funzionamento del tracciamento degli URL tramite frammenti nei parametri di personalizzazione (tag di ancoraggio con cancelletto). (NEO-25774)
* È stato risolto un problema di tracciamento quando si utilizzavano formule di tracciamento personalizzate specifiche. (NEO-25277)
* È stato risolto un problema che impediva il monitoraggio dei &quot;clic di notifica&quot; (notifiche push iOS e Android). (NEO-25965)
* È stato corretto un problema di regressione che interessava i campi calcolati in un flusso di lavoro e causava un errore nel flusso di lavoro. (NEO-25194)
* È stata corretta una regressione che impediva il funzionamento della creazione immediata di URL di tracciamento Web. (NEO-20999)
* È stato risolto un problema di regressione con i rapporti di consegna forniti che venivano visualizzati troncati quando venivano esportati in PDF. (NEO-25757)
* È stato risolto un problema di arresto anomalo nella procedura guidata di distribuzione.
* È stato risolto un problema che poteva impedire il corretto funzionamento del flusso di lavoro di notifica dell&#39;offerta dopo un post aggiornamento.
* Il connettore iOS HTTP2 è stato migliorato (aggiornamenti di terze parti e gestione degli errori). (NEO-25904, NEO-25903)
* L&#39;elenco jarsToSkip in catalina.properties è stato aggiornato per rimuovere il riferimento a un file jar non più utilizzato (notifiche iOS).
* È stato risolto un problema che impediva la preparazione della consegna dopo l&#39;aggiornamento postaggiornato.
* Dopo il passaggio al [nuovo meccanismo](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)ID sequenza, tutte le applicazioni Web che aggiornano la tabella dei destinatari vengono ripubblicate durante il post-aggiornamento.
* Risolto un problema di potenziale vulnerabilità XSS nel contenuto di distribuzione. (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) Versione 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_8 giugno 2020_

**Novità?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Supporto delle emoticon</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Durante la progettazione di un messaggio in Campaign, puoi ora inserire facilmente gli emoticon nel corpo del messaggio, utilizzando un pulsante apposito. Gli emoticon possono essere aggiunti anche nella riga dell’oggetto dell’e-mail. Puoi personalizzare l’elenco degli emoticon disponibili nell’interfaccia.</p>
    <p>Per ulteriori informazioni sull’aggiunta degli emoticon, consulta la <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">documentazione dettagliata</a>. Scopri come personalizzare l’elenco degli emoticon <a href="../../delivery/using/customizing-emoticon-list.md">in questa sezione</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connettore FDA per Azure Synapse</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Puoi ora collegare la tua istanza di Campaign al database esterno di Azure Synapse. Questa connessione viene gestita tramite un nuovo account esterno.</p>
    <p>Azure Synapse è disponibile solo per gli ambienti Hybrid e On-Premise. Per ulteriori informazioni, consulta la <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">documentazione dettagliata</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Leggi sulla privacy in Thailandia e Brasile</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La Legge sulla Protezione dei Dati Personali (Personal Data Protection Act, PDPA) thailandese è la nuova legge sulla privacy che armonizza e modernizza i requisiti di protezione dei dati in Thailandia. </p>
   <p>La società brasiliana Lei Geral de Proteção de Dados (LGPD) sarà attiva all'inizio del 2021 per tutte le aziende che raccolgono o trattano dati personali in Brasile.</p>
   <p>Queste normative si applicano ai clienti di Adobe Campaign che conservano dati per soggetti residenti in questi paesi. Oltre alle funzionalità relative alla privacy già disponibili in Campaign (compresa la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli degli utenti), stiamo sfruttando questa opportunità per includere funzionalità aggiuntive, al fine di aiutarti ad essere pronto per l’entrata in vigore di PDPA e LGPD:</p>
   <ul> 
     <li><p>Diritto di accesso e Diritto di eliminazione: stiamo sfruttando le funzionalità aggiunte per il GDPR e il CCPA. <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">Leggi tutto</a></p></li> 
     <li> <p>Durante la creazione di una richiesta di privacy tramite l’interfaccia o l’API di Campaign, ora selezioni il tipo di <strong>normativa</strong>: PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Ulteriori informazioni</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Per impostazione predefinita, per tutti i clienti è attivata la protezione migliorata per il tracking dei collegamenti nelle e-mail. In aggiunta, è disponibile una funzione di sicurezza avanzata che può essere abilitata contattando l’Assistenza clienti. Ulteriori dettagli sulla funzione e sui passaggi che i clienti non in hosting devono seguire per abilitarla sono disponibili nella [Lista di controllo protezione e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html). (NEO-24232)

* Per ottimizzare la protezione, l’algoritmo di hash MD5 utilizzato per generare i nomi dei file è stato rafforzato con l’algoritmo sha256 per il caricamento di file pubblici. (NEO-17044)

* Per rafforzare la protezione contro gli attacchi XSS, gli script lato client vengono disabilitati durante l’esecuzione di una pagina mirror. (NEO-17987)

* È stato risolto un problema che impediva al flusso di lavoro tecnico **Pulizia richieste privacy** di eliminare i dati di riconciliazione. (NEO-25168, NEO-21004)

* È stato risolto un problema con l’attività **File Transfer** che impediva il funzionamento dell’autenticazione basata su chiave SFTP su Debian 9. (NEO-23183)

**Miglioramenti della compatibilità**

Campaign supporta ora i seguenti sistemi:
* Sistemi operativi: Debian 10
* RDBMS: Oracle 18c e Oracle 19c
* FDA: Azure Synapse Analytics

Ulteriori informazioni nella [matrice di compatibilità di Campaign](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html).

**Miglioramenti**

* La messaggistica transazionale è stata migliorata per offrire una migliore user experience. Ora puoi annullare la pubblicazione di un modello di messaggio transazionale, eliminandolo dalle istanze di esecuzione. [Ulteriori informazioni](../../message-center/using/template-unpublication.md).

* Sono disponibili nuove opzioni per impostare limitazioni durante l’invio di e-mail che includono immagini o allegati. Tali protezioni possono evitare problemi di prestazioni, il che è particolarmente utile con la messaggistica transazionale. [Leggi tutto](../../installation/using/configuring-campaign-options.md#delivery)

* La nuova opzione **Prepare the delivery parts in the database** consente di eseguire la preparazione della consegna direttamente all’interno del database, il che può accelerare notevolmente l’analisi. Questa opzione è disponibile solo per configurazioni specifiche. [Ulteriori informazioni](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Sono state migliorate le prestazioni dell’[attività del connettore della gestione delle relazioni con i clienti](../../workflow/using/crm-connector.md) per Microsoft Dynamics. (NEO-13303, NEO-12710)

* La versione della memoria condivisa è stata aumentata.

   >[!WARNING]
   >
   >Questo miglioramento richiede un ulteriore passaggio al termine dell’aggiornamento. Consulta la sezione **Evoluzioni tecniche** di seguito.

* Il flusso di lavoro di pulizia è stato migliorato. Anche le tabelle di lavoro isolate di tutti i flussi di lavoro eliminati vengono ora eliminate automaticamente dal flusso di lavoro di pulizia. [Ulteriori informazioni](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* I certificati per le app mobili iOS con il connettore iOS HTTP2 vengono ora convalidati prima dell’invio di notifiche push, impedendo in tal modo la mancata riuscita delle consegne a causa di certificati scaduti.

* La gestione delle connessioni proxy HTTP è stata migliorata. [Ulteriori informazioni](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Altre modifiche**

* I connettori SMS legacy sono ora obsoleti. Consulta la [pagina Funzioni obsolete](../../rn/using/deprecated-features.md).

* Non puoi più utilizzare il tuo account Litmus per predisporre e utilizzare il rendering della casella in entrata in Adobe Campaign. [Ulteriori informazioni](../../delivery/using/inbox-rendering.md).

* Per distinguere meglio le viste dalle cartelle, il colore dei nomi delle viste è stato modificato da blu scuro a ciano scuro. [Leggi tutto](../../platform/using/access-management.md#about-views)

* Campaign Classic può ora essere collegato agli account per la gestione delle relazioni con i clienti di Microsoft Dynamics in hosting nelle aree geografiche di Regno Unito, India e Canada. Ciò vale per i tipi di distribuzione Office 365 e On-Premise (Dynamics 2015).

* Campaign esegue ora una verifica TLS per verificare che il nome host del server corrisponda al nome host nel certificato fornito.

* La tabella delle statistiche di consegna e tracking visualizza ora una voce per ogni consegna per il canale SMS, invece di una voce per destinatario della consegna.

* È stato aggiunto un messaggio di errore nel file di log per avvisare gli utenti quando il file scaricato ha dimensioni maggiori dello spazio su disco.

* Sono ora disponibili le seguenti funzioni per il connettore Snowflake: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Evoluzioni tecniche**

Questa nuova build aggiorna la memoria condivisa e richiede passaggi aggiuntivi per eseguire l’aggiornamento. In qualità di amministratore di Campaign, devi rimuovere i segmenti di memoria. Questi passaggi sono obbligatori, poiché i vecchi segmenti impediranno l’avvio di nlserver/nlsrvmod.

Su Windows, è necessario riavviare il sistema.

Su Debian/CentOs, è necessaria l’eliminazione della memoria condivisa. Di seguito sono riportati i passaggi da seguire:

Prima di eseguire l’aggiornamento, è necessario seguire questi passaggi:

1. Arrestare il servizio apache2 (http2 su CentOS) se è in esecuzione.
1. Arrestate il servizio nlserver (nlserver6 per build precedenti) se è in esecuzione.

Dopo l’aggiornamento:

1. Se la versione è precedente alla versione corrente, rimuovere la memoria condivisa utilizzando il comando **ipcrm**.
1. Avviare il servizio nlserver se era in esecuzione.
1. Avviare il servizio apache2 se era in esecuzione.

Di seguito sono riportate le righe di comando per Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Un esempio per Linux è disponibile in questa [pagina](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Patch**

* È stato risolto un problema di regressione minore nei log del flusso di lavoro di pulizia.
* È stato risolto un problema nell’attività **Loading (SOAP)** del flusso di lavoro durante l’analisi dei file WSDL.
* È stato risolto un problema che causava un errore durante l’aggiornamento di numerosi flussi di lavoro tramite un’attività **Survey** per elaborare in modo efficiente un elevato numero di flussi di lavoro.
* È stato risolto un problema di connettività intermittente durante l’elaborazione di messaggi inMail dall’MTA avanzato. (NEO-20380)
* È stato risolto un problema che impediva la corretta visualizzazione delle percentuali di hot click quando le immagini venivano visualizzate con una larghezza del 100% nell’HTML. (NEO-23203)
* È stato risolto un problema che impediva la visualizzazione completa del contenuto condizionale della consegna nel report sugli hot click. (NEO-18729)
* È stato risolto un problema che saltava il passaggio di approvazione del target quando si riprendeva un flusso di lavoro per inviare una consegna ricorrente. (NEO-18166)
* È stato risolto un problema che impediva al pulsante **Restart message preparation** di riprendere la consegna dopo la risoluzione di un errore nel flusso di lavoro. (NEO-13488)
* È stato risolto un problema che poteva causare un errore nelle consegne in modalità mid-sourcing durante la fase di aumento, in cui il target includeva destinatari con formati e-mail giapponesi. (NEO-23846)
* È stato risolto un problema di conversione del fuso orario con il connettore Snowflake (NEO-20105)
* È stato risolto un problema con gli account esterni che utilizzavano FTP su SSL. (NEO-20498)
* È stato risolto un problema che poteva impedire la visualizzazione delle immagini nelle consegne Line. (NEO-23207)
* È stato risolto un problema che causava un errore durante la pubblicazione di un’offerta. (NEO-23312)
* È stato risolto un problema con le notifiche push che consentiva il funzionamento delle connessioni di prova nelle app mobili, anche quando il certificato era scaduto. (NEO-22991)
* È stato risolto un problema che poteva interessare le notifiche push quando inviate con un’elevata frequenza. (NEO-20516)
* È stato risolto un problema che causava l’inclusione di duplicati nei dati di tracking anche se i log di tracking non ne includevano. (NEO-20040)
* È stato risolto un problema che causava l’invio di e-mail transazionali duplicate dopo la risoluzione di un errore di comunicazione del server di tracking. (NEO-23640)
* È stato risolto un problema che eliminava il valore del parametro di codifica durante il reindirizzamento da un URL di tracciamento (impatto sui caratteri giapponesi). (NEO-25637)
* È stato risolto un problema che poteva impedire il funzionamento di una query durante il confronto di numeri in virgola mobile. (NEO-23243)
* È stato risolto un problema che poteva impedire la visualizzazione del contenuto della colonna **Modified by** dopo il riavvio di un flusso di lavoro. (NEO-23035)
* È stato risolto un problema che causava un errore nel flusso di lavoro tecnico di tracking durante il download dei log da un secondo contenitore. (NEO-23159)
* È stato risolto un problema che poteva causare un errore dei flussi di lavoro durante l’esecuzione di un’attività **Enrichment**. (NEO-17338)
* È stato aggiunto un controllo al campo **Doubles to keep** nell’attività del flusso di lavoro **Deduplicazione** per impedire l’inserimento di valori nulli o negativi.
* La **procedura guidata di pianificazione** è stata rimossa dalle campagne ricorrenti per evitare di citare ore e minuti. Vengono prese in considerazione solo le date.
* È stato risolto un problema relativo ai campi di archiviazione aggiuntivi durante la creazione di consegne tramite l’opzione **Computed by a script** nell’attività del flusso di lavoro **Script**. (NEO-20609)
* È stato risolto un problema che impediva l’eliminazione dei flussi di lavoro fantasma nelle attività di pulizia del database.
* È stato risolto un problema che causava un errore del flusso di lavoro tecnico di **fatturazione (profili attivi)**. (NEO-19777)
* È stato risolto un problema di regressione quando si utilizzava la funzione di connettore ACS che impediva la connessione a un&#39;istanza Campaign Standard (gestione errata della connessione FOH/FOH2). (NEO-23433)
* È stato risolto un problema che impediva la creazione di un’estensione dello schema su una chiave primaria con più colonne con una tabella Hadoop. (NEO-17390)
* È stato risolto un problema nell’attività **Loading (SOAP)** che poteva impedire il caricamento di file WSDL da un URL. (NEO-16924)
* È stato risolto un problema che impediva l’esecuzione di un **arresto incondizionato** tramite la console in caso di bilanciamento del carico di più server del flusso di lavoro attivi. (NEO-19556)
* È stato risolto un problema di regressione che causava l’arresto anomalo del flusso di lavoro di pulizia.
* È stato risolto un problema che poteva verificarsi durante la pubblicazione di un modello in un’istanza di esecuzione.
* È stato risolto un problema che poteva impedire l’esecuzione del flusso di lavoro tecnico collectPrivacyRequests. (NEO-20513, NEO-25169)
* Sono stati risolti dei problemi che potevano verificarsi quando si tentava di collegarsi a Audience Manager dopo l’aggiornamento alla build 9080. (NEO-20511, NEO-25167)
* Sono stati risolti dei problemi che potevano verificarsi durante l’esportazione di report in formato PDF o XLS. (NEO-20982, NEO-23493, NEO-23348)
* È stato risolto un problema che poteva far sì che una consegna fosse visualizzata due volte nell’elenco di consegna dopo l’invio.
* È stato risolto un problema relativo alla preparazione delle consegne che poteva verificarsi quando la configurazione dell’indirizzamento era impostata per inviare la consegna tramite mid-sourcing.
* È stato risolto un problema che poteva visualizzare un messaggio di errore quando si faceva clic su un collegamento di un’applicazione web all’interno di un messaggio Line.
* È stato risolto un problema che eliminava la cronologia dell’attività **Incremental query** dopo l’esecuzione del flusso di lavoro di pulizia.
* È stato risolto un problema che si verificava durante la creazione di un account esterno di mid-sourcing a causa del quale l’opzione NmsMidSourcing_LastBroadLog_&lt;InternalName> risultava mancante.
* È stato risolto un problema di regressione della connessione al database che causava il riavvio costante del server Web a causa di un problema di codifica del database. Ciò potrebbe portare ad un consumo eccessivo. (NEO-23264)
