---
title: Release 19.2
seo-title: Release 19.2
description: Release 19.2
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fd7bc26fe12a26d8fb0dcccd2135b799e76b52bd

---


# Release 19.2{#release-19-2}

[Genera aggiornamento](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | Rilasci [del Pannello di](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) controllo| Aggiornamenti [alla](../../rn/using/documentation-updates.md) documentazione| [Versioni](../../rn/using/release--19-1.md) precedenti| Funzioni [obsolete](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Disponibilità generale</strong></td>
   <td><img src="assets/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Non più disponibile</strong></td> 
   <td><img src="assets/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Ultima build stabile disponibile. Build convalidata in produzione.<br> </td>
   <td>Build convalidata da Adobe. In attesa di prove di produzione.<br> </td>
   <td>Nuova build disponibile con correzioni di bug. L'aggiornamento è obbligatorio.<br> </td>
   <td>Contiene regressioni note. L'aggiornamento è obbligatorio.<br> </td>
  </tr> 
 </tbody> 
</table>

L&#39; **ultima build** stabile è 9032 (205c981c3). Fai clic [qui](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/blue_2.png) Release 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_07 febbraio 2020_

**Miglioramenti**

* È stato risolto un problema di regressione a causa dell&#39;implementazione della certificazione SSL che causava un errore di connessione utente sul server Windows. (NEO-20629)
* È stato risolto un problema che causava la visualizzazione di un numero di tag versione non corretto nel menu **Informazioni** .

## ![](assets/orange_2.png) Release 19.2 - Build 9080 {#release-19-2-build-9080}

_02 dicembre 2019_

**Cosa c&#39;è di nuovo?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA è la nuova legge sulla privacy dello Stato della California che armonizza e aggiorna i requisiti di protezione dei dati in vigore dal 1° gennaio 2020. CCPA si applica ai clienti di Adobe Campaign che detengono i dati per i soggetti dati residenti in California.</p>
    <p>Oltre alle funzionalità per la privacy già disponibili (compresa la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente), Adobe Campaign ti aiuta a semplificare la tua preparazione all'adozione dell'APP:</p>
    <ul>
      <li>Diritto di accesso e Diritto di eliminazione: stiamo sfruttando le funzionalità aggiunte per il GDPR. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Leggi tutto</a></li>
      <li>È possibile verificare se un consumatore ha rinunciato alla vendita di Dati Personali. A questo scopo, è necessario estendere la tabella Profili e aggiungere un campo <strong>Rifiuto per CCPA</strong> . <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Leggi tutto</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Monitoraggio live del flusso di lavoro</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Ora puoi monitorare lo stato di esecuzione di tutti i flussi di lavoro sulla tua istanza utilizzando viste predefinite.</p>
   <p>Per ulteriori informazioni, consulta la documentazione <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status"></a>dettagliata.</p></td> 
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
<td> <p>Adobe Campaign consente di provare il nuovo formato <a href="https://amp.dev/about/email/">AMP per e-mail</a> interattivo, che consente agli esperti di marketing di includere componenti AMP nei messaggi per migliorare l'esperienza e-mail con contenuti avanzati, dinamici e interattivi, direttamente utilizzabili nel messaggio stesso.</p>
   <p>Questa funzionalità viene rilasciata come versione beta pubblica.</p>
   <p>Per ulteriori informazioni, consultate la documentazione <a href="../../delivery/using/defining-interactive-content.md"></a> dettagliata e il video <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html"></a>dell'esercitazione.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Secure SMS Messaging (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Gli SMS protetti ora sono supportati tramite il connettore SMPP generico esteso. Consente una connessione crittografata al provider.</p> <p><strong>Avviso</strong> Questa funzione richiede un certificato aggiornato su tutti i server. Certificati non validi, revocati o scaduti genereranno errori che influiranno sulle capacità di invio SMS complessive.</p><p>Per ulteriori informazioni, consulta la documentazione <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html"></a>dettagliata. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Risolte le vulnerabilità di Cross Site Scripting memorizzate nell&#39;interfaccia Campaign: convalida dei dati di input e codifica di output. (NEO-16810)
* È stato risolto un problema di sicurezza relativo all&#39;autorizzazione del profilo che poteva consentire l&#39;accesso a dati non autorizzati, rafforzando i criteri di restrizione dell&#39;accesso. (NEO-14445)

**Miglioramenti**

* Ottimizzazione del consumo di memoria per le notifiche push.
* Per l&#39;ottimizzazione delle prestazioni e dell&#39;archiviazione, è stata migliorata la gestione del file **logins.log** . Ora il file viene suddiviso in più file, uno ogni giorno con un massimo di 365 file conservati. [Leggi tutto](../../production/using/log-files.md)
* È ora possibile configurare l&#39;account esterno di Microsoft Dynamics CRM utilizzando le credenziali della password (password + nome utente) o il certificato (chiave privata). [Leggi tutto](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Sono stati aggiunti alcuni miglioramenti al connettore FDA Hadoop per migliorare l&#39;affidabilità
* È stato aggiunto un particolare carrello per controllare lo spazio su disco prima di consentire il caricamento di risorse pubbliche sul server.
* Sono state aggiunte nuove opzioni [](../../installation/using/configuring-campaign-options.md) campagna:
   * L&#39;opzione di configurazione **WdbcKillSessionPolicy** consente di influenzare il comportamento di arresto **** incondizionato in tutti i flussi di lavoro e le query di database PostgreSQL.
   * L&#39;opzione **NmsOperation_DeliveryPreparationWindow** consente di definire il numero di giorni al di sopra dei quali le consegne con stato incoerente verranno escluse dal conteggio delle consegne in esecuzione.
   * L&#39;opzione **WdbcOptions_TempDbName** consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server. In questo modo vengono ottimizzati backup e replica. [Leggi tutto](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * L&#39;opzione **XtkCleanup_NoStats** è stata migliorata per PostgreSQL per controllare meglio il comportamento della fase di ottimizzazione dell&#39;archiviazione del flusso di lavoro di pulizia del database. [Leggi tutto](../../production/using/database-cleanup-workflow.md#statistics-update)
* È stato aggiunto un meccanismo di blocco dell&#39;account all&#39;API **login()** . Consente di evitare ulteriori tentativi di accesso dopo un certo numero di tentativi di accesso consecutivi non riusciti in un intervallo di tempo specificato.
* Una nuova opzione **Massimo tempo** di esecuzione della personalizzazione nelle proprietà di consegna consente di definire un periodo di timeout per il runtime di personalizzazione, al fine di evitare che la fase di personalizzazione venga eseguita troppo a lungo. [Leggi tutto](../../delivery/using/personalization-fields.md#timing-out-personalization)
* L&#39;opzione del protocollo **** ftp è stata aggiunta per consentire l&#39;utilizzo di una configurazione proxy per le connessioni SFTP. [Leggi tutto](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nuovo supporto dell&#39;accesso proxy a un server esterno SFTP per gli ambienti interni.
* È stato aggiunto un tutorial specifico per impedire l&#39;installazione di pacchetti non compatibili con l&#39;istanza Campaign. [Leggi tutto](../../installation/using/installing-campaign-standard-packages.md)

_Sistemi obsoleti_

I seguenti sistemi ora sono [obsoleti](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) per le implementazioni di Campaign Classic:
* Apache 2.2
* Centos 6

Verifica di disporre delle versioni supportate di tutti i sistemi elencati nella più recente matrice di compatibilità delle campagne. [Leggi tutto](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

È ora disponibile la build 1.0.26 dell&#39;SDK iOS. In questa nuova build, abbiamo aggiunto il supporto di iOS 13. Questa nuova versione ora supporta la priorità delle notifiche e il nuovo processo di gestione dei token di registrazione per le notifiche push iOS 13. Se esegui applicazioni su una versione precedente dell’SDK, devi ricompilare le applicazioni con il nuovo SDK. Per ottenere l&#39;SDK, contatta l&#39;Assistenza clienti Adobe.

**Patch**

* È stato corretto un arresto anomalo della console che si verificava quando si aggiungeva una tabella collegata vuota nell&#39;attività del flusso di lavoro **di caricamento dati (RDBMS)** . (NEO-12213)
* È stato risolto un problema che poteva impedire l&#39;elaborazione di alcuni messaggi da parte del server di origine mid-Sourcing. (NEO-12395)
* È stato risolto un problema nel flusso di lavoro di pulizia del database quando si utilizzava l&#39;opzione di bande query con Teradata. (NEO-12399)
* È stato risolto un problema che interessava l&#39;analisi dei recapito con regola di tipologia, incluso il dominio ne.jp. (NEO-12609)
* È stato risolto un problema relativo agli aggiornamenti SMS via TLS che implicavano l&#39;applicazione di criteri di certificato più restrittivi. Questi aggiornamenti potrebbero causare un errore di connessione tra server di marketing e server di mid-sourcing in caso di certificato non aggiornato. (NEO-17698)
* È stato risolto un problema che si verificava durante l&#39;utilizzo del pulsante di connessione **** Test su un account esterno in un ambiente di mid-sourcing con autenticazione Vault. (NEO-12722)
* È stato risolto un problema relativo alle query che utilizzano le funzioni data con una connessione FDA Hadoop. (NEO-12847)
* È stato risolto un problema che si verificava durante la sostituzione di un’immagine nell’editor e-mail. (NEO-13098)
* È stato risolto un problema che poteva causare errori successivi all&#39;aggiornamento nelle cartelle eliminate o spostate in un&#39;altra posizione. (NEO-13118)
* È stato risolto un problema di visualizzazione dell&#39;immagine quando si utilizzava l&#39;opzione **Definisci immagine per dimensione** schermo dispositivo sui messaggi LINE. (NEO-13228)
* È stato risolto un problema di preparazione della consegna che si verificava quando l&#39;opzione **Escludi indirizzo duplicato durante la consegna** era deselezionata. (NEO-13240)
* È stato risolto un problema nei flussi di lavoro che si verificava quando si utilizzava l&#39;attività di trasferimento **dei** file per scaricare i file utilizzando l&#39;opzione **Elimina i file sorgente dopo il trasferimento** , con un nome contenente uno spazio. (NEO-13411)
* È stato risolto un problema con la pulizia della cache Tomcat che poteva causare problemi di memoria. (NEO-13456)
* È stato risolto un problema che si verificava durante l&#39;installazione del **controllo del motore delle offerte con il pacchetto di istanza** di esecuzione incorporato in un&#39;istanza di controllo esistente in esecuzione in Microsoft SQL 2017. (NEO-13539)
* È stato corretto un arresto anomalo della console che si verificava quando si deselezionavano gli URL tracciati in un messaggio e-mail dalla scheda Contenuto **** testo. (NEO-13545)
* È stato risolto un problema di codifica relativo al nome del mittente cinese. (NEO-13837)
* È stato corretto un errore che poteva verificarsi durante la visualizzazione dei dati di risposta del sondaggio da Esplora risorse. (NEO-14590)
* È stato risolto un problema che poteva causare una discrepanza tra la classificazione del registro di consegna e la tabella di quarantena. (NEO-16547)
* È stato risolto un problema relativo alle chiavi DKIM che non venivano incorporate nelle e-mail. (NEO-16804)
* È stato risolto un problema che causava la visualizzazione del codice di errore errato quando veniva utilizzato un token di sessione non valido nel contesto delle chiamate API per attivare gli eventi. Il codice di errore era &#39;HTTP 200 OK&#39; invece di &#39;HTTP 403 Vibidden&#39;. (NEO-16826)
* È stato risolto un problema che si verificava durante la visualizzazione dei rapporti di consegna tramite accesso Web. (NEO-17015)
* È stato risolto un problema di autenticazione IMS quando si effettuava l&#39;accesso ad Adobe Campaign. (NEO-17312)
* È stato risolto un problema che impediva l&#39;eliminazione delle e-mail in quarantena tramite il processo di gestione della privacy. (NEO-17314)
* Sono stati corretti i problemi di throughput dopo l&#39;aggiornamento a 9031 con il database SQL. (NEO-17558)
* È stato risolto un problema che interessava il connettore CRM con Salesforce. (NEO-17712)
* È stato risolto un problema di timeout durante l&#39;importazione di dati da un SFTP esterno. (NEO-19723)
* È stato risolto un problema durante l&#39;accesso ai modelli predittivi. (NEO-19713)
* È stato risolto un problema che interessava il campionamento casuale nell&#39;attività del flusso di lavoro **suddiviso** con il database FDA Hadoop. (NEO-16636)

