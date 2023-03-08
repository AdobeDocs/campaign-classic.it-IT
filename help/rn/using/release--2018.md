---
product: campaign
title: Versioni di Campaign Classic 2018
description: Ulteriori informazioni sulle versioni di Campaign Classic 2018
hidefromtoc: true
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: c929557ee9f5467f9c3b8eb1ed25fae5399820ba
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 8%

---

# Versioni 2018{#release-2018}

![](../../assets/v7-only.svg)

## Versione 18.10

### Versione 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 luglio 2019

**Miglioramenti**

* È ora possibile eliminare i record fittizi creati in Microsoft Dynamics durante il flusso di lavoro di importazione.
* È stato risolto un problema relativo all’attività del flusso di lavoro Raccolta file che poteva registrare errori in loop quando l’accesso a un file veniva negato. (NEO-12085)
* È stato risolto un problema che causava discrepanze nella generazione di rapporti tra le attività degli utenti e i rapporti di tracciamento per l’indicatore di consegna aperto. (NEO-11742)
* Sono state migliorate le autorizzazioni per eseguire il pacchetto dell’area di sicurezza quando si utilizza un account interno.
* È stato risolto un problema che poteva causare errori nei registri matchild. (NEO-8978)

### Versione 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 aprile 2019

**Miglioramenti**

* È stato risolto un problema di deadlock SQL che causava un errore di analisi della consegna in caso di analisi/invio simultanei (quando due consegne venivano analizzate contemporaneamente). (NEO-13026)
* È stato rimosso il limite di 10.000 record nella Workflow Heatmap per risolvere un problema di dati mancante. (NEO-12329)
* È stato risolto un problema che si verificava con l’utilizzo dell’opzione &quot;Mantieni tutti i dati aggiuntivi dal set principale&quot; in un’attività del flusso di lavoro di arricchimento. (NEO-13291)

### Versione 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 aprile 2019

**Miglioramenti**

* È stato risolto un problema relativo al processo di elaborazione degli indicatori di tracciamento per i messaggi transazionali. (NEO-12529, NEO-12581)
* È stato risolto un problema relativo all’API HTTPRequest che non attendeva il completamento di tutti i callback. (NEO-12628)
* Sono stati aggiunti indici nelle tabelle temporanee dei coupon per ottimizzare l’invio della consegna. (NEO-12437)
* È stato risolto un problema che si verificava durante l’analisi di un messaggio per i destinatari dei domini giapponesi (.JP). (NEO-12246)
* Nell’integrazione di Analytics, ora è consentito il recupero di dati di segmenti AAM con il carattere %. (NEO-12025)
* È stato risolto un problema di arresto anomalo di Tomcat durante l’invio di notifiche push tramite HTTP2. (NEO-12701)

### Versione 18.10.3 - Build 8981{#release-18-10-3-build-8981}

