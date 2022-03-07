---
product: campaign
title: Versioni 2020
description: Ulteriori informazioni sulle versioni di Campaign Classic 2020
feature: Overview
role: User
level: Beginner
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: c228f827e91f25ee3a837f7fe6549ae4e5714ba3
workflow-type: tm+mt
source-wordcount: '6619'
ht-degree: 73%

---

# Versioni 2020{#release-2020}

![](../../assets/v7-only.svg)


## Versione 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Versione 20.3.3 - Build 9234 {#release-20-3-3-build-9234}

_11 gennaio 2021_

* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)
* È stato risolto un problema di regressione relativo al processo di generazione del broadlog che poteva causare l’arresto anomalo del processo MTA.

### ![](assets/do-not-localize/red_2.png) Versione 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 ottobre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), è necessario eseguire l’aggiornamento affinché sia il server di Campaign che la console client possano connettersi a Campaign dopo il **30 giugno 2021**. [Ulteriori informazioni](../../technotes/using/ims-updates.md)
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.
> * Se utilizzi l’integrazione Experience Cloud Triggers tramite autenticazione oAuth, devi passare ad Adobe I/O come descritto [in questa pagina](../../integrations/using/configuring-adobe-io.md). La modalità di autenticazione OAuth legacy con Campaign [è stata ritirata](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) a **settembre 2021**. Gli ambienti in hosting usufruiscono di una proroga fino al **23 febbraio 2022**. In qualità di cliente on-premise o ibrido, contatta l’Assistenza clienti Adobe per estendere il supporto a febbraio 2022. Devi fornire ad Adobe [l’AppID dell’applicazione OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional).


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
   * Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS. Per poter connettersi dopo il 30 giugno 2021 è obbligatorio l’aggiornamento della console server e client.
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
* È stato aggiunto il supporto dell’intervallo ID negativo per la sequenza nmsBroadlogId. Questa build regola il valore min_value della sequenza nmsBroadlogId in modo che includa l&#39;intervallo negativo. Nel caso in cui si disponga di un caso d’uso rigoroso che non consente ID negativi, ripristina il valore min_value della sequenza a 1.

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
* È stata corretta una regressione che poteva bloccare l’esportazione dei dati del flusso di lavoro in un database FDA (Teradata, Snowflake).

## Versione 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Versione 20.2.5 - Build 9188 {#release-20-2-5-build-9188}

_15 aprile 2021_

* È stata corretta una regressione della console client che causava messaggi di errore persistenti nella schermata di connessione IMS. (NEO-34821)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

_31 marzo 2021_

**Miglioramenti**

* È stato migliorato il modo per evitare arresti anomali in caso di chiamate di sapone non valide. Questo potrebbe causare l’interruzione del funzionamento dell’istanza quando si tenta di eseguire query complesse specifiche. (NEO-28796, NEO-30553)
* È stato risolto un problema di regressione che impediva l’invio di consegne SMS con TLS a causa della verifica del nome host. (NEO-29581)
* È stato risolto un problema che impediva il funzionamento dei collegamenti di tracciamento firmati su alcuni client e-mail. (NEO-28414, NEO-29615)
* È stata corretta una sequenza di ID di tracciamento quando si utilizzano i tag di tracciamento webApp che poteva causare conflitti con ID duplicati. (NEO-27931)
* È stato risolto un problema che causava l’arresto dei flussi di lavoro in esecuzione a causa del riavvio giornaliero del server wfserver. (NEO-30047)
* È stato risolto un problema di sicurezza relativo all’utilizzo delle chiamate API effettuate da utenti non amministratori che tentavano di sincronizzare i modelli Adobe Experience Manager. (NEO-32389, NEO-23487)
* È stato risolto un problema che causava l’arresto anomalo della console durante la chiusura di una finestra di dialogo di consegna su una consegna creata con da un modello. (NEO-31547)
* È stato risolto un problema che si verificava durante la creazione e il salvataggio di una consegna all’interno di **Targeting e flusso di lavoro** scheda di una campagna: l&#39;anteprima avrebbe esito negativo con il seguente errore. (NEO-29440)
* È stato risolto un problema con l’invio di risposte non valide da parte di Tomcat 8.5 che causava errori nei registri di messaggistica transazionale. (NEO-30858)
* È stato risolto un problema di regressione che causava il danneggiamento della memoria nella gestione dei thread esterni e un impatto sulle prestazioni.
* È stato risolto un problema che poteva causare un errore del flusso di lavoro Fatturazione quando si utilizzava una mappatura di destinazione personalizzata. La chiave primaria dello schema personalizzato viene memorizzata nella colonna &quot;sourceId&quot;, che consentiva solo valori interi. Ora consente sia valori interi che valori stringa. (NEO-25914, NEO-28146)
* È stata corretta una regressione che impediva l’utilizzo di alcuni componenti della console, come il selettore data e la gestione delle immagini nelle consegne. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Versione 20.2.4 - Build 9187 {#release-20-2-4-build-9187}

_15 aprile 2021_

* È stata corretta una regressione della console client che causava messaggi di errore persistenti nella schermata di connessione IMS. (NEO-34821)
* È stata corretta una regressione che impediva l’utilizzo di alcuni componenti della console, come il selettore data e la gestione delle immagini nelle consegne. (NEO-31453, NEO-31454)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

_22 dicembre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), è necessario eseguire l’aggiornamento affinché sia il server di Campaign che la console client possano connettersi a Campaign dopo il **30 giugno 2021**.  [Ulteriori informazioni](../../technotes/using/ims-updates.md)
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.
> * Se utilizzi l’integrazione Experience Cloud Triggers tramite autenticazione oAuth, devi passare ad Adobe I/O come descritto [in questa pagina](../../integrations/using/configuring-adobe-io.md). La modalità di autenticazione OAuth legacy con Campaign [è stata ritirata](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) a **settembre 2021**. Gli ambienti in hosting usufruiscono di una proroga fino al **23 febbraio 2022**. In qualità di cliente on-premise o ibrido, contatta l’Assistenza clienti Adobe per estendere il supporto a febbraio 2022. Devi fornire ad Adobe [l’AppID dell’applicazione OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional).


