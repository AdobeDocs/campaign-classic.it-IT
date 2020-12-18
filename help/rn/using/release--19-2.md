---
solution: Campaign Classic
product: campaign
title: Versione 19.2
description: Versione 19.2
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 8%

---


# Versione 19.2{#release-19-2}

## ![](assets/do-not-localize/orange_2.png) Versione 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_07 febbraio 2020_

**Miglioramenti**

* È stato risolto un problema di regressione a causa dell&#39;implementazione della certificazione SSL che causava un errore di connessione utente sul server Windows. (NEO-20629)
* È stato risolto un problema che causava la visualizzazione di un numero di tag versione non corretto nel menu **Informazioni su**.

## ![](assets/do-not-localize/orange_2.png) Versione 19.2 - Build 9080 {#release-19-2-build-9080}

_02 dicembre 2019_

**Novità**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA è la nuova legge sulla privacy dello Stato della California che armonizza e aggiorna i requisiti di protezione dei dati in vigore dal 1° gennaio 2020. CCPA si applica a  clienti Adobe Campaign che detengono i dati per i soggetti dati residenti in California.</p>
    <p>Oltre alle funzionalità per la privacy già disponibili (compresa la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente),  Adobe Campaign facilita la preparazione dell'app:</p>
    <ul>
      <li>Diritto di accesso e Diritto di eliminazione: stiamo sfruttando le funzionalità aggiunte per il GDPR. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Leggi tutto</a></li>
      <li>È possibile verificare se un consumatore ha rinunciato alla vendita di Dati Personali. Per questo, è necessario estendere la tabella Profili e aggiungere un campo <strong>Rifiuto per CCPA</strong>. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Leggi tutto</a></li></td> 
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
<td> <p> Adobe Campaign consente di provare il nuovo formato interattivo <a href="https://amp.dev/about/email/">AMP for Email</a>, che consente agli esperti di marketing di includere componenti AMP nei messaggi per migliorare l'esperienza e-mail con contenuti avanzati, dinamici e interattivi, direttamente utilizzabili nel messaggio stesso.</p>
   <p>Questa funzionalità viene rilasciata come versione beta pubblica.</p>
   <p>Per ulteriori informazioni, consulta la <a href="../../delivery/using/defining-interactive-content.md">documentazione dettagliata</a> e il <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">video tutorial</a>.</p><br /></td> 
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
<td> <p>Gli SMS protetti ora sono supportati tramite il connettore SMPP generico esteso. Consente una connessione crittografata al provider.</p> <p><strong></strong> Attenzione: questa funzione richiede un certificato aggiornato su tutti i server. Certificati non validi, revocati o scaduti genereranno errori che influiranno sulle capacità di invio SMS complessive.</p><p>Per ulteriori informazioni, consulta la <a href="https://helpx.adobe.com/it/campaign/kb/sms-connector-protocol-and-settings.html">documentazione dettagliata</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Risolte le vulnerabilità di Cross Site Scripting memorizzate nell&#39;interfaccia Campaign: convalida dei dati di input e codifica di output. (NEO-16810)
* È stato risolto un problema di sicurezza relativo all&#39;autorizzazione del profilo che poteva consentire l&#39;accesso a dati non autorizzati, rafforzando i criteri di restrizione dell&#39;accesso. (NEO-14445)

**Miglioramenti**

