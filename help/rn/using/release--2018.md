---
product: campaign
title: Versioni di Campaign Classic 2018
description: Ulteriori informazioni sulle versioni di Campaign Classic 2018
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: 96f2ae67a5b47b80533e759713cf5b36baa8cf36
workflow-type: tm+mt
source-wordcount: '5414'
ht-degree: 8%

---

# Versioni 2018{#release-2018}

![](../../assets/v7-only.svg)

## Versione 18.10

### Versione 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 luglio 2019

**Miglioramenti**

* È ora possibile eliminare i record fittizi creati in Microsoft Dynamics durante il flusso di lavoro di importazione.
* È stato risolto un problema relativo all’attività del flusso di lavoro Raccolta file che poteva registrare gli errori in loop quando l’accesso a un file veniva negato. (NEO-12085)
* È stato risolto un problema che causava discrepanze nella generazione di rapporti tra le attività degli utenti e i rapporti di tracciamento per l’indicatore di consegna aperta. (NEO-11742)
* Sono state migliorate le autorizzazioni per eseguire il pacchetto della zona di sicurezza quando si utilizza un account interno.
* È stato risolto un problema che poteva causare errori nei log figlio master. (NEO-8978)

### Versione 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 aprile 2019

**Miglioramenti**

* È stato risolto un problema relativo al blocco critico SQL che causava un errore di analisi della consegna in caso di analisi/invio simultanei (quando due consegne venivano analizzate contemporaneamente). (NEO-13026)
* È stato rimosso il limite di 10.000 record in Workflow Heatmap per risolvere un problema di dati mancanti. (NEO-12329)
* È stato risolto un problema che si verificava con l’opzione &quot;Conserva tutti i dati aggiuntivi dal set principale&quot; in un’attività del flusso di lavoro di arricchimento. (NEO-13291)

### Versione 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 aprile 2019

**Miglioramenti**

* È stato risolto un problema relativo al processo di elaborazione degli indicatori di tracciamento per i messaggi transazionali. (NEO-12529, NEO-12581)
* È stato risolto un problema relativo all’API HTTPRequest che non aspettava il completamento di tutti i callback. (NEO-12628)
* Sono stati aggiunti indici nelle tabelle temporanee del coupon per ottimizzare l’invio della consegna. (NEO-12437)
* È stato risolto un problema che si verificava durante l’analisi di un messaggio con targeting dei destinatari per i domini giapponesi (.JP). (NEO-12246)
* Nell’integrazione di Analytics, è ora consentito il recupero di dati AAM segmento con carattere %. (NEO-12025)
* È stato risolto un problema di arresto anomalo Tomcat che si verificava durante l’invio di notifiche push tramite HTTP2. (NEO-12701)

### Versione 18.10.3 - Build 8981{#release-18-10-3-build-8981}