**Miglioramenti**

* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.
* L’autenticazione dell’integrazione dei trigger originariamente basata su oAUTH per accedere alla pipeline è stata modificata e spostata in Adobe I/O. [Ulteriori informazioni](../../integrations/using/configuring-adobe-io.md)
* Con la [fine del supporto del protocollo binario legacy del servizio APNs per iOS](https://developer.apple.com/news/?id=c88acm2b), tutte le istanze che lo utilizzano vengono aggiornate al protocollo HTTP/2 nella fase di post-aggiornamento.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)
* È stato risolto un problema che causava la disattivazione del connettore SMPP dopo un errore di connessione, impedendo l’invio di altre consegne SMS e causando problemi di prestazioni. (NEO-28609)
* È stato risolto un problema di arresto anomalo del server impedendo il danneggiamento della memoria durante la pulizia del parser di espressione. (NEO-26856)
* È stato risolto un problema che causava l’arresto anomalo del server durante la visualizzazione dei dati di destinazione del resto di un’attività **Split** in un flusso di lavoro.
* È stato risolto un problema che poteva mostrare un messaggio di errore durante il tentativo di visualizzare l’anteprima dei messaggi SMS dopo una query su uno schema diverso da **Destinatario** (nms:recipient). (NEO-27517)
* È stato risolto un problema che si verificava quando si effettuava una richiesta di connessione HTTPS con il numero di porta esplicitamente definito nel nome host, a causa del quale la chiamata non riusciva e si verificava un errore di certificato. (NEO-29146)
* È stato risolto un problema nella gestione del thread POSIX che generava file di dump di grandi dimensioni sull&#39;istanza di marketing. (NEO-28117, NEO-29281)
* Sono stati risolti dei problemi che potevano causare l’arresto anomalo del processo web durante la preparazione delle consegne o con un’anteprima ricorrente della consegna. (NEO-27790, NEO-27517)
* È stato risolto un problema che causava un errore nell’invio di consegne o prove se attivato da un operatore non amministratore. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **Rilascio di ottobre del nuovo Pannello di controllo Campaign** con configurazione dei domini tramite CNAME e nuove funzionalità di monitoraggio del database. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=it).

### ![](assets/do-not-localize/red_2.png) Versione 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_11 settembre 2020_

* È stato risolto un problema di regressione dovuto una singola funzione errata sulla parte di consegna, che generava un sovraccarico di memoria causando il blocco della preparazione della consegna. (NEO-27346)
* È stato risolto un problema di post-aggiornamento che disattivava Apache e il server web prima della ripubblicazione dell’applicazione web. (NEO-27155)
* È stato risolto un problema di regressione nella gestione dei modelli di HTML che causava la visualizzazione degli URL di tracciamento a causa di un’interpretazione errata delle schede. (NEO-25909)
* È stato risolto un problema relativo al flusso di lavoro di pulizia del database che poteva non riuscire a causa di un&#39;origine dati non gestita. (NEO-23160, NEO-23364)
* Il flusso di lavoro di pulizia ora svuota gli elenchi scaduti per batch di 100 invece che singolarmente.
* È stata corretta una regressione che impediva di modificare il nome interno di un account esterno. (NEO-27323)
* È stata corretta una regressione che causava un avvio errato del modulo nlserver (log degli errori) durante il post-aggiornamento.
* È stata migliorata la gestione degli aggiornamenti per la memoria condivisa. I passaggi aggiuntivi richiesti nella 20.2 non sono più necessari.

### ![](assets/do-not-localize/red_2.png) Versione 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_22 luglio 2020_

