---
solution: Campaign Classic
product: campaign
title: Versione 20.1
description: Versione 20.1
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
translation-type: tm+mt
source-git-commit: 91313fdc7aed6597d8d54d65b747c835e0cd9ccb
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 10%

---


# Versione 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) Versione 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_23 dicembre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), l’aggiornamento è obbligatorio per il server Campaign e la console client per poter connettersi a Campaign dopo il **30 giugno 2021**.
   >
   > 
* Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.


* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Versione 20.1.3 - Build 9124{#release-20-1-3-build-9124}

_6 maggio 2020_

* È stato risolto un problema dell’attività **File Transfer** che impediva il funzionamento dell’autenticazione basata su chiave SFTP su Debian 9. (NEO-23183)

## ![](assets/do-not-localize/red_2.png) Versione 20.1.2 - Build 9123{#release-20-1-2-build-9123}

_13 marzo 2020_

* È stato risolto un problema che impediva la distribuzione della versione sui server Red Hat 7. (NEO-23332)

## ![](assets/do-not-localize/red_2.png) Versione 20.1 - Build 9122{#release-20-1-build-9122}

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
    <p>Per ulteriori informazioni, consulta la <a href="../../installation/using/configure-fda-snowflake.md">documentazione dettagliata</a> e <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">video tutorial</a>.</p>
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

**Miglioramenti della sicurezza**

* Maggiore sicurezza nella configurazione dei report per proteggere dal click-jacking. Questo vale per i nuovi rapporti. Per applicare le modifiche ai vecchi rapporti, è necessario ripubblicarli. (NEO-13282)

* Risolvere un piccolo problema di memoria in cryptString. (NEO-20071)

* È stato migliorato il monitoraggio JSP per correggere una divulgazione IP interna. (NEO-16821)

* È stato risolto un problema a causa del quale le informazioni sulla traccia dello stack potevano essere visualizzate agli utenti non amministratori. (NEO-12388)

* È stata migliorata la gestione dei dati memorizzati nella cache delle sessioni precedenti. (NEO-17039)

* È stato risolto un problema che impediva al file logins.log di registrare i tentativi di accesso riusciti tramite IMS. (NEO-11004)

**Miglioramenti**

* iOS 13 è ora supportato con il connettore HTTP2.

* È stata migliorata la gestione della quarantena e la pulizia delle tabelle utilizzate dalla funzione di notifica push (nms:address e nms:appSubscriptionRcp). Per iOS (solo connettore HTTP2), i token disattivati vengono ora gestiti come per Android. Il flag disable ora è impostato nella tabella NmsAppSubscriptionRcp. [Leggi tutto](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* È stata aggiunta una nuova opzione nelle attività del flusso di lavoro **Codice JavaScript** e **Codice JavaScript avanzato** per definire un periodo di timeout. Questo impedisce l’esecuzione della fase di esecuzione di javascript per troppo tempo. Se trascorre il periodo di timeout, il flusso di lavoro viene interrotto. Il timeout predefinito è di 1 ora. [Leggi tutto](../../workflow/using/sql-code-and-javascript-code.md)

* L’analisi della consegna viene ora interrotta quando non viene trovata alcuna affinità corrispondente sul server di mid-sourcing e viene visualizzato il messaggio di errore corrispondente.

* È ora supportato il failover del database per Postgres: quando il server di database si blocca e si riavvia, Campaign ora si riconnette automaticamente a esso.

* La vista **Avvia in sospeso** è stata aggiunta al nodo Amministrazione > Audit > Stato flussi di lavoro . Questo ti consente di monitorare tutti i flussi di lavoro sull&#39;istanza che sono in attesa di essere avviati dal processo **operationMgt**. Questa visualizzazione viene fornita con il pacchetto Campagne di marketing . [Leggi tutto](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Altre modifiche**

* Su Linux, l&#39;avvio del servizio nlserver ora utilizza un&#39;unità di sistema invece dello script /etc/init.d/nlserver6. La migrazione al nuovo schema di avvio viene eseguita automaticamente quando installi il pacchetto 20.1. /etc/init.d/nlserver6 è ancora disponibile ma per interagire con il servizio nlserver (avvio, riavvio, arresto, ecc.), si consiglia di utilizzare direttamente il comando systemctl.

* Le tabelle personalizzate più utilizzate sono state spostate dalla sequenza **xtkNewId** alle sequenze dedicate. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Prestazioni query migliorate che potrebbero essere influenzate da connessioni di database non necessarie.

* Sono state migliorate le prestazioni della procedura guidata di aggiornamento del database per ridurre il numero di istruzioni SQL al fine di ottimizzare il tempo di risposta.

* La gestione dei record del database è stata migliorata.

* La robustezza del pool di connessioni è stata migliorata, il che potrebbe impedire che si verifichino errori di connessione imprevisti troppo spesso.

* Le regole di convalida dell’indirizzo e-mail per inviare un indirizzo in quarantena in caso di errore soft sono state migliorate. [Leggi tutto](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Per Debian, Campaign ora utilizza le librerie PCRE di sistema quando sono disponibili.

* Campaign ora consente l’utilizzo di una libreria ODBC di sistema più recente.

* È stato aggiunto un timeout al servlet LINE quando si apre una connessione per caricare un’immagine ricca. Se il caricamento dell’immagine richiede troppo tempo, il servlet interrompe la connessione per evitare un collo di bottiglia.

**Patch**

* È stato risolto un problema di crittografia della chiave dell’account quando si utilizzava il connettore del Hadoop.

* È stato risolto un problema di regressione a causa dell’implementazione della certificazione SSL che causava un errore della connessione utente sul server Windows. (NEO-20629)

* È stato risolto un problema relativo all’attività di query incrementale in caso di ID flusso di lavoro negativi. (NEO-19779)

* È stato risolto un problema di codifica durante l’esecuzione di query tramite il connettore FDA Netezza. (NEO-19594)

* È stato risolto un problema che causava un errore durante l&#39;utilizzo del metodo POST nell&#39;attività dell&#39;evento del flusso di lavoro **Download Web** .

* È stato risolto un problema relativo alla generazione di proposte di offerta. (NEO-18176)

* È stato risolto un problema di visualizzazione del piè di pagina durante l’utilizzo del modello di modulo web di acquisizione.

* È stato risolto un problema che poteva causare l’arresto anomalo degli URL durante l’analisi del contenuto delle consegne continue. (NEO-16910)

* È stato risolto un problema che impediva il calcolo dei campi **Start** e **End** durante la creazione di una nuova campagna.

* È stato risolto un problema relativo all&#39;attività del flusso di lavoro **File Download** quando si utilizza un URL.

* È stato risolto un problema che si verificava durante l’anteprima di un elenco importato in un’attività query di un rapporto. (NEO-13119)

* È stato risolto un problema che causava la visualizzazione di un&#39;immagine obsoleta durante la selezione del blocco di personalizzazione **Powered by Campaign** nell&#39;editor e-mail.

* È stata migliorata la comunicazione di rete tra il client e il server.

* È stato risolto un problema che si verificava quando nella stessa campagna venivano creati troppi flussi di lavoro. Ora non puoi creare più di 28 flussi di lavoro. Viene visualizzato un avviso.

* È stato risolto un problema che si verificava durante l’utilizzo dell’opzione di riconciliazione **A selection of columns** in a2/>Union **in un’attività del flusso di lavoro.**

* È stato risolto un problema di arresto anomalo della console che poteva verificarsi quando si utilizzava un elenco di arricchimento danneggiato in un flusso di lavoro. (NEO-18096)

* Sono stati risolti diversi problemi di arresto anomalo della console che potevano verificarsi nei flussi di lavoro (NEO-18010, NEO-18032)

* È stato risolto un problema che consentiva l&#39;esecuzione di un&#39;attività flusso di lavoro **External signal** anche quando è stata disabilitata. (NEO-17524)

* È stato risolto un problema che si verificava durante la creazione di un nuovo schema.

* È stato risolto un problema di tracking durante l’invio di messaggi SMS. (NEO-19595)

* È stato risolto un problema che mostrava un numero di pubblico di destinazione errato negli indicatori di consegna.

* È stato risolto un problema che visualizzava percentuali errate durante la generazione di un rapporto descrittivo tramite un’attività del flusso di lavoro. (NEO-14314)

* È stato risolto un problema che causava la visualizzazione di numeri diversi nel report della velocità effettiva di consegna quando il parametro di visualizzazione dell&#39;ora. (NEO-11783)

* È stato risolto un problema che impediva agli indicatori di tracciamento dei messaggi transazionali di essere aggiornati dal flusso di lavoro Tracking. (NEO-17770)

* È stato risolto un problema di regressione che causava l’arresto anomalo del processo Web e il riavvio durante la richiesta di un’offerta tramite SOAP. (NEO-19482)

* È stato risolto un problema che impediva il caricamento di dati in risorse pubbliche se la directory di caricamento era una posizione condivisa remota. (NEO-19361)

* È stato risolto un problema che causava un costante errore del **Import audiences from the Adobe Experience Cloud** technical workflow tp. (NEO-18463)

* È stato risolto un problema che impediva l’invio di consegne durante l’utilizzo di modelli importati da Experience Manager. (NEO-17540)

* È stato risolto un problema che si verificava dopo l’aggiornamento alla build 9032 e che impediva la connessione dell’istanza al server FTP tramite il protocollo SSL. (NEO-20498)

* È stato risolto un problema che si verificava durante l’eliminazione, l’inserimento o l’aggiornamento di una grande quantità di dati con l’attività **Update data** in un flusso di lavoro utilizzando uno schema FDA come dimensione di targeting. (NEO-13280)

* È stato risolto un problema che impediva l’invio di e-mail in caso di codice JavaScript all’esterno del tag di contenuto HTML. (NEO-18628)

* È stato risolto un problema che si verificava durante il tentativo di visualizzazione della pagina speculare dai registri di consegna di un messaggio inviato. (NEO-17976)

* È stato risolto un problema che impediva la visualizzazione del blocco di personalizzazione **Collega a pagina speculare** nella scheda **Contenuto testo** dopo aver fatto clic su **Importa HTML** in una consegna. (NEO-17568)

* È stato chiarito il messaggio di errore visualizzato quando si fa clic su un collegamento a una pagina speculare scaduta. (NEO-17340)

* È stato risolto un problema che impediva l&#39;utilizzo di alcuni pulsanti nella schermata di creazione **Distribuzione dati** .

* È stato risolto un problema che si verificava durante la pianificazione di un’attività di consegna in un’istanza con Asia/Calcutta come fuso orario. (NEO-20001)

* Ora viene visualizzato un errore quando una consegna presenta un problema di configurazione dell’affinità.

* È stato risolto un problema che causava la visualizzazione di un numero di tag di versione errato nel menu **Informazioni su** .

* È stato risolto un problema che si verificava durante il tentativo di aggiornare l&#39;account di indirizzamento dalle proprietà di una consegna ricorrente in un flusso di lavoro. (NEO-18684)

* È stato risolto un problema che si verificava durante la connessione all’istanza tramite il modulo di reindirizzamento, che impediva la corretta pulizia della connessione una volta chiusa.
