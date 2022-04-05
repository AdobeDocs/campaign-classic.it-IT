---
product: campaign
title: Versioni di Campaign Classic 2019
description: Ulteriori informazioni sulle versioni di Campaign Classic 2019
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
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

* È stato risolto un problema di regressione a causa dell’implementazione della certificazione SSL che causava un errore della connessione utente sul server Windows. (NEO-20629)
* È stato risolto un problema che causava la visualizzazione di un numero di tag di versione errato nel **Informazioni** menu.


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
   <td> <p>CCPA è la nuova legge sulla privacy dello Stato della California che armonizza e modernizza i requisiti di protezione dei dati in vigore dal 1° gennaio 2020. Il CCPA si applica ai clienti Adobe Campaign che detengono dati per soggetti residenti in California.</p>
    <p>Oltre alle funzionalità per la privacy già disponibili (tra cui la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente), Adobe Campaign facilita la conformità a CCPA:</p>
    <ul>
      <li>Diritto di accesso e diritto alla cancellazione: stiamo sfruttando le funzionalità aggiunte per il RGPD. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Maggiori informazioni</a></li>
      <li>Puoi verificare se un consumatore ha rinunciato alla vendita di Informazioni personali. A questo scopo, devi estendere la tabella Profili e aggiungere un <strong>Rinuncia per CCPA</strong> campo . <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Maggiori informazioni</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Monitoraggio del flusso di lavoro in tempo reale</strong><br /> </th> 
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
<td> <p>Adobe Campaign consente di provare il nuovo interattivo <a href="https://amp.dev/about/email/">AMP per e-mail</a> , che consente agli esperti di marketing di includere componenti AMP all’interno dei messaggi per migliorare l’esperienza e-mail con contenuti avanzati, dinamici e interattivi, direttamente utilizzabili all’interno del messaggio stesso.</p>
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
<td> <p>SMS protetti è ora supportato tramite il connettore generico esteso SMPP. Ciò consente una connessione crittografata al provider.</p> <p><strong>Avviso</strong> Questa funzione richiede un certificato aggiornato su tutti i server. I certificati non validi, revocati o scaduti generano errori che influiscono sulle funzionalità di invio complessivo degli SMS.</p><p>Per ulteriori informazioni, consulta la <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-protocol.html?lang=it">documentazione dettagliata</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* Sono state corrette le vulnerabilità di cross-site scripting memorizzate nell’interfaccia di Campaign: convalida dei dati di input e codifica dell’output. (NEO-16810)
* È stato risolto un problema di sicurezza relativo all’autorizzazione dei profili che poteva consentire l’accesso a dati non autorizzati, rafforzando i criteri di restrizione dell’accesso. (NEO-14445)

**Miglioramenti**