* È stato risolto un problema che impediva il funzionamento del tracking quando la funzione di firma era disabilitata. (NEO-26411)
* È stato risolto un problema che causava il blocco dei collegamenti non firmati da domini personalizzati in casi in cui dovevano essere consentiti. (NEO-25210)
* È stato risolto un problema che poteva impedire di aprire/fare clic sugli URL di tracking quando si utilizzavano alcune versioni precedenti di Outlook. (NEO-25688)
* È stato corretto un problema a causa del quale gli URL delle pagine speculari venivano definiti in modo non corretto nelle comunicazioni e-mail (a causa di un controllo errato dei caratteri ASCII). (NEO-26084)
* È stato risolto un problema relativo alla gestione degli URL di codifica nel servizio di anti-phishing. (NEO-25283)
* È stato risolto un problema che impediva il funzionamento del tracking degli URL tramite frammenti nei parametri di personalizzazione (tag di ancoraggio con cancelletto). (NEO-25774)
* È stato risolto un problema di tracking che si verificava con l’utilizzo di alcune formule personalizzate. (NEO-25277)
* È stato risolto un problema che impediva il tracking dei “clic di notifica” (notifiche push iOS e Android). (NEO-25965)
* È stato corretto un problema di regressione che interessava i campi calcolati in un flusso di lavoro causandone un’interruzione anomala. (NEO-25194)
* È stata corretta una regressione che impediva il funzionamento della creazione immediata di URL di tracking web. (NEO-20999)
* È stato risolto un problema di regressione relativo ai rapporti di consegna forniti, la cui visualizzazione risultava troncata dopo l’esportazione in PDF. (NEO-25757)
* È stato risolto un problema di arresto anomalo nella procedura guidata di distribuzione.
* È stato risolto un problema che poteva impedire il corretto funzionamento del flusso di lavoro di notifica dell’offerta dopo un post-aggiornamento.
* Il connettore iOS HTTP2 è stato migliorato (aggiornamenti di terze parti e gestione degli errori). (NEO-25904, NEO-25903)
* È stato aggiornato l’elenco jarsToSkip in catalina.properties, con la rimozione del riferimento a un file jar non più utilizzato (notifiche iOS).
* È stato risolto un problema che impediva la preparazione della consegna dopo un post-aggiornamento.
* Dopo il passaggio al [nuovo meccanismo di sequenza ID](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), tutte le applicazioni web che aggiornano la tabella dei destinatari vengono ripubblicate durante il post-aggiornamento.
* È stato risolto un problema di potenziale vulnerabilità XSS nel contenuto di consegna. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Nuova versione del Pannello di controllo Campaign di giugno** con monitoraggio dei profili attivi, audit del recapito messaggi del sottodominio e gestione delle chiavi GPG. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

### ![](assets/do-not-localize/red_2.png) Versione 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_8 giugno 2020_

**Novità?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Supporto delle emoticon</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Durante la progettazione di un messaggio in Campaign, puoi ora inserire facilmente gli emoticon nel corpo del messaggio, utilizzando un pulsante apposito. Gli emoticon possono essere aggiunti anche nella riga dell’oggetto dell’e-mail. Puoi personalizzare l’elenco degli emoticon disponibili nell’interfaccia.</p>
    <p>Per ulteriori informazioni sull’aggiunta degli emoticon, consulta la <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">documentazione dettagliata</a>. Scopri come personalizzare l’elenco degli emoticon <a href="../../delivery/using/customizing-emoticon-list.md">in questa sezione</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connettore FDA per Azure Synapse</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Puoi ora collegare la tua istanza di Campaign al database esterno di Azure Synapse. Questa connessione viene gestita tramite un nuovo account esterno.</p>
    <p>Azure Synapse è disponibile solo per gli ambienti Hybrid e On-Premise. Per ulteriori informazioni, consulta la <a href="../../installation/using/configure-fda-synapse.md">documentazione dettagliata</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Leggi sulla privacy in Thailandia e Brasile</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La Legge sulla Protezione dei Dati Personali (Personal Data Protection Act, PDPA) thailandese è la nuova legge sulla privacy che armonizza e modernizza i requisiti di protezione dei dati in Thailandia. </p>
   <p>La Legge Generale sulla Protezione dei Dati (Lei Geral de Proteção de Dados - LGPD) brasiliana entrerà in vigore all’inizio del 2021 per tutte le aziende che raccolgono o elaborano dati personali in Brasile.</p>
   <p>Queste normative si applicano ai clienti di Adobe Campaign che conservano dati per soggetti residenti in questi paesi. Oltre alle funzionalità relative alla privacy già disponibili in Campaign (compresa la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli degli utenti), stiamo sfruttando questa opportunità per includere funzionalità aggiuntive, al fine di aiutarti ad essere pronto per l’entrata in vigore di PDPA e LGPD:</p>
   <ul> 
     <li><p>Diritto di accesso e Diritto di eliminazione: stiamo sfruttando le funzionalità aggiunte per il GDPR e il CCPA. <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">Leggi tutto</a></p></li> 
     <li> <p>Durante la creazione di una richiesta di privacy tramite l’interfaccia o l’API di Campaign, ora selezioni il tipo di <strong>normativa</strong>: PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Ulteriori informazioni</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Per impostazione predefinita, per tutti i clienti è attivata la protezione migliorata per il tracking dei collegamenti nelle e-mail. In aggiunta, è disponibile una funzione di sicurezza avanzata che può essere abilitata contattando l’Assistenza clienti. Ulteriori dettagli sulla funzione e sui passaggi che i clienti non in hosting devono seguire per abilitarla sono disponibili nella [Lista di controllo protezione e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html). (NEO-24232)

