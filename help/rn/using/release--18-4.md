---
title: Versione 18.4
seo-title: Versione 18.4
description: Versione 18.4
seo-description: null
page-status-flag: never-activated
uuid: d132570e-20e6-4550-95bd-176701f43b19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 4dc87ff3-eb6a-40ac-97ee-00b64cd7718d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2263'
ht-degree: 7%

---


# Versione 18.4{#release-18-4}

## Versione 18.4.5 - Build 8937{#release-18-4-5-build-8937}

21 novembre 2018

**Miglioramenti**

* Sono stati risolti diversi problemi durante l&#39;esecuzione di flussi di lavoro che utilizzano MySQL su FDA. (NEO-11652)
* È stato corretto un problema a causa del quale, in casi specifici, una parte della popolazione di distribuzione rimaneva in sospeso. (NEO-11336)
* È stato risolto un problema intermittente con la risposta automatica SMS. (NEO-11811)
* È stato risolto un problema di esaurimento ID quando si utilizzavano gli indirizzi iniziali in una consegna. (NEO-11842)
* È stato corretto un errore di sintassi durante l&#39;esecuzione di un ordinamento in un&#39;attività di flusso di lavoro di arricchimento. (NEO-11394)
* È stato risolto un problema che poteva causare un arresto anomalo del server Web al riavvio di IIS. (NEO-10862)
* È stato risolto un problema che poteva causare un errore nel flusso di lavoro di tracciamento dopo un aggiornamento della build (FDA - SQL). (NEO-11635)
* È stato risolto un problema che poteva causare la perdita dei dati dell&#39;elenco dei flussi di lavoro. (NEO-11696)
* È stato risolto un problema di prestazioni durante l&#39;invio delle notifiche push. (NEO-11787)
* È stato risolto un problema che impediva il monitoraggio Web per i domini &quot;com.au&quot; (NEO-4385).
* È stato corretto un problema di blocco dei client che poteva verificarsi quando si utilizzavano flussi di lavoro complessi. (NEO-11847)
* È stato corretto un errore Oracle durante il salvataggio di una nuova consegna dopo la selezione di un elemento di uno schema specifico (NEO-11682).
* È stato risolto un problema che si verificava durante la query in un campo contenente caratteri con accenti (FDA/Teradata). L&#39;account esterno ora consente di modificare la codifica utilizzata per comunicare con il driver Teradata. (NEO-11818).
* È stato risolto un problema di tracciamento durante il passaggio di URL in variabili aggiuntive in una notifica push che poteva causare la mancata formattazione o la mancata ricezione di dati non corretti da parte dell&#39;applicazione mobile. (NEO-11468, NEO-11960)
* È stato risolto un problema che causava un problema di visualizzazione quando si utilizzava una distribuzione di valori con un collegamento 1:N. (NEO-11820)
* È stato risolto un problema che impediva il funzionamento del carico di massa su Teradata 16.
* È stata aumentata la dimensione del buffer per la marca temporale su Teradata per evitare problemi di binding con il driver 15.10.
* È stata migliorata la gestione degli indici dei nomi lunghi che potrebbero causare problemi di postaggiornamento.
* È stato migliorato il tempo di memoria condivisa disponibile durante l&#39;elaborazione dei dati figlio (MTA).
* È stato corretto un potenziale blocco critico in Apache (tracciamento).

## Versione 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1o agosto 2018

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati, il che rende più semplice e chiaro verificare quali e-mail sono state distribuite correttamente o hanno avuto esito negativo attraverso l&#39;archiviazione CCN. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del sistema di bilanciamento del carico al posto degli IP dei clienti nei log di monitoraggio. (NEO-11295)
* È stato corretto un errore con codifica LATIN1 quando si utilizzava una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;opzione di **[!UICONTROL Prepare the personalization data with a workflow]** consegna. (NEO-11047, NEO-11301)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato risolto un problema che si verificava durante l&#39;utilizzo di campi calcolati in un&#39;attività di **[!UICONTROL Survey answers]** flusso di lavoro. (NEO-11382)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dei dati memorizzati in XML in un&#39;attività di **[!UICONTROL Survey answers]** workflow. (NEO-10816)
* È stato risolto un problema durante l&#39;esecuzione dell&#39;aggiornamento del server con build 8935.
* È stato risolto un problema che causava errori inutili nel registro post-aggiornamento quando un&#39;attività del **[!UICONTROL Survey answers]** flusso di lavoro non era completamente configurata.
* FDA Teradata: è stato risolto un problema relativo ai campi e agli indici con incremento automatico nelle tabelle SQL.

