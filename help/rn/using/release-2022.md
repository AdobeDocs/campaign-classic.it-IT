---
product: campaign
title: Versioni di Campaign Classic 2022
description: Ulteriori informazioni sulle versioni di Campaign Classic 2022
feature: Release Notes
role: User
level: Beginner
hide: true
hidefromtoc: true
exl-id: 28490323-41d0-4d61-b309-6892fb826d21
source-git-commit: 62fc46e45078fce56eadda3518251e61244bf5d0
workflow-type: ht
source-wordcount: '2099'
ht-degree: 100%

---

# Versioni 2022{#release-2022}

## Versione 7.3.1 - Build 9352 {#release-7-3-1}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_1 luglio 2022_

**Novità**

<table> 
<thead>
<tr> 
<th> <strong>Notifiche sensibili al tempo</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Con iOS 15, Apple ha aggiunto il concetto di “notifiche urgenti” che permette allo sviluppatore dell’app di ignorare la modalità di attivazione quando una notifica è considerata urgente e deve quindi raggiungere l’utente in tempo reale.</p>
<p>Consulta la <a href="../../delivery/using/create-notifications-ios.md">documentazione dettagliata</a> per scoprire come creare una notifica sensibile.</p>
</td> 
</tr> 
</tbody> 
</table>

**Aggiornamenti della compatibilità**

* L’SDK di Adobe Campaign ora supporta Android 12 e iOS 15 per le notifiche push.
* Adobe Campaign è ora compatibile con MySQL 8.
* Adobe Campaign è ora compatibile con Windows 11.
* Adobe Campaign è ora compatibile con Debian 11. Per ulteriori informazioni, consulta questa [nota tecnica](../../technotes/using/tech-stack-upgrade.md).