* Per ottimizzare la protezione, l’algoritmo di hash MD5 utilizzato per generare i nomi dei file è stato rafforzato con l’algoritmo sha256 per il caricamento di file pubblici. (NEO-17044)

* Per rafforzare la protezione contro gli attacchi XSS, gli script lato client vengono disabilitati durante l’esecuzione di una pagina mirror. (NEO-17987)

* È stato risolto un problema che impediva al flusso di lavoro tecnico **Pulizia richieste privacy** di eliminare i dati di riconciliazione. (NEO-25168, NEO-21004)

* È stato risolto un problema con l’attività **File Transfer** che impediva il funzionamento dell’autenticazione basata su chiave SFTP su Debian 9. (NEO-23183)

**Miglioramenti della compatibilità**

Campaign supporta ora i seguenti sistemi:
* Sistemi operativi: Debian 10
* RDBMS: Oracle 18c e Oracle 19c
* FDA: Azure Synapse Analytics

Ulteriori informazioni nella [matrice di compatibilità di Campaign](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html).

**Miglioramenti**

* La messaggistica transazionale è stata migliorata per offrire una migliore user experience. Ora puoi annullare la pubblicazione di un modello di messaggio transazionale, eliminandolo dalle istanze di esecuzione. [Ulteriori informazioni](../../message-center/using/publishing-message-templates.md#template-unpublication).

* Sono disponibili nuove opzioni per impostare limitazioni durante l’invio di e-mail che includono immagini o allegati. Tali protezioni possono evitare problemi di prestazioni, il che è particolarmente utile con la messaggistica transazionale. [Leggi tutto](../../installation/using/configuring-campaign-options.md#delivery)

* La nuova opzione **Prepare the delivery parts in the database** consente di eseguire la preparazione della consegna direttamente all’interno del database, il che può accelerare notevolmente l’analisi. Questa opzione è disponibile solo per configurazioni specifiche. [Ulteriori informazioni](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Sono state migliorate le prestazioni dell’[attività del connettore della gestione delle relazioni con i clienti](../../workflow/using/crm-connector.md) per Microsoft Dynamics. (NEO-13303, NEO-12710)

* La versione della memoria condivisa è stata aumentata.

   >[!WARNING]
   >
   >Questo miglioramento richiede un ulteriore passaggio al termine dell’aggiornamento. Consulta la sezione **Evoluzioni tecniche** di seguito.

* Il flusso di lavoro di pulizia è stato migliorato. Anche le tabelle di lavoro isolate di tutti i flussi di lavoro eliminati vengono ora eliminate automaticamente dal flusso di lavoro di pulizia. [Ulteriori informazioni](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* I certificati per le app mobili iOS con il connettore iOS HTTP2 vengono ora convalidati prima dell’invio di notifiche push, impedendo in tal modo la mancata riuscita delle consegne a causa di certificati scaduti.

* La gestione delle connessioni proxy HTTP è stata migliorata. [Ulteriori informazioni](../../installation/using/file-res-management.md).

* Nuova opzione nelle attività dei flussi di lavoro **[!UICONTROL Javascript Code]** e **[!UICONTROL Advanced Javascript Code]** per interrompere l’esecuzione dopo un limite. Il valore predefinito è 1 ora. [Ulteriori informazioni](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Altre modifiche**

* I connettori SMS legacy sono ora obsoleti. Consulta la [pagina Funzioni obsolete](../../rn/using/deprecated-features.md).

* Non puoi più utilizzare il tuo account Litmus per predisporre e utilizzare il rendering della casella in entrata in Adobe Campaign. [Ulteriori informazioni](../../delivery/using/inbox-rendering.md).

* Per distinguere meglio le viste dalle cartelle, il colore dei nomi delle viste è stato modificato da blu scuro a ciano scuro. [Leggi tutto](../../platform/using/access-management-folders.md)

* Campaign Classic può ora essere collegato agli account per la gestione delle relazioni con i clienti di Microsoft Dynamics in hosting nelle aree geografiche di Regno Unito, India e Canada. Ciò vale per i tipi di distribuzione Office 365 e On-Premise (Dynamics 2015).

* Campaign esegue ora una verifica TLS per verificare che il nome host del server corrisponda al nome host nel certificato fornito.

* La tabella delle statistiche di consegna e tracking visualizza ora una voce per ogni consegna per il canale SMS, invece di una voce per destinatario della consegna.

* È stato aggiunto un messaggio di errore nel file di log per avvisare gli utenti quando il file scaricato ha dimensioni maggiori dello spazio su disco.

* Sono ora disponibili le seguenti funzioni per il connettore Snowflake: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Evoluzioni tecniche**

Questa nuova build aggiorna la memoria condivisa e richiede passaggi aggiuntivi per eseguire l’aggiornamento. In qualità di amministratore di Campaign, devi rimuovere i segmenti di memoria. Questi passaggi sono obbligatori, poiché i vecchi segmenti impediranno l’avvio di nlserver/nlsrvmod.

Su Windows, è necessario riavviare il sistema.

Su Debian/CentOs, è necessaria l’eliminazione della memoria condivisa. Di seguito sono riportati i passaggi da seguire:

Prima di eseguire l’aggiornamento, è necessario seguire questi passaggi:

1. Arrestare il servizio apache2 (http2 su CentOS) se è in esecuzione.
1. Arrestate il servizio nlserver (nlserver6 per build precedenti) se è in esecuzione.

Dopo l’aggiornamento:

1. Se la versione è precedente alla versione corrente, rimuovere la memoria condivisa utilizzando il comando **ipcrm**.
1. Avviare il servizio nlserver se era in esecuzione.
1. Avviare il servizio apache2 se era in esecuzione.

Di seguito sono riportate le righe di comando per Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Un esempio per Linux è disponibile in questa [pagina](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Patch**

* È stato risolto un problema di regressione minore nei log del flusso di lavoro di pulizia.
* È stato risolto un problema nell’attività **Loading (SOAP)** del flusso di lavoro durante l’analisi dei file WSDL.
* È stato risolto un problema che causava un errore durante l’aggiornamento di numerosi flussi di lavoro tramite un’attività **Survey** per elaborare in modo efficiente un elevato numero di flussi di lavoro.
* È stato risolto un problema di connettività intermittente durante l’elaborazione di messaggi inMail dall’MTA avanzato. (NEO-20380)
* È stato risolto un problema che impediva la corretta visualizzazione delle percentuali di hot click quando le immagini venivano visualizzate con una larghezza del 100% nell’HTML. (NEO-23203)
* È stato risolto un problema che impediva la visualizzazione completa del contenuto condizionale della consegna nel report sugli hot click. (NEO-18729)
* È stato risolto un problema che saltava il passaggio di approvazione del target quando si riprendeva un flusso di lavoro per inviare una consegna ricorrente. (NEO-18166)
* È stato risolto un problema che impediva al pulsante **Restart message preparation** di riprendere la consegna dopo la risoluzione di un errore nel flusso di lavoro. (NEO-13488)
* È stato risolto un problema che poteva causare un errore nelle consegne in modalità mid-sourcing durante la fase di aumento, in cui il target includeva destinatari con formati e-mail giapponesi. (NEO-23846)
* È stato risolto un problema di conversione del fuso orario con il connettore Snowflake (NEO-20105)
* È stato risolto un problema con gli account esterni che utilizzavano FTP su SSL. (NEO-20498)
* È stato risolto un problema che poteva impedire la visualizzazione delle immagini nelle consegne Line. (NEO-23207)
* È stato risolto un problema che causava un errore durante la pubblicazione di un’offerta. (NEO-23312)
* È stato risolto un problema con le notifiche push che consentiva il funzionamento delle connessioni di prova nelle app mobili, anche quando il certificato era scaduto. (NEO-22991)
* È stato risolto un problema che poteva interessare le notifiche push quando inviate con un’elevata frequenza. (NEO-20516)
* È stato risolto un problema che causava l’inclusione di duplicati nei dati di tracking anche se i log di tracking non ne includevano. (NEO-20040)
* È stato risolto un problema che causava l’invio di e-mail transazionali duplicate dopo la risoluzione di un errore di comunicazione del server di tracking. (NEO-23640)
* È stato risolto un problema che eliminava il valore del parametro di codifica durante il reindirizzamento da un URL di tracking (riguarda i caratteri giapponesi). (NEO-25637)
* È stato risolto un problema che poteva impedire il funzionamento di una query durante il confronto di numeri in virgola mobile. (NEO-23243)
* È stato risolto un problema che poteva impedire la visualizzazione del contenuto della colonna **Modified by** dopo il riavvio di un flusso di lavoro. (NEO-23035)
* È stato risolto un problema che causava un errore nel flusso di lavoro tecnico di tracking durante il download dei log da un secondo contenitore. (NEO-23159)
* È stato risolto un problema che poteva causare un errore dei flussi di lavoro durante l’esecuzione di un’attività **Enrichment**. (NEO-17338)
* È stato aggiunto un controllo al campo **Doubles to keep** nell’attività del flusso di lavoro **Deduplicazione** per impedire l’inserimento di valori nulli o negativi.
* La **procedura guidata di pianificazione** è stata rimossa dalle campagne ricorrenti per evitare di citare ore e minuti. Vengono prese in considerazione solo le date.
* È stato risolto un problema relativo ai campi di archiviazione aggiuntivi durante la creazione di consegne tramite l’opzione **Computed by a script** nell’attività del flusso di lavoro **Script**. (NEO-20609)
* È stato risolto un problema che impediva l’eliminazione dei flussi di lavoro fantasma nelle attività di pulizia del database.
* È stato risolto un problema che causava un errore del flusso di lavoro tecnico di **fatturazione (profili attivi)**. (NEO-19777)
* È stato risolto un problema di regressione che, nell’utilizzo della funzione del connettore ACS, impediva la connessione a un’istanza Campaign Standard (gestione errata della connessione FOH/FOH2). (NEO-23433)
* È stato risolto un problema che impediva la creazione di un’estensione dello schema su una chiave primaria con più colonne con una tabella Hadoop. (NEO-17390)
* È stato risolto un problema nell’attività **Loading (SOAP)** che poteva impedire il caricamento di file WSDL da un URL. (NEO-16924)
* È stato risolto un problema che impediva l’esecuzione di un **arresto incondizionato** tramite la console in caso di bilanciamento del carico di più server del flusso di lavoro attivi. (NEO-19556)
* È stato risolto un problema di regressione che causava l’arresto anomalo del flusso di lavoro di pulizia.
* È stato risolto un problema che poteva verificarsi durante la pubblicazione di un modello in un’istanza di esecuzione.
* È stato risolto un problema che poteva impedire l’esecuzione del flusso di lavoro tecnico collectPrivacyRequests. (NEO-20513, NEO-25169)
* Sono stati risolti i problemi che potevano verificarsi durante il tentativo di connessione ad Audience Manager dopo l’aggiornamento alla build 9080. (NEO-20511, NEO-25167)
* Sono stati risolti dei problemi che potevano verificarsi durante l’esportazione di report in formato PDF o XLS. (NEO-20982, NEO-23493, NEO-23348)
* È stato risolto un problema che poteva far sì che una consegna fosse visualizzata due volte nell’elenco di consegna dopo l’invio.
* È stato risolto un problema relativo alla preparazione delle consegne che poteva verificarsi quando la configurazione dell’indirizzamento era impostata per inviare la consegna tramite mid-sourcing.
* È stato risolto un problema che poteva visualizzare un messaggio di errore quando si faceva clic su un collegamento di un’applicazione web all’interno di un messaggio Line.
* È stato risolto un problema che eliminava la cronologia dell’attività **Incremental query** dopo l’esecuzione del flusso di lavoro di pulizia.
* È stato risolto un problema che si verificava durante la creazione di un account esterno di mid-sourcing a causa del quale l’opzione NmsMidSourcing_LastBroadLog_&lt;InternalName> risultava mancante.
* È stato risolto un problema di regressione della connessione al database che provocava il riavvio costante del server web a causa di un problema di codifica del database. Ciò poteva portare a un consumo eccessivo. (NEO-23264)


## Versione 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Versione 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_15 aprile 2021_

* È stata corretta una regressione della console client che causava messaggi di errore persistenti nella schermata di connessione IMS. (NEO-34821)

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

_23 dicembre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), è necessario eseguire l’aggiornamento affinché sia il server di Campaign che la console client possano connettersi a Campaign dopo il **30 giugno 2021**. [Ulteriori informazioni](../../technotes/using/ims-updates.md)
>
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.


* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Versione 20.1.3 - Build 9124{#release-20-1-3-build-9124}

_6 maggio 2020_

* È stato risolto un problema dell’attività **File Transfer** che impediva il funzionamento dell’autenticazione basata su chiave SFTP su Debian 9. (NEO-23183)

### ![](assets/do-not-localize/red_2.png) Versione 20.1.2 - Build 9123{#release-20-1-2-build-9123}

_13 marzo 2020_

* È stato risolto un problema che impediva la distribuzione della versione sui server Red Hat 7. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Versione 20.1 - Build 9122{#release-20-1-build-9122}

_17 febbraio 2020_

**Novità**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connettore FDA Snowflake</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake è un data warehouse cloud completamente gestito costruito per scalare sia a livello di storage che di calcolo. Con questo nuovo connettore, Adobe Campaign ora può sfruttare la potenza del Snowflake per eseguire la segmentazione dei big data. Questo connettore è disponibile per tutti i clienti, incluso ospitato da Adobe.</p>
    <p>Per ulteriori informazioni, consulta la <a href="../../installation/using/configure-fda-snowflake.md">documentazione dettagliata</a> e <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">video tutorial</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Miglioramenti al connettore FDA di hadoop</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Il connettore FDA del Hadoop è stato migliorato per supportare il Hadoop 3.0 e Cloudera.</p>
    <p>Per ulteriori informazioni, consulta la <a href="../../installation/using/configure-fda-hadoop.md">documentazione dettagliata</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

* Maggiore sicurezza nella configurazione dei report per proteggere dal click-jacking. Questo vale per i nuovi rapporti. Per applicare le modifiche ai vecchi rapporti, è necessario ripubblicarli. (NEO-13282)

* Risolvere un piccolo problema di memoria in cryptString. (NEO-20071)

* È stato migliorato il monitoraggio JSP per correggere una divulgazione IP interna. (NEO-16821)

* È stato risolto un problema a causa del quale le informazioni sulla traccia dello stack potevano essere visualizzate agli utenti non amministratori. (NEO-12388)

* È stata migliorata la gestione dei dati memorizzati nella cache delle sessioni precedenti. (NEO-17039)

* È stato risolto un problema che impediva al file logins.log di registrare i tentativi di accesso riusciti tramite IMS. (NEO-11004)

**Miglioramenti**

* iOS 13 è ora supportato con il connettore HTTP2.

* È stata migliorata la gestione della quarantena e la pulizia delle tabelle utilizzate dalla funzione di notifica push (nms:address e nms:appSubscriptionRcp). Per iOS (solo per il connettore HTTP2), i token disattivati vengono ora gestiti nello stesso modo di Android. Il flag disable ora è impostato nella tabella NmsAppSubscriptionRcp. [Maggiori informazioni](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* È stata aggiunta una nuova opzione nel **Codice JavaScript** e **Codice JavaScript avanzato** attività del flusso di lavoro per definire un periodo di timeout. Questo impedisce l’esecuzione della fase di esecuzione di JavaScript per troppo tempo. Se trascorre il periodo di timeout, il flusso di lavoro viene interrotto. Il timeout predefinito è di 1 ora. [Maggiori informazioni](../../workflow/using/sql-code-and-javascript-code.md)

* L’analisi della consegna viene ora interrotta quando non viene trovata alcuna affinità corrispondente sul server di mid-sourcing e viene visualizzato il messaggio di errore corrispondente.

* È ora supportato il failover del database per Postgres: quando il server di database si blocca e si riavvia, Campaign ora si riconnette automaticamente a esso.

* La **Inizio in sospeso** la visualizzazione è stata aggiunta al nodo Amministrazione > Audit > Stato flussi di lavoro . Questo ti consente di monitorare tutti i flussi di lavoro sull’istanza in attesa di essere avviati dalla **operationMgt** processo. Questa visualizzazione viene fornita con il pacchetto Campagne di marketing . [Leggi tutto](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Altre modifiche**

* Su Linux, l&#39;avvio del servizio nlserver ora utilizza un&#39;unità di sistema invece dello script /etc/init.d/nlserver6. La migrazione al nuovo schema di avvio viene eseguita automaticamente quando installi il pacchetto 20.1. /etc/init.d/nlserver6 è ancora disponibile ma per interagire con il servizio nlserver (avvio, riavvio, arresto, ecc.), si consiglia di utilizzare direttamente il comando systemctl.

* Le tabelle personalizzate più utilizzate sono state spostate dalla **xtkNewId** sequenza a sequenze dedicate. [Maggiori informazioni](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Prestazioni query migliorate che potrebbero essere influenzate da connessioni di database non necessarie.

* Sono state migliorate le prestazioni della procedura guidata di aggiornamento del database per ridurre il numero di istruzioni SQL al fine di ottimizzare il tempo di risposta.

* La gestione dei record del database è stata migliorata.

* La robustezza del pool di connessioni è stata migliorata, il che potrebbe impedire che si verifichino errori di connessione imprevisti troppo spesso.

* Le regole di convalida dell’indirizzo e-mail per inviare un indirizzo in quarantena in caso di errore soft sono state migliorate. [Maggiori informazioni](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Per Debian, Campaign ora utilizza le librerie PCRE di sistema quando sono disponibili.

* Campaign ora consente l’utilizzo di una libreria ODBC di sistema più recente.

* È stato aggiunto un timeout al servlet LINE quando si apre una connessione per caricare un’immagine ricca. Se il caricamento dell’immagine richiede troppo tempo, il servlet interrompe la connessione per evitare un collo di bottiglia.

**Patch**

* È stato risolto un problema di crittografia della chiave dell’account quando si utilizzava il connettore del Hadoop.

* È stato risolto un problema di regressione a causa dell’implementazione della certificazione SSL che causava un errore della connessione utente sul server Windows. (NEO-20629)

* È stato risolto un problema relativo all’attività di query incrementale in caso di ID flusso di lavoro negativi. (NEO-19779)

* È stato risolto un problema di codifica durante l’esecuzione di query tramite il connettore FDA Netezza. (NEO-19594)

* È stato risolto un problema che causava un errore durante l’utilizzo del metodo POST nel **Download Web** attività dell’evento del flusso di lavoro.

* È stato risolto un problema relativo alla generazione di proposte di offerta. (NEO-18176)

* È stato risolto un problema di visualizzazione del piè di pagina durante l’utilizzo del modello di modulo web di acquisizione.

* È stato risolto un problema che poteva causare l’arresto anomalo degli URL durante l’analisi del contenuto delle consegne continue. (NEO-16910)

* È stato risolto un problema relativo alla **Inizio** e **Fine** campi che non vengono calcolati durante la creazione di una nuova campagna.

* È stato risolto un problema relativo alla **Download file** attività del flusso di lavoro quando utilizzi un URL.

* È stato risolto un problema che si verificava durante l’anteprima di un elenco importato in un’attività query di un rapporto. (NEO-13119)

* È stato risolto un problema che causava la visualizzazione di un&#39;immagine obsoleta durante la selezione della **Alimentato da campagna** blocco di personalizzazione nell’editor e-mail.

* È stata migliorata la comunicazione di rete tra il client e il server.

* È stato risolto un problema che si verificava quando nella stessa campagna venivano creati troppi flussi di lavoro. Ora non puoi creare più di 28 flussi di lavoro. Viene visualizzato un avviso.

* È stato risolto un problema che si verificava con l’utilizzo di **Selezione di colonne** opzione di riconciliazione in un **Union** attività del flusso di lavoro.

* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si utilizzava un elenco di arricchimento danneggiato in un flusso di lavoro. (NEO-18096)

* Sono stati risolti diversi problemi di arresto anomalo della console che potevano verificarsi nei flussi di lavoro (NEO-18010, NEO-18032)

* È stato risolto un problema che consentiva l’esecuzione di un **Segnale esterno** attività del flusso di lavoro anche quando è stato disabilitato. (NEO-17524)

* È stato risolto un problema che si verificava durante la creazione di un nuovo schema.

* È stato risolto un problema di tracking durante l’invio di messaggi SMS. (NEO-19595)

* È stato risolto un problema che mostrava un numero di pubblico di destinazione errato negli indicatori di consegna.

* È stato risolto un problema che visualizzava percentuali errate durante la generazione di un rapporto descrittivo tramite un’attività del flusso di lavoro. (NEO-14314)

* È stato risolto un problema che causava la visualizzazione di numeri diversi nel report della velocità effettiva di consegna quando il parametro di visualizzazione dell&#39;ora. (NEO-11783)

* È stato risolto un problema che impediva agli indicatori di tracciamento dei messaggi transazionali di essere aggiornati dal flusso di lavoro Tracking. (NEO-17770)

* È stato risolto un problema di regressione che causava l’arresto anomalo del processo Web e il riavvio durante la richiesta di un’offerta tramite SOAP. (NEO-19482)

* È stato risolto un problema che impediva il caricamento di dati in risorse pubbliche se la directory di caricamento era una posizione condivisa remota. (NEO-19361)

* È stato risolto un problema che causava il **Importare tipi di pubblico da Adobe Experience Cloud** il workflow tecnico non riesce costantemente. (NEO-18463)

* È stato risolto un problema che impediva l’invio di consegne durante l’utilizzo di modelli importati da Experience Manager. (NEO-17540)

* È stato risolto un problema che si verificava dopo l’aggiornamento alla build 9032 e che impediva la connessione dell’istanza al server FTP tramite il protocollo SSL. (NEO-20498)

* È stato risolto un problema che si verificava durante l&#39;eliminazione, l&#39;inserimento o l&#39;aggiornamento di una grande quantità di dati con il **Update data** in un flusso di lavoro utilizzando uno schema FDA come dimensione di targeting. (NEO-13280)

* È stato risolto un problema che impediva l’invio di e-mail in caso di codice JavaScript all’esterno del tag di contenuto di HTML. (NEO-18628)

* È stato risolto un problema che si verificava durante il tentativo di visualizzazione della pagina speculare dai registri di consegna di un messaggio inviato. (NEO-17976)

* È stato risolto un problema che impediva la **Collegamento a una pagina speculare** blocco di personalizzazione da visualizzare nel **Contenuto testo** scheda dopo aver fatto clic **Importa HTML** in una consegna. (NEO-17568)

* È stato chiarito il messaggio di errore visualizzato quando si fa clic su un collegamento a una pagina speculare scaduta. (NEO-17340)

* È stato risolto un problema che impediva l&#39;utilizzo di alcuni pulsanti nel **Distribuzione dei dati** schermata di creazione.

* È stato risolto un problema che si verificava durante la pianificazione di un’attività di consegna in un’istanza con Asia/Calcutta come fuso orario. (NEO-20001)

* Ora viene visualizzato un errore quando una consegna presenta un problema di configurazione dell’affinità.

* È stato risolto un problema che causava la visualizzazione di un numero di tag di versione errato nel **Informazioni** menu.

* È stato risolto un problema che si verificava durante il tentativo di aggiornare l&#39;account di indirizzamento dalle proprietà di una consegna ricorrente in un flusso di lavoro. (NEO-18684)

* È stato risolto un problema che si verificava durante la connessione all’istanza tramite il modulo di reindirizzamento, che impediva la corretta pulizia della connessione una volta chiusa.
