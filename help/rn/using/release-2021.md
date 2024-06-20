---
product: campaign
title: Versioni di Campaign Classic 2021
description: Ulteriori informazioni sulle versioni di Campaign Classic 2021
feature: Release Notes
role: User
level: Beginner
hidefromtoc: true
exl-id: 0cd6bf20-da72-4cf0-9f5d-d4e8acdd324d
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 99%

---

# Versioni 2021{#release-2021}

## Versione 7.1 (21.1)

>[!CAUTION]
>Utilizza il menu **[!UICONTROL Help > About...]** per controllare il [numero di versione e di build](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) di Adobe Campaign. Tuttavia, per tutte le build comprese tra 9277 e 9343 elencate in questa pagina, il numero di versione è 7.0 anziché 7.1.
> 

### Versione 21.1.4 - Build 9343 {#release-21-1-4-build-9343}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_8 ottobre 2021_

**Patch**

* È stata migliorata la correzione del flusso di lavoro di fatturazione disponibile nella build 9342. In precedenza, per applicare la correzione era necessario riavviare manualmente il flusso di lavoro. Ora il successivo aggiornamento riavvia automaticamente il flusso di lavoro.

* È stato risolto un problema che poteva impedire la corretta gestione delle offerte quando si utilizzava il modulo **Interaction** con l’opzione [Power Booster](../../installation/using/power-booster-and-power-cluster.md). (NEO-39263)

* È stato corretto un errore di tipo “Impossibile trovare ipaffinity xxx nel mid server xxx” che poteva verificarsi durante l’invio della consegna se si utilizzava più di un’affinità IP in un’istanza multi-mid-sourcing. (NEO-37514)

### Versione 21.1.4 - Build 9342 {#release-21-1-4-build-9342}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_7 settembre 2021_

**Miglioramento della sicurezza**

* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi di navigazione nelle directory. (NEO-28547)

**Miglioramenti**

* Al termine del suo ciclo di vita, Flash è stato rimosso da tutte le funzioni e i componenti di Campaign correlati e sostituito con HTML5. Il tipo di grafico **Misuratore** è stato rimosso. (NEO-30330) [Ulteriori informazioni](../../reporting/using/creating-a-chart.md)
* Durante l’installazione della console client su Windows, il programma di installazione ora controlla se è presente un nodo del registro principale e, se necessario, ne crea uno. Questo evita potenziali problemi durante l’avvio della console. (NEO-34854)
* La funzione di firma di tracciamento è stata migliorata per evitare errori collegati al modo in cui strumenti di terze parti (client e-mail, browser Internet, ecc.) gestiscono i caratteri speciali. I parametri URL sono ora codificati.

**Altre modifiche**