29 gennaio 2019

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [eseguire l’aggiornamento alla build più recente](../../production/using/build-upgrade.md)  o contatto [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Miglioramenti**

* È stato risolto un problema relativo all’attività del flusso di lavoro s3 File Transfer. (NEO-12473)
* È stato risolto un problema relativo al flusso di lavoro di tracciamento che poteva non riuscire. (NEO-12520)
* È stato risolto un problema con l’accesso IMS.
* È stato risolto un problema relativo all’anteprima e all’approvazione del contenuto nella messaggistica transazionale quando si utilizzava un ID offerta di grandi dimensioni.
* È stato risolto un problema relativo al flusso di lavoro Mid-sourcing (contatori di consegna).
* È stato risolto un problema con l’aggiornamento della struttura del database a causa del quale venivano eliminati nuovi indici su NmsRecipient.
* È stato risolto un arresto anomalo della console che poteva verificarsi utilizzando l’opzione Definito in un file esterno per il target principale di una consegna. (NEO-12349)
* Sono stati corretti diversi arresti anomali di InMail.
* È stato risolto un problema che si verificava durante l’utilizzo di un’attività del flusso di lavoro Update data (Aggiorna dati) per eliminare i record memorizzati in un database di Teradate FDA.
* Sono stati risolti i problemi di incoerenza nella gestione segreta delle chiavi.
* È stato risolto un problema relativo all’attività Enrichment che si verificava durante la digitazione di un campo come: xml=true and calculated=true
* È stato risolto un problema di escape carattere che si verificava durante l’invio di notifiche push su un’app mobile.
* È stato risolto un problema che impediva il passaggio dal metodo di sincronizzazione FDA al metodo di sincronizzazione SOAP in un account esterno Mid-Sourcing.

### Versione 18.10.2 - Build 8978{#release-18-10-2-build-8978}

6 dicembre 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [eseguire l’aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatto [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Miglioramenti**

* Sono stati risolti diversi problemi che si verificavano durante l’esecuzione di flussi di lavoro tramite MySQL su FDA. (NEO-11652)
* È stato risolto un problema di prestazioni che si verificava durante l’invio di notifiche push. (NEO-11787)
* È stato risolto un problema di esaurimento ID che si verificava con l’utilizzo di indirizzi di seed in una consegna. (NEO-11842)
* È stato risolto un problema di blocco del client che poteva verificarsi durante l’utilizzo di flussi di lavoro complessi. (NEO-11847)
* È stato risolto un problema di visualizzazione che si verificava con l’utilizzo di una distribuzione di valori con un collegamento 1:N. (NEO-11820)
* È stato corretto un errore di Oracle in Workflow Heatmap.
* È stato risolto un problema corretto che si verificava con l’aggiunta di una proposta di offerta in un’attività di arricchimento.
* È stato risolto un problema di connessione di gestione dati SQL.
* È stato risolto un problema nella generazione di nomi di tabelle del flusso di lavoro temporanee in caso di ID negativi.
* È stato risolto un problema relativo al calcolo delle durate del flusso di lavoro in Workflow HeatMap.


### Versione 18.10.1 - Build 8977{#release-18-10-build-8977}

5 novembre 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [eseguire l’aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatto [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
     <li> <p>Tracciare le notifiche in background in iOS </p> </li> 
     <li> <p>Implementare il feedback sulle chiamate di registrazione in iOS</p> </li> 
     <li> <p>Migliorare la velocità di preparazione delle consegne in iOS</p> </li> 
    </ul> <p>Come parte del deprezzamento del GCM da parte di Google, il connettore Android V2 ora consente connessioni solo al server FCM.</p><p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentazione dettagliata</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Attività di gestione dati SQL<br /> </td> 
   <td> <p>È stata aggiunta una nuova attività del flusso di lavoro di gestione dati. Il <strong>Gestione dati SQL</strong> L'attività consente di scrivere o copiare e incollare script SQL personalizzati per creare e popolare tabelle di lavoro (solo FDA). </p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/sql-data-management.md">documentazione dettagliata</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Monitoraggio del flusso di lavoro<br /> </td> 
   <td> <p>Con la nuova Adobe Campaign Workflow HeatMap, gli amministratori della piattaforma dispongono di una rappresentazione grafica rapida di tutti i flussi di lavoro simultanei, che consente loro di monitorare il carico sull’istanza e pianificare i flussi di lavoro di conseguenza.</p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/heatmap.md">documentazione dettagliata</a>.</p> <p>Il pacchetto Workflow HeatMap è disponibile anche su richiesta per le build precedenti alla 8977 (a partire dalla build 8700). Per ulteriori informazioni sulla richiesta e l’installazione di, consulta <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">questa pagina</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* È stato risolto un problema di sicurezza che poteva causare vulnerabilità ad attacchi SSRF (Server Side Request Forgery) e attacchi DoS (Denial of Service). (NEO-11453)
* Contenuto (reindirizzamento del tracciamento, pagine mirror, sondaggi, ecc.) ora Campaign utilizza l’intestazione X-Robots-Tag: nocache. Questo impedisce l’indicizzazione di questo contenuto da parte dei motori di ricerca Internet. (NEO-11101)
* È stato risolto un problema di iniezione XTK nell’API di abbonamento (nms):subscription:Annulla iscrizione e nms:subscription:Abbonati).
* È stato risolto un problema di iniezione XTK nell’applicazione web per l’annullamento dell’abbonamento.
* Sono state rimosse le password che venivano visualizzate in modo insicuro in alcuni registri SMS.

**Miglioramenti**

* Le API di Campaign Classic sono ora disponibili in una [pagina dedicata](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it). Se stavi utilizzando il file jsapi.chm, ora devi fare riferimento alla nuova versione online.
* Sono ora supportati PostgreSQL 10, Debian 9 e Teradata 16.20. Consulta la [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html).
* Durante la creazione di una connessione SFTP, ora puoi utilizzare l’autenticazione proxy. Per ulteriori informazioni, consulta [documentazione dettagliata](../../installation/using/file-res-management.md) (NEO-9868)
* Il **Formula di calcolo della data** L’opzione è ora disponibile nelle proprietà di consegna quando si crea una singola consegna utilizzando il modello di consegna direct mailing. (NEO-9792)
* La gestione dei nomi di dominio è stata migliorata per il tracciamento dei cookie e le applicazioni web. Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot; di seguito.
* L’importazione di risorse condivise Adobe Marketing Cloud in una consegna o pagina di destinazione è stata migliorata in termini di sicurezza e prestazioni.
* Una nuova casella di controllo è disponibile nell’account esterno del canale mobile per abilitare le tracce SMPP dettagliate nel file di registro, rendendo questo output direttamente accessibile dall’interfaccia di Adobe Campaign.
* Nei broadlog esiste ora una distinzione tra il numero massimo di connessioni e il numero massimo di messaggi all&#39;ora. Una volta raggiunti i limiti, è possibile comprendere perché il throughput è limitato. In precedenza, lo stesso messaggio (&quot;quota soddisfatta&quot;) si applicava a entrambi i casi.
* È ora possibile specificare uno script SQL da eseguire durante l&#39;acquisizione di una connessione dal pool. Questo script può essere utilizzato per impostare lo schema predefinito. Questo script verrà applicato dopo l’esecuzione della query banding. (NEO-11256)
* L’SDK di Campaign non memorizza più l’ID utente in modo da rispettare le normative PII. I dati vengono ora memorizzati come hash.
* Durante l’importazione di un file XML di esportazione del pacchetto, Campaign ora supporta la presenza di DBA nel file, anche se la codifica è dichiarata in modo esplicito al suo interno.

**Evoluzioni tecniche**

Aggiornamento client e server

>[!CAUTION]
>
>Se si dispone di un server che è stato aggiornato alla versione 18.10, sarà necessario utilizzare un client 18.10 per accedere al server. Il client 18.10 sarà in grado di connettersi a una versione server precedente.

Gestione dei nomi di dominio

La gestione dei nomi di dominio è stata migliorata per il tracciamento dei cookie e le applicazioni web.

Ora, tutti i nomi di dominio di secondo livello a due lettere sono supportati per impostazione predefinita (ad esempio .aa.com). Per i nomi di dominio più complessi (ad esempio domini di secondo livello a tre lettere come .com.au), è necessario aggiungerli nel **cookieDomains** dell’opzione serverConf (sotto il tag di reindirizzamento). Ecco un esempio:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Miglioramenti dell’indice

Gli indici su NmsRecipient sono stati rielaborati. Questo dovrebbe migliorare le prestazioni sulle query che utilizzano questa tabella. Se è stata eseguita un&#39;estensione di NmsRecipient, è possibile verificare che non siano presenti indici che duplicano i nuovi indici, in modo da ridurre al minimo l&#39;utilizzo di spazio sul server del database. (NEO-8228)

In PostgreSql quando si utilizzano regole di confronto UTF-8, ora è possibile creare indici che ottimizzano le operazioni &quot;LIKE &#39;string%&#39;&quot; (o &quot;starts with&quot;). Se esegui altre operazioni sulla stessa colonna (ad esempio ordina per o unisci), sarà necessario un altro indice standard. Sul lato schema, questo verrà fatto aggiungendo indexOption=&quot;searchFromStart&quot; nella definizione dell’indice (creerà un indice varchar_pattern_ops invece di un indice ad albero standard). Ad esempio (su NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Sono stati aggiunti nuovi indici a NmsRtEvent e NmsEventHisto (nella colonna &quot;Pianificato&quot;), per migliorare il tempo di visualizzazione nel modulo corrispondente (NEO-11738).

Queste modifiche dell’indice possono comportare un aumento del tempo necessario per eseguire il post-aggiornamento.

**Patch**

* È stato corretto un errore che impediva l’accesso ai file da **Download web** l’attività del flusso di lavoro non venga scaricata. (NEO-11105)
* È stato corretto un errore che occasionalmente causava la **Invio di indicatori e attributi della campagna** workflow in stato Non riuscito (NEO-10820).
* È stato risolto un problema che eliminava l’elenco dei destinatari creato dopo l’esecuzione dell’attività di aggiornamento elenco in un flusso di lavoro. (NEO-11696)
* È stato risolto un problema che causava la visualizzazione errata delle campagne un mese prima nel calendario Campaign (in un’istanza giapponese). (NEO-11445)
* È stato risolto un problema che impediva la visualizzazione della configurazione di Analytics nella scheda Web Analytics delle Proprietà di consegna. (NEO-11619)
* È stato corretto un errore visualizzato durante il tentativo di modificare e salvare il modulo di input nms:delivery. (NEO-10973)
* È stato risolto un problema di configurazione dell’account esterno che si verificava durante l’esecuzione di un flusso di lavoro contenente un’attività File transfer. (NEO-11012)
* È stato risolto un problema che restituiva righe vuote quando si utilizzava la funzione zcat per caricare i file nell’attività di caricamento dei dati. (NEO-11273)
* È stato risolto un problema che generava registri ampi duplicati durante l’analisi della consegna. (NEO-11360)
* È stato risolto un problema che causava un errore nella consegna a causa della mancanza della chiave del collegamento esterno dopo l’esecuzione dell’attività Enrichment in un flusso di lavoro. (NEO-11537)
* È stato risolto un problema che impediva la corretta disinstallazione o ripristino di Adobe Campaign quando il percorso di installazione includeva caratteri specifici GB18030 cinesi.
* È stato risolto un problema che collegava alcuni registri di tracciamento alla consegna errata. (NEO-11412)
* È stato risolto un problema che poteva causare la permanenza di alcune parti dei registri di consegna con lo stato in sospeso più a lungo del previsto. (NEO-11336)
* È stato corretto un errore che si verificava durante la modifica di una query per aggiungere un coupon a una consegna. (NEO-11037)
* È stato risolto un problema nei rapporti a causa del quale i grafici calcolavano sempre la somma dei valori indipendentemente dall’operatore aggregato selezionato. (NEO-10913)
* Poiché la funzione &quot;request.scheme&quot; è obsoleta, è stata rimossa dalla documentazione JSAPI. (NEO-10828)
* È stato risolto un problema che impediva ad alcuni utenti con configurazioni specifiche del fuso orario di accedere ad Adobe Campaign. (NEO-10712)
* È stato risolto un problema che si verificava durante la configurazione di un account esterno del canale mobile utilizzando il connettore SMPP generico esteso: se si specificavano parametri diversi per il ricevitore, il trasmettitore utilizzava erroneamente tali parametri al posto dei propri.
* È stato risolto un problema che causava un errore nelle consegne pianificate durante l’impostazione di una frequenza per la regola di pressione, perché le consegne venivano costantemente ricalcolate dopo il primo arbitrato. (NEO-10016)
* È stato risolto un problema che causava l&#39;arresto anomalo del server Web IIS durante il processo di riciclo del pool di applicazioni (nella libreria nlsrvmod.dll). (NEO-10862)
* È stato risolto un problema che poteva impedire la ricerca di un destinatario in **Profili e destinazione** schermo. (NEO-8228)
* È stato risolto un problema che poteva causare un errore di timeout durante l’accesso alla cartella Cronologia eventi nel caso di un numero elevato di record. (NEO-11738)
* È stato risolto un problema che poteva causare la restituzione errata di &quot;Non raggiungibile&quot; da parte dei destinatari della consegna LINE. (NEO-10833)
* È stato risolto un problema che si verificava durante l’esecuzione di una query del flusso di lavoro con una colonna aggiuntiva sull’Oracle. (NEO-11615)
* È stato apportato un miglioramento per garantire che le connessioni chiuse non vengano mantenute nel pool di connessioni per troppo tempo. (NEO-11392)
* È stato risolto un problema che si verificava durante l’utilizzo di un’attività del flusso di lavoro di targeting (query, caricamento dati (RDBMS), ecc.) connesso tramite FDA a una tabella di Oracle esterna contenente caratteri UTF8 (nel nome della tabella, nel nome del campo, ecc.) e che conteneva anche un vincolo di chiave primaria con un nome di vincolo di default generato dal sistema. (NEO-10714)
* È stato risolto un problema che poteva impedire l’eliminazione del contenuto HTML di una consegna. (NEO-11327)
* È stato risolto un problema relativo all’anteprima di file XML e CSV in una direct mailing dopo l’esecuzione di una campagna. (NEO-11290)
* È stato risolto un problema che si verificava durante l’ordinamento dei dati in un’attività del flusso di lavoro di arricchimento. (NEO-11394)
* È stato risolto un problema che si verificava durante l’ordinamento dei dati in un rapporto personalizzato. (NEO-10896)
* È stato risolto un problema che causava errori durante l’utilizzo dell’impostazione useVault con Teradata. (NEO-11399)
* È stato risolto un problema che causava l’arresto anomalo della console client di Adobe Campaign durante l’eliminazione di più righe di query. (NEO-10744)
* È stato risolto un problema che impediva l’applicazione delle regole di pressione in alcuni casi durante la consegna della direct mailing. (NEO-9004)
* È stato risolto un problema che si verificava durante l’utilizzo dell’attività di caricamento dati per importare una colonna con tipo di dati &quot;tempo&quot;: il separatore dell’ora veniva reimpostato anche dopo la rimozione. (NEO-10743)
* È stato risolto un problema che impediva la visualizzazione della cartella Consegne dall’elenco della cartella Esecuzione nelle proprietà Consegna durante la modifica di una consegna ricorrente. (NEO-11094)
* È stato risolto un problema che impediva alla finestra Visualizza popolazione di visualizzare più di 200 record come destinazione risultante di un’attività Query in un flusso di lavoro. (NEO-11195)
* È stato risolto un problema in Oracle che impediva l’esecuzione di una query DELETE con più di 1000 elementi selezionati. (NEO-11171)
* È stato risolto un problema che causava la codifica degli URL come URL tracciati nei parametri aggiuntivi di una consegna di notifiche push in Android. (NEO-11468)
* È stato corretto un errore di script che si verificava nel rapporto delle attività utente quando si impostavano i parametri su &quot;Intervalli di un giorno&quot; e &quot;Aperture&quot;. (NEO-11655)
* È stato risolto un problema che si verificava durante la connessione al server di mid-sourcing o al Centro messaggi tramite un proxy web autenticato. (NEO-11309)
* È stato corretto un errore di Oracle che si verificava al salvataggio di una nuova composizione di consegna dopo la selezione di un elemento di uno schema specifico **basato su una vista SQL**. (NEO-11682)
* È stato risolto un problema che causava la generazione di file di rifiuto contenenti falsi positivi durante l’elaborazione di un file zip contenente un .csv tramite un’attività di caricamento file tramite l’opzione Decompressione.
* xtkjoblog viene ora eliminato dalla pulizia.

## Versione 18.6

### Versione 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 agosto 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [eseguire l’aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatto [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Query banding<br /> </td> 
   <td> <p>Quando più utenti di Campaign si connettono allo stesso account esterno di Teradata FDA, ora puoi passare una banda di query (coppie chiave/valore) specifica per ogni utente. Ogni volta che un utente di Campaign esegue una query sul database Teradata, Adobe Campaign è ora in grado di inviare metadati associati all’utente. Tali dati, che consistono in un elenco di chiavi e valori, possono quindi essere utilizzati dagli amministratori di Teradate a scopo di audit o per gestire, ad esempio, i diritti di accesso.</p><p>Per ulteriori informazioni, consulta la <a href="../../installation/using/external-accounts.md">documentazione dettagliata</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati per semplificare e chiarire la verifica delle e-mail consegnate correttamente o non consegnate tramite l’archiviazione Ccn. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del load balancer invece degli IP dei clienti nei registri di tracciamento. (NEO-11295)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato corretto un errore di sintassi durante l’ordinamento dei risultati dell’attività di arricchimento. (NEO-11394)
* È stato risolto un problema che si verificava con l’utilizzo di campi calcolati in una **[!UICONTROL Survey answers]** attività del flusso di lavoro. (NEO-11382)
* Tomcat è stato aggiornato per prevenire lo sfruttamento delle vulnerabilità. (NEO-11503)
* È stato corretto un errore di codifica LATIN1 che si verificava con l’utilizzo di una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l’utilizzo di **[!UICONTROL Prepare the personalization data with a workflow]** opzione di consegna. (NEO-11047)
* È stato risolto un problema di post-aggiornamento che impediva l’invio di SMS quando si utilizzava un connettore esteso.
* Importazione/esportazione del pacchetto migliorata (nell’interfaccia sono stati aggiunti log e area).
* È stato risolto un problema che causava la visualizzazione di errori inutili nel registro di post-aggiornamento in caso di **[!UICONTROL Survey answers]** l’attività del flusso di lavoro non è stata completamente configurata.

**Evoluzioni tecniche**

Query banding

Una chiave specifica (PROXYUSER o PROXYROLE) viene utilizzata per associare un utente o un ruolo Teradata a un utente Campaign. È stata aggiunta una nuova autorizzazione per utilizzare questo utente/ruolo proxy. È necessario aggiungere il diritto di accesso GRANT CONNECT THROUGH all&#39;account del database (quello definito nell&#39;account esterno Teradata).

È stata aggiunta una nuova scheda negli account esterni di Teradata. Il **[!UICONTROL Query banding]** La scheda include le seguenti opzioni:

* **[!UICONTROL Active]**: seleziona questa casella per attivare la funzione.
* **[!UICONTROL Default]**: inserisci un Query Banda predefinito che verrà utilizzato se a un utente non è associata alcuna Query Banda. Se non è stata definita alcuna query banding predefinita, gli utenti a cui non è associata alcuna query banding non potranno utilizzare Teradata.
* **[!UICONTROL Users]**: per ogni utente, specifica un Query banding. Puoi aggiungere tutte le coppie chiave/valore necessarie. Ad esempio: &quot;priorità=1;carico di lavoro=alto;&quot;

Per ulteriori informazioni sul Query banding, consulta questi articoli:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Versione 18.6.1 - Build 8947{#release-18-6-build-8947}

25 giugno 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [eseguire l’aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatto [supporto tecnico](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Miglioramenti della sicurezza<br /> </td> 
   <td> È stata aggiunta una serie di miglioramenti di sicurezza a Campaign Classic. Miglioramenti e correzioni sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Supporto di Windows Server 2016<br /> </td> 
   <td> Adobe Campaign è ora compatibile con Windows Server 2016. Fai riferimento a <a href="https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html">Matrice di compatibilità Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

decryptString

Il **decryptString** è obsoleto. Consulta la sezione [Funzioni obsolete e rimosse](deprecated-features.md) articolo.

Per i nuovi clienti, questa funzione viene ora utilizzata solo per decrittografare l’ID crittografato del destinatario nelle pagine di destinazione. Per decrittografare le password archiviate in un account esterno, utilizzare il nuovo **decryptPassword** funzione.

Per i clienti esistenti, il comportamento di questa funzione non viene modificato, ma si consiglia di utilizzare **decryptPassword** invece di **decryptString**. Il **XtkSecurity_Unsafe_DecryptString** l’opzione di compatibilità viene aggiunta dal post-aggiornamento e attivata per impostazione predefinita, consentendo di continuare a utilizzare la funzione. Se desideri disattivare **decryptString**, disattiva l’opzione.

decryptPassword

Il **decryptPassword** è stata aggiunta la funzione. Consente di decrittografare una password archiviata in un account esterno. Consulta la sezione [JSAPI](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html) per ulteriori informazioni.

API dei file

Per le nuove installazioni, l’accesso alle cartelle tramite API di file è limitato al **var**, **sftp** e cartelle temporanee di Adobe Campaign.

Per i clienti esistenti, le API dei file non possono più accedere al **conf** cartella di Adobe Campaign. Il **XtkSecurity_Disable_JSFileSandboxing** l’opzione di compatibilità viene aggiunta dal post-aggiornamento e attivata per impostazione predefinita, consentendo di continuare ad accedere alle altre cartelle. Se desideri limitare l’accesso a **var**, **sftp** e cartelle temporanee di Adobe Campaign, disattiva l’opzione.

**Patch**

* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)

## Versione 18.4

### Versione 18.4.5 - Build 8937{#release-18-4-5-build-8937}

21 novembre 2018

**Miglioramenti**

* Sono stati risolti diversi problemi che si verificavano durante l’esecuzione di flussi di lavoro tramite MySQL su FDA. (NEO-11652)
* È stato risolto un problema che causava la permanenza di una parte della popolazione di consegna nello stato In sospeso, in casi specifici. (NEO-11336)
* È stato risolto un problema intermittente relativo alla risposta automatica SMS. (NEO-11811)
* È stato risolto un problema di esaurimento ID che si verificava con l’utilizzo di indirizzi di seed in una consegna. (NEO-11842)
* È stato corretto un errore di sintassi durante l’esecuzione di un ordinamento in un’attività del flusso di lavoro di arricchimento. (NEO-11394)
* È stato risolto un problema che poteva causare un arresto anomalo del server web durante il riavvio di IIS. (NEO-10862)
* È stato risolto un problema che poteva causare un errore nel flusso di lavoro di tracciamento dopo un aggiornamento della build (FDA - SQL). (NEO-11635)
* È stato risolto un problema che poteva causare la perdita di dati dell’elenco del flusso di lavoro. (NEO-11696)
* È stato risolto un problema di prestazioni che si verificava durante l’invio di notifiche push. (NEO-11787)
* È stato risolto un problema che impediva il funzionamento del tracciamento web per i domini &quot;com.au&quot; (NEO-4385).
* È stato risolto un problema di blocco del client che poteva verificarsi durante l’utilizzo di flussi di lavoro complessi. (NEO-11847)
* È stato corretto un errore di Oracle che si verificava durante il salvataggio di una nuova consegna dopo la selezione di un elemento di uno schema specifico (NEO-11682).
* È stato risolto un problema che si verificava durante la query di un campo contenente caratteri con accenti (FDA/Teradata). L&#39;account esterno ora consente di modificare la codifica utilizzata per comunicare con il driver della Teradata. (NEO-11818).
* È stato risolto un problema di tracciamento che si verificava durante il passaggio di URL in variabili aggiuntive in una notifica push, che poteva causare la ricezione di dati non formattati correttamente o errati da parte dell’app mobile. (NEO-11468, NEO-11960)
* È stato risolto un problema che causava un problema di visualizzazione durante l’utilizzo di una distribuzione di valori con un collegamento 1:N. (NEO-11820)
* È stato risolto un problema che impediva il funzionamento del carico in blocco sulla Teradata 16.
* È stata aumentata la dimensione del buffer per la marca temporale sulla Teradata per evitare problemi di binding con il driver 15.10.
* È stata migliorata la gestione degli indici dei nomi lunghi che poteva causare problemi post-aggiornamento.
* È stato migliorato il tempo disponibile per la memoria condivisa durante l’elaborazione dei dati inattivi (MTA, Children Dead Processing).
* È stato risolto un potenziale deadlock in Apache (tracciamento).


### Versione 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1° agosto 2018

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati per semplificare e chiarire la verifica delle e-mail consegnate correttamente o non consegnate tramite l’archiviazione Ccn. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del load balancer invece degli IP dei clienti nei registri di tracciamento. (NEO-11295)
* È stato corretto un errore di codifica LATIN1 che si verificava con l’utilizzo di una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l’utilizzo di **[!UICONTROL Prepare the personalization data with a workflow]** opzione di consegna. (NEO-11047, NEO-11301)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato risolto un problema che si verificava con l’utilizzo di campi calcolati in una **[!UICONTROL Survey answers]** attività del flusso di lavoro. (NEO-11382)
* È stato risolto un problema che si verificava durante l’utilizzo di dati memorizzati in XML in una **[!UICONTROL Survey answers]** attività del flusso di lavoro. (NEO-10816)
* È stato risolto un problema che si verificava durante l’aggiornamento del server con la build 8935.
* È stato risolto un problema che causava la visualizzazione di errori inutili nel registro di post-aggiornamento in caso di **[!UICONTROL Survey answers]** l’attività del flusso di lavoro non è stata completamente configurata.
* Teradata FDA: è stato risolto un problema relativo ai campi e agli indici incrementati automaticamente nelle tabelle SQL.

### Versione 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 giugno 2018

**Miglioramenti**

* È stato risolto un problema di codifica del tracciamento con Microsoft Edge e Internet Explorer. (NEO-11257)
* È stato risolto un problema relativo alla personalizzazione dei collegamenti immagine nelle consegne LINE. (NEO-11077)
* È stato risolto un problema che impediva il corretto funzionamento del meccanismo di generazione della sequenza ID. (NEO-11115)
* È stato risolto un problema che impediva il funzionamento delle richieste di privacy (RGPD) quando si utilizzava uno spazio dei nomi personalizzato con una chiave di riconciliazione del tipo intero. (NEO-11123)
* È stato corretto un errore che poteva verificarsi durante l’utilizzo di **[!UICONTROL Distribution of values]** opzione in **[!UICONTROL Query]** attività del flusso di lavoro. (NEO-10958)
* È stato risolto un problema che si verificava durante la sincronizzazione degli spazi dell’offerta dall’istanza di marketing all’istanza di interazione. (NEO-11162)
* È stata migliorata la gestione degli indici dei nomi lunghi durante il post-aggiornamento

### Versione 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 maggio 2018

**Miglioramenti**

* È stato risolto un problema che impediva il corretto funzionamento dell’aggiornamento di Windows Server.
* È stato risolto un problema in **[!UICONTROL Survey Result]** quando si utilizzano dati memorizzati in XML. Il rapporto non veniva visualizzato correttamente. (NEO-10816)
* È stato risolto un problema di prestazioni che poteva verificarsi con il processo inMail quando si utilizzava un server di posta non recapitata. (NEO-10641)
* È stato risolto un problema di aggiornamento del database che poteva verificarsi quando si aggiornavano più di 1000 schemi.

### Versione 18.4.1 - Build 8931{#release-18-4-build-8931}

24 aprile 2018

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
   <td> Regolamento generale sulla protezione dei dati (RGPD) dell’UE<br /> </td> 
   <td> <p>Il RGPD è la nuova legge sulla privacy dell’Unione europea (UE) che armonizza e modernizza i requisiti in materia di protezione dei dati, in vigore dal 25 maggio 2018. Il GDPR si applica ai clienti di Adobe Campaign che conservano dati per soggetti che risiedono nell’Unione europea.</p> <p>Oltre alle funzionalità per la privacy già disponibili in Adobe Campaign (tra cui la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente), in qualità di responsabile del trattamento dei dati vogliamo sfruttare l’opportunità di includere funzionalità aggiuntive per aiutarti ad essere pronto a determinate richieste RGPD in qualità di titolare del trattamento dei dati:</p> 
    <ul> 
     <li> <p>Diritto di accesso: consente all’interessato di ricevere una copia dei suoi dati personali acquisiti dai titolari del trattamento, inclusi potenzialmente i dati memorizzati in Adobe Campaign.</p> </li> 
     <li> <p>Diritto di cancellazione: autorizza l’interessato a richiedere la cancellazione dei suoi dati personali acquisiti dai titolari del trattamento, inclusi potenzialmente i dati memorizzati in Adobe Campaign.</p> </li> 
    </ul> Per ulteriori informazioni, consulta la <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">documentazione dettagliata</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Profili attivi<br /> </td> 
   <td> <p>Adobe Campaign ora fornisce l’elenco dei profili attivi, aggiornato mensilmente tramite un flusso di lavoro dedicato.</p> <p>Per ulteriori informazioni, consulta la <a href="../../platform/using/about-profiles.md#active-profiles">documentazione dettagliata</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Miglioramento del connettore push Android<br /> </td> 
   <td> <p>Il connettore Android è stato migliorato per supportare una velocità effettiva più elevata. </p> <p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/configuring-the-mobile-application.md">documentazione dettagliata</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* L’espansione delle entità esterne è ora disabilitata per evitare potenziali attacchi da parte di utenti non autenticati. (NEO-10173)
* Autorizzazioni avanzate per impedire agli utenti standard di modificare i parametri di configurazione dell’istanza come URL di accesso all’applicazione, impostazioni LDAP e così via. (NEO-10171)
* È stato risolto un problema che poteva rivelare informazioni sensibili tramite tracce dello stack. I dettagli dell’errore vengono ora registrati nel back-end in una posizione non accessibile dalla rete esterna. (NEO-10176)
* Autorizzazioni avanzate per impedire agli utenti standard di visualizzare i documenti caricati e/o i pacchetti esportati di un amministratore. (NEO-10170)

**Miglioramenti**

* **Canale LINE - Miglioramento dell’architettura**: come tutti gli altri canali in Adobe Campaign, il canale LINE è ora supportato su tutti i tipi di distribuzione: in hosting, ibrida e on-premise.
* **Generazione automatica della sequenza**: il meccanismo di generazione degli ID è stato migliorato per aumentare la durata delle istanze Campaign con grandi volumi di oggetti.

**Altre modifiche**

* È disponibile una nuova modalità per l’importazione dei pacchetti utilizzando la riga di comando, che consente le dipendenze circolari (non consigliata per i pacchetti di grandi dimensioni). Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot;. (NEO-8979)
* Sono state migliorate le prestazioni per grandi quantità di dati caricati in Teradata e è stato risolto un problema che impediva la visualizzazione del valore corretto dei dati elaborati nel registro. (NEO-10429)
* L’importazione di tipi di pubblico da Audience Manager ora funziona con file suddivisi. In precedenza, solo l’ultimo file del segmento veniva importato dal flusso di lavoro tecnico importSharedAudience. (NEO-10156)
* In Windows, il percorso di installazione predefinito del server Campaign è stato modificato. Quando si avvia l&#39;installazione della versione a 64 bit, il percorso di installazione predefinito è ora: **C:\Program Files\Adobe\Adobe Campaign Classic v7** invece di **File C:\Program (x86)\Adobe\Adobe Campaign Classic v7**
* Le regole MX predefinite sono state migliorate per includere più domini e ottimizzare la velocità effettiva.
* Sono state applicate restrizioni di accesso alla chiamata SOAP della procedura guidata di distribuzione (xtk:serverOptions#SaveOptions).
* La libreria obsoleta weka.jar è stata rimossa e la libreria OpenSSL è stata aggiornata per l’ottimizzazione della sicurezza.
* È stato migliorato il flusso di lavoro tecnico di fatturazione per proteggere le prestazioni delle istanze.
* È stata ripristinata la possibilità per gli amministratori di impostare o reimpostare la password di qualsiasi operatore. A questo scopo, fai clic con il pulsante destro del mouse su un operatore, seleziona **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e impostare la nuova password dell&#39;operatore. È consigliabile che gli operatori modifichino la password alla prima riconnessione. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../production/using/lost-password.md).
* Per supportare la nuova funzione di multitenancy in Adobe Target, è ora possibile aggiungere agli URL un nuovo parametro &quot;at_property&quot; durante la configurazione di opzioni e account esterni per l’integrazione con Target. Il valore da utilizzare per questo parametro si trova in Adobe Target e verrà utilizzato da Campaign durante l’esecuzione di chiamate a Target. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* Ora puoi specificare una pagina di destinazione predefinita da aprire facendo clic su un’immagine fornita da Adobe Target. In precedenza, facendo clic su tale immagine veniva creato il set di immagini predefinito durante la creazione dell’e-mail. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* Aggiunto **Abilita tracce SMPP** per forzare l&#39;output di analisi, selezionare la casella di controllo nell&#39;account esterno. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Evoluzioni tecniche**

queryDef

queryDef è stato modificato per quanto riguarda la clausola &quot;orderBy&quot;. Prima della modifica, la chiave primaria della tabella interrogata veniva implicitamente aggiunta alle clausole &quot;orderBy&quot;. In alcuni motori di database (almeno postgresql), impedisce l&#39;utilizzo di indici (tutti i campi della clausola orderBy devono essere coperti dallo stesso indice). Se si è dipendenti da questo comportamento, è necessario aggiungere esplicitamente la chiave primaria nella clausola &quot;orderBy&quot;.

Ad esempio, se disponi della seguente query:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Sarebbe implicitamente consegnato come (prima delle modifiche del 18.4):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

funzione urlEncode

La funzione JavaScript urlEncode non funzionava correttamente per i caratteri non ASCII. È stato corretto e ora dovrebbe funzionare con tutti i caratteri Unicode (inclusi i caratteri giapponesi). Se per il carattere non ASCII si utilizza il comportamento &quot;urlEncode&quot;, sarà necessario adattare il codice.

Nuova modalità di importazione pacchetti

È disponibile una nuova modalità per l’importazione dei pacchetti utilizzando la riga di comando, che consente le dipendenze circolari (non consigliata per i pacchetti di grandi dimensioni). La funzionalità esistente viene mantenuta. Per tali pacchetti con dipendenze circolari, un nuovo flag **-usejs** è stato aggiunto al pacchetto della riga di comando import. Quando viene eseguito, utilizzerà il motore JSE come quando l’importazione del pacchetto viene eseguita dall’interfaccia.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patch**

* È stato risolto un problema di sincronizzazione che si verificava durante la replica dei registri di consegna e di tracciamento da Adobe Campaign Standard a Adobe Campaign Classic. (NEO-10023)
* È stato risolto un problema relativo alla gestione delle tabelle Error e Log nella Teradata quando un flusso di lavoro ETL riprendeva dopo un errore in un’operazione di caricamento rapido. Le tabelle Errore e Registro ora vengono eliminate correttamente ogni volta che il flusso di lavoro riprende. (NEO-10672)
* È stato risolto un problema post-aggiornamento per installare automaticamente il pacchetto Hive (necessario per il Hadoop) se il pacchetto FDA è installato. (NEO-10592)
* È stato corretto un errore a causa del quale i domini non validi venivano trattati come **Non definito** errore. (NEO-10248)
* È stato risolto un problema che duplicava i registri nella tabella deliveryLogStats durante l’invio di consegne push android. (NEO-10234)
* È stato risolto un problema che poteva impedire la lettura di determinati formati di codice a barre da parte degli scanner di codici a barre. (NEO-10125)
* È stato risolto un problema relativo alla funzione JavaScript &quot;urlEncode&quot; quando si utilizzavano caratteri non ASCII. Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot;. (NEO-10123)
* È stato risolto un problema che si verificava durante l’esecuzione di una query contenente funzioni sha256 sui database Teradata. (NEO-10119)
* Sono stati corretti alcuni errori di memoria del flusso di lavoro che potevano verificarsi nell’attività SalesForce quando si utilizzavano tabelle SalesForce di dimensioni molto grandi. (NEO-9900)
* È stato risolto un problema relativo al **Genera complemento** opzione nel targeting delle attività del flusso di lavoro quando si utilizza FDA. (NEO-9878)
* È stato risolto un problema che poteva causare **Elaborato** e **Completato** le metriche non vengono aggiornate nell’istanza di marketing quando si utilizza il mid-sourcing. (NEO-9454)
* Sono state corrette le regole di non riproposizione dell’interazione quando la piattaforma contiene più di 10.000 offerte in totale (NEO-9352)
* È stato risolto un problema che poteva impedire di specificare la destinazione di una consegna quando si utilizzava un file esterno XML. (NEO-9312)
* È stato risolto un problema che poteva causare errori del flusso di lavoro durante l’esecuzione di un’ipotesi su un’offerta e l’aggiornamento dello stato della proposta. (NEO-9304)
* Sono stati corretti gli errori che si verificavano durante l’analisi della consegna quando si utilizzavano regole di pressione basate su un attributo della mappatura di consegna Android. (NEO-9202)
* È stato risolto un problema che si verificava durante l’ordinamento delle colonne nell’elenco dei destinatari e che poteva causare problemi di prestazioni. Per ulteriori informazioni sulle modifiche di queryDef, consulta la sezione &quot;Evoluzioni tecniche&quot; di seguito. (NEO-9042)
* È stato risolto un problema a causa del quale i collegamenti in un messaggio e-mail di approvazione potevano indicare un URL di accesso errato, in particolare quando si utilizzava un tipo di accesso di Federated ID. (NEO-9011)
* È stato risolto un problema che poteva causare la visualizzazione di date errate nei selettori di date dei rapporti per alcuni fusi orari. (NEO-9007)
* È stato risolto un problema che impediva la visualizzazione della destinazione di un oggetto in uscita quando si utilizzava un database SQL FDA. (NEO-8924)
* È stato risolto un problema che impediva al connettore MS Dynamics CRM di estrarre i dati per i primi 7 giorni del mese. (NEO-8803)
* È stato corretto un errore nell’integrazione di Analytics che impediva agli utenti di includere caratteri internazionali. (NEO-8719)
* È stato risolto un problema che poteva abilitare la modifica del flusso di lavoro senza i diritti appropriati. (NEO-8708)
* È stato risolto un problema con FDA su HTTP che si verificava durante l’utilizzo del Centro messaggi in un’architettura ibrida, causando l’interruzione o la perdita della connessione (timeout). (NEO-8438)
* Sono stati corretti gli errori del flusso di lavoro che si verificavano nell’attività di query incrementale per gli ID negativi. (NEO-8229)
* È stato risolto un problema che poteva causare la visualizzazione di barre di scorrimento doppie in determinate schermate. (NEO-8208)
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore durante l’esecuzione della procedura guidata di aggiornamento della struttura del database. PostUpgrade eseguirà una ridenominazione degli indici con nomi più lunghi di 30. Tieni presente che per le tabelle di grandi dimensioni la sostituzione dell’indice richiederà del tempo. (NEO-7983)
* È stato risolto un problema che impediva la corretta sincronizzazione dei registri di tracciamento dall’istanza di esecuzione del Centro messaggi all’istanza di controllo. (NEO-7286)
* È stato risolto un problema di prestazioni relativo all’attività di arricchimento delle offerte. (NEO-7263)
* È stato risolto un problema che impediva l’utilizzo della funzione DaysAgo durante la query di un database Redshift tramite FDA. (NEO-7099)
* È stata risolta una regressione nella gestione dei dati che impediva la creazione di indici sulle attività del flusso di lavoro di tipo Arricchimento.
* È stato risolto un problema che poteva verificarsi durante la creazione di risorse esterne con il @id titolo
* È stato risolto un problema che poteva verificarsi durante il caricamento di file compressi tramite un server FTP o durante il caricamento di file il cui nome conteneva caratteri jolly.
* È stato risolto un problema relativo alle enumerazioni dei tipi di base lunghi nelle risorse personalizzate esterne create in Campaign Standard.
* È stato risolto un problema che poteva causare l’invio di SMS anche quando la connessione con il provider non riusciva, causando perdite di SMS.
* È stato corretto un errore che causava il blocco indefinito di una connessione SMTP.
* È stato risolto un problema relativo alle regole di tipologia di pressione durante la preparazione dei messaggi quando si utilizza una mappatura LINE o quando gli schemi di filtraggio e targeting differiscono.
