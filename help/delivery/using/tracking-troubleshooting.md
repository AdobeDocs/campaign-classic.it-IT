---
product: campaign
title: Risoluzione dei problemi di tracciamento
description: Questa sezione fornisce domande comuni relative alla configurazione e all’implementazione del tracciamento in Adobe Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring, Troubleshooting
role: User
exl-id: 62e67a39-1e5c-4716-a3f3-b0ca69693cd0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 1%

---

# Risoluzione dei problemi di tracciamento {#tracking-troubleshooting}

In questa sezione troverai domande comuni relative alla configurazione e all’implementazione del tracciamento in Adobe Campaign Classic.

## Il flusso di lavoro di tracciamento non riesce {#tracking-workflow-failing}

Il flusso di lavoro di tracciamento non riesce, come posso rilevare le righe danneggiate nel file di tracciamento?

>[!NOTE]
>
>Disponibile solo per Windows

Il file di registro di tracciamento danneggiato .../nl6/var/&lt;instance_name>/redir/log/0x0000 log può arrestare il flusso di lavoro di tracciamento. Per rilevare facilmente le righe danneggiate e rimuoverle per riprendere il flusso di lavoro di tracciamento, puoi utilizzare i comandi seguenti.

### So in quale file si trova la riga danneggiata

In questo caso, le righe danneggiate si trovano nel file 0x00000000000A0000.log, ma lo stesso processo può essere applicato a un set di file - uno per uno.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Puoi quindi interrompere il flusso di lavoro di tracciamento, eliminare le righe danneggiate e riavviare il flusso di lavoro.

### Non è possibile individuare il file in cui si trova la riga danneggiata

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

## Il tracciamento dei collegamenti ha esito negativo a intermittenza {#tracking-links-fail-intermittently}

Quando tenti di accedere ai collegamenti di tracciamento, viene visualizzato il seguente messaggio:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. Accesso &lt;redirection_server>/r/test URL e verifica se il numero di build e localhost sono stati restituiti dalla richiesta.

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

1. Controllare manualmente se &lt;deliveryid>Il file .xml esiste nel computer in .../nl6/var/&lt;instance_name>/redir/url/&lt;yyyy> (AAAA rappresenta l’anno di consegna).

1. Controlla manualmente se &lt;trackingurlid> si trova nella sezione &lt;deliveryid>file .xml.

1. Verifica manualmente l’esistenza di broadlogID nella consegna deliveryID correlata.

1. Verifica &lt;deliveryid>autorizzazioni dei file .xml in .../nl6/var/&lt;instance_name>directory /redir/url/year.

   Devono disporre di almeno 644 autorizzazioni in modo che Apache possa leggere gli URL di tracciamento per reindirizzare il collegamento richiesto.

## Aggiornare l&#39;opzione NmsTracking_Pointer? {#updating-option}

Per aggiornare l&#39;opzione NmsTracking_Pointer, effettuare le seguenti operazioni:

1. Interrompi il flusso di lavoro di tracciamento.

1. Arresta il servizio trackinglogd.

1. Aggiornare l&#39;opzione NmsTracking_Pointer al valore desiderato.

1. Riavviare il servizio trackinglogd.

1. Riavvia il flusso di lavoro di tracciamento.

## Il tracciamento non sembra funzionare con alcuni WebMail {#webmail}

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

## Il recupero dei registri di tracciamento è troppo lento {#slow-retrieval}

Quando l’istanza non recupera i registri di tracciamento direttamente ma da un server Adobe Campaign Classic lontano, i registri vengono recuperati tramite la chiamata SOAP GetTrackingLogs definita nello schema remoteTracking.

Un&#39;opzione nel file serverConf.xml consente di impostare il numero di registri recuperati contemporaneamente tramite questo metodo: logCountPerRequest.

Il valore predefinito di logCountPerRequest è 1000 e in alcuni casi potrebbe essere troppo piccolo. I valori accettati devono essere compresi tra 0 e 10.000.

## Impossibile collegare i registri di tracciamento ai destinatari {#link-recipients}

In Adobe Campaign Classic, una mappatura di destinazione dovrebbe essere univoca in termini di schema del destinatario rispetto agli schemi broadlog/trackinglog.

![](assets/tracking-troubleshooting.png)

Non è possibile utilizzare più schemi di targeting con lo stesso schema di registro di tracciamento, poiché il flusso di lavoro di tracciamento non sarà in grado di riconciliare i dati con l’ID di targeting.

Se non desideri utilizzare la mappatura di destinazione predefinita con nms:recipient, ti consigliamo i seguenti approcci:

* Se desideri utilizzare una dimensione di targeting personalizzata, devi creare uno schema broadLog/trackingLog personalizzato utilizzando nms:broadlog come modello (ad esempio nms:broadLogRcp, nms:broadLogSvc, ecc.).

* Se desideri utilizzare OOB trackingLogRcp/broadLogRcp, la dimensione di targeting deve essere nms:recipient e la dimensione di filtro può essere uno schema personalizzato.
