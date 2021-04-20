---
solution: Campaign Classic
product: campaign
title: Note sulla versione 18.10 di Campaign
description: Note sulla versione per Campaign 18.10
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: 57996f77-4ac2-402a-95db-b75d4bea4eeb
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '2372'
ht-degree: 7%

---

# Versione 18.10{#release-18-10}

## Versione 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 luglio 2019

**Miglioramenti**

* È ora possibile eliminare i record fittizi creati in Microsoft Dynamics durante il flusso di lavoro di importazione.
* È stato risolto un problema relativo all’attività del flusso di lavoro Raccolta file che poteva registrare gli errori in loop quando l’accesso a un file veniva negato. (NEO-12085)
* È stato risolto un problema che causava discrepanze nella generazione di rapporti tra le attività degli utenti e i rapporti di tracciamento per l’indicatore di consegna aperta. (NEO-11742)
* Sono state migliorate le autorizzazioni per eseguire il pacchetto della zona di sicurezza quando si utilizza un account interno.
* È stato risolto un problema che poteva causare errori nei log figlio master. (NEO-8978)

## Versione 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 aprile 2019

**Miglioramenti**

* È stato risolto un problema relativo al blocco critico SQL che causava un errore di analisi della consegna in caso di analisi/invio simultanei (quando due consegne venivano analizzate contemporaneamente). (NEO-13026)
* È stato rimosso il limite di 10.000 record in Workflow Heatmap per risolvere un problema di dati mancanti. (NEO-12329)
* È stato risolto un problema che si verificava con l’opzione &quot;Conserva tutti i dati aggiuntivi dal set principale&quot; in un’attività del flusso di lavoro di arricchimento. (NEO-13291)

## Versione 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 aprile 2019

**Miglioramenti**

* È stato risolto un problema relativo al processo di elaborazione degli indicatori di tracciamento per i messaggi transazionali. (NEO-12529, NEO-12581)
* È stato risolto un problema relativo all’API HTTPRequest che non aspettava il completamento di tutti i callback. (NEO-12628)
* Sono stati aggiunti indici nelle tabelle temporanee del coupon per ottimizzare l’invio della consegna. (NEO-12437)
* È stato risolto un problema che si verificava durante l’analisi di un messaggio con targeting dei destinatari per i domini giapponesi (.JP). (NEO-12246)
* Nell’integrazione di Analytics, è ora consentito il recupero di dati AAM segmento con carattere %. (NEO-12025)
* È stato risolto un problema di arresto anomalo Tomcat che si verificava durante l’invio di notifiche push tramite HTTP2. (NEO-12701)

## Versione 18.10.3 - Build 8981{#release-18-10-3-build-8981}

29 gennaio 2019

