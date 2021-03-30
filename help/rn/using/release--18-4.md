---
solution: Campaign Classic
product: campaign
title: Note sulla versione 18.4 di Campaign
description: Note sulla versione per Campaign 18.4
feature: null
role: null
level: null
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 7%

---


# Versione 18.4{#release-18-4}

## Versione 18.4.5 - Build 8937{#release-18-4-5-build-8937}

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

## Versione 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1o agosto 2018

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati, il che rende più semplice e chiaro il controllo delle e-mail consegnate correttamente o non riuscite tramite l’archiviazione CCN. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del load balancer invece degli IP dei clienti nei log di monitoraggio dei broadcaster. (NEO-11295)
* È stato corretto un errore di codifica LATIN1 durante l’utilizzo di una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava quando si utilizzava l’opzione di consegna **[!UICONTROL Prepare the personalization data with a workflow]** . (NEO-11047, NEO-11301)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato risolto un problema che si verificava durante l’utilizzo dei campi calcolati in un’attività del flusso di lavoro **[!UICONTROL Survey answers]** . (NEO-11382)
* È stato risolto un problema che si verificava durante l’utilizzo dei dati memorizzati in XML in un’attività del flusso di lavoro **[!UICONTROL Survey answers]** . (NEO-10816)
* È stato risolto un problema che si verificava durante l’aggiornamento del server con la build 8935.
* È stato risolto un problema che mostrava errori inutili nel registro post-aggiornamento quando un’attività del flusso di lavoro **[!UICONTROL Survey answers]** non era completamente configurata.
* Teradata FDA: è stato risolto un problema relativo ai campi e agli indici con incremento automatico nelle tabelle SQL.

## Versione 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 giugno 2018

**Miglioramenti**

* È stato risolto un problema di codifica del tracking con Microsoft Edge e Internet Explorer. (NEO-11257)
* È stato risolto un problema relativo alla personalizzazione dei collegamenti alle immagini nelle consegne LINE. (NEO-11077)
* È stato risolto un problema che impediva il corretto funzionamento del meccanismo di generazione della sequenza ID. (NEO-11115)
* È stato risolto un problema che impediva il funzionamento delle richieste di privacy (RGPD) quando si utilizza uno spazio dei nomi personalizzato con una chiave di riconciliazione del tipo intero. (NEO-11123)
* È stato corretto un errore che poteva verificarsi durante l’utilizzo dell’opzione **[!UICONTROL Distribution of values]** nelle attività del flusso di lavoro **[!UICONTROL Query]** . (NEO-10958)
* È stato risolto un problema che si verificava durante la sincronizzazione degli spazi di offerta dall’istanza di marketing all’istanza di interazione. (NEO-11162)
* È stata migliorata la gestione degli indici dei nomi lunghi durante il post aggiornamento

## Versione 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 maggio 2018

**Miglioramenti**

* È stato risolto un problema che impediva il corretto funzionamento dell&#39;aggiornamento di Windows Server.
* È stato risolto un problema nell&#39;attività **[!UICONTROL Survey Result]** quando si utilizzano i dati memorizzati in XML. Il rapporto non veniva visualizzato correttamente. (NEO-10816)
* È stato risolto un problema di prestazioni che poteva verificarsi con il processo inMail quando si utilizzava un server di posta non recapitata. (NEO-10641)
* È stato risolto un problema di aggiornamento del database che poteva verificarsi durante l’aggiornamento di più di 1000 schemi.

## Versione 18.4 - Build 8931{#release-18-4-build-8931}

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
   <td> Regolamento generale UE sulla protezione dei dati (RGPD)<br /> </td> 
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

**Miglioramenti della sicurezza**

* L’espansione delle entità esterne è ora disabilitata per impedire potenziali attacchi da parte di utenti non autenticati. (NEO-10173)
* Autorizzazioni estese per impedire agli utenti standard di modificare i parametri di configurazione dell&#39;istanza come URL di accesso all&#39;applicazione, impostazioni LDAP, ecc. (NEO-10171)
* È stato risolto un problema che poteva rivelare informazioni sensibili tramite tracce di stack. I dettagli dell’errore vengono ora registrati nel back-end in una posizione non accessibile dalla rete esterna. (NEO-10176)
* Autorizzazioni estese per impedire agli utenti standard di visualizzare i documenti caricati e/o i pacchetti esportati di un amministratore. (NEO-10170)

**Miglioramenti**

* **Canale LINE - miglioramento** dell&#39;architettura: Come per tutti gli altri canali in Adobe Campaign, il canale LINE è ora supportato in tutti i tipi di distribuzione: in hosting, ibrido e on-premise.
* **Generazione** automatica della sequenza: Il meccanismo di generazione ID è stato migliorato per aumentare la durata delle istanze Campaign con grandi volumi di oggetti. Per ulteriori informazioni, consulta questa [nota tecnica](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html).

**Altre modifiche**

