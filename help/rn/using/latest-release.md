---
title: Ultima versione
description: Ultima versione
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
source-git-commit: eab67029d477044bc853f2a5c2de06ace70ebbee

---


# Ultima versione{#latest-release}

[Genera aggiornamento](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | Rilasci [del Pannello di](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) controllo| Aggiornamenti [alla](../../rn/using/documentation-updates.md) documentazione| [Versioni](../../rn/using/release--19-2.md) precedenti| Funzioni [obsolete](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Disponibilità generale</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Non più disponibile</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Ultima build stabile disponibile. Build convalidata in produzione.<br> </td>
   <td>Build convalidata da Adobe. In attesa di prove di produzione.<br> </td>
   <td>Nuova build disponibile con correzioni di bug. L'aggiornamento è obbligatorio.<br> </td>
   <td>Contiene regressioni note. L'aggiornamento è obbligatorio.<br> </td>
  </tr> 
 </tbody> 
</table>

L&#39; **ultima build** stabile è 9032 (3a9dc9c). Fai clic [qui](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) Release 20.1.2 - Build 9123 {#release-20-1-2-build-9123}

_13 marzo 2020_

* È stato risolto un problema che impediva la distribuzione della versione sui server Red Hat 7. (NEO-23332)

## ![](assets/do-not-localize/orange_2.png) Release 20.1 - Build 9122 {#release-20-1-build-9122}

_17 febbraio 2020_

**Novità?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connettore FDA per fiocco di neve</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake è un data warehouse cloud completamente gestito, progettato per essere scalato sia a livello di storage che di calcolo. Con questo nuovo connettore, Adobe Campaign ora può sfruttare la potenza di Snowflake per eseguire la segmentazione dei Big Data. Questo connettore è disponibile per tutti i clienti, incluso ospitato da Adobe.</p>
    <p>Per ulteriori informazioni, consultate la documentazione <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake"></a> dettagliata e il video <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html"></a>tutorial.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Miglioramenti del connettore Hadoop FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Il connettore FDA Hadoop è stato migliorato per supportare Hadoop 3.0 e Cloudera.</p>
    <p>Per ulteriori informazioni, consulta la documentazione <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3"></a>dettagliata.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Miglioramento della protezione nella configurazione del report per proteggere dal clickjacking. Questo vale per i nuovi rapporti. Per i vecchi rapporti, è necessario ripubblicarli per applicare le modifiche. (NEO-13282)

* Risolvere un piccolo problema di memoria in cryptString. (NEO-20071)

* È stato migliorato il JSP del monitor per correggere una divulgazione IP interna. (NEO-16821)

* È stato risolto un problema per il quale le informazioni di traccia dello stack potevano essere visualizzate agli utenti non amministratori. (NEO-12388)

* È stata migliorata la gestione dei dati memorizzati nella cache delle sessioni precedenti. (NEO-17039)

* È stato risolto un problema che impediva al file logins.log di registrare i tentativi di accesso riusciti tramite IMS. (NEO-11004)

**Miglioramenti**

* iOS 13 è ora supportato con il connettore HTTP2.

* Miglioramento della gestione della quarantena e della pulizia delle tabelle utilizzate dalla funzione di notifica push (nms:address e nms:appSubscriptionRcp). Per iOS (solo connettore HTTP2), i token disattivati ora vengono gestiti come per Android. Il flag disable ora è impostato nella tabella NmsAppSubscriptionRcp. [Leggi tutto](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* È stata aggiunta una nuova opzione nel codice **** JavaScript e nelle attività del flusso di lavoro del codice **JavaScript** avanzato per definire un periodo di timeout. Questo impedisce l&#39;esecuzione troppo lunga della fase di esecuzione javascript. Se il periodo di timeout intercorre, il flusso di lavoro viene interrotto. Il timeout predefinito è 1 ora. [Leggi tutto](../../workflow/using/sql-code-and-javascript-code.md)

* L&#39;analisi di consegna ora viene arrestata quando non viene trovata alcuna affinità corrispondente nel server di mid-sourcing e viene visualizzato il messaggio di errore corrispondente.

* È ora supportato il failover del database per Postgres: quando il server del database si arresta in modo anomalo e si riavvia, Campaign ora si riconnette automaticamente ad esso.

* La vista **Avvia in sospeso** è stata aggiunta al nodo Amministrazione > Audit > Stato flussi di lavoro. Questo consente di monitorare tutti i flussi di lavoro sull&#39;istanza in attesa di essere avviati dal processo **operationMgt** . Questa visualizzazione viene fornita con il pacchetto Campagne di marketing. [Leggi tutto](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Altre modifiche**

* In Linux, l&#39;avvio del servizio di nlserver ora utilizza un&#39;unità di sistema invece dello script /etc/init.d/nlserver6. La migrazione al nuovo schema di avvio viene eseguita automaticamente quando installate il pacchetto 20.1. /etc/init.d/nlserver6 è ancora disponibile, ma per interagire con il servizio nlserver (avvio, riavvio, arresto, ecc.), si consiglia di utilizzare direttamente il comando systemctl.

* Le tabelle personalizzate più utilizzate sono state spostate dalla sequenza **xtkNewId** alle sequenze dedicate. [Leggi tutto](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Sono state migliorate le prestazioni delle query che potrebbero essere influenzate da connessioni di database non necessarie.

* Sono state migliorate le prestazioni della procedura guidata di aggiornamento del database.

* La gestione dei record del database è stata migliorata.

* La robustezza del pool di connessioni è stata migliorata, il che potrebbe impedire che si verificassero errori di connessione imprevisti troppo spesso.

* Sono state migliorate le regole di convalida dell&#39;indirizzo e-mail per inviare un indirizzo alla quarantena in caso di errore soft. [Leggi tutto](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Per Debian, Campaign utilizza ora le librerie PCRE di sistema quando sono disponibili.

* Campaign ora consente l&#39;utilizzo di una libreria ODBC di sistema più recente.

* È stato aggiunto un timeout al servlet LINE quando si apre una connessione per caricare un&#39;immagine RTF. Se il caricamento dell’immagine richiede troppo tempo, il servlet interrompe la connessione per evitare un collo di bottiglia.

**Patch**

* È stato risolto un problema di crittografia della chiave dell&#39;account quando si utilizzava il connettore Hadoop.

* È stato risolto un problema di regressione a causa dell&#39;implementazione della certificazione SSL che causava un errore di connessione utente sul server Windows. (NEO-20629)

* È stato risolto un problema relativo all&#39;attività di query incrementale in caso di ID di flusso di lavoro negativi. (NEO-19779)

* È stato risolto un problema di codifica durante l&#39;esecuzione di query tramite il connettore Netezza FDA. (NEO-19594)

* È stato risolto un problema che causava un errore durante l&#39;utilizzo del metodo POST nell&#39;attività dell&#39;evento del flusso di lavoro Download **** Web.

* È stato risolto un problema relativo alla generazione della proposta di offerta. (NEO-18176)

* È stato risolto un problema di visualizzazione dei piè di pagina durante l&#39;utilizzo del modello di modulo Web di acquisizione.

* È stato risolto un problema che causava l&#39;arresto anomalo dell&#39;analisi degli URL nel contenuto di consegne continue. (NEO-16910)

* È stato risolto un problema che impediva il calcolo dei campi **Inizio** e **Fine** durante la creazione di una nuova campagna.

* È stato risolto un problema relativo all&#39;attività del flusso di lavoro **File Download** quando si utilizzava un URL.

* È stato risolto un problema che si verificava durante l&#39;anteprima di un elenco importato in un&#39;attività di query di un report. (NEO-13119)

* È stato risolto un problema che causava la visualizzazione di un&#39;immagine non aggiornata quando si selezionava il blocco **Power by Campaign** Personalization (Personalizzazione in funzione) nell&#39;editor e-mail.

* È stata migliorata la comunicazione di rete tra il client e il server.

* È stato risolto un problema che si verificava quando troppi flussi di lavoro venivano creati nella stessa campagna. Ora non è possibile creare più di 28 flussi di lavoro. Viene visualizzato un avviso.

* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;opzione **Una selezione di colonne** riconciliazione in un&#39;attività del flusso di lavoro **Unione** .

* È stato corretto un problema di arresto anomalo della console che si verificava quando si utilizzava un elenco di arricchimenti danneggiato in un flusso di lavoro. (NEO-18096)

* Sono stati risolti diversi problemi di arresto anomalo della console che potevano verificarsi nei flussi di lavoro (NEO-18010, NEO-18032)

* È stato risolto un problema che consentiva l&#39;esecuzione di un&#39;attività del flusso di lavoro del segnale **** esterno anche quando era disabilitata. (NEO-17524)

* È stato risolto un problema durante la creazione di un nuovo schema.

* È stato risolto un problema di tracciamento durante l&#39;invio di messaggi SMS. (NEO-19595)

* È stato risolto un problema che causava la visualizzazione di un numero di audience con targeting non corretto negli indicatori di distribuzione.

* È stato risolto un problema che causava la visualizzazione di percentuali errate durante la generazione di un rapporto descrittivo tramite un&#39;attività del flusso di lavoro. (NEO-14314)

* È stato risolto un problema che causava la visualizzazione di numeri diversi da parte del report sulla velocità di consegna quando veniva visualizzato il parametro della visualizzazione ora. (NEO-11783)

* È stato risolto un problema che impediva l&#39;aggiornamento degli indicatori di tracciamento dei messaggi transazionali dal flusso di lavoro Tracciamento. (NEO-17770)

* È stato risolto un problema di regressione che causava l&#39;arresto anomalo del processo Web e il riavvio durante la richiesta di un&#39;offerta tramite SOAP. (NEO-19482)

* È stato risolto un problema che impediva il caricamento di dati in risorse pubbliche se la directory di caricamento era una posizione condivisa remota. (NEO-19361)

* È stato risolto un problema che causava il costante errore del flusso di lavoro **Importa pubblico dal flusso di lavoro tecnico di Adobe Experience Cloud** . (NEO-18463)

* È stato risolto un problema che impediva l&#39;invio di consegne quando si utilizzavano i modelli importati da Experience Manager. (NEO-17540)

* È stato risolto un problema che si verificava dopo l&#39;aggiornamento alla build 9032 e che impediva all&#39;istanza di connettersi al server FTP tramite il protocollo SSL. (NEO-20498)

* È stato risolto un problema che si verificava durante l&#39;eliminazione, l&#39;inserimento o l&#39;aggiornamento di una grande quantità di dati con l&#39;attività **Aggiorna dati** in un flusso di lavoro utilizzando uno schema FDA come dimensione di targeting. (NEO-13280)

* È stato risolto un problema che impediva l&#39;invio di e-mail quando si utilizzava l&#39;istruzione &#39;if&#39; all&#39;esterno del `body` tag.

* È stato risolto un problema che si verificava durante il tentativo di visualizzare la pagina mirror dai log di consegna di un messaggio inviato. (NEO-17976)

* È stato risolto un problema che impediva la visualizzazione del blocco **Collegamento a pagina** speculare nella scheda Contenuto **** testo dopo aver fatto clic su **Importa HTML** in una consegna. (NEO-17568)

* Il messaggio di errore visualizzato quando si fa clic su un collegamento a una pagina mirror scaduta è stato chiarito. (NEO-17340)

* È stato risolto un problema che impediva l&#39;utilizzo di alcuni pulsanti nella schermata di creazione della distribuzione **dei** dati.

* È stato risolto un problema che si verificava durante la pianificazione di un&#39;attività di consegna in un&#39;istanza con Asia/Calcutta come fuso orario. (NEO-2001)

* Ora viene visualizzato un errore quando un recapito presenta un problema di configurazione dell&#39;affinità.

* È stato risolto un problema che causava la visualizzazione di un numero di tag versione non corretto nel menu **Informazioni** .

* È stato risolto un problema che si verificava durante il tentativo di aggiornare il conto di routing dalle proprietà di una consegna ricorrente in un flusso di lavoro. (NEO-18684)

* È stato risolto un problema che si verificava durante la connessione all&#39;istanza tramite il modulo di reindirizzamento, che impediva la corretta pulizia della connessione una volta chiusa.
