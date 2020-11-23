---
solution: Campaign Classic
product: campaign
title: Versione 19.1
description: Versione 19.1
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2622'
ht-degree: 7%

---


# Versione 19.1{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) Versione 19.1.7 - Build 9036 {#release-19-1-7-build-9036}

_15 settembre 2020_

**Miglioramenti**

* È stato migliorato nlsrvmod per l&#39;utilizzo di thread Apache 2.4 per correggere gli arresti anomali di nlsrvmod.
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;attività Trasferimento file con un account esterno di Azure e una crittografia SSL. La connessione è stata eseguita tramite HTTP invece che mediante HTTPS. (NEO-26720)
* È stato risolto un problema con il meccanismo di cache URL che non recuperava l&#39;etichetta o la categoria.
* È stato corretto un problema a causa del quale gli URL delle pagine mirror venivano definiti in modo non corretto nelle comunicazioni e-mail (a causa di un controllo errato dei caratteri ASCII). (NEO-26084)
* L&#39;elenco jarsToSkip in catalina.properties è stato aggiornato per rimuovere il riferimento a un file jar non più utilizzato (notifiche iOS).
* È stato risolto un problema di regressione che impediva dopo la pubblicazione dopo l&#39;aggiornamento post.
* Risolto un problema di regressione con i report di consegna forniti con Scene7 che venivano visualizzati troncati quando venivano esportati in PDF. (NEO-25757)
* È stato risolto un problema che eliminava il valore del parametro di codifica durante il reindirizzamento da un URL di tracciamento (impatto sui caratteri giapponesi). (NEO-25637)
* È stato risolto un problema che causava il blocco dei collegamenti non firmati da domini personalizzati quando questi dovevano essere consentiti. (NEO-25210)
* È stato corretto un problema di regressione che interessava i campi calcolati in un flusso di lavoro e causava un errore nel flusso di lavoro. (NEO-25194)
* È stato risolto un problema di compatibilità con Microsoft Dynamics (dalla versione 8.2) che poteva impedire l&#39;esecuzione di alcune chiamate API (RetrieveAllEntities). (NEO-24528)
* È stato risolto un problema di regressione quando si utilizzava la funzione di connettore ACS che impediva la connessione a un&#39;istanza Campaign Standard (gestione errata della connessione FOH/FOH2). (NEO-23433)
* È stato risolto un problema di regressione della connessione al database che causava il riavvio costante del server Web a causa di un problema di codifica del database. Ciò potrebbe portare ad un consumo eccessivo. (NEO-23264)
* È stato risolto un problema relativo al flusso di lavoro di pulizia del database che poteva non riuscire a causa di un&#39;origine dati non gestita. (NEO-23160, NEO-23364)
* Il flusso di lavoro di pulizia ora svuota gli elenchi scaduti per batch di 100 invece di uno per uno.
* Dopo il passaggio al [nuovo meccanismo](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)ID sequenza, tutte le applicazioni Web che aggiornano la tabella dei destinatari vengono ripubblicate durante il post-aggiornamento.
* È stato risolto un problema che impediva l&#39;invio di e-mail in caso di codice JavaScript all&#39;esterno del tag di contenuto HTML. (NEO-18628)
* È stato risolto un problema che impediva l&#39;aggiornamento degli indicatori di tracciamento dei messaggi transazionali dal flusso di lavoro Tracciamento. (NEO-17770)
* Sono state migliorate le prestazioni della procedura guidata di aggiornamento del database per ridurre il numero di istruzioni SQL al fine di ottimizzare il tempo di risposta.
* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si deselezionavano gli URL tracciati in un messaggio e-mail dalla scheda Contenuto **** testo a causa di una variabile non inizializzata. (NEO-13545)
* È stato risolto un problema che impediva il caricamento di file in un&#39;attività di trasferimento file tramite un account esterno di Azure Blob Storage a causa di una variabile non inizializzata (m_pCurlReader). (NEO-13717)
* È stato risolto un problema di post-aggiornamento che disattivava Apache e il server Web prima della ripubblicazione dell’applicazione Web. (NEO-27155)
* È stata corretta una regressione che causava la selezione di un fuso orario non corretto durante l&#39;impostazione dell&#39;ora in un&#39;attività del flusso di lavoro **Scheduler** .

