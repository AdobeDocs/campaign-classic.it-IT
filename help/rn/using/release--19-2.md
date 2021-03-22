---
solution: Campaign Classic
product: campaign
title: Versione 19.2
description: Note sulla versione di Campaign 19.2
feature: null
role: null
level: null
translation-type: tm+mt
source-git-commit: 96f5709b4c67d1979286cc1f71069a64435c5c70
workflow-type: tm+mt
source-wordcount: '1484'
ht-degree: 11%

---


# Versione 19.2{#release-19-2}

## ![](assets/do-not-localize/limited_2.png) Versione 19.2.4 - Build 9082 {#release-19-2-4-build-9082}

_22 marzo 2021_

* È stata corretta una regressione che impediva l’utilizzo di alcuni componenti della console, come il selettore data e la gestione delle immagini nelle consegne. (NEO-31453, NEO-31454)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Connettiti a [Distribuzione di software di Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) per scaricare la nuova versione. Scopri come proporre l’aggiornamento della console a tutti gli utenti finali [in questa pagina](../../installation/using/client-console-availability-for-windows.md).

_23 dicembre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), l’aggiornamento è obbligatorio per il server Campaign e la console client per poter connettersi a Campaign dopo il **30 giugno 2021**.
   >
   > 
* Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.



* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Versione 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_7 febbraio 2020_

**Miglioramenti**

* È stato risolto un problema di regressione a causa dell’implementazione della certificazione SSL che causava un errore della connessione utente sul server Windows. (NEO-20629)
* È stato risolto un problema che causava la visualizzazione di un numero di tag di versione errato nel menu **Informazioni su** .

## ![](assets/do-not-localize/red_2.png) Versione 19.2 - Build 9080 {#release-19-2-build-9080}

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
      <li>Diritto di accesso e diritto alla cancellazione: stiamo sfruttando le funzionalità aggiunte per il RGPD. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Leggi tutto</a></li>
      <li>Puoi verificare se un consumatore ha rinunciato alla vendita di Informazioni personali. A questo scopo, devi estendere la tabella Profili e aggiungere un campo <strong>Rinuncia per CCPA</strong> . <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Leggi tutto</a></li></td> 
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
<td> <p>Adobe Campaign consente di provare il nuovo formato interattivo <a href="https://amp.dev/about/email/">AMP per e-mail</a>, che consente agli esperti di marketing di includere componenti AMP all’interno dei messaggi, per migliorare l’esperienza e-mail con contenuti avanzati, dinamici e interattivi, direttamente utilizzabili all’interno del messaggio stesso.</p>
   <p>Questa funzionalità viene rilasciata come versione beta pubblica.</p>
   <p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/defining-interactive-content.md">documentazione dettagliata</a> e il <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">video tutorial</a>.</p><br /></td> 
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
<td> <p>SMS protetti è ora supportato tramite il connettore generico esteso SMPP. Ciò consente una connessione crittografata al provider.</p> <p><strong></strong> AvvisoQuesta funzione richiede un certificato aggiornato su tutti i server. I certificati non validi, revocati o scaduti generano errori che influiscono sulle funzionalità di invio complessivo degli SMS.</p><p>Per ulteriori informazioni, consulta la <a href="https://helpx.adobe.com/it/campaign/kb/sms-connector-protocol-and-settings.html">documentazione dettagliata</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Sono state corrette le vulnerabilità di cross-site scripting memorizzate nell’interfaccia di Campaign: convalida dei dati di input e codifica dell’output. (NEO-16810)
* È stato risolto un problema di sicurezza relativo all’autorizzazione del profilo che poteva consentire l’accesso a dati non autorizzati, rafforzando i criteri di restrizione dell’accesso. (NEO-14445)

**Miglioramenti**

