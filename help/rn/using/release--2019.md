---
product: campaign
title: Versioni di Campaign Classic 2019
description: Ulteriori informazioni sulle versioni di Campaign Classic 2019
hidefromtoc: true
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: c929557ee9f5467f9c3b8eb1ed25fae5399820ba
workflow-type: tm+mt
source-wordcount: '4825'
ht-degree: 24%

---

# Versioni 2019{#release-2019}

![](../../assets/v7-only.svg)

## Versione 19.2{#release-19-2}

### ![](assets/do-not-localize/limited_2.png) Versione 19.2.4 - Build 9082 {#release-19-2-4-build-9082}

_15 aprile 2021_

* È stata corretta una regressione della console client che causava messaggi di errore persistenti nella schermata di connessione IMS. (NEO-34821)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

_22 marzo 2021_

* È stata corretta una regressione che impediva l’utilizzo di alcuni componenti della console, come il selettore data e la gestione delle immagini nelle consegne. (NEO-31453, NEO-31454)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

_23 dicembre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), è necessario eseguire l’aggiornamento affinché sia il server di Campaign che la console client possano connettersi a Campaign dopo il **30 giugno 2021**. [Ulteriori informazioni](../../technotes/using/ims-updates.md)
>
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.



* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Versione 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_7 febbraio 2020_

**Miglioramenti**

* È stato risolto un problema di regressione dovuto all’implementazione della certificazione SSL che causava un errore di connessione utente sul server Windows. (NEO-20629)
* È stato risolto un problema che causava la visualizzazione di un numero di tag di versione errato in **Informazioni su** menu.


### ![](assets/do-not-localize/red_2.png) Versione 19.2 - Build 9080 {#release-19-2-build-9080}

_2 dicembre 2019_

