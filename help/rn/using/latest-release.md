---
solution: Campaign Classic
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 57093a687534ed1e7f77738ca233d4cc86cf40cf
workflow-type: tm+mt
source-wordcount: '1875'
ht-degree: 97%

---


# Ultima versione{#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni apportati con l’**ultima versione di Campaign Classic Release Candidate**.

Per la versione Campaign Classic Gold Standard (ultima build GA), [fare riferimento a questa pagina](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versione 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 ottobre 2020_

**Novità**

<table> 
<thead>
<tr> 
<th> <strong>Miglioramenti delle notifiche push in iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Nell’integrazione dell’app mobile con Campaign, si deve proteggere la comunicazione con il servizio APN (Apple Push Notification Service). È possibile utilizzare l’autenticazione basata su certificato o su token.
</p>
<p>Per le app mobili iOS in Campaign Classic ora sono disponibili queste due modalità di autenticazione:
</p>
<ul> 
<li><p>Autenticazione basata su token (consigliata): modalità di autenticazione basata su un file .p8. Questa modalità di autenticazione è più veloce in quanto ogni richiesta ad APN contiene il token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Ulteriori informazioni</a></p></li>
<li><p>Autenticazione basata su certificato: modalità di autenticazione basata su un file .p12. Per ogni app, è necessario un certificato separato. Questo certificato viene consegnato da Apple tramite l’account sviluppatore personale. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Ulteriori informazioni</a></p></li> 
</ul>
<p>Scopri come selezionare la modalità di autenticazione in Campaign nella <a href="../../delivery/using/configuring-the-mobile-application.md">documentazione dettagliata</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Miglioramenti delle notifiche push in Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Le notifiche push in Android</a> sono state migliorate per supportare l’API FCM HTTP v1 per l’autenticazione dei canali push Android. </p>
<p>Con il supporto della nuova versione API, ora è possibile inviare messaggi di notifica FCM che forniscono funzionalità avanzate di messaggistica push. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Ulteriori informazioni</a></p> 
<p>Scopri come configurare l’API FCM HTTP v1 API per Android in Adobe Campaign in <a href="../../delivery/using/configuring-the-mobile-application-android.md">questa sezione</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

>[!CAUTION]
>
>Questa versione include un nuovo protocollo di connessione: l&#39;aggiornamento è obbligatorio sia per il server Campaign che per la console client per poter connettersi a Campaign dopo il 21 marzo 2021.

**Miglioramenti della sicurezza**

* Caricamento sicuro delle librerie: per proteggere dagli attacchi di precaricamento delle DLL, Campaign ora carica le DLL di Windows solo dal percorso predefinito di sistema di Windows durante il caricamento del client Campaign (nlclient). [Ulteriori informazioni](https://support.microsoft.com/it-it/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-25661)
* È stato risolto un problema, riscontrato durante la gestione delle richieste di privacy GDPR, che impediva l’eliminazione dei record dalle tabelle personalizzate con una relazione di secondo livello con la tabella Destinatario. (NEO-25967)
* È stato risolto un problema di sicurezza relativo all’utilizzo delle chiamate API effettuate da utenti non amministratori che tentavano di sincronizzare i modelli Adobe Experience Manager. (NEO-23487)

**Aggiornamenti della compatibilità**

Campaign supporta ora i seguenti sistemi:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Ulteriori informazioni nella [matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md).

**Funzioni obsolete**

Nella 20.3 le seguenti funzioni sono diventate obsolete:

* Il dominio demdex, utilizzato per importare ed esportare pubblici nell’Adobe Experience Cloud, è diventato obsoleto. Se utilizzi il dominio demdex per l’importazione/esportazione degli account esterni, devi adattare di conseguenza l’implementazione. [Ulteriori informazioni](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* L’autenticazione dell’integrazione dei trigger, originariamente basata su OAUTH per accedere alla pipeline ora è stata modificata e spostata in Adobe I/O. [Ulteriori informazioni](../../integrations/using/configuring-adobe-io.md)

Ulteriori informazioni sono disponibili nella pagina [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md).

**Miglioramenti**

* Sono stati apportati diversi miglioramenti alla **console Client**:
   * Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS. Per poter connettersi dopo il 21 marzo 2021, è necessario aggiornare la console server e client.
   * Per evitare l’incompatibilità con alcune limitazioni delle regole dell’oggetto Criteri di gruppo di protezione Internet, la schermata di accesso alla console del client Campaign è stata sostituita da un modulo Windows standard incorporato.
   * È stato risolto un problema che si verificava durante l’utilizzo di copia/incolla delle attività in un flusso di lavoro tramite la console Client a 64 bit. (NEO-27635)
   * Nel menu **Informazioni** sono state aggiunte informazioni per distinguere le console da 64 e da 32 bit.
* Nei registri, durante la ripresa di un flusso di lavoro, ora viene visualizzato un identificatore che consente di individuare meglio quale flusso è stato ripreso.
* È stato introdotto un nuovo cookie permanente: nllastdelid. Questo cookie (diverso da UUID230) memorizzerà deliveryId. Se il cookie di sessione non è presente, le informazioni del registro di trasmissione vengono recuperate dal deliveryId presente in questo cookie.
Questa modifica risolve un problema che si verificava al termine della sessione del browser: il cookie di sessione contenente deliveryId e broadlogId veniva eliminato. Senza deliveryId, non è possibile trovare le informazioni del registro di trasmissione e le informazioni della tabella di tracking risultano mancanti in caso di tracking permanente (ultima consegna).
Ulteriori informazioni sui cookie in [questa sezione](../../platform/using/privacy-and-recommendations.md#cookies).
* Il riavvio del processo MTA prima dell’invio della consegna ha migliorato le prestazioni del throughput di consegna di volumi elevati con il server di recapito.

**Altre modifiche**

* Quando si utilizza un percorso relativo per SFTP, i caratteri `~/` non vengono più aggiunti automaticamente. Se necessario, è possibile aggiungere manualmente caratteri `~/` al percorso, ma Adobe consiglia di utilizzare un **percorso assoluto**.
* L’autenticazione Windows NT è stata rimossa dai metodi di autenticazione disponibili durante la configurazione di un nuovo database con Microsoft SQL Server. [Leggi tutto](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Il flusso di lavoro di pulizia del database è stato ottimizzato per Teradata al fine di migliorare le prestazioni. (NEO-19959)
* È stato migliorato il messaggio di errore visualizzato durante l’inserimento di un’immagine da Adobe Target che lasciava il nome del tenant vuoto nell’account esterno.
* Nelle proprietà di consegna, l’opzione **[!UICONTROL Archive emails]** è stata rinominata **[!UICONTROL Email BCC]**.
* Per migliorare la robustezza, ora vengono rifiutate le query selectAll con nodi non validi. In caso di necessità si può disattivare il controllo e tornare al comportamento precedente, impostando XtkSecurity_Disable_QueryCheck su 0.

**Evoluzioni tecniche**

Tomcat è stato aggiornato dalla versione 7 (7.0.103) alla versione 8 (8.5.57).

La directory `tomcat-7` viene sostituita da una directory `tomcat-8`.

In Windows, _iis_neolane_setup.vbs_ e _apache_neolane.conf_ ora sono installati nella directory `conf` (in precedenza era `tomcat-7/conf`).

Su linux, _apache_neolane.conf_ è ora installato nella directory `conf`.

**Patch**

* È stato risolto un problema che poteva impedire il ricalcolo delle statistiche di consegna.
* È stato risolto un problema che mostrava un messaggio di errore durante il caricamento di un file CSV utilizzando la build 9080 di Campaign Classic connessa a un server che utilizzava una build precedente. (NEO-23218)
* È stato risolto un problema che poteva mostrare un messaggio di errore durante la configurazione della procedura guidata di Microsoft Dynamics CRM per un account esterno. Ciò era dovuto a un problema di compatibilità con la versione più recente dell’API di MS Dynamics CRM. (NEO-24528)
* È stato risolto un problema che impediva l’esportazione di record di ricerca (ovvero dati composti da record di chiave esterna connessi ad altre tabelle) da Campaign Classic a Microsoft Dynamics utilizzando il connettore di gestione delle relazioni con i clienti. (NEO-23864)
* È stato risolto un problema che poteva impedire il recupero dei dati di Microsoft Dynamics se nel connettore di gestione delle relazioni con i clienti era abilitata l’opzione di **Indice automatico**. (NEO-25981)
* È stato risolto un problema con l’autenticazione IMS che poteva lasciare le connessioni aperte anche dopo essere state terminate. Le connessioni terminate ora verranno automaticamente chiuse non appena giunte al termine, per evitare l’accumulo di connessioni e il consumo delle risorse del sistema. (NEO-25996)
* È stato risolto un problema che non mostrava alcun messaggio di errore quando per una consegna non riusciva la sincronizzazione del contenuto Adobe Experience Manager, a causa di una configurazione errata dell’account esterno (account o password non corretti). Ora in caso di errore viene visualizzato un messaggio che consente di identificare più facilmente il problema. (NEO-25586)
* È stato risolto un problema che si verificava selezionando il tipo di operazione **Aggiorna** nell’attività **Aggiorna dati**. Se i dati da aggiornare erano errati, il flusso di lavoro restituiva un errore e aveva esito negativo. In caso di dati errati, il flusso di lavoro non avrà esito negativo e i record verranno memorizzati in una transizione in uscita **Rifiutati**. (NEO-23794)
* È stato risolto un problema che poteva impedire il funzionamento di flussi di lavoro contenenti flussi di lavoro secondari. (NEO-24036)
* È stato risolto un problema che impediva la visualizzazione del pulsante **Salva** durante la modifica di una descrizione del modello della campagna con copia-incolla di simboli come, ad esempio, i caratteri giapponesi. (NEO-27071)
* È stato risolto un problema che poteva impedire la modifica del server di tracking nella configurazione guidata dell’istanza.
* È stato risolto un problema che impediva il salvataggio della descrizione di una campagna o di un modello di campagna facendo clic all’esterno della finestra prima di fare clic sul pulsante **Salva**. (NEO-27449)
* È stato risolto un problema che poteva impedire il funzionamento del flusso di lavoro tecnico **Numero di profili di fatturazione attivi** (billingActiveContactCount). Il problema poteva verificarsi in caso di esecuzione di un collegamento su un campo calcolato in un’estensione dello schema. Veniva creata una grande quantità di dati che poteva causare l’esaurimento dello spazio temporaneo nel database. (NEO-24062)
* È stato risolto un problema relativo all’attività di **caricamento dei dati (file)**, che poteva impedire l’importazione di caratteri giapponesi da file TXT e CSV se questi erano posizionati alla fine del file. (NEO-24957)
* È stato risolto un problema relativo alle consegne continue, che poteva impedire il corretto popolamento dei campi **Analisi avviata** e **Analisi completata**. (NEO-20755)
* È stato risolto un problema che poteva mostrare un messaggio di errore durante il tentativo di visualizzare l’anteprima dei messaggi SMS dopo una query su uno schema diverso da **Destinatario** (nms:recipient). (NEO-27517)
* È stato risolto un problema che si verificava con l’utilizzo del connettore FDA Snowflake. Un utente con diritti di accesso FDA Snowflake non riusciva a eseguire una query su uno schema di Snowflake. Nei registri veniva visualizzato un errore di tipo “Password non trovata”. (NEO-23851)
* È stato risolto un problema che si verificava quando, utilizzando un connettore FDA, il nome dello schema FDA collegato era una sottostringa del nome di un elemento dello schema corrente. Ciò si verificava, ad esempio, se lo schema FDA era “cust” e uno degli elementi nello schema Destinatario era “customer”. Nel recuperare la colonna all’interno dell’elemento “cliente”, aggiungendo una colonna dallo schema FDA “cust” mancava il valore per la colonna locale. (NEO-20193)
* È stato risolto un problema nei flussi di lavoro che si verificava recuperando i record da un database esterno e inserendoli nel database Campaign. (NEO-26359)
* È stato risolto un problema nel flusso di lavoro tecnico **Aggiorna stato evento**: per mantenere l’equivalenza dei campi corrispondenti in entrata nell’attività **Statistiche di consegna**, il dimensionamento di tre campi di destinazione nell’attività **Aggiorna stati di consegna** è stato modificato da 32 a 64 bit. (NEO-11557) Ulteriori informazioni sul flusso di lavoro **Aggiorna stato evento** in [questa sezione](../../workflow/using/about-technical-workflows.md).
* È stato risolto un problema nel report **Cronologia eventi del centro messaggi**, che causava errori di script durante il tentativo di applicazione dei filtri e rendeva impossibile il filtro per un intervallo di date. (NEO-23365)
* È stato risolto un problema di interferenza tra i flussi di lavoro tecnici **Processi di Campaign** (operationMgt) e **Preview** (previsioni). Ciò si verificava quando le consegne programmate restavano nello stato “Target Ready” (Pronto per la destinazione) o “Ready to be delivered” (Pronto per essere consegnato). (NEO-20819)
* È stato risolto un problema di analisi XML che impediva la presenza dell’identificatore XML nel campo mdata in xtkOperator. Ciò causava un errore di post aggiornamento. (NEO-26113)
* È stato risolto un problema che si verificava durante l’utilizzo dell’attività **Trasferimento file** collegata a un account esterno di Azure crittografato in SSL, se la connessione veniva effettuata con HTTP invece che HTTPS. (NEO-26720)
* È stato risolto un problema del database MSSQL che poteva provocare un errore con la procedura up_updatestats durante il flusso di lavoro di pulizia.
* È stato corretto un arresto anomalo che si verificava durante l’arresto del processo Web se le richieste di interazione erano ancora in elaborazione. (NEO-26447)
* È stato risolto un problema che impediva l’operazione della funzione **NoNull** in Oracle DB dopo l’aggiornamento 9032. (NEO-26488)
* È stato risolto un problema che causava un errore nel flusso di lavoro di tracking dopo l’aggiornamento 9171 se il pacchetto LINEV2 era installato senza il pacchetto Message Center.
* È stato risolto un problema di scalabilità che impediva l’aumento del pool di connessioni al numero desiderato perché la stringa di connessione del database per l’attributo APP finiva per ottenere un valore non valido. (NEO-25105)
* È stato risolto un problema a livello di configurazione proxy che impediva di accedere ad Adobe Campaign dopo l’ultimo aggiornamento di Windows 10. (NEO-27813)
* È stato risolto un problema che rendeva visibili gli URL indesiderati nelle e-mail inviate dopo l’importazione di modelli HTML contenenti collegamenti di tracking. (NEO-25909)
* È stato risolto un problema che causava l’arresto anomalo del server durante la visualizzazione dei dati di destinazione del resto di un’attività **Split** in un flusso di lavoro.
* È stato risolto un problema di arresto anomalo del server impedendo il danneggiamento della memoria durante la pulizia del parser di espressione. (NEO-26856)
* È stato risolto un problema nell’attività di arricchimento con variabili di istanza definite da utenti non amministratori. (NEO-25653)