>[!CAUTION]
>
>Questa build è stata richiamata. [effettuare l&#39;aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contattare [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Miglioramenti**

* È stato risolto un problema relativo all’attività del flusso di lavoro s3 File Transfer . (NEO-12473)
* È stato risolto un problema del flusso di lavoro di tracciamento che poteva non riuscire. (NEO-12520)
* È stato risolto un problema relativo all’accesso IMS.
* È stato risolto un problema relativo all’approvazione dell’anteprima e del contenuto nei messaggi transazionali quando si utilizzava un ID offerta di grandi dimensioni.
* È stato risolto un problema relativo al flusso di lavoro Mid-sourcing (contatori di consegna).
* È stato risolto un problema relativo all&#39;aggiornamento della struttura del database a causa del quale venivano rilasciati nuovi indici su NmsRecipient.
* È stato corretto un arresto anomalo della console che poteva verificarsi quando si utilizzava l’opzione Definito in un file esterno per la destinazione principale di una consegna. (NEO-12349)
* Sono stati corretti diversi arresti anomali di InMail.
* È stato risolto un problema che si verificava durante l’utilizzo di un’attività Aggiorna flusso di lavoro dati per eliminare i record memorizzati in un database FDA Teradata.
* Sono stati risolti i problemi di incoerenza nella gestione delle chiavi segrete.
* È stato risolto un problema relativo all’attività Arricchimento durante la digitazione di un campo come: xml=true e calculate=true
* È stato risolto un problema di escape del carattere durante l’invio di notifiche push su un’app mobile.
* È stato risolto un problema che impediva il passaggio da FDA al metodo di sincronizzazione SOAP in un account esterno di mid-Sourcing.

## Versione 18.10.2 - Build 8978{#release-18-10-2-build-8978}

6 dicembre 2018

>[!CAUTION]
>
>Questa build è stata richiamata. [effettuare l&#39;aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contattare [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Miglioramenti**

* Sono stati risolti diversi problemi durante l’esecuzione di flussi di lavoro tramite MySQL su FDA. (NEO-11652)
* È stato risolto un problema di prestazioni durante l’invio di notifiche push. (NEO-11787)
* È stato risolto un problema di esaurimento ID quando si utilizzavano gli indirizzi di seed in una consegna. (NEO-11842)
* È stato risolto un problema di blocco del client che poteva verificarsi durante l’utilizzo di flussi di lavoro complessi. (NEO-11847)
* È stato risolto un problema di visualizzazione che si verificava quando si utilizzava una distribuzione di valori con un collegamento 1:N. (NEO-11820)
* È stato corretto un errore di Oracle in Workflow Heatmap.
* È stato risolto un problema corretto quando si aggiungeva una proposta di offerta in un’attività di arricchimento.
* È stato risolto un problema di connessione di gestione dati SQL.
* È stato risolto un problema relativo alla generazione di nomi di tabella del flusso di lavoro temporaneo in caso di ID negativi.
* È stato risolto un problema relativo al calcolo delle durate del flusso di lavoro in Workflow HeatMap.


## Versione 18.10 - Build 8977{#release-18-10-build-8977}

5 novembre 2018

>[!CAUTION]
>
>Questa build è stata richiamata. [effettuare l&#39;aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contattare [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Novità**

<table> 
 <thead> 
  <tr> 
   <th> Funzionalità<br /> </th> 
   <th> Descrizione<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Miglioramenti delle notifiche push<br /> </td> 
   <td> Sono stati implementati diversi miglioramenti per le notifiche push in Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Tracciare le notifiche silenziose in iOS </p> </li> 
     <li> <p>Implementazione del feedback sulle chiamate di registrazione in iOS</p> </li> 
     <li> <p>Migliorare la velocità di preparazione delle consegne iOS</p> </li> 
    </ul> <p>Come parte del deprezzamento del GCM da parte di Google, il connettore Android V2 ora permette connessioni solo al server FCM.</p><p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentazione dettagliata</a>. L'aggiornamento manuale a FCM è descritto in questo <a href="https://helpx.adobe.com/it/campaign/kb/migrate-to-fcm.html">articolo</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> Attività di gestione dati SQL<br /> </td> 
   <td> <p>È stata aggiunta una nuova attività del flusso di lavoro di gestione dati. L'attività <strong>SQL Data Management</strong> consente di scrivere o copiare-incollare i propri script SQL per creare e popolare tabelle di lavoro (solo FDA). </p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/sql-data-management.md">documentazione dettagliata</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Monitoraggio del flusso di lavoro<br /> </td> 
   <td> <p>Con la nuova Adobe Campaign Workflow HeatMap, gli amministratori della piattaforma dispongono di una rapida rappresentazione grafica di tutti i flussi di lavoro simultanei, che consente loro di monitorare il carico sull’istanza e pianificare i flussi di lavoro di conseguenza.</p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/heatmap.md">documentazione dettagliata</a>.</p> <p>Il pacchetto Workflow HeatMap è disponibile anche su richiesta per le build precedenti alla 8977 (a partire dalla build 8700). Per ulteriori informazioni sulla richiesta e l'installazione, consulta <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">questa pagina</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* È stato risolto un problema di sicurezza che poteva causare vulnerabilità agli attacchi SSRF (Server Side Request Forgery) e attacchi di negazione del servizio (DoS). (NEO-11453)
* Contenuto (reindirizzamento di tracciamento, pagine mirror, sondaggi, ecc.) verrà ora servito da Campaign con il tag X-Robots: intestazione nocache. Questo impedisce l’indicizzazione di questo contenuto da parte dei motori di ricerca Internet. (NEO-11101)
* È stato risolto un problema di iniezione XTK nell’API di abbonamento (nms:subscription:Unsubscription e nms:subscription:Subscribe).
* È stato risolto un problema di iniezione XTK nell’applicazione Web di annullamento dell’abbonamento.
* Sono state rimosse le password che erano visualizzate in modo non corretto in alcuni registri SMS.

**Miglioramenti**

* Le API di Campaign Classic sono ora disponibili in una [pagina dedicata](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html). Se stavi utilizzando il file jsapi.chm, ora devi fare riferimento alla nuova versione online.
* PostgreSQL 10, Debian 9 e Teradata 16.20 sono ora supportati. Consulta la [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html).
* Quando crei una connessione SFTP, ora puoi utilizzare l’autenticazione proxy. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../installation/using/file-res-management.md) (NEO-9868)
* L’opzione **Formula di calcolo della data** è ora disponibile nelle proprietà di consegna quando crei una singola consegna utilizzando il modello di consegna della direct mailing. (NEO-9792)
* La gestione dei nomi di dominio è stata migliorata per il tracciamento dei cookie e le applicazioni web. Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot;.
* L’importazione di risorse condivise Adobe Marketing Cloud in una consegna o in una pagina di destinazione è stata migliorata in termini di sicurezza e prestazioni.
* Una nuova casella di controllo è disponibile nell&#39;account esterno del canale mobile per abilitare tracce SMPP dettagliate nel file di registro, che rende questo output direttamente accessibile dall&#39;interfaccia Adobe Campaign.
* Nei registri di trasmissione, esiste ora una distinzione tra il numero massimo di connessioni e il numero massimo di messaggi all’ora. Una volta raggiunti i limiti, è possibile sapere perché la velocità effettiva è limitata. Precedentemente, lo stesso messaggio (&quot;quota soddisfatta&quot;) si applicava a entrambi i casi.
* È ora possibile specificare uno script SQL da eseguire quando si acquisisce una connessione dal pool. Questo script può essere utilizzato per impostare lo schema predefinito. Questo script verrà applicato dopo il binding della query. (NEO-11256)
* L’SDK di Campaign non memorizza più l’ID utente per conformarsi alle nostre normative PII. I dati vengono ora memorizzati come hash.
* Durante l’importazione di un file XML di esportazione del pacchetto, Campaign ora supporta la presenza di BOM nel file, anche se la codifica è dichiarata esplicitamente in esso.

**Evoluzioni tecniche**

Aggiornamento client e server

>[!CAUTION]
>
>Se disponi di un server aggiornato alla versione 18.10, per accedere al server dovrai utilizzare un client 18.10. Il client 18.10 sarà in grado di connettersi a una versione precedente del server.

Gestione dei nomi di dominio

La gestione dei nomi di dominio è stata migliorata per il tracciamento dei cookie e le applicazioni web.

Ora, tutti i nomi di dominio di secondo livello a due lettere sono supportati per impostazione predefinita (ad esempio, .aa.com). Per nomi di dominio più complessi (ad esempio domini di secondo livello a tre lettere come .com.au), devi aggiungerli nell&#39;opzione **cookieDomains** del serverConf (sotto il tag di reindirizzamento). Ecco un esempio:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Miglioramenti dell’indice

Gli indici su NmsRecipient sono stati rielaborati. Ciò dovrebbe migliorare le prestazioni sulle query che utilizzano questa tabella. Se hai eseguito un&#39;estensione di NmsRecipient, potresti voler verificare di non avere indici che duplicano i nuovi indici (per ridurre l&#39;utilizzo di spazio sul server di database). (NEO-8228)

Su PostgreSql quando si utilizza un confronto UTF-8, è ora possibile creare indici che ottimizzano le operazioni &quot;LIKE &#39;string%&#39;&quot; (o &quot;inizia con&quot;). Se esegui altre operazioni sulla stessa colonna (ad esempio, ordinando per o unisciti), sarà necessario un altro indice standard. Sul lato dello schema, questo verrà fatto aggiungendo indexOption=&quot;searchFromStart&quot; nella definizione dell&#39;indice (creerà un indice varchar_pattern_ops invece di un indice della struttura standard). Ad esempio (su NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Sono stati aggiunti nuovi indici a NmsRtEvent e NmsEventHisto (nella colonna &quot;Pianificato&quot;), per migliorare il tempo di visualizzazione sul modulo corrispondente (NEO-11738).

Queste modifiche dell&#39;indice possono comportare un aumento del tempo necessario per eseguire il post-aggiornamento.

**Patch**

* È stato corretto un errore che impediva il download dei file dall&#39;attività del flusso di lavoro **Download Web** . (NEO-11105)
* È stato corretto un errore che talvolta lasciava il flusso di lavoro **Invio di indicatori e attributi della campagna** in uno stato Non riuscito (NEO-10820).
* È stato risolto un problema che eliminava l’elenco dei destinatari creato dopo l’esecuzione dell’attività di aggiornamento Elenco in un flusso di lavoro. (NEO-11696)
* È stato risolto un problema che visualizzava in modo errato le campagne un mese prima nel calendario Campaign (su un’istanza giapponese). (NEO-11445)
* È stato risolto un problema che impediva la visualizzazione della configurazione di Analytics nella scheda Analisi web delle proprietà della consegna. (NEO-11619)
* È stato corretto un errore che veniva visualizzato quando si tentava di modificare e salvare il modulo di input nms:delivery . (NEO-10973)
* È stato risolto un problema di configurazione dell’account esterno che si verificava durante l’esecuzione di un flusso di lavoro contenente un’attività di trasferimento file . (NEO-11012)
* È stato risolto un problema che restituiva righe vuote quando si utilizzava la funzione zcat per caricare i file nell’attività di caricamento dei dati. (NEO-11273)
* È stato risolto un problema che generava registri ampi duplicati durante l’analisi della consegna. (NEO-11360)
* È stato risolto un problema che causava un errore di consegna a causa di una chiave di collegamento esterna mancante dopo l’esecuzione dell’attività Enrichment in un flusso di lavoro. (NEO-11537)
* È stato risolto un problema che impediva la corretta disinstallazione o riparazione di Adobe Campaign quando il percorso di installazione includeva caratteri cinesi GB18030 specifici.
* È stato risolto un problema che collegava alcuni registri di tracciamento alla consegna errata. (NEO-11412)
* È stato risolto un problema che poteva causare la permanenza di alcune parti dei registri di consegna con stato in sospeso per un periodo più lungo del previsto. (NEO-11336)
* È stato corretto un errore che si verificava durante la modifica di una query per aggiungere un coupon a una consegna. (NEO-11037)
* È stato risolto un problema nei rapporti a causa del quale i grafici calcolavano sempre la somma dei valori indipendentemente dall’operatore aggregato selezionato. (NEO-10913)
* Poiché la funzione &quot;request.schema&quot; è obsoleta, è stata rimossa dalla documentazione JSAPI. (NEO-10828)
* È stato risolto un problema che impediva ad alcuni utenti con configurazioni di fuso orario specifiche di accedere ad Adobe Campaign. (NEO-10712)
* È stato risolto un problema che si verificava durante la configurazione di un account esterno di canale mobile utilizzando il connettore SMPP generico esteso: se si specificava l&#39;utilizzo di parametri diversi per il ricevitore, il trasmettitore utilizzava erroneamente tali parametri invece dei propri parametri.
* È stato risolto un problema che causava un errore delle consegne programmate durante l’impostazione di una frequenza per la regola di pressione, perché le consegne venivano costantemente ricalcolate dopo il primo arbitrato. (NEO-10016)
* È stato risolto un problema che causava l&#39;arresto anomalo del server Web IIS durante il processo di riciclo del pool di applicazioni (nella libreria nlsrvmod.dll). (NEO-10862)
* È stato risolto un problema che poteva impedire la ricerca di un destinatario nella schermata **Profili e Target** . (NEO-8228)
* È stato risolto un problema che poteva causare un errore di timeout durante l’accesso alla cartella Cronologia eventi in caso di un numero elevato di record. (NEO-11738)
* È stato risolto un problema che poteva causare la restituzione errata dei destinatari della consegna LINE come &quot;Non raggiungibile&quot;. (NEO-10833)
* È stato risolto un problema che si verificava durante l’esecuzione di una query del flusso di lavoro con una colonna aggiuntiva all’Oracle. (NEO-11615)
* È stato apportato un miglioramento per garantire che le connessioni chiuse non vengano mantenute nel pool di connessioni per troppo tempo. (NEO-11392)
* È stato risolto un problema che si verificava durante l’utilizzo di un’attività del flusso di lavoro di targeting (query, caricamento dati (RDBMS), ecc.) collegato tramite FDA a una tabella di Oracle esterna contenente caratteri UTF8 (nel nome della tabella, nel nome del campo, ecc.) e che conteneva anche un vincolo di chiave primaria con un nome di vincolo predefinito generato dal sistema. (NEO-10714)
* È stato risolto un problema che poteva impedire l’eliminazione del contenuto HTML di una consegna. (NEO-11327)
* È stato risolto un problema relativo all’anteprima dei file XML e CSV in una direct mailing dopo l’esecuzione di una campagna. (NEO-11290)
* È stato risolto un problema che si verificava durante l’ordinamento dei dati in un’attività del flusso di lavoro di arricchimento. (NEO-11394)
* È stato risolto un problema che si verificava durante l’ordinamento dei dati in un rapporto personalizzato. (NEO-10896)
* È stato risolto un problema che causava errori durante l&#39;utilizzo dell&#39;impostazione useVault con Teradata. (NEO-11399)
* È stato risolto un problema che causava l’arresto anomalo della console client di Adobe Campaign durante l’eliminazione di più righe di query. (NEO-10744)
* È stato risolto un problema che impediva l’applicazione di regole di pressione in alcuni casi durante la consegna della direct mailing. (NEO-9004)
* È stato risolto un problema che si verificava durante l’utilizzo dell’attività Caricamento dati per importare una colonna con il tipo di dati &quot;time&quot;: il separatore di tempo viene reimpostato anche dopo la rimozione. (NEO-10743)
* È stato risolto un problema che impediva la visualizzazione della cartella Consegne dall’elenco Cartelle di esecuzione nelle proprietà Consegna durante la modifica di una consegna ricorrente. (NEO-11094)
* È stato risolto un problema che impediva alla finestra Visualizza popolazione di visualizzare più di 200 record come destinazione risultante di un’attività Query in un flusso di lavoro. (NEO-11195)
* È stato risolto un problema in Oracle che impediva l’esecuzione di una query DELETE con più di 1000 elementi selezionati. (NEO-11171)
* È stato risolto un problema che portava a codificare gli URL come URL tracciati nei parametri aggiuntivi di una consegna di notifiche push Android. (NEO-11468)
* È stato corretto un errore di script che si verificava nel report Attività utente quando i parametri venivano impostati su &quot;Intervalli di un giorno&quot; e &quot;Aperture&quot;. (NEO-11655)
* È stato risolto un problema che si verificava durante la connessione al server di mid-sourcing o al Centro messaggi tramite un proxy web autenticato. (NEO-11309)
* È stato corretto un errore di Oracle che si verificava quando si salvava una nuova composizione di consegna dopo aver selezionato un elemento di uno schema specifico **in base a una visualizzazione SQL**. (NEO-11682)
* È stato risolto un problema che causava la generazione di file di rifiuto contenenti falsi positivi durante l’elaborazione di un file zip contenente un .csv tramite un’attività di caricamento file tramite l’opzione Decompression.
* xtkjoblog viene eliminato dalla pulizia.