* Ottimizzazione del consumo di memoria per le notifiche push.
* Per l&#39;ottimizzazione delle prestazioni e dell&#39;archiviazione, è stata migliorata la gestione del file **logins.log**. Ora il file viene suddiviso in più file, uno ogni giorno con un massimo di 365 file conservati. [Leggi tutto](../../production/using/log-files.md)
* È ora possibile configurare l&#39;account esterno di Microsoft Dynamics CRM utilizzando le credenziali della password (password + nome utente) o il certificato (chiave privata). [Leggi tutto](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Sono stati aggiunti alcuni miglioramenti al connettore Hadoop FDA per migliorare l&#39;affidabilità
* È stato aggiunto un particolare carrello per controllare lo spazio su disco prima di consentire il caricamento di risorse pubbliche sul server.
* Sono state aggiunte nuove [opzioni campagna](../../installation/using/configuring-campaign-options.md):
   * L&#39;opzione di configurazione **WdbcKillSessionPolicy** consente di influenzare il comportamento di **Arresto incondizionato** in tutti i flussi di lavoro e nelle query del database PostSQL.
   * L&#39;opzione **NmsOperation_DeliveryPreparationWindow** consente di definire il numero di giorni al di sopra dei quali le consegne con stato incoerente verranno escluse dal conteggio delle consegne in esecuzione.
   * L&#39;opzione **WdbcOptions_TempDbName** consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server. In questo modo vengono ottimizzati backup e replica. [Leggi tutto](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * L&#39;opzione **XtkCleanup_NoStats** è stata migliorata per PostgreSQL per controllare meglio il comportamento del passaggio di ottimizzazione dell&#39;archiviazione del flusso di lavoro di pulizia del database. [Leggi tutto](../../production/using/database-cleanup-workflow.md#statistics-update)