Consulta la [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Miglioramenti**

* Dopo la fine del ciclo di vita di Microsoft Internet Explorer 11, il motore di rendering HTML per Adobe Services (pagina di accesso) nella console client utilizza ora Edge Chromium. Microsoft Internet Explorer 11 è ancora il motore di rendering HTML per le dashboard nella console client.  Inoltre, ora ogni installazione della console client (dalla versione della build Campaign Classic 7.3) richiede l’installazione di Microsoft Edge WebView2 Runtime. [Ulteriori informazioni](../../installation/using/installing-the-client-console.md)
* La gestione delle connessioni al database in Adobe Campaign è stata migliorata per ottimizzarne la stabilità.
* L’autenticazione di Microsoft Exchange Online OAuth 2.0 per POP3 è ora supportata in Campaign. [Maggiori informazioni](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Sono stati risolti diversi problemi relativi all’utilizzo di un’attività del flusso di lavoro di arricchimento con dati esterni. (NEO-38069)
* Il connettore FDA SAP Hana è stato aggiornato per funzionare con la versione più recente del database SAP Hana (2.x).
* Il connettore FDA Teradata è stato aggiornato per funzionare con la versione più recente di Teradata (17).
* Nella versione 20.2, il supporto dell’autenticazione basata sui token per le consegne iOS è stato introdotto per le nuove consegne e i nuovi modelli di consegna. Nella versione 7.2, era stata aggiunta una patch al post-aggiornamento per applicare il supporto dell’autenticazione basata su token a un massimo di 10.000 consegne e modelli di consegna creati in precedenza. Nella versione 7.3, la patch è stata migliorata e il limite è stato rimosso.

**Patch**

* È stato corretto un errore della build precedente che impediva agli utenti di ridimensionare la pagina di accesso IMS. (NEO-30085)
* È stato corretto un errore che si verificava durante l’installazione del pacchetto content manager su un’istanza esistente. (NEO-32349)
* È stato risolto un problema nel menu di **Campaigns** a causa del quale veniva visualizzato continuamente un messaggio di “operazione in corso”. (NEO-44904)
* Con Adobe Analytics abilitato, è stato risolto un problema a causa del quale BID (Broadlog ID) e CID (Campaign ID) venivano rimossi dall’URL se si inviava un’e-mail con un URL senza salvare la consegna. (NEO-38678)
* È stato risolto un problema che si verificava durante il caricamento di un’immagine nella cartella delle risorse pubbliche in un’istanza con configurazione specifica del Centro messaggi. Viene visualizzato un messaggio di errore di tipo: “Impossibile caricare le immagini sui server di tracciamento”. (NEO-38546, NEO-45572)
* È stato risolto un problema che causava l’arresto anomalo del sistema durante la rigenerazione della configurazione in caso di file di configurazione non validi. (NEO-38752)
* È stato risolto un problema che poteva causare un aggiornamento errato degli indicatori di consegna. (NEO-44827)
* È stato risolto un problema che poteva causare un errore post-aggiornamento durante l’utilizzo di query complesse. (NEO-43648)
* È stato risolto un problema che poteva impedire il funzionamento dell’anteprima di webApps. (NEO-43242)
* È stato risolto un problema che poteva causare un errore nella preparazione della consegna se si utilizzava un file di mappatura target esterno in un flusso di lavoro con un’attività di caricamento dati (file). (NEO-43691)
* È stato risolto un problema che poteva causare arresti anomali e richiedeva il riavvio completo dell’istanza. (NEO-44645)
* È stato risolto un problema che poteva impedire il caricamento di qualsiasi risultato di Workflow Heatmap. (NEO-43360)
* È stato risolto un problema che poteva causare problemi di connessione se si utilizzava il connettore esterno FDA. (NEO-42722)
* È stato risolto un problema relativo alle bozze che si verificava con l’utilizzo della sostituzione degli indirizzi e dell’esclusione dei gruppi di controllo. (NEO-39695)
* È stato risolto un problema che poteva provocare errori del flusso di lavoro a causa di un problema del connettore Snowflake. (NEO-46299)
* È stato risolto un problema che poteva bloccare la console del client a causa di un carattere non valido in un blocco di personalizzazione. (NEO-45761)
* È stato risolto un problema che poteva causare problemi di connessione durante la creazione di un account esterno per Snowflake come database esterno. (NEO-45744)
* È stato risolto un problema a causa del quale le informazioni delle tabelle potevano risultare protette da un attributo visibleIf. (NEO-37865)
* È stato risolto un problema a causa del quale poteva comparire il messaggio di errore “$ non è definito” durante la fase di analisi della consegna. (NEO-32940)
* È stato risolto un problema che causava l’associazione delle consegne a un eventType errato. (NEO-45743)
* È stato risolto un problema che poteva provocare arresti anomali a causa di core dump intermittenti. (NEO-30549)
* È stato risolto un problema che poteva causare arresti anomali durante l’utilizzo di codice HTML errato in una consegna. (NEO-40385)
* È stato risolto un problema che poteva impedire agli utenti non amministratori di accedere alla scheda **Analysis** (Analisi) nelle proprietà di consegna. (NEO-34025)
* È stato risolto un problema che poteva impedire il caricamento di un’immagine in modalità blocco da un server esterno durante la preparazione dei messaggi. (NEO-40307)
* È stato risolto un problema che poteva causare l’invio della consegna a un numero di destinatari maggiore del previsto. (NEO-45108)

## Versione 7.2.2 - Build 9349 {#release-7-2-2}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_1 marzo 2022_

>[!NOTE]
>
> Questa build è compatibile con la console client v7.2.1.

**Patch**

* È stato risolto un problema a causa del quale, durante la configurazione dell’account esterno **Web Analytics**, lo stato di integrazione era sempre “Integrazione riuscita”, anche in caso di errori. (NEO-36672)
* Sono stati corretti diversi errori post-aggiornamento relativi al meccanismo degli ID di sequenza in caso di ID negativi. (NEO-43205, NEO-42846, NEO-42845)
* È stato risolto un problema che si verificava con l’utilizzo dell’account esterno **Web Analytics** con consegne ricorrenti e continue, che causava la perdita parziale di dati dall’account esterno. (NEO-38548)
* È stato risolto un problema che rallentava la fase di post-aggiornamento della tabella NmsActiveContact. (NEO-43206)
* È stato risolto un problema di errore post-aggiornamento che si verificava se le cartelle predefinite erano state spostate dal nodo **Amministrazione** a qualsiasi altra posizione. (NEO-42875)
* È stato risolto un problema che si verificava con l’utilizzo di un’attività del flusso di lavoro **Update data** (Aggiorna dati) che poteva impedire l’aggiornamento dello schema del destinatario con i dati del destinatario da un database esterno di Google Cloud. (NEO-42343)
* È stato risolto un problema relativo al connettore Adobe Analytics durante la fase di post-aggiornamento. (NEO-43318, NEO-38136)
* È stato risolto un problema CUID sovrascritto da “VALUE_TO_CHANGE” durante la fase di post-aggiornamento. (NEO-43267)
* È stato risolto un problema che causava errori durante la sincronizzazione delle istanze di mid-sourcing e marketing su una configurazione multi-mid. (NEO-10432)
* È stato risolto un problema che causava un errore durante l’aggiornamento del flusso di lavoro di recapito messaggi in caso di più di 1000 registri broadlog contemporaneamente. (NEO-40276)
* È stato risolto un problema che impediva l&#39;aggiornamento automatico degli indicatori di consegna dei rapporti di apertura e di clic. (NEO-43253)

## Versione 7.2.1 - Build 9346 {#release-7-2-1}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_10 gennaio 2022_

**Miglioramento della sicurezza**

Agli account FDA sono stati apportati diversi miglioramenti di sicurezza:

* Quando configuri l’account esterno FDA, ora puoi accedere al tuo account Snowflake utilizzando l’autenticazione con coppia di chiavi per una maggiore sicurezza. [Maggiori informazioni](../../installation/using/configure-fda-snowflake.md)
* Quando configuri l’account esterno FDA, ora puoi accedere all’account Azure Synapse Analytics utilizzando l’identità gestita assegnata dal sistema. [Maggiori informazioni](../../installation/using/configure-fda-synapse.md#azure-external)
* Tutti i riferimenti alla libreria log4j sono stati rimossi da Campaign per garantire la sicurezza ottimale.

**Aggiornamenti della compatibilità**

Adobe Campaign è ora compatibile con Windows Server 2019. Consulta la [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Miglioramenti**

* Connettore Microsoft Dynamics CRM 365

  Sono state applicate correzioni critiche relative all’API web di Microsoft Dynamics Connector:

   * È stato risolto un problema, durante un’importazione attivata da un flusso di lavoro, che causava il salvataggio dei valori nulli dei campi di tipo stringa come Null invece di valori vuoti.
   * È stato risolto un problema che causava il seguente errore per l’importazione o l’esportazione di dati tramite chiamate API web: “URI non valido: lo schema URI è troppo lungo”.
   * Sono stati risolti diversi problemi di importazione di dati contenenti campi di ricerca da Microsoft Dynamics 365.

* Connettore FDA BigQuery Google

   * Il connettore FDA Google BigQuery è ora disponibile per le distribuzioni in hosting. [Maggiori informazioni](../../installation/using/configure-fda-google-big-query.md)
   * È stato aggiunto il supporto per abilitare le connessioni a un server proxy per il connettore FDA BigQuery Google. Le opzioni proxy necessarie possono essere impostate tramite il campo Opzioni nella configurazione dell’account esterno. [Leggi tutto](../../installation/using/configure-fda-google-big-query.md#google-external)

**Altre modifiche**

* Dopo essere state dichiarate obsolete, le attività di azione Microsoft CRM, Salesforce, Oracle CRM On Demand sono state rimosse dall’interfaccia. Per configurare la sincronizzazione dati tra Adobe Campaign e un sistema CRM, puoi utilizzare l’attività del connettore CRM. [Maggiori informazioni](../../workflow/using/crm-connector.md)
* Il campo **[!UICONTROL Encrypted identifier]** è stato aggiunto allo schema visitatore (nms:visitor). Questo è un campo calcolato e deve essere utilizzato per le applicazioni web. Questo si applica quando il canale Line è configurato sull’istanza di mid-sourcing.
* È ora possibile utilizzare le origini dati del CRM con l’attività **Modifica l’origine dati**.
* È stata aggiunta una nuova opzione nella proprietà **Gestione degli errori** delle attività del flusso di lavoro: l’opzione **Interrompi in caso di errore** arresta automaticamente il flusso di lavoro. Non potrai riavviarlo successivamente (NEO-29661). [Maggiori informazioni](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Ora viene utilizzata una sequenza dedicata per generare le chiavi primarie per la tabella nmsGroup, che viene utilizzata per creare gruppi statistici di destinatari. In precedenza, veniva utilizzata la sequenza xtknewId. (NEO-30832)
* È stato aggiunto il supporto per le operazioni di aggiornamento batch tramite l’attività del connettore CRM.
* Sono state migliorate le prestazioni per i tempi di elaborazione della messaggistica transazionale. (NEO-40370)

**Patch**

* È stato risolto un problema che si verificava durante la creazione di una consegna e che causava un errore nella scheda **Immagini** della finestra **Tracciamento e immagini**. Ciò si verificava quando si utilizzava una configurazione proxy automatica. (NEO-33260)
* È stato risolto un problema che poteva impedire il caricamento di un file su un server Debian 10 (HTTPS) in modalità sincrona.
* È stato risolto un problema che poteva impedire l’eliminazione dei record della tabella delle statistiche sulle consegne (`nmsDeliveryLogStats`) dall’istanza di mid-sourcing durante la pulizia del database dopo l’eliminazione delle consegne correlate. (NEO-31034)
* È stato risolto un problema che impediva l’invio di notifiche di app mobili su iOS durante l’utilizzo dell’autenticazione basata su token (NEO-38640).
* È stato risolto un problema che poteva causare la visualizzazione di messaggi di errore script durante il tentativo di creazione e configurazione di rapporti (NEO-38393).
* È stato risolto un problema che poteva causare un errore del flusso di lavoro di tracciamento in Oracle a causa di elevati volumi di indicatori di consegna aggiornati simultaneamente (NEO-39653).
* È stato risolto un problema che poteva impedire l’invio di una consegna a causa di un errore che si verificava durante l’esecuzione di una tipologia di controllo (NEO-39833).
* È stato risolto un problema nelle pagine di destinazione che poteva impedire la corretta visualizzazione dei caratteri speciali nelle pagine HTML delle risposte ai sondaggi online (NEO-39438).
* È stato risolto un problema che poteva impedire il funzionamento della console Campaign Classic facendo clic con il pulsante destro del mouse su una delle cartelle nella scheda Explorer risorse (NEO-38884).
* È stato corretto un errore che si verificava utilizzando un modello di consegna creato in precedenza collegato a un account Web Analytics in una nuova consegna in cui la configurazione di Web Analytics era mancante. (NEO-28666)
* È stato risolto un problema che poteva impedire la visualizzazione in anteprima delle consegne mobili collegate a un flusso di lavoro.
* È stato corretto un errore che impediva il reindirizzamento degli URL di tracciamento personalizzati quando era abilitato il meccanismo di firma URL per i collegamenti di tracciamento.
* È stato risolto un problema che poteva causare errori di post aggiornamento a causa di un problema di gestione dell’indice.
* È stato corretto un errore che si verificava durante l’utilizzo dei tipi di dati dei campi di ricerca con Microsoft Dynamics CRM nelle attività del flusso di lavoro **Importa** o **Esporta**.
* È stato risolto un problema che poteva impedire agli utenti di accedere alla console a causa di un problema di configurazione proxy. (NEO-38388)
* È stato risolto un problema di regressione che impediva il funzionamento corretto della funzionalità **Purge folder** (Svuota cartella). (NEO-37459)
* È stato risolto un problema che causava un errore di richiesta non valida quando si utilizzavano campi di dati xml con l’account Microsoft Dynamics CRM se il codice xml di riferimento conteneva virgolette doppie.
* È stato risolto un problema che causava la registrazione errata dei problemi di timeout della rete: invece di essere registrati come errori di rete, venivano registrati come problemi di interruzione dello script. Questo problema si verificava nel caso di richieste HTTP incluse nelle attività JavaScript. (NEO-38079)
* È stato risolto un problema a causa del quale venivano restituiti risultati errati nell’esecuzione delle funzioni Amazon Redshift HoursDiff e MinutesDiff durante il tentativo di estrarre il componente “time”.(NEO-31673)
* È stato risolto un problema che impediva il caricamento del rapporto **Hot click** per le consegne a partire dalla build 9182. (NEO-28900)
* È stato corretto un errore che sostituiva il simbolo &amp; in un URL con il riferimento all’entità carattere (`&amp;`) impedendo agli utenti di accedere all’URL collegato a un codice QR. (NEO-28621)
* È stato risolto un problema che creava un nuovo account esterno ogni volta che un utente creava un nuovo flusso di lavoro di Campaign e un’attività di consegna collegata a un account Web Analytics. La causa era un ID mancante nell’oggetto di consegna webAnalyticsAccount. (NEO-39691)
* È stato risolto un problema che poteva impedire il funzionamento dell’attività del flusso di lavoro **Read list** (Leggi elenco) se l’elenco era stato identificato nel database con un ID negativo. (NEO-39607)
* È stato risolto un problema che poteva causare il mancato funzionamento del flusso di lavoro **Mid-sourcing (registri di consegna)**. (NEO-39662)
* È stato risolto un problema che poteva impedire la visualizzazione in anteprima delle consegne e-mail collegate a un flusso di lavoro. (NEO-37840)
* È stato risolto un problema che poteva causare l’eliminazione di tabelle valide contenenti valori di elenco da parte del flusso di lavoro di pulizia del database. (NEO-34911)
* È stato risolto un problema che poteva causare l’arresto anomalo del flusso di lavoro di fatturazione sulle istanze di marketing.