## ![](assets/do-not-localize/orange_2.png) Versione 19.1.6 - Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Questa build è solo per installazioni locali. Per le distribuzioni ibride, le istanze ospitate continueranno a eseguire la build 9032. Non aggiornare l&#39;istanza di marketing alla build 9035 perché non è compatibile con 9032.

_3 ottobre 2019_

**Miglioramenti**

* È stato risolto un problema che si verificava con l’utilizzo del connettore di gestione delle relazioni con i clienti per Salesforce. (NEO-17712)
* È stato risolto un problema di indice che poteva causare problemi di prestazioni durante l’invio di messaggi transazionali.
* È stato risolto un problema di prestazioni durante l&#39;invio dei messaggi. (NEO-17558)
* È stato risolto un problema che poteva impedire l&#39;elaborazione di alcuni messaggi da parte del server di origine mid-Sourcing. (NEO-12395)
* È stato risolto un problema che impediva l&#39;uso completo dell&#39;attività di gestione dati SQL (manca la &quot;gestione dati SQL&quot; denominata right).

## ![](assets/do-not-localize/red_2.png) Versione 19.1.5 - Build 9033{#release-19-1-5-build-9033}

_13 agosto 2019_

**Miglioramenti**

* È stato risolto un problema con l&#39;istruzione SQL &#39;SELECT COUNT&#39; che è stata eseguita sul database predefinito anziché sul database FDA durante l&#39;estrazione dei dati nell&#39;attività Gestione dati.
* Per migliorare le funzionalità dell&#39;infrastruttura del cliente, nel file di configurazione del server è ora disponibile una dichiarazione proxy SFTP.
* È stato risolto un problema di arresto anomalo che si verificava quando il campo **Aggiungi tabella** collegata era vuoto nell&#39;attività del flusso di lavoro **Caricamento dati (RDBMS)** . (NEO-12213)
* È stato risolto un problema relativo all&#39;installazione del pacchetto midEmitter tramite la riga di comando.
* È stata aggiunta una nuova opzione di autenticazione per supportare le credenziali OAuth nel connettore CA con Microsoft Dynamics. (NEO-11982)
* È stato risolto un problema con la gestione UUID (Unique Universal Identifier) che causava il fallimento delle attività del flusso di lavoro di caricamento di query e dati con Hive FDA.
* Risolto un problema di regressione su  Oracle che causava la visualizzazione di alcune funzioni come non valide dopo l&#39;aggiornamento. (NEO-12759)
* È stata corretta una regressione che causava la selezione di un fuso orario non corretto durante l&#39;impostazione dell&#39;ora in un&#39;attività del flusso di lavoro dell&#39;Utilità di pianificazione.

## ![](assets/do-not-localize/green_2.png) Versione 19.1.4 - Build 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>19.1.4 Le versioni Gold Standard sono elencate in questa [pagina](../../rn/using/gold-standard.md).


## ![](assets/do-not-localize/red_2.png) Versione 19.1.2 - Build 9029{#release-19-1-2-build-9029}

_21 giugno 2019_

**Miglioramenti della sicurezza**

* Per ottimizzare la sicurezza, la libreria Java (Netty) è stata aggiornata alla versione più recente (4.1.34). (NEO-12788)

**Miglioramenti**

* È stata corretta una regressione collegata alla gestione delle colonne di dominio che impediva l&#39;invio di e-mail in determinate configurazioni.
* Per migliorare le prestazioni, alle chiamate SOAP rtEvent è stato aggiunto un attributo _operation=&quot;none&quot; per evitare richieste &quot;SELECT FOR UPDATE&quot;.
* È stato risolto un problema di visualizzazione del flusso di lavoro con transizioni in uscita dopo l&#39;attività Test. (NEO-12727)
* È ora possibile eliminare i record fittizi creati in Microsoft Dynamics durante il flusso di lavoro di importazione.
* Sono state migliorate le autorizzazioni per eseguire il pacchetto della zona di sicurezza quando si utilizza un account interno.

