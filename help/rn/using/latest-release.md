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
source-git-commit: d9b6ae9f7e2f3b15698f1a420b5416162cbcc758
workflow-type: tm+mt
source-wordcount: '1987'
ht-degree: 1%

---


# Ultima versione{#latest-release}

![](assets/do-not-localize/cp-icon.png) **Nuovo rilascio** di giugno Pannello di controllo Campaign con monitoraggio profili attivi, controllo della recapito del sottodominio e gestione chiavi GPG. [Ulteriori](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html)informazioni.

## ![](assets/do-not-localize/blue_2.png) Release 20.2.1 - Build 9180 {#release-20-2-2-build-9180}

_22 luglio 2020_

* È stato risolto un problema che impediva il monitoraggio quando la funzionalità di firma era disabilitata o quando si utilizzava una vecchia istanza di marketing con un identificatore Mid recente. (NEO-26411)
* È stato risolto un problema che causava il blocco dei collegamenti non firmati da domini personalizzati quando questi dovevano essere consentiti. (NEO-25210)
* È stato risolto un problema che poteva impedire di aprire/fare clic sugli URL di tracciamento quando si utilizzavano alcune versioni precedenti di Outlook. (NEO-25688)
* È stato corretto un problema a causa del quale gli URL delle pagine mirror venivano definiti in modo non corretto nelle comunicazioni e-mail. (NEO-26084)
* È stato risolto un problema con la gestione degli URL di codifica nel servizio di anti-phishing. (NEO-25283)
* È stato risolto un problema che impediva il funzionamento del tracciamento degli URL tramite frammenti nei parametri di personalizzazione (tag di ancoraggio con cancelletto). (NEO-25774)
* È stato risolto un problema di tracciamento quando si utilizzavano formule di tracciamento personalizzate specifiche. (NEO-25277) È stato risolto un problema che impediva il funzionamento del tracciamento dei &quot;clic di notifica&quot; (notifiche push iOS e Android). (NEO-25965)
* È stata corretta una regressione che ha un impatto sui campi calcolati in un flusso di lavoro. (NEO-25194)
* È stata corretta una regressione che impediva il funzionamento della creazione immediata di URL di tracciamento Web. (NEO-20999)
* È stato risolto un problema relativo ai rapporti di consegna forniti con Scene7 che venivano visualizzati troncati quando venivano esportati in PDF. (NEO-25757)
* È stato risolto un problema di arresto anomalo nella procedura guidata di distribuzione.
* È stato risolto un problema che poteva impedire il corretto funzionamento del flusso di lavoro di notifica dell&#39;offerta dopo un post aggiornamento.
* Il connettore iOS HTTP2 è stato migliorato (aggiornamenti di terze parti e gestione degli errori). (NEO-25904, NEO-25903)
* L&#39;elenco jarsToSkip in catalina.properties è stato aggiornato per rimuovere il riferimento a un file jar non più utilizzato (notifiche iOS).
* È stato risolto un problema che impediva la preparazione della consegna dopo l&#39;aggiornamento postaggiornato.
* Dopo il passaggio al [nuovo meccanismo](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)ID sequenza, tutte le applicazioni Web che aggiornano la tabella dei destinatari vengono ripubblicate durante il post-aggiornamento.
* Risolto un problema di potenziale vulnerabilità XSS nel contenuto di distribuzione. (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) Release 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_8 giugno 2020_

**Novità?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Supporto delle icone</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Durante la progettazione di un messaggio in Campaign, ora puoi inserire facilmente le icone nel corpo del messaggio, utilizzando un pulsante dedicato. Possono anche essere aggiunti nella riga dell’oggetto dell’e-mail. Potete personalizzare l’elenco delle icone disponibili nell’interfaccia.</p>
    <p>Per ulteriori informazioni sull’aggiunta di icone, consultate la documentazione <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons"></a>dettagliata. Scoprite come personalizzare l’elenco delle icone <a href="../../delivery/using/customizing-emoticon-list.md">in questa sezione</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connettore FDA di Azure Synapse</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>È ora possibile collegare l'istanza Campaign al database esterno di Azure Synapse. Questa connessione viene gestita tramite un nuovo account esterno.</p>
    <p>Azure Synapse è disponibile solo per gli ambienti ibridi e locali. Per ulteriori informazioni, consulta la <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">documentazione dettagliata</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Tailandia e Brasile Privacy Laws</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La Legge per la Protezione dei Dati Personali (PPDPA) della Thailandia è la nuova legge sulla privacy che armonizza e aggiorna i requisiti di protezione dei Dati per la Thailandia. </p>
   <p>La società brasiliana Lei Geral de Proteção de Dados (LGPD) entrerà in vigore a partire dal 16 agosto per tutte le aziende che raccolgono o elaborano dati personali in Brasile.</p>
   <p>Queste normative si applicano ai clienti  Adobe Campaign che detengono i dati per i soggetti che risiedono in questi paesi. Oltre alle funzionalità per la privacy già disponibili in Campaign (compresa la gestione del consenso, le impostazioni di conservazione dei dati e i ruoli utente), stiamo sfruttando questa opportunità per includere funzionalità aggiuntive, per facilitare la disponibilità di PDF e LGPD:</p>
   <ul> 
     <li><p>Diritto di accesso e Diritto di eliminazione: stiamo sfruttando le funzionalità aggiunte per il GDPR e il CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Leggi tutto</a></p></li> 
     <li> <p>Quando crei una richiesta di privacy utilizzando l'interfaccia o l'API di Campaign, ora seleziona il tipo di <strong>regolamento</strong> : PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Ulteriori informazioni</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