* È stata risolta una regressione introdotta in 21.1.3 con un nuovo guardrail del il flusso di lavoro di fatturazione. Il flusso di lavoro di fatturazione veniva eseguito su istanze errate e si verificava un arresto anomalo durante il tentativo di inviare il rapporto di fatturazione che non veniva generato. Per applicare la correzione, è necessario riavviare manualmente il flusso di lavoro.
* I connettori Microsoft CRM precedentemente dichiarati obsoleti (per implementazioni Office 365 e on-premise) sono stati rimossi dall’interfaccia. [Ulteriori informazioni](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* In seguito alla migrazione a Tomcat 8, lo script di installazione di IIS è stato aggiornato per risolvere i problemi di integrazione di IIS. (NEO-31019)
* L’identificazione dell’origine dati è stata migliorata nelle schede dati e schema della finestra **Visualizza popolazione** delle transizioni del flusso di lavoro.
* Gli indici di database mancanti sono stati aggiunti ai seguenti schemi per evitare problemi di aggiornamento del database: xtk:rights, nms:dlvExclusion, nms:seedMember, nms:trackingUrl

**Patch**

* È stato risolto un problema che impediva il funzionamento del rapporto Hot Click quando le offerte erano collegate alla consegna. (NEO-26295)
* È stato risolto un problema a causa del quale l’attività **Flusso di lavoro secondario** non generava una tabella di output. (NEO-36242)
* Sono stati risolti diversi problemi riguardanti l’esportazione PDF del rapporto **Analisi descrittiva**. (NEO-25847)
* È stato risolto un problema che poteva causare un errore nelle consegne durante l’utilizzo di una consegna e-mail esterna. (NEO-37435)
* È stato corretto un errore che si verificava durante la connessione a Microsoft CRM tramite API web. Il messaggio di errore è stato rimosso perché le funzionalità non erano interessate.
* È stato risolto un problema di deduplica del registro di tracciamento quando il server mid veniva impostato come relay tra i server di tracciamento e di marketing. (NEO-36285)
* È stata corretta una regressione che impediva l’utilizzo di Vault come archivio di codice specifico.
* È stato risolto un problema che impediva l’utilizzo di variabili in un’attività del flusso di lavoro **Enrichment** quando la transizione in ingresso proveniva da un’origine dati FDA.
* È stato risolto un problema che poteva causare il mancato funzionamento degli URL nei messaggi e-mail.

### Versione 21.1.3 - Build 9330 {#release-21-1-3-build-9330}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_5 giugno 2021_

**Novità**


<table>
<thead>
<tr>
<th><strong>Nuova attività per flusso di lavoro: cambiare l’origine dati</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>La nuova attività <b>Change Data Source</b> consente di cambiare l’origine dati della tabella di lavoro di un flusso di lavoro. Questa possibilità offre maggiore flessibilità nella gestione dei dati tra diverse origini dati (FDA e database locale).</p>
<p>Nei flussi di lavoro di Adobe Campaign, i dati vengono gestiti utilizzando tabelle di lavoro (o temporanee). Durante l’esecuzione del flusso di lavoro, le tabelle di lavoro condividono i dati tra le varie attività del flusso di lavoro. Per impostazione predefinita, le tabelle di lavoro vengono create sullo stesso database dell’origine dei dati su cui si eseguono le query.</p>
<p>Per ulteriori informazioni, consulta la <a href="../../workflow/using/change-data-source.md">documentazione dettagliata</a>.</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>Integrazione con il Journey Orchestration Adobe</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>L’integrazione tra Journey Orchestration e Adobe Campaign Classic è ora GA. Consente al Journey Orchestration di inviare e-mail, notifiche push e SMS utilizzando le funzionalità di messaggistica transazionale di Adobe Campaign Classic.</p>
<p>La connessione tra le istanze Journey Orchestration e Campaign Classic viene impostata per Adobe al momento del provisioning.</p>
<p>Per ulteriori informazioni, consulta la <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=it">documentazione di Journey Orchestration</a>. Un caso d’uso dettagliato è presentato in questa <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=it">sezione</a></p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Miglioramenti al canale LINE</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Sono stati aggiunti i seguenti miglioramenti al canale LINE:
</p>
<ul> 
<li><p>Supporto per il tipo di messaggio video LINE</p></li>
<li><p>Supporto per API di registrazione partner LINE</p></li>
<li><p>Supporta un nuovo tentativo di invio del messaggio in caso di errore sul lato server LINE o di timeout della rete</p></li>
</ul>
<p>Per ulteriori informazioni consulta la <a href="../../delivery/using/line-channel.md">documentazione dettagliata</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Connettore FDA Vertica Analytics</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Ora puoi collegare l’istanza Adobe Campaign Classic al database esterno Vertica. Questa connessione viene gestita tramite un nuovo account esterno.</p>
<p>Per ulteriori informazioni consulta la <a href="../../installation/using/configure-fda-vertica.md">documentazione dettagliata</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Connettore FDA BigQuery Google</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Ora puoi collegare la tua istanza Adobe Campaign Classic al database esterno Google Big Query. Questa connessione viene gestita tramite un nuovo account esterno.
</p>
<p>Per ulteriori informazioni consulta la <a href="../../installation/using/configure-fda-google-big-query.md">documentazione dettagliata</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Miglioramenti della sicurezza**

* L’accesso al metodo API **xtk:session#GetCnxInfo** che restituisce i dettagli completi della connessione al database è ora limitato solo agli utenti amministratori. (NEO-27779)
* La funzione decryptString obsoleta è stata sostituita con decryptPassword nei file JavaScript relativi a alla gestione delle relazioni con i clienti.
* La funzione di firma di tracciamento è stata migliorata per ridurre il rischio di errori di reindirizzamento quando strumenti di terze parti (client e-mail, browser Internet, strumenti di sicurezza dei collegamenti sicuri) modificano il collegamento tracciato.
* È stato risolto un problema che poteva impedire il funzionamento degli URL tracciati quando contenevano caratteri maiuscoli. Il meccanismo di firma degli URL tracciati ora distingue tra maiuscole e minuscole. (NEO-28414)

**Aggiornamenti della compatibilità**

Campaign supporta ora i seguenti sistemi:
* Connettore FDA BigQuery Google
* Connettore FDA Vertica Analytics
* PostgreSQL 13

Ulteriori informazioni nella [matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md).

**Funzioni obsolete**

* A partire dalla versione 21.1 di Campaign, il Connettore dati di Adobe Analytics è diventato obsoleto. Se utilizzi questo connettore, devi adattare di conseguenza l’implementazione con il nuovo connettore Adobe Analytics.
* Il supporto per Debian 8 è ora obsoleto.
* In seguito alla rimozione di Oracle CRM in 20.3, l’account esterno correlato è stato rimosso dall’interfaccia.

Ulteriori informazioni sono disponibili nella pagina [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md).

**Miglioramenti**

* Durante il salvataggio di un flusso di lavoro sono stati aggiunti ulteriori controlli per verificare che i nomi delle attività siano univoci e che le transizioni siano sempre seguite da un’attività.
* Il flusso di lavoro tecnico **Fatturazione (fatturazione)** ora include le attività originariamente eseguite dal flusso di lavoro **Numero di profili di fatturazione attivi** (billingActiveContactCount), che è stato rimosso. Il rapporto e-mail inviato ogni mese dal flusso di lavoro fornisce ora informazioni sul numero di profili attivi nell’istanza. [Ulteriori informazioni](../../workflow/using/about-technical-workflows.md).
* È stato aggiunto il nuovo attributo **_keyOnMData** per poter utilizzare una chiave per le operazioni sui dati per memoria.

**Altre modifiche**

* È stato aggiunto un guardrail per consentire l’esecuzione del [flusso di lavoro tecnico di fatturazione](../../production/using/monitoring-processes.md#billing-report) solo sull’istanza di marketing.
* La terza parte openssl per Windows è stata aggiornata alla versione 1.1.1h.
* Nella descrizione del pacchetto Debian, nlserver è stato modificato in server Adobe Campaign Classic.

**Patch**

* È stato risolto un problema che si verificava durante la modifica del timeout sessione per disconnettersi dagli utenti dopo un periodo di tempo specifico in cui gli utenti rimanevano connessi anche dopo l’orario impostato.
* È stato risolto un problema a causa del quale le consegne venivano visualizzate come di sola lettura ma potevano ancora essere modificate nelle proprietà delle consegne.
* È stato corretto un errore che causava la scomparsa della barra degli strumenti di modifica durante la progettazione di un’applicazione web.
* È stato corretto un errore che causava la visualizzazione della versione testuale di un’e-mail con intestazioni Adobe Campaign Classic durante l’aggiunta di un collegamento a un’e-mail. (NEO-29211
* Durante l’utilizzo di FDA tramite la connessione HTTPS, il flusso di lavoro **Midsourcing (registri di consegna)** (defaultMidSourcingLog) si bloccava nell’arco temporale impostato dall’opzione **NmsMidSourcing_LogsPeriodHour**. Questo impediva l’aggiornamento dei record con i dati che si verificavano dopo tale arco temporale impostato. (NEO-30833)
* È stato risolto un problema che si verificava dopo l’esecuzione del flusso di lavoro di sincronizzazione del centro messaggi. Ogni volta che una cartella di oggetti di consegna veniva spostata in una cartella personalizzata, il flusso di lavoro riportava le consegne nella cartella **Cronologia dei messaggi transazionali** generica. (NEO-27445)
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore durante il tentativo di visualizzare i rapporti **Statistiche di trasmissione**, **Indicatori di tracciamento** e **Statistiche sulle attività di condivisione**.
* L’attività del flusso di lavoro **Oracle On Demand** è stata rimossa dall’interfaccia in seguito alla deprecazione del connettore di gestione delle relazioni con i clienti Oracle.
* È stato risolto un problema che arrestava l’esecuzione dei flussi di lavoro di elaborazione dopo il riavvio giornaliero del modulo server del flusso di lavoro (wfserver). (NEO-30047)
* È stato risolto un problema che impediva l’aggiornamento del documento di gestione MX, che poteva avere un impatto negativo sulla reputazione IP. (NEO-29897)
* Sono stati risolti i problemi che causavano arresti anomali del processo web durante la ricezione di una chiamata SOAP. (NEO-28796, NEO-29600)
* È stato risolto un problema che impediva la creazione dell’indice FDA di SAP HANA. (NEO-29664)
* È stato risolto un problema che poteva mantenere i messaggi transazionali nello stato **In attesa** durante l’esecuzione di chiamate SOAP contenenti un’intestazione. (NEO-28737)
* È stato risolto un problema che si verificava quando si utilizzava il connettore FDA Teradata: tutte le tabelle temporanee venivano create su un solo nodo del cluster, il che poteva finire per consumare l’intero spazio di spool e provocare l’arresto anomalo di Teradata. Le tabelle temporanee vengono ora generate su molti nodi. (NEO-28230)
* È stato risolto un problema che si verificava durante l’utilizzo di applicazioni web a causa del quale i tag di tracciamento generavano chiavi primarie non corrette nello schema **nms:trackingURL**. (NEO-27931)
* La compatibilità con ODBC 3.x è stata migliorata per garantire la precisione dei messaggi di errore.
* È stato risolto un problema che poteva causare arresti anomali della console in caso di utilizzo di modelli di contenuto personalizzati nelle consegne e-mail. (NEO-31547)
* È stato risolto un problema che impediva a Tomcat di inviare risposte valide a causa di una connessione lenta o di dimensioni di risposta elevate. (NEO-30858)
* È stato risolto un problema che poteva verificarsi durante la lettura di UUID da un database PostgreSQL.
* È stato risolto un problema che poteva causare problemi di prestazioni durante la ricerca di dati di proposta collegati alle offerte. (NEO-27554)
* È stato risolto un problema che causava la mancata risposta del processo web quando il servizio IMS veniva attivato ma non rispondeva.
* È stato risolto un problema che impediva l’invio di una consegna con un gruppo di bozze a causa di un meccanismo di unione specifico che non consentiva la personalizzazione della consegna. (NEO-14391)
* È stato risolto un problema che impediva l’invio di un avviso con l’attività di avviso se una query e un’attività di arricchimento miravano alla tabella di consegna. (NEO-25157)

### Versione 21.1.2 - Build 9282 {#release-21-1-2-build-9282}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_15 aprile 2021_

* La gestione delle password è stata migliorata per potenziare la sicurezza.
* È stato risolto un problema che poteva causare arresti anomali dell’MTA.

### Versione 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_22 febbraio 2021_

**Miglioramenti della sicurezza**

* Il meccanismo di autenticazione della console è stato migliorato per ottimizzare la sicurezza. (NEO-26944)
* È stato risolto un problema di sicurezza per rafforzare la protezione contro attacchi SSRF (Server Side Request Forgery). (NEO-28532)

**Aggiornamenti della compatibilità**

Campaign supporta ora i seguenti sistemi:

* L’utilizzo di un account Salesforce CRM esterno ora supporta la versione 49 delle API di Salesforce.

**Funzioni obsolete**

Il report **Technical Deliverability Monitoring** è ora obsoleto.

Ulteriori informazioni sono disponibili nella pagina [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md).

**Miglioramenti**

**Il servizio di feedback delle e-mail (EFS, Email Feedback Service)** è un servizio scalabile che acquisisce direttamente i commenti dall’MTA (Mail Transfer Agent) avanzato, migliorando così la precisione della generazione di rapporti. Questa funzionalità viene rilasciata come versione beta privata e sarà disponibile progressivamente per tutti i clienti nelle versioni future.

* Vengono ora acquisite tutte le categorie di feedback per la generazione di rapporti completi e precisi.
* Il calcolo dell’indicatore Delivered è ora basato sul feedback in tempo reale dall’MTA avanzato per una maggiore precisione e reattività.
* Il servizio EFS risolve il problema dei ritardi nella generazione sincrona di rapporti sui soft bounce.

**Altre modifiche**

* Utilizzando la compressione è stata migliorata la velocità di trasferimento per i registri di tracciamento di grandi dimensioni.
* La funzione Workflow Heatmap è stata migliorata per evitare timeout durante l’esecuzione di flussi di lavoro con più attività. (NEO-27423).
* È stato risolto un problema a causa del quale un’offerta poteva essere presentata anche dopo la data di fine. Campaign Classic ora prende in considerazione l’intera marca temporale della data di fine, anziché solo la data. (NEO-27590)
* Il collegamento Google+ è stato rimosso dal blocco di personalizzazione dei **collegamenti per condivisione social network**.
* È stato risolto un problema in seguito all’implementazione di una correzione di bug nell’ultima release. È stato aggiunto un controllo al nome host durante la connessione tramite SSL/TLS, che causava la mancata riuscita delle consegne di SMS. La verifica del nome host è stata disattivata per la maggior parte dei protocolli come POP3, SMS e HTTP con proxy e la verifica del certificato per l’account SMS esterno è stata migliorata con tre valori (NEO-29581). [Ulteriori informazioni](../../delivery/using/sms-protocol.md#skip-tls)

**Patch**

* È stato risolto un problema che impediva il funzionamento delle scelte rapide da tastiera Tab, Invio ed Esc nella nuova schermata di accesso.
* È stato risolto un problema di aggiornamento a causa del quale il nome di un flusso di lavoro appena creato veniva sostituito con il valore predefinito dopo il salvataggio (NEO-26106).
* È stato risolto un problema che si verificava durante l’esecuzione di flussi di lavoro in cui un nuovo campo veniva aggiunto come parte di un’attività **Enrichment** (Arricchimento) prima di un’attività **Delivery** (Consegna) utilizzando una mappatura di destinazione tramite **file esterno**: dei campi indesiderati venivano aggiunti alla mappatura di destinazione tramite **file esterno**. (NEO-27687)
* È stato risolto un problema che causava la modifica di alcuni caratteri nel codice sorgente alla riapertura di un’applicazione web creata e salvata in precedenza. (NEO-27597)
* È stato risolto un problema che poteva verificarsi durante l’aggiornamento a una build contenente il nuovo meccanismo di firma per il tracciamento dei collegamenti (da Build 19.1.4 e Campaign 20.2): se a un evento erano associati più modelli, l’aggiornamento poteva causare la selezione del modello errato durante l’invio del messaggio transazionale. (NEO-28326)
* È stato risolto un problema che causava la mancata risposta dell’MTA e l’impossibilità di elaborare le consegne, a meno che non venisse riavviato. (NEO-27455)
* È stato risolto un problema nel database MSSQL relativo alla gestione del fuso orario durante le operazioni di caricamento in massa per una colonna del tipo datetime. (NEO-27375)
* È stato corretto un problema di query del flusso di lavoro che si verificava con l’utilizzo delle funzioni xtk Redshift. SubDays, SubSeconds, SubMinutes e SubHours accettano ora entrambi i tipi di marca temporale Redshift (NEO-24962).
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore script durante il tentativo di visualizzare in anteprima un rapporto con accesso anonimo. (NEO-27081)
* È stato risolto un problema che poteva ridurre l’utilizzo di memoria sul server durante l’analisi della consegna.
* È stato risolto un problema che poteva impedire il funzionamento dell’istanza durante il tentativo di eseguire specifiche query complesse.
* È stato risolto un problema che poteva impedire l’esecuzione del flusso di lavoro tecnico per la **sincronizzazione delle pagine Twitter**. (NEO-28634)
* È stato risolto un problema che poteva mostrare un messaggio di errore relativo alla funzione decryptPassword quando si tentava di pubblicare su X (precedentemente noto come Twitter) utilizzando il modello di consegna **Tweet (twitter)**. (NEO-28216)
* È stato risolto un problema che si verificava durante l’utilizzo di un’attività **JavaScript** per effettuare una richiesta HTTP in un flusso di lavoro. Dopo aver definito il numero di porta nel nome host, la chiamata non riusciva e veniva visualizzato il seguente errore (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* È stato risolto un problema che impediva l’invio di nuove consegne con la personalizzazione dei dati di targeting (NEO-30323).
* È stato risolto un problema che causava diversi arresti anomali nell’istanza di marketing causando core file.
* È stato risolto un problema a causa del quale il flusso di lavoro di **tracciamento** non riusciva e veniva visualizzato il seguente errore (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* È stato risolto un problema che si verificava durante la creazione e il salvataggio di una consegna nella scheda **Targeting &amp; Workflow** di una campagna: l’anteprima non riusciva e veniva visualizzato il seguente errore (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* È stato corretto un errore che si verificava durante la configurazione di un account esterno tra un’istanza di marketing e un’istanza Adobe Campaign Standard o un’istanza midsourcing Campaign Classic e l’utilizzo dell’opzione “DisableFOH2=1”. Con l’utilizzo dell’opzione “DisableFOH2=1” nell’account esterno, le connessioni non venivano chiuse correttamente e si accumulavano, generando il seguente errore (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* È stato corretto un errore relativo alla funzione SMS che si verificava in caso di problemi di connessione tra il server e il provider. La connessione veniva quindi automaticamente disattivata dall’elemento secondario MTA. Adobe Campaign Classic non tentava il collegamento a questa connessione non funzionante finché non fosse stato avviato un nuovo elemento secondario.
