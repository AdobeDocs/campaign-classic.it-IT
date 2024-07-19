---
product: campaign
title: Monitoraggio dei processi
description: Scopri come monitorare i processi di Campaign
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '3643'
ht-degree: 0%

---

# Monitoraggio dei processi{#monitoring-processes}


Il server applicazioni e il server di reindirizzamento (**monitoraggio**) possono essere monitorati manualmente o automaticamente.

## Monitoraggio manuale {#manual-monitoring}

Per accedere alla pagina di monitoraggio dei processi di Adobe Campaign, passare alla scheda **[!UICONTROL Monitoring]** e fare clic sul collegamento **[!UICONTROL Overview]**.

![](assets/d_ncs_monitoring.png)

La pagina visualizzata consente di visualizzare lo stato dell’istanza connessa, ovvero:

* informazioni sull’istanza: versione, nome, motore di database, pacchetti installati, indicatori del sistema del server,
* l’elenco dei processi mancanti e delle informazioni di esecuzione (data di inizio, PID, ecc.),
* una visualizzazione dei flussi di lavoro e delle consegne.

Ulteriori modi per monitorare i processi di Campaign sono presentati in [questa pagina](../../production/using/monitoring-guidelines.md).

### Giornale di registrazione {#log-journal}

Per visualizzare il giornale di registrazione relativo a un processo, fare clic sul processo, ad esempio **mta**, quindi selezionare **[!UICONTROL Open the log journal]**.

![](assets/d_ncs_monitoring2.png)

### Indicatori di sistema {#system-indicators}