* Per impostazione predefinita, per tutti i clienti è attivata una protezione migliore per il tracciamento dei collegamenti nelle e-mail. È disponibile un&#39;ulteriore funzione di sicurezza avanzata che può essere abilitata contattando l&#39;Assistenza clienti. Ulteriori dettagli sulla funzionalità e sui passaggi per consentire ai clienti non ospitati di utilizzarla sono disponibili nell&#39;elenco di controllo [Sicurezza e Privacy](https://helpx.adobe.com/campaign/kb/acc-security.html). (NEO-24232)

* Per ottimizzare la sicurezza, l&#39;algoritmo di hash MD5 utilizzato per generare i nomi dei file è stato rafforzato con sha256 per il caricamento di file pubblici. (NEO-17044)

* Per rafforzare la protezione contro gli attacchi XSS, gli script sul lato client vengono disabilitati durante l&#39;esecuzione di una pagina mirror. (NEO-17987)

* È stato risolto un problema che impediva al flusso di lavoro tecnico **Privacy Request Cleanup** di eliminare i dati di riconciliazione. (NEO-25168, NEO-21004)

* È stato risolto un problema con l&#39;attività **Trasferimento** file che impediva il funzionamento dell&#39;autenticazione basata su chiave SFTP su Debian 9. (NEO-23183)

**Miglioramenti della compatibilità**

Campaign supporta ora i seguenti sistemi:
* Sistemi operativi: Debian 10
* RDBMS: Oracle 18c e Oracle 19c
* FDA: Azure Synapse  Analytics

Ulteriori informazioni nella matrice [Compatibilità](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)campagna.

**Miglioramenti**

* I messaggi transazionali sono stati migliorati per una migliore esperienza utente. Ora puoi annullare la pubblicazione di un modello di messaggio transazionale, che lo elimina dalle istanze di esecuzione. [Ulteriori](../../message-center/using/template-unpublication.md)informazioni.

* Sono disponibili nuove opzioni per impostare limitazioni durante l&#39;invio di e-mail che includono immagini o allegati. Tali tutdrail possono evitare problemi di prestazioni, che è particolarmente utile con i messaggi transazionali. [Leggi tutto](../../installation/using/configuring-campaign-options.md#delivery)

* La nuova opzione **Prepara le parti di consegna nel database** consente di eseguire la preparazione della consegna direttamente all&#39;interno del database, il che può accelerare notevolmente l&#39;analisi. Questa opzione è disponibile solo per configurazioni specifiche. [Ulteriori](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)informazioni. (NEO-23886)

* Sono state migliorate le prestazioni dell&#39;attività [del connettore](../../workflow/using/crm-connector.md) CRM per Microsoft Dynamics. (NEO-13303, NEO-12710)

* La versione della memoria condivisa è stata incrementata.

   >[!WARNING]
   >
   >Questo miglioramento richiede un ulteriore passaggio dopo l&#39;esecuzione dell&#39;aggiornamento. Fare riferimento alla sezione **Tecniche evoluzioni** seguente.

* Il flusso di lavoro di pulizia è stato migliorato. Anche le tabelle di lavoro isolate di tutti i flussi di lavoro eliminati ora vengono eliminate automaticamente dal flusso di lavoro di pulizia. [Ulteriori](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)informazioni.

* I certificati per le applicazioni mobili iOS con il connettore iOS HTTP2 ora vengono convalidati prima dell&#39;invio delle notifiche push, impedendo in tal modo la mancata riuscita delle consegne a causa dei certificati scaduti.

* È stata migliorata la gestione delle connessioni proxy HTTP. [Ulteriori](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)informazioni.