**Novità**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA è la nuova legge sulla privacy dello Stato della California che armonizza e modernizza i requisiti di protezione dei dati, in vigore dal 1° gennaio 2020. Il CCPA si applica ai clienti di Adobe Campaign che detengono i dati per i soggetti residenti in California.</p>
    <p>Oltre alle funzionalità per la privacy già disponibili (tra cui la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente), Adobe Campaign contribuisce a garantire la conformità a CCPA:</p>
    <ul>
      <li>Diritto di accesso e diritto alla cancellazione: stiamo sfruttando le funzionalità aggiunte per il RGPD. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Maggiori informazioni</a></li>
      <li>Puoi verificare se un consumatore ha rinunciato alla vendita di Informazioni personali. A questo scopo, devi estendere la tabella dei profili e aggiungere una <strong>Rinuncia per CCPA</strong> campo. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Maggiori informazioni</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Monitoraggio live dei flussi di lavoro</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Ora puoi monitorare lo stato di esecuzione di tutti i flussi di lavoro sull’istanza utilizzando viste predefinite.</p>
   <p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">documentazione dettagliata</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Contenuto interattivo con AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign consente di provare il nuovo <a href="https://amp.dev/about/email/">AMP per e-mail</a> che consente agli addetti al marketing di includere componenti AMP all’interno dei messaggi, per migliorare l’esperienza e-mail con contenuti avanzati, dinamici e interattivi, direttamente utilizzabili all’interno del messaggio stesso.</p>
   <p>Questa funzionalità viene rilasciata come versione beta pubblica.</p>
   <p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/defining-interactive-content.md">documentazione dettagliata</a> e il <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">video tutorial</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Messaggi SMS protetti (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>La funzione per SMS protetti è ora supportata tramite il connettore generico esteso SMPP. Ciò consente una connessione crittografata al provider.</p> <p><strong>Avvertenza</strong> Questa funzione richiede un certificato aggiornato su tutti i server. I certificati non validi, revocati o scaduti generano errori che influiscono sulle funzionalità complessive di invio degli SMS.</p><p>Per ulteriori informazioni, consulta la <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-protocol.html?lang=it">documentazione dettagliata</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* Sono state risolte le vulnerabilità di cross-site scripting memorizzate nell’interfaccia di Campaign: convalida dei dati di input e codifica dell’output. (NEO-16810)
* È stato risolto un problema di sicurezza relativo all’autorizzazione del profilo che poteva consentire l’accesso a dati non autorizzati, rafforzando i criteri di restrizione dell’accesso. (NEO-14445)

**Miglioramenti**

* Ottimizzazione del consumo di memoria per le notifiche push.
* Per ottimizzare le prestazioni e lo storage, è possibile gestire **logins.log** è stato migliorato. Il file è ora suddiviso in più file, uno ogni giorno con un massimo di 365 file conservati. [Maggiori informazioni](../../production/using/log-files.md)
* È ora possibile configurare l&#39;account esterno di Microsoft Dynamics CRM utilizzando le credenziali della password (password + nome utente) o il certificato (chiave privata). [Maggiori informazioni](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Sono stati aggiunti alcuni miglioramenti al connettore FDA del Hadoop per migliorare l’affidabilità
* È stato aggiunto un guardrail specifico per controllare lo spazio su disco prima di consentire il caricamento di risorse pubbliche sul server.
* Nuovo [Opzioni campagna](../../installation/using/configuring-campaign-options.md) sono stati aggiunti:
   * Il **WdbcKillSessionPolicy** l&#39;opzione di configurazione consente di **Interruzione incondizionata** su tutti i flussi di lavoro e le query del database PostgreSQL.
   * Il **NmsOperation_DeliveryPreparationWindow** consente di definire il numero di giorni oltre i quali le consegne con stato incoerente verranno escluse dal conteggio delle consegne in esecuzione.
   * Il **WdbcOptions_TempDbName** consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server. Ciò consente di ottimizzare backup e repliche. [Maggiori informazioni](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * Il **XtkCleanup_NoStats** L&#39;opzione è stata migliorata per PostgreSQL al fine di controllare meglio il comportamento del passaggio di ottimizzazione dell&#39;archiviazione del flusso di lavoro di pulizia del database. [Maggiori informazioni](../../production/using/database-cleanup-workflow.md#statistics-update)
* Un meccanismo di blocco dell’account è stato aggiunto al **logon()** API. Impedisce ulteriori tentativi di accesso dopo un determinato numero di tentativi consecutivi di accesso non riusciti entro un intervallo di tempo specificato.
* Una nuova **Tempo di esecuzione massimo per la personalizzazione** nelle proprietà di consegna consente di definire un periodo di timeout per il runtime di personalizzazione, al fine di evitare che la fase di personalizzazione venga eseguita per troppo tempo. [Maggiori informazioni](../../delivery/using/personalization-fields.md#timing-out-personalization)
* Il **protocollo ftp** è stata aggiunta l’opzione per consentire l’utilizzo di una configurazione proxy per le connessioni SFTP. [Maggiori informazioni](../../installation/using/file-res-management.md)
* Nuovo supporto dell’accesso proxy a un server esterno SFTP per gli ambienti on-premise.
* È stato aggiunto un guardrail specifico per impedire l’installazione di pacchetti non compatibili con l’istanza Campaign. [Maggiori informazioni](../../installation/using/installing-campaign-standard-packages.md)

_Sistemi obsoleti_

I seguenti sistemi sono ora [obsoleto](deprecated-features.md) per le implementazioni di Campaign Classic:
* Apache 2.2
* Centos 6

Verifica di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità di Campaign più recente. [Maggiori informazioni](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

_SDK mobile di Campaign_

È ora disponibile la build 1.0.26 dell’SDK di iOS. In questa nuova build è stato aggiunto il supporto di iOS 13. Questa nuova versione ora supporta la priorità delle notifiche e il nuovo processo di gestione dei token di registrazione per le notifiche push in iOS 13. Se esegui applicazioni su una versione precedente dell’SDK, devi ricompilare le applicazioni con il nuovo SDK. Per ottenere l’SDK, contatta [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Patch**

* È stato risolto un problema di arresto anomalo quando il **Aggiungi tabella collegata** il campo era vuoto nel **Caricamento dati (RDBMS)** attività del flusso di lavoro. (NEO-12213)
* È stato risolto un problema che poteva causare la mancata elaborazione di alcuni messaggi da parte del server Mid-Sourcing. (NEO-12395)
* È stato risolto un problema nel flusso di lavoro di pulizia del database che si verificava con l’utilizzo dell’opzione Query banding con Teradata. (NEO-12399)
* È stato risolto un problema che influiva sull’analisi della consegna con la regola di tipologia che includeva il dominio ne.jp. (NEO-12609)
* È stato risolto un problema relativo agli aggiornamenti SMS su TLS che implicava criteri di certificato più restrittivi. Questi aggiornamenti potrebbero causare un errore di connessione tra i server di marketing e mid-sourcing in caso di certificato non aggiornato. (NEO-17698)
* È stato risolto un problema che si verificava con l’utilizzo di **Verifica connessione** su un account esterno in un ambiente di mid-sourcing con autenticazione Vault. (NEO-12722)
* È stato risolto un problema relativo alle query che utilizzavano funzioni data con una connessione di Hadoop FDA. (NEO-12847)
* È stato risolto un problema che si verificava durante la sostituzione di un’immagine nell’editor e-mail. (NEO-13098)
* È stato risolto un problema che poteva causare errori post-aggiornamento nelle cartelle eliminate o spostate in un altro percorso. (NEO-13118)
* È stato risolto un problema sulla visualizzazione delle immagini quando si utilizzava **Definisci l’immagine per dimensione schermo del dispositivo** nei messaggi LINE. (NEO-13228)
* È stato risolto un problema di preparazione della consegna che si verificava quando **Escludi indirizzo duplicato durante la consegna** è deselezionata. (NEO-13240)
* È stato risolto un problema nei flussi di lavoro che si verificava con l’utilizzo di **Trasferimento file** attività per scaricare file tramite **Elimina i file di origine dopo il trasferimento** , con un nome contenente uno spazio. (NEO-13411)
* È stato risolto un problema relativo alla pulizia della cache Tomcat che poteva causare problemi di memoria. (NEO-13456)
* È stato risolto un problema che si verificava durante l’installazione di **Controllo del motore di offerta con istanza di esecuzione** pacchetto incorporato su un&#39;istanza di controllo esistente in esecuzione in Microsoft SQL 2017. (NEO-13539)
* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si deselezionava gli URL tracciati in un’e-mail da **Contenuto testo** a causa di una variabile non inizializzata. (NEO-13545)
* È stato risolto un problema di codifica relativo al nome del mittente cinese. (NEO-13837)
* È stato corretto un errore che poteva verificarsi durante la visualizzazione dei dati di risposta del sondaggio da Esplora risorse. (NEO-14590)
* È stato risolto un problema che poteva causare discrepanze tra la classificazione del registro di consegna e la tabella di quarantena. (NEO-16547)
* È stato risolto un problema relativo alle chiavi DKIM che non erano incorporate nelle e-mail. (NEO-16804)
* È stato risolto un problema che causava la visualizzazione di un codice di errore errato quando veniva utilizzato un token di sessione non valido nel contesto di chiamate API per attivare gli eventi. Il codice di errore era &#39;HTTP 200 OK&#39; invece di &#39;HTTP 403 Forbidden&#39;. (NEO-16826)
* È stato risolto un problema che si verificava durante la visualizzazione dei rapporti di consegna tramite accesso web. (NEO-17015)
* È stato risolto un problema di autenticazione IMS che si verificava all’accesso ad Adobe Campaign. (NEO-17312)
* È stato risolto un problema che impediva l’eliminazione delle e-mail in quarantena da parte del processo di gestione della privacy. (NEO-17314)
* Sono stati risolti i problemi di velocità effettiva dopo l’aggiornamento a 9031 con il database SQL. (NEO-17558)
* È stato risolto un problema che interessava il connettore CRM con Salesforce. (NEO-17712)
* È stato risolto un problema di timeout che si verificava durante l’importazione di dati da un SFTP esterno. (NEO-19723)
* È stato risolto un problema che si verificava durante l’accesso a Modelli predittivi. (NEO-19713)
* È stato risolto un problema che interessava il campionamento casuale in **Dividi** attività del flusso di lavoro con database FDA del Hadoop. (NEO-16636)
* È stata corretta una regressione in Oracle che causava la mancata validità di alcune funzioni dopo il post-aggiornamento. (NEO-12759)


## Versione 19.1{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) Versione 19.1.8 - Build 9039 {#release-19-1-8-build-9039}

_15 aprile 2021_

* È stata corretta una regressione della console client che causava messaggi di errore persistenti nella schermata di connessione IMS. (NEO-34821)
* È stata corretta una regressione che poteva bloccare l’esportazione dei dati del flusso di lavoro in un database FDA (Teradata, Snowflake).

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

_22 marzo 2021_

* È stata corretta una regressione che impediva l’utilizzo di alcuni componenti della console, come il selettore data e la gestione delle immagini nelle consegne. (NEO-31453, NEO-31454)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

_16 dicembre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), è necessario eseguire l’aggiornamento affinché sia il server di Campaign che la console client possano connettersi a Campaign dopo il **30 giugno 2021**. [Ulteriori informazioni](../../technotes/using/ims-updates.md)
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.
> * Se utilizzi l’integrazione Experience Cloud Triggers tramite autenticazione oAuth, devi passare ad Adobe I/O come descritto [in questa pagina](../../integrations/using/configuring-adobe-io.md). La modalità di autenticazione OAuth legacy con Campaign [è stata ritirata](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) a **settembre 2021**. Gli ambienti in hosting usufruiscono di una proroga fino al **23 febbraio 2022**. Se sei un cliente on-premise o ibrido, contatta l’Assistenza clienti Adobe per estendere il supporto fino a febbraio 2022. Devi fornire ad Adobe [l’AppID dell’applicazione OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional).



**Miglioramenti**

* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.
* L’autenticazione dell’integrazione dei trigger per accedere alla pipeline, originariamente basata sulla configurazione di autenticazione OAuth, è stata modificata e spostata in Adobe I/O. [Ulteriori informazioni](../../integrations/using/configuring-adobe-io.md)
* Con la fine del supporto del protocollo binario legacy del servizio APNs per iOS, tutte le istanze che utilizzano questo protocollo vengono aggiornate al protocollo HTTP/2 nella fase di post-aggiornamento.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)
* È stato risolto un problema che causava la disattivazione del connettore SMPP dopo un errore di connessione, impedendo l’invio di altre consegne SMS e causando problemi di prestazioni.
* È stato risolto un problema che causava la visualizzazione di percentuali errate durante la generazione di un rapporto descrittivo tramite un’attività del flusso di lavoro. (NEO-14314)
* È stato risolto un problema di preparazione della consegna che si verificava quando **Escludi indirizzo duplicato durante la consegna** è stata deselezionata. (NEO-13240)
* È stato risolto un problema che poteva causare un errore dei flussi di lavoro durante l’esecuzione di un’attività **Enrichment**. (NEO-17338)
* È stato risolto un problema nei flussi di lavoro che si verificava recuperando i record da un database esterno e inserendoli nel database Campaign. (NEO-26359)
* È stato risolto un problema di arresto anomalo del server impedendo il danneggiamento della memoria durante la pulizia del parser di espressione.
* È stato risolto un problema che impediva il corretto funzionamento di **NoNull** oracle dopo l’aggiornamento alla build 9032. (NEO-26488)
* È stato risolto un problema che impediva la visualizzazione del pulsante **Salva** durante la modifica di una descrizione del modello della campagna con copia-incolla di simboli come, ad esempio, i caratteri giapponesi. (NEO-27071)
* È stato risolto un problema che impediva il salvataggio della descrizione di una campagna o di un modello di campagna facendo clic all’esterno della finestra prima di fare clic sul pulsante **Salva**. (NEO-27449)
* È stato risolto un problema a livello di configurazione proxy che impediva di accedere ad Adobe Campaign dopo l’ultimo aggiornamento di Windows 10. (NEO-27813)
* È stato risolto un problema relativo alla gestione delle righe vuote nei file di registro, che causava errori nel comportamento del processo MTA e determinava cali delle prestazioni nell’invio della consegna.

**Evoluzioni tecniche**

Tomcat è stato aggiornato dalla versione 7 (7.0.103) alla versione 8 (8.5.57). La directory `tomcat-7` viene sostituita da una directory `tomcat-8`. In Windows, _iis_neolane_setup.vbs_ e _apache_neolane.conf_ ora sono installati nella directory `conf` (in precedenza era `tomcat-7/conf`). Su linux, _apache_neolane.conf_ è ora installato nella directory `conf`.

In Linux, l&#39;avvio del servizio nlserver ora utilizza un&#39;unità di sistema invece dello script /etc/init.d/nlserver6. La migrazione al nuovo schema di avvio viene eseguita automaticamente quando si installa il pacchetto 19.1.8. Il /etc/init.d/nlserver6 è ancora fornito, ma per interagire con il servizio nlserver (avvia, riavvia, arresta, ecc.), si consiglia di utilizzare direttamente il comando systemctl.


### ![](assets/do-not-localize/red_2.png) Versione 19.1.7 - Build 9036 {#release-19-1-7-build-9036}

_15 settembre 2020_

**Miglioramenti**

* È stato migliorato nlsrvmod per l’utilizzo del thread Apache 2.4 per correggere gli arresti anomali di nlsrvmod.
* È stato risolto un problema che si verificava durante l’utilizzo dell’attività Trasferimento file con un account esterno di Azure e una crittografia SSL. La connessione è stata eseguita tramite HTTP invece che HTTPS. (NEO-26720)
* È stato risolto un problema con il meccanismo di cache dell’URL che non recuperava l’etichetta o la categoria.
* È stato corretto un problema a causa del quale gli URL delle pagine speculari venivano definiti in modo non corretto nelle comunicazioni e-mail (a causa di un controllo errato dei caratteri ASCII). (NEO-26084)
* È stato aggiornato l’elenco jarsToSkip in catalina.properties, con la rimozione del riferimento a un file jar non più utilizzato (notifiche iOS).
* È stato risolto un problema di regressione che impediva la pubblicazione dopo un post-aggiornamento.
* È stata corretta una regressione a causa della quale i rapporti di consegna predefiniti venivano visualizzati troncati quando venivano esportati in PDF. (NEO-25757)
* È stato risolto un problema che eliminava il valore del parametro di codifica durante il reindirizzamento da un URL di tracking (riguarda i caratteri giapponesi). (NEO-25637)
* È stato risolto un problema che causava il blocco dei collegamenti non firmati da domini personalizzati in casi in cui dovevano essere consentiti. (NEO-25210)
* È stato corretto un problema di regressione che interessava i campi calcolati in un flusso di lavoro causandone un’interruzione anomala. (NEO-25194)
* È stato risolto un problema di compatibilità con Microsoft Dynamics (dalla versione 8.2) che poteva impedire l’esecuzione di alcune chiamate API (RetrieveAllEntities). (NEO-24528)
* È stato risolto un problema di regressione che, nell’utilizzo della funzione del connettore ACS, impediva la connessione a un’istanza Campaign Standard (gestione errata della connessione FOH/FOH2). (NEO-23433)
* È stato risolto un problema di regressione della connessione al database che provocava il riavvio costante del server web a causa di un problema di codifica del database. Ciò poteva portare a un consumo eccessivo. (NEO-23264)
* È stato risolto un problema relativo al flusso di lavoro di pulizia del database che poteva non riuscire a causa di un&#39;origine dati non gestita. (NEO-23160, NEO-23364)
* Il flusso di lavoro di pulizia ora svuota gli elenchi scaduti per batch di 100 invece che singolarmente.
* Dopo il passaggio al nuovo meccanismo di sequenza ID, tutte le applicazioni web che aggiornano la tabella dei destinatari vengono ripubblicate durante il post-aggiornamento.
* È stato risolto un problema che impediva l’invio delle e-mail in presenza di codice JavaScript esterno al tag di contenuto HTML. (NEO-18628)
* È stato risolto un problema che impediva l’aggiornamento degli indicatori di tracciamento dei messaggi transazionali da parte del flusso di lavoro di tracciamento. (NEO-17770)
* Sono state migliorate le prestazioni della procedura guidata di aggiornamento del database per ridurre il numero di istruzioni SQL e ottimizzare il tempo di risposta.
* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si deselezionava gli URL tracciati in un’e-mail da **Contenuto testo** a causa di una variabile non inizializzata. (NEO-13545)
* È stato risolto un problema che impediva il caricamento di file in un’attività di trasferimento file tramite un account esterno di archiviazione BLOB di Azure a causa di una variabile non inizializzata (m_pCurlReader). (NEO-13717)
* È stato risolto un problema di post-aggiornamento che disattivava Apache e il server web prima della ripubblicazione dell’applicazione web. (NEO-27155)
* È stata corretta una regressione che causava la selezione di un fuso orario errato durante l’impostazione dell’ora in una **Scheduler** attività del flusso di lavoro.


### ![](assets/do-not-localize/red_2.png) Versione 19.1.6 - Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Questa build è solo per le installazioni on-premise. Per le distribuzioni ibride, le istanze ospitate continueranno a eseguire la build 9032. Non aggiornare l’istanza marketing alla build 9035 in quanto non compatibile con 9032.

_3 ottobre 2019_

**Miglioramenti**

* È stato risolto un problema che si verificava con l’utilizzo del connettore di gestione delle relazioni con i clienti per Salesforce. (NEO-17712)
* È stato risolto un problema di indice che poteva causare problemi di prestazioni durante l’invio di messaggi transazionali.
* È stato risolto un problema di prestazioni che si verificava durante l’invio di messaggi. (NEO-17558)
* È stato risolto un problema che poteva causare la mancata elaborazione di alcuni messaggi da parte del server Mid-Sourcing. (NEO-12395)
* È stato risolto un problema che impediva il pieno utilizzo dell’attività di gestione dati SQL (mancava l’autorizzazione denominata &quot;Gestione dati SQL&quot;).

### ![](assets/do-not-localize/red_2.png) Versione 19.1.5 - Build 9033{#release-19-1-5-build-9033}

_13 agosto 2019_

**Miglioramenti**

* È stato risolto un problema con l’istruzione SQL &quot;SELECT COUNT&quot; che veniva eseguita sul database predefinito anziché sul database FDA durante l’estrazione dei dati nell’attività di gestione dati.
* Per migliorare le funzionalità dell’infrastruttura del cliente, ora nel file di configurazione del server è disponibile una dichiarazione proxy SFTP.
* È stato risolto un problema di arresto anomalo quando il **Aggiungi tabella collegata** il campo era vuoto nel **Caricamento dati (RDBMS)** attività del flusso di lavoro. (NEO-12213)
* È stato risolto un problema con l’installazione del pacchetto midEmitter tramite riga di comando.
* È stata aggiunta una nuova opzione di autenticazione per supportare le credenziali OAuth all’interno del connettore AC con Microsoft Dynamics. (NEO-11982)
* È stato risolto un problema relativo alla gestione di UUID (Unique Universal Identifier) che causava il mancato funzionamento delle attività del flusso di lavoro Query e Caricamento dati con Hive FDA.
* È stata corretta una regressione in Oracle che causava la mancata validità di alcune funzioni dopo il post-aggiornamento. (NEO-12759)
* È stata corretta una regressione che causava la selezione di un fuso orario errato durante l’impostazione dell’ora in un’attività del flusso di lavoro Scheduler.

### ![](assets/do-not-localize/green_2.png) Versione 19.1.4 - Build 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4. [!DNL Gold Standard] Le versioni di sono elencate in questo [pagina](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png) Versione 19.1.2 - Build 9029{#release-19-1-2-build-9029}

_21 giugno 2019_

**Miglioramenti di sicurezza**

* Per ottimizzare la sicurezza, la libreria Java (Netty) è stata aggiornata all’ultima versione (4.1.34). (NEO-12788)

**Miglioramenti**

* È stata corretta una regressione collegata alla gestione delle colonne di dominio che impediva l’invio delle e-mail su alcune configurazioni.
* Per migliorare le prestazioni, è stato aggiunto un attributo _operation=&quot;none&quot; alle chiamate SOAP di rtEvent per evitare richieste &quot;SELECT FOR UPDATE&quot;.
* È stato risolto un problema di visualizzazione del flusso di lavoro con transizioni in uscita dopo l’attività Test. (NEO-12727)
* È ora possibile eliminare i record fittizi creati in Microsoft Dynamics durante il flusso di lavoro di importazione.
* Sono state migliorate le autorizzazioni per eseguire il pacchetto dell’area di sicurezza quando si utilizza un account interno.


### ![](assets/do-not-localize/red_2.png) Versione 19.1 - Build 9026{#release-19-1-build-9026}

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
   <td> Pannello di controllo<br /> </td> 
   <td> <p>Per aumentare l’efficienza del lavoro come utente amministratore, gestisci le impostazioni dei server SFTP monitorando l’archiviazione, aggiungi indirizzi IP al inserisco nell'elenco Consentiti di e installando chiavi SSH per ogni istanza. Il Pannello di controllo Campaign è disponibile solo per i clienti ospitati su AWS a partire da oggi (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">accedi oggi stesso all’Experience Cloud</a>).</p> <p>Per ulteriori informazioni, consulta la <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it">documentazione dettagliata</a> e il <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=it">video tutorial</a>. </p><p>Nota: per accedere al Pannello di controllo Campaign non è necessario effettuare l’aggiornamento alla build Campaign più recente.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit trail<br /> </td> 
   <td> <p>In qualità di amministratore, aumenta la produttività monitorando e gestendo le modifiche apportate all’interno dell’istanza di Adobe Campaign Classic. Nella traccia di audit vengono registrate le azioni eseguite su Schemi di origine, Flussi di lavoro e Opzioni. Puoi verificare rapidamente se un elemento è stato creato, modificato o eliminato.</p><p>Per ulteriori informazioni, consulta <a href="../../production/using/audit-trail.md">documentazione dettagliata</a> e <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">video tutorial</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Sicurezza, robustezza e scalabilità<br /> </td> 
   <td> È stata aggiunta una serie di miglioramenti a Campaign Classic. Guardrail, robustezza e scalabilità sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aggiornamento della matrice di compatibilità<br /> </td> 
   <td> Con questa nuova versione, Adobe Campaign ora supporta i seguenti sistemi di database. Consulta la sezione <a href="https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html">Matrice di compatibilità</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18 quater</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* Per motivi di sicurezza, non è più possibile inserire comandi arbitrari quando si utilizza **[!UICONTROL Pre-process the file]** opzione in un **[!UICONTROL Data loading (file)]** attività del flusso di lavoro. È ora disponibile un elenco a discesa che consente di selezionare tra 3 opzioni: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) oppure **[!UICONTROL Decrypt]** (gpg). È stato aggiunto il flag di sicurezza XtkSecurity_Disable_Preproc. Per i nuovi clienti, questa opzione sarà impostata su 0. Per i clienti esistenti, questa opzione sarà impostata su 1 dal post-aggiornamento per mantenere il comportamento precedente. Fai riferimento a questa [sezione](../../workflow/using/data-loading--file-.md).
* È stato risolto un problema di visibilità della password che si verificava durante il test della connessione di un account esterno FDA senza fuso orario impostato.
* Libreria PDFBox rimossa.
* Tomcat è stato aggiornato alla versione 7.0.93.
* È stato risolto un problema di visibilità del token che si verificava quando il token di sicurezza non era valido.
* È stato risolto un potenziale problema di iniezione XTK nel file JSP WSDL (schemawsdl.jsp).
* L&#39;archiviazione delle credenziali e delle password nel codice sorgente e nella memoria dell&#39;applicazione è stata ottimizzata.
* La restrizione della visualizzazione PII è stata ottimizzata. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Sono stati risolti i problemi di incoerenza nella gestione segreta delle chiavi.
* Lo stesso errore generico ora viene visualizzato per i tentativi di accesso non riusciti con un nome utente valido o non valido.
* È stata migliorata la denominazione dei file caricati.
* È stata aggiunta una nuova opzione XtkSecurity_Disable_GetSetEnv per bloccare l’utilizzo delle funzioni setEnv e getEnv.
* Le informazioni riservate sono ora nascoste nell&#39;analisi dello stack dell&#39;applicazione.

**Guardrail, robustezza e scalabilità**

* Durata: ottimizzazione dell’utilizzo della sequenza XtkNewId: le tabelle più impegnative sono state spostate dalla sequenza xtkNewId alle sequenze dedicate.
* FDA su HTTP v2: il protocollo FDA su HTTP è ampiamente utilizzato nelle distribuzioni ibride, in particolare per il recupero broadLog e la preparazione della consegna. È stata migliorata la robustezza per evitare problemi di rete e possibili errori quali il recupero o la trasmissione dei dati. Questo richiede che le build a entrambe le estremità della connessione siano aggiornate, altrimenti verrà ancora utilizzato il vecchio protocollo.
* Tracciamento del flusso di lavoro: è stata migliorata la robustezza del flusso di lavoro di tracciamento. Sono stati risolti diversi problemi relativi al tracciamento di inserimenti/aggiornamenti di registri e alla personalizzazione del tracciamento URL. Inoltre, il flusso di lavoro di tracciamento ora rileva i problemi del registro di tracciamento che potrebbero causare errori e arrestare il flusso di lavoro. Questi problemi vengono ora eliminati e non elaborati.
* Flusso di lavoro di pulizia: il flusso di lavoro di pulizia è stato migliorato per evitare potenziali errori e arresti. In questo modo si ottimizzano le dimensioni e le prestazioni del database.
* Immagini incorporate nei messaggi transazionali: è stato aggiunto il supporto completo delle immagini incorporate nei messaggi transazionali, per evitare possibili arresti anomali o immagini mancanti.
* Dimensioni database - XtkJobLog: è stato aggiunto un meccanismo di eliminazione alla tabella. Questo ha un impatto positivo sulla dimensione del database.
* Archiviazione Ccn: i parametri predefiniti per l&#39;archiviazione Ccn sono stati modificati per velocizzare l&#39;archiviazione. [Maggiori informazioni](../../installation/using/email-archiving.md#parameters)
* Aggiornamento della struttura del database: le richieste SQL generate dalla Procedura guidata di aggiornamento della struttura del database sono state migliorate per velocizzarne l&#39;esecuzione.
* Guardrail per le azioni dell’operatore: sono stati implementati diversi guardrail per impedire agli operatori di eseguire azioni che potrebbero influire sull’integrità della piattaforma. Gli schemi incorporati non possono più essere eliminati tramite l’interfaccia. Inoltre, il codice XML di origine del flusso di lavoro non può più essere modificato da utenti non amministratori.
* Sono state rese disponibili due nuove opzioni: **XtkSecurity_Restrict_EditXML** (consente di disabilitare l’edizione del codice XML delle consegne) e **NmsOperation_OperationMgtDebug** (consente di monitorare l’esecuzione del flusso di lavoro tecnico operationMgt). [Leggi tutto](../../installation/using/configuring-campaign-options.md)

**Altre modifiche**

* Notifiche push: è ora supportata l’opzione ID thread per push iOS.
* È stata migliorata la gestione degli indici dei nomi lunghi che poteva causare problemi post-aggiornamento.
* Ora, durante l’analisi di una consegna decomail, se la modalità di pubblicazione è impostata su **[!UICONTROL None]** nella procedura guidata di distribuzione viene registrato un errore e l’analisi viene interrotta: &quot;La modalità di pubblicazione è impostata su &quot;none&quot;: impossibile incorporare l’immagine. Le immagini non verranno visualizzate sul feature phone.&quot; (NEO-12208)
* La gestione del broadlog è stata migliorata per la messaggistica transazionale. Quando i broadLog vengono sincronizzati dall&#39;istanza di esecuzione all&#39;istanza di controllo, il campo @lastModified viene aggiornato alla data corrente del sistema. L&#39;opzione MC_Update_BlLastModified è stata aggiunta per le istanze di controllo. True indica che la data corrente verrà utilizzata nell&#39;istanza di controllo (comportamento predefinito). False significa che viene utilizzata la data di @lastModified del broadlog dell’istanza di esecuzione. (NEO-12579)
* Sono stati aggiunti indici nelle tabelle temporanee dei coupon per ottimizzare l’invio della consegna. (NEO-12437)
* Nell’integrazione di Analytics, ora è consentito il recupero di dati di segmenti AAM con il carattere %. (NEO-12025)
* È stato rimosso il limite di 10.000 record nella Workflow Heatmap per risolvere un problema di dati mancante. (NEO-12329)
* Open Office non è supportato ed è stato rimosso completamente dall&#39;applicazione. Se lo stavi ancora utilizzando, passa a Libre Office in quanto non funzionerà più a partire dalla versione 19.1.
* È ora possibile limitare l’accesso in scrittura all’attività Update data in Workflow utilizzando gli attributi sysfilter. [Maggiori informazioni](../../configuration/using/filtering-schemas.md)

**Patch**

* È stato risolto un problema che impediva il caricamento del certificato per le notifiche push per dispositivi mobili iOS.
* Sono stati risolti potenziali arresti anomali ricorrenti del server per le notifiche push transazionali. Sono stati risolti altri problemi di arresto anomalo.
* È stato risolto un problema che causava discrepanze nella generazione di rapporti tra le attività degli utenti e i rapporti di tracciamento per l’indicatore di consegna aperto. (NEO-11742)
* È stato risolto un problema con l’accesso IMS.
* È stato risolto un problema che poteva causare la perdita di immagini in una consegna durante l’aggiunta di un’immagine dalla libreria. (NEO-11900)
* È stato risolto un problema che poteva verificarsi durante l’estrazione dei dettagli dell’offerta in una consegna direct mailing. (NEO-11700)
* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)
* È stato risolto un arresto anomalo della console che poteva verificarsi utilizzando l’opzione Definito in un file esterno per il target principale di una consegna. (NEO-12349)
* È stato risolto un problema che si verificava durante l’analisi di un messaggio per i destinatari dei domini giapponesi (.JP). (NEO-12246)
* È stato risolto un problema di visualizzazione che si verificava con l’utilizzo di una distribuzione di valori con un collegamento 1:N. (NEO-12212, NEO-11820)
* È stato risolto un problema che poteva causare errori NmsMxDomain nei registri MTA dopo un post-aggiornamento. (NEO-12752)
* È stato risolto un problema che si verificava con l’utilizzo dell’opzione &quot;Mantieni tutti i dati aggiuntivi dal set principale&quot; in un’attività del flusso di lavoro di arricchimento. (NEO-13291)
* È stato risolto un problema di arresto anomalo di Tomcat durante l’invio di notifiche push tramite HTTP2. (NEO-12701)
* È stato risolto un problema relativo all’API HTTPRequest che non attendeva il completamento di tutti i callback. (NEO-12628)
* È stato risolto un problema relativo al processo di elaborazione degli indicatori di tracciamento per i messaggi transazionali. (NEO-12529)
* È stato risolto un problema relativo all’utilizzo dei temi nella gestione delle offerte. (NEO-11804)
* È stato risolto un problema di prestazioni che si verificava durante l’invio di notifiche push. (NEO-11787)
* È stato risolto un problema che si verificava durante l’anteprima di un file XML o CSV in uscita in gestione delle offerte per una consegna direct mailing. (NEO-11290)
* È stato risolto un problema che si verificava durante l’installazione di **Gestione dei social network** (Social Marketing). (NEO-12081)
* È stato risolto un problema che impediva l’eliminazione di un’applicazione web anche se si disponeva dei diritti di accesso corretti. (NEO-12072)
* È stato risolto un problema che poteva causare la sovrascrittura di alcuni valori durante l’esportazione e quindi l’importazione di un oggetto tramite XML. È stata aggiunta l’opzione XtkExport_IncludeDefaultValues. Se è impostato su True (comportamento predefinito), vengono esportati tutti i valori. Se è impostato su False, le modifiche vengono sovrascritte con il valore predefinito. (NEO-11979)
* È stato risolto un problema che causava la **[!UICONTROL Alert]** l’attività del flusso di lavoro non riesce quando viene aggiunta un’attività di arricchimento dopo una query. (NEO-12132)
* È stato risolto un problema relativo alle impostazioni Oracle a causa del quale gli offset della pipeline (trigger) non venivano recuperati correttamente dal database, causando duplicati. (NEO-12121)
* È stato risolto un problema che poteva causare errori di visualizzazione nelle tabelle pivot durante l’utilizzo dell’integrazione di Analytics (NEO-12103)
* È stato risolto un problema relativo al rapporto Analisi descrittiva. (NEO-11414)
* È stato risolto un problema relativo ai connettori di gestione delle relazioni con i clienti a causa del quale la tabella remota conteneva un campo il cui nome conteneva un trattino basso.
* È stato risolto un problema che poteva causare un problema di visualizzazione dei simboli di valuta nei report Ipotesi. (NEO-11634)
* È stato risolto un problema di reindirizzamento e tracciamento che si verificava con l’utilizzo di determinati caratteri nei collegamenti di tracciamento.
* È stato risolto un problema che impediva il corretto funzionamento dell’anteprima delle offerte.
* È stato risolto un problema che impediva la rimozione dei mancati recapiti non permanenti dalla tabella degli indirizzi.
* È stato corretto un errore JAVA che si verificava con l’utilizzo di codici a barre.
* È stato risolto un problema di traduzione nelle applicazioni web (NEO-12460)
* È stato risolto un problema relativo all’attività del flusso di lavoro s3 File Transfer. (NEO-12473)
* È stato risolto un problema relativo ai campi data nelle applicazioni web. (NEO-12496)
* È stato risolto un problema di esaurimento ID che si verificava con l’utilizzo di indirizzi di seed in una consegna. (NEO-11842)
* È stato risolto un problema di compatibilità tra phantomjs e Debian 9.
* È stato corretto un errore che si verificava durante l’approvazione del contenuto di una bozza. (NEO-12725)
* È stato risolto un problema con la funzione del flusso di lavoro &quot;Escludi questo sottoinsieme dal gruppo&quot;. (NEO-12441)
* È stato risolto un problema relativo all’API HTTPRequest-wait che non attendeva il completamento di tutti i callback. (NEO-12628)
* È stato risolto un problema relativo all’attività &quot;Aggiorna pubblico condiviso&quot; in un’attività divisa. (NEO-11562)
* È stato risolto un problema di arresto anomalo del server web. (NEO-12904)
* È stato risolto un problema relativo al parametro Nature nei modelli transazionali. (NEO-12334)
* È stato risolto un problema di arresto anomalo della console che si verificava durante la visualizzazione degli URL tracciati nell’editor di testo e-mail. (NEO-13122)
* È stato risolto un problema relativo all’attività Split File durante l’importazione di tipi di pubblico da Audience Manager. (NEO-11550)
* È stato risolto un problema che causava errori nel rapporto hot click. (NEO-11459)
* È stato risolto un problema relativo al rendering delle offerte. (NEO-11565)
* È stato risolto un problema relativo all’attività List Update durante l’importazione di tipi di pubblico da Audience Manager. (NEO-11226)
* È stato risolto un problema relativo all’attività Pianificazione e alla configurazione del fuso orario. (NEO-11662)
* È stato risolto un problema che causava un errore nel flusso di lavoro di tracciamento in caso di URL non validi.
* È stato risolto un problema relativo agli account esterni dopo l’importazione del pacchetto dell’app mobile.
* È stato risolto un problema che si verificava durante l’assegnazione di un fuso orario a un operatore. (NEO-12464)
* È stato risolto un problema che poteva causare errori nei registri matchild. (NEO-11539, NEO-8978)
* È stato risolto un problema che si verificava facendo clic sull’icona Cronologia in un rapporto salvato. (NEO-11620)
* È stato risolto un problema che si verificava durante la modifica di una tabella pivot in un rapporto. (NEO-12068)