Selezionare l&#39;elenco degli indicatori di sistema per visualizzare le informazioni relative alla macchina, ad esempio la memoria fisica e virtuale, i processi attivi e lo spazio disponibile su disco. Gli indicatori sono diversi per i sistemi operativi Linux e Windows. Vai alla pagina **[!UICONTROL Instance Monitoring]** e fai clic sul collegamento **[!UICONTROL Display]** per aprire l&#39;elenco degli indicatori.

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]**: indicatore specifico per **Centro messaggi**. [Ulteriori informazioni](../../message-center/using/additional-configurations.md#monitoring-thresholds)

* **[!UICONTROL Memory]**: informazioni relative alla memoria fisica (RAM).

  **[!UICONTROL Current value]**: consumo di memoria corrente.

  **[!UICONTROL Max Value]**: quantità totale di memoria installata.

  **[!UICONTROL Available]**: memoria disponibile.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge l&#39;80% della quantità totale.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge il 90% della quantità totale.

  Quando vengono visualizzati gli indicatori **[!UICONTROL Warning]** e **[!UICONTROL Alert]**, è possibile risolvere il problema aggiungendo RAM al computer in cui è installato il server Adobe Campaign. Puoi anche decidere di installare il server Adobe Campaign su un computer dedicato.

* **[!UICONTROL Swap Memory]**: informazioni relative alla memoria virtuale corrispondenti a un file di paging: un&#39;area del disco rigido utilizzata da Windows come se fosse RAM.

  **[!UICONTROL Current value]**: consumo effettivo di memoria.

  **[!UICONTROL Max Value]**: memoria totale.

  **[!UICONTROL Available]**: memoria disponibile.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge l&#39;80% della quantità totale.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge il 90% della quantità totale.

  Quando vengono visualizzati gli indicatori **[!UICONTROL Warning]** e **[!UICONTROL Alert]**, è possibile risolvere il problema aumentando le dimensioni del file Exchange nelle impostazioni avanzate di Windows.

* **[!UICONTROL Disk XXX]**: informazioni relative ai lettori di computer.

  **[!UICONTROL Current value]**: spazio su disco effettivamente utilizzato.

  **[!UICONTROL Max Value]**: capacità disco totale.

  **[!UICONTROL Available]**: spazio su disco disponibile.

  **[!UICONTROL Used]**: percentuale del disco utilizzato.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando lo spazio disponibile su disco raggiunge l&#39;80% della capacità totale.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando lo spazio disponibile su disco raggiunge il 90% della capacità totale.

* **[!UICONTROL Number of processes too old]**: informazioni relative ai processi Adobe Campaign attivi da più di un giorno.

  **[!UICONTROL Current value]**: numero di processi attualmente attivi.

  **[!UICONTROL Max Value]**: numero massimo di processi autorizzati (1).

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato se il numero di processi è uguale a 1.

  Quando viene visualizzato l&#39;indicatore **[!UICONTROL Alert]**, è possibile che il processo interessato sia bloccato dal modulo di gestione di database SQL o che sia bloccato in un ciclo infinito. Il processo **watchdog** fornito da Adobe Campaign riavvia automaticamente tutti i processi ogni giorno e consente di risolvere il problema. Tuttavia, puoi anche interrompere personalmente il processo in questione per forzare il riavvio.

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]**: indicatore specifico per **Centro messaggi**. Per ulteriori informazioni, consultare [questa sezione](../../message-center/using/additional-configurations.md#monitoring-thresholds).

* **[!UICONTROL Load average (1/5/15 minutes)]**: informazioni relative al carico, ovvero la velocità di utilizzo del processore da parte dei processi in esecuzione sul computer nell&#39;ultimo minuto, cinque minuti o quindici minuti

  **[!UICONTROL Current value]**: carico effettivo del computer.

  **[!UICONTROL Max value]**: carico di utilizzo massimo dei processi nel computer

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il carico raggiunge l&#39;80% del valore massimo autorizzato nell&#39;ultimo minuto, cinque minuti o quindici minuti.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il carico raggiunge il 90% del valore massimo autorizzato dell&#39;ultimo minuto, cinque minuti o quindici minuti.

* **[!UICONTROL Memory]** informazioni relative alla memoria fisica (RAM).

  **[!UICONTROL Current value]**: consumo effettivo di memoria.

  **[!UICONTROL Max Value]**: quantità totale di memoria installata.

  **[!UICONTROL Available]**: memoria disponibile.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge l&#39;80% della quantità totale.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge il 90% della quantità totale.

  Quando vengono visualizzati gli indicatori **[!UICONTROL Warning]** e **[!UICONTROL Alert]**, è possibile risolvere il problema aggiungendo RAM al computer in cui è installato il server Adobe Campaign. Puoi anche decidere di installare il server Adobe Campaign su un computer dedicato.

* **[!UICONTROL Swap Memory]**: informazioni relative alla memoria virtuale corrispondenti a un file di paging: un&#39;area del disco rigido utilizzata da Windows come se fosse RAM.

  **[!UICONTROL Current value]**: consumo effettivo di memoria.

  **[!UICONTROL Max Value]**: memoria totale.

  **[!UICONTROL Available]**: memoria disponibile.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge l&#39;80% della quantità totale.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il consumo di memoria raggiunge il 90% della quantità totale.

  Quando vengono visualizzati gli indicatori **[!UICONTROL Warning]** e **[!UICONTROL Alert]**, è possibile risolvere il problema aumentando le dimensioni del file di Exchange.

* **[!UICONTROL Core Files]**: informazioni relative ai file generati in seguito all&#39;arresto anomalo di un processo Adobe Campaign. Questi file consentono di diagnosticare i motivi dell&#39;arresto anomalo.

  **[!UICONTROL Current Value]**: numero di file esistenti.

  **[!UICONTROL Max Value]**: numero massimo di file autorizzati (1).

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il numero di file si avvicina a 1.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il numero di file è uguale a 1.

  Quando un processo risulta mancante a causa di un arresto anomalo, viene visualizzato in rosso nell&#39;elenco dei processi e viene riavviato automaticamente dal processo **watchdog** fornito da Adobe Campaign.

* **[!UICONTROL Number of shared memory segments]**: informazioni relative ai segmenti di memoria condivisi da tutti i processi Adobe Campaign.

  **[!UICONTROL Current value]**: numero di segmenti di memoria attualmente in uso.

  **[!UICONTROL Max Value]**: numero massimo di segmenti di memoria autorizzati (2).

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il numero di segmenti di memoria raggiunge 1.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il numero di segmenti di memoria raggiunge 2.

* **[!UICONTROL Number of processes too old]**: informazioni relative ai processi attivi da più di un giorno.

  **[!UICONTROL Current value]**: numero di processi attualmente attivi.

  **[!UICONTROL Max Value]**: numero massimo di processi autorizzati.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il numero di processi raggiunge l&#39;80% della soglia autorizzata.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il numero di processi raggiunge il 90% della soglia autorizzata.

* **[!UICONTROL File Handles]**: informazioni relative ai descrittori dei file, ovvero il numero di file aperti per processo.

  **[!UICONTROL Current value]**: numero corrente di descrittori di file.

  **[!UICONTROL Max Value]**: numero massimo di descrittori di file autorizzati dal sistema operativo.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il numero di descrittori di file autorizzati raggiunge la soglia dell&#39;80%.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il numero di descrittori di file autorizzati raggiunge la soglia del 90%.

* **[!UICONTROL Processes]**: informazioni relative ai processi del computer.

  **[!UICONTROL Current value]**: numero di processi attualmente attivi.

  **[!UICONTROL Max Value]**: numero massimo di processi autorizzati.

  **[!UICONTROL Active Processes]**: numero di processi attivi.

  **[!UICONTROL Inactive Processes]**: numero di processi inattivi.

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il numero di processi autorizzati raggiunge la soglia dell&#39;80%.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il numero di processi autorizzati raggiunge la soglia del 90%.

* **[!UICONTROL Zombie Processes]**: informazioni relative ai processi interrotti ma con un identificatore di processo (PID) ancora visibile nella tabella del processo.

  **[!UICONTROL Current value]**: numero di processi zombie attualmente attivi.

  **[!UICONTROL Max Value]**: numero massimo di processi di autorizzazione zombie (2).

  **[!UICONTROL Warning]**: questo indicatore viene visualizzato quando il numero di processi zombie si avvicina a 2.

  **[!UICONTROL Alert]**: questo indicatore viene visualizzato quando il numero di processi zombie raggiunge 2.

#### Personalizzare gli indicatori {#customized-indicators}

Adobe Campaign consente di personalizzare gli indicatori, come descritto di seguito:

1. Creare un file **.sh** e denominarlo **[!UICONTROL cust_indicators.sh]**.
1. Aggiungi gli indicatori personalizzati a questo file. Ad esempio:

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   o

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. Salvare il file nella cartella **[!UICONTROL usr/local/neolane/nl6]**.

Questo file viene richiamato da Adobe Campaign.

## Rapporti SMTP {#smtp-reports}

I rapporti di monitoraggio della consegna SMTP sono integrati nella piattaforma Adobe Campaign. È possibile accedervi tramite la console o utilizzando l’accesso web.

Questi rapporti visualizzano le statistiche di consegna SMTP e gli errori SMTP per dominio. Per accedervi, l&#39;operatore deve disporre dei diritti di **Amministrazione**.

Sono raggruppati in **Monitoraggio** > &#39;Monitoraggio SMTP&#39;.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* Le informazioni relative al monitoraggio SMTP sono disponibili solo se il canale e-mail è stato attivato.
>* **[!UICONTROL SMTP sending statistics]** sono offerti solo se il server delle statistiche è avviato nell&#39;istanza.
>

### Statistiche di invio SMTP {#smtp-sending-statistics}

Il report **[!UICONTROL SMTP sending statistics]** consente di controllare l&#39;attività del server. Visualizza una sintesi di ciascuno dei metafiltri.

![](assets/smtp_stats_report.png)

L’elenco degli indicatori per questo rapporto è riportato sotto il grafico.

1. Numero totale di messaggi inviati.
1. Rappresenta i messaggi in/out:

   * Linea blu: messaggi pronti per l’invio arrivati nello shaper, ovvero l’ultima fase prima dell’invio di SMTP (coincide con i dati in arrivo).

   * Linea verde: messaggi inviati correttamente (coincide con i dati in uscita).

   * Linea rossa: messaggi abbandonati da Shaper, restituiti a **mta** (coincide con i dati rifiutati durante il ripristino).

   Questi valori sono espressi in numero di messaggi all’ora.

1. Rappresenta due code dello shaper:

   * Curva blu: coda di messaggi attivi. Questi messaggi saranno inviati il prima possibile.

   * Curva di Kaki: la coda &#39;differita&#39;. Questi messaggi non possono essere restituiti per il momento a causa di limitazioni o perché non è disponibile alcuna connessione alla destinazione. I tentativi avranno luogo ogni 5, 10, 20, 40, 2 min, ecc. per il periodo di tempo definito **MaxAgeSec** prima di essere abbandonato.

1. Questo grafico mostra un dettaglio dei messaggi abbandonati (curva rossa nel secondo grafico): mostra la proporzione di messaggi abbandonati senza nuovi tentativi (malva) rispetto ai messaggi con invio non riuscito (rossa). Questo consente di visualizzare la proporzione di messaggi non elaborati entro il periodo concesso a causa di limitazioni del server di statistiche (limitazione) o a causa dell’indisponibilità del server remoto.
1. Le connessioni SMTP si aprono o vengono aperte.
1. Stima del numero di **mtachild**.

>[!NOTE]
>
>Questo report è correlato allo stato del componente Traffic Shaper e-mail.

### Errori SMTP per dominio {#smtp-errors-per-domain}

Questo rapporto ti consente di visualizzare gli errori di consegna, in un periodo impostato, suddivisi per dominio.

>[!NOTE]
>
>Le opzioni **minConnectionsToLog**, **minErrorsToLog** e **minMessagesToLog** del file **serverConf.xml** definiscono le soglie oltre le quali vengono prese in considerazione le statistiche di connessione.

![](assets/smtp_error_report.png)

L’elenco degli indicatori per questa relazione è riportato sotto la tabella.

* La colonna **Dominio** contiene il nome del dominio a cui vengono inviati i messaggi (o il nome di dominio reale, yahoo.com ad esempio, yahoo.fr),
* La colonna **Cnx** visualizza il numero di connessioni SMTP aperte per questo dominio.
* La colonna **Inviato** corrisponde al numero di messaggi inviati a questo dominio.
* La colonna **Volume** visualizza il volume di messaggi che sono stati tentati di inviare a questo dominio (valore approssimativo).
* La colonna **Errori** visualizza un indicatore di volume degli errori in questo dominio nel periodo.
* Nella colonna **Ultima risposta** viene visualizzato l&#39;ultimo messaggio di risposta SMTP ricevuto per questo dominio.
* La colonna **Data** visualizza la data dell&#39;ultima risposta SMTP ricevuta per questo dominio.

>[!NOTE]
>
>I valori visualizzati nelle colonne **Cnx**, **Sent** e **Volume** vengono calcolati rispetto al periodo selezionato nel campo **[!UICONTROL Period]**.

Fai clic su un nome di dominio per visualizzarne gli errori.

Sono categorizzati in base al PublicId: questo identificatore corrisponde a un indirizzo IP condiviso da diversi mta di Adobe Campaign dietro un router. Il server delle statistiche utilizza questo identificatore per memorizzare le statistiche di connessione e consegna tra questo punto iniziale e il server di destinazione.

![](assets/smtp_error_report_details.png)

Il campo **[!UICONTROL Owner of domain]** consente di raggruppare vari nomi di dominio con la stessa etichetta. Nella visualizzazione del rapporto iniziale, tutti i nomi di dominio MX saranno associati a questo proprietario.

Fai clic su un identificatore PublicId per visualizzare ulteriori dettagli.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>La percentuale di errori è rappresentata da due grafici. La prima è una barra di avanzamento orizzontale su sfondo nero. Il secondo grafico è cronologico. Il periodo selezionato è diviso in dodici intervalli di tempo, ciascuno rappresentato da una barra di avanzamento verticale. In entrambe le rappresentazioni, se non è stato rilevato alcun errore, la barra è nera. Il colore della barra dipende dalla percentuale di errori riscontrati (giallo, arancione e infine rosso). Il colore grigio indica che non è stato trovato alcun volume di dati significativo. È possibile visualizzare la percentuale esatta di errori posizionando il cursore sul grafico.

>[!NOTE]
>
>Per ulteriori informazioni sugli errori SMTP e sulla loro gestione in Adobe Campaign, consulta [questa sezione](../../installation/using/email-deliverability.md).

## Rapporto di fatturazione {#billing-report}

Il flusso di lavoro tecnico **[!UICONTROL Billing]** invia il report sull&#39;attività di sistema all&#39;operatore di fatturazione tramite e-mail. Viene attivato per impostazione predefinita il 25 di ogni mese sull’istanza Marketing.

Il flusso di lavoro tecnico si trova in una sottocartella del seguente nodo: **Amministrazione** > **Produzione** > **Flussi di lavoro tecnici**.

![](assets/billing.png)

Una volta avviato il flusso di lavoro ogni 25 del mese, l’operatore di fatturazione riceverà il seguente rapporto nella propria casella in entrata.

![](assets/billing_2.png)

Per tenere traccia delle consegne sono disponibili le metriche seguenti:

* **[!UICONTROL Start date]**: data di inizio della consegna. Tieni presente che può essere precedente alla data &quot;da&quot; del rapporto.
* **[!UICONTROL Label]**: etichetta della consegna. Le consegne con meno di 100 messaggi da inviare sono considerate troppo piccole e quindi aggregate per data di inizio, nel qual caso l&#39;etichetta visualizza il numero di aggregati, ad esempio [Aggregazione di 3 consegne di piccole dimensioni].
* **[!UICONTROL Total volume]**: volume totale di byte trasferiti per la consegna.
* **[!UICONTROL Avg volume]**: volume medio di byte trasferiti. Questo è il risultato della seguente formula **(volume totale/messaggi)**, che è la base di calcolo della metrica **[!UICONTROL Multiplier]**.
* **[!UICONTROL Messages]**: numero di messaggi inviati. Ciò include sia i messaggi inviati correttamente sia i tentativi (in seguito alla ricezione di un messaggio di mancato recapito dal server contattato).
* **[!UICONTROL Multiplier (x)]** : il valore del moltiplicatore viene dedotto dal volume medio dei messaggi.
* **[!UICONTROL Count]** : risultato della moltiplicazione dei messaggi e del moltiplicatore.

## Monitoraggio automatico {#automatic-monitoring}

Adobe Campaign offre diversi metodi di monitoraggio automatico, descritti di seguito.

### Riga di comando {#command-line}

Comando

**nlserver monitor**

Consente di elencare una serie di indicatori sui moduli Adobe Campaign e sul sistema.

Genera output in un formato XML facilmente elaborato.

Questo comando può essere eseguito anche con il parametro **-missing**, che elenca i processi mancanti in questa istanza quando i file di configurazione dicono che devono essere in esecuzione.

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### Informazioni pubblicate dal server {#information-published-by-the-server}

#### /r/test {#r-test}

La pagina **http(s)://`<application>`/r/test** viene utilizzata per testare il server di reindirizzamento. È consigliabile utilizzare questo stesso metodo per testare i server frontali utilizzati per il tracciamento. Questa pagina può essere utilizzata anche per testare un dispatcher di carico.

Visualizza una riga come questa in formato XML:

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**Frequenza**: questo test non utilizza alcun carico e può essere eseguito molto spesso (ad esempio una volta al secondo).

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

Questa pagina **http(s)://`<Application server url>`/nl/jsp/ping.jsp** funziona come la sua controparte di rete: verifica una query completa che passa attraverso apache/tomcat/modulo web/database e carica sul client. Se tutto funziona correttamente, restituisce un &quot;OK&quot;. È consigliabile eseguire questo test su computer con accesso ai database (ad esempio, mta e sondaggi).

**Utilizzo**: un token di sessione associato a un account di accesso dell&#39;operatore deve essere passato come argomento per eseguire l&#39;accesso in modalità remota (vedere il suggerimento in [Monitoraggio automatico tramite script Adobe Campaign](#automatic-monitoring-via-adobe-campaign-scripts)).

Ad esempio:

![](assets/ncs_monitoring_ping.png)

Il nome dell’operatore e l’accesso devono essere configurati in precedenza nella console client di Adobe Campaign con i diritti del database.

![](assets/ncs_operators_rights_01.png)

**Frequenza**: questo test utilizza una larghezza di banda molto ridotta. Può quindi essere eseguito abbastanza spesso, anche se non più di una volta al minuto.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

Questo è un test per verificare che un operatore possa accedere al server Adobe Campaign tramite una pagina web; la stessa pagina web a cui si accede tramite i menu della console client. Puoi richiamare questa pagina dai tuoi strumenti di sorveglianza (Tivoli, Nagios, ecc.).

![](assets/ncs_monitoring_web.png)

**Utilizzo**: è necessario utilizzare come argomento un token di sessione associato a un account di accesso dell&#39;operatore che consente di connettersi all&#39;istanza (vedi il suggerimento in [Monitoraggio automatico tramite script Adobe Campaign](#automatic-monitoring-via-adobe-campaign-scripts)).

L’operatore e il relativo accesso devono essere configurati in precedenza nella console client di Adobe Campaign con i diritti e le restrizioni del database appropriati.

**Frequenza**: questo è un test server completo e non deve essere eseguito spesso (può essere eseguito una volta ogni dieci minuti, ad esempio).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

**jsp** rappresenta il punto di ingresso delle API dell&#39;applicazione Adobe Campaign. Essa può pertanto fornire un monitoraggio dettagliato della domanda. Può essere utilizzato anche per monitorare i servizi web di Adobe Campaign. Viene utilizzato nei nostri script di monitoraggio, ma tieni presente che è solo per gli utenti esperti.

### Monitoraggio basato sui tipi di distribuzione {#monitoring-based-on-deployment-types}

Adobe Campaign abilita diverse configurazioni di distribuzione (per ulteriori informazioni, consulta [questa sezione](../../installation/using/hosting-models.md)). Questa sezione descrive le varie tecniche di monitoraggio automatico da applicare a seconda del tipo di installazione.

<table> 
 <thead> 
  <tr> 
   <th> Tipo di distribuzione </th> 
   <th> Monitoraggio </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Autonomo </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/monitor.jsp</span> sul server Adobe Campaign</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Standard </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/ping.jsp</span> sui server frontali</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> sul server applicazioni</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Enterprise </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/ping.jsp</span> sui server frontali</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> e <span class="uicontrol">/nl/jsp/monitor.jsp</span> sul server applicazioni</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> sul server applicazioni</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Monitoraggio automatico tramite script di Adobe Campaign {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign può fornire uno strumento di monitoraggio delle istanze (netreport) che consente di inviare un rapporto via e-mail relativo alle anomalie rilevate.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>Questo strumento può essere utilizzato per monitorare le istanze, ma non è supportato da Adobe Campaign. Per ulteriori informazioni, contatta l’amministratore di Campaign.

### Elementi richiesti {#required-elements}

Per il monitoraggio automatico sono necessarie le seguenti precauzioni di preinstallazione:

* Devi disporre dei file **netreport.tgz** (installazione Linux) o **netreport.zip** (installazione Windows),
* Consigliamo vivamente di non installare il monitoraggio sul computer da monitorare,
* deve essere installato su un computer con JRE o JDK,
* in Linux, il computer da monitorare deve avere il pacchetto **bc**. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages).

### Procedura di installazione {#installation-procedure}

La procedura di installazione è la seguente:

1. Nella console, crea un nuovo operatore, se necessario (l’utente &quot;di monitoraggio&quot; esiste già), ma non assegna diritti.
1. Esegui estrazione archivio.
1. Leggi il file **readme**.
1. Aggiorna il file di configurazione **netconf.xml**.
1. Aggiorna il file **netreport.bat** (Windows) o **netreport.sh** (Linux).

### Configurazione del file netconf.xml {#configuring-the-netconf-xml-file}

Il file di configurazione XML contiene i seguenti elementi:

* [Elemento &quot;Properties&quot;](#properties--element)
* [Elemento &#39;Instance&#39;](#instance--element)
* [Elemento &quot;Host&quot;](#host--element)
* [Sottoelementi](#sub-elements)

Di seguito è riportato un esempio di configurazione:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>È possibile specificare varie configurazioni aggiungendo un suffisso al file **netconf.xml**, ad esempio **netconf-dev.xml**, **netconf-prod.xml** e così via. Specificare quindi la configurazione da utilizzare per l&#39;esecuzione di netreport nei file **netreport.bat** o **netreport.sh** aggiungendo ad esempio **$JAVA_HOME/bin/java netreport dev** o **@%JAVA_HOME%binjava netreport prod**.

>[!IMPORTANT]
>
>Affinché l&#39;operatore **monitoraggio** funzioni, il computer su cui viene eseguito netreport deve trovarsi in un&#39;area di sicurezza in modalità **sessionTokenOnly**. Se per questo operatore non è stata specificata alcuna maschera IP attendibile, l&#39;area di sicurezza deve essere anche in modalità **allowEmptyPassword** e **allowUserPassword**.

#### Elemento &quot;Properties&quot; {#properties--element}

Questo elemento viene utilizzato per popolare la configurazione delle e-mail, ad esempio

* **mailServer**: server SMTP utilizzato per inviare le e-mail (esempio: smtp.domain.net).
* **mailFrom**: indirizzo e-mail del mittente del report (esempio: monitoring@domain.net).
* **recipientList**: elenco di indirizzi e-mail dei destinatari del monitoraggio. Gli indirizzi devono essere separati da virgole (senza spazi).
* La modalità &#39;**notte**&#39; (facoltativa) viene utilizzata per evitare l&#39;invio di e-mail tra il periodo di tempo specificato. Al contrario, i dati vengono consolidati e un’e-mail riguardante l’attività della notte viene inviata dopo l’ora di fine (7:00 per impostazione predefinita).
* Il sottoelemento **buildRange** (facoltativo) consente di specificare un numero di build minimo e massimo. Verrà generato un errore per tutti i computer il cui numero di build non rientra in questo intervallo

  ```
  <buildRange minimum="0000" maximum="9999"/>
  ```

* È possibile aggiungere un sottoelemento **`<sla>`** (facoltativo) nell&#39;elemento **properties**. A ogni esecuzione del netreport verrà generato un file di log. Il nome del file contiene il nome della configurazione e la data e l&#39;ora, ad esempio **dev_06_12_13_16_47_05.tmp**. Il file contiene le seguenti informazioni: nome dell’istanza, nome del computer, livello di gravità, (da 0 a 3, da meno critico a più critico), data (formato marca temporale), tempo trascorso (in millisecondi) tra la query e la risposta, servizio utilizzato (http, ncs, ncsex, redir). Queste informazioni sono separate da segni di tabulazione e interruzioni di riga alla fine di ciascun servizio.

>[!NOTE]
>
>L&#39;attributo **persistHtmlFile** con valore &quot;true&quot; nell&#39;elemento **`<property>`** viene utilizzato per registrare lo stato di monitoraggio più recente nel file **netreport.md**. Il file viene salvato nella directory di installazione.

#### Elemento &#39;Instance&#39; {#instance--element}

Questo elemento consente di raggruppare più computer (host) nella stessa istanza. I nomi delle istanze vengono visualizzati nella prima parte del messaggio e-mail di monitoraggio. Puoi fare clic sul nome di un’istanza per accedere ai dettagli relativi a ciascun computer.

```
instance name="instance-name" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **nome**: nome dell&#39;istanza che verrà visualizzato nella prima parte dell&#39;e-mail.
* **recipientList** (facoltativo): ti consente di inviare tramite e-mail un rapporto di monitoraggio relativo a una particolare istanza.

#### Elemento &quot;Host&quot; {#host--element}

Questo elemento configura il monitoraggio di un dato server sull’host, ovvero

* **nome**: nome del computer da monitorare.
* **alias** (facoltativo): nome del computer monitorato che verrà visualizzato nel report.
* **sessionToken**: fornisce l&#39;autenticazione di accesso tramite un token di sessione autorizzato.

  Per configurare il token di sessione, seleziona l&#39;operatore **monitoraggio** nella console Adobe Campaign. Nella scheda **Diritti di accesso**, specifica gli indirizzi IP dei computer autorizzati a monitorare questa istanza. Potrai quindi connetterti alla pagina di monitoraggio da tali computer utilizzando l&#39;identificatore **monitoraggio** e senza dover specificare una password.

  ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** (facoltativo): consente di ordinare gli errori in base al livello di gravità. I valori possibili sono &#39;0&#39; (tutti i livelli visualizzati), &#39;1&#39; (solo gli errori alti e critici visualizzati) e &#39;2&#39; (solo gli errori critici visualizzati). Se questo attributo non viene fornito, vengono visualizzati tutti i livelli di errore.
* **filter** (facoltativo): consente di escludere alcuni errori del flusso di lavoro, ad esempio **filter=&quot;wkf;wkf1&quot;**. Le etichette del flusso di lavoro devono essere separate da un punto e virgola.

#### Sottoelementi {#sub-elements}

* **tcp**: verifica se il server è attivo o inattivo. Immettere un numero di porta.
* **http**: verifica che il server Web esista (il server applicazioni è operativo).
* **ncs**: controlla i processi nell&#39;istanza immessa nell&#39;attributo &#39;instance&#39; (errori del flusso di lavoro, utilizzo della memoria, ecc.). L&#39;attributo **included** (obbligatorio) consente di visualizzare i processi inattivi (valori &#39;true&#39; o &#39;false&#39;).
* **redir**: verifica il tracciamento.

Nella maggior parte dei casi, è possibile mantenere solo i sottoelementi **ncs** e **redir**.

In ogni caso, alcuni nodi possono essere sovraccaricati nei sottoelementi (ad esempio, il nodo **port=75** per sovraccaricare la porta utilizzata per la connessione http, ncs o redir):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

Nei sottoelementi **ncs**, **redir** e **http**, è possibile aggiungere l&#39;attributo **isSecure** (facoltativo) per scegliere se utilizzare o meno il protocollo https (valori &#39;true&#39; o &#39;false&#39;). Se questo attributo non viene fornito, viene utilizzato il protocollo http.

### Configurazione del file netreport.bat o netreport.sh {#configuring-the-netreport-bat-or-netreport-sh--file}

Per configurarlo, modifica questo file e indica in quale directory è installato JRE o JDK.

### Avvio del monitoraggio {#launching-monitoring}

Per avviare il monitoraggio, eseguire il file **netreport.bat** o **netreport.sh** a intervalli regolari tramite uno script. Un rapporto viene inviato dopo la prima esecuzione e quindi solo in caso di cambiamento di stato.

### Verifica del monitoraggio {#testing-monitoring}

Per verificare il monitoraggio, eseguire il file **netreport.bat** o **netreport.sh**.

Viene inviata un&#39;e-mail ai destinatari specificati in **recipientList** del file **netconf.xml**.