**Altre modifiche**

* I vecchi connettori SMS ora sono obsoleti. Consultare la pagina [Funzioni](../../rn/using/deprecated-features.md)obsolete.

* Non è più possibile utilizzare il proprio account Litmus per effettuare il provisioning e utilizzare il rendering Inbox in  Adobe Campaign. [Ulteriori](../../delivery/using/inbox-rendering.md)informazioni.

* Per distinguere meglio le viste dalle cartelle, il colore dei nomi delle viste è stato modificato da blu scuro a ciano scuro. [Leggi tutto](../../platform/using/access-management.md#about-views)

* Campaign Classic può ora essere connesso agli account di Microsoft Dynamics CRM ospitati nelle regioni Regno Unito, India e Canada. Ciò vale per i tipi di distribuzione di Office 365 e locale (Dynamics 2015).

* Campaign esegue ora una verifica TLS per verificare che il nome host del server corrisponda al nome host nel certificato fornito.

* La tabella delle statistiche di consegna e tracciamento ora mostra una voce per ogni consegna per il canale SMS, invece di una voce per destinatario della consegna.

* È stato aggiunto un messaggio di errore nel file di registro per avvisare gli utenti quando il file scaricato è più grande dello spazio su disco.

* Sono ora disponibili le seguenti funzioni per il connettore Snowflake: Mesi Fa, GiorniFaInt, DataDataOra, AnniFa.

**Evoluzioni tecniche**

Questa nuova build aggiorna la memoria condivisa e richiede passaggi aggiuntivi per eseguire l&#39;aggiornamento. In qualità di amministratore di Campaign, devi rimuovere i segmenti di memoria. Questi passaggi sono obbligatori, poiché i vecchi segmenti impediranno l&#39;avvio di nlserver/nlsrvmod.

In Windows, è necessario riavviare il sistema.

Su Debian/CentOs, è necessaria l&#39;eliminazione della memoria condivisa. Di seguito sono riportati i passaggi da seguire:

Prima di eseguire l&#39;aggiornamento, è necessario eseguire la procedura seguente:

1. Arrestate il servizio apache2 (http2 on CentOS) se è in esecuzione.
1. Arrestate il servizio nlserver (nlserver6 per build precedenti) se è in esecuzione.

Dopo l&#39;aggiornamento:

1. Rimuovete la memoria condivisa utilizzando il comando **ipcrm** , se la versione è precedente alla versione corrente.
1. Avviate il servizio nlserver se era in esecuzione.
1. Avviate il servizio apache2 se era in esecuzione.

Ecco le righe di comando per Debian:

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

* Risolto un problema di regressione minore nei registri del flusso di lavoro di pulizia.
* È stato risolto un problema nell&#39;attività di **caricamento del flusso di lavoro (SOAP)** durante l&#39;analisi dei file WSDL.
* È stato risolto un problema che causava un errore durante l’aggiornamento di numerosi flussi di lavoro mediante un’attività **del sondaggio** per elaborare in modo efficiente un elevato numero di flussi di lavoro.
* È stato risolto un problema di connettività intermittente durante l&#39;elaborazione dei messaggi inMail dall&#39;MTA avanzato. (NEO-20380)
* È stato risolto un problema che impediva la corretta visualizzazione delle percentuali di clic con il pulsante di scelta rapida quando le immagini venivano visualizzate con una larghezza del 100% nell’HTML. (NEO-23203)
* È stato risolto un problema che impediva la visualizzazione completa del contenuto condizionale della consegna nel rapporto sui clic attivi. (NEO-18729)
* È stato risolto un problema che ignorava il passaggio di approvazione della destinazione quando si riprendeva un flusso di lavoro per inviare una consegna ricorrente. (NEO-18166)
* È stato risolto un problema che impediva al pulsante **Riavvia preparazione** messaggio di riprendere la consegna dopo la risoluzione di un errore nel flusso di lavoro. (NEO-13488)
* È stato risolto un problema che poteva causare un errore nelle consegne in modalità mid-sourcing durante la fase di rampa verso l’alto, in cui i destinatari inclusi nella destinazione erano in formato e-mail giapponese. (NEO-23846)
* È stato risolto un problema di conversione del fuso orario con il connettore Snowflake (NEO-20105)
* È stato risolto un problema con gli account esterni che utilizzavano FTP su SSL. (NEO-20498)
* È stato risolto un problema che poteva impedire la visualizzazione delle immagini nelle consegne di linea. (NEO-23207)
* È stato risolto un problema che causava un errore durante la pubblicazione di un&#39;offerta. (NEO-23312)
* È stato risolto un problema con le notifiche push che consentiva il funzionamento delle connessioni di prova nelle applicazioni mobili, anche quando il certificato era scaduto. (NEO-22991)
* È stato risolto un problema che poteva interessare le notifiche push quando inviate ad alta frequenza. (NEO-20516)
* È stato risolto un problema che causava l&#39;inclusione di duplicati dei dati di tracciamento anche se i registri di tracciamento non li includevano. (NEO-20040)
* È stato risolto un problema che causava l&#39;invio di e-mail transazionali duplicate dopo la risoluzione di un errore di comunicazione del server di tracciamento. (NEO-23640)
* È stato risolto un problema che eliminava il valore del parametro di codifica durante il reindirizzamento da un URL di tracciamento. (NEO-25637)
* È stato risolto un problema che poteva impedire il funzionamento di una query durante il confronto di numeri mobili. (NEO-23243)
* È stato risolto un problema che poteva impedire la visualizzazione del contenuto **Modificato dal** contenuto della colonna dopo il riavvio di un flusso di lavoro. (NEO-23035)
* È stato risolto un problema che causava un errore nel flusso di lavoro tecnico di tracciamento durante il download dei registri da un secondo contenitore. (NEO-23159)
* È stato risolto un problema che poteva causare un errore nei flussi di lavoro durante l&#39;esecuzione di un&#39;attività di **arricchimento** . (NEO-17338)
* È stato aggiunto un controllo al **doppio per mantenere** il campo nell&#39;attività del flusso di lavoro **Deduplicazione** per impedire l&#39;immissione di valori null o negativi.
* Rimozione della procedura guidata **** Scheduler dalle campagne ricorrenti per evitare di menzionare ore e minuti. Vengono prese in considerazione solo le date.
* È stato risolto un problema relativo ai campi di archiviazione aggiuntivi durante la creazione di consegne tramite l&#39;opzione **Calcolato da uno script** nell&#39;attività del flusso di lavoro **script** . (NEO-20609)
* È stato risolto un problema che impediva l&#39;eliminazione dei flussi di lavoro fantasma nelle attività di pulizia del database.
* È stato risolto un problema che causava il fallimento del flusso di lavoro tecnico di **fatturazione (profili attivi)** . (NEO-19777)
* È stato risolto un problema durante il test della connessione dell&#39;account esterno acsDefaultAccount. (NEO-23433)
* È stato risolto un problema che impediva la creazione di un&#39;estensione dello schema su una chiave primaria con più colonne con una tabella Hadoop. (NEO-17390)
* È stato risolto un problema nell&#39;attività di **caricamento (SOAP)** che poteva impedire il caricamento di file WSDL da un URL. (NEO-16924)
* È stato risolto un problema che impediva l&#39;esecuzione di un arresto **** non condizionale nella console in caso di bilanciamento del carico di più server del flusso di lavoro attivi. (NEO-19556)
* È stata corretta una regressione che causava l’arresto anomalo del flusso di lavoro di pulizia.
* È stato risolto un problema che poteva verificarsi durante la pubblicazione di un modello in un&#39;istanza di esecuzione.
* È stato risolto un problema che poteva impedire l&#39;esecuzione del flusso di lavoro tecnico collectPrivacyRequests. (NEO-20513, NEO-25169)
* Sono stati risolti i problemi che potevano verificarsi quando si tentava di connettersi a  Audience Manager dopo l&#39;aggiornamento alla build 9080. (NEO-20511, NEO-25167)
* Risolti i problemi che potevano verificarsi durante l&#39;esportazione di rapporti in formato PDF o XLS. (NEO-20982, NEO-23493, NEO-23348)
* È stato risolto un problema che poteva visualizzare due volte una consegna nell&#39;elenco di consegna dopo l&#39;invio.
* È stato risolto un problema di preparazione della consegna che poteva verificarsi quando la configurazione del routing era impostata per inviare la consegna tramite mid-sourcing.
* È stato risolto un problema che poteva visualizzare un messaggio di errore quando si faceva clic su un collegamento di applicazione Web all&#39;interno di un messaggio di riga.
* È stato risolto un problema che poteva impedire a Microsoft Dynamics CRM di recuperare tutte le entità. (NEO-24528)
* È stato risolto un problema che eliminava la cronologia dell&#39;attività di query **** incrementale dopo l&#39;esecuzione del flusso di lavoro di pulizia.
* È stato risolto un problema che si verificava durante la creazione di un account esterno mid-sourcing a causa del quale mancava l&#39;opzione NmsMidSourcing_LastBroadLog_&lt;InternalName>
