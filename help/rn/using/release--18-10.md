---
title: Versione 18.10
seo-title: Versione 18.10
description: Versione 18.10
seo-description: null
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
source-wordcount: '2371'
ht-degree: 8%

---


# Versione 18.10{#release-18-10}

## Versione 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 luglio 2019

**Miglioramenti**

* È ora possibile eliminare i record fittizi creati in Microsoft Dynamics durante il flusso di lavoro di importazione.
* È stato risolto un problema relativo all&#39;attività del flusso di lavoro Raccolta file che poteva registrare gli errori in loop quando l&#39;accesso a un file veniva negato. (NEO-12085)
* È stato risolto un problema che causava discrepanze tra le attività degli utenti e i rapporti di tracciamento per l&#39;indicatore di consegna aperto. (NEO-11742)
* Sono state migliorate le autorizzazioni per eseguire il pacchetto della zona di sicurezza quando si utilizza un account interno.
* È stato risolto un problema che poteva causare errori nei registri secondari principali. (NEO-8978)

## Versione 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 aprile 2019

**Miglioramenti**

* È stato risolto un problema di blocco critico SQL che causava un errore di analisi del recapito in caso di analisi/invio simultanei (quando due consegne venivano analizzate contemporaneamente). (NEO-13026)
* È stato rimosso il limite di 10.000 record nella mappa di calore del flusso di lavoro per risolvere un problema di dati mancante. (NEO-12329)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;opzione &quot;Conserva tutti i dati aggiuntivi dal set principale&quot; in un&#39;attività del flusso di lavoro di arricchimento. (NEO-13291)

## Versione 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 aprile 2019

**Miglioramenti**

* È stato risolto un problema relativo al processo di elaborazione degli indicatori di tracciamento per i messaggi transazionali. (NEO-12529, NEO-12581)
* È stato risolto un problema con l’API HTTPRequest che non aspettava il completamento di tutte le callback. (NEO-12628)
* Sono stati aggiunti indici nelle tabelle temporanee dei coupon per ottimizzare l&#39;invio delle consegne. (NEO-12437)
* È stato risolto un problema durante l&#39;analisi di un messaggio che determinava il targeting dei destinatari per i domini giapponesi (.JP). (NEO-12246)
* Nell&#39;integrazione di Analytics, è ora consentito il recupero di dati AAM segmento con carattere %. (NEO-12025)
* È stato corretto un problema di arresto anomalo Tomcat durante l&#39;invio delle notifiche push tramite HTTP2. (NEO-12701)

## Versione 18.10.3 - Build 8981{#release-18-10-3-build-8981}

29 gennaio 2019

>[!CAUTION]
>
>Questa costruzione è stata richiamata. Effettuare l&#39; [aggiornamento alla build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) più recente o contattare il supporto [](https://support.neolane.net/)tecnico.

**Miglioramenti**

* È stato risolto un problema relativo all&#39;attività del flusso di lavoro di trasferimento file s3. (NEO-12473)
* È stato risolto un problema con il flusso di lavoro di tracciamento che poteva non riuscire. (NEO-12520)
* È stato risolto un problema relativo all&#39;accesso IMS.
* È stato risolto un problema relativo all&#39;approvazione dell&#39;anteprima e del contenuto nei messaggi transazionali quando si utilizza un ID offerta grande.
* È stato risolto un problema con il flusso di lavoro di origine intermedia (contatori di consegna).
* È stato risolto un problema con l&#39;aggiornamento della struttura del database che causava l&#39;eliminazione di nuovi indici su NmsRecipient.
* È stato corretto un arresto anomalo della console che poteva verificarsi quando si utilizzava l&#39;opzione Definito in un file esterno per la destinazione principale di una consegna. (NEO-12349)
* Sono stati corretti diversi arresti anomali di InMail.
* È stato risolto un problema che si verificava durante l&#39;utilizzo di un&#39;attività del flusso di lavoro Aggiorna dati per eliminare i record memorizzati in un database FDA Teradata.
* Risolti problemi di incoerenza nella gestione delle chiavi segrete.
* È stato risolto un problema relativo all&#39;attività di arricchimento durante la digitazione di un campo come: xml=true e calculate=true
* È stato risolto un problema di escape dei caratteri durante l&#39;invio di notifiche push in un&#39;applicazione mobile.
* È stato risolto un problema che impediva il passaggio da FDA a metodo di sincronizzazione SOAP in un account esterno di Media Sourcing.