* È disponibile una nuova modalità per l’importazione dei pacchetti utilizzando la riga di comando, che consente le dipendenze circolari (non consigliata per i pacchetti di grandi dimensioni). Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot; . (NEO-8979)
* Sono state migliorate le prestazioni per il caricamento di grandi quantità di dati nelle Teradate e sono stati risolti un problema che impediva la visualizzazione del valore corretto dei dati elaborati nel registro. (NEO-10429)
* L’importazione di tipi di pubblico da Audience Manager ora funziona con file suddivisi. In precedenza, solo l’ultimo file del segmento veniva importato dal flusso di lavoro tecnico importSharedAudience . (NEO-10156)
* In Windows, il percorso di installazione predefinito del server Campaign è stato modificato. Quando si avvia la configurazione della versione a 64 bit, il percorso di installazione predefinito è ora: **C:\Program Files\Adobe\Adobe Campaign Classic v7** invece di **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* Le regole MX predefinite sono state migliorate per includere più domini e ottimizzare il throughput.
* Sono state applicate restrizioni di accesso alla chiamata SOAP della procedura guidata di distribuzione (xtk:serverOptions#SaveOptions).
* La libreria obsoleta weka.jar è stata rimossa e la libreria OpenSSL è stata aggiornata per l’ottimizzazione della sicurezza.
* È stato migliorato il flusso di lavoro tecnico di fatturazione per proteggere le prestazioni delle istanze.
* È stata ripristinata la possibilità per gli amministratori di impostare o reimpostare la password di qualsiasi operatore. A questo scopo, fai clic con il pulsante destro del mouse su un operatore, seleziona **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e imposta la nuova password dell’operatore. È consigliato agli operatori di modificare la password al primo riconnettersi. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../production/using/lost-password.md).
* Per supportare la nuova funzione multitenancy in Adobe Target, è ora possibile aggiungere agli URL un nuovo parametro &quot;at_property&quot; durante la configurazione di opzioni e account esterni per l’integrazione con Target. Il valore da utilizzare per questo parametro può essere trovato in Adobe Target e verrà utilizzato da Campaign quando si eseguono chiamate a Target. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* È ora possibile specificare una pagina di destinazione predefinita da aprire quando si fa clic su un’immagine trasmessa da Adobe Target. Precedentemente, quando si faceva clic su tale immagine, veniva visualizzato il set di immagini predefinito al momento della creazione del messaggio e-mail. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* Aggiunta della casella di controllo **Abilita tracce SMPP** nell&#39;account esterno per forzare l&#39;output delle tracce. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

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
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

funzione urlEncode

La funzione JavaScript &#39;urlEncode&#39; non funzionava correttamente per i caratteri non ASCII. È stato corretto e ora deve funzionare con tutti i caratteri Unicode (inclusi i caratteri giapponesi). Se si fa affidamento sul comportamento &quot;urlEncode&quot; per i caratteri non ASCII, sarà necessario adattare il codice.

Importazione pacchetto - nuova modalità

È disponibile una nuova modalità per l’importazione dei pacchetti utilizzando la riga di comando, che consente le dipendenze circolari (non consigliata per i pacchetti di grandi dimensioni). La funzionalità esistente viene mantenuta. Per tali pacchetti con dipendenze circolari, all’importazione del pacchetto della riga di comando è stato aggiunto un nuovo flag **-usejs**. Una volta eseguito, utilizzerà il motore JSEngine come quando l&#39;importazione del pacchetto viene eseguita dall&#39;interfaccia.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patch**

* È stato risolto un problema di sincronizzazione durante la replica dei registri di consegna e tracciamento da Adobe Campaign Standard a Adobe Campaign Classic. (NEO-10023)
* È stato risolto un problema relativo alla gestione delle tabelle Error e Log in Teradata quando si riprendeva un flusso di lavoro ETL dopo un errore in un’operazione di caricamento rapido. Le tabelle Error e Log vengono ora eliminate correttamente ogni volta che il flusso di lavoro riprende. (NEO-10672)
* È stato risolto un problema di post aggiornamento per installare automaticamente il pacchetto Hive (necessario per il Hadoop) se il pacchetto FDA è installato. (NEO-10592)
* È stato corretto un errore che trattava i domini non validi come errore **Non definito**. (NEO-10248)
* È stato risolto un problema che duplicava i registri nella tabella deliveryLogStats durante l’invio di consegne push android. (NEO-10234)
* È stato risolto un problema che poteva causare la mancata lettura di alcuni formati di codice a barre da parte degli scanner di codice a barre. (NEO-10125)
* È stato risolto un problema relativo alla funzione JavaScript &#39;urlEncode&#39; quando si utilizzano caratteri non ASCII. Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot; . (NEO-10123)
* È stato risolto un problema che si verificava durante l’esecuzione di una query con funzioni sha256 sui database di Teradata. (NEO-10119)
* Correzione degli errori di memoria del flusso di lavoro che possono verificarsi nell&#39;attività SalesForce quando si utilizzano tabelle SalesForce molto grandi. (NEO-9900)
* È stato risolto un problema con l’opzione **Genera complemento** nel targeting delle attività del flusso di lavoro quando si utilizza l’FDA. (NEO-9878)
* È stato risolto un problema che poteva causare il mancato aggiornamento delle metriche **Processed** e **Success** nell&#39;istanza di marketing quando si utilizza il mid-sourcing. (NEO-9454)
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