## ![](assets/do-not-localize/red_2.png) Versione 19.1 - Build 9026{#release-19-1-build-9026}

_30 maggio 2019_

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
   <td> Pannello di controllo Campaign<br /> </td> 
   <td> <p>Per migliorare l'efficienza del lavoro di amministratore, gestisci le impostazioni dei tuoi server SFTP monitorando lo storage, aggiungi indirizzi IP al  di inserire nell'elenco Consentiti e installa le chiavi SSH per ogni istanza. Il Pannello di controllo Campaign è disponibile solo per i clienti ospitati su AWS a partire da oggi (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">accedete al Experience Cloud  oggi</a>).</p> <p>Per ulteriori informazioni, consulta la <a href="https://docs.adobe.com/content/help/it-IT/control-panel/using/control-panel-home.html">documentazione dettagliata</a> e il <a href="https://docs.adobe.com/content/help/it-IT/campaign-classic-learn/control-panel/control-panel-overview.html">video tutorial</a>. </p><p>Nota: l'aggiornamento alla build Campaign più recente non è richiesto per accedere al Pannello di controllo Campaign.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit trail<br /> </td> 
   <td> <p>In qualità di amministratore, aumentate la produttività monitorando e gestendo le modifiche apportate all'interno dell'istanza Adobe Campaign Classic. La traccia di controllo registra le azioni eseguite sugli schemi di origine, sui flussi di lavoro e sulle opzioni. Potete verificare rapidamente se un elemento è stato creato, modificato o eliminato.</p><p>For more information, refer to the <a href="../../production/using/audit-trail.md">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/monitoring/audit-trail.html">how-to video</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail, robustezza e scalabilità<br /> </td> 
   <td> Una serie di miglioramenti è stata aggiunta al Campaign Classic. I miglioramenti a livello di affidabilità, robustezza e scalabilità sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aggiornamento della matrice di compatibilità<br /> </td> 
   <td> Con questa nuova versione,  Adobe Campaign ora supporta i seguenti sistemi di database. Refer to the <a href="https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html">Compatibility Matrix</a>.<br /> 
    <ul> 
     <li> <p> Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Per motivi di sicurezza, non è più possibile inserire comandi arbitrari quando si utilizza l&#39; **[!UICONTROL Pre-process the file]** opzione in un&#39;attività di **[!UICONTROL Data loading (file)]** flusso di lavoro. È ora disponibile un elenco a discesa che consente di selezionare tra 3 opzioni: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) o **[!UICONTROL Decrypt]** (gpg). È stato aggiunto il flag di protezione XtkSecurity_Disable_Preproc. Per i nuovi clienti, questa opzione sarà impostata su 0. Per i clienti esistenti, questa opzione sarà impostata su 1 per il post-aggiornamento per mantenere il comportamento precedente. Refer to this [section](../../workflow/using/data-loading--file-.md).
* È stato risolto un problema di visibilità della password che si verificava durante il test della connessione di un account FDA esterno senza fuso orario impostato.
* La libreria PDFBox è stata rimossa.
* Tomcat è stato aggiornato alla versione 7.0.93.
* È stato risolto un problema di visibilità token che si verificava quando il token di protezione non era valido.
* È stato corretto un potenziale problema di iniezione XTK nel JSP WSDL (schemawsdl.jsp).
* La memorizzazione delle credenziali e della password nel codice sorgente e nella memoria dell&#39;applicazione è stata ottimizzata.
* La limitazione della visualizzazione PII è stata ottimizzata. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Risolti problemi di incoerenza nella gestione delle chiavi segrete.
* Ora viene visualizzato lo stesso errore generico per i tentativi di accesso non riusciti con un nome utente valido o non valido.
* La denominazione dei file caricati è stata migliorata.
* È stata aggiunta una nuova opzione XtkSecurity_Disable_GetSetEnv per bloccare l&#39;uso delle funzioni setEnv e getEnv.
* Le informazioni riservate ora sono nascoste nella traccia dello stack dell&#39;applicazione.

**Miglioramenti a livello di affidabilità e scalabilità**

* Lifespan - Ottimizzazione della sequenza XtkNewId: le tabelle più dispendiose sono state spostate dalla sequenza xtkNewId alle sequenze dedicate. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA su HTTP v2: il protocollo FDA su HTTP è ampiamente utilizzato nelle distribuzioni ibride, in particolare per il recupero e la preparazione della distribuzione di ampiLog. La robustezza è stata migliorata per evitare problemi di rete e possibili errori durante il recupero o l&#39;invio dei dati. Ciò richiede che le build a entrambe le estremità della connessione siano aggiornate, altrimenti verrà utilizzato il vecchio protocollo.
* Flusso di lavoro di tracciamento: la robustezza del flusso di lavoro di tracciamento è stata migliorata. Sono stati risolti diversi problemi relativi al tracciamento di inserimenti/aggiornamenti del registro e alla personalizzazione del tracciamento URL. Inoltre, il flusso di lavoro di tracciamento ora rileva i problemi del registro che potrebbero causare errori e interrompere il flusso di lavoro. Questi problemi vengono ora scartati e non elaborati.
* Flusso di lavoro di pulizia: il flusso di lavoro di pulizia è stato migliorato per evitare potenziali errori e arresti. Questo ottimizza le dimensioni e le prestazioni del database.
* Immagini incorporate nei messaggi transazionali: abbiamo aggiunto il supporto completo delle immagini incorporate nei messaggi transazionali, per evitare possibili arresti anomali o immagini mancanti.
* Dimensione del database - XtkJobLog: a questa tabella è stato aggiunto un meccanismo di rimozione. Questo ha un impatto positivo sulla dimensione del database.
* Archiviazione CCN: i parametri predefiniti per l&#39;archiviazione CCN sono stati modificati per aumentare la velocità di archiviazione. [Leggi tutto](../../installation/using/email-archiving.md#parameters)
* Aggiornamento struttura del database: Sono state migliorate le richieste SQL generate dalla procedura guidata di aggiornamento della struttura del database per velocizzare l&#39;esecuzione.
* Garanzie per le azioni dell&#39;operatore: sono stati implementati diversi presidi per impedire agli operatori di eseguire azioni che potrebbero incidere sull&#39;integrità della piattaforma. Gli schemi predefiniti non possono più essere eliminati dall&#39;interfaccia. Inoltre, l’XML di origine del flusso di lavoro non può più essere modificato da utenti non amministratori.
* Sono state rese disponibili due nuove opzioni: **XtkSecurity_Restrict_EditXML** (consente di disabilitare l&#39;edizione del codice XML delle consegne) e **NmsOperation_OperationMgtDebug** (consente di monitorare l&#39;esecuzione del flusso di lavoro tecnico operationMgt). [Leggi tutto](../../installation/using/configuring-campaign-options.md)

**Altre modifiche**

* Notifiche push: ora è supportata l&#39;opzione Thread ID per il push iOS.
* È stata migliorata la gestione degli indici dei nomi lunghi che potrebbero causare problemi di postaggiornamento.
* Ora, durante l&#39;analisi di una consegna definitiva, se la modalità di pubblicazione è impostata **[!UICONTROL None]** nella procedura guidata di distribuzione, viene registrato un errore e l&#39;analisi viene arrestata: &quot;La modalità di pubblicazione è impostata su &#39;none&#39;: Impossibile incorporare l&#39;immagine. Le immagini non verranno visualizzate sul cellulare.&quot; (NEO-12208)
* La gestione del broadcast è stata migliorata per i messaggi transazionali. Quando i log di trasmissione vengono sincronizzati dall&#39;istanza di esecuzione all&#39;istanza di controllo, il campo @lastModified viene aggiornato alla data corrente del sistema. Per le istanze di controllo è stata aggiunta l’opzione MC_Update_BlLastModified. True indica che la data corrente verrà utilizzata nell&#39;istanza di controllo (comportamento predefinito). False indica che utilizzeremo la data @lastModified dell&#39;istanza di esecuzione del registro di trasmissione. (NEO-12579)
* Sono stati aggiunti indici nelle tabelle temporanee dei coupon per ottimizzare l&#39;invio delle consegne. (NEO-12437)
* Nell&#39;integrazione di Analytics, è ora consentito il recupero di dati AAM segmento con carattere %. (NEO-12025)
* È stato rimosso il limite di 10.000 record nella mappa di calore del flusso di lavoro per risolvere un problema di dati mancante. (NEO-12329)
* Open Office non è supportato e ora è completamente rimosso dall&#39;applicazione. Se ancora si utilizza, passare a Libre Office in quanto non funzionerà più a partire dalla 19.1.
* Ora puoi limitare l&#39;accesso in scrittura all&#39;attività di aggiornamento dei dati nel flusso di lavoro utilizzando gli attributi sysfilter. [Leggi tutto](../../configuration/using/filtering-schemas.md)

**Patch**

* È stato risolto un problema che impediva il caricamento del certificato per le notifiche push mobili iOS.
* Sono stati corretti i potenziali arresti anomali ricorrenti del server per le notifiche push transazionali. Sono stati risolti altri problemi di arresto anomalo.
* È stato risolto un problema che causava discrepanze tra le attività degli utenti e i rapporti di tracciamento per l&#39;indicatore di consegna aperto. (NEO-11742)
* È stato risolto un problema relativo all&#39;accesso IMS.
* È stato risolto un problema che poteva causare la mancanza di immagini in una consegna quando si aggiungeva un&#39;immagine dalla libreria. (NEO-11900)
* È stato risolto un problema che poteva verificarsi durante l&#39;estrazione dei dettagli dell&#39;offerta in una consegna diretta per posta. (NEO-11700)
* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)
* È stato corretto un arresto anomalo della console che poteva verificarsi quando si utilizzava l&#39;opzione Definito in un file esterno per la destinazione principale di una consegna. (NEO-12349)
* È stato risolto un problema durante l&#39;analisi di un messaggio che determinava il targeting dei destinatari per i domini giapponesi (.JP). (NEO-12246)
* È stato corretto un problema di visualizzazione quando si utilizzava una distribuzione di valori con un collegamento 1:N. (NEO-12212, NEO-11820)
* È stato risolto un problema che poteva causare errori NmsMxDomain nei registri MTA dopo un post aggiornamento. (NEO-12752)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;opzione &quot;Conserva tutti i dati aggiuntivi dal set principale&quot; in un&#39;attività del flusso di lavoro di arricchimento. (NEO-13291)
* È stato corretto un problema di arresto anomalo Tomcat durante l&#39;invio delle notifiche push tramite HTTP2. (NEO-12701)
* È stato risolto un problema con l’API HTTPRequest che non aspettava il completamento di tutte le callback. (NEO-12628)
* È stato risolto un problema relativo al processo di elaborazione degli indicatori di tracciamento per i messaggi transazionali. (NEO-12529)
* È stato risolto un problema relativo all&#39;utilizzo dei temi nella gestione delle offerte. (NEO-11804)
* È stato risolto un problema di prestazioni durante l&#39;invio delle notifiche push. (NEO-11787)
* È stato risolto un problema durante l&#39;anteprima di un file XML o CSV in uscita nella gestione delle offerte per la consegna diretta per posta. (NEO-11290)
* È stato risolto un problema durante l&#39;installazione del pacchetto **Gestione dei social network** (Social Marketing). (NEO-12081)
* È stato risolto un problema che impediva l&#39;eliminazione di un&#39;applicazione Web anche se disponeva dei diritti di accesso corretti. (NEO-12072)
* È stato risolto un problema che poteva causare la sovrascrittura di alcuni valori durante l&#39;esportazione e l&#39;importazione di un oggetto tramite XML. È stata aggiunta l’opzione XtkExport_IncludeDefaultValues. Se è impostata su True (comportamento predefinito), vengono esportati tutti i valori. Se è impostata su False, le modifiche vengono sovrascritte con il valore predefinito. (NEO-11979)
* È stato risolto un problema che causava il fallimento dell&#39;attività del **[!UICONTROL Alert]** flusso di lavoro quando un&#39;attività di arricchimento veniva aggiunta dopo una query. (NEO-12132)
* È stato risolto un problema  impostazioni Oracle in cui gli offset della pipeline (trigger) non venivano recuperati correttamente dal database causando duplicati. (NEO-12121)
* È stato risolto un problema che poteva causare errori di visualizzazione nelle tabelle pivot quando si utilizzava l&#39;integrazione di Analytics (NEO-12103)
* È stato risolto un problema relativo al report Analisi descrittiva. (NEO-11414)
* È stato risolto un problema con i connettori CRM quando la tabella remota conteneva un campo con un carattere di sottolineatura nel nome.
* È stato risolto un problema che poteva causare un problema di visualizzazione dei simboli di valuta nei rapporti Ipotesi. (NEO-11634)
* È stato risolto un problema di reindirizzamento e tracciamento quando si utilizzano alcuni caratteri nei collegamenti di tracciamento.
* È stato risolto un problema che impediva il corretto funzionamento dell&#39;anteprima dell&#39;offerta.
* È stato risolto un problema che impediva la rimozione dei rimbalzi software dalla tabella indirizzi.
* È stato corretto un errore JAVA durante l&#39;utilizzo di codici a barre.
* È stato risolto un problema di traduzione nelle applicazioni Web (NEO-12460)
* È stato risolto un problema relativo all&#39;attività del flusso di lavoro di trasferimento file s3. (NEO-12473)
* È stato risolto un problema relativo ai campi data nelle applicazioni Web. (NEO-12496)
* È stato risolto un problema di esaurimento ID quando si utilizzavano gli indirizzi iniziali in una consegna. (NEO-11842)
* È stato risolto un problema con la compatibilità phantomjs e Debian 9.
* È stato corretto un errore durante l&#39;approvazione del contenuto di una prova. (NEO-12725)
* È stato risolto un problema con la funzione di flusso di lavoro &quot;Escludi questo sottoinsieme dalla popolazione&quot;. (NEO-12441)
* È stato risolto un problema con l’API HTTPRequest-wait che non aspettava il completamento di tutte le callback. (NEO-12628)
* È stato risolto un problema con l&#39;attività &quot;Aggiorna pubblico condiviso&quot; in un&#39;attività divisa. (NEO-11562)
* È stato corretto un problema di arresto anomalo del server Web. (NEO-12904)
* È stato risolto un problema con il parametro Natura nei modelli transazionali. (NEO-12334)
* È stato risolto un problema di arresto anomalo della console durante la visualizzazione degli URL tracciati nell’editor di testo e-mail. (NEO-13122)
* È stato risolto un problema relativo all&#39;attività Dividi file durante l&#39;importazione di audience da  Audience Manager. (NEO-11550)
* È stato risolto un problema che causava errori nel rapporto clic con il pulsante destro del mouse. (NEO-11459)
* È stato risolto un problema con il rendering delle offerte. (NEO-11565)
* È stato risolto un problema con l&#39;attività di aggiornamento elenco durante l&#39;importazione di audience da  Audience Manager. (NEO-11226)
* È stato risolto un problema con la configurazione dell&#39;attività Pianificazione e del fuso orario. (NEO-11662)
* È stato risolto un problema che causava un errore nel flusso di lavoro di tracciamento in caso di URL con formato errato.
* È stato risolto un problema con gli account esterni dopo l&#39;importazione del pacchetto dell&#39;applicazione mobile.
* È stato risolto un problema durante l&#39;assegnazione di un fuso orario a un operatore. (NEO-12464)
* È stato risolto un problema che poteva causare errori nei registri secondari principali. (NEO-11539, NEO-8978)
* È stato risolto un problema che si verificava facendo clic sull&#39;icona Cronologia in un rapporto salvato. (NEO-11620)
* È stato risolto un problema che si verificava durante la modifica di una tabella pivot in un report. (NEO-12068)