* Ottimizzazione del consumo di memoria per le notifiche push.
* Per ottimizzare le prestazioni e lo storage, la gestione **logins.log** è stato migliorato. Il file viene ora suddiviso in più file, uno ogni giorno con un massimo di 365 file conservati. [Maggiori informazioni](../../production/using/log-files.md)
* È ora possibile configurare l’account esterno di Microsoft Dynamics CRM utilizzando le credenziali password (password + nome utente) o il certificato (chiave privata). [Maggiori informazioni](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Sono stati aggiunti alcuni miglioramenti al connettore FDA del Hadoop per migliorare l&#39;affidabilità
* È stata aggiunta una protezione specifica per controllare lo spazio su disco prima di consentire il caricamento di risorse pubbliche sul server.
* Nuovo [Opzioni di Campaign](../../installation/using/configuring-campaign-options.md) sono stati aggiunti:
   * La **WdbcKillSessionPolicy** l&#39;opzione di configurazione consente di influenzare **Arresto incondizionato** comportamento su tutti i flussi di lavoro e le query del database PostgreSQL.
   * La **NmsOperation_DeliveryPreparationWindow** consente di definire il numero di giorni al di sopra dei quali le consegne con stato incoerente verranno escluse dal conteggio delle consegne in esecuzione.
   * La **WdbcOptions_TempDbName** consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server. Questo ottimizza i backup e la replica. [Maggiori informazioni](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * La **XtkCleanup_NoStats** È stata migliorata l&#39;opzione per PostgreSQL per controllare meglio il comportamento del passaggio di ottimizzazione dello storage del flusso di lavoro di pulizia del database. [Maggiori informazioni](../../production/using/database-cleanup-workflow.md#statistics-update)
* È stato aggiunto un meccanismo di blocco dell’account a **logon()** API. Impedisce ulteriori tentativi di accesso dopo un certo numero di tentativi di accesso consecutivi non riusciti entro un intervallo di tempo specificato.
* Nuovo **Tempo massimo di esecuzione personalizzazione** nelle proprietà di consegna ti consente di definire un periodo di timeout per il tempo di esecuzione della personalizzazione, al fine di evitare che la fase di personalizzazione venga eseguita troppo a lungo. [Maggiori informazioni](../../delivery/using/personalization-fields.md#timing-out-personalization)
* La **protocollo ftp** è stata aggiunta l’opzione per consentire l’utilizzo di una configurazione proxy per le connessioni SFTP. [Maggiori informazioni](../../installation/using/file-res-management.md)
* Nuovo supporto dell’accesso proxy a un server esterno SFTP per ambienti on-premise.
* È stata aggiunta una protezioni specifica per impedire l’installazione di pacchetti non compatibili con l’istanza Campaign. [Maggiori informazioni](../../installation/using/installing-campaign-standard-packages.md)

_Sistemi obsoleti_

I seguenti sistemi sono ora [obsoleto](deprecated-features.md) per le implementazioni di Campaign Classic:
* Apache 2.2
* Centos 6

Verifica di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità di Campaign più recente. [Maggiori informazioni](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

_SDK per Campaign Mobile_

È ora disponibile la build 1.0.26 dell’SDK per iOS. In questa nuova build è stato aggiunto il supporto di iOS 13. Questa nuova versione supporta ora la priorità delle notifiche e il nuovo processo di gestione dei token di registrazione per le notifiche push iOS 13. Se esegui applicazioni su una versione precedente dell&#39;SDK, devi ricompilare le applicazioni con il nuovo SDK. Per ottenere l&#39;SDK, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Patch**

* È stato risolto un problema di arresto anomalo quando **Aggiungi tabella collegata** il campo era vuoto nel **Caricamento dati (RDBMS)** attività del flusso di lavoro. (NEO-12213)
* È stato risolto un problema che poteva causare l’elaborazione di alcuni messaggi da parte del server Mid-Sourcing. (NEO-12395)
* È stato risolto un problema nel flusso di lavoro di pulizia del database quando si utilizzava l’opzione di banding delle query con Teradata. (NEO-12399)
* È stato risolto un problema che interessava l’analisi della consegna con la regola di tipologia, incluso il dominio ne.jp . (NEO-12609)
* È stato risolto un problema relativo agli aggiornamenti SMS su TLS che implicavano un criterio di certificato più restrittivo. Questi aggiornamenti potrebbero causare un errore di connessione tra i server di marketing e di mid-sourcing in caso di certificato obsoleto. (NEO-17698)
* È stato risolto un problema che si verificava con l’utilizzo di **Prova connessione** su un account esterno in un ambiente di mid-sourcing con autenticazione Vault. (NEO-12722)
* È stato risolto un problema sulle query che utilizzano le funzioni data con una connessione al Hadoop FDA. (NEO-12847)
* È stato risolto un problema che si verificava durante la sostituzione di un’immagine nell’editor e-mail. (NEO-13098)
* È stato risolto un problema che poteva causare errori post-aggiornamento nelle cartelle che erano state eliminate o spostate in un altro percorso. (NEO-13118)
* È stato risolto un problema nella visualizzazione dell&#39;immagine quando si utilizzava **Definire l’immagine per le dimensioni dello schermo del dispositivo** opzione sui messaggi LINE. (NEO-13228)
* È stato risolto un problema di preparazione della consegna quando **Escludere l’indirizzo duplicato durante la consegna** deselezionata. (NEO-13240)
* È stato risolto un problema nei flussi di lavoro che si verificava con l’utilizzo di **Trasferimento file** per scaricare i file utilizzando **Elimina i file di origine dopo il trasferimento** con nome contenente un carattere spazio. (NEO-13411)
* È stato risolto un problema con la pulizia della cache Tomcat che poteva causare problemi di memoria. (NEO-13456)
* È stato risolto un problema che si verificava durante l’installazione di **Controllo del motore di offerta con istanza di esecuzione** pacchetto integrato in un&#39;istanza di controllo esistente in esecuzione in Microsoft SQL 2017. (NEO-13539)
* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si deselezionavano gli URL tracciati in un messaggio e-mail dal **Contenuto testo** a causa di una variabile non inizializzata. (NEO-13545)
* È stato risolto un problema di codifica sul nome del mittente cinese. (NEO-13837)
* È stato corretto un errore che poteva verificarsi durante la visualizzazione dei dati di risposta del sondaggio da Esplora risorse. (NEO-14590)
* È stato risolto un problema che poteva causare discrepanze tra la classificazione del registro di consegna e la tabella di quarantena. (NEO-16547)
* È stato risolto un problema relativo alle chiavi DKIM che non erano incorporate nelle e-mail. (NEO-16804)
* È stato risolto un problema che visualizzava il codice di errore errato quando veniva utilizzato un token di sessione non valido nel contesto di chiamate API per attivare gli eventi. Il codice di errore era &quot;HTTP 200 OK&quot; invece di &quot;HTTP 403 Forbidden&quot;. (NEO-16826)
* È stato risolto un problema che si verificava durante la visualizzazione dei rapporti di consegna tramite accesso web. (NEO-17015)
* È stato risolto un problema di autenticazione IMS durante l’accesso ad Adobe Campaign. (NEO-17312)
* È stato risolto un problema che impediva l’eliminazione delle e-mail messe in quarantena dal processo di gestione della privacy. (NEO-17314)
* Sono stati risolti i problemi di throughput dopo l&#39;aggiornamento a 9031 con il database SQL. (NEO-17558)
* È stato risolto un problema che interessava il connettore di gestione delle relazioni con i clienti con Salesforce. (NEO-17712)
* È stato risolto un problema di timeout durante l’importazione di dati da un SFTP esterno. (NEO-19723)
* È stato risolto un problema che si verificava all’accesso ai modelli Predictive. (NEO-19713)
* È stato risolto un problema che interessava il campionamento casuale in **Divisione** attività del flusso di lavoro con il database FDA del Hadoop. (NEO-16636)
* È stata corretta una regressione sull’Oracle che causava la visualizzazione di alcune funzioni come non valide dopo l’aggiornamento. (NEO-12759)


## Versione 19.1{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) Versione 19.1.8 - Build 9039 {#release-19-1-8-build-9039}

_15 aprile 2021_

* È stata corretta una regressione della console client che causava messaggi di errore persistenti nella schermata di connessione IMS. (NEO-34821)
* È stata corretta una regressione che poteva bloccare l’esportazione dei dati del flusso di lavoro in un database FDA (Teradata, Snowflake).

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

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
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.
> * Se utilizzi l’integrazione Experience Cloud Triggers tramite autenticazione oAuth, devi passare ad Adobe I/O come descritto [in questa pagina](../../integrations/using/configuring-adobe-io.md). La modalità di autenticazione OAuth legacy con Campaign [è stata ritirata](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) a **settembre 2021**. Gli ambienti in hosting usufruiscono di una proroga fino al **23 febbraio 2022**. In qualità di cliente on-premise o ibrido, contatta l’Assistenza clienti Adobe per estendere il supporto a febbraio 2022. Devi fornire ad Adobe [l’AppID dell’applicazione OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional).



**Miglioramenti**

* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.
* L’autenticazione dell’integrazione dei trigger originariamente basata su oAUTH per accedere alla pipeline è stata modificata e spostata in Adobe I/O. [Ulteriori informazioni](../../integrations/using/configuring-adobe-io.md)
* Con la fine del supporto del protocollo binario legacy del servizio APNs per iOS, tutte le istanze che utilizzano questo protocollo vengono aggiornate al protocollo HTTP/2 nella fase di post-aggiornamento.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)
* È stato risolto un problema che causava la disattivazione del connettore SMPP dopo un errore di connessione, impedendo l’invio di altre consegne SMS e causando problemi di prestazioni.
* È stato risolto un problema che visualizzava percentuali errate durante la generazione di un rapporto descrittivo tramite un’attività del flusso di lavoro. (NEO-14314)
* È stato risolto un problema di preparazione della consegna quando **Escludere l’indirizzo duplicato durante la consegna** opzione deselezionata. (NEO-13240)
* È stato risolto un problema che poteva causare un errore dei flussi di lavoro durante l’esecuzione di un’attività **Enrichment**. (NEO-17338)
* È stato risolto un problema nei flussi di lavoro che si verificava recuperando i record da un database esterno e inserendoli nel database Campaign. (NEO-26359)
* È stato risolto un problema di arresto anomalo del server impedendo il danneggiamento della memoria durante la pulizia del parser di espressione.
* È stato risolto un problema che impediva la **NoNull** funzionamento nei database Oracle dopo l&#39;aggiornamento alla build 9032. (NEO-26488)
* È stato risolto un problema che impediva la visualizzazione del pulsante **Salva** durante la modifica di una descrizione del modello della campagna con copia-incolla di simboli come, ad esempio, i caratteri giapponesi. (NEO-27071)
* È stato risolto un problema che impediva il salvataggio della descrizione di una campagna o di un modello di campagna facendo clic all’esterno della finestra prima di fare clic sul pulsante **Salva**. (NEO-27449)
* È stato risolto un problema a livello di configurazione proxy che impediva di accedere ad Adobe Campaign dopo l’ultimo aggiornamento di Windows 10. (NEO-27813)
* È stato risolto un problema relativo alla gestione di righe vuote nei file di registro, che causava errori nel comportamento del processo MTA e causava un calo delle prestazioni nell’invio della consegna.

**Evoluzioni tecniche**

Tomcat è stato aggiornato dalla versione 7 (7.0.103) alla versione 8 (8.5.57). La directory `tomcat-7` viene sostituita da una directory `tomcat-8`. In Windows, _iis_neolane_setup.vbs_ e _apache_neolane.conf_ ora sono installati nella directory `conf` (in precedenza era `tomcat-7/conf`). Su linux, _apache_neolane.conf_ è ora installato nella directory `conf`.

Su Linux, l&#39;avvio del servizio nlserver ora utilizza un&#39;unità di sistema invece dello script /etc/init.d/nlserver6. La migrazione al nuovo schema di avvio viene eseguita automaticamente quando installi il pacchetto 19.1.8. /etc/init.d/nlserver6 è ancora disponibile ma per interagire con il servizio nlserver (avvio, riavvio, arresto, ecc.), si consiglia di utilizzare direttamente il comando systemctl.


### ![](assets/do-not-localize/red_2.png) Versione 19.1.7 - Build 9036 {#release-19-1-7-build-9036}

_15 settembre 2020_

**Miglioramenti**

* È stato migliorato nlsrvmod per l’utilizzo del thread Apache 2.4 per correggere gli arresti anomali di nlsrvmod.
* È stato risolto un problema che si verificava durante l’utilizzo dell’attività Trasferimento file con un account esterno di Azure e una crittografia SSL. La connessione è stata eseguita tramite HTTP anziché HTTPS. (NEO-26720)
* È stato risolto un problema con il meccanismo di cache url che non recuperava l’etichetta o la categoria.
* È stato corretto un problema a causa del quale gli URL delle pagine speculari venivano definiti in modo non corretto nelle comunicazioni e-mail (a causa di un controllo errato dei caratteri ASCII). (NEO-26084)
* È stato aggiornato l’elenco jarsToSkip in catalina.properties, con la rimozione del riferimento a un file jar non più utilizzato (notifiche iOS).
* È stato risolto un problema di regressione che impediva dopo la pubblicazione dopo l’aggiornamento.
* È stata corretta una regressione con i rapporti di consegna predefiniti che venivano troncati quando venivano esportati in PDF. (NEO-25757)
* È stato risolto un problema che eliminava il valore del parametro di codifica durante il reindirizzamento da un URL di tracking (riguarda i caratteri giapponesi). (NEO-25637)
* È stato risolto un problema che causava il blocco dei collegamenti non firmati da domini personalizzati in casi in cui dovevano essere consentiti. (NEO-25210)
* È stato corretto un problema di regressione che interessava i campi calcolati in un flusso di lavoro causandone un’interruzione anomala. (NEO-25194)
* È stato risolto un problema di compatibilità con Microsoft Dynamics (dalla versione 8.2) che poteva impedire l’esecuzione di alcune chiamate API (RetrieveAllEntities). (NEO-24528)
* È stato risolto un problema di regressione che, nell’utilizzo della funzione del connettore ACS, impediva la connessione a un’istanza Campaign Standard (gestione errata della connessione FOH/FOH2). (NEO-23433)
* È stato risolto un problema di regressione della connessione al database che provocava il riavvio costante del server web a causa di un problema di codifica del database. Ciò poteva portare a un consumo eccessivo. (NEO-23264)
* È stato risolto un problema relativo al flusso di lavoro di pulizia del database che poteva non riuscire a causa di un&#39;origine dati non gestita. (NEO-23160, NEO-23364)
* Il flusso di lavoro di pulizia ora svuota gli elenchi scaduti per batch di 100 invece che singolarmente.
* Dopo il passaggio al nuovo meccanismo di sequenza ID, tutte le applicazioni web che aggiornano la tabella dei destinatari vengono ripubblicate durante il post-aggiornamento.
* È stato risolto un problema che impediva l’invio di e-mail in caso di codice JavaScript all’esterno del tag di contenuto di HTML. (NEO-18628)
* È stato risolto un problema che impediva agli indicatori di tracciamento dei messaggi transazionali di essere aggiornati dal flusso di lavoro Tracking. (NEO-17770)
* Sono state migliorate le prestazioni della procedura guidata di aggiornamento del database per ridurre il numero di istruzioni SQL al fine di ottimizzare il tempo di risposta.
* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si deselezionavano gli URL tracciati in un messaggio e-mail dal **Contenuto testo** a causa di una variabile non inizializzata. (NEO-13545)
* È stato risolto un problema che impediva il caricamento di file in un’attività File Transfer utilizzando un account esterno Azure Blob Storage a causa di una variabile non inizializzata (m_pCurlReader). (NEO-13717)
* È stato risolto un problema di post-aggiornamento che disattivava Apache e il server web prima della ripubblicazione dell’applicazione web. (NEO-27155)
* È stata corretta una regressione che causava la selezione di un fuso orario errato quando si impostava il tempo in un **Scheduler** attività del flusso di lavoro.


### ![](assets/do-not-localize/red_2.png) Versione 19.1.6 - Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Questa build è solo per installazioni on-premise. Per le distribuzioni ibride, le istanze in hosting continueranno a eseguire la build 9032. Non aggiornare l’istanza di marketing alla build 9035 in quanto non è compatibile con la versione 9032.

_3 ottobre 2019_

**Miglioramenti**

* È stato risolto un problema che si verificava con l’utilizzo del connettore di gestione delle relazioni con i clienti per Salesforce. (NEO-17712)
* È stato risolto un problema di indice che poteva causare problemi di prestazioni durante l’invio di messaggi transazionali.
* È stato risolto un problema di prestazioni durante l’invio dei messaggi. (NEO-17558)
* È stato risolto un problema che poteva causare l’elaborazione di alcuni messaggi da parte del server Mid-Sourcing. (NEO-12395)
* È stato risolto un problema che impediva l&#39;uso completo dell&#39;attività di gestione dati SQL (la &quot;gestione dati SQL&quot; denominata right era mancante).

### ![](assets/do-not-localize/red_2.png) Versione 19.1.5 - Build 9033{#release-19-1-5-build-9033}

_13 agosto 2019_

**Miglioramenti**

* È stato risolto un problema relativo all’istruzione SQL &quot;SELECT COUNT&quot; che veniva eseguita nel database predefinito anziché nel database FDA durante l’estrazione dei dati nell’attività di gestione dei dati.
* Per migliorare le funzionalità dell’infrastruttura cliente, nel file di configurazione del server è ora disponibile una dichiarazione proxy SFTP.
* È stato risolto un problema di arresto anomalo quando **Aggiungi tabella collegata** il campo era vuoto nel **Caricamento dati (RDBMS)** attività del flusso di lavoro. (NEO-12213)
* È stato risolto un problema relativo all’installazione del pacchetto midEmitter tramite la riga di comando.
* È stata aggiunta una nuova opzione di autenticazione per supportare le credenziali OAuth all’interno del connettore AC con Microsoft Dynamics. (NEO-11982)
* È stato risolto un problema nella gestione UID (Unique Universal Identifier) che causava il mancato funzionamento delle attività del flusso di lavoro di caricamento query e dati con Hive FDA.
* È stata corretta una regressione sull’Oracle che causava la visualizzazione di alcune funzioni come non valide dopo l’aggiornamento. (NEO-12759)
* È stata corretta una regressione che portava a scegliere un fuso orario errato quando si impostava l’ora in un’attività del flusso di lavoro di pianificazione.

### ![](assets/do-not-localize/green_2.png) Versione 19.1.4 - Build 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4 [!DNL Gold Standard] le versioni sono elencate in [page](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png) Versione 19.1.2 - Build 9029{#release-19-1-2-build-9029}

_21 giugno 2019_

**Miglioramenti di sicurezza**

* Per ottimizzare la sicurezza, la libreria Java (Netty) è stata aggiornata alla versione più recente (4.1.34). (NEO-12788)

**Miglioramenti**

* È stata corretta una regressione collegata alla gestione delle colonne del dominio che impediva l’invio di e-mail in determinate configurazioni.
* Per migliorare le prestazioni, è stato aggiunto un attributo _operation=&quot;none&quot; alle chiamate SOAP rtEvent per evitare le richieste &quot;SELECT FOR UPDATE&quot;.
* È stato risolto un problema di visualizzazione del flusso di lavoro relativo alle transizioni in uscita dopo l’attività Test . (NEO-12727)
* È ora possibile eliminare i record fittizi creati in Microsoft Dynamics durante il flusso di lavoro di importazione.
* Sono state migliorate le autorizzazioni per eseguire il pacchetto della zona di sicurezza quando si utilizza un account interno.


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
   <td> Pannello di controllo Campaign<br /> </td> 
   <td> <p>Per aumentare l’efficienza del lavoro come utente amministratore, gestisci le impostazioni dei server SFTP monitorando l’archiviazione, aggiungi gli indirizzi IP all’inserire nell'elenco Consentiti e installa le chiavi SSH per ogni istanza. Pannello di controllo Campaign è disponibile solo per i clienti ospitati su AWS a partire da oggi (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">accedere all'Experience Cloud oggi stesso</a>).</p> <p>Per ulteriori informazioni, consulta la <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it">documentazione dettagliata</a> e il <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=it">video tutorial</a>. </p><p>Nota: l’aggiornamento alla build Campaign più recente non è necessario per accedere al Pannello di controllo Campaign.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit trail<br /> </td> 
   <td> <p>In qualità di amministratore, aumenta la produttività monitorando e gestendo le modifiche apportate all'interno dell'istanza Adobe Campaign Classic. La traccia di audit registra le azioni eseguite sugli schemi di origine, sui flussi di lavoro e sulle opzioni. Puoi verificare rapidamente se un elemento è stato creato, modificato o eliminato.</p><p>Per ulteriori informazioni, consulta la <a href="../../production/using/audit-trail.md">documentazione dettagliata</a> e <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">video tutorial</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Sicurezza, robustezza e scalabilità<br /> </td> 
   <td> È stata aggiunta una serie di miglioramenti ad Campaign Classic. Guardrail, robustezza e scalabilità sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aggiornamento della matrice di compatibilità<br /> </td> 
   <td> Con questa nuova versione, Adobe Campaign ora supporta i seguenti sistemi di database. Fai riferimento a <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matrice di compatibilità</a>.<br /> 
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

* Per motivi di sicurezza, non è più possibile inserire comandi arbitrari quando si utilizza il **[!UICONTROL Pre-process the file]** in un **[!UICONTROL Data loading (file)]** attività del flusso di lavoro. È ora disponibile un elenco a discesa che consente di scegliere tra 3 opzioni: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) o **[!UICONTROL Decrypt]** (gpg). È stato aggiunto il flag di sicurezza XtkSecurity_Disable_Preproc . Per i nuovi clienti, questa opzione è impostata su 0. Per i clienti esistenti, questa opzione sarà impostata su 1 dal post aggiornamento per mantenere il comportamento precedente. Fai riferimento a questo [sezione](../../workflow/using/data-loading--file-.md).
* È stato risolto un problema di visibilità della password che si verificava durante il test della connessione di un account esterno FDA senza impostazione del fuso orario.
* La libreria PDFBox è stata rimossa.
* Tomcat è stato aggiornato alla versione 7.0.93.
* È stato risolto un problema di visibilità del token che si verificava quando il token di sicurezza non era valido.
* È stato risolto un potenziale problema di iniezione XTK nel JSP WSDL (schemawsdl.jsp).
* L&#39;archiviazione delle credenziali e delle password nel codice sorgente e nella memoria dell&#39;applicazione è stata ottimizzata.
* La limitazione della visualizzazione PII è stata ottimizzata. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Sono stati risolti i problemi di incoerenza nella gestione delle chiavi segrete.
* Viene ora visualizzato lo stesso errore generico per i tentativi di accesso non riusciti con un nome utente valido o non valido.
* La denominazione dei file caricati è stata migliorata.
* È stata aggiunta una nuova opzione XtkSecurity_Disable_GetSetEnv per bloccare l&#39;utilizzo delle funzioni setEnv e getEnv.
* Le informazioni sensibili sono ora nascoste nella traccia dello stack dell’applicazione.

**Miglioramenti a livello di sicurezza, robustezza e scalabilità**

* Lifespan - Ottimizzazione dell&#39;utilizzo della sequenza XtkNewId: le tabelle più dispendiose sono state spostate dalla sequenza xtkNewId alle sequenze dedicate.
* FDA su HTTP v2: il protocollo FDA su HTTP è ampiamente utilizzato nelle implementazioni ibride, soprattutto per il recupero e la preparazione di consegne wideLog. La robustezza è stata migliorata per evitare problemi di rete e possibili errori durante il recupero o il push dei dati. Ciò richiede che le build a entrambe le estremità della connessione siano aggiornate, altrimenti verrà comunque utilizzato il vecchio protocollo.
* Flusso di lavoro di tracciamento: la robustezza del flusso di lavoro di tracciamento è stata migliorata. Sono stati risolti diversi problemi relativi al tracciamento degli inserimenti/aggiornamenti dei log e alla personalizzazione del tracciamento degli URL. Inoltre, il flusso di lavoro di tracciamento ora rileva i problemi del registro di tracciamento che potrebbero causare errori e arrestare il flusso di lavoro. Questi problemi vengono ora scartati e non elaborati.
* Flusso di lavoro di pulizia: il flusso di lavoro di pulizia è stato migliorato per evitare potenziali errori e arresti. Questo ottimizza le dimensioni e le prestazioni del database.
* Immagini incorporate nei messaggi transazionali: abbiamo aggiunto il supporto completo delle immagini incorporate nei messaggi transazionali, per evitare possibili arresti anomali o immagini mancanti.
* Dimensione del database - XtkJobLog: a questa tabella è stato aggiunto un meccanismo di eliminazione. Questo ha un impatto positivo sulle dimensioni del database.
* Archiviazione CCN: i parametri predefiniti per l&#39;archiviazione CCN sono stati modificati per aumentare la velocità di archiviazione. [Maggiori informazioni](../../installation/using/email-archiving.md#parameters)
* Aggiornamento della struttura del database: Le richieste SQL generate dall&#39;aggiornamento guidato della struttura del database sono state migliorate per un&#39;esecuzione più rapida.
* Guardrail per le azioni dell&#39;operatore: sono state implementate diverse protezioni per impedire agli operatori di eseguire azioni che potrebbero influire sull&#39;integrità della piattaforma. Gli schemi incorporati non possono più essere eliminati tramite l’interfaccia . Inoltre, l’XML di origine del flusso di lavoro non può più essere modificato da utenti non amministratori.
* Sono state rese disponibili due nuove opzioni: **XtkSecurity_Restrict_EditXML** (consente di disabilitare la modifica del codice XML delle consegne) e **NmsOperation_OperationMgtDebug** (consente di monitorare l’esecuzione del flusso di lavoro tecnico operationMgt). [Leggi tutto](../../installation/using/configuring-campaign-options.md)

**Altre modifiche**

* Notifiche push: ora è supportata l’opzione Thread ID per il push iOS.
* È stata migliorata la gestione degli indici dei nomi lunghi che potrebbero causare problemi dopo l&#39;aggiornamento.
* Ora, durante l’analisi di una consegna definitiva, se la modalità di pubblicazione è impostata su **[!UICONTROL None]** nella procedura guidata di distribuzione viene registrato un errore e l’analisi viene interrotta: &quot;La modalità di pubblicazione è impostata su &#39;none&#39;: Impossibile incorporare l&#39;immagine. Le immagini non verranno visualizzate sul telefono cellulare.&quot; (NEO-12208)
* La gestione del registro di trasmissione è stata migliorata per la messaggistica transazionale. Quando i registri di trasmissione vengono sincronizzati dall’istanza di esecuzione all’istanza di controllo, il campo @lastModified viene aggiornato alla data corrente del sistema. L&#39;opzione MC_Update_BlLastModified è stata aggiunta per le istanze di controllo. True indica che la data corrente verrà utilizzata nell&#39;istanza di controllo (comportamento predefinito). False significa che utilizziamo la data @lastModified dell&#39;istanza di esecuzione del registro di trasmissione. (NEO-12579)
* Sono stati aggiunti indici nelle tabelle temporanee del coupon per ottimizzare l’invio della consegna. (NEO-12437)
* Nell’integrazione di Analytics, è ora consentito il recupero di dati AAM segmento con carattere %. (NEO-12025)
* È stato rimosso il limite di 10.000 record in Workflow Heatmap per risolvere un problema di dati mancanti. (NEO-12329)
* Open Office non è supportato ed è stato rimosso completamente dall&#39;applicazione. Se lo si stava ancora utilizzando, passare a Libre Office in quanto non funzionerà più a partire dal 19.1.
* È ora possibile limitare l’accesso in scrittura all’attività Update data in Workflow utilizzando gli attributi sysfilter. [Maggiori informazioni](../../configuration/using/filtering-schemas.md)

**Patch**

* È stato risolto un problema che impediva il caricamento del certificato per le notifiche push mobili iOS.
* Sono stati corretti i potenziali arresti anomali del server ricorrenti per le notifiche push transazionali. Sono stati risolti altri problemi di arresto anomalo.
* È stato risolto un problema che causava discrepanze nella generazione di rapporti tra le attività degli utenti e i rapporti di tracciamento per l’indicatore di consegna aperta. (NEO-11742)
* È stato risolto un problema relativo all’accesso IMS.
* È stato risolto un problema che poteva causare la perdita di immagini in una consegna quando si aggiungeva un’immagine dalla libreria . (NEO-11900)
* È stato risolto un problema che poteva verificarsi durante l’estrazione dei dettagli dell’offerta in una consegna direct mailing. (NEO-11700)
* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)
* È stato corretto un arresto anomalo della console che poteva verificarsi quando si utilizzava l’opzione Definito in un file esterno per la destinazione principale di una consegna. (NEO-12349)
* È stato risolto un problema che si verificava durante l’analisi di un messaggio con targeting dei destinatari per i domini giapponesi (.JP). (NEO-12246)
* È stato risolto un problema di visualizzazione che si verificava quando si utilizzava una distribuzione di valori con un collegamento 1:N. (NEO-12212, NEO-11820)
* È stato risolto un problema che poteva causare errori NmsMxDomain nei registri MTA dopo un aggiornamento successivo. (NEO-12752)
* È stato risolto un problema che si verificava con l’opzione &quot;Conserva tutti i dati aggiuntivi dal set principale&quot; in un’attività del flusso di lavoro di arricchimento. (NEO-13291)
* È stato risolto un problema di arresto anomalo Tomcat che si verificava durante l’invio di notifiche push tramite HTTP2. (NEO-12701)
* È stato risolto un problema relativo all’API HTTPRequest che non aspettava il completamento di tutti i callback. (NEO-12628)
* È stato risolto un problema relativo al processo di elaborazione degli indicatori di tracciamento per i messaggi transazionali. (NEO-12529)
* È stato risolto un problema relativo all’utilizzo dei temi nella gestione delle offerte. (NEO-11804)
* È stato risolto un problema di prestazioni durante l’invio di notifiche push. (NEO-11787)
* È stato risolto un problema durante l’anteprima di un file XML o CSV in uscita nella gestione delle offerte per una consegna direct mailing. (NEO-11290)
* È stato risolto un problema che si verificava durante l’installazione di **Gestione dei social network** (Social marketing). (NEO-12081)
* È stato risolto un problema che impediva l&#39;eliminazione di un&#39;applicazione Web anche se disponevi dei diritti di accesso corretti. (NEO-12072)
* È stato risolto un problema che poteva causare la sovrascrittura di alcuni valori durante l’esportazione e l’importazione di un oggetto tramite XML. È stata aggiunta l’opzione XtkExport_IncludeDefaultValues . Se è impostato su True (comportamento predefinito), vengono esportati tutti i valori. Se è impostato su False, le modifiche vengono sovrascritte con il valore predefinito. (NEO-11979)
* È stato risolto un problema che causava la **[!UICONTROL Alert]** l’attività del flusso di lavoro non riesce quando è stata aggiunta un’attività di arricchimento dopo una query. (NEO-12132)
* È stato risolto un problema relativo alle impostazioni di Oracle a causa del quale gli offset della pipeline (trigger) non venivano recuperati correttamente dal database, causando duplicati. (NEO-12121)
* È stato risolto un problema che poteva causare errori di visualizzazione nelle tabelle pivot durante l’utilizzo dell’integrazione di Analytics (NEO-12103)
* È stato risolto un problema relativo al rapporto Analisi descrittiva . (NEO-11414)
* È stato risolto un problema relativo ai connettori di gestione delle relazioni con i clienti quando la tabella remota conteneva un campo con un trattino basso nel nome.
* È stato risolto un problema che poteva causare un problema di visualizzazione dei simboli di valuta nei rapporti Ipotesi . (NEO-11634)
* È stato risolto un problema di reindirizzamento e tracciamento che si verificava quando si utilizzavano determinati caratteri nei collegamenti di tracciamento.
* È stato risolto un problema che impediva il corretto funzionamento dell’anteprima dell’offerta.
* È stato risolto un problema che impediva la rimozione dei mancati recapiti soft dalla tabella degli indirizzi.
* È stato corretto un errore JAVA che si verificava con l’utilizzo dei codici a barre.
* È stato risolto un problema di traduzione nelle applicazioni web (NEO-12460)
* È stato risolto un problema relativo all’attività del flusso di lavoro s3 File Transfer . (NEO-12473)
* È stato risolto un problema relativo ai campi data nelle applicazioni web. (NEO-12496)
* È stato risolto un problema di esaurimento ID quando si utilizzavano gli indirizzi di seed in una consegna. (NEO-11842)
* È stato risolto un problema relativo alla compatibilità phantomjs e Debian 9.
* È stato corretto un errore che si verificava con l’approvazione del contenuto di una bozza. (NEO-12725)
* È stato risolto un problema relativo alla funzione del flusso di lavoro &quot;Escludi questo sottoinsieme dalla popolazione&quot;. (NEO-12441)
* È stato risolto un problema relativo all’API HTTPRequest-wait che non aspettava il completamento di tutti i callback. (NEO-12628)
* È stato risolto un problema relativo all’attività &quot;Aggiorna pubblico condiviso&quot; in un’attività divisa. (NEO-11562)
* È stato risolto un problema di arresto anomalo del server Web. (NEO-12904)
* È stato risolto un problema relativo al parametro Natura nei modelli transazionali. (NEO-12334)
* È stato risolto un problema di arresto anomalo della console durante la visualizzazione degli URL tracciati nell’editor di testo delle e-mail. (NEO-13122)
* È stato risolto un problema relativo all’attività Split File durante l’importazione di tipi di pubblico da Audience Manager. (NEO-11550)
* È stato risolto un problema che causava errori nel rapporto sugli hot click. (NEO-11459)
* È stato risolto un problema relativo al rendering delle offerte. (NEO-11565)
* È stato risolto un problema relativo all’attività Aggiornamento elenco durante l’importazione di tipi di pubblico da Audience Manager. (NEO-11226)
* È stato risolto un problema relativo all’attività Pianificazione e alla configurazione del fuso orario. (NEO-11662)
* È stato risolto un problema che causava un errore del flusso di lavoro di tracciamento in caso di URL non validi.
* È stato risolto un problema relativo agli account esterni dopo l’importazione del pacchetto dell’app mobile.
* È stato risolto un problema che si verificava durante l’assegnazione di un fuso orario a un operatore . (NEO-12464)
* È stato risolto un problema che poteva causare errori nei log figlio master. (NEO-11539, NEO-8978)
* È stato risolto un problema che si verificava facendo clic sull’icona Cronologia in un rapporto salvato. (NEO-11620)
* È stato risolto un problema che si verificava durante la modifica di una tabella pivot in un rapporto. (NEO-12068)