* È stato aggiunto un meccanismo di blocco dell&#39;account all&#39;API **access()**. Consente di evitare ulteriori tentativi di accesso dopo un certo numero di tentativi di accesso consecutivi non riusciti in un intervallo di tempo specificato.
* Una nuova opzione **Tempo massimo di esecuzione della personalizzazione** nelle proprietà di consegna consente di definire un periodo di timeout per il tempo di esecuzione della personalizzazione, al fine di evitare che la fase di personalizzazione venga eseguita troppo a lungo. [Leggi tutto](../../delivery/using/personalization-fields.md#timing-out-personalization)
* L&#39;opzione **ftp protocol** è stata aggiunta per consentire l&#39;utilizzo di una configurazione proxy per le connessioni SFTP. [Leggi tutto](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nuovo supporto dell&#39;accesso proxy a un server esterno SFTP per gli ambienti interni.
* È stato aggiunto un tutorial specifico per impedire l&#39;installazione di pacchetti non compatibili con l&#39;istanza Campaign. [Leggi tutto](../../installation/using/installing-campaign-standard-packages.md)

_Sistemi obsoleti_

I seguenti sistemi ora sono [obsoleti](https://helpx.adobe.com/it/campaign/kb/deprecated-and-removed-features.html) per le implementazioni dei Campaign Classic:
* Apache 2.2
* Centos 6

Verificate di disporre delle versioni supportate di tutti i sistemi elencati nella più recente matrice di compatibilità delle campagne. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

È ora disponibile la build 1.0.26 dell&#39;SDK iOS. In questa nuova build, abbiamo aggiunto il supporto di iOS 13. Questa nuova versione ora supporta la priorità delle notifiche e il nuovo processo di gestione dei token di registrazione per le notifiche push iOS 13. Se esegui applicazioni su una versione precedente dell’SDK, devi ricompilare le applicazioni con il nuovo SDK. Per ottenere l&#39;SDK, contatta  Assistenza clienti di Adobe.

**Patch**

* È stato risolto un problema di arresto anomalo che si verificava quando il campo **Aggiungi tabella collegata** era vuoto nell&#39;attività del flusso di lavoro **Caricamento dati (RDBMS)**. (NEO-12213)
* È stato risolto un problema che poteva impedire l&#39;elaborazione di alcuni messaggi da parte del server di origine mid-Sourcing. (NEO-12395)
* È stato risolto un problema nel flusso di lavoro di pulizia del database quando si utilizzava l&#39;opzione di bande query con Teradata. (NEO-12399)
* È stato risolto un problema che interessava l&#39;analisi dei recapito con regola di tipologia, incluso il dominio ne.jp. (NEO-12609)
* È stato risolto un problema relativo agli aggiornamenti SMS via TLS che implicavano l&#39;applicazione di criteri di certificato più restrittivi. Questi aggiornamenti potrebbero causare un errore di connessione tra server di marketing e server di mid-sourcing in caso di certificato non aggiornato. (NEO-17698)
* È stato risolto un problema che si verificava durante l&#39;utilizzo del pulsante **Test connection** su un account esterno in un ambiente mid-sourcing con autenticazione Vault. (NEO-12722)
* È stato risolto un problema relativo alle query che utilizzano le funzioni data con una connessione FDA Hadoop. (NEO-12847)
* È stato risolto un problema che si verificava durante la sostituzione di un’immagine nell’editor e-mail. (NEO-13098)
* È stato risolto un problema che poteva causare errori successivi all&#39;aggiornamento nelle cartelle eliminate o spostate in un&#39;altra posizione. (NEO-13118)
* È stato risolto un problema di visualizzazione dell&#39;immagine quando si utilizzava l&#39;opzione **Definisci immagine per dimensione schermo dispositivo** nei messaggi LINE. (NEO-13228)
* È stato risolto un problema di preparazione della consegna quando l&#39;opzione **Escludi indirizzo duplicato durante la consegna** era deselezionata. (NEO-13240)
* È stato risolto un problema nei flussi di lavoro che causava l&#39;utilizzo dell&#39;attività **Trasferimento file** per scaricare i file utilizzando l&#39;opzione **Elimina i file sorgente dopo il trasferimento**, con un nome contenente uno spazio. (NEO-13411)
* È stato risolto un problema con la pulizia della cache Tomcat che poteva causare problemi di memoria. (NEO-13456)
* È stato risolto un problema che si verificava durante l&#39;installazione del **controllo del motore delle offerte con il pacchetto di esecuzione** incorporato in un&#39;istanza di controllo esistente in esecuzione in Microsoft SQL 2017. (NEO-13539)
* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si deselezionavano gli URL tracciati in un messaggio e-mail, dalla scheda **Contenuto testo** a causa di una variabile non inizializzata. (NEO-13545)
* È stato risolto un problema di codifica relativo al nome del mittente cinese. (NEO-13837)
* È stato corretto un errore che poteva verificarsi durante la visualizzazione dei dati di risposta del sondaggio da Esplora risorse. (NEO-14590)
* È stato risolto un problema che poteva causare una discrepanza tra la classificazione del registro di consegna e la tabella di quarantena. (NEO-16547)
* È stato risolto un problema relativo alle chiavi DKIM che non venivano incorporate nelle e-mail. (NEO-16804)
* È stato risolto un problema che causava la visualizzazione del codice di errore errato quando veniva utilizzato un token di sessione non valido nel contesto delle chiamate API per attivare gli eventi. Il codice di errore era &#39;HTTP 200 OK&#39; invece di &#39;HTTP 403 Vibidden&#39;. (NEO-16826)
* È stato risolto un problema che si verificava durante la visualizzazione dei rapporti di consegna tramite accesso Web. (NEO-17015)
* È stato risolto un problema di autenticazione IMS durante l&#39;accesso a  Adobe Campaign. (NEO-17312)
* È stato risolto un problema che impediva l&#39;eliminazione delle e-mail in quarantena tramite il processo di gestione della privacy. (NEO-17314)
* Risolti problemi di throughput dopo l’aggiornamento a 9031 con il database SQL. (NEO-17558)
* È stato risolto un problema che interessava il connettore CRM con Salesforce. (NEO-17712)
* È stato risolto un problema di timeout durante l&#39;importazione di dati da un SFTP esterno. (NEO-19723)
* È stato risolto un problema durante l&#39;accesso ai modelli predittivi. (NEO-19713)
* È stato risolto un problema che interessava il campionamento casuale nell&#39;attività del flusso di lavoro **Dividi** con il database Hadoop FDA. (NEO-16636)
* Risolto un problema di regressione su  Oracle che causava la visualizzazione di alcune funzioni come non valide dopo l&#39;aggiornamento. (NEO-12759)