* Ottimizzazione del consumo di memoria per le notifiche push.
* Per ottimizzare le prestazioni e lo storage, è stata migliorata la gestione del file **logins.log** . Il file viene ora suddiviso in più file, uno ogni giorno con un massimo di 365 file conservati. [Leggi tutto](../../production/using/log-files.md)
* È ora possibile configurare l’account esterno di Microsoft Dynamics CRM utilizzando le credenziali password (password + nome utente) o il certificato (chiave privata). [Leggi tutto](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Sono stati aggiunti alcuni miglioramenti al connettore FDA del Hadoop per migliorare l&#39;affidabilità
* È stata aggiunta una protezione specifica per controllare lo spazio su disco prima di consentire il caricamento di risorse pubbliche sul server.
* Sono state aggiunte nuove [opzioni campagna](../../installation/using/configuring-campaign-options.md):
   * L&#39;opzione di configurazione **WdbcKillSessionPolicy** consente di influenzare il comportamento **Arresto incondizionato** su tutti i flussi di lavoro e le query del database PostgreSQL.
   * L&#39;opzione **NmsOperation_DeliveryPreparationWindow** ti consente di definire il numero di giorni oltre i quali le consegne con stato incoerente verranno escluse dal conteggio delle consegne in esecuzione.
   * L&#39;opzione **WdbcOptions_TempDbName** consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server. Questo ottimizza i backup e la replica. [Leggi tutto](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * L&#39;opzione **XtkCleanup_NoStats** è stata migliorata per PostgreSQL per controllare meglio il comportamento del passaggio di ottimizzazione dello storage del flusso di lavoro di pulizia del database. [Leggi tutto](../../production/using/database-cleanup-workflow.md#statistics-update)
* È stato aggiunto un meccanismo di blocco dell’account all’API **logon()** . Impedisce ulteriori tentativi di accesso dopo un certo numero di tentativi di accesso consecutivi non riusciti entro un intervallo di tempo specificato.
* Una nuova opzione **Maximum personalization run time** nelle proprietà di consegna ti consente di definire un periodo di timeout per il tempo di esecuzione della personalizzazione, al fine di evitare che la fase di personalizzazione venga eseguita troppo a lungo. [Leggi tutto](../../delivery/using/personalization-fields.md#timing-out-personalization)
* È stata aggiunta l’opzione **protocollo ftp** per consentire l’utilizzo di una configurazione proxy per le connessioni SFTP. [Leggi tutto](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nuovo supporto dell’accesso proxy a un server esterno SFTP per ambienti on-premise.
* È stata aggiunta una protezioni specifica per impedire l’installazione di pacchetti non compatibili con l’istanza Campaign. [Leggi tutto](../../installation/using/installing-campaign-standard-packages.md)

_Sistemi obsoleti_

I seguenti sistemi sono ora [obsoleti](https://helpx.adobe.com/it/campaign/kb/deprecated-and-removed-features.html) per le implementazioni di Campaign Classic:
* Apache 2.2
* Centos 6

Verifica di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità di Campaign più recente. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

_SDK per Campaign Mobile_

È ora disponibile la build 1.0.26 dell’SDK per iOS. In questa nuova build è stato aggiunto il supporto di iOS 13. Questa nuova versione supporta ora la priorità delle notifiche e il nuovo processo di gestione dei token di registrazione per le notifiche push iOS 13. Se esegui applicazioni su una versione precedente dell&#39;SDK, devi ricompilare le applicazioni con il nuovo SDK. Per ottenere l&#39;SDK, contatta l&#39; [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Patch**

* È stato risolto un problema di arresto anomalo che si verificava quando il campo **Aggiungi tabella collegata** era vuoto nell&#39;attività del flusso di lavoro **Caricamento dati (RDBMS)** . (NEO-12213)
* È stato risolto un problema che poteva causare l’elaborazione di alcuni messaggi da parte del server Mid-Sourcing. (NEO-12395)
* È stato risolto un problema nel flusso di lavoro di pulizia del database quando si utilizzava l’opzione di banding delle query con Teradata. (NEO-12399)
* È stato risolto un problema che interessava l’analisi della consegna con la regola di tipologia, incluso il dominio ne.jp . (NEO-12609)
* È stato risolto un problema relativo agli aggiornamenti SMS su TLS che implicavano un criterio di certificato più restrittivo. Questi aggiornamenti potrebbero causare un errore di connessione tra i server di marketing e di mid-sourcing in caso di certificato obsoleto. (NEO-17698)
* È stato risolto un problema che si verificava quando si utilizzava il pulsante **Test connection** su un account esterno in un ambiente di mid-sourcing con autenticazione Vault. (NEO-12722)
* È stato risolto un problema sulle query che utilizzano le funzioni data con una connessione al Hadoop FDA. (NEO-12847)
* È stato risolto un problema che si verificava durante la sostituzione di un’immagine nell’editor e-mail. (NEO-13098)
* È stato risolto un problema che poteva causare errori post-aggiornamento nelle cartelle che erano state eliminate o spostate in un altro percorso. (NEO-13118)
* È stato risolto un problema nella visualizzazione dell&#39;immagine quando si utilizzava l&#39;opzione **Definisci immagine per dimensione schermo dispositivo** nei messaggi LINE. (NEO-13228)
* È stato risolto un problema di preparazione della consegna quando l’opzione **Escludi indirizzo duplicato durante la consegna** non era selezionata. (NEO-13240)
* È stato risolto un problema nei flussi di lavoro che si verificava durante l’utilizzo dell’attività **Trasferimento file** per scaricare i file utilizzando l’opzione **Elimina i file di origine dopo il trasferimento**, con un nome contenente un carattere spazio. (NEO-13411)
* È stato risolto un problema con la pulizia della cache Tomcat che poteva causare problemi di memoria. (NEO-13456)
* È stato risolto un problema che si verificava durante l’installazione del **Controllo del motore di offerta con il pacchetto integrato di esecuzione** su un’istanza di controllo esistente in esecuzione in Microsoft SQL 2017. (NEO-13539)
* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si deselezionavano gli URL tracciati in un messaggio e-mail dalla scheda **Contenuto testo** a causa di una variabile non inizializzata. (NEO-13545)
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
* È stato risolto un problema che interessava il campionamento casuale nell’attività del flusso di lavoro **Split** con database FDA di Hadoop. (NEO-16636)
* È stata corretta una regressione sull’Oracle che causava la visualizzazione di alcune funzioni come non valide dopo l’aggiornamento. (NEO-12759)