## Versione 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 giugno 2018

**Miglioramenti**

* È stato risolto un problema di codifica del tracciamento con Microsoft Edge e Internet Explorer. (NEO-11257)
* È stato risolto un problema con la personalizzazione dei collegamenti immagine nelle consegne LINE. (NEO-11077)
* È stato risolto un problema che impediva il corretto funzionamento del meccanismo di generazione della sequenza ID. (NEO-11115)
* È stato risolto un problema che impediva il funzionamento delle richieste di privacy (GDPR) quando si utilizzava uno spazio dei nomi personalizzato con una chiave di riconciliazione del tipo intero. (NEO-11123)
* È stato corretto un errore che poteva verificarsi quando si utilizzava l&#39; **[!UICONTROL Distribution of values]** opzione nelle attività del **[!UICONTROL Query]** flusso di lavoro. (NEO-10958)
* È stato risolto un problema che si verificava durante la sincronizzazione degli spazi di offerta dall&#39;istanza di marketing all&#39;istanza di interazione. (NEO-11162)
* Miglioramento della gestione degli indici dei nomi lunghi durante il post-aggiornamento

## Versione 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 maggio 2018

**Miglioramenti**

* È stato risolto un problema che impediva il corretto funzionamento dell&#39;aggiornamento di Windows Server.
* È stato risolto un problema nell&#39; **[!UICONTROL Survey Result]** attività quando si utilizzavano i dati memorizzati in XML. Il rapporto veniva visualizzato in modo non corretto. (NEO-10816)
* È stato risolto un problema di prestazioni che poteva verificarsi con il processo inMail quando si utilizzava un server di posta indesiderata. (NEO-10641)
* È stato risolto un problema di aggiornamento del database che poteva verificarsi quando si aggiornavano più di 1000 schemi.

## Versione 18.4 - Build 8931{#release-18-4-build-8931}

24 aprile 2018

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
   <td> EU General Data Protection Regulation (GDPR)<br /> </td> 
   <td> <p>Il GDPR è la nuova legge dell’Unione europea sulla privacy che armonizza e aggiorna i requisiti di protezione dei dati in vigore dal 25 maggio 2018. Il GDPR si applica ai clienti di Adobe Campaign che conservano dati per soggetti che risiedono nell’Unione europea.</p> <p>Oltre alle funzionalità per la privacy già disponibili in  Adobe Campaign (compresa la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente), stiamo sfruttando questa opportunità in qualità di processore dati per includere funzionalità aggiuntive, al fine di facilitare la tua disponibilità in qualità di Titolare dei Dati per determinate richieste GDPR:</p> 
    <ul> 
     <li> <p>Diritto di accesso: consente all'Oggetto dati di ricevere una copia dei propri dati personali acquisiti dai Controllori dati, che possono includere dati memorizzati in  Adobe Campaign.</p> </li> 
     <li> <p>Destra per eliminare: autorizza l'Oggetto dati a cancellare i propri dati personali acquisiti dai Controllori dati, potenzialmente includendo i dati memorizzati in  Adobe Campaign.</p> </li> 
    </ul> Per ulteriori informazioni, consulta la <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">documentazione dettagliata</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Profili attivi<br /> </td> 
   <td> <p> Adobe Campaign ora fornisce l'elenco dei profili attivi, aggiornati mensilmente tramite un flusso di lavoro dedicato.</p> <p>Per ulteriori informazioni, consulta la <a href="../../platform/using/about-profiles.md#active-profiles">documentazione dettagliata</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Miglioramento del connettore push Android<br /> </td> 
   <td> <p>Il connettore Android è stato migliorato per supportare un throughput più elevato. </p> <p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/configuring-the-mobile-application.md">documentazione dettagliata</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* L&#39;espansione di entità esterne è ora disabilitata per impedire potenziali attacchi da parte di utenti non autenticati. (NEO-10173)
