---
title: Ultima versione
description: Note sulla versione dei Campaign Classic più recenti
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 3%

---


# Ultima versione{#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni apportate con l’ **ultima versione** Campaign Classic Release Candidate.

Per la versione Campaign Classic Gold Standard (ultima build GA), [fare riferimento a questa pagina](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versione 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 ottobre 2020_

**Novità?**

<table> 
<thead>
<tr> 
<th> <strong>Miglioramenti delle notifiche push iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Quando integrate l'app mobile con Campaign, dovete proteggere la comunicazione con il servizio APN (Apple Push Notification Service). Potete utilizzare l'autenticazione basata su certificato o su token.
</p>
<p>Queste due modalità di autenticazione sono ora disponibili per le app mobili iOS in Campaign Classic:
</p>
<ul> 
<li><p>Autenticazione basata su token (consigliato): questa modalità di autenticazione è basata su un file .p8. Questa modalità di autenticazione è più veloce in quanto ogni richiesta ad APN contiene il token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Ulteriori informazioni</a></p></li>
<li><p>Autenticazione basata su certificato: questa modalità di autenticazione è basata su un file .p12. Per ogni app, è necessario un certificato separato. Questo certificato viene consegnato da Apple tramite il vostro account sviluppatore. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Ulteriori informazioni</a></p></li> 
</ul>
<p>Scopri come selezionare la modalità di autenticazione in Campaign nella documentazione <a href="../../delivery/using/configuring-the-mobile-application.md"></a>dettagliata.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Miglioramenti delle notifiche push di Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Le notifiche push Android sono state migliorate per supportare l'API FCM HTTP v1 per l'autenticazione dei canali push Android. </p>
<p>Con la nuova versione API supportata, ora potete inviare messaggi di notifica FCM che forniscono funzionalità avanzate di messaggistica push. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Ulteriori informazioni</a></p> 
<p>Scoprite come configurare FCM HTTP v1 API per Android in  Adobe Campaign in <a href="../../delivery/using/configuring-the-mobile-application-android.md">questa sezione</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Miglioramenti della sicurezza**

* Caricamento sicuro delle librerie: Per proteggere dagli attacchi di precaricamento delle DLL, Campaign ora carica le DLL di Windows solo dal percorso DLL di sistema predefinito di Windows durante il caricamento del client della campagna (nlclient). [Ulteriori](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) informazioni (NEO-24147)
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-25661)
* È stato risolto un problema che si verificava durante la gestione delle richieste di privacy GDPR che impediva l&#39;eliminazione dei record dalle tabelle personalizzate con una relazione di secondo livello con la tabella Recipient. (NEO-25967)
* È stato risolto un problema di sicurezza utilizzando le chiamate API effettuate da utenti non amministratori quando tentavano di sincronizzare i modelli Adobe Experience Manager. (NEO-23487)

**Aggiornamenti della compatibilità**

Campaign supporta ora i seguenti sistemi:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Funzioni obsolete**

In 20.3 le seguenti funzioni sono obsolete:

* Il dominio demdex utilizzato per importare ed esportare audience nell&#39;Adobe Experience Cloud è obsoleto. Se utilizzate il dominio demdex per gli account esterni di importazione/esportazione, dovete adattare di conseguenza l&#39;implementazione. [Ulteriori informazioni](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Attiva l&#39;autenticazione dell&#39;integrazione originariamente basata sull&#39;impostazione dell&#39;autenticazione oAUTH per accedere alla pipeline ora è stata modificata e spostata nell&#39;I/O  Adobe. [Ulteriori informazioni](../../integrations/using/about-triggers.md)

Ulteriori informazioni sono disponibili nella pagina [Funzioni](../../rn/using/deprecated-features.md)obsolete e rimosse.

**Miglioramenti**

* Sono stati apportati diversi miglioramenti alla console **** Client:
   * Per evitare l&#39;incompatibilità con alcune limitazioni delle regole dell&#39;oggetto Criteri di gruppo di protezione Internet, la schermata di accesso alla console del client Campaign è stata sostituita da un modulo Windows standard incorporato.
   * È stato risolto un problema che si verificava durante la copia/incolla delle attività in un flusso di lavoro tramite la console Client a 64 bit. (NEO-27635)
   * Nel menu **Informazioni** , sono state aggiunte informazioni per distinguere le console da 64 a 32 bit.