## Versione 18.10.2 - Build 8978{#release-18-10-2-build-8978}

6 dicembre 2018

>[!CAUTION]
>
>Questa costruzione è stata richiamata. Effettuare l&#39; [aggiornamento alla build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) più recente o contattare il supporto [](https://support.neolane.net/)tecnico.

**Miglioramenti**

* Sono stati risolti diversi problemi durante l&#39;esecuzione di flussi di lavoro che utilizzano MySQL su FDA. (NEO-11652)
* È stato risolto un problema di prestazioni durante l&#39;invio delle notifiche push. (NEO-11787)
* È stato risolto un problema di esaurimento ID quando si utilizzavano gli indirizzi iniziali in una consegna. (NEO-11842)
* È stato corretto un problema di blocco dei client che poteva verificarsi quando si utilizzavano flussi di lavoro complessi. (NEO-11847)
* È stato corretto un problema di visualizzazione quando si utilizzava una distribuzione di valori con un collegamento 1:N. (NEO-11820)
* È stato corretto un errore Oracle in Worflow Heatmap.
* È stato risolto un problema corretto quando si aggiungeva una proposta di offerta in un&#39;attività di arricchimento.
* È stato risolto un problema di connessione di gestione dati SQL.
* È stato risolto un problema con la generazione di nomi di tabella del flusso di lavoro temporaneo in caso di ID negativi.
* È stato risolto un problema con il calcolo delle durate del flusso di lavoro in Workflow HeatMap.


## Versione 18.10 - Build 8977{#release-18-10-build-8977}

5 nov 2018

>[!CAUTION]
>
>Questa costruzione è stata richiamata. Effettuare l&#39; [aggiornamento alla build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) più recente o contattare il supporto [](https://support.neolane.net/)tecnico.

**Novità?**

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
   <td> Sono stati implementati diversi miglioramenti per le notifiche push in  Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Tenere traccia delle notifiche silenziose in iOS </p> </li> 
     <li> <p>Implementare il feedback sulle chiamate di registrazione in iOS</p> </li> 
     <li> <p>Miglioramento della velocità di preparazione della distribuzione iOS</p> </li> 
    </ul> <p>Come parte dell'ammortamento GCM di Google, il connettore Android V2 ora consente le connessioni solo al server FCM.</p><p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentazione dettagliata</a>. L'aggiornamento manuale a FCM è dettagliato in questo <a href="https://helpx.adobe.com/it/campaign/kb/migrate-to-fcm.html">articolo</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> Attività di gestione dati SQL<br /> </td> 
   <td> <p>È stata aggiunta una nuova attività del flusso di lavoro di gestione dei dati. L'attività <strong>SQL Data Management</strong> consente di scrivere o copiare/incollare script SQL personalizzati per creare e compilare tabelle di lavoro (solo FDA). </p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/sql-data-management.md">documentazione dettagliata</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Monitoraggio del flusso di lavoro<br /> </td> 
   <td> <p>Con la nuova  Adobe Campaign Workflow HeatMap, gli amministratori della piattaforma dispongono di una rapida rappresentazione grafica di tutti i flussi di lavoro simultanei, che consente loro di monitorare il carico sull'istanza e pianificare i flussi di lavoro di conseguenza.</p> <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/heatmap.md">documentazione dettagliata</a>.</p> <p>Il pacchetto HeatMap del flusso di lavoro è disponibile anche su richiesta per le build precedenti alla 8977 (avvio build 8700). Per ulteriori informazioni sulla richiesta e l’installazione, consultare <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">questa pagina</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* È stato risolto un problema di sicurezza che poteva causare vulnerabilità agli attacchi SSRF (Server Side Request Forgery) e attacchi DoS (Denial of Service). (NEO-11453)
