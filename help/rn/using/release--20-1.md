---
solution: Campaign Classic
product: campaign
title: Versione 20.1
description: Versione 20.1
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
translation-type: tm+mt
source-git-commit: 8d4fd855df2f373c2684fd8dfaf54ffe42e196f1
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 6%

---


# Versione 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) Versione 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_24 dicembre 2020_

>[!CAUTION]
>
>Questa versione include un nuovo protocollo di connessione:  l&#39;aggiornamento è obbligatorio sia per il server Campaign che per la console client per poter connettersi a Campaign dopo il 21 marzo 2020

* Il protocollo di connessione è stato aggiornato per seguire il nuovo meccanismo di autenticazione IMS.
* È stato risolto un problema di sicurezza per rafforzare la protezione contro i problemi SSRF (Server Side Request Forgery). (NEO-27777)

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
   <td> <p>Il Snowflake è un data warehouse cloud completamente gestito, progettato per essere scalato sia a livello di storage che di calcolo. Con questo nuovo connettore,  Adobe Campaign ora può sfruttare la potenza del Snowflake per eseguire la segmentazione Big Data. Questo connettore è disponibile per tutti i clienti, incluso ospitato da  Adobe.</p>
    <p>Per ulteriori informazioni, consultare la <a href="../../installation/using/configure-fda-snowflake.md">documentazione dettagliata</a> e <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">video di esercitazione</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Miglioramenti del connettore hadoop FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Il connettore Hadoop FDA è stato migliorato per supportare Hadoop 3.0 e Cloudera.</p>
    <p>Per ulteriori informazioni, consulta la <a href="../../installation/using/configure-fda-hadoop.md">documentazione dettagliata</a>.</p>
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

* È stata aggiunta una nuova opzione nelle attività del flusso di lavoro **codice JavaScript** e **codice JavaScript avanzato** per definire un periodo di timeout. Questo impedisce l&#39;esecuzione troppo lunga della fase di esecuzione di javascript. Se il periodo di timeout intercorre, il flusso di lavoro viene interrotto. Il timeout predefinito è 1 ora. [Leggi tutto](../../workflow/using/sql-code-and-javascript-code.md)

* L&#39;analisi di consegna ora viene arrestata quando non viene trovata alcuna affinità corrispondente nel server di mid-sourcing e viene visualizzato il messaggio di errore corrispondente.

* È ora supportato il failover del database per Postgres: quando il server del database si arresta in modo anomalo e si riavvia, Campaign ora si riconnette automaticamente ad esso.

* La vista **Avvia in sospeso** è stata aggiunta al nodo Amministrazione > Audit > Stato flussi di lavoro. Questo consente di monitorare tutti i flussi di lavoro sull&#39;istanza in attesa di essere avviati dal processo **operationMgt**. Questa visualizzazione viene fornita con il pacchetto Campagne di marketing. [Leggi tutto](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Altre modifiche**

* In Linux, l&#39;avvio del servizio di nlserver ora utilizza un&#39;unità di sistema invece dello script /etc/init.d/nlserver6. La migrazione al nuovo schema di avvio viene eseguita automaticamente quando installate il pacchetto 20.1. /etc/init.d/nlserver6 è ancora disponibile, ma per interagire con il servizio nlserver (avvio, riavvio, arresto, ecc.), si consiglia di utilizzare direttamente il comando systemctl.