29 gennaio 2019

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [aggiornamento alla build più recente](../../production/using/build-upgrade.md)  o contatti [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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

### Versione 18.10.2 - Build 8978{#release-18-10-2-build-8978}

6 dicembre 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatti [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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


### Versione 18.10.1 - Build 8977{#release-18-10-build-8977}

5 novembre 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatti [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
     <li> <p>Migliorare la velocità di preparazione delle consegne in iOS</p> </li> 
    </ul> <p>Come parte del deprezzamento del GCM da parte di Google, il connettore Android V2 ora permette connessioni solo al server FCM.</p><p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentazione dettagliata</a>. L'aggiornamento manuale a FCM è descritto in questo <a href="https://helpx.adobe.com/it/campaign/kb/migrate-to-fcm.html">articolo</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> Attività di gestione dati SQL<br /> </td> 
   <td> <p>È stata aggiunta una nuova attività del flusso di lavoro di gestione dati. La <strong>Gestione dati SQL</strong> attività consente di scrivere o copiare-incollare i propri script SQL per creare e popolare tabelle di lavoro (solo FDA). </p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/sql-data-management.md">documentazione dettagliata</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Monitoraggio del flusso di lavoro<br /> </td> 
   <td> <p>Con la nuova Adobe Campaign Workflow HeatMap, gli amministratori della piattaforma dispongono di una rapida rappresentazione grafica di tutti i flussi di lavoro simultanei, che consente loro di monitorare il carico sull’istanza e pianificare i flussi di lavoro di conseguenza.</p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/heatmap.md">documentazione dettagliata</a>.</p> <p>Il pacchetto Workflow HeatMap è disponibile anche su richiesta per le build precedenti alla 8977 (a partire dalla build 8700). Per ulteriori informazioni su come richiederlo e installarlo, consulta <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">questa pagina</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* È stato risolto un problema di sicurezza che poteva causare vulnerabilità agli attacchi SSRF (Server Side Request Forgery) e attacchi di negazione del servizio (DoS). (NEO-11453)
* Contenuto (reindirizzamento di tracciamento, pagine mirror, sondaggi, ecc.) verrà ora servito da Campaign con il tag X-Robots: intestazione nocache. Questo impedisce l’indicizzazione di questo contenuto da parte dei motori di ricerca Internet. (NEO-11101)
* È stato risolto un problema di iniezione XTK nell’API di abbonamento (nms):subscription:Annulla sottoscrizione e nms:subscription:Iscriviti).
* È stato risolto un problema di iniezione XTK nell’applicazione Web di annullamento dell’abbonamento.
* Sono state rimosse le password che erano visualizzate in modo non corretto in alcuni registri SMS.

**Miglioramenti**

* Le API di Campaign Classic sono ora disponibili in una [pagina dedicata](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it). Se stavi utilizzando il file jsapi.chm, ora devi fare riferimento alla nuova versione online.
* PostgreSQL 10, Debian 9 e Teradata 16.20 sono ora supportati. Consulta la [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html).
* Quando crei una connessione SFTP, ora puoi utilizzare l’autenticazione proxy. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../installation/using/file-res-management.md) (NEO-9868)
* La **Formula di calcolo della data** è ora disponibile nelle proprietà di consegna quando crei una singola consegna utilizzando il modello di consegna direct mailing. (NEO-9792)
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

Ora, tutti i nomi di dominio di secondo livello a due lettere sono supportati per impostazione predefinita (ad esempio, .aa.com). Per i nomi di dominio più complessi (ad esempio, domini di secondo livello a tre lettere come .com.au), devi aggiungerli nel **cookieDomains** dell&#39;opzione serverConf (sotto il tag di reindirizzamento). Ecco un esempio:

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

* È stato corretto un errore che impediva ai file di **Download Web** attività del flusso di lavoro da scaricare. (NEO-11105)
* È stato corretto un errore che talvolta lasciava la variabile **Invio di indicatori e attributi della campagna** in uno stato Non riuscito (NEO-10820).
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
* È stato risolto un problema che poteva impedire la ricerca di un destinatario in **Profili e Target** schermo. (NEO-8228)
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
* È stato corretto un errore di Oracle che si verificava quando una nuova composizione di consegna veniva salvata dopo la selezione di un elemento di uno schema specifico **basato su una vista SQL**. (NEO-11682)
* È stato risolto un problema che causava la generazione di file di rifiuto contenenti falsi positivi durante l’elaborazione di un file zip contenente un .csv tramite un’attività di caricamento file tramite l’opzione Decompression.
* xtkjoblog viene eliminato dalla pulizia.

## Versione 18.6

### Versione 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 agosto 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatti [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Proiezione query<br /> </td> 
   <td> <p>Quando più utenti di Campaign si collegano allo stesso account esterno della Teradata FDA, ora puoi passare una banda di query (coppie chiave/valore) specifica per ogni utente. Ogni volta che un utente di Campaign esegue una query sul database di Teradata, Adobe Campaign è ora in grado di inviare i metadati associati all’utente. Questi dati, costituiti da un elenco di chiavi e valori, possono quindi essere utilizzati dagli amministratori di Teradata a scopo di controllo o per gestire i diritti di accesso, ad esempio.</p><p>Per ulteriori informazioni, consulta la <a href="../../installation/using/external-accounts.md">documentazione dettagliata</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati, il che rende più semplice e chiaro il controllo delle e-mail consegnate correttamente o non riuscite tramite l’archiviazione CCN. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del load balancer invece degli IP dei clienti nei log di monitoraggio dei broadcaster. (NEO-11295)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato corretto un errore di sintassi durante l’ordinamento dei risultati dell’attività di arricchimento. (NEO-11394)
* È stato risolto un problema che si verificava durante l’utilizzo dei campi calcolati in una **[!UICONTROL Survey answers]** attività del flusso di lavoro. (NEO-11382)
* Tomcat è stato aggiornato per prevenire lo sfruttamento delle vulnerabilità. (NEO-11503)
* È stato corretto un errore di codifica LATIN1 durante l’utilizzo di una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l&#39;utilizzo del **[!UICONTROL Prepare the personalization data with a workflow]** opzione di consegna. (NEO-11047)
* È stato risolto un problema relativo al post aggiornamento che impediva l’invio di SMS quando si utilizzava un connettore esteso.
* Importazione/esportazione del pacchetto migliorata (registro e area geografica aggiunti nell’interfaccia).
* È stato risolto un problema che mostrava errori inutili nel registro post-aggiornamento quando un **[!UICONTROL Survey answers]** attività del flusso di lavoro non configurata completamente.

**Evoluzioni tecniche**

Proiezione query

Una chiave specifica (PROXYUSER o PROXYROLE) viene utilizzata per associare un utente o un ruolo di Teradata a un utente di Campaign. È stata aggiunta una nuova autorizzazione per utilizzare questo utente/ruolo proxy. È necessario aggiungere il diritto di accesso GRANT CONNECT THROUGH all’account del database (quello definito nell’account esterno Teradata).

È stata aggiunta una nuova scheda negli account esterni Teradata. La **[!UICONTROL Query banding]** La scheda include le seguenti opzioni:

* **[!UICONTROL Active]**: selezionare questa casella per attivare la funzione.
* **[!UICONTROL Default]**: immetti un binding di query predefinito che verrà utilizzato se un utente non dispone di un binding di query associato. Se non è definito alcun banding di query predefinito, gli utenti che non dispongono di un binding di query associato non saranno in grado di utilizzare Teradate.
* **[!UICONTROL Users]**: per ogni utente, specificare una banda di query. Puoi aggiungere tutte le coppie chiave/valore necessarie. Ad esempio: &quot;priority=1;carico di lavoro=alto;&quot;

Per ulteriori informazioni sul binding delle query, consulta questi articoli:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Versione 18.6.1 - Build 8947{#release-18-6-build-8947}

25 giugno 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatti [supporto tecnico](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> In Campaign Classic è stata aggiunta una serie di miglioramenti a livello di sicurezza. I miglioramenti e le correzioni sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Supporto di Windows Server 2016<br /> </td> 
   <td> Adobe Campaign è ora compatibile con Windows Server 2016. Fai riferimento a <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matrice di compatibilità di Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

decryptString

La **decryptString** è obsoleta. Fai riferimento a [Funzioni obsolete e rimosse](deprecated-features.md) articolo.

Per i nuovi clienti, questa funzione ora viene utilizzata solo per decifrare l’ID crittografato del destinatario nelle pagine di destinazione. Per decrittografare le password memorizzate in un account esterno, utilizza il nuovo **decryptPassword** funzione .

Per i clienti esistenti, il comportamento di questa funzione non viene modificato, ma ti consigliamo di utilizzare **decryptPassword** anziché **decryptString**. La **XtkSecurity_Unsafe_DecryptString** l’opzione di compatibilità viene aggiunta dall’aggiornamento successivo e attivata per impostazione predefinita, consentendo di continuare a utilizzare la funzione . Per disattivare **decryptString**, disattiva l’opzione .

decryptPassword

La **decryptPassword** è stata aggiunta la funzione . Consente di decrittografare una password memorizzata in un account esterno. Fai riferimento a [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) documentazione per ulteriori informazioni.

API file

Per le nuove installazioni, l’accesso alle cartelle tramite API di file è limitato alla **var**, **sftp** e cartelle temporanee di Adobe Campaign.

Per i clienti esistenti, le API dei file non possono più accedere al **conf** cartella di Adobe Campaign. La **XtkSecurity_Disable_JSFileSandboxing** l’opzione di compatibilità viene aggiunta dall’aggiornamento successivo e attivata per impostazione predefinita, consentendo di continuare ad accedere alle altre cartelle. Se desideri limitare l’accesso al **var**, **sftp** e cartelle temporanee di Adobe Campaign, disattiva l’opzione .

**Patch**

* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)

## Versione 18.4

### Versione 18.4.5 - Build 8937{#release-18-4-5-build-8937}

21 novembre 2018

**Miglioramenti**

* Sono stati risolti diversi problemi durante l’esecuzione di flussi di lavoro tramite MySQL su FDA. (NEO-11652)
* È stato risolto un problema a causa del quale, in casi specifici, una parte della popolazione di consegna rimaneva in sospeso. (NEO-11336)
* È stato risolto un problema intermittente relativo alla risposta automatica SMS. (NEO-11811)
* È stato risolto un problema di esaurimento ID quando si utilizzavano gli indirizzi di seed in una consegna. (NEO-11842)
* È stato corretto un errore di sintassi durante l’esecuzione di un ordinamento in un’attività del flusso di lavoro di arricchimento. (NEO-11394)
* È stato risolto un problema che poteva causare un arresto anomalo del server Web al riavvio di IIS. (NEO-10862)
* È stato risolto un problema che poteva causare un errore del flusso di lavoro di tracciamento dopo un aggiornamento della build (FDA - SQL). (NEO-11635)
* È stato risolto un problema che poteva causare la perdita dei dati dell’elenco dei flussi di lavoro. (NEO-11696)
* È stato risolto un problema di prestazioni durante l’invio di notifiche push. (NEO-11787)
* È stato risolto un problema che impediva il funzionamento del web tracking per i domini &quot;com.au&quot; (NEO-4385).
* È stato risolto un problema di blocco del client che poteva verificarsi durante l’utilizzo di flussi di lavoro complessi. (NEO-11847)
* È stato corretto un errore di Oracle durante il salvataggio di una nuova consegna dopo la selezione di un elemento di uno schema specifico (NEO-11682).
* È stato risolto un problema che si verificava durante l’esecuzione di una query in un campo contenente caratteri con accenti (FDA/Teradata). L’account esterno ora consente di modificare la codifica utilizzata per comunicare con il driver di Teradata. (NEO-11818).
* È stato risolto un problema di tracciamento che si verificava quando si trasmettevano URL in variabili aggiuntive in una notifica push e che poteva causare la ricezione di dati non corretti o formattati dall’app mobile. (NEO-11468, NEO-11960)
* È stato risolto un problema che causava un problema di visualizzazione quando si utilizza una distribuzione di valori con un collegamento 1:N. (NEO-11820)
* È stato risolto un problema che impediva il funzionamento del carico di massa sulle Teradate 16.
* È stata aumentata la dimensione del buffer per la marca temporale sulle Teradate per evitare problemi di associazione con il driver 15.10.
* È stata migliorata la gestione degli indici dei nomi lunghi che potrebbero causare problemi dopo l&#39;aggiornamento.
* È stato migliorato il tempo disponibile per la memoria condivisa durante l’elaborazione dei dati MTA (Children Dead Processing).
* È stato corretto un potenziale deadlock in Apache (tracciamento).


### Versione 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1o agosto 2018

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati, il che rende più semplice e chiaro il controllo delle e-mail consegnate correttamente o non riuscite tramite l’archiviazione CCN. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del load balancer invece degli IP dei clienti nei log di monitoraggio dei broadcaster. (NEO-11295)
* È stato corretto un errore di codifica LATIN1 durante l’utilizzo di una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l&#39;utilizzo del **[!UICONTROL Prepare the personalization data with a workflow]** opzione di consegna. (NEO-11047, NEO-11301)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato risolto un problema che si verificava durante l’utilizzo dei campi calcolati in una **[!UICONTROL Survey answers]** attività del flusso di lavoro. (NEO-11382)
* È stato risolto un problema che si verificava durante l’utilizzo dei dati memorizzati in XML in un **[!UICONTROL Survey answers]** attività del flusso di lavoro. (NEO-10816)
* È stato risolto un problema che si verificava durante l’aggiornamento del server con la build 8935.
* È stato risolto un problema che mostrava errori inutili nel registro post-aggiornamento quando un **[!UICONTROL Survey answers]** attività del flusso di lavoro non configurata completamente.
* Teradata FDA: è stato risolto un problema relativo ai campi e agli indici con incremento automatico nelle tabelle SQL.

### Versione 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 giugno 2018

**Miglioramenti**

* È stato risolto un problema di codifica di tracking con Microsoft Edge e Internet Explorer. (NEO-11257)
* È stato risolto un problema relativo alla personalizzazione dei collegamenti alle immagini nelle consegne LINE. (NEO-11077)
* È stato risolto un problema che impediva il corretto funzionamento del meccanismo di generazione della sequenza ID. (NEO-11115)
* È stato risolto un problema che impediva il funzionamento delle richieste di privacy (RGPD) quando si utilizza uno spazio dei nomi personalizzato con una chiave di riconciliazione del tipo intero. (NEO-11123)
* È stato corretto un errore che poteva verificarsi durante l’utilizzo di **[!UICONTROL Distribution of values]** opzione in **[!UICONTROL Query]** attività del flusso di lavoro. (NEO-10958)
* È stato risolto un problema che si verificava durante la sincronizzazione degli spazi di offerta dall’istanza di marketing all’istanza di interazione. (NEO-11162)
* È stata migliorata la gestione degli indici dei nomi lunghi durante il post aggiornamento

### Versione 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 maggio 2018

**Miglioramenti**

* È stato risolto un problema che impediva il corretto funzionamento dell&#39;aggiornamento di Windows Server.
* È stato risolto un problema in **[!UICONTROL Survey Result]** quando si utilizzano i dati memorizzati in XML. Il rapporto non veniva visualizzato correttamente. (NEO-10816)
* È stato risolto un problema di prestazioni che poteva verificarsi con il processo inMail quando si utilizzava un server di posta non recapitata. (NEO-10641)
* È stato risolto un problema di aggiornamento del database che poteva verificarsi durante l’aggiornamento di più di 1000 schemi.

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
   <td> Regolamento generale sulla protezione dei dati (RGPD) dell'UE<br /> </td> 
   <td> <p>Il RGPD è la nuova legge sulla privacy dell’Unione europea (UE) che armonizza e modernizza i requisiti in materia di protezione dei dati in vigore dal 25 maggio 2018. Il GDPR si applica ai clienti di Adobe Campaign che conservano dati per soggetti che risiedono nell’Unione europea.</p> <p>Oltre alle funzionalità per la privacy già disponibili in Adobe Campaign (tra cui la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente), stiamo sfruttando questa opportunità nel nostro ruolo di Incaricato del trattamento dei dati per includere funzionalità aggiuntive, per aiutarti a essere pronto come Titolare del trattamento dei dati per alcune richieste RGPD:</p> 
    <ul> 
     <li> <p>Diritto di accesso: consente all’interessato di ricevere una copia dei propri dati personali acquisiti dai Titolari del trattamento dei dati, che potrebbero includere i dati archiviati in Adobe Campaign.</p> </li> 
     <li> <p>Diritto di cancellazione: concede all’interessato il diritto di cancellare i propri dati personali acquisiti dai Titolari del trattamento dei dati, potenzialmente inclusi i dati archiviati in Adobe Campaign.</p> </li> 
    </ul> Per ulteriori informazioni, consulta la <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">documentazione dettagliata</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Profili attivi<br /> </td> 
   <td> <p>Adobe Campaign fornisce ora l’elenco dei profili attivi, aggiornati mensilmente tramite un flusso di lavoro dedicato.</p> <p>Per ulteriori informazioni, consulta la <a href="../../platform/using/about-profiles.md#active-profiles">documentazione dettagliata</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Miglioramento del connettore push Android<br /> </td> 
   <td> <p>Il connettore Android è stato migliorato per supportare una maggiore velocità effettiva. </p> <p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/configuring-the-mobile-application.md">documentazione dettagliata</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* L’espansione delle entità esterne è ora disabilitata per impedire potenziali attacchi da parte di utenti non autenticati. (NEO-10173)
* Autorizzazioni estese per impedire agli utenti standard di modificare i parametri di configurazione dell&#39;istanza come URL di accesso all&#39;applicazione, impostazioni LDAP, ecc. (NEO-10171)
* È stato risolto un problema che poteva rivelare informazioni sensibili tramite tracce di stack. I dettagli dell’errore vengono ora registrati nel back-end in una posizione non accessibile dalla rete esterna. (NEO-10176)
* Autorizzazioni estese per impedire agli utenti standard di visualizzare i documenti caricati e/o i pacchetti esportati di un amministratore. (NEO-10170)

**Miglioramenti**

* **Canale LINE - miglioramento dell&#39;architettura**: Come per tutti gli altri canali in Adobe Campaign, il canale LINE è ora supportato in tutti i tipi di distribuzione: in hosting, ibrido e on-premise.
* **Generazione automatica della sequenza**: Il meccanismo di generazione ID è stato migliorato per aumentare la durata delle istanze Campaign con grandi volumi di oggetti. Per ulteriori informazioni, consulta [nota tecnica](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html).

**Altre modifiche**

* È disponibile una nuova modalità per l’importazione dei pacchetti utilizzando la riga di comando, che consente le dipendenze circolari (non consigliata per i pacchetti di grandi dimensioni). Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot; . (NEO-8979)
* Sono state migliorate le prestazioni per il caricamento di grandi quantità di dati nelle Teradate e sono stati risolti un problema che impediva la visualizzazione del valore corretto dei dati elaborati nel registro. (NEO-10429)
* L’importazione di tipi di pubblico da Audience Manager ora funziona con file suddivisi. In precedenza, solo l’ultimo file del segmento veniva importato dal flusso di lavoro tecnico importSharedAudience . (NEO-10156)
* In Windows, il percorso di installazione predefinito del server Campaign è stato modificato. Quando si avvia la configurazione della versione a 64 bit, il percorso di installazione predefinito è ora: **C:\Program Files\Adobe\Adobe Campaign Classic v7** anziché **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* Le regole MX predefinite sono state migliorate per includere più domini e ottimizzare il throughput.
* Sono state applicate restrizioni di accesso alla chiamata SOAP della procedura guidata di distribuzione (xtk:serverOptions#SaveOptions).
* La libreria obsoleta weka.jar è stata rimossa e la libreria OpenSSL è stata aggiornata per l’ottimizzazione della sicurezza.
* È stato migliorato il flusso di lavoro tecnico di fatturazione per proteggere le prestazioni delle istanze.
* È stata ripristinata la possibilità per gli amministratori di impostare o reimpostare la password di qualsiasi operatore. A questo scopo, fai clic con il pulsante destro del mouse su un operatore e seleziona **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e impostare la nuova password dell&#39;operatore. È consigliato agli operatori di modificare la password al primo riconnettersi. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../production/using/lost-password.md).
* Per supportare la nuova funzione multitenancy in Adobe Target, è ora possibile aggiungere agli URL un nuovo parametro &quot;at_property&quot; durante la configurazione di opzioni e account esterni per l’integrazione con Target. Il valore da utilizzare per questo parametro può essere trovato in Adobe Target e verrà utilizzato da Campaign quando si eseguono chiamate a Target. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* È ora possibile specificare una pagina di destinazione predefinita da aprire quando si fa clic su un’immagine trasmessa da Adobe Target. Precedentemente, quando si faceva clic su tale immagine, veniva visualizzato il set di immagini predefinito al momento della creazione del messaggio e-mail. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* Aggiunto **Abilita tracce SMPP** nell&#39;account esterno per forzare l&#39;output delle tracce. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Evoluzioni tecniche**

queryDef

queryDef è stato modificato per quanto riguarda la clausola &quot;orderBy&quot;. Prima della modifica, la chiave primaria della tabella interrogata verrebbe implicitamente aggiunta alle clausole &quot;orderBy&quot;. Su alcuni motori di database (almeno postgresql), impedisce l&#39;uso di indici (tutti i campi della clausola orderBy devono essere coperti dallo stesso indice). Se sei stato dipendente da questo comportamento, dovrai aggiungere esplicitamente la chiave primaria nella clausola &quot;orderBy&quot;.

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

Viene implicitamente consegnato come (prima delle modifiche alla versione 18.4):

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

La funzione JavaScript &#39;urlEncode&#39; non funzionava correttamente per i caratteri non ASCII. È stato corretto e ora deve funzionare con tutti i caratteri Unicode (inclusi i caratteri giapponesi). Se si fa affidamento sul comportamento &quot;urlEncode&quot; per i caratteri non ASCII, sarà necessario adattare il codice.

Importazione pacchetto - nuova modalità

È disponibile una nuova modalità per l’importazione dei pacchetti utilizzando la riga di comando, che consente le dipendenze circolari (non consigliata per i pacchetti di grandi dimensioni). La funzionalità esistente viene mantenuta. Per tali pacchetti con dipendenze circolari, un nuovo flag **-usejs** è stato aggiunto all’importazione del pacchetto della riga di comando. Una volta eseguito, utilizzerà il motore JSEngine come quando l&#39;importazione del pacchetto viene eseguita dall&#39;interfaccia.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patch**

* È stato risolto un problema di sincronizzazione durante la replica dei registri di consegna e tracciamento da Adobe Campaign Standard a Adobe Campaign Classic. (NEO-10023)
* È stato risolto un problema relativo alla gestione delle tabelle Error e Log in Teradata quando si riprendeva un flusso di lavoro ETL dopo un errore in un’operazione di caricamento rapido. Le tabelle Error e Log vengono ora eliminate correttamente ogni volta che il flusso di lavoro riprende. (NEO-10672)
* È stato risolto un problema di post aggiornamento per installare automaticamente il pacchetto Hive (necessario per il Hadoop) se il pacchetto FDA è installato. (NEO-10592)
* È stato corretto un errore a causa del quale i domini non validi venivano trattati come **Non definito** errore. (NEO-10248)
* È stato risolto un problema che duplicava i registri nella tabella deliveryLogStats durante l’invio di consegne push android. (NEO-10234)
* È stato risolto un problema che poteva causare la mancata lettura di alcuni formati di codice a barre da parte degli scanner di codice a barre. (NEO-10125)
* È stato risolto un problema relativo alla funzione JavaScript &#39;urlEncode&#39; quando si utilizzano caratteri non ASCII. Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot; . (NEO-10123)
* È stato risolto un problema che si verificava durante l’esecuzione di una query con funzioni sha256 sui database di Teradata. (NEO-10119)
* Correzione degli errori di memoria del flusso di lavoro che possono verificarsi nell&#39;attività SalesForce quando si utilizzano tabelle SalesForce molto grandi. (NEO-9900)
* È stato risolto un problema relativo alla **Genera complemento** in attività di targeting del flusso di lavoro quando si utilizza l’FDA. (NEO-9878)
* È stato risolto un problema che poteva portare al **Elaborato** e **Completato** le metriche non vengono aggiornate nell’istanza di marketing quando si utilizza il mid-sourcing. (NEO-9454)
* Sono state corrette le regole di non riproposta per l’interazione quando nella piattaforma sono presenti più di 10.000 offerte in totale (NEO-9352)
* È stato risolto un problema che poteva impedire di specificare la destinazione di una consegna quando si utilizzava un file esterno XML. (NEO-9312)
* È stato risolto un problema che poteva causare errori nel flusso di lavoro durante l’esecuzione di un’ipotesi su un’offerta e l’aggiornamento dello stato della proposta. (NEO-9304)
* Sono stati corretti gli errori che si verificavano durante l’analisi della consegna quando si utilizzavano regole di pressione basate su un attributo della mappatura della consegna Android. (NEO-9202)
* È stato risolto un problema che poteva causare problemi di prestazioni durante l’ordinamento delle colonne nell’elenco dei destinatari. Per ulteriori informazioni sulle modifiche queryDef, consulta la sezione &quot;Evoluzioni tecniche&quot; di seguito. (NEO-9042)
* È stato risolto un problema a causa del quale i collegamenti in un messaggio e-mail di approvazione potevano puntare a un URL di accesso errato, soprattutto quando si utilizzava un tipo di accesso di Federated ID. (NEO-9011)
* È stato risolto un problema che poteva causare la visualizzazione di date errate nei selettori di date dei rapporti per alcuni blocchi temporali. (NEO-9007)
* È stato risolto un problema che impediva la visualizzazione della destinazione di un uscita quando si utilizzava un database SQL FDA. (NEO-8924)
* È stato risolto un problema che impediva al connettore MS Dynamics CRM di estrarre i dati per i primi 7 giorni del mese. (NEO-8803)
* È stato corretto un errore nell’integrazione di Analytics che impediva agli utenti di includere caratteri internazionali. (NEO-8719)
* È stato risolto un problema che poteva abilitare la modifica del flusso di lavoro senza i diritti appropriati. (NEO-8708)
* È stato risolto un problema relativo a FDA su HTTP quando si utilizzava Message Center (Centro messaggi) in un’architettura ibrida, che causava il rilascio o la perdita di connessione (timeout). (NEO-8438)
* Sono stati corretti gli errori del flusso di lavoro che si verificavano nell’attività di query incrementale per gli ID negativi. (NEO-8229)
* È stato risolto un problema che poteva causare la visualizzazione di barre di scorrimento doppie in alcune schermate. (NEO-8208)
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore durante l&#39;esecuzione della procedura guidata di aggiornamento della struttura del database. Il PostUpgrade eseguirà una ridenominazione degli indici con nomi superiori a 30. Tieni presente che per le tabelle di grandi dimensioni, la sostituzione dell’indice richiederà del tempo. (NEO-7983)
* È stato risolto un problema a causa del quale i registri di tracciamento non venivano sincronizzati correttamente dall’istanza di esecuzione del Centro messaggi all’istanza di controllo dell’istanza. (NEO-7286)
* È stato risolto un problema di prestazioni relativo all’attività di arricchimento dell’offerta. (NEO-7263)
* È stato risolto un problema che impediva l&#39;utilizzo della funzione DaysAgo durante l&#39;esecuzione di query su un database Redshift tramite FDA. (NEO-7099)
* È stata corretta una regressione nella gestione dei dati che impediva la creazione di indici sulle attività del flusso di lavoro simili a Enrichment.
* È stato risolto un problema che poteva verificarsi durante la creazione di risorse esterne con il titolo @id
* È stato risolto un problema che poteva verificarsi durante il caricamento di file ZIP tramite un server FTP o durante il caricamento di file con caratteri jolly nel nome file.
* È stato risolto un problema relativo alle enumerazioni di tipi di base lunghi nelle risorse personalizzate esterne create in Campaign Standard.
* È stato risolto un problema che poteva causare l’invio di SMS anche quando la connessione con il provider non andava a buon fine e causava perdite di SMS.
* È stato corretto un errore che causava il blocco indefinito di una connessione SMTP.
* È stato risolto un problema relativo alle regole di tipologia della pressione durante la preparazione dei messaggi quando si utilizza una mappatura LINE o quando gli schemi di filtro e targeting sono diversi.
