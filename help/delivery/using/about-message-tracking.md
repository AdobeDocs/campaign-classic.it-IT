---
product: campaign
title: Introduzione al tracciamento
description: Scopri le linee guida generali per il tracciamento in Adobe Campaign
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 2%

---

# Introduzione al tracciamento dei messaggi {#get-started-tracking}

>[!IMPORTANT]
>
>Per **informazioni generali sul tracciamento** valide sia per Campaign Classic v7 che per Campaign v8, consulta la [documentazione sul tracciamento dei messaggi per Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}:
>
>* [Configura collegamenti tracciati](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [Configurare le opzioni di tracciamento URL](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [Tracciamento collegamenti personalizzati](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [Registri di tracciamento degli accessi](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [Tracciamento dei test](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [Rapporti di tracciamento](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**In questa pagina sono documentate solo le funzionalità di tracciamento specifiche di Campaign Classic v7**, principalmente per le distribuzioni ibride e on-premise.

## Funzioni di tracciamento

### Configurazione di tracciamento {#configure-tracking}

Per le **distribuzioni ibride/on-premise** di Campaign Classic v7, è necessario configurare il tracciamento a livello di istanza prima di utilizzarlo.

>[!NOTE]
>
>Per Campaign v8 Managed Cloud Services, la configurazione del tracciamento viene eseguita da Adobe.

**Principio di funzionamento**

Prima di utilizzare il tracciamento, devi configurarlo per la tua istanza. La configurazione deve essere eseguita sui server applicazioni Adobe Campaign e sui server web.

In Campaign sono disponibili due tipi di tracciamento:

* **Tracciamento web**: questa modalità ti consente di tenere traccia delle visite alle pagine del tuo sito web
* **Tracciamento messaggi**: questa modalità consente di tenere traccia delle consegne dei messaggi e del comportamento dei destinatari

La modalità di tracciamento viene selezionata durante l’installazione. Per le installazioni on-premise, la configurazione del tracciamento deve essere definita a livello di istanza. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#operating-principle)

**Server di monitoraggio**

Per configurare il tracciamento, l’istanza deve essere dichiarata e registrata con i server di tracciamento. Il server di tracciamento viene utilizzato per registrare e recuperare informazioni sugli URL su cui i destinatari hanno fatto clic.

Per le installazioni on-premise, il server di tracciamento è in genere un server web che esegue l’applicazione web Adobe Campaign. L’URL del server di tracciamento deve essere definito nella configurazione dell’istanza. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#tracking-server)

**Salvataggio del tracciamento**

Una volta configurato il tracciamento e popolati gli URL, è necessario registrare il server di tracciamento. La registrazione consente ad Adobe Campaign di salvare le informazioni di tracciamento e di fornire rapporti e statistiche sulle attività tracciate.

Per le installazioni on-premise, le informazioni di tracciamento vengono memorizzate nel database e recuperate tramite flussi di lavoro tecnici. Il flusso di lavoro tecnico **Tracking** elabora e memorizza i dati di tracciamento raccolti dal server di reindirizzamento. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#saving-tracking)

### Tracciamento delle applicazioni web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**Il tracciamento delle applicazioni Web è specifico di Campaign Classic v7** e non è disponibile in Campaign v8.

**Tracking di un’applicazione web**

È inoltre possibile monitorare e misurare le visite sulle pagine delle applicazioni web con i tag di tracciamento. Questa funzionalità può essere utilizzata per tutti i tipi di applicazioni Web, ad esempio moduli e pagine di destinazione. [Ulteriori informazioni](../../web/using/tracking-a-web-application.md)

**Rinuncia al tracking delle applicazioni web**

La rinuncia al tracciamento delle applicazioni web consente di interrompere il tracciamento dei comportamenti web degli utenti finali che rinunciano al tracciamento comportamentale. Puoi includere la possibilità di visualizzare un banner nelle applicazioni web o nelle pagine di destinazione per consentire agli utenti di rinunciare. [Ulteriori informazioni](../../web/using/web-application-tracking-opt-out.md)

## Risoluzione dei problemi di tracciamento {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

I seguenti suggerimenti per la risoluzione dei problemi si applicano alle **distribuzioni ibride/on-premise di Campaign Classic v7**. Alcune informazioni possono essere applicate anche alle distribuzioni on-premise di Campaign v8. Per Campaign v8 Managed Cloud Services, contatta il rappresentante Adobe per assistenza.

Per i passaggi di base per la risoluzione dei problemi di tracking in Campaign v8, consulta [Risoluzione dei problemi di tracking nella documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}.

### Controlli di base {#basic-checks}

**Verificare che il processo trackinglogd sia in esecuzione**

Questo processo legge dalla memoria condivisa IIS/server Web e scrive i registri di reindirizzamento.

Puoi accedervi dalla homepage selezionando la scheda Monitoraggio nella tua istanza. È inoltre possibile eseguire il comando seguente sull&#39;istanza: `<user>@<instance>:~$ nlserver pdump`

Se il processo trackinglogd non viene visualizzato nell&#39;elenco, avviarlo con il comando seguente nell&#39;istanza: `<user>@<instance>:~$ nlserver start trackinglogd`

**Verificare che il flusso di lavoro tecnico di tracciamento sia stato eseguito di recente**

Puoi individuare il flusso di lavoro tecnico Tracciamento nelle cartelle Amministrazione > Produzione > Flussi di lavoro tecnici.

### Risoluzione avanzata dei problemi {#advanced-troubleshooting}

+++Il flusso di lavoro di tracciamento non riesce

>[!NOTE]
>
>Disponibile solo per Windows

Il file di registro di tracciamento danneggiato .../nl6/var/&lt;nome_istanza>/redir/log/0x0000 log può arrestare il flusso di lavoro di tracciamento. Per rilevare facilmente le righe danneggiate e rimuoverle per riprendere il flusso di lavoro di tracciamento, puoi utilizzare i comandi seguenti.

**So in quale file si trova la riga danneggiata**

In questo caso, le righe danneggiate si trovano nel file 0x00000000000A0000.log, ma lo stesso processo può essere applicato a un set di file - uno per uno.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Puoi quindi interrompere il flusso di lavoro di tracciamento, eliminare le righe danneggiate e riavviare il flusso di lavoro.

**Non so in quale file si trovi la riga danneggiata**

1. utilizzare la riga di comando seguente per archiviare tutti i file di tracciamento.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. Il comando elenca tutte le righe danneggiate. Ad esempio:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Il ritorno a capo è stato aggiunto prima dell’agente utente per consentire una migliore lettura e non riflette l’efficacia del rendering.

1. Esegui un comando grep per trovare il file corrispondente.

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. Individuare il registro con il nome del file e il numero di riga. Ad esempio:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >È stato aggiunto un ritorno a capo prima dell’agente utente per consentire una migliore lettura e non riflette l’efficacia del rendering.

Puoi quindi interrompere il flusso di lavoro di tracciamento, eliminare le righe danneggiate e riavviare il flusso di lavoro.

+++

+++Il tracciamento dei collegamenti ha esito negativo a intermittenza

Quando tenti di accedere ai collegamenti di tracciamento, viene visualizzato il seguente messaggio:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. Accedi all’URL di &lt;redirection_server>/r/test e verifica se il numero di build e localhost sono stati restituiti dalla richiesta.

1. Verificare la configurazione spareServer nel file serverConf.xml per il server di tracciamento. Questa configurazione deve essere in modalità di reindirizzamento.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Verifica manualmente se il file &lt;deliveryID>.xml esiste nel computer nella directory .../nl6/var/&lt;nome_istanza>/redir/url/&lt;AAAA> (AAAA rappresenta l’anno di consegna).

1. Verifica manualmente se &lt;trackingUrlId> è disponibile nel file &lt;deliveryID>.xml.

1. Verifica manualmente l’esistenza di broadlogID nella consegna deliveryID correlata.

1. Controlla le autorizzazioni dei file &lt;deliveryID>.xml nella directory .../nl6/var/&lt;nome_istanza>/redir/url/year.

   Devono disporre di almeno 644 autorizzazioni in modo che Apache possa leggere gli URL di tracciamento per reindirizzare il collegamento richiesto.

+++

+++Aggiornamento dell&#39;opzione NmsTracking_Pointer

Per aggiornare l&#39;opzione NmsTracking_Pointer, effettuare le seguenti operazioni:

1. Interrompi il flusso di lavoro di tracciamento.

1. Arresta il servizio trackinglogd.

1. Aggiornare l&#39;opzione NmsTracking_Pointer al valore desiderato.

1. Riavviare il servizio trackinglogd.

1. Riavvia il flusso di lavoro di tracciamento.

+++

+++Il tracciamento non funziona con alcuni WebMail

Puoi personalizzare la formula di tracciamento dei clic e specificare una formula di tracciamento Adobe Analytics personalizzata.

Questo tipo di personalizzazione deve essere fatto con cautela per evitare di aggiungere caratteri di avanzamento riga aggiuntivi. Tutti i caratteri di avanzamento riga presenti al di fuori dell’espressione JavaScript saranno presenti nella formula finale.

Questo tipo di carattere di avanzamento riga aggiuntivo nell’URL di tracciamento causerà un problema in alcuni webMail (AOL, GMail, ecc.).

**Primo esempio:**

* Sintassi errata

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* Sintassi corretta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

Per capire dove si trova l’avanzamento di riga aggiuntivo, puoi sostituire l’espressione JavaScript con una stringa fissa STRING.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Secondo esempio**

* Sintassi errata

  ```
  <%@ include option='NmsTracking_ClickFormula' %>
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* Sintassi corretta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

Per capire dove si trova l’avanzamento di riga aggiuntivo, puoi sostituire l’espressione JavaScript con una stringa fissa STRING.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++Il recupero dei registri di tracciamento è troppo lento

Quando l’istanza non recupera i registri di tracciamento direttamente ma da un server Adobe Campaign Classic lontano, i registri vengono recuperati tramite la chiamata SOAP GetTrackingLogs definita nello schema remoteTracking.

Un&#39;opzione nel file serverConf.xml consente di impostare il numero di registri recuperati contemporaneamente tramite questo metodo: logCountPerRequest.

Il valore predefinito di logCountPerRequest è 1000 e in alcuni casi potrebbe essere troppo piccolo. I valori accettati devono essere compresi tra 0 e 10.000.

+++

+++Impossibile collegare i registri di tracciamento ai destinatari

In Adobe Campaign Classic, una mappatura di destinazione dovrebbe essere univoca in termini di schema del destinatario rispetto agli schemi broadlog/trackinglog.

![](assets/tracking-troubleshooting.png)

Non è possibile utilizzare più schemi di targeting con lo stesso schema di registro di tracciamento, poiché il flusso di lavoro di tracciamento non sarà in grado di riconciliare i dati con l’ID di targeting.

Se non desideri utilizzare la mappatura di destinazione predefinita con nms:recipient, ti consigliamo i seguenti approcci:

* Se si desidera utilizzare una dimensione di targeting personalizzata, è necessario creare lo schema broadLog/trackingLog personalizzato utilizzando come modello nms:broadlog (ad esempio nms:broadLogRcp, nms:broadLogSvc e così via).

* Se si desidera utilizzare OOB trackingLogRcp/broadLogRcp, la dimensione di targeting deve essere nms:recipient e la dimensione di filtro potrebbe essere uno schema personalizzato.

+++