* Contenuto (reindirizzamento tracciamento, pagine mirror, sondaggi, ecc.) ora verrà servito da Campaign con il tag X-Robots: nocache header. Ciò impedisce l&#39;indicizzazione di questo contenuto da parte dei motori di ricerca Internet. (NEO-11101)
* È stato risolto un problema di iniezione XTK nell&#39;API di iscrizione (nms:subscription:Unsubscription e nms:subscription:Subscribe).
* È stato risolto un problema di iniezione XTK nell’applicazione Web di annullamento della sottoscrizione.
* Sono state rimosse le password che venivano visualizzate in modo invisibile in alcuni log SMS.

**Miglioramenti**

* Le API di Campaign Classic sono ora disponibili in una [pagina dedicata](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Se stavi utilizzando il file jsapi.chm, ora devi fare riferimento alla nuova versione online.
* PostgreSQL 10, Debian 9 e Teradata 16.20 ora sono supportati. Consulta la [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html).
* Quando si crea una connessione SFTP, ora è possibile utilizzare l&#39;autenticazione proxy. For more information, refer to the [detailed documentation](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) (NEO-9868)
* L&#39;opzione di formula **di calcolo della** data è ora disponibile nelle proprietà di consegna quando si crea un singolo recapito utilizzando il modello di consegna diretta per posta. (NEO-9792)
* La gestione dei nomi di dominio è stata migliorata per il tracciamento dei cookie e per le applicazioni Web. Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot; di seguito.
* L&#39;importazione di risorse condivise Adobe Marketing Cloud in una pagina di consegna o di destinazione è stata migliorata in termini di sicurezza e prestazioni.
* Una nuova casella di controllo è disponibile nell&#39;account esterno del canale Mobile per abilitare tracce SMPP dettagliate nel file di registro, che rende questo output direttamente accessibile dall&#39;interfaccia Adobe Campaign .
* Nei log di trasmissione, ora esiste una distinzione tra il numero massimo di connessioni e il numero massimo di messaggi per ora. Una volta raggiunti i limiti, è possibile sapere perché il throughput è limitato. In precedenza, lo stesso messaggio (&quot;quota soddisfatta&quot;) era applicato a entrambi i casi.
* È ora possibile specificare uno script SQL da eseguire quando si acquisisce una connessione dal pool. Questo script può essere utilizzato per impostare lo schema predefinito. Questo script verrà applicato dopo l&#39;esecuzione della bendatura della query. (NEO-11256)
* Campaign SDK non memorizza più l&#39;ID utente per conformarsi alle nostre normative PII. I dati ora vengono memorizzati come hash.
* Quando si importa un file XML di esportazione del pacchetto, Campaign ora supporta la presenza di BOM nel file, anche se la codifica è dichiarata esplicitamente in esso.

**Evoluzioni tecniche**

Aggiornamento client e server

>[!CAUTION]
>
>Se disponete di un server aggiornato alla versione 18.10, per accedere al server dovrete utilizzare un client 18.10. Il client 18.10 sarà in grado di connettersi a una versione server precedente.

Gestione dei nomi di dominio

La gestione dei nomi di dominio è stata migliorata per il tracciamento dei cookie e per le applicazioni Web.

Ora, tutti i nomi di dominio di secondo livello di due lettere sono supportati per impostazione predefinita (ad esempio .aa.com). Per nomi di dominio più complessi (ad esempio domini di secondo livello di tre lettere come .com.au), è necessario aggiungerli nell&#39;opzione **cookieDomains** di serverConf (sotto il tag di reindirizzamento). Esempio:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Miglioramenti dell&#39;indice

Gli indici su NmsRecipient sono stati rielaborati. Ciò dovrebbe migliorare le prestazioni sulle query che utilizzano questa tabella. Se è stata eseguita un&#39;estensione di NmsRecipient, è possibile verificare che non siano presenti indici che duplicano i nuovi indici (per ridurre al minimo l&#39;utilizzo di spazio nel server di database). (NEO-8228)

In PostgreSql, quando si utilizza un confronto UTF-8, è ora possibile creare indici che ottimizzino le operazioni &quot;LIKE &#39;string%&#39; (o &quot;Inizia con&quot;). Se si eseguono altre operazioni sulla stessa colonna (ad esempio, ordine in base a o unione), sarà necessario un altro indice standard. Dal lato dello schema, questo verrà fatto aggiungendo indexOption=&quot;searchFromStart&quot; nella definizione dell&#39;indice (creerà un indice varchar_pattern_ops invece di un indice della struttura ad albero standard). Ad esempio (su NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Sono stati aggiunti nuovi indici a NmsRtEvent e NmsEventHisto (nella colonna &quot;Pianificato&quot;), per migliorare il tempo di visualizzazione sul modulo corrispondente (NEO-11738).

Queste modifiche all&#39;indice potrebbero determinare un aumento del tempo necessario per eseguire l&#39;aggiornamento successivo.

**Patch**

* È stato corretto un errore che impediva il download dei file dall&#39;attività del flusso di lavoro di download **** Web. (NEO-11105)
* È stato corretto un errore che a volte lasciava il flusso di lavoro **Invio di indicatori e attributi** della campagna in uno stato Non riuscito (NEO-10820).
* È stato risolto un problema che eliminava l&#39;elenco dei destinatari creato dopo l&#39;esecuzione dell&#39;attività di aggiornamento Elenco in un flusso di lavoro. (NEO-11696)
* È stato risolto un problema che causava erroneamente la visualizzazione delle campagne un mese prima nel calendario Campaign (su un&#39;istanza giapponese). (NEO-11445)
* È stato risolto un problema che impediva la visualizzazione della configurazione di Analytics nella scheda Analisi Web delle proprietà di consegna. (NEO-11619)
* È stato corretto un errore visualizzato quando si tentava di modificare e salvare il modulo di input nms:delivery. (NEO-10973)
* È stato risolto un problema di configurazione dell&#39;account esterno che si verificava durante l&#39;esecuzione di un flusso di lavoro contenente un&#39;attività di trasferimento file. (NEO-11012)
* È stato risolto un problema che causava la restituzione di righe vuote quando si utilizzava la funzione zcat per caricare i file nell&#39;attività di caricamento dei dati. (NEO-11273)
* È stato risolto un problema che generava registri ampi duplicati durante l&#39;analisi della consegna. (NEO-11360)
* È stato risolto un problema che causava un errore di consegna a causa di una chiave di collegamento esterna mancante dopo l&#39;esecuzione dell&#39;attività di arricchimento in un flusso di lavoro. (NEO-11537)
* È stato risolto un problema che impediva la corretta disinstallazione o riparazione di  Adobe Campaign quando il percorso di installazione includeva caratteri cinesi GB18030 specifici.
* È stato risolto un problema che collegava alcuni registri di monitoraggio alla consegna errata. (NEO-11412)
* È stato risolto un problema che poteva causare la permanenza di alcune parti dei log di consegna con stato in sospeso maggiore del previsto. (NEO-11336)
* È stato corretto un errore che si verificava durante la modifica di una query per aggiungere un coupon a una consegna. (NEO-11037)
* È stato risolto un problema nei report che faceva in modo che i grafici calcolassero sempre la somma dei valori indipendentemente dall&#39;operatore aggregato selezionato. (NEO-10913)
* Poiché la funzione &quot;request.Scheme&quot; è obsoleta, è stata rimossa dalla documentazione JSAPI. (NEO-10828)
* È stato risolto un problema che impediva ad alcuni utenti con specifiche configurazioni di fuso orario di accedere a  Adobe Campaign. (NEO-10712)
* È stato risolto un problema che si verificava durante la configurazione di un account esterno di un canale mobile utilizzando il connettore SMPP generico esteso: se si specificavano parametri diversi per il ricevitore, il trasmettitore utilizzava erroneamente questi parametri invece dei propri.
* È stato risolto un problema che causava il fallimento delle consegne programmate durante l&#39;impostazione di una frequenza per la regola di pressione, in quanto le consegne venivano continuamente ricalcolate dopo il primo arbitrato. (NEO-10016)
* È stato risolto un problema che causava l&#39;arresto anomalo del server Web IIS durante il processo di riciclo del pool di applicazioni (nella libreria nlsrvmod.dll). (NEO-10862)
* È stato risolto un problema che poteva impedire la ricerca di un destinatario nella schermata **Profili e Target** . (NEO-8228)
* È stato risolto un problema che poteva causare un errore di timeout durante l&#39;accesso alla cartella Cronologia eventi nel caso di un numero elevato di record. (NEO-11738)
* È stato risolto un problema che poteva causare la restituzione errata dei destinatari della distribuzione LINE come &quot;Non raggiungibile&quot;. (NEO-10833)
* È stato risolto un problema che si verificava durante l&#39;esecuzione di una query del flusso di lavoro con una colonna aggiuntiva in Oracle. (NEO-11615)
* È stato migliorato il sistema per garantire che le connessioni chiuse non vengano mantenute nel pool di connessioni troppo a lungo. (NEO-11392)
* È stato risolto un problema che si verificava durante l&#39;utilizzo di un&#39;attività del flusso di lavoro di targeting (query, caricamento dei dati (RDBMS), ecc.) collegato tramite FDA a una tabella Oracle esterna che conteneva caratteri UTF8 (nel nome della tabella, nel nome del campo, ecc.) e che conteneva anche un vincolo di chiave primaria con un nome di vincolo predefinito generato dal sistema. (NEO-10714)
* È stato risolto un problema che poteva impedire l&#39;eliminazione del contenuto HTML di una consegna. (NEO-11327)
* È stato risolto un problema relativo all&#39;anteprima dei file XML e CSV in un messaggio di posta diretta dopo l&#39;esecuzione di una campagna. (NEO-11290)
* È stato risolto un problema che si verificava durante l&#39;ordinamento dei dati in un&#39;attività di flusso di lavoro di arricchimento. (NEO-11394)
* È stato risolto un problema durante l&#39;ordinamento dei dati in un report personalizzato. (NEO-10896)
* È stato risolto un problema che causava errori durante l&#39;utilizzo dell&#39;impostazione useVault con Teradata. (NEO-11399)
* È stato risolto un problema che causava l&#39;arresto anomalo della console client Adobe Campaign  durante l&#39;eliminazione di più righe di query. (NEO-10744)
* È stato risolto un problema che impediva l&#39;applicazione delle regole di pressione in alcuni casi durante la consegna della posta diretta. (NEO-9004)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;attività di caricamento dei dati per importare una colonna con il tipo di dati &quot;ora&quot;: il separatore di tempo viene reimpostato anche dopo la rimozione. (NEO-10743)
* È stato risolto un problema che impediva la visualizzazione della cartella Consegne dall&#39;elenco delle cartelle Esecuzione nelle proprietà Consegna durante la modifica di un recapito periodico. (NEO-11094)
* È stato risolto un problema che impediva alla finestra Visualizza popolazione di visualizzare più di 200 record come destinazione risultante di un&#39;attività Query in un flusso di lavoro. (NEO-11195)
* È stato risolto un problema in Oracle che impediva l&#39;esecuzione di una query DELETE con più di 1000 elementi selezionati. (NEO-11171)
* È stato risolto un problema che causava la codifica degli URL come URL tracciati nei parametri aggiuntivi di una notifica push Android. (NEO-11468)
* È stato corretto un errore di script che si verificava nel report Attività utente quando si impostavano i parametri su &quot;Intervalli di un giorno&quot; e &quot;Apre&quot;. (NEO-11655)
* È stato risolto un problema che si verificava durante la connessione al server di mid-sourcing o al Centro messaggi tramite un proxy Web autenticato. (NEO-11309)
* È stato corretto un errore Oracle che si verificava durante il salvataggio di una nuova composizione di consegna dopo la selezione di un elemento di uno schema specifico **basato su una vista** SQL. (NEO-11682)
* È stato risolto un problema che causava la generazione di file di rifiuto contenenti falsi positivi durante l&#39;elaborazione di un file zip contenente un .csv tramite un&#39;attività di caricamento tramite l&#39;opzione Decompressione.
* xtkjoblog è ora eliminato dalla pulizia.