* Autorizzazioni più rigorose per impedire agli utenti standard di modificare i parametri di configurazione dell’istanza come gli URL di accesso all’applicazione, le impostazioni LDAP, ecc. (NEO-10171)
* È stato risolto un problema che poteva rivelare informazioni riservate tramite tracce dello stack. I dettagli degli errori vengono ora registrati nel back-end in una posizione non accessibile dalla rete esterna. (NEO-10176)
* Autorizzazioni più rigorose per impedire agli utenti standard di visualizzare i documenti caricati da un amministratore e/o i pacchetti esportati. (NEO-10170)

**Miglioramenti**

* **Canale LINE - Miglioramento** dell&#39;architettura: Come per tutti gli altri canali in  Adobe Campaign, il canale LINE ora è supportato in tutti i tipi di distribuzione: ospitato, ibrido e locale.
* **Generazione** automatica della sequenza: Il meccanismo di generazione ID è stato migliorato per aumentare la durata delle istanze di Campaign con grandi volumi di oggetti. For more information, refer to this [technote](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html).

**Altre modifiche**

* È disponibile una nuova modalità per l&#39;importazione di pacchetti utilizzando la riga di comando, che consente dipendenze circolari (non consigliato per i pacchetti di grandi dimensioni). Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot;. (NEO-8979)
* Sono state migliorate le prestazioni per il caricamento di grandi quantità di dati in Teradata e è stato risolto un problema che impediva la visualizzazione del valore corretto dei dati elaborati nel registro. (NEO-10429)
* L&#39;importazione di audience da  Audience Manager ora funziona con file suddivisi. In precedenza, solo l’ultimo file del segmento veniva importato dal flusso di lavoro tecnico importSharedAudience. (NEO-10156)
* In Windows, il percorso di installazione predefinito del server Campaign è stato modificato. Quando si avvia la versione a 64 bit, il percorso di installazione predefinito è ora: **C:\Program Files\Adobe\Adobe Campaign Classic v7** invece di **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* Le regole MX predefinite sono state migliorate per includere più domini e ottimizzare il throughput.
* Sono state applicate restrizioni di accesso alla chiamata SOAP della procedura guidata di distribuzione (xtk:serverOptions#SaveOptions).
* La libreria obsoleta weka.jar è stata rimossa e la libreria OpenSSL è stata aggiornata per l&#39;ottimizzazione della sicurezza.
* È stato migliorato il flusso di lavoro tecnico di fatturazione per proteggere le prestazioni delle istanze.
* È stata ripristinata la possibilità per gli amministratori di impostare o reimpostare la password di qualsiasi operatore. A questo scopo, fare clic con il pulsante destro del mouse su un operatore, selezionare **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e impostare la nuova password dell&#39;operatore. È consigliabile che gli operatori cambino la password al primo riconnessione. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../production/using/lost-password.md).
* Per supportare la nuova funzione di multitenanza in  Adobe Target, ora è possibile aggiungere un nuovo parametro &quot;at_property&quot; agli URL quando si configurano le opzioni e gli account esterni per l&#39;integrazione con Target. Il valore da utilizzare per questo parametro può essere trovato in  Adobe Target e verrà utilizzato da Campaign per eseguire chiamate a Target. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* È ora possibile specificare una pagina di destinazione predefinita da aprire quando si fa clic su un&#39;immagine trasmessa da  Adobe Target. In precedenza, facendo clic su tale immagine si passava al set di immagini predefinito al momento della creazione del messaggio e-mail. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../integrations/using/inserting-a-dynamic-image.md).
* Aggiunta della casella **Abilita tracce** SMPP nell&#39;account esterno per forzare l&#39;output delle tracce. Per ulteriori informazioni, consulta la [documentazione dettagliata](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Evoluzioni tecniche**

queryDef

queryDef è stato modificato per quanto riguarda la clausola &quot;orderBy&quot;. Prima della modifica, la chiave primaria della tabella interrogata sarebbe implicitamente aggiunta alle clausole &quot;orderBy&quot;. In alcuni motori di database (almeno postgresql), impedisce l&#39;uso di indici (tutti i campi della clausola orderBy devono essere coperti dallo stesso indice). Se dipendevi da questo comportamento, dovrai aggiungere esplicitamente la chiave primaria nella clausola &quot;orderBy&quot;.

Ad esempio, se si dispone della seguente query:

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

Sarebbe implicitamente consegnato come (prima delle modifiche alla versione 18.4):

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

La funzione JavaScript &#39;urlEncode&#39; non funzionava correttamente per i caratteri non ASCII. È stato corretto e ora deve funzionare con tutti i caratteri Unicode (inclusi i caratteri giapponesi). Se si utilizza il comportamento &#39;urlEncode&#39; per i caratteri non ASCII, sarà necessario adattare il codice.

Importazione pacchetto - nuova modalità

È disponibile una nuova modalità per l&#39;importazione di pacchetti utilizzando la riga di comando, che consente dipendenze circolari (non consigliato per i pacchetti di grandi dimensioni). La funzionalità esistente viene mantenuta. Per tali pacchetti con dipendenze circolari, all&#39;importazione del pacchetto della riga di comando è stato aggiunto un nuovo flag **-usejs** . Una volta eseguito, utilizzerà il motore JSEngine come quando l&#39;importazione del pacchetto viene eseguita dall&#39;interfaccia.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patch**

* È stato risolto un problema di sincronizzazione durante la replica dei registri di consegna e tracciamento da  Adobe Campaign Standard ad Adobe Campaign Classic. (NEO-10023)
* È stato risolto un problema relativo alla gestione delle tabelle Error e Log in Teradata quando un flusso di lavoro ETL veniva ripreso dopo un errore in un&#39;operazione di caricamento rapida. Le tabelle Errore e Registro ora vengono eliminate correttamente ogni volta che il flusso di lavoro riprende. (NEO-10672)
* È stato risolto un problema di postaggiornamento per installare automaticamente il pacchetto Hive (necessario per Hadoop) se è installato il pacchetto FDA. (NEO-10592)
* Risolto un errore che trattava domini non validi come errore **Non definito** . (NEO-10248)
* È stato risolto un problema che causava la duplicazione dei registri nella tabella deliveryLogStats durante l&#39;invio delle consegne push android. (NEO-10234)
* È stato risolto un problema che poteva impedire la lettura di alcuni formati di codici a barre da parte degli scanner di codici a barre. (NEO-10125)
* È stato risolto un problema relativo alla funzione JavaScript &#39;urlEncode&#39; quando si utilizzano caratteri non ASCII. Per ulteriori informazioni, consulta la sezione &quot;Evoluzioni tecniche&quot;. (NEO-10123)
* È stato risolto un problema durante l&#39;esecuzione di una query che includeva le funzioni sha256 nei database Teradata. (NEO-10119)
* Correzione degli errori di memoria del flusso di lavoro che possono verificarsi nell&#39;attività SalesForce quando si utilizzano tabelle SalesForce molto grandi. (NEO-9900)
* È stato risolto un problema con l&#39;opzione **Genera complemento** nelle attività del flusso di lavoro di targeting quando si utilizza FDA. (NEO-9878)
* È stato risolto un problema che poteva causare l&#39;aggiornamento delle metriche **Elaborato** e **Successo** nell&#39;istanza di marketing quando si utilizzava il mid-sourcing. (NEO-9454)
* Corrette le regole di non riproposta di interazione quando più di 10k offerte in totale nella piattaforma (NEO-9352)
* È stato risolto un problema che poteva impedire di specificare la destinazione di una consegna quando si utilizzava un file XML esterno. (NEO-9312)
* È stato risolto un problema che poteva causare errori di flusso di lavoro durante l&#39;esecuzione di un&#39;ipotesi su un&#39;offerta e l&#39;aggiornamento dello stato della proposta. (NEO-9304)
* Sono stati corretti degli errori che si verificavano durante l&#39;analisi del recapito quando si utilizzavano regole di pressione basate su un attributo del mapping di consegna Android. (NEO-9202)
* È stato risolto un problema che si verificava durante l&#39;ordinamento delle colonne nell&#39;elenco dei destinatari e che poteva generare problemi di prestazioni. Per ulteriori informazioni sulle modifiche queryDef, vedere la sezione &quot;Evoluzioni tecniche&quot; di seguito. (NEO-9042)
* È stato risolto un problema a causa del quale i collegamenti contenuti in un messaggio e-mail di approvazione potevano puntare a un URL di accesso errato, in particolare quando si utilizzava un tipo di login di Federated ID. (NEO-9011)
* È stato risolto un problema che poteva causare la visualizzazione di date errate nei selettori delle date dei rapporti per alcuni orari. (NEO-9007)
* È stato risolto un problema che impediva la visualizzazione della destinazione di un&#39;uscita quando si utilizza un database SQL FDA. (NEO-8924)
* È stato risolto un problema che causava il mancato pulling dei dati da parte del connettore MS Dynamics CRM per i primi 7 giorni del mese. (NEO-8803)
* È stato corretto un errore con l&#39;integrazione di Analytics che impediva agli utenti di includere caratteri internazionali. (NEO-8719)
* È stato risolto un problema che poteva consentire la modifica del flusso di lavoro senza i diritti appropriati. (NEO-8708)
* È stato risolto un problema con FDA su HTTP quando si utilizzava Message Center in un&#39;architettura ibrida, che causava un rilascio della connessione o una perdita di connessione (timeout). (NEO-8438)
* Sono stati corretti gli errori del flusso di lavoro che si verificavano nell&#39;attività di query incrementale per gli ID negativi. (NEO-8229)
* È stato risolto un problema che poteva causare la visualizzazione di barre di scorrimento doppie in alcune schermate. (NEO-8208)
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore durante l&#39;esecuzione della procedura guidata di aggiornamento della struttura del database. PostUpgrade eseguirà una ridenominazione degli indici con nomi superiori a 30. Tenere presente che per le tabelle di grandi dimensioni, la sostituzione dell&#39;indice richiederà tempo. (NEO-7983)
* È stato corretto un problema a causa del quale i registri di monitoraggio non venivano sincronizzati correttamente dall&#39;istanza di esecuzione del Centro messaggi per controllare l&#39;istanza. (NEO-7286)
* È stato risolto un problema di prestazioni con l&#39;attività di arricchimento dell&#39;offerta. (NEO-7263)
* È stato risolto un problema che impediva l&#39;utilizzo della funzione DaysAgo durante la query di un database Redshift tramite FDA. (NEO-7099)
* Risolto un problema di regressione nella gestione dei dati che impediva la creazione dell&#39;indice sulle attività del flusso di lavoro di tipo Enrichment.
* È stato risolto un problema che poteva verificarsi durante la creazione di risorse esterne con il titolo @id
* È stato risolto un problema che poteva verificarsi durante il caricamento di file compressi tramite un server FTP o durante il caricamento di file con caratteri jolly nel nome del file.
* È stato risolto un problema con le enumerazioni di tipo base esteso nelle risorse personalizzate esterne create in Campaign Standard.
* È stato risolto un problema che poteva causare l&#39;invio di SMS anche quando la connessione con il provider non andava a buon fine, causando perdite di SMS.
* È stato corretto un errore che causava il blocco indefinito di una connessione SMTP.
* È stato risolto un problema relativo alle regole di tipo di pressione durante la preparazione dei messaggi quando si utilizzava una mappatura LINE o quando gli schemi di filtro e targeting erano diversi.