* L’identificatore del flusso di lavoro ora viene visualizzato nei registri durante la ripresa di un flusso di lavoro, per identificare meglio quale flusso di lavoro è stato ripreso.
* È stato introdotto un nuovo cookie permanente: nllastdelid. Questo cookie (diverso da UUID230) memorizzerà deliveryId. Se il cookie di sessione non è presente, le informazioni del registro di trasmissione vengono recuperate dall&#39;ID consegna presente in questo cookie.
Questa modifica risolve un problema che si verificava al termine della sessione del browser: il cookie di sessione contenente deliveryId e broadcastId è stato eliminato. Senza deliveryId, non è possibile trovare le informazioni del registro di trasmissione e le informazioni della tabella di tracciamento risultano mancanti in caso di tracciamento permanente (ultima consegna).
Ulteriori informazioni sui cookie in [questa sezione](../../platform/using/privacy-and-recommendations.md#cookies).
* Miglioramento delle prestazioni del throughput di consegna di volumi elevati con il server di recapito riavviando il processo MTA prima dell&#39;invio della consegna.

**Altre modifiche**

* Quando si utilizza un percorso relativo per SFTP, `~/` i caratteri non vengono più aggiunti automaticamente. Se necessario, è possibile aggiungere manualmente `~/` caratteri al percorso, ma  Adobe consiglia di utilizzare un percorso **** assoluto.
* L&#39;autenticazione Windows NT è stata rimossa dai metodi di autenticazione disponibili durante la configurazione di un nuovo database con Microsoft SQL Server. [Leggi tutto](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Il flusso di lavoro di pulizia del database è stato ottimizzato per Teradata al fine di migliorare le prestazioni. (NEO-19959)
* È stato migliorato il messaggio di errore visualizzato durante l&#39;inserimento di un&#39;immagine da  Adobe Target e il nome tenant era vuoto nell&#39;account esterno.
* Nelle proprietà di consegna, l&#39; **[!UICONTROL Archive emails]** opzione è stata rinominata **[!UICONTROL Email BCC]**.
* Per migliorare la robustezza, selezionare Tutte le query con nodi non validi ora vengono rifiutate. Se è necessario disattivare il controllo e tornare al comportamento precedente, è possibile impostare XtkSecurity_Disable_QueryCheck su 0.

**Evoluzioni tecniche**

Tomcat è stato aggiornato dalla versione 7 (7.0.103) alla versione 8 (8.5.57).

La `tomcat-7` directory viene sostituita da una `tomcat-8` directory.

In Windows, _iis_neolane_setup.vbs_ e _apache_neolane.conf_ ora sono installati nella `conf` directory (anziché `tomcat-7/conf` in precedenza).

Su linux, _apache_neolane.conf_ è ora installato nella `conf` directory.

**Patch**

* È stato risolto un problema che poteva impedire il ricalcolamento delle statistiche di consegna.
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore durante il caricamento di un file CSV quando si utilizzava la build Campaign Classic 9080 connessa a un server che utilizzava una build precedente. (NEO-23218)
* È stato risolto un problema che poteva visualizzare un messaggio di errore durante la configurazione della procedura guidata di Microsoft Dynamics CRM per un account esterno. Ciò è dovuto a un problema di compatibilità con la versione API di MS Dynamics CRM più recente. (NEO-24528)
* È stato risolto un problema che impediva l&#39;esportazione di record di ricerca (ovvero dati composti da record di chiave esterna connessi ad altre tabelle) da Campaign Classic a Microsoft Dynamics utilizzando il connettore CRM. (NEO-23864)
* È stato risolto un problema che poteva impedire il recupero dei dati di Microsoft Dynamics se l&#39;opzione di indice **** automatico era abilitata nel connettore CRM. (NEO-25981)
* È stato risolto un problema con l&#39;autenticazione IMS che poteva lasciare le connessioni aperte anche se fossero state terminate. Le connessioni interrotte verranno automaticamente chiuse non appena terminate, per evitare l&#39;accumulo di connessioni e il consumo delle risorse del sistema. (NEO-25996)
* È stato risolto un problema che non mostrava alcun messaggio di errore quando la sincronizzazione del contenuto Adobe Experience Manager non riusciva per una consegna, a causa di una configurazione errata dell&#39;account esterno (account o password non corretti). Ora viene visualizzato un messaggio in caso di errore, che consente di identificare più facilmente il problema. (NEO-25586)
* È stato risolto un problema che si verificava selezionando il tipo di operazione **Aggiorna** nell&#39;attività dati **** Aggiorna. Se i dati da aggiornare non sono corretti, il flusso di lavoro risulterebbe in errore e non funzionerebbe. In caso di dati errati, il flusso di lavoro non avrà esito negativo e i record verranno memorizzati in una transizione **Rifiuta** in uscita. (NEO-23794)
* È stato risolto un problema che poteva impedire il funzionamento di flussi di lavoro contenenti flussi di lavoro secondari. (NEO-24036)
* È stato risolto un problema che impediva la visualizzazione del pulsante **Salva** durante la modifica di una descrizione del modello di campagna durante la copia-incolla di simboli come, ad esempio, i caratteri giapponesi. (NEO-27071)
* È stato risolto un problema che poteva impedire la modifica del server di tracciamento nella configurazione guidata dell&#39;istanza.
* È stato risolto un problema che impediva il salvataggio della descrizione di una campagna o di un modello di campagna quando si faceva clic all&#39;esterno della finestra prima di fare clic sul pulsante **Salva** . (NEO-27449)
* È stato risolto un problema che poteva impedire il funzionamento del flusso di lavoro tecnico **Numero di profili** di fatturazione attivi (fatturazioneActiveContactCount). Ciò potrebbe verificarsi se è stato eseguito un collegamento su un campo calcolato in un&#39;estensione dello schema. È stata creata una grande quantità di dati che potrebbe causare l&#39;esaurimento dello spazio temporaneo nel database. (NEO-24062)
* È stato risolto un problema relativo all&#39;attività di caricamento dei **dati (file)** , che poteva impedire l&#39;importazione di caratteri giapponesi da file TXT e CSV se questi erano posizionati alla fine del file. (NEO-24957)
* È stato risolto un problema relativo alle consegne continue che poteva impedire che i campi **Analisi avviata** e **Analisi completata** fossero popolati correttamente. (NEO-20755)
* È stato risolto un problema che poteva visualizzare un messaggio di errore durante il tentativo di visualizzare l&#39;anteprima dei messaggi SMS dopo una query su uno schema diverso da **Recipient** (nms:destinatario). (NEO-27517)
* È stato risolto un problema durante l&#39;utilizzo del connettore FDA del Snowflake . Un utente con diritti di accesso FDA  Snowflake non è stato in grado di eseguire una query su uno schema di Snowflake . Nei registri veniva visualizzato un errore di tipo &quot;Password non trovata&quot;. (NEO-23851)
* È stato risolto un problema che si verificava durante l&#39;utilizzo di un connettore FDA quando il nome dello schema FDA collegato era una sottostringa del nome di un elemento dello schema corrente. Ciò si verificava, ad esempio, se lo schema FDA era &quot;cust&quot; e uno degli elementi nello schema Destinatario era &quot;customer&quot;. Quando si recupera la colonna all&#39;interno dell&#39;elemento &quot;cliente&quot; e si aggiunge una colonna dallo schema FDA &quot;cust&quot;, mancava il valore per la colonna locale. (NEO-20193)
* È stato risolto un problema nei flussi di lavoro che si verificava durante il recupero dei record da un database esterno e il loro inserimento nel database Campaign. (NEO-26359)
* È stato risolto un problema nel flusso di lavoro tecnico **Aggiorna stato** evento: per corrispondere al ridimensionamento dei campi corrispondenti in entrata nell&#39;attività delle statistiche **di** consegna, il ridimensionamento di tre campi di destinazione nell&#39;attività **Aggiorna stati** di consegna è stato modificato da 32 a 64 bit. (NEO-11557) Ulteriori informazioni sul flusso di lavoro **Aggiorna stato** evento in [questa sezione](../../workflow/using/message-center--execution-.md).
* È stato risolto un problema nel rapporto Cronologia **eventi del Centro** messaggi che causava errori di script durante il tentativo di applicazione dei filtri e rendeva impossibile il filtro per un intervallo di date. (NEO-23365)
* È stato risolto un problema di interferenza tra i flussi di lavoro tecnici dei processi **** Campaign (operationMgt) e **Preview** (previsioni). Ciò si verificava quando le consegne programmate restavano nello stato &quot;Target Ready&quot; o &quot;Ready to be delivery&quot; (Pronto per essere consegnato). (NEO-20819)
* È stato risolto un problema di analisi XML che impediva la presenza dell&#39;identificatore XML nel campo dei dati in xtkOperator. Ciò causava un errore di postaggiornamento. (NEO-26113)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;attività **Trasferimento** file collegata a un account esterno di Azure crittografato in SSL, in cui la connessione veniva effettuata con HTTP invece che HTTPS. (NEO-26720)
* È stato risolto un problema per il database MSSQL a causa del quale si poteva verificare un errore con la procedura up_updatestats durante il flusso di lavoro di pulizia.
* È stato corretto un arresto anomalo che si verificava durante l&#39;arresto del processo Web se le richieste di interazione venivano ancora elaborate. (NEO-26447)
* È stato risolto un problema che impediva il funzionamento della funzione **NoNull** in Oracle DB dopo l&#39;aggiornamento 9032. (NEO-26488)
* È stato risolto un problema che causava un errore nel flusso di lavoro di tracciamento dopo l&#39;aggiornamento 9171 se il pacchetto LINEV2 era installato senza il pacchetto Message Center.
* È stato risolto un problema di scalabilità che impediva l&#39;aumento del pool di connessioni al numero desiderato di connessioni perché la stringa di connessione del database per l&#39;attributo &#39;APP&#39; finiva per ottenere un valore non valido. (NEO-25105)
* È stato risolto un problema a livello di configurazione proxy che impediva di accedere  Adobe Campaign dopo l&#39;ultimo aggiornamento di Windows 10. (NEO-27813)
* È stato risolto un problema che rendeva gli URL indesiderati visibili nelle e-mail inviate dopo l’importazione di modelli HTML contenenti collegamenti di tracciamento. (NEO-25909)
* È stato risolto un problema che causava l&#39;arresto anomalo del server durante la visualizzazione dei dati di destinazione del resto di un&#39;attività **Split** in un flusso di lavoro.
* È stato risolto un problema di arresto anomalo del server che impediva il danneggiamento della memoria durante la pulizia del parser di espressioni. (NEO-26856)
* È stato risolto un problema nell&#39;attività di arricchimento per il quale gli utenti non amministratori definivano variabili di istanza. (NEO-25653)