* Le tabelle personalizzate più dispendiose sono state spostate dalla sequenza **xtkNewId** alle sequenze dedicate. [Leggi tutto](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Sono state migliorate le prestazioni delle query che potrebbero essere influenzate da connessioni di database non necessarie.

* Sono state migliorate le prestazioni della procedura guidata di aggiornamento del database per ridurre il numero di istruzioni SQL al fine di ottimizzare il tempo di risposta.

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

* È stato risolto un problema che causava un errore durante l&#39;utilizzo del metodo POST nell&#39;attività dell&#39;evento del flusso di lavoro **Download Web**.

* È stato risolto un problema relativo alla generazione della proposta di offerta. (NEO-18176)

* È stato risolto un problema di visualizzazione dei piè di pagina durante l&#39;utilizzo del modello di modulo Web di acquisizione.

* È stato risolto un problema che causava l&#39;arresto anomalo dell&#39;analisi degli URL nel contenuto di consegne continue. (NEO-16910)

* È stato risolto un problema che impediva il calcolo dei campi **Start** e **End** durante la creazione di una nuova campagna.

* È stato risolto un problema relativo all&#39;attività del flusso di lavoro **File Download** quando si utilizza un URL.

* È stato risolto un problema che si verificava durante l&#39;anteprima di un elenco importato in un&#39;attività di query di un report. (NEO-13119)

* È stato risolto un problema che causava la visualizzazione di un&#39;immagine obsoleta quando si selezionava il blocco di personalizzazione **Alimentato da Campaign** nell&#39;editor e-mail.

* È stata migliorata la comunicazione di rete tra il client e il server.

* È stato risolto un problema che si verificava quando troppi flussi di lavoro venivano creati nella stessa campagna. Ora non è possibile creare più di 28 flussi di lavoro. Viene visualizzato un avviso.

* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;opzione di riconciliazione **Una selezione di colonne** in un&#39;attività del flusso di lavoro **Union**.

* È stato corretto un problema di arresto anomalo della console che si verificava quando si utilizzava un elenco di arricchimenti danneggiato in un flusso di lavoro. (NEO-18096)

* Sono stati risolti diversi problemi di arresto anomalo della console che potevano verificarsi nei flussi di lavoro (NEO-18010, NEO-18032)

* È stato risolto un problema che consentiva l&#39;esecuzione di un&#39;attività del flusso di lavoro **Segnale esterno** anche quando era disabilitata. (NEO-17524)

* È stato risolto un problema durante la creazione di un nuovo schema.

* È stato risolto un problema di tracciamento durante l&#39;invio di messaggi SMS. (NEO-19595)

* È stato risolto un problema che causava la visualizzazione di un numero di audience con targeting non corretto negli indicatori di distribuzione.

* È stato risolto un problema che causava la visualizzazione di percentuali errate durante la generazione di un rapporto descrittivo tramite un&#39;attività del flusso di lavoro. (NEO-14314)

* È stato risolto un problema che causava la visualizzazione di numeri diversi da parte del report sulla velocità di consegna quando veniva visualizzato il parametro della visualizzazione ora. (NEO-11783)

* È stato risolto un problema che impediva l&#39;aggiornamento degli indicatori di tracciamento dei messaggi transazionali dal flusso di lavoro Tracciamento. (NEO-17770)

* È stato risolto un problema di regressione che causava l&#39;arresto anomalo del processo Web e il riavvio durante la richiesta di un&#39;offerta tramite SOAP. (NEO-19482)

* È stato risolto un problema che impediva il caricamento di dati in risorse pubbliche se la directory di caricamento era una posizione condivisa remota. (NEO-19361)

* È stato risolto un problema che causava il costante errore dell&#39; **Importa pubblico dal flusso di lavoro tecnico Adobe Experience Cloud**. (NEO-18463)

* È stato risolto un problema che impediva l&#39;invio di consegne quando si utilizzavano modelli importati da  Experience Manager. (NEO-17540)

* È stato risolto un problema che si verificava dopo l&#39;aggiornamento alla build 9032 e che impediva all&#39;istanza di connettersi al server FTP tramite il protocollo SSL. (NEO-20498)

* È stato risolto un problema che si verificava durante l&#39;eliminazione, l&#39;inserimento o l&#39;aggiornamento di una grande quantità di dati con l&#39;attività **Aggiorna dati** in un flusso di lavoro utilizzando uno schema FDA come dimensione di targeting. (NEO-13280)

* È stato risolto un problema che impediva l&#39;invio di e-mail in caso di codice JavaScript all&#39;esterno del tag di contenuto HTML. (NEO-18628)

* È stato risolto un problema che si verificava durante il tentativo di visualizzare la pagina mirror dai log di consegna di un messaggio inviato. (NEO-17976)

* È stato risolto un problema che impediva la visualizzazione del blocco di personalizzazione **Collega a pagina mirror** nella scheda **Contenuto testo** dopo aver fatto clic su **Importa HTML** in una consegna. (NEO-17568)

* Il messaggio di errore visualizzato quando si fa clic su un collegamento a una pagina mirror scaduta è stato chiarito. (NEO-17340)

* È stato risolto un problema che impediva l&#39;utilizzo di alcuni pulsanti nella schermata di creazione **Distribuzione dati**.

* È stato risolto un problema che si verificava durante la pianificazione di un&#39;attività di consegna in un&#39;istanza con Asia/Calcutta come fuso orario. (NEO-20001)

* Ora viene visualizzato un errore quando un recapito presenta un problema di configurazione dell&#39;affinità.

* È stato risolto un problema che causava la visualizzazione di un numero di tag versione non corretto nel menu **Informazioni su**.

* È stato risolto un problema che si verificava durante il tentativo di aggiornare il conto di routing dalle proprietà di una consegna ricorrente in un flusso di lavoro. (NEO-18684)

* È stato risolto un problema che si verificava durante la connessione all&#39;istanza tramite il modulo di reindirizzamento, che impediva la corretta pulizia della connessione una volta chiusa